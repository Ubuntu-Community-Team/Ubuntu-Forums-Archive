---
title: "replaced sound card, now cant change drivers"
date: 2013-05-28
forum: Multimedia Software
---

### Post by bunglehaze on 2013-05-28
Hi guys, I had a few issues with my onboard sound card so added in an old turtle beach card temporarily to get some sound working, now my Audigy2 card is here (I had one before on an old version of Ubuntu years ago) so I have added it in, got rid of the old one and did the usual purge of pulseaudio and alsa that was suggested in the help files for sound issues. I am still having a few issues though.

First of all I managed to **** something up and got the Dummy Output issue in sound settings, the only way to get rid of that (nothing else seemed to work) was to manually remove all pulseaudio, OSS and alsa packages in synaptic, reboot , sudo apt-get install alsa-base pulseaudio and then reboot again.

This time, drivers showed up again but the old ones - first the onboard sound drivers which is no worry as I have not disabled that but more annoyingly the old turtle beach ones Sound Fusion CS46xx are still there and NO soundblaster ones.

Now at this stage I am not really sure what else I can do to remove the Sound Fusion drivers from being loaded and replace them with the correct SB ones - please help as I am tearing my hair out trying to get sound working again :)

I am guessing a kernel module or similar must be loading the drivers, I don't want to touch those without a bit of advice first though :)

hwinfo --sound output

> > hal.1: read hal dataprocess 2679: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
19: PCI 14.2: 0403 Audio device                                 
  [Created at pci.318]
  Unique ID: 5Dex.9zCmC9gVD38
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia (Intel HDA)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 "SBx00 Azalia (Intel HDA)"
  SubVendor: pci 0x1458 "Giga-byte Technology"
  SubDevice: pci 0xa002 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe024000-0xfe027fff (rw,non-prefetchable)
  IRQ: 16 (2018 events)
  Module Alias: "pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: PCI 100.1: 0403 Audio device
  [Created at pci.318]
  Unique ID: NXNs.sjTjCqbMOx1
  Parent ID: _Znp.ZJmKoWxd6BF
  SysFS ID: /devices/pci0000:00/0000:00:02.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: sound
  Model: "nVidia Audio device"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0e0b 
  SubVendor: pci 0x107d "LeadTek Research Inc."
  SubDevice: pci 0x2747 
  Revision: 0xa1
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfcffc000-0xfcffffff (rw,non-prefetchable)
  IRQ: 19 (25401 events)
  Module Alias: "pci:v000010DEd00000E0Bsv0000107Dsd00002747bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #9 (PCI bridge)

31: PCI 307.0: 0401 Multimedia audio controller
  [Created at pci.318]
  Unique ID: Phdb.r2wSKYSOUwF
  Parent ID: qscc.ULOo3yhA66C
  SysFS ID: /devices/pci0000:00/0000:00:14.4/0000:03:07.0
  SysFS BusID: 0000:03:07.0
  Hardware Class: sound
  Model: "Voyetra Santa Cruz"
  Vendor: pci 0x1013 "Cirrus Logic"
  Device: pci 0x6003 "CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator]"
  SubVendor: pci 0x5053 "Voyetra Technologies"
  SubDevice: pci 0x3357 "Santa Cruz"
  Revision: 0x01
  Driver: "snd_cs46xx"
  Driver Modules: "snd_cs46xx"
  Memory Range: 0xfddff000-0xfddfffff (rw,non-prefetchable)
  Memory Range: 0xfdc00000-0xfdcfffff (rw,non-prefetchable)
  IRQ: 21 (10181 events)
  Module Alias: "pci:v00001013d00006003sv00005053sd00003357bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_cs46xx is active
    Driver Activation Cmd: "modprobe snd_cs46xx"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (PCI bridge)


---

### Post by bunglehaze on 2013-05-28
Just to add to this. I can select the old soundcard (CS_46xx) amplified option and sound will work temporarily but will stretch and distort.

---

### Post by Yellow Pasque on 2013-05-28
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by bunglehaze on 2013-05-29
removed as it contained data no longer relevant, posts following this are updated as I reinstalled Ubuntu from scratch and have different issues.

---

### Post by bunglehaze on 2013-05-31
Ok, I took the drastic step and wiped my Ubuntu 13.04 install and reinstalled from fresh, the Audigy driver is now showing up in Sound settings but is not playing any sound. Being a bit paranoid that I was missing something I booted into Windows 7 and installed the Audigy driver - working perfectly.

