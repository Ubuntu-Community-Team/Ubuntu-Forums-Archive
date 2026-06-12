---
title: "Zoiper success with Ubuntu 9.10 “Karmic Koala”"
date: 2010-02-07
forum: Multimedia Software
---

### Post by ihristov on 2010-02-07
Just wanted to report a workaround for making Zoiper work with Ubuntu 9.10 &#8220;Karmic Koala&#8221;

This is for folks that need an IAX/IAX2 software VoIP client. Zoiper (formerly Idefisk) is a good IAX and SIP client, albeit not open source. The free version is pretty decent and I have been using idefisk on Linux for years.

With the change in 9.10 to use PulseAudio by default some ALSA apps have issues. Zoiper is one of them. 

The issue was that I could only see 2 HDMI sound devices (not the analog speaker and microphone which were already taken by PulseAudio)

I followed the article [_Why you should care about PulseAudio (and how to start doing it)_]("http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it") and the [_Debian HOWTO_]("http://forums.debian.net/viewtopic.php?t=12497"). For the record I could not make kiax work even after I could see the proper devices. Even created an extra device as explained in the how-to cited above.

At the end of the day the workaround is pretty simple, you don't need to install any packages. Need only to create /etc/asound.conf and restart the pulseaudio daemon

1) Download and install the version of Zoiper for Ubuntu Jaunty with ALSA
2) create a new file called /etc/asound.conf with the following content
```
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

pcm.!default {
    type pulse
}

ctl.!default {
    type pulse
}
```
3) kill pulseaudio or logoff and login back in again
4) Now start zoiper and you should be able to see the proper audio device(s), select it and there is sound

Enjoy

---

