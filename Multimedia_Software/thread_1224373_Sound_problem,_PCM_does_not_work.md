---
title: "Sound problem, PCM does not work"
date: 2009-07-27
forum: Multimedia Software
---

### Post by laggarkalle on 2009-07-27
Hi!

My system is based on a gigabyte motherboard with integrated sound card. 
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I would like to user the spdif output (card 0, device 1).

My system worked without any problems after installation. After som updates and tweaking it however stopped working for some reason, the only thing was works is DTS-passthrough in e.g. XBMC, I get sound if I play a movie which supports 5.1 audio but not if I play a mp3-file or movie without any surround.

What is the problem? No error messages is generated then play audio files, it play but no sound is coming from the receiver.
I have updated to alsa 1.0.20, it did not work before that update either. Nothing is muted in alsamixer. 

I am using Linux mint based on Ubuntu intrepid, i had the exact same problem before using Ubuntu. 

Can anyone help me?

---

### Post by martinbaselier on 2009-07-27
Could you post the output of:
lspci | grep Audio -i

---

### Post by laggarkalle on 2009-07-27
Yes, sir. 

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

---

### Post by martinbaselier on 2009-07-27
2 devices, interesting:
Some more detail would be nice. I'd like to see the output of:
lspci -s 00:14.2 -v
lspci -s 01:05.1 -v

---

### Post by laggarkalle on 2009-07-27
Yes, the addtional sound card is HDMI audio (intergrated Video with HDMI).

lspci -s 01:05.1 -v
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
        Subsystem: ATI Technologies Inc RS780 Azalia controller
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 3
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

lspci -s 00:14.2 -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Giga-byte Technology Device a022
        Flags: bus master, slow devsel, latency 32, IRQ 16
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

---

### Post by martinbaselier on 2009-07-27
Drivers are loaded normally. Nothing is muted. Now I wonder what tweaking you have done. 

Did you create ~/.asoundrc or /etc/asound.conf ? 

Or change the settings for the loaded module in /etc/modprobe.d/

The commandline can show you:
**cat ~/.asoundrc**
**cat /etc/asound.conf**
both of these files are normally not needed, so you can move them (as a backup and then restart)

**cat /etc/modprobe.d/* | grep snd-hda-intel**
will show any custom settings for the card you made, if you did. 

Do you have pulseaudio running?

**ps -e | grep pulse**
is how to see that.

If so, try 
**pulseaudio -kill**
to test without pulse or
**killall -KILL pulseaudio**
Let's first test without it, before adding it later (if you want to)
If you want to use it, you can always test later with pulse. 

If none of these show anything, you must have made some strange settings somewhere else. 

Does aplay play sounds?

Are your gstreamer settings correct? (system sound, totem gstreamer, banshee and more)
**gstreamer-properties**

---

### Post by laggarkalle on 2009-07-27
I deleted both .asoundrc and /etc/asound.conf, DTS sound still works...

cat /etc/modprobe.d/* | grep snd-hda-intel

cat: /etc/modprobe.d/arch: Is a directory
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

no pulseaudio is running

aplay does not play any sounds

i don't know abount gstreamer-properties. I have only debued with aplay, xbmc and mplayer. 


Can the alias thing cause something?

---

### Post by igorzwx on 2009-07-27
Sorry to intervene, but if you kill pulse,
you would not have sound (this was my experience)

---

### Post by igorzwx on 2009-07-27
Can you install another Ubuntu 9.04 in dual boot (for experiments)?

---

### Post by laggarkalle on 2009-07-28
Yes, i can. But it will work, I am going to solve this problem. 
One strange thing is that when playing a e.g mp3-file, my reseivcer lights up, but nothing more. My thoery is that it outputs at maybe 48000 hz which my resivcer is incapable of? How to set what?

---

### Post by igorzwx on 2009-07-28
It might be reasonable to have two Ubuntu 9.04 (in dual boot)
with different sound systems.
One of them may work.

Check if your hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by laggarkalle on 2009-07-28
hmm, i have for some reason to alsa deamons in /etc/init.d/ alsa-utils and alsasound, why?

I get the following output if I stoping alsasound:

/etc/init.d/alsasound stop
Shutting down sound driver: ERROR: Module snd_hda_codec_atihdmi is in use
ERROR: Module snd_hda_codec_realtek is in use
ERROR: Module snd_hda_codec is in use by snd_hda_codec_atihdmi,snd_hda_codec_realtek
ERROR: Module snd_hwdep is in use by snd_hda_codec
ERROR: Module snd_pcm is in use by snd_hda_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_codec_realtek,snd_hda_codec,snd_hwdep,snd                                                                                                       _pcm,snd_timer
done

How two disable the hdmi audio interface?

---

### Post by igorzwx on 2009-07-28
[http://www.google.com/search?q=alsa%20wiki%20troubleshooting&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=alsa%20wiki%20troubleshooting&ie=UTF-8&oe=UTF-8)

---

### Post by igorzwx on 2009-07-28
Was it suggested for PulseAudio?

---

### Post by laggarkalle on 2009-07-28
Yes, finally, aplay playing sounds, using the following command: 
aplay -vv -D iec958:CARD=SB,DEV=0 test.wav

But what is the difference between the above command, and this command:
mplayer alsa:device=hw=0.1  test.wav (which not working)

Howto configure asound.conf to use the above settings? Or what else could be the problem. 

I see no reason too install pulseaudio, it was not include in this dist (Linux Mint 6 Fluxbox edition)

---

### Post by igorzwx on 2009-07-28
[http://www.google.com/search?q=asound.conf%20&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=asound.conf%20&ie=UTF-8&oe=UTF-8)

the easiest way to find an answer :P

---

### Post by laggarkalle on 2009-07-28
Thank you all, the following content in asound.conf solved it 
pcm.!default {
type plug
slave {
rate 48000
pcm "spdif"
}
}

---

