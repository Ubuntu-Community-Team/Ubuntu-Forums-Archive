---
title: "Asus Xonar DX - Distortion when levels aren't equal"
date: 2011-10-23
forum: Multimedia Software
---

### Post by thecapsaicinkid on 2011-10-23
Pulseaudio upmixes all audio by default, so if like me you actually prefer 2ch music to be played back in 2ch you have to manually drop the rear levels to zero with the audio mixer (fade slider if using the standard Ubuntu mixer)

You can disable remixing with pulse but that also stops LFE remixing so nothing is routed to the subwoofer, not really an option.

The problem I have now is, if you attempt to set the level of any speaker to be different to any other by either moving the fade slider in the default mixer, or in pauvmixer 'unlocking' each channel and moving the slider, audio distortion occurs.

Now in 11.04, if you move the rear sliders to just above zero there's no distortion. In 10.04 LTS (which I'm now using), any difference in output between the channels causes a scratchy distortion.

Anyone got a workaround for this? Upgrading alsa drivers from backports maybe?

Personally I think it's a hideous idea that pulse upmixes by default (and doesn't let you disable it without disabling LFE/downmixing also) but that's another story.

---

### Post by thecapsaicinkid on 2011-10-23
Setting the level of the rears to zero with alsa mixer avoids the distortion. I've created launchers on the taskbar to mute/unmute the rears

```

amixer -c 1 set 'Master' rear 0%
amixer -c 1 set 'Master' rear 100%

```

-c 1 is the card number, try 0 first

---

