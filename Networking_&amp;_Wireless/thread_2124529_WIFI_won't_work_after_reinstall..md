---
title: "WIFI won't work after reinstall."
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by sticeXXD on 2013-03-11
ok i got a silly little netbook to carry movies around on, had 12.04 on it lost the password (fiances fault) and so i reinstalled 12..04, wifi worked before no problem, iv been searching all the threads and i can't find a solution that helps me anywhere, The netbook is a COBY 10 inch netbook PC 

 dmesg | grep rt2
[  530.005553] rt2800pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  530.005577] rt2800pci 0000:02:00.0: setting latency timer to 64
[  530.062753] Registered led device: rt2800pci-phy0::radio
[  530.062850] Registered led device: rt2800pci-phy0::assoc
[  530.062933] Registered led device: rt2800pci-phy0::quality
[  530.204837] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
stice@stice-laptop:~$ 
 this is what i get, nothing comes up when i type rfkill list all, and my hard toggle doesnt change a thing it's Fn + F1 , as previousl;y mentioned though it worked fine before now it doesnt work at all, please help and thanks in advance.

---

### Post by cortman on 2013-03-11
Please post the output of

```
lspci
```

and

```
iwconfig
```

---

### Post by sticeXXD on 2013-03-11
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe



lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by cortman on 2013-03-11
Hi, follow the instructions in this [post]("http://ubuntuforums.org/showthread.php?t=1749179&p=10877688#post10877688").

---

### Post by sticeXXD on 2013-03-11
ok tried to no effect, i probably put them in the wrong place in gedit or some such but its still not working at all.

---

### Post by cortman on 2013-03-11
Well, we can check that. Please post output of

```
cat /etc/modprobe.d/blacklist.conf
```

Also, did you reboot after running those commands?

---

### Post by sticeXXD on 2013-03-12
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib

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

---

### Post by cortman on 2013-03-12
Don't know that it will make any difference at all but you should copy the block you added into the end of the file- make it look like this:

```

[COLOR=#000000]# This file lists those modules which we don't want to be loaded by[/COLOR]
[COLOR=#000000]# alias expansion, usually so some other driver will be loaded for the[/COLOR]
[COLOR=#000000]# device instead.[/COLOR]

[COLOR=#000000]# evbug is a debug tool that should be loaded explicitly[/COLOR]
[COLOR=#000000]blacklist evbug[/COLOR]

[COLOR=#000000]# these drivers are very simple, the HID drivers are usually preferred[/COLOR]
[COLOR=#000000]blacklist usbmouse[/COLOR]
[COLOR=#000000]blacklist usbkbd[/COLOR]

[COLOR=#000000]# replaced by e100[/COLOR]
[COLOR=#000000]blacklist eepro100[/COLOR]

[COLOR=#000000]# replaced by tulip[/COLOR]
[COLOR=#000000]blacklist de4x5[/COLOR]

[COLOR=#000000]# causes no end of confusion by creating unexpected network interfaces[/COLOR]
[COLOR=#000000]blacklist eth1394[/COLOR]

[COLOR=#000000]# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much[/COLOR]
[COLOR=#000000]# hardware on its own (Ubuntu bug #2011, #6810)[/COLOR]
[COLOR=#000000]blacklist snd_intel8x0m[/COLOR]

[COLOR=#000000]# Conflicts with dvb driver (which is better for handling this device)[/COLOR]
[COLOR=#000000]blacklist snd_aw2[/COLOR]

[COLOR=#000000]# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)[/COLOR]
[COLOR=#000000]blacklist i2c_i801[/COLOR]

[COLOR=#000000]# replaced by p54pci[/COLOR]
[COLOR=#000000]blacklist prism54[/COLOR]

[COLOR=#000000]# replaced by b43 and ssb.[/COLOR]
[COLOR=#000000]blacklist bcm43xx[/COLOR]

[COLOR=#000000]# most apps now use garmin usb driver directly (Ubuntu: #114565)[/COLOR]
[COLOR=#000000]blacklist garmin_gps[/COLOR]

[COLOR=#000000]# replaced by asus-laptop (Ubuntu: #184721)[/COLOR]
[COLOR=#000000]blacklist asus_acpi[/COLOR]

[COLOR=#000000]# low-quality, just noise when being used for sound playback, causes[/COLOR]
[COLOR=#000000]# hangs at desktop session start (Ubuntu: #246969)[/COLOR]
[COLOR=#000000]blacklist snd_pcsp[/COLOR]

[COLOR=#000000]# ugly and loud noise, getting on everyone's nerves; this should be done by a[/COLOR]
[COLOR=#000000]# nice pulseaudio bing (Ubuntu: #77010)[/COLOR]
[COLOR=#000000]blacklist pcspkr[/COLOR]

[COLOR=#000000]# EDAC driver for amd76x clashes with the agp driver preventing the aperture[/COLOR]
[COLOR=#000000]# from being initialised (Ubuntu: #297750). Blacklist so that the driver[/COLOR]
[COLOR=#000000]# continues to build and is installable for the few cases where its[/COLOR]
[COLOR=#000000]# really needed.[/COLOR]
[COLOR=#000000]blacklist amd76x_edac

[/COLOR][COLOR=#000000]blacklist rt2800pci[/COLOR]
[COLOR=#000000]blacklist rt2800lib[/COLOR]
[COLOR=#000000]blacklist rt2x00pci[/COLOR]
[COLOR=#000000]blacklist rt2x00lib

```
[/COLOR]

---

### Post by sticeXXD on 2013-03-12
nope did nothing sadly, it worked fine before the update but nothing is working fter :( sad face lol

---

### Post by cortman on 2013-03-12
Hi, now run
```
sudo modprobe [COLOR=#000000]rt2860sta[/COLOR]
```

Then see if the wireless fires up.

---

### Post by sticeXXD on 2013-03-12
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rt2860sta not found.

---

### Post by sticeXXD on 2013-03-13
this is what my terminal says when i run that command.

---

### Post by cortman on 2013-03-13
Sorry, try

```
sudo modprobe rt2800pci
```

---

### Post by sticeXXD on 2013-03-13
that fixed it....am i gonna need to remember this command or is it just fixed for good?

---

### Post by sticeXXD on 2013-03-13
btw thank you thank you thank you for your help so very very much.

---

### Post by cortman on 2013-03-14
Restart the computer. If the wireless still works, it's fixed for good. If it doesn't, we'll just need to add that module to /etc/modules so it starts up every time.
Glad to help. :)

---

### Post by sticeXXD on 2013-03-14
ok ya i need to add the module and i dont remember how to make this a solved thread.

---

