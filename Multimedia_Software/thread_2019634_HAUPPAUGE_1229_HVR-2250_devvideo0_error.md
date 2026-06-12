---
title: "HAUPPAUGE 1229 HVR-2250 /dev/video0 error?"
date: 2012-07-07
forum: Multimedia Software
---

### Post by jessicasix on 2012-07-07
Hello, I'm new to all this.  I just installed Ubuntu 12.04 yesterday and everything went well.
I wanted to use a TV Card I bought in 2009:  HAUPPAUGE 1229 HVR-2250.
It works in Windows XP, but not in Ubuntu.
I tried installing a couple of TV applications:
   TVtime
   MeTV

When I click on TVtime, I get a blue box with some info.
  No signal
  No video source
  No such file or directory
      Cannot open capture device /dev/video0

I found a post here about trying to make MythTV work, which appears to start out describing how to make the TV card work, so I used those instructions:
    [http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

After the "lspci" step, I did see the SAA7164.  In fact, here's everything I saw:

===
00:00.0 Host bridge: NVIDIA Corporation Device 0800 (rev b1)
00:00.1 RAM memory: NVIDIA Corporation Device 0808 (rev a1)
00:00.2 RAM memory: NVIDIA Corporation Device 0809 (rev a1)
00:00.3 RAM memory: NVIDIA Corporation Device 080a (rev a1)
00:00.4 RAM memory: NVIDIA Corporation Device 080b (rev a1)
00:00.5 RAM memory: NVIDIA Corporation Device 080c (rev b1)
00:00.6 RAM memory: NVIDIA Corporation Device 080d (rev a1)
00:00.7 RAM memory: NVIDIA Corporation Device 080e (rev a1)
00:01.0 RAM memory: NVIDIA Corporation Device 080f (rev a1)
00:01.1 RAM memory: NVIDIA Corporation Device 0810 (rev a1)
00:01.2 RAM memory: NVIDIA Corporation Device 0811 (rev a1)
00:01.3 RAM memory: NVIDIA Corporation Device 0812 (rev a1)
00:01.4 RAM memory: NVIDIA Corporation Device 0813 (rev a1)
00:01.5 RAM memory: NVIDIA Corporation Device 0814 (rev a1)
00:01.6 RAM memory: NVIDIA Corporation Device 081a (rev a1)
00:01.7 RAM memory: NVIDIA Corporation Device 080e (rev a1)
00:02.0 PCI bridge: NVIDIA Corporation Device 0815 (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation Device 0817 (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP55 SMBus (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: NVIDIA Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: NVIDIA Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: NVIDIA Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a3)
00:15.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 VGA compatible controller: NVIDIA Corporation GT200 [GeForce GTX 260] (rev a1)
02:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
03:07.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
03:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
===

I then rebooted, but still have the same error.

If I run MeTV, I get a box:
 "Your ME TV database is too old to use this version of MeTV.  Would you like to clear the Me TV database?  All of your channels, EPG events and scheduled recordings will be deleted.  If you just upgraded Me TV then this is probably what you want to do.    The Me TV database is located at ~/.local/share/me-tv.db"
   [quit]     [Delete my old Me TV data!]

If I click on the 2nd button, it just hangs and does nothing.

If anyone has any other info or documentation, I'd love to hear from you.

Thanks!

---

### Post by interglossa on 2012-07-08
I am using the HVR-950Q but I have the same experiences with me-tv.  With tvtime I can find the device with -d /dev/video1 but I also get no signal.

Are there any threads giving some instructions on these applications?  it's too bad to have to fall back on windows....

---

### Post by jessicasix on 2012-07-08
Ok, after doing a little more research, I think the reason TVtime won't work is because it's  for an "analog" device, and that /dev/video0 has no meaning to the new digital HAuppauge card.

Reading this link further, regarding MythTV, it mentions how to install it using the MythTV Backend Setup.  However, I tried this and fond it very very very painful and difficult to use/understand.  When I run it, I get a big GUI, and the mouse/pointer disappears.  I really don't know what I'm supposed to do.
I just thought by now people would be using digital TV cards since analog has been a thing of the past for years now.  I'm surprised it doesn't just WORK, and it's one of the reasons I picked Ubuntu since I heard things work well.

I'm not sure what type of device MeTV wants.

If anyone has some configs or a good document describing step-by-step how to make this work, I'd really appreciate hearing from you!

Thanks!

---

