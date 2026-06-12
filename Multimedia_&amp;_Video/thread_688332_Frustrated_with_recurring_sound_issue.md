---
title: "Frustrated with recurring sound issue"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by KroniKlepto on 2008-02-05
I made the switch from XP to Ubuntu 6 months or so ago (have since upgraded to Gutsy), and have had this problem the entire time.  Still dual booted with XP to play Oblivion.  

The issue:

Sound stops working after ubuntu updates that require a restart and/or just rebooting (switching to xp.)  Sound works in XP.  Previously, I would reboot a few times, open the sound preferences, switch playback from autodetect to the 4th CA0106, hit Test, and get a solid beep... switch back to autodetect, reboot, and it would usually work.

After this morning's update, I still have no sound after the usual few reboots.  I attempted the steps in [this thread](http://ubuntuforums.org/showthread.php?t=205449), with no joy.

**lspci**
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 Mass storage controller: Silicon Image, Inc. Unknown device 3531 (rev 01)
05:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


**lspci | grep -i audio**
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
05:07.0 Multimedia audio controller: Creative Labs SB Audigy LS

**cat /proc/asound/cards**
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf9ef8000 irq 17
 1 [U0x46d0x8b2    ]: USB-Audio - USB Device 0x46d:0x8b2
                      USB Device 0x46d:0x8b2 at usb-0000:00:0b.0-4, full speed
 2 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xec00 irq 23

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I'm pretty much a linux n00b, but... to me, it looks like there are way too many sound card drivers loaded and possibly that the video cards are interfering?  I have no idea how to resolve this issue, so any help is appreciated.

---

### Post by buzzmandt on 2008-02-05
you seem to have 2 sound cards, an nvidia card and a creative labs.  I have the same set up.  What would happen to me is it would switch sometimes to the other sound card as the default sound out.  Figure out which one you are using and disable the otherone.  Or if sound stops working, switch your speakers to the other one and see if it's working, that's my bet.

someone should be able to tell you how to set one as default output if you need both sound cards to work.

---

### Post by KroniKlepto on 2008-02-05
Thanks, buzzmandt.  Before coffee this morning, I was looking at the nvidia card thinking that it was erroneously listing one or both of the geforce 7600's as sound cards.  A quick search revealed that ALC883 is the onboard sound card... disabled in BIOS and I'm good to go.  I think the reason that it didn't even occur to me was that I switched to Ubuntu after building this new box this past summer, and never bothered to disable onboard because I was too excited to be rid of windows.  Or, I'm retarded... either way, thanks again.

---

