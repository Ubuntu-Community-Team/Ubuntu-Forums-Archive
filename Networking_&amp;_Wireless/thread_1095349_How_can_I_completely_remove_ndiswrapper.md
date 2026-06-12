---
title: "How can I completely remove ndiswrapper?"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-03-13
I have checked completely remove ndiswrapper common and utils in synaptic. But it seems that ndiswrapper is still running. 
Here's my lsmod

```
coppen@coppen-laptop:~$ lsmod |grep 818 
rtl8187                53248  0 
usbcore               149360  8 ndiswrapper,ohci_hcd,ehci_hcd,usbhid,usb_storage,libusual,rtl8187
mac80211              216820  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               32392  2 rtl8187,mac80211

```

dmesg also shows ndiswrapper driver is present```

coppen@coppen-laptop:~$ dmesg |grep ndiswrapper
[   14.265419] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.266569] usbcore: registered new interface driver ndiswrapper

```
How can I get rid of ndiswrapper? I want to try the oringal driver rtl8187 again. Thanks!

---

### Post by Kobalt on 2009-03-13
Did you install ndiswrapper from Synaptic only, or compiled as well?
Try this to kill ndiswrapper : 
```
sudo killall ndiswrapper
```

---

### Post by Ayuthia on 2009-03-13
You can try and blacklist it:
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
```

To remove the module for the current session:
```
sudo modprobe -r ndiswrapper
```

---

### Post by afeasfaerw23231233 on 2009-03-13
> **Kobalt said:**
> Did you install ndiswrapper from Synaptic only, or compiled as well?
Try this to kill ndiswrapper : 
```
sudo killall ndiswrapper
```


I think ndiswrapper was installed by synaptic. 
```

coppen@coppen-laptop:~$ sudo killall ndiswrapper
[sudo] password for coppen: 
ndiswrapper: no process killed

```

---

### Post by afeasfaerw23231233 on 2009-03-13
> **Ayuthia said:**
> You can try and blacklist it:
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
```

To remove the module for the current session:
```
sudo modprobe -r ndiswrapper
```

I have run your command and reboot the computer but ndiswrapper still presents on dmesg and lsmod.
```
 coppen@coppen-laptop:~$ dmesg |grep ndiswrapper[   14.248206] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.252568] usbcore: registered new interface driver ndiswrapper
coppen@coppen-laptop:~$ lsmod |grep 818 rtl8187                53248  0 
usbcore               149360  8 ndiswrapper,ohci_hcd,ehci_hcd,usbhid,usb_storage,libusual,rtl8187
mac80211              216820  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               32392  2 rtl8187,mac80211

```

---

### Post by afeasfaerw23231233 on 2009-03-13
Here's my lshw
```


  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:43:74:7b:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.123.10 multicast=yes wireless=IEEE 802.11bg

```
It doesn't show the driver version.

---

### Post by kevdog on 2009-03-14
sudo aptitude purge ndiswrapper

or if installed from source

sudo make uninstall

---

### Post by afeasfaerw23231233 on 2009-03-14
I run ```

sudo aptitude purge ndiswrapper

```
```

coppen@coppen-laptop:~$ sudo aptitude purge ndiswrapper
[sudo] password for coppen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Couldn't find package "ndiswrapper".  However, the following
packages contain "ndiswrapper" in their name:
  ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9 
Couldn't find package "ndiswrapper".  However, the following
packages contain "ndiswrapper" in their name:
  ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9 
The following packages will be REMOVED:
  dolphin{u} kde-icons-oxygen{u} kdebase-bin{u} kdebase-data{u} 
  kdebase-runtime{u} kdebase-runtime-bin-kde4{u} kdebase-runtime-data{u} 
  kdebase-runtime-data-common{u} kdelibs-bin{u} kdelibs5{u} 
  kdelibs5-data{u} kfind{u} khelpcenter4{u} libclucene0ldbl{u} libgda3-3{u} 
  libgda3-bin{u} libgda3-common{u} libgdl-1-0{u} libgdl-1-common{u} 
  libkonq5{u} libkonq5-templates{u} libphonon4{u} libpq5{u} 
  libqt3-mt-sqlite{u} libqt4-opengl{u} libqt4-svg{u} libraptor1{u} 
  librasqal0{u} librdf0{u} libshp1{u} libsoprano4{u} libstreamanalyzer0{u} 
  libstreams0{u} libstrigiqtdbusclient0{u} phonon{u} 
  phonon-backend-gstreamer{u} python-gnome2-extras{u} raptor-utils{u} 
  redland-utils{u} soprano-daemon{u} 
0 packages upgraded, 0 newly installed, 40 to remove and 19 not upgraded.
Need to get 0B of archives. After unpacking 119MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 141860 files and directories currently installed.)
Removing khelpcenter4 ...
Removing kfind ...
Removing python-gnome2-extras ...
Removing libgda3-bin ...
Removing libgda3-3 ...
Removing libgda3-common ...
Removing libgdl-1-0 ...
Removing libgdl-1-common ...
Removing redland-utils ...
Removing libqt3-mt-sqlite ...
Removing raptor-utils ...
Removing libshp1 ...
Removing kdebase-data ...
Removing kdebase-bin ...
Removing dolphin ...
Removing libkonq5 ...
Removing kdebase-runtime ...
Removing kdebase-runtime-bin-kde4 ...
Removing kde-icons-oxygen ...
Removing kdebase-runtime-data ...
Removing kdebase-runtime-data-common ...
Removing kdelibs5 ...
Removing kdelibs5-data ...
Removing libstreamanalyzer0 ...
Removing libkonq5-templates ...
Removing phonon ...
Removing phonon-backend-gstreamer ...
Removing libphonon4 ...
Removing libqt4-opengl ...
Removing libqt4-svg ...
Removing libstreams0 ...
Removing libstrigiqtdbusclient0 ...
Removing kdelibs-bin ...
Removing libsoprano4 ...
Removing soprano-daemon ...
Removing libclucene0ldbl ...
Removing librdf0 ...
Removing libpq5 ...
Removing librasqal0 ...
Removing libraptor1 ...
Processing triggers for python-support ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
 
```

