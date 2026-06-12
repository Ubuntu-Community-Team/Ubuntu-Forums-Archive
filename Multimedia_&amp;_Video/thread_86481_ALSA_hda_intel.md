---
title: "ALSA hda intel"
date: 2005-11-05
forum: Multimedia &amp; Video
---

### Post by commodore on 2005-11-05
[https://wiki.ubuntu.com//HdaIntelSoundHowto](https://wiki.ubuntu.com//HdaIntelSoundHowto)

It doesn't work. There aren't linux-headers-2.6.10-5-686

---

### Post by Remmelas on 2005-11-05
[QUOTE=commodore][https://wiki.ubuntu.com//HdaIntelSoundHowto](https://wiki.ubuntu.com//HdaIntelSoundHowto)

It doesn't work. There aren't linux-headers-2.6.10-5-686[/QUOTE]
you need to use the linux-headers package that matches your running kernel, instead of what they wrote on that article.  For example, the kernel i run is linux-2.6.12-9-k7 so I would have to use linux-headers-2.6.12-9-k7, you can see what kernel you are running easily by either watching at boot, or, ```
sudo apt-get install linuxinfo
``` and then execute ```
linuxinfo
```
you should get output similar to ```
Linux thazz 2.6.12-9-k7 #1 Mon Oct 10 13:47:52 BST 2005
One AMD Unknown 1540MHz processor, 3063.80 total bogomips, 511M RAM
System library 2.3.5

``` replace the 2.6.10-5.686 with what ever the kernel version output is from linuxinfo.

---

### Post by kairu0 on 2005-11-05
I have an ALSA hda intel and it worked out of the box in Breezy.

Before you follow that howto, I suggest checking your volume to see if it's probably muted by default. Download alsamixergui or any other alsa mixer and run it to unmute the main channel.

---

### Post by commodore on 2005-11-06
Which one is the main channel? There's so many stuff there. I don't know anything about sound. I dunno what do I have to mute and what do I have to unmute.

EDIT: I fiddled with all kinds of stuff there and finally got it to work! Thank you kairu0! You don't know how much you've helped me! You rule!

---

### Post by commodore on 2005-11-06
There's still one problem. There's some sough (don't know if it's the right word) in the headphones. I can live with it, but I would be very happy If I'd get it fixed.

---

### Post by kairu0 on 2005-11-06
[QUOTE=commodore]Which one is the main channel?[/QUOTE]

For me, it was "Front." It probably depends on your laptop, though.

---

### Post by kairu0 on 2005-11-06
[QUOTE=commodore]There's still one problem. There's some sough (don't know if it's the right word) in the headphones.[/QUOTE]

You mean "static" or "noise"? I have noise coming from my speakers. It's caused by an IRQ conflict, and I haven't resolved it yet.

---

### Post by iNerdSure on 2005-11-07
Hi, I have a similar SILENT. NO SOUND! problem. Have followed the steps in the solution suggested.

Output fo linuxinfo:
> ins@inerdsure:~$ linuxinfo
Linux sgc9711 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005
One Intel Pentium M 800MHz processor, 1581.05 total bogomips, 502M RAM
System library 2.3.5
ins@inerdsure:~$

How to:
> .. replace the 2.6.10-5.686 with what ever the kernel version output is from linuxinfo..?

Any steps I might have missed? Please help. Many thanks.

---

### Post by commodore on 2005-11-07
Did you try alsamixer? Go to synaptic> search for alsamixergui> install it> type alsamixergui in terminal> try and set on/off all kinds of channels there while you're playing music.

---

### Post by iNerdSure on 2005-11-07
Thanks, Commodore. Installed alsamixergui from Synaptics. Ran alsamixer in Terminal. Manipulated the controls. No success. Still SILENCE - NO SOUND. 

Any other troubleshooting or diagnostics I could use?

---

### Post by Kallewoof on 2005-11-10
Same problem here. I've got an Amilo Pro V2040, installed Ubuntu Breezy on it yesterday. Everything works perfectly except the sound. 
I've opened I think 3 or 4 different alsa mixers and set the volume for everything up to max, and unmuted everything (including "front") to no avail.

-Kalle.

---

### Post by kairu0 on 2005-11-20
[QUOTE=Kallewoof]Same problem here. I've got an Amilo Pro V2040, installed Ubuntu Breezy on it yesterday. Everything works perfectly except the sound. 
I've opened I think 3 or 4 different alsa mixers and set the volume for everything up to max, and unmuted everything (including "front") to no avail.

-Kalle.[/QUOTE]

Is your Amilo card getting detected? Read the output of dmesg to see that it is.

---

### Post by Kallewoof on 2005-11-20
Sorry, I was unclear. Amilo Pro is the name of the laptop brand (Fujitsu-Siemens). The soundcard is the HDA Intel. And yep, it all detects and such, but there's no sound.

-Kalle.

---

### Post by Kallewoof on 2005-11-21
Now that was odd.

I booted into Ubuntu, came to the login screen, and then:
- hit Ctrl+Alt+F2,
- logged in (as my regular user)
- cd'd into a dir where I had some mp3's
- did "mplayer foo.mp3"
- got sound! but it had a high-pitched noise-thing in the background.
- hit Alt+F3
- logged in (as my regular user)
- did "alsamixer"
- and as I hit the down-arrow once, to decrease the volume on the "headphones" which was the leftmost one, it all went silent.

Any ideas what might cause that?

-Kalle.

---

### Post by Kallewoof on 2005-11-22
I just checked the latest alsa release (Nov 16th; 1.0.10). It has a buttload of hda intel fixes. 

Anyone know approximately how much time Ubuntu takes to add a new alsa version into their distribution?

-Kalle.

---

### Post by luxir on 2005-11-22
I have an ASUS A3E laptop with on board Intel hda. Been trying desperately to get some sound out of it. Tonight, I removed alsa-source package (with the intention to replace it by a newer version) and <surprise> I have sound. 

Being unaware of the inner workings of alsa, I cannot explain why removing a source package would enable sound, but just to be certain, I re-installed alsa-source: sound was gone. 

So I removed it again and am enjoying my music without alsa-source! Perhaps wirth a try?

---

### Post by Kallewoof on 2005-11-23
I didn't actually have alsa-source installed so I installed it. No difference. Removed it. No difference. Thanks for the tip though!

-Kalle.

---

### Post by Robocoastie on 2005-11-23
similar situation except its only affecting my tv card and games. Anything else for sound works great - music, desktop alerts, etc...

I did sudo apt-cache search alsa
and installed some things I didn't have thinking those might do the trick but no luck. alsamixer shows the "line in" as not adjustable which I suspect is the problem but how to fix this? Also, I don't know if this is related or not but if I go to the Multimedia System Selector no matter what I choose for "Default Source Input" it crashes when I click on test.

HDA Intel (which is a SigmaTel STAC9221 A1 chipset.

Ubuntu 5.10 64bit with 32bit on another partition.
Dell Dimension 5100 w/ P4-HT-EM64T 2.8GHz
1.5GB RAM

linuxinfo output:
```

Linux talviak05 2.6.12-10-amd64-xeon #1 SMP Fri Nov 18 12:35:54 UTC 2005
Two Intel Pentium 4 2793MHz processors, 11108.35 total bogomips, 1534M RAM
System library 2.3.5
rob@talviak05:~$
```

Attached is my dmsg output and I noticed this in it but I don't know what to do about it:

```

[   64.260406] Linux video capture interface: v1.00
[   64.325151] cx2388x v4l2 driver version 0.0.4 loaded
[   64.326212] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 18 (level, low) -> IRQ  18
[   64.326260] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   64.326263] cx88[0]: try to pick one of the existing card configs via
[   64.326264] cx88[0]: card=<n> insmod option.  Updating to the latest
[   64.326266] cx88[0]: version might help as well.
[   64.326268] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   64.326271] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   64.326274] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   64.326276] cx88[0]:    card=2 -> GDI Black Gold
[   64.326278] cx88[0]:    card=3 -> PixelView
[   64.326280] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   64.326282] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   64.326284] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   64.326286] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   64.326288] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   64.326291] cx88[0]:    card=9 -> Leadtek PVR 2000
[   64.326293] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   64.326295] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   64.326297] cx88[0]:    card=12 -> ASUS PVR-416
[   64.326299] cx88[0]:    card=13 -> MSI TV-@nywhere
[   64.326302] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   64.326304] cx88[0]:    card=15 -> DVICO FusionHDTV DVB-T1
[   64.326306] cx88[0]:    card=16 -> KWorld LTV883RF
[   64.326308] cx88[0]:    card=17 -> DViCO - FusionHDTV 3 Gold
[   64.326311] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   64.326313] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   64.326315] cx88[0]:    card=20 -> Provideo PV259
[   64.326317] cx88[0]:    card=21 -> DVICO FusionHDTV DVB-T Plus
[   64.326320] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   64.326322] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   64.326324] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   64.326327] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Cen ter (MEC)
[   64.326329] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   64.326333] cx88[0]: subsystem: 1043:4820, board: UNKNOWN/GENERIC [card=0,aut odetected]
[   64.485711] cx88[0]/0: found at 0000:03:02.0, rev: 3, irq: 18, latency: 64, m mio: 0xee000000
[   64.497166] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[   64.534646] cx88[0]/0: registered device video0 [v4l2]
[   64.536485] cx88[0]/0: registered device vbi0
```

My particular tv card is an Asus tv880 which lspci reports as a Winfast TV2000 XP by Conexant cx8800. I've searched around on various video4linux sites but there's so many of those sites that it hurts one's head trying to sort out relevant ones.

grrrr file too big again, well the quoted above is probably the relevant part anyway. I didn't see anything in it related to the soundcard either yet I have sound anyway with everything but tv card and games.

---

### Post by commodore on 2005-12-05
I had to reinstall Ubuntu (again) and now I can't get it to work again. I tried installing the stuff and everything. I know alsamixer should help, but xmms says couldn't open audio. If it could just open it and there would be no sound I could use alsamixer. There's no azx ([https://wiki.ubuntu.com//HdaIntelSoundHowto](https://wiki.ubuntu.com//HdaIntelSoundHowto)) when configuring alsa.

---

### Post by commodore on 2005-12-06
I fixed it. There was some problem with xmms.

---

### Post by Robocoastie on 2005-12-09
I have a similar issue so I'm using this thread rather than make a new one.

Rig: Dell Dimension 5100
WinXP MCE2005/Ubuntu 5.10 32bit (also tried 64bit same issue)
Issues:
1) no sound in *some* games such as Tuxracer and the bubble pop game whatever its called. I did get sound in Enemy Territory after following the wiki's instructions. Distorted sound in quake4-demo
Windows reports my sound chipset as a "SigmaTel". But in Ubuntu the volume control (alsamixergui) says its an hda intel but lists it and SigmaTel as available choices in the device setting.

2) front panel headphone and microphone jacks don't work.

The games not working correctly isn't really a big deal to me because I've mostly given up on PC gaming and use my xbox more but it does indicate a possibly larger problem with the sound system. Item 2 is a BIG issue because I use skype a lot so prefer to use my headset when I'm using that.

thanks,

Rob

---

### Post by LiquidIQ on 2005-12-13
For the front panel headphone and mic not working, was there an Audigy card in there at any time? If so, check and see if there is a ribbon cable (beyond the grey one that looks like an IDE cable) with a white connector and unplug that from the front panel.

There is also bug fixes in ALSA 1.0.10 but it seems like it's a pain to install on Ubuntu... I haven't personally tried it yet.

Oh, also, do the front panel in/out work in Windows?

---

### Post by Robocoastie on 2005-12-13
Aye they work in windows just fine. I suspect its driver related because there's a special SigmaTel driver for the sound system in windows. I don't know if there was an Audigy in it, I doubt it though. I got the system (was a sweet deal too) in Dell's refurbished section. Imagine my pleasent surprise when I discovered the CPU was actually an EM64T one!

edit/add:

I just figured out a way to get sound in those games that were silent before from another thread. #killall esd
once I did that I had sound in tuxracer.

edit/add 2:

WOOTS!!! Got it all working! I followed this tip at the wiki site: [https://wiki.ubuntu.com/HdaIntelSoundHowto?highlight=%28hda%29%7C%28intel%29](https://wiki.ubuntu.com/HdaIntelSoundHowto?highlight=%28hda%29%7C%28intel%29)  and installed the latest stable ALSA version (.10) and after compiling it all (and having to apt-get ncurses-dev ### in order to do so) and a little minor tweaking in the mixer after running alsaconf it was all working! It added a lot more features than the default version in 5.10 Ubuntu such as settings for the mic, headphones, digital plug etc...

---

### Post by LiquidIQ on 2005-12-14
Awesome! Glad to hear it :)

Hmmm.... 1.0.10 has more fixes than I though, hah. It would be nice if someone made a .deb package for 1.0.10 though.

---

