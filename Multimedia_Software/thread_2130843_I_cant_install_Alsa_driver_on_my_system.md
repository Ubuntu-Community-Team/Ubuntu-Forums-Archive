---
title: "I cant install Alsa driver on my system"
date: 2013-03-30
forum: Multimedia Software
---

### Post by mr.suchy on 2013-03-30
Hi

I have this sound card:
```
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
    Subsystem: Creative Labs SBLive! 5.1 Model SB0100
    Flags: bus master, medium devsel, latency 32, IRQ 10
    I/O ports at d800 [size=32]
    Capabilities: [dc] Power Management version 1
    Kernel modules: snd-emu10k1


```

When I want install sound driver alsa-driver-1.0.25.tar.bz2 I have error:

```
In file included from /usr/src/alsa/alsa-driver-1.0.25/firewire/speakers.c:5:0:
/usr/src/alsa/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c: In function ‘fwspk_card_free’:
/usr/src/alsa/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c:664:2: error: implicit declaration of function ‘fw_device_put’ [-Werror=implicit-function-declaration]
/usr/src/alsa/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c: In function ‘fwspk_probe’:
/usr/src/alsa/alsa-driver-1.0.25/firewire/../alsa-kernel/firewire/speakers.c:721:2: error: implicit declaration of function ‘fw_device_get’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.25/firewire/speakers.o] B&#322;&#261;d 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.25/firewire] B&#322;&#261;d 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.25] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-3.5.0-18-generic'
make: *** [compile] B&#322;&#261;d 2


```

---

### Post by ManamiVixen on 2013-03-30
You don't need to install it. It is already included in the Kernel. Is there a reason why you are trying to install it?

EDIT: I see that is an SB0100 which is included in Dell Computers. Be aware it is actually a Sound Blaster Live! Value card which is a stripped down version of the original Live! and is missing stuff like MIDI playback.

---

### Post by mr.suchy on 2013-03-31
Thanks for replay. I want install ALSA driver beacause I dont have sound in my computer. When I install Xubuntu everything was good almost beacause I have strange noise in my speakers so that is the reason why I try install alsa and pulsaudio once again. Do you have any HOWTO install sound card in Xubuntu 12.10 ?

-edit

I dont see my Sound Blaster in pulseaudio server, configuration.

---

### Post by ManamiVixen on 2013-04-01
Do you have onboard audio enabled or a HDMI Enabled Graphics card? They may be causing issues and I need to know. Also, try "alsamixer" in terminal. It will list the default card in the top left corner of the terminal window. If the Sound Blaster is default, push F5 on the keyboard and look for channels that say "MM" at the bottom. If they say that, they are muted. Just select them with the arrow keys and push up to unmute and set sound level. **DO NOT SET ANY SLIDER OVER 100%!!! IT WILL CAUSE THE SOUND TO COME OUT LIKE CRAP!!!** But up to 100% is fine. What you are lookig for in particular is PCM and Master. They control the main sound output. If you don't have Surround Sound, you can keep the other channels muted if you want. Ther also should be MIC. If you use that, only the rear MIC jack will work.  Also, I said the SB0100 was the cheap DELL card, I was mistaken. The SB0200 is the Cheap Dell Card. The SB0100 is the official Sound Blaster and is fully featured. Sorry about that.

---

### Post by mr.suchy on 2013-04-02
ehh thanks for help but just like I said. I think I dont have a alsa in my system. When I try install I have error like in first port. When I type alsamixer I have "command not find".

---

### Post by ManamiVixen on 2013-04-02
Thats very, very, odd.... ALSA is default on all Linux computers. It's part of the kernel.

Try "sudo apt-get install alsa-utils" then do "alsamixer" again.

Edit: Hold on. You may have broken ALSA with the compiling. Meaning you now have a compromised kernel and broken packages. I urge you to reinstall Ubuntu before continuing with the sound troubleshooting.

---

### Post by mr.suchy on 2013-04-02
I all ready have alsa-utils. Thanks for advice.

---

### Post by mr.suchy on 2013-04-03
Today I red [https://help.ubuntu.com/12.10/ubuntu-help/sound-nosound.html](https://help.ubuntu.com/12.10/ubuntu-help/sound-nosound.html) and I sure that I need to install sound driver in my system. In another post somebody has the same problem as me. But he run this command and I can't do that because I have error
```
sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
```
because I dont have information that linux can't find this package. What can I don besides install a fresh system ?

---

