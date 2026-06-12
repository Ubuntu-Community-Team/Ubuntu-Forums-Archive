---
title: "Midi unavailable java 1.5"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by njochen on 2006-07-02
Hi,

I am trying to use java 1.5 (tiger) on ubuntu 6.06. I installed the java SDK and everything seems to be working. However, when I tried to run a midi application that i built i got this:

javax.sound.midi.MidiUnavailableException: Audio Device Unavailable
javax.sound.midi.MidiUnavailableException: Audio Device Unavailable
        at com.sun.media.sound.MixerSynth.implOpen(MixerSynth.java:154)
        at com.sun.media.sound.AbstractMidiDevice.doOpen(AbstractMidiDevice.java:144)
        at com.sun.media.sound.AbstractMidiDevice.openInternal(AbstractMidiDevice.java:134)
        at com.sun.media.sound.AbstractMidiDevice.getReceiverReferenceCounting(AbstractMidiDevice.java:339)
        at javax.sound.midi.MidiSystem.getReceiver(MidiSystem.java:243)
        at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:442)
        at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:348)


it looks like the midi devices are not available on linux ? I am sort of new to developing on linux but I am a little confused as to how to fix this. any help would be appreciated !!!

thanks
- jochen

---

### Post by njochen on 2006-07-02
wow. strange. i just closed and reopened my application and suddenly it worked...
how strange...

---

