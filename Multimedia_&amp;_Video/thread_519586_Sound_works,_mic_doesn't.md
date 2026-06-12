---
title: "Sound works, mic doesn't"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by TheFuzzy0ne on 2007-08-07
Hi everyone. I've just installed the alsa lib and drivers to get my sound card working.

Here is some of the output from running various commands at the CLI:

```

daz@fuzz-comp:~$ sudo lspci -v

*SNIP*

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device a88d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

*SNIP*

```

```

daz@fuzz-comp:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I followed the guide [here]("http://alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0") (which was the only one on [www.alsa-project.org](www.alsa-project.org) for Nvidia cards), but my sound works great, although my mic doesn't.

I use my mic for TeamSpeak, and the strange thing is that when I speak, it acknowledges it, and the green light comes on which activates my mic, but for some reason my voice is not transmitted. I tried to record myself blowing into the mic, and when I play it back, I can only hear a series of faint clicks instead which replaces the bits where I blew into the mic. However, it should be noted that when I blow into the mic I can hear it through my headset and/or speakers.

I have all the channels turned up to full in alsamixer, including both of the "capture" sliders.

I have two input sources to set in alsamixer. One is set to "Mic" and the other is set to "Front Mic" (both jacks have identical symptoms).

I've tested the mic, and it works on my other 2 machines without a hitch, so I can confirm the mic is not the problem.

I am a bit baffled about the file I need to put into /etc/modutils/. I created the file and named it "alsa", and ran update-modules. Since rebooting, the file has disappeared. Is this right, or have I put the file in the wrong place?

My PC is a brand new Acer Aspire T180, but they sealed it up so if I try to gain access to it, it will void the warranty.

I would really appreciate some advice here. I have another card which I know works, but it has no pin headers for front mic and headset, which would be a slight issue for me.

Thanks in advance.

---

### Post by jnorthr on 2007-08-07
had the same problem yesterday. was using a usb microphone and ubuntu did not recognise it so i just found an old mic with an rca jack and plugged it into to mic in port of my laptop and it worked ok. Can you try another mic to see if it's the hardware ?

---

### Post by TheFuzzy0ne on 2007-08-07
> **jnorthr said:**
> had the same problem yesterday. was using a usb microphone and ubuntu did not recognise it so i just found an old mic with an rca jack and plugged it into to mic in port of my laptop and it worked ok. Can you try another mic to see if it's the hardware ?

I already did. My trusty older mic worked great on my old machine, but it's not doing anything on the new one. I just think it's weird that I can hear myself blowing into the mic. That suggests it is working, and perhaps there's something wrong with the routing on my system.

---

### Post by victorgreen on 2007-09-13
I have roughtly the same problem, my longitech headset will be recognized. One setting will be tweaking in capture or mic or digital and then my friend stops being able to hear me and likewise for my friend who is also on 7.04. 

This is absolutely ridiculous.

---

### Post by oxygenws on 2007-09-13
check out this guide: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by srangelov on 2007-12-04
Hi!

The solution is simple. It is an issue of the soundcard setup.

1. Double-click on the sound icon from the main panel - the Volume Control panel opens.
2. Click on File -> Change Device and select Realtek ALC883.
3. Click on Edit -> Preferences and select all tracks to be visible.
4. The track In-gain should be enabled with a slider up to the top.
5. You can mute the Microphone - so that you cannot hear yourself.

That's it!

Make a test call via skype or other messenger and enjoy Ubuntu :)

Sotir

---

### Post by go_beep_yourself on 2007-12-09
> **srangelov said:**
> Hi!

The solution is simple. It is an issue of the soundcard setup.

1. Double-click on the sound icon from the main panel - the Volume Control panel opens.
2. Click on File -> Change Device and select Realtek ALC883.
3. Click on Edit -> Preferences and select all tracks to be visible.
4. The track In-gain should be enabled with a slider up to the top.
5. You can mute the Microphone - so that you cannot hear yourself.

That's it!

Make a test call via skype or other messenger and enjoy Ubuntu :)

Sotir

How can that be done without Gnome? I have enlightenment only. My computer can't run Gnome. How can I do that with alsamixer.

---