Sudo make uninstall has the following result: ```

coppen@coppen-laptop:~$ sudo make uninstall
[sudo] password for coppen: 
make: *** No rule to make target `uninstall'.  Stop.

```
```

I reboot the computer and 
 dmesg |grep ndis
[   14.248373] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.252120] usbcore: registered new interface driver ndiswrapper

``````

lsmod |grep 818 
rtl8187                53248  0 
usbcore               149360  8 ndiswrapper,ohci_hcd,ehci_hcd,usbhid,usb_storage,libusual,rtl8187
mac80211              216820  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               32392  2 rtl8187,mac80211


``` Seems ndiswrapper has still not been removed yet? I want to use back the native rtl8187 driver.

EDIT: I remember that I only installed ndiswrapper from synaptic. But I am 100% sure.

---

### Post by Kobalt on 2009-03-14
You didn't uninstall ndiswrapper yet (from the aptitude command you executed and posted here before). To remove any ndiswrapper package, proceed this way : 
```
sudo aptitude remove ndiswrapper-*
```

---

### Post by afeasfaerw23231233 on 2009-03-14
I run your command: 
```
sudo aptitude remove ndiswrapper-*
[sudo] password for coppen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "ndiswrapper-*"
Couldn't find any package whose name or description matched "ndiswrapper-*"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information   
```

No packages will be installed, upgraded, or removed?

---

### Post by afeasfaerw23231233 on 2009-03-14
Also I want to know why lshw -C network doesn't show the driver version?

---

### Post by Kobalt on 2009-03-14
> **afeasfaerw23231233 said:**
> I run your command: 
```
sudo aptitude remove ndiswrapper-*
[sudo] password for coppen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "ndiswrapper-*"
Couldn't find any package whose name or description matched "ndiswrapper-*"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information   
```

No packages will be installed, upgraded, or removed?

My mistake. Please try this instead : 
```
sudo aptitude remove --purge ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
```

---

### Post by afeasfaerw23231233 on 2009-03-14
```
sudo aptitude remove --purge ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
[sudo] password for coppen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```still the same

---

### Post by ugm6hr on 2009-03-14
aptitude will only remove if it was used to install:

```
sudo apt-get remove ndiswrapper-common
```

---

### Post by afeasfaerw23231233 on 2009-03-14
coppen@coppen-laptop:~$ sudo apt-get remove ndiswrapper-common
[sudo] password for coppen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

why it can't be removed?

---

### Post by afeasfaerw23231233 on 2009-03-14
```

coppen@coppen-laptop:~$ sudo aptitude remove --purge ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
[sudo] password for coppen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```Why it can't be removed?
```
 dmesg |grep ndiswra
[   14.220581] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.224459] usbcore: registered new interface driver ndiswrapper
coppen@coppen-laptop:~$ lsmod |grep 818 
rtl8187                53248  0 
usbcore               149360  8 ndiswrapper,ohci_hcd,ehci_hcd,usbhid,usb_storage,libusual,rtl8187

```

---

### Post by ugm6hr on 2009-03-14
Post output from:

```
cat /etc/modprobe.d/blacklist
cat /etc/modules
```

---

### Post by afeasfaerw23231233 on 2009-03-14
```
coppen@coppen-laptop:~$ cat /etc/modprobe.d/blacklist
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

#blacklist rtl818x
#blacklist rtl8187

blacklist ndiswrapper
coppen@coppen-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

# Generated by sensors-detect on Fri Feb 27 15:19:48 2009
# Chip drivers
coretemp



ndiswrapper
coppen@coppen-laptop:~$ 

```Should I remove ndiswrapper from /etc/modules?
EDIT: I remember last time I checked /etc/modules ndiswrapper wasn't here. But it reappears again?

---

### Post by ugm6hr on 2009-03-14
> **afeasfaerw23231233 said:**
> Should I remove ndiswrapper from /etc/modules?
EDIT: I remember last time I checked /etc/modules ndiswrapper wasn't here. But it reappears again?

Yes.

```
sudo nano /etc/modules
```

Delete that line, and save (Ctrl+X).
Reboot.

Also - run:
```
sudo apt-get install -f
```

---

### Post by afeasfaerw23231233 on 2009-03-14
After reboot ndiswrapper disappears from dmesg and lsmod

```
sudo apt-get install -f
[sudo] password for coppen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
```

But lshw -C network still doesn't show the driver version being used. 
```
 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:43:74:7b:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.123.10 multicast=yes wireless=IEEE 802.11bg

```
Is the native rtl8187 driver being used now?

---

### Post by afeasfaerw23231233 on 2009-03-16
bump

---

### Post by ugm6hr on 2009-03-16
Presumably yes.  ndiswrapper doesn't load now, so it must be the rtl8187.

Uncertain why lshw doesn't report it.

---

### Post by afeasfaerw23231233 on 2009-03-21
My problem seems solved

[http://ubuntuforums.org/showthread.php?p=6932570#post6932570](http://ubuntuforums.org/showthread.php?p=6932570#post6932570)

---

