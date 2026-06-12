---
title: "Poor Sound in Fullscreen Flash Video Lenovo T60"
date: 2011-01-12
forum: Multimedia Software
---

### Post by kernelles on 2011-01-12
Sound is fine in flash video, but gets garbled in fullscreen.

Another problem I'm having is that when I turn the volume past 60% using the sound applet on the panel, it gets very distorted. If I open sound preferences, I notice it is in the "amplified" zone at this point, so I have to keep it in the "unamplified" zone, but then it's not loud enough.

Here is my soundcard info:

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio C
ontroller (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at ee400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

More info on my setup: output on my system from Alsa: [http://www.alsa-project.org/db/?f=d6767e7d7f2aff633cdbd0b04166b53cdd874ae8](http://www.alsa-project.org/db/?f=d6767e7d7f2aff633cdbd0b04166b53cdd874ae8)

Thanks!
Les.

---

### Post by tommcd on 2011-01-12
Try running **alsamixer** from the terminal and either mute or turn down the level(s) (there may be more than one) for the computer's microphone. When I installed Lubuntu 10.10 on my desktop I had an annoying humming sound if I turned up the volume on my speakers past half way. Turning down the microphone level in alsamixer fixed the problem. I don't even have a microphone connected to my computer; but it was still giving feedback to the sound coming through my speakers somehow.

---

### Post by kernelles on 2011-01-16
Thanks, that helped. But this means I can't put my volume past 40%. Is there any other solution?

---

### Post by mjohns55 on 2011-09-04
I also have a ThinkPad T60 having the exact same problem:  Flash audio is fine when in standard window, BUT, when going to full screen mode the audio becomes 'garbled'.  I could describe it like this... if there was a video of someone holding a solid "Ahhhhhh" sound, when in full screen mode, it would sound like they were gargling mouthwash (hence, the 'garbled' descriptor)

I've used every release of Ubuntu for the last 3 yrs, and this issue has only started on the 11.04 Natty release :(

If there is no resolution to be had, then I think my plan will be to wait for the 11.10 release and just do a clean install.  If this problem persists, then I don't know what to do... :'(

Did anyone find any resolution to this garbling issue anywhere else?

---

### Post by nicktr on 2011-09-24
Same problem here.  I also found this started with 11.04.

I have several T60s and the problem (in my experience) is confined to those with ATI graphics.  Both X1300 and X1400 seem to have the same problem.  The T60 with the Intel 950 does not seem to have this problem.

Further observations:

I also notice that as well as the garbled audio, playback speed also drops slightly as well.  The suggestions from elsewhere on the net to disable hardware acceleration in the Flash settings makes no difference.

I only experience this issue with Flash fullscreen playback from within a browser (same issue on both Firefox and Chrome).  Full-screen playback of .flv files in Movie Player is fine, even with HD material.

Installing the ATI proprietary fglrx makes no difference.  (Though I only tried the version from the Ubuntu repository installed using Synaptic - not tried direct from ATI).

This issue seems to be raise in many posts but I've not found a solution that works.  Anyone else able to confirm the symptoms or found a solution?

---

### Post by gerardodelariva on 2011-10-02
I've got exactly the same problem. Everything works perfect here except for fullscreen flash audio (as in youtube videos).

Fullscreen anything else is flawless.

---

### Post by dave2001 on 2011-10-04
Here's another T60 owner with the same problem. And yes I DO have an ati x1400 graphics card in it. Just did a fresh install of 11.04 and I thought they finally fixed all the problems with the radeon driver (as this card is no longer supported under fglrx, radeon's really the best option). *sigh* oh well, I suppose it was too good to be true. I'll try some of my "fixes" for the graphics issues in older ubuntu versions and see if they help this problem. Has anyone reported this as a bug already?

---

### Post by dave2001 on 2011-10-04
Ok, I've got some verification that this problem is related to the graphics driver somehow. Booting with a kernel line option of "radeon.modeset=0" (which should disable kernel mode setting for the radeon driver) fixes the sound distortion in full-screen flash video. Of course it also reintroduces other problems like massive screen tearing and desktop graphic glitches. I'm still a loooog way off from being a linux expert, so I'm hoping this new info gives someone else ideas on how to fix this issue without disabling KMS.

---

### Post by dave2001 on 2011-10-05
For anyone else suffering from this problem, I've got a very limited and not wholly satisfactory solution.

There is an addon for firefox called "FlashVideoReplacer"

It allows you to easily configure your streaming flash video's to be sent out to an external standalone player (I'm using VLC). The standalone VLC window pops up when you open a page containing a flash video. Plays fine in fullscreen, no audio distortion. Tested on several youtube video's.

Unfortunately it this addon doesn't work on many sites.

---

### Post by kernelles on 2011-10-05
> **dave2001 said:**
> For anyone else suffering from this problem, I've got a very limited and not wholly satisfactory solution.

There is an addon for firefox called "FlashVideoReplacer"

It allows you to easily configure your streaming flash video's to be sent out to an external standalone player (I'm using VLC). The standalone VLC window pops up when you open a page containing a flash video. Plays fine in fullscreen, no audio distortion. Tested on several youtube video's.

