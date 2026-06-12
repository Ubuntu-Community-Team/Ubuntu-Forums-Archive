---
title: "Yet ANOTHER broken Broadcam wireless driver"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by beeser on 2011-04-27
Hey everybody;

I installed 10.10 on a Dell Inspiron 1545 a couple of days ago.  It was a bit rough, but as of yesterday, it was up and running well.  Then, in the afternoon, the wireless dropped out.  It seems these Broadcom cards are very problematic...

So I tried this:

[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

and everything went well until I got to this:

sudo insmod wl.ko

At which point the reply is:

insmod: can't read 'wl.ko': No such file or directory

Yet I can clearly see it:

:~$ ls /lib/modules/2.6.35-28-generic-pae/kernel/net/wireless
cfg80211.ko             lib80211_crypt_tkip.ko  lib80211.ko
lib80211_crypt_ccmp.ko  lib80211_crypt_wep.ko   wl.ko
:~$ 

Any ideas?

Thanks!

---

### Post by Megaptera on 2011-04-27
I used this simple fix on my 1545 with 10.10 
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

don't worry that it says 'mini' ... and don't forget the reboot.

Hope this helps?

---

### Post by beeser on 2011-04-27
I appreciate the reply, thanks!

What that did was put a new file, dkms, into the "update" folder in the wireless kernel.  Inside the file is the wl.ko.  When I did the:

System>Administration>Additional Drivers

It came back with, "No proprietary drivers are in use on this system." 

Still no joy.  I don't even see a wireless connection as on option when I pull down the menu in the upper right of the panel in the GUI (next to the audio volume control).

---

### Post by TBABill on 2011-04-27
Since you already had a working connection this is odd unless you got a kernel update that borked the module (or the blacklist). 
 
What happens when you ```
sudo modprobe wl
```

---

### Post by TBABill on 2011-04-27
And do you see any other apparent wireless drivers listed in the output of ```
lsmod
``` or the presence of the wl?

---

### Post by josephmills on 2011-04-27
hi there please take out all ip address but could we please see a 
```
lsmod | grep wl 
```
and a 
```
dmesg | grep wl 
```
and a this is the one to take out the ip 
```
sudo lshw -C network
``` 
thanks

---

### Post by beeser on 2011-04-27
Yeah, I thought it was weird that it just stopped working, too.  I didn't perform any updates until this morning, kinda hoping there would be in cure in there, somewhere....

"sudo modprobe wl" just brings back my shell prompt.  Here's what "lsmod" found:

~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
snd_hda_codec_idt      54919  1 
joydev                  8767  0 
snd_hda_intel          22299  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
wl                   1959565  0 
i915                  296139  3 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168732  3 i915,drm_kms_helper
dell_wmi                2852  0 
lib80211                5058  1 wl
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               55847  0 
intel_agp              26926  2 i915
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
lp                      7342  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
dell_laptop             5730  0 
dcdbas                  5442  1 dell_laptop
agpgart                32075  2 drm,intel_agp
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40236  0 
ahci                   19198  3 
sky2                   45456  0 
libahci                21792  1 ahci
~$

---

### Post by beeser on 2011-04-27
> **josephmills said:**
> hi there please take out all ip address but could we please see a 
```
lsmod | grep wl 
```and a 
```
dmesg | grep wl 
```and a this is the one to take out the ip 
```
sudo lshw -C network
```thanks

~$ lsmod | grep wl
wl                   1959565  0 
lib80211                5058  1 wl
~$ 

~$ dmesg | grep wl
[   12.110206] wl: module license 'MIXED/Proprietary' taints kernel.
~$ 

~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f69fe000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:4d:dc:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=xxx.xxx.x.x latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
~$

---

### Post by josephmills on 2011-04-27
could we also see a ```
rfkill list 
``` thanks

---

### Post by josephmills on 2011-04-27
> **beeser said:**
> ~$ lsmod | grep wl
wl                   1959565  0 
lib80211                5058  1 wl
~$ 

I don't see all the mods
> 
~$ dmesg | grep wl
[   12.110206] wl: module license 'MIXED/Proprietary' taints kernel.
~$ 

I dont see the firmware either 

> 
~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f69fe000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:4d:dc:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=xxx.xxx.x.x latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
~$

I also don't see the driver here either

---

### Post by josephmills on 2011-04-27
lets see a ```
lspci -vnn | grep 14e3 
```
Thanks

---

### Post by TBABill on 2011-04-27
> **beeser said:**
> ~$ lsmod | grep wl
wl 1959565 0 
lib80211 5058 1 wl
~$ 
 
~$ dmesg | grep wl
[ 12.110206] wl: module license 'MIXED/Proprietary' taints kernel.
~$ 
 
~$ sudo lshw -C network
*-network UNCLAIMED 
description: Network controller
product: WiFi Link 5100
vendor: Intel Corporation
~$
I'm a bit confused. We are looking for Broadcom driver wl and firmware, but your lshw returned info on an Intel WiFi Link 5100 (link regarding that device [http://www.intel.com/Assets/PDF/prodbrief/319981.pdf](http://www.intel.com/Assets/PDF/prodbrief/319981.pdf)) Do you have more than one device on the machine at this time, one of them being Intel and the other a Broadcom? The Broadcom was not listed, although you seem to have built the module.

---

### Post by beeser on 2011-04-27
> **josephmills said:**
> lets see a ```
lspci -vnn | grep 14e3 
```Thanks

Well, doing that simply brings me back to my shell prompt, like all I did was hit the "Enter" key.

Here's this:

~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
:~$ 

Thanks for your patience on this!

---

### Post by josephmills on 2011-04-27
> **beeser said:**
> Well, doing that simply brings me back to my shell prompt, like all I did was hit the "Enter" key.

Here's this:

~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
:~$ 

Thanks for your patience on this!

try ```
rfkill unblock all 
``` thanks

---

