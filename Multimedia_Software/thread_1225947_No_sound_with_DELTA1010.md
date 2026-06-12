---
title: "No sound with DELTA1010"
date: 2009-07-29
forum: Multimedia Software
---

### Post by drumanart on 2009-07-29
Hello everybody.
I have a fresh installed jaunty with ubuntu-studio.
After disable the On Board sound-card at the BIOS, my Delta1010 is recognized as the first sound-card but still I have no sound.

I followed the Sound Trouble Shooting link here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
but without succes.


**aplay -l** returnes:

martin@martin-desktop:~$ **aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: M1010 [M Audio Delta 1010], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



**lspci -v** returnes:

04:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712
[Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: VIA Technologies Inc. Device d630
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at ec00 [size=32]
        I/O ports at e880 [size=16]
        I/O ports at e800 [size=16]
        I/O ports at e480 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: ICE1712
        Kernel modules: snd-ice1712



**alsamixer** shows:
Card: M Audio Delta 1010                                          

Chip: ICE1712 - multitrack                                        

iew: [Playback] Capture  All                                     

Item: IEC958 [H/W In 0]


**Preferences Sound ERROR message:**
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample !
gconfaudiosink profile=chat: Could not open audio device for playback.


Hopefully somebody can help

regards Martin

---

### Post by EzeKB on 2010-07-15
I'm having problems with Delta 1010 LT too. Can't get no audio.
As soon as anybody figures out how to solve it I'll let you know. If you can solve it first, post how so I can fix it too. :?
Thanks!

---

### Post by jeebustrain on 2010-07-15
here's the fix: 

[http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-a-781558/#post3846043](http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-a-781558/#post3846043)

follow the instructions in green and reboot.

---

### Post by lidex on 2010-07-17
Required reading:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442?comments=all]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442?comments=all")

---

