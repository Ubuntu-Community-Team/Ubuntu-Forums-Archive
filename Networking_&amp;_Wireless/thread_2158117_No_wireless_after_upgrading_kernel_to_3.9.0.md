---
title: "No wireless after upgrading kernel to 3.9.0"
date: 2013-06-27
forum: Networking &amp; Wireless
---

### Post by sobinary on 2013-06-27
My wireless was working fine on kernel 3.8.0, but no longer works in 3.9.0. By that, I mean "Wifi" isn't even an option in the Network Settings. 

I'm using Ubuntu 13.04 on a Sony Vaio Fit 14E. Here's my network adapter's info: 
```
 lspci -vvnn | grep 14e4
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
```

And then

```
  *-network UNCLAIMED            description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0700000-c0707fff
```

I've tried installing different drivers for the 43142 with no success (maybe incorrectly?). Ethernet works perfectly.

Any help would be _immensely_ appreciated because I need this computer for work. Thank you!

---

### Post by chili555 on 2013-06-27
> I've tried installing different drivers for the 43142 with no successWhich, please? What may we have to remove before we proceed? How did you go about installing kernel version 3.9? May we have a link?

---

### Post by chili555 on 2013-06-27
Off for the evening, so I'll give the generic answer:```
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
```Be sure you've installed linux-image-extra and if generic headers are not available, you can probably get away with linux-headers matching your 3.9 kernel version. I don't know if this is where you got 3.9, but notice here that linux-image, linux-image-extras and linux-headers are all needed.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/)

---

### Post by sobinary on 2013-06-27
Mainly ```
 [FONT=Consolas]sudo -i wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb[/FONT] 
``` and combinations of re-installing associated broadcom packages via Synaptics. I don't quite remember how I obtained 3.9. If there's a decent chance that re-installing the kernel will fix this, then I'm willing to do it.

---

### Post by sobinary on 2013-06-27
The attached screenshots show what I have installed. For the extras you mention, I believe I have the 3.8 versions. Should that suffice, or is there a way to get the 3.9s (as they don't appear in Synaptics)? I'd be okay with going back to 3.8, but the speakers and mic don't work with that version :(

---

### Post by chili555 on 2013-06-28
That should probably work, actually. Let's see:```
sudo modprobe wl
dmesg | grep wl
iwconfig
```Thanks.

---

### Post by sobinary on 2013-06-28
Ok,
```

sudo modprobe wl
libkmod: ERROR ../libkmod/libkmod-module.c:791 kmod_module_insert_module: could not find module by name='wl'ERROR: could not insert 'wl': Function not implemented
libkmod: ERROR ../libkmod/libkmod-module.c:925 command_do: Error running install command for wl
ERROR: could not insert 'wl': Operation not permitted

```
```
[COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep wl
[/FONT][/COLOR]
```
```
iwconfig
eth0      no wireless extensions.
lo        no wireless extensions.

```
Looks like this may be the problem?

---

### Post by chili555 on 2013-06-28
May I see:```
ls /lib/modules/`uname -r`/updates/dkms/
```Those tickmarks are on the left side of my US keyboard on the same key with [SIZE=4]~[/SIZE]. Also:```
sudo dpkg -r  wireless-bcm43142-dkms
sudo apt-get install --reinstall bcmwl-kernel-source
```One of these is going to hiccup and we'll get a clue as to what's wrong.

---

### Post by sobinary on 2013-06-28
I've now lost connectivity on all kernels (due to the drivers tinkering). I just hard reset my machine, and will install 12.10 this time. If I get the same problem, then see you soon. Either way, thank you so much for your effort in helping me!

---

