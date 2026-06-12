---
title: "Major Audio Issues"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by Deiz on 2008-01-31
I'm having issues setting up audio output - I have an Audigy 2 ZS that I want to use for all sound, besides music via Foobar2000 (Which I'm running in Wine.). Foobar2000 would be fed with my DAC, which connects via USB.

DAC: Can seemingly only be accessed by ESD and PulseAudio, and once that happens, I can't select "USB Audio" in sound preferences, as I get a "Resource busy or not available." error
 
Audigy 2 ZS: Can be accessed by p16v, OSS, ALSA, "ADC Capture/Standard PCM Playback". Once p16v is used,the other three give me a "Resource busy or not available." error.

ALSA, OSS, and ADC Capture/Standard PCM Playback are all substantially quieter than p16v - Does p16v ignore system volume settings?

Games: Make no sound when p16v is in use, as I assume they're trying to use ALSA or OSS. If ALSA or OSS are available and ESD hasn't been used by Foobar2000, the game will make sound, but Foobar2000 cannot use ESD while the game is running. The inverse is true, as well.

Another **extremely** annoying quirk is that on some boots, ALSA will work, but usually, it doesn't, and just gives me "Resource busy or not available." I've no idea what causes this.

Any help is greatly appreciated. It's a pain in the *** to reboot five or six times just to get sound in a game I'm going to play for twenty minutes.

Edit: A small update, I was wrong.

ALSA will only ever work if Wine's audio driver is something other than ESD. It doesn't matter if Wine / Foobar2000 through Wine has been run, if the setting is there, ALSA does notwork.

Another edit: It seems that if wine is configured to be *anything*, even ALSA, ALSA will not work. Whenever Wine is configured to use a driver, the logon/logoff noises go through to my DAC instead of the Audigy.

In order to get sound back, I need to purge linux-sound-base, alsa-base, and alsa-utils.

Edit 3: That no longer works. I've uninstalled Wine, purged everything, reinstalled everything, and double-checked all settings. ALSA still doesn't function.

---

### Post by Deiz on 2008-02-01
Bump. Any help is appreciated.

---

