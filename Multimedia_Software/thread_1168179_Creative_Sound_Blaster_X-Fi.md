---
title: "Creative Sound Blaster X-Fi"
date: 2009-05-23
forum: Multimedia Software
---

### Post by m10sang10 on 2009-05-23
Hi Gentlemen;
My OS is Ubuntu 9.04 and my problem is about  Creative  Sound Blaster X-Fi card, after some time without sounds I was trying to do it work, well at the end I got it working, but...only Movie Player work OK, Rhythmbox emits sounds mixed with 'shrieks', VLC simply doesn't emit any sound by speakers, the same way does mozilla firefox.

Really I don't know which could be the problem, therefore 	
I ask you to help me, please.

Thanks in advance 
Mark.

PD: I Attach  photo of Preferences->Sound and another details.

---

### Post by Noah_Kapiolani on 2009-05-23
I begin by apologizing for not being able to directly help you with your problem.  I have used sound blaster cards since 1994 and have always been happy with them under windoze.  However, when i built my latest system i put one in and when it did not work i started to read how little they support Linux, so i returned my sound blaster card and bought a cheap Turtle Beach Rivera (30.00 bucks). Just stuck it in the slot and Ubuntu 9.04 recognized it and it worked right away.  Good Luck

---

### Post by m10sang10 on 2009-05-23
> **m10sang10 said:**
> Hi Gentlemen;
My OS is Ubuntu 9.04 and my problem is about  Creative  Sound Blaster X-Fi card, after some time without sounds I was trying to do it work, well at the end I got it working, but...only Movie Player work OK, Rhythmbox emits sounds mixed with 'shrieks', VLC simply doesn't emit any sound by speakers, the same way does mozilla firefox.

Really I don't know which could be the problem, therefore 	
I ask you to help me, please.

Thanks in advance 
Mark.

PD: I Attach  photo of Preferences->Sound and another details.

I am sending 'another details'(I hope)

---

### Post by m10sang10 on 2009-05-23
Thanks Noah_Kapiolani

-------------------

anothers details:

01:00.1 Audio device: ATI Technologies Inc HD48x0 audio 
	Subsystem: ATI Technologies Inc HD48x0 audio 
	Flags: bus master, fast devsel, latency 0, IRQ 17 
	Memory at f7dfc000 (64-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 
	Kernel driver in use: HDA Intel 
	Kernel modules: snd-hda-intel 


05:02.0 Multimedia audio controller: Creative Labs SB X-Fi 
	Subsystem: Creative Labs Device 0021 
	Flags: bus master, medium devsel, latency 64, IRQ 18 
	I/O ports at ec00 [size=32] 
	Memory at fea00000 (64-bit, non-prefetchable) [size=2M] 
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M] 
	Capabilities: <access denied> 
	Kernel driver in use: CTALSA 
	Kernel modules: ctxfi 




**** List of PLAYBACK Hardware Devices **** 
card 0: XFi [Creative X-Fi], device 0: X-Fi 20k1 [WaveOut/WaveIn] 
  Subdevices: 8/8 
  Subdevice #0: subdevice #0 
  Subdevice #1: subdevice #1 
  Subdevice #2: subdevice #2 
  Subdevice #3: subdevice #3 
  Subdevice #4: subdevice #4 
  Subdevice #5: subdevice #5 
  Subdevice #6: subdevice #6 
  Subdevice #7: subdevice #7 
card 1: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0

---

### Post by m10sang10 on 2009-05-24
Help?

---

### Post by mountain_goat on 2009-05-24
Hello Mark,
Yes, Creative audio cards have been somewhat a problem, both with microsoft windows and with linux systems.
I have a X-Fi music card installed and have installed the latest creative driver as detailed in thread 870001 by Nullhead.
As yet you will not be able to have multi channel sound or use external I/O, so there are limitations still.
But the driver does work well now. Set your system sound preferences to use autodetect or ALSA, not OSS.
View thread [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)
Hope this helps

---

### Post by m10sang10 on 2009-05-24
.
'But the driver does work well now. Set your system sound preferences to use autodetect or ALSA, not OSS.
View thread [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)
Hope this helps[/QUOTE]'

Thanks mountain_goat
I think that I can live with no multi channels, but is it possible to use VCL as default(or simply that it work)?  and if so, how could I do it?


The problem is that 'movie player' is the only one that works appropriately, but it has problems when playing films.

Thank in advance.

---

### Post by m10sang10 on 2009-05-25
Toc, toc 
Is somebody there?

---

### Post by Mastermind501235 on 2009-07-13
Well, until I've build my new system i used ESS sound card and it was OK.
New system config:
MB: GA-M57SLI-S4 (nForce 570 SLI)
CPU: AMD Athlon64 X2 6000+
RAM: 4 GB (800 Mhz DDR II)
HDD: 400 GB SATA Seagate
Video: NV GF 9800 GT
Sound: Creative Labs Sound Blaster X-Fi Extreme Audio

I used HDD from the old system, everything worked except the sound.
So I've installed 64-bit Ubuntu 8.10. and it had sound card support right after installtion. Then I've updated to the 9.04 and sound card support disappeared. I've used dmesg command and it stated that I don't have drivers for the card. After this I've downloaded 9.04 ISO. Suprisingly the system recognized my card from LiveCD. So I've reinstalled the system from LiveCD and now it sounds. Problem solved.

---

### Post by xenogia on 2009-07-13
Supposedly there are new open source ALSA drivers in the work for the X-Fi card and the Auzentech line thank god.  From what I have heard from the grapevine they maybe in the next kernel.

Check this out
[http://ubuntuforums.org/showthread.php?t=1211151](http://ubuntuforums.org/showthread.php?t=1211151)

---

### Post by dr_jaymahdi on 2009-07-19
I am wondering if this is for the Sound Blaster X-Fi PCI or PCI-E version?

---