Back to Ubuntu, I logged in, get a slight noise during boot, kinda like an acknowledgement the soundcard is there before cutting out, I have been into alsamixer and just once managed to get some sound working which did not persist past a reboot and trying to repeat the same steps of making sure all the channels showed some volume does not seem to be working again.

One of my pet hates when I switched to Ubuntu many, many years ago was that simple things were sometimes infuriatingly difficult to fix, MP3's back in the day and Audio drivers were the issue, what a shame it seems that in the age of 13.04 the same problems seem to exist and are still as painstaking to try and work out. In any case, the driver is loading fine in settings so I am guessing that somewhere the soundcard is either not being enabled as the active hardware or something is blocking it from working - any suggestions please as I can't work without music?

regards

---

### Post by bunglehaze on 2013-05-31
hwinfo output - this shows that the driver is active and loading the correct module

> hal.1: read hal dataprocess 7952: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
19: PCI 14.2: 0403 Audio device                                 
  [Created at pci.318]
  Unique ID: 5Dex.9zCmC9gVD38
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia (Intel HDA)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 "SBx00 Azalia (Intel HDA)"
  SubVendor: pci 0x1458 "Giga-byte Technology"
  SubDevice: pci 0xa002 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe024000-0xfe027fff (rw,non-prefetchable)
  IRQ: 16 (1176 events)
  Module Alias: "pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: PCI 100.1: 0403 Audio device
  [Created at pci.318]
  Unique ID: NXNs.sjTjCqbMOx1
  Parent ID: _Znp.ZJmKoWxd6BF
  SysFS ID: /devices/pci0000:00/0000:00:02.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: sound
  Model: "nVidia Audio device"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0e0b 
  SubVendor: pci 0x107d "LeadTek Research Inc."
  SubDevice: pci 0x2747 
  Revision: 0xa1
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfcffc000-0xfcffffff (rw,non-prefetchable)
  IRQ: 19 (103286 events)
  Module Alias: "pci:v000010DEd00000E0Bsv0000107Dsd00002747bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #9 (PCI bridge)

31: PCI 306.0: 0401 Multimedia audio controller
  [Created at pci.318]
  Unique ID: Kaa7.WdjVi6EJHT5
  Parent ID: qscc.ULOo3yhA66C
  SysFS ID: /devices/pci0000:00/0000:00:14.4/0000:03:06.0
  SysFS BusID: 0000:03:06.0
  Hardware Class: sound
  Model: "Creative SB Audigy2 OEM HP"
  Vendor: pci 0x1102 "Creative Labs"
  Device: pci 0x0004 "SB Audigy"
  SubVendor: pci 0x1102 "Creative Labs"
  SubDevice: pci 0x1009 "SB Audigy2 OEM HP"
  Revision: 0x04
  Driver: "snd_emu10k1"
  Driver Modules: "snd_emu10k1"
  I/O Ports: 0xcf00-0xcf3f (rw)
  IRQ: 20 (419 events)
  Module Alias: "pci:v00001102d00000004sv00001102sd00001009bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_emu10k1 is active
    Driver Activation Cmd: "modprobe snd_emu10k1"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (PCI bridge)

---

### Post by Yellow Pasque on 2013-05-31
Well, now that you've wiped the system, can you do the alsa info thing again? Please, just copy/paste the link and not all of that text (or use [ code ][ /code ] tags for large blocks of text). A lot of times with Audigy's you have to toggle the Digital/IEC958 settings in alsamixer for some reason.

---

### Post by bunglehaze on 2013-05-31
No problem.

[http://www.alsa-project.org/db/?f=4b7e7a8f813381e5ecb6f43a75321a7cc31e025c](http://www.alsa-project.org/db/?f=4b7e7a8f813381e5ecb6f43a75321a7cc31e025c)

There is the link. 

No idea exactly what I did to enable sound the last time, if it survives a reboot though I am happy enough but I am sure I am not the only person who has this problem so it would be good to get to the bottom of it.

regards

**added**

I just went into alsamixer again and checked the ouputs on each channel "Audigy Analog/Digital Output Jack " was muted. I forgot that the levels do not unmute when you increase them. For now then the sound seems to be working so I need to check if the setting survives after a reboot

---

