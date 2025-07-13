# Analytics Client

[![Build Status](https://travis-ci.org/john-doherty/mixpanel-lite.svg?branch=master)](https://travis-ci.org/john-doherty/mixpanel-lite)

A lightweight _(2.9k)_ JavaScript analytics client library with offline support for Hybrid and Progressive Web Apps.

This library provides a simple API for tracking events and user properties, compatible with popular analytics service endpoints. Events are written to localStorage first and are only removed once the analytics API confirms receipt, thus allowing the device to go offline without losing events.

**Note**: This client library can be used with self-hosted analytics APIs (like [TrainerDay's analytics-api](https://github.com/trainerday/analytics-api)) or any compatible analytics service endpoint.

## Usage

Add [analytics-client.min.js](dist/analytics-client.min.js) to your project:

```html
<script src="analytics-client.min.js"></script>
```

At present only the following methods are supported:

```js
// setup analytics client
mixpanel.init('your-token-here'); // pass { mute: true } to mute by default

// assign all future events to a user
mixpanel.identify('user@email.com');

// register 'Gender' as a super property
mixpanel.register({'Gender': 'Female'});

// assign user info
mixpanel.people.set({
    $email: 'user@email.com' // only special properties need the $
});

// track an event
mixpanel.track('Your Event Name' {
    firstName: 'Optional event property 1',
    lastName: 'Optional event property 2'
});

// clear current identity
mixpanel.reset();

// stop sending data to analytics (calls to track, identify etc are ignored)
mixpanel.mute();

// resume sending data to analytics
mixpanel.unmute();

// check if analytics is muted
if (mixpanel.muted) {
    console.log('Analytics is disabled');
}
```

## Contributing

Pull requests are welcomed:

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request

### Dependencies

analytics-client uses `window.localStorage` and `window.Promise` which should exist in all modern browsers.

### Update .min files

To generate a new [analytics-client.min.js](dist/analytics-client.min.js) from source, tweak the version number in `package.json` and run:

```bash
npm run build
```

## Star the repo

Star the repo if you find this useful as it helps me prioritize which bugs I should tackle first.

## History

For change-log, check [releases](https://github.com/john-doherty/mixpanel-lite/releases).

## License

Licensed under [MIT License](LICENSE) &copy; [John Doherty](https://twitter.com/mrJohnDoherty)
