---
title: "ALSA ...intel8x0.c:547: codec_semaphore"
date: 2010-04-29
forum: Multimedia Software
---

### Post by aeltester on 2010-04-29
mornin experts,
have been fiddling with this onboad soundcard (see infos below) for the past two days. Alsa used to recognize the tv-card as a sound card while ignoring the actual soundcard. some modprobes, alsa reloads, alsamixer resetting, alsa-base-conf editing etc. (basically all troubleshooting tips I could find through google) lead to me actually being able to hear something (using snd-intel8x0) very quietly as if the extAmp-switch were turned on. I then played around with alsamixer until I heard nothing again, did a kernel update (by accident) and swooosh I'm back where I started. No, actually I'm worse off because now alsa doesn't even recognize the tv-card anymore.

It seems to me, that semaphore (whatever that might be) got effed up (see dmesg). anyone who's got an idea on how to fix this?

[http://www.alsa-project.org/db/?f=430780d148bc3531cf6ec1559e6270ff79bdaf4f](http://www.alsa-project.org/db/?f=430780d148bc3531cf6ec1559e6270ff79bdaf4f)
```

$ hwinfo --sound
13: PCI 02.7: 0401 Multimedia audio controller                  
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1039_7012
  Unique ID: 1sCg.VZKJaFOytR1
  SysFS ID: /devices/pci0000:00/0000:00:02.7
  SysFS BusID: 0000:00:02.7
  Hardware Class: sound
  Model: "Silicon Integrated SiS 7012 onboard [Asus P4SC-EA] AC'97 Sound Controller"
  Vendor: pci 0x1039 "Silicon Integrated Systems Corp."
  Device: pci 0x7012 "AC'97 Sound Controller"
  SubVendor: pci 0x1039 "Silicon Integrated Systems Corp."
  SubDevice: pci 0x7012 "SiS 7012 onboard [Asus P4SC-EA] AC'97 Sound Controller"
  Revision: 0xa0
  I/O Ports: 0x9400-0x94ff (rw)
  I/O Ports: 0x9000-0x907f (rw)
  IRQ: 18 (no events)
  Module Alias: "pci:v00001039d00007012sv00001039sd00007012bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_intel8x0 is active
    Driver Activation Cmd: "modprobe snd_intel8x0"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```
```
$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

I'm in the group audio, my menu.lst is up to date, I'm not booting some old kernel.

thanks in advance
P

---

### Post by lidex on 2010-04-29
Try removing that option you added to alsa-base.conf:
```
snd-intel8x0 ac97_quirk=3

```
Now go to this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") and install alsa-backports. Reboot.

What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by aeltester on 2010-04-30
are you a god or something?

I did what you said. ```
$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for paprika: 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  paprika    1444 F.... pulseaudio
```

and afterwards out of curiosity ```
$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: SI7012 [SiS SI7012], Gerät 0: Intel ICH [SiS SI7012]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
```

alright then, loads of thanks. I don't understand why it suddenly picked the card up. I did NOTHING else since the last post...

amazed
P

---

### Post by lidex on 2010-04-30
Awesome. If it's truly fixed please mark the thread as solved using 'Thread Tools' up top.

---

