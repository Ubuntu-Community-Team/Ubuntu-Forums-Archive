---
title: "Soundblaster Audigy 2 Platinum"
date: 2009-02-08
forum: Multimedia Software
---

### Post by Revan53 on 2009-02-08
I'm having trouble getting my sound card working. I found a command and got the following:

bob@bob-desktop:~$  hwinfo --sound
11: PCI 208.0: 0401 Multimedia audio controller                 
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_1102_4
  Unique ID: oxTw.vIcU+IM+7DC
  Parent ID: vuMS.fnpiWG08KJ2
  SysFS ID: /devices/pci0000:00/0000:00:0e.0/0000:02:08.0
  SysFS BusID: 0000:02:08.0
  Hardware Class: sound
  Model: "Creative SB Audigy2 ZS"
  Vendor: pci 0x1102 "Creative Labs"
  Device: pci 0x0004 "SB Audigy"
  SubVendor: pci 0x1102 "Creative Labs"
  SubDevice: pci 0x1002 "SB Audigy2 ZS"
  Revision: 0x04
  Driver: "EMU10K1_Audigy"
  Driver Modules: "snd_emu10k1"
  I/O Ports: 0x9400-0x943f (rw)
  IRQ: 16 (1864 events)
  Module Alias: "pci:v00001102d00000004sv00001102sd00001002bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_emu10k1 is active
    Driver Activation Cmd: "modprobe snd_emu10k1"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (PCI bridge)

It shows as Audigy 2 ZS, minw is the Platinum, Is that the problem?

Thanks

---

### Post by redroad55 on 2009-02-08
Have you gotten the driver from alsa [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs")
The good news that it is supported , although there seems to be a few to choose from .. If you have not already Go to applications > system > admin. > hardware drivers and see if a driver for your soundcard is there and enable .. Post back with results and or questions .. Best to you

oh sorry I see the driver now in your post > Revision: 0x04
Driver: "EMU10K1_Audigy"

---

### Post by Revan53 on 2009-02-08
Installed ALSA Mixer and received the following:

Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Master": `,' is an invalid character in key/directory names

Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23

This goes on but, I don't understand the "Sigmatel". I thinks it is my modem sound?

How do I edit configuration files?

Thanks

---

### Post by redroad55 on 2009-02-08
This guide will help you with that[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")  
Post back if I can help you any further .. Best to you

---

