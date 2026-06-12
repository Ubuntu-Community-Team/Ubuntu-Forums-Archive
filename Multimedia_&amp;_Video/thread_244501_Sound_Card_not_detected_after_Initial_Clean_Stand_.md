---
title: "Sound Card not detected after Initial Clean Stand Alone Install"
date: 2006-08-26
forum: Multimedia &amp; Video
---

### Post by StGeorge on 2006-08-26
Ubuntu installed well on my IBM Thinkpad 770X.

The problem now is that Ubuntu has not installed a sound driver.
I have checked ALSA Soundcard Matrix see:

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

but my manufacturer is not listed.

I have my original Drive backed up on part of my hard drive on a FAT32 drive.
Is there any way to use this?

Device Type Sound, video and game controllers
Device Name
Description Crystal PnP Audio System Control Registers
Manufacturer Crystal Semiconductor Corporation
Driver Provider Crystal Semiconductor
Driver Date 10-14-1998

Device Type Sound, video and game controllers
Device Name
Description Crystal PnP Audio System CODEC
Manufacturer Crystal Semiconductor Corporation
Driver Provider Crystal Semiconductor
Driver Date 10-14-1998

Device Type Sound, video and game controllers
Device Name
Description Crystal PnP Audio System MPU-401 Compatible
Manufacturer Crystal Semiconductor Corporation
Driver Provider Crystal Semiconductor
Driver Date 10-14-1998

Device Type Sound, video and game controllers
Device Name
Description Crystal SoundFusion(tm) PCI Audio Accelerator
Manufacturer Crystal Semiconductor Corporation
Driver Provider Crystal
Driver Date 2-12-1999

Device Type Sound, video and game controllers
Device Name
Description Crystal SoundFusion(tm) Virtual MPU-401
Manufacturer Crystal Semiconductor Corporation
Driver Provider Crystal
Driver Date 2-12-1999
Any ideas out there would be appreciated.

---

### Post by StGeorge on 2006-08-27
It seems that Crystal is part of Cirrus Logic as I have entries relating to a sound card in device manager.

See Screenshot.

Here is other info:

When I click on Volume Control, I get two messages: 

No volume control GStreamer plugins and/or devices found

Volume Control:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Below is from Device Manager:

Device Manager//Devices//CS4610/11 (CrystalClear SoundFusion Accelerator)

PCI TAB 

Vendor-Cirrus Logic

Product-CS 4610/11 [CrystalClear SoundFusion

OEM Vendor-IBM

OEM Product-CS4610 SoundFusion Audio

Advanced TAB on Screenshot

System//Preferences//Sound:
No default souncard visible

I hope this info will mean something to someone who knows what they are doing as I am a Noobie to Ubuntu.

---

