---
title: "Delta 66, no sound, tried almost everything, read everything,,,"
date: 2010-10-10
forum: Multimedia Software
---

### Post by Joel_Ellis on 2010-10-10
Hi there,

I'm new to Linux (Ubuntu). I have used numerous windows versions over time. A friend of mine told me that LInux is really good. I then installed Ubuntu 10.04. Everything works just great, It's a really good OP-system but I can't get sound out of my Delta 66 card. I have read loads of stuff all over the net and tried so much but still no sound. 

The story so far:
I have a Delta 66 card connected to a Behringer mixing console.
My onboard card is disabled through Bios.
A graphic card with audio input

Here is my setup through aplay:
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M66 [M Audio Delta 66], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I made my Delta card default through ,asoundrc:
defaults.ctl.card 1
defaults.pcm.card 1
defaults.timer.card 1

I removed pulse audio:
$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
I installed the alsamixerGui and graohic interface for Alsamixer. I also have good levels in Alsamixer.

I get sound when I test the system through gstreamer-properties.

I also updated Alsa to 1.0.23 but then lost my card completely.

I don't get sound when I play stuff through Movie player or VLC player.

What's wrong??? please help me I'm going insane

---

### Post by cchhrriiss121212 on 2010-10-10
Removing pulse was a good idea and that should be the hardest step for most users. From the sound of it you made an error when you upgraded ALSA (which is not even necessary), going to be easier to fix if you can explain what you did or what guide you were following.

Does aplay -l show your card? What about lspci -v?

---

### Post by DJonsson2008 on 2010-10-10
If it's any help my DAW runs on Xubuntu 9.4. 
With 9.4 on a fresh install I find it takes about 30-60 
minutes to get it running including install of Audacity.

Like yourself I disable the internal sound card on the bios. 
This bios switch is done though before installing Xubuntu, 
after that the Delta card just works.

---

### Post by Joel_Ellis on 2010-10-10
Cheers for the answer mate. I actually went back to 1.0.21 and did all the stuff in the beginning of my post.
   lspci -v says with 1.0.21 says (only audio related)

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: Giga-byte Technology Device 5000
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
    Subsystem: ASUSTeK Computer Inc. Device aa28
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f5010000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

05:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
    Subsystem: VIA Technologies Inc. Device d632
    Flags: bus master, medium devsel, latency 32, IRQ 19
    I/O ports at c000 [size=32]
    I/O ports at c100 [size=16]
    I/O ports at c200 [size=16]
    I/O ports at c300 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: ICE1712
    Kernel modules: snd-ice1712

.

---

### Post by Joel_Ellis on 2010-10-10
Ubuntu studi might be something for me. Or is it built in the same way with PulseAudio and stuff.

I turn off the sound card before I did the fresh install. I have made a few during the time of this audio related problem ;) 

I forgot, I also deleted the .pulse folder and the cookie file as well with no luck.

---

### Post by DJonsson2008 on 2010-10-10
Looking at that Delta DAW install its actually Xubuntu 10.04, it started as 9.4 then was upgraded to 10.04, in any case Delta cards
are known to work well with Ubuntu.

The 2 tools for I use to adjust input and output volume are

alsamixergui and envy24

M-Audio's website forum can also be very helpful on this subject.

[http://forums.m-audio.com/](http://forums.m-audio.com/)

---

### Post by DJonsson2008 on 2010-10-10
One of the improvements since 10.04 make it so you can simply disable pulse audio in the startup.

I'm not on an Ubuntu machine a the moment but it should be easily available under one of the system or settings menus. 

Once you find our startup apps gui
all you need to do 
uncheck [ ] pulse audio as an 
auto startup app.

---

### Post by DJonsson2008 on 2010-10-10
I found Ubuntu Studio was packed with lot of things 
I did not need.

In the end for my DAW a standard install of Xubuntu was 
slightly lighter for the quiet Atom Duo-Core Intel machine 
I was running it on. 9.4 if I remember correctly did not
have Pulseaudio as a default, so that helped.

All I use now is Audacity for home recording sessions, which 
seemed like a simple starting point. So far I don't use 
JACK and the other advanced studio tools that are part
of Ubuntu Studio. Other people do though and if that is
the direction you are going perhaps Ubuntu Studio may be
a better entry point.

---

### Post by cchhrriiss121212 on 2010-10-10
Your output seems in order.
Studio is just the same as Ubuntu plus a few extra packages, so installing it won't help as it has the same pulse setup. You may just be looking at the wrong section in envy as it has many different tabs. The one you want to use for setting volume is analogue volume, DACs are outputs and ADCs are inputs.
Or your HDMI audio may still be acting as the default card.

---

### Post by Joel_Ellis on 2010-10-10
> **cchhrriiss121212 said:**
> Your output seems in order.
Studio is just the same as Ubuntu plus a few extra packages, so installing it won't help as it has the same pulse setup. You may just be looking at the wrong section in envy as it has many different tabs. The one you want to use for setting volume is analogue volume, DACs are outputs and ADCs are inputs.
Or your HDMI audio may still be acting as the default card.
 
My next thing was actually to change the order of the cards in alsa.conf file so Delta card becomes card 0, but I don't know where to put the code. I had a look at the code for multiple cards at ALSA home page.
 
I been at the M-audio page as well found almost the same stuff as here.

---

### Post by Joel_Ellis on 2010-10-11
A quick update. 

I changed the order of the cards so my DElta 66 is card 0.

I also see output in the level meters for PCM OUt 1 and 2 in the Envy24 Control when I'm playing music with VLC player. I think I'm pretty close now.

Please someone help me with the last bits.

---

### Post by cchhrriiss121212 on 2010-10-11
Like I said the only thing you have not confirmed is the analogue volume levels, it could be that you have raised the wrong ones, so just raise them all if you haven't already.
Also check you are using ALSA audio output in VLC.

---

### Post by Joel_Ellis on 2010-10-12
Cheers all fo the guidance. I'm kind of embarresed:guitar:. After I had changed the order of the cards I had good levels on the 1 and 2 analogic outputs in Envy24 as I said the earlier post. 
 
The thing was that I had changed to to outputs 3 and 4 on my break-out box to the Behringer mixer a while back. So when I was playing around with my kids yesterday I remember this change. I ran to the computer and changed to 1 and 2 on the break-out box and there was sound.
 
Sometimes You are just stupier than usual and this brain starting to get old and worn out as well ;)

---

