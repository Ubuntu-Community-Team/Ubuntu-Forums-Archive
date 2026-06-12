---
title: "SD QAM on a &quot;low-end&quot; processor"
date: 2011-07-05
forum: Mythbuntu
---

### Post by gabrielbenjamin on 2011-07-05
My cable provider (WideOpenWest) is changing its basic lineup to SD clear QAM, and I'm in the process of finding a PCI digital tuner card for the family Mythbuntu box of several years. The Hauppauge HVR-1150 looks pretty much perfect for our needs, except in the CPU department. The system requirements say 2.4 GHz, and we have a Sempron 3500+ that I don't feel like overclocking from 2 GHz.

Here's the question: Those requirements are for HD, which we're never going to upgrade to. How much less CPU power can we get away with for SD capture? Or is it just as CPU intensive?

Secondarily I would like to know if Mythbuntu 9.04 is sufficient for using a QAM tuner.

---

### Post by nickrout on 2011-07-05
You do not need anything much in terms of CPU power to record a digital stream. The system pretty well dumps the stream from the tuner card straight to disk.

Playback is another matter, but your CPU should handle that fine.

I would however upgrade to mythtv 0.24-fixes, which may mean you need to go to a more recent version of ubuntu.

---

### Post by agamotto on 2011-07-05
For SD, you should be fine.  Just make sure in the recording profile to make sure that the 'profile' is set to record everything at 720x480 resolution, which is the NTSC (analog) overscan limit, if memory serves.  This should ensure a 'full' picture that isn't squished or letter-boxed to death.

The only suggestion I have based on your lower-spec system is that you not try to record two HD streams/programs at the same time... this will probably bog your system down badly, if not crash it.

In playback, go for the best video card your budget allows.  Many excellent cards can be had for under $100.  The nVidia ones even offer a feature called VDPAU that takes a lot of stress of the CPU in terms of spitting HD content out to a telly.

Version 9.04 would be fine, but I would recommend 10.04 LTS for reliability.  You will have to poll other people on this fourm about 11.04, as I have had no luck with it in any of its flavors.

---

### Post by klc5555 on 2011-07-06
> **gabrielbenjamin said:**
> My cable provider (WideOpenWest) is changing its basic lineup to SD clear QAM, and I'm in the process of finding a PCI digital tuner card for the family Mythbuntu box of several years. The Hauppauge HVR-1150 looks pretty much perfect for our needs, except in the CPU department. The system requirements say 2.4 GHz, and we have a Sempron 3500+ that I don't feel like overclocking from 2 GHz.

Here's the question: Those requirements are for HD, which we're never going to upgrade to. How much less CPU power can we get away with for SD capture? Or is it just as CPU intensive?

Secondarily I would like to know if Mythbuntu 9.04 is sufficient for using a QAM tuner.

Oddly enough, until about a month ago I had a machine with an old AMD Athlon 2400+ motherboard that worked perfectly for SD (and analog) recording (and display) with 9.04/mythtv 0.21.  You'll do fine.

---

### Post by movieman on 2011-07-08
> **klc5555 said:**
> Oddly enough, until about a month ago I had a machine with an old AMD Athlon 2400+ motherboard that worked perfectly for SD (and analog) recording (and display) with 9.04/mythtv 0.21.  You'll do fine.

Until last week I was using a pair of dual-core Atoms (one with an Ion chipset for HD playback). I wouldn't expect the CPU to make much difference for recording, though one of the reasons I upgraded the backend system was that transcoding on the Atom was slow.

---

### Post by gabrielbenjamin on 2011-07-31
Thank you all for your help so far. I have a new problem, however: i can't get MythTV to talk to the card now that it's installed! I have to admit I don't know for sure if I installed the drivers for it, but I don't know which ones they are. Even having passed that hurdle, I'm not sure what type of tuner it is, and there's nothing about it in the MythTV wiki. Am I lucky enough that someone here has any experience with/knowledge about the HVR-1150?

---

### Post by klc5555 on 2011-07-31
I don't use the card, but it's listed as a standard saa7134 device here: [http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.saa7134](http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.saa7134)

It would appear that the saa7134 driver should be autodetecting the card as card=155 according to the cardlist; running

dmesg | grep saa

or similar from a prompt should produce the information as to whether the card is being properly autodetected.

If the card is not properly autodetected, so that the incorrect card parameter is being passed to the card according to the dmesg output, sometimes the driver can be forced to load the correct parameter by composing a specialized .conf file for your card under /etc/modprobe.d whose single line would look something like:

options saa7134 card=155

Sometimes, however, the saa7134 driver simply ignores module parameters passed to it in a .conf file. In this case, the saa7134 needs to be blacklisted and then loaded separately with a modprobe command that includes the needed card parameter, as described in Gentoo's wiki installation article on the saa7134 driver here: [http://en.gentoo-wiki.com/wiki/Saa7134](http://en.gentoo-wiki.com/wiki/Saa7134)

modprobe saa7134 card=155

The occasional difficulty in the latter approach in currentish Mythbuntu is that the modprobe command needs to load the card driver before startup initializes the mythtv backend.

---

