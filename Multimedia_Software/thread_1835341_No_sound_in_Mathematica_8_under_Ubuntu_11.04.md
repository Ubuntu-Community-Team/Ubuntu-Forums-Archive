---
title: "No sound in Mathematica 8 under Ubuntu 11.04"
date: 2011-08-29
forum: Multimedia Software
---

### Post by hameerabbasi on 2011-08-29
Hello,

Mathematica 8, under Ubuntu 11.04, gives no sound. I get the following messages when playing any sound:

```
Java::excptn: A Java exception occurred: javax.sound.midi.MidiUnavailableException
    at javax.sound.midi.MidiSystem.getDefaultDeviceWrapper(MidiSystem.java:1078)
    at javax.sound.midi.MidiSystem.getReceiver(MidiSystem.java:240)
    at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:442)
    at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:348)
Caused by: java.lang.IllegalArgumentException: Requested device not installed
    at javax.sound.midi.MidiSystem.getDefaultDevice(MidiSystem.java:1130)
    at javax.sound.midi.MidiSystem.getDefaultDeviceWrapper(MidiSystem.java:1076)
    ... 13 more.

Java::excptn: A Java exception occurred: javax.sound.midi.MidiUnavailableException
    at javax.sound.midi.MidiSystem.getDefaultDeviceWrapper(MidiSystem.java:1078)
    at javax.sound.midi.MidiSystem.getSynthesizer(MidiSystem.java:307)
Caused by: java.lang.IllegalArgumentException: Requested device not installed
    at javax.sound.midi.MidiSystem.getDefaultDevice(MidiSystem.java:1130)
    at javax.sound.midi.MidiSystem.getDefaultDeviceWrapper(MidiSystem.java:1076)
    ... 11 more.
```I have tried everything [here]("https://help.ubuntu.com/community/Mathematica"), [here]("http://unix.stackexchange.com/questions/15191/mathematica-makes-no-sound-under-ubuntu-11-04") and [here]("http://superuser.com/questions/295979/no-sound-in-mathematica-8-0-1-under-linux"). I get the following output in [FONT=Courier New]init.m[/FONT] modifications (as I prefer to change [FONT=Courier New]$SoundDisplayFunction[/FONT] directly, even if I use [FONT=Courier New]Unprotect[][/FONT]):

```
Set::wrsym: Symbol $SoundDisplayFunction is Protected.
```

After that, the same thing if I play any sound. Any idea to get sound fully functional?

---

