---
title: "Hauppauge 1600 TV card still doesn't work"
date: 2009-01-19
forum: Multimedia Software
---

### Post by sfordin on 2009-01-19
Hi, all,

I've been combing the threads on this topic here and elsewhere, and I've dutifully followed what I believe are the correct instructions; for example, [here]("http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600"), but still no joy. I simply cannot get my Hauppauge HVR-1600 TV card to work in Ubuntu 8.10 with MythTV, xawtv, mplayer, Kaffeine, TVtime, VLC, xine, or anything else. Even the thread marked SOLVED didn't help me at all.

The closest I've gotten is with MythTV. The card is recognized and channels get scanned in the backend, but when I click "Watch TV" in the front end, the screen goes blank for a few moments -- maybe two or three seconds, and then I'm returned to the MythTV main menu, no TV, no sound, no nothing.

The card works in Windows XP (this is a dual-boot machine), and I know I have sufficient hardware resources. Here are some details:

[LIST]
[*]Kernel: 2.6.27-9-generic
[*]CPU: Athlon 64 3500+
[*]Video: Nvidia GeForce FX 5200 AGP w/256MB RAM
[*]RAM: 3GB DDR
[*]Sound: Creative X-Fi Fatal1ty
[*]TV Card: Hauppauge WinTV-HVR-1600 Model 1199 (74041)
[/LIST]

Yeah, I know, it's AGP, but still... I'm wondering if there's perhaps a conflict between the X-Fi card and the 1600. The X-Fi was a bit of a pain to install, but it works fine now. Similarly, I resolved the conflict between the 1600 and the Nvidia card by adding vmalloc=256M to the kernel line in my /boot/grub/menu.lst file.

I've installed the Conexant cx18 drivers and compiled the kernel, as described on [LinuxTV.org]("http://www.linuxtv.org/"). I've dotted all the "i"s and watched my "P"s and "Q"s, but still no joy. The cx18 drivers seem to be getting loaded correctly, as reported by dmesg:

```
scott@reason:~$ dmesg | grep cx18
[   15.812410] cx18:  Start initialization, version 1.0.4
[   15.812480] cx18-0: Initializing card #0
[   15.812484] cx18-0: Autodetected Hauppauge card
[   15.813767] cx18 0000:02:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.813777] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   15.815657] cx18-0: cx23418 revision 01010000 (B)
[   16.192532] cx18-0: Autodetected Hauppauge HVR-1600
[   16.192534] cx18-0: Raw VBI supported; Sliced VBI is not yet supported
[   16.648806] tuner 2-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   16.648843] cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   16.805846] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[   16.805849] DVB: registering new adapter (cx18)
[   16.990265] cx18-0: DVB Frontend registered
[   16.990268] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[   16.990326] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[   16.990373] cx18-0: Registered device vbi0 for encoder VBI (60 x 17328 bytes)
[   16.990420] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[   16.990423] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   17.288610] cx18:  End initialization
[   51.683348] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   51.878915] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   51.885063] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   52.977931] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
```

I bought the 1600 card, just this past Saturday from CircuitCity, in anticipation of the coming broadcast switchover in the US to digital television. Unfortunately, CircuitCity is going out of business now and they won't take the card back... I'm hoping someone can help me, please, before I have to resort to eBay or CraigsList or suchlike.

Thanks in advance for any help!

Scott

---

### Post by gohanssjn on 2009-01-21
I have this configuration:

Kernel: 2.6.27-9-generic 
CPU: Intel Q6600
Video: Nvidia GeForce 8800GTX 
RAM: 4GB DDR 
Sound: Creative X-Fi Fatal1ty 
TV Card: Hauppauge WinTV-HVR-1600

MythTV and VLC both load the uner and give a great picture, but the sound is overlaid with static and unusable.  Just another data point for anyone who can help or may be able to help with more info.

---

### Post by gohanssjn on 2009-02-13
I've tried just about everything under the sun.  Nothing works :(

---

### Post by rbmorse on 2009-02-16
My HVR1800 (same chip) doesn't work either. 

Actually, I can get a video stream using the composite input out of the cable box, but no audio. It looks pretty good in TVtime, but in Mplayer it's all green and purple. 

The thing "just works" in Windows XP.

---

### Post by forks on 2009-02-27
I just got mine to work finally.  My problem was the restricted nVidia drivers don't like the HVR-1600 drivers.  My secret sauce was to get the 1600 drivers following this process:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

Get the latest nVidia drivers following this process:

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)
(to run this you need to stop X and then start it when you are done.  This is done:
"sudo /etc/init.d/gdm stop"
"sudo /etc/init.d/gdm start")

And get them to work together using this post, part (1).

[http://ubuntuforums.org/showthread.php?t=1004660&highlight=cx18+nvidia](http://ubuntuforums.org/showthread.php?t=1004660&highlight=cx18+nvidia)

Hope that helps.

---

### Post by Jeconti on 2009-06-19
I'm having the same issue, and I found this post after I already tried the fix listed. I noticed somewhere that someone said they needed to bump vmalloc to 512, is there a way to know how much vm you need to allocated? 

or

Do I need to use the most current nVIDIA drivers? Can I roll back to one that is usable?

---

