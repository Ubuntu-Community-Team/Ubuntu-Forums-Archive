---
title: "Ubuntu/Feisty sound no longer audible (Sony laptop, PCG-FXA53)"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by wirawan0 on 2007-09-09
I installed Ubuntu Feisty (7.04) on my Sony VAIO laptop (PCG-FXA53, powered by AMD Athlon CPU, 512 MB RAM). Using the very first installation, I could get the sound to work fine. Right now, after updates (current kernel was = 2.6.20-16-generic), the sound could no longer be heard. Of course in between I also installed quite a  bit of things, so I can't quite pinpoint where I did wrong.

Here is the output of lspci:
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)
00:0a.0 CardBus bridge: Texas Instruments PCI1420
00:0a.1 CardBus bridge: Texas Instruments PCI1420
00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

I tried to play an audio file, e.g. 

$ play /usr/share/sounds/login.wav

The program went fine, as if it played the sound. But no sound was heard.

Here are the things that I've looked at:

* Are the volume levels OK (the PCM and overall volume)? YES.
* Is the audio muted? The mixer (both alsamixer or the GUI mixer) say NO.
* Are the audio devices accessible? YES. Otherwise play command would give some error indication.

In brief, the OS seems to see the sound card as "OK", but somehow no sound was output if I tried all the programs: xmms, play, ogg123, etc. Also, dmesg doesn't seem to indicate any error.

I rebooted into the 7.04 liveCD, and the audio went back to work. So something is wrong with my current installation on the hard disk.

Can you help me find the error? I will give you more diagnostic output if you need them.


Wirawan

---

### Post by wirawan0 on 2007-09-20
No answer, huh? :-(

Never mind. I found the answer: my overall volume level was too low. I raised it up to >50%, and the sound was heard again. It's strange that this sound card seemingly has a "nonlinear" volume control (I mean "nonlinear" with respect to our ears. The 50% volume level does not correspond to 50% of the maximum volume level as I typically would expect. In Windows, the volume was increased rapidly when the slider goes from 0--30%,  then barely increasing afterward.  In Linux, it's the other way around. The volume level goes up rapidly only after the slider is moved at or beyond ~50% . Weird.

---

