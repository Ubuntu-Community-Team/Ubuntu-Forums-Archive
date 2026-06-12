---
title: "Please include finally a working audio system in next Ubuntu"
date: 2010-08-18
forum: Multimedia Software
---

### Post by SRTS on 2010-08-18
Please please, make the next Ubuntu release FINALLY have a real working audio system!

So far the pulseaudio would only work for applications that support it. But __ALL__ java applications DONT support it. Someone said that other java such as openjdk supports it but IT'S JUST NOT TRUE.
Sun and open java just claim to support things like alsa, but in the end no matter what they just grab the audio device exclusively (OSS).
So there starts the next problem: padsp! At first it works fine and wraps all the apps that the normal Ubuntu pulseaudio system cant handle. However, after some minutes or sometimes an hour the padsp thread will just stop outputting any sound (and instead start lagging somewhat each time sound was supposed to play). So it'll be required to completely restart the app that was wrapped. Each time.
This hassle is like some alpha system that's in testing status. I've been putting up with it because I otherwise like it though.

but pleeeeasse just release a good, working audio system like any other OS in the next Ubuntu version, ok? That just can PLAY ALL audio?
Thanks a lot in advance. Otherwise good OS!

---

### Post by mikewhatever on 2010-08-18
Try filing an intelligent bug report at launchpad.net. Forum members are mostly users like yourself, and some will hardly know what you are talking about.
[Howto Report BUGS]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by texaswriter on 2010-08-18
> **SRTS said:**
> Please please, make the next Ubuntu release FINALLY have a real working audio system!

So far the pulseaudio would only work for applications that support it. But __ALL__ java applications DONT support it. Someone said that other java such as openjdk supports it but IT'S JUST NOT TRUE.
Sun and open java just claim to support things like alsa, but in the end no matter what they just grab the audio device exclusively (OSS).
So there starts the next problem: padsp! At first it works fine and wraps all the apps that the normal Ubuntu pulseaudio system cant handle. However, after some minutes or sometimes an hour the padsp thread will just stop outputting any sound (and instead start lagging somewhat each time sound was supposed to play). So it'll be required to completely restart the app that was wrapped. Each time.
This hassle is like some alpha system that's in testing status. I've been putting up with it because I otherwise like it though.

but pleeeeasse just release a good, working audio system like any other OS in the next Ubuntu version, ok? That just can PLAY ALL audio?
Thanks a lot in advance. Otherwise good OS!

Never had a problem with ANY linux operating system or Ubuntu operating system play audio. I've installed apps in Wine/Crossover, and sounds "just works". Any given audio, just works. 

This seems like an unjustified rant which really have no place. 

If you really want to do some good, be as specific as you can [no citing "alsa", "oss" or "padsp" is not specific]. Let's talk about specific applications, how the sound failed, more details, more details and finally, more details. Then you can file those into a nice bug report(s) so that it would actually make a difference.

So, no, I really doubt there will be a "finally working audio system" as the audio already works fine. The bugs, sure, let's bring them out so they can get fixed... but rants like this are just not helpful to anyone.

---

