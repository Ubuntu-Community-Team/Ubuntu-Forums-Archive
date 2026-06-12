---
title: "Transcriber in Ubuntu 11.04"
date: 2011-05-09
forum: Multimedia Software
---

### Post by neilhnz on 2011-05-09
Although an old program, it is a fantastic little program. I cannot find anything else that will do the same job as well.

It used to work fine but now under Ubuntu 11.04 it comes up with an error message when you try and play the sound file.

This is the error message.
Could not gain access to /dev/sound/dsp for writing.
Could not gain access to /dev/sound/dsp for writing.
    while executing
"player play -start [expr int($begin*$rate)] -end [expr int($end*$rate)]"
    (procedure "PlayRange" line 56)
    invoked from within
"PlayRange $pos $end $script"
    (procedure "Play" line 64)
    invoked from within
"Play"
    (procedure "PlayOrPause" line 10)
    invoked from within
"PlayOrPause"
    invoked from within
".cmd.play invoke"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list $w invoke]"
    (procedure "tk::ButtonUp" line 22)
    invoked from within
"tk::ButtonUp .cmd.play"
    (command bound to event)

Any help would be greatly appreciated.

Regards,

Neil...

---

### Post by pmyteh on 2011-05-18
I don't know how to solve the problem "properly", but a workaround is to wrap the execution of transcriber inside a call to padsp, which is the PulseAudio OSS wrapper. This seems to work, though I haven't tested it in detail:
```
user@machine$ padsp transcriber
```By amending the entry for transcriber in System > Preferences > Main Menu it should be possible to do this automatically when you click on the menu entry.

Hope that helps,
Tom

---