Unfortunately it this addon doesn't work on many sites.

I have since installed the 11.10 beta on the same machine, and the problem is solved. Until I did that, nothing worked. The full release of 11.10 happens on Oct. 13, so I would just wait a couple weeks and do a fresh install. Hope it works for you, too!

---

### Post by dave2001 on 2011-10-05
> **kernelles said:**
> I have since installed the 11.10 beta on the same machine, and the problem is solved.

Great news! Thanks for the update kernelles! I usually wait a while before moving to the new version, but I believe I'll be installing 11.10 as soon as the final release hits.

---

### Post by mag88 on 2011-10-13
You may laugh, but for me worked. The cause for your problem is your proprietary video driver. I don't know the mechanism, but it seems that's why.:p
I had the same problem (I do not own a T60, but my PC has an ATI based video card) until I installed the ATI opensource driver and followed the instructions listed [here]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch"). Worked for me.
Now I enjoy flash videos and movies having no problem.:popcorn:


Cheers

---

### Post by dave2001 on 2011-10-13
> **mag88 said:**
> The cause for your problem is your proprietary video driver. 
 
Thanks for the suggestion, unfortunately this fix will not work for me. My Thinkpad T60 has an ATI x1400 video card, which is no longer supported by the proprietary fglrx driver, which means I never installed it. The open source radeon driver is the only one I've used (at least for the last several version of ubuntu).

---

### Post by dave2001 on 2011-10-13
> **kernelles said:**
> I have since installed the 11.10 beta on the same machine, and the problem is solved. Until I did that, nothing worked. The full release of 11.10 happens on Oct. 13, so I would just wait a couple weeks and do a fresh install. Hope it works for you, too!


BAD NEWS! I just installed the final release of 11.10 Oneiric Ocelot on my Thinkpad T60 model 2637-UN6 and the problem persists. I wonder why this fixed the issue for you kernelles?

---

### Post by kolinab on 2011-10-16
I'm searching for a solution to this problem too, although I'm not sure it's exactly related to this flash issue described above or not. I filed a report at:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/873370](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/873370)

I'm also searching around now for other similar reports. 

My t60 sound is perfect for a while, until I start doing a few things, playing sound (from Banshee for example) in the background while I open a new application or something, then sound becomes garbled. Strange. 

Sound was perfect in 11.04 and this is a new problem for me under 11.10

---

### Post by dave2001 on 2011-10-17
My solution: reinstall 10.04 LTS

I just really was not happy with a number of things in Oneiric and Natty, the full screen flash glitch among them.

---

### Post by ak2766 on 2011-11-20
I just upgraded to Oneiric Ocelot (64bit) and I'm still experiencing the 'garbled' sound in full screen video - Firefox and Chromium.  Audio and Video in all other applications is working fine - just flashplayer in full screen browser windows...  I'm running the latest Flashplayer version 11.1.102.55 as reported by [http://www.adobe.com/software/flash/about/]("http://www.adobe.com/software/flash/about/")

My system is an IBM Thinkpad Z61m with the now infamous video card:
```

lspci -vvv -s 1:0.0
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 202a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 46
	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 2000 [size=256]
	Region 2: Memory at ee000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at ee020000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0300c  Data: 41a9
	Kernel driver in use: radeon
	Kernel modules: radeon

```

The saga continues...

:(

---

### Post by mike75bug on 2012-05-01
***** Nevermind.  I looked and it is just using the fallback driver.  It did fix the audio problem in fullscreen flash video.  I am just using it to watch Hulu and host internal Wordpress sites for testing, so the video is not getting hammered like a gaming machine.

If fixed it on my Lenovo T60 today.

I downloaded the new ATI Catalyst driver and installed it (Just posted 4/25/2012).  After installing though, I went to use aticonfig and it said there are no supported cards.

BUT, I don't have the audio problem anymore in fullscreen flash.

[http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run)

---

### Post by khora on 2013-02-21
Installing official Chrome, which has its own flash support, solved fullscreen flash sound problem for me. I have Lubuntu 12.10 on a T60 and ATI X1400.

---

### Post by wildmanne39 on 2013-02-21
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

