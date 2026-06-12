---
title: "old alsa with new hardware"
date: 2012-12-04
forum: Mythbuntu
---

### Post by mookie60 on 2012-12-04
Just put together a first-time-build HTPC.   Rather than installing Mythbuntu 12.04 (saving that for a new SSD), I wussied-out and just installed the drives (one for the OS and one for recordings) from my old Mythbuntu 10.04 system.   

Once the video driver situation got squared away, things seem to work well, mostly.  Of course ALSA still thinks it's on the old hardware.  The frontend plays recordings from the backend but without sound.   I tried to re-scan the audio (from within Myth setup), but it errors and finds no hardware.

I tried running Alsamixergui to find the new sound hardware (integrated Intel), but it will not start, giving me this error:

  alsamixer: function snd_ctl_open failed for default: no such file or directory

I never had a sound issue with the old system.  How do I "reset" ALSA to use the new hardware?

Thanks

---

### Post by nickrout on 2012-12-04
> **mookie60 said:**
> Just put together a first-time-build HTPC.   Rather than installing Mythbuntu 12.04 (saving that for a new SSD), I wussied-out and just installed the drives (one for the OS and one for recordings) from my old Mythbuntu 10.04 system.   

Once the video driver situation got squared away, things seem to work well, mostly.  Of course ALSA still thinks it's on the old hardware.  The frontend plays recordings from the backend but without sound.   I tried to re-scan the audio (from within Myth setup), but it errors and finds no hardware.

I tried running Alsamixergui to find the new sound hardware (integrated Intel), but it will not start, giving me this error:

  alsamixer: function snd_ctl_open failed for default: no such file or directory

I never had a sound issue with the old system.  How do I "reset" ALSA to use the new hardware?

ThanksRemove /etc/asound.conf and ~/.asoundrc (backing up if you think you may need them).

Other than those config files the kernel probes and finds your sound cards on boot. What is the output of lspci and ls -l /proc/asound/

---

### Post by mookie60 on 2012-12-04
Nick,

Thanks for the help.

I could not find: /etc/asound.conf and ~/.asoundrc 

But I did find a /etc/ld.so.conf.d/libasound2.conf  It seemed close, so I renamed it with a .bak  - reboot - didn't help.  Then put it back the way it was.


ls -l /proc/asound/  returned:

  ls: cannot access /proc/asound/: No such file or directory

lspci:

00:00.0 Host bridge: Intel Corporation Device 0150 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0162 (rev 09)
00:14.0 USB Controller: Intel Corporation Device 1e31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 1e3a (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 1e2d (rev 04)
00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 1e10 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Device 1e18 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1d.0 USB Controller: Intel Corporation Device 1e26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1e4a (rev 04)
00:1f.2 SATA controller: Intel Corporation Device 1e02 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 1e22 (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 PCI bridge: Device 1b21:1080 (rev 03)
04:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

---

### Post by nickrout on 2012-12-05
It appears that no sound modules are loaded because your current kernel does not recognise and support the sound card.

Try booting a live cd of a recent distro like mythbuntu 12.04 and see if you get sound.

Googling "Audio device: Intel Corporation Device 1e20" produces some results for people with similar problems.

---

### Post by mookie60 on 2012-12-05
I've already booted into 12.04, and yes the sound worked.   So I guess I'm stuck doing the upgrade.   Should never have assumed integrated sound wouldn't be a problem

I hesitated to move to 12.04 in the first place because I'm zero for 3, when it comes to successful backup/restores of the existing database.

Thank you very much for the help.

---

