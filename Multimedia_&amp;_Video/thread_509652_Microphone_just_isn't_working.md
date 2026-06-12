---
title: "Microphone just isn't working"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by bollofinwe on 2007-07-25
I have read many of the microphone threads, it seems most people's problem is that their mic is too quiet or they haven't switched sound capture on.

However, my problem seems different and through my hour of searching I don't think anyone else has had the same problems.

Currently I have done the following:
[LIST]
[*]I have set capture on

[*]I have boosted the mic

[*]The mic volume is up full
[/LIST]

To help you guys get a feel for the problem I will now list as much relevant information as I can.

I am currently on Fiesty 7.0.4. When i go into sound recorder and attempt to record anything it either crashes or records and when I attempt to play back afterward it just doesn't click in the "play" button and claims I haven't recorded anything.

Also, when I try to change the input device in my sound recorder and then click record it jumps back to "Capture", which I find unusual.

When I go into System > Preferences > Sound and under the "Audio Conferencing" heading I click "test" on plackback I get an error stating : 
```

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available."
```

and on capture:

```
"gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available."

```

When using OSS, but when I change it to ALSA I get no errors.


When making a loud enough sound through my mic I can hear it through my speakers.


When using audacity with an input preference of OSS: /dev/dsp or dsp1 the bar moves when I make noises with my mic (whilst recording) as though it's picking up sound but I get the following error when trying to play back:

```
Error whilst opening sound device. Please check the output device settings and the project sample rate
```

I also get this (except output changed for input) when trying to record with anything but the above OSS settings.


My main aim is to use ventrillo. Is that too much to ask (btw I got vent up and running just people cant hear me)

---

