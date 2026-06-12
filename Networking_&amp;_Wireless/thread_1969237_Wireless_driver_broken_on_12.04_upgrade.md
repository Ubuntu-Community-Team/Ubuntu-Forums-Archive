---
title: "Wireless driver broken on 12.04 upgrade"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by mellery on 2012-04-29
My wireless has stopped working on upgrade to 12.04, here is info I've found requested in other threads, if anyone can help

lspci | grep work
```
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

```

sudo lshw -C network
```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbc00000-fbc03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: f0:4d:a2:b6:6d:2a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.2.116 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:e000(size=256) memory:d0b10000-d0b10fff memory:d0b00000-d0b0ffff memory:fb200000-fb21ffff

```

lsmod
```
Module                  Size  Used by
ppp_deflate            13038  1 
zlib_deflate           27139  1 ppp_deflate
bsd_comp               12994  0 
ppp_async              17539  1 
crc_ccitt              12667  1 ppp_async
des_generic            21415  0 
md4                    12595  0 
joydev                 17693  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
dm_crypt               23125  0 
parport_pc             32866  0 
ppdev                  17113  0 
nls_utf8               12557  1 
cifs                  287273  2 
binfmt_misc            17540  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                87692  0 
serio_raw              13211  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
i915                  468651  3 
wmi                    19256  1 dell_wmi
drm_kms_helper         46978  1 i915
r8169                  62099  0 
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915

```

I think the problem is with the following

sudo apt-get install --reinstall bcmwl-kernel-source
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,151 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 283451 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.2.0-24-generic
Building for architecture x86_64
Building initial module for 3.2.0-24-generic
Error! Bad return status for module build on kernel: 3.2.0-24-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
cryptsetup: WARNING: could not determine root device from /etc/fstab

```

/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log has the following text
```
DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.2.0-24-generic (x86_64)
Sun Apr 29 20:17:42 EDT 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make: execvp: make: Too many levels of symbolic links
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] Error 127
make: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
```

---

### Post by Guitar John on 2012-04-29
Go into the Software Center and type "b43" into the search bar.  I think you win find what you are looking fo there.  I had the same problem with 11.10 on my old Dell 2200.

---

### Post by chili555 on 2012-04-29
I'm not at all sure that b43 is correct for his device without more information. Please post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by mellery on 2012-04-29
firmware-b43-lpphy-installer, b43-fwcutter, and firmware-b43legacy-installer are all installed

firmware-b43-installer isn't installed but it doesn't list bcm4313 as a supported chipset

---

### Post by mellery on 2012-04-29
> **chili555 said:**
> I'm not at all sure that b43 is correct for his device without more information. Please post:```
lspci -nn | grep 0280
```Thanks.

 lspci -nn | grep 0280

```
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

thanks

---

### Post by chili555 on 2012-04-29
If kindly old Dr. Chili were the kind of person to curse, he'd start now. Your device is claimed by *three* competing drivers and none are b43! We have some work to do. First, let's try to get bcmwl-kernel-source going:```
sudo su
apt-get remove --purge bcmwl-kernel-source
apt-get install bcmwl-kernel-source
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
echo wl >> /etc/modules
exit
```If all this goes without drama, reboot and let us have your report.

I think there is a very slight possibility that one of the two that we blacklisted is correct. I hope I'm wrong.

---

### Post by mellery on 2012-04-29
"apt-get install bcmwl-kernel-source" still fails with the error in my first post

The following ones were already blacklisted,
```
blacklist bcma
blacklist brcm80211
blacklist brcmwl

```

I've added brcmsmac to the blacklist, and wl to /etc/modules

edit: rebooted and no luck

---

### Post by chili555 on 2012-04-29
> Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.And what did it say?> blacklist bcma
blacklist brcm80211
blacklist brcmwlBe sure to add brcmsmac.

---

### Post by mellery on 2012-04-29
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log has the following text
```
DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.2.0-24-generic (x86_64)
Sun Apr 29 20:17:42 EDT 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make: execvp: make: Too many levels of symbolic links
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] Error 127
make: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
```[/QUOTE]

---

### Post by chili555 on 2012-04-29
> **mellery said:**
> /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log has the following text
```
DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.2.0-24-generic (x86_64)
Sun Apr 29 20:17:42 EDT 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make: execvp: make: Too many levels of symbolic links
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] Error 127
make: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
```Sorry, I didn't see that above. Still studying...

If you boot into an older kernel at the GRUB menu, can you --reinstall it? I wonder if it would help to --reinstall linux-image-`uname -r` and linux-headers-`uname -r.`

I wonder if it's a 64-bit issue. I successfully reinstalled bcmwl-kernel-source just now on 32-bit PAE.

---

### Post by kerpap on 2012-04-30
Same problem here. also noticed that I cant get the new kernel updates for VMware player and it has stopped working.

the error happens when it tries to update the virtual network devices in VMware when it downloads and configures the kernel updates.

Im not sure if it is related....

---

### Post by mellery on 2012-04-30
> **chili555 said:**
> Sorry, I didn't see that above. Still studying...

If you boot into an older kernel at the GRUB menu, can you --reinstall it? I wonder if it would help to --reinstall linux-image-`uname -r` and linux-headers-`uname -r.`

I wonder if it's a 64-bit issue. I successfully reinstalled bcmwl-kernel-source just now on 32-bit PAE.

how do I see the grub screen on startup to pick an older kernel?

---

### Post by mellery on 2012-04-30
> **kerpap said:**
> Same problem here. also noticed that I cant get the new kernel updates for VMware player and it has stopped working.

the error happens when it tries to update the virtual network devices in VMware when it downloads and configures the kernel updates.

Im not sure if it is related....

I filed a bug here if you want to add that you have the same problem

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/991090](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/991090)

---

### Post by chili555 on 2012-04-30
> how do I see the grub screen on startup to pick an older kernel?When you first boot your computer, you should see something like this. Arrow down to Previous Linux Versions and pick an earlier version. Press Enter and boot into it.

Can you reinstall bcmwl-kernel-source from there? If so, I have a pretty good idea how we can fix the latest version.

---

### Post by mellery on 2012-04-30
Looks like upgrading to precise removed all my old kernel versions.  I only found 3.2.0-23 in the precise repositories, so I tried installing bcmwl-kernel-source with that kernel but got the same error.  Wireless worked fine in oneric

---

### Post by ts3 on 2012-04-30
For what it's worth, installing bcmwl-kernel-source, broadcom-sta-common and broadcom-sta-source worked when installing from the Software Centre (did that a couple of days ago, after the final release came out and after people started having problems with building the driver and installing through the system settings -> additional drivers option).  Typing "bcm" in the search box in the Software Centre brings up the three packages.

---

### Post by chili555 on 2012-04-30
> **mellery said:**
> Looks like upgrading to precise removed all my old kernel versions.  I only found 3.2.0-23 in the precise repositories, so I tried installing bcmwl-kernel-source with that kernel but got the same error.  Wireless worked fine in onericYou might try:```
sudo apt-get install --reinstall linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

After that, try to reinstall bcmwl-kernel-source.> For what it's worth, installing bcmwl-kernel-source, broadcom-sta-common and broadcom-sta-source worked when installing from the Software Centre Indeed it usually does, including the 10-12 cases I've worked on since 12.04 was released; just not here.

---

### Post by mellery on 2012-04-30
same errors as before, I also get the same error when trying to reinstall the headers :(

```
mike@mike-laptop:~$ sudo apt-get install --reinstall linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/947 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 309639 files and directories currently installed.)
Preparing to replace linux-headers-3.2.0-23-generic 3.2.0-23.36 (using .../linux-headers-3.2.0-23-generic_3.2.0-23.36_amd64.deb) ...
Unpacking replacement linux-headers-3.2.0-23-generic ...
Setting up linux-headers-3.2.0-23-generic (3.2.0-23.36) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Error! Bad return status for module build on kernel: 3.2.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
mike@mike-laptop:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,151 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 309639 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building for 3.2.0-23-generic and 3.2.0-24-generic
Building for architecture x86_64
Building initial module for 3.2.0-23-generic
Error! Bad return status for module build on kernel: 3.2.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
cryptsetup: WARNING: could not determine root device from /etc/fstab

```

---

### Post by chili555 on 2012-04-30
Please download this: [https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945147/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_i386.deb](https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945147/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_i386.deb)

Install it with:```
sudo dpkg -i bcmwl*.deb
```Thanks.

---

### Post by mellery on 2012-04-30
The i386 version gave the following 
```
mike@mike-laptop:~/Downloads$ sudo dpkg -i bcmwl*.deb
(Reading database ... 309589 files and directories currently installed.)
Unpacking bcmwl-kernel-source:i386 (from bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu5_i386.deb) ...
(Noting disappearance of bcmwl-kernel-source, which has been completely replaced.)
dpkg: dependency problems prevent configuration of bcmwl-kernel-source:i386:
 bcmwl-kernel-source:i386 depends on dkms.
 bcmwl-kernel-source:i386 depends on linux-libc-dev.
 bcmwl-kernel-source:i386 depends on libc6-dev.
dpkg: error processing bcmwl-kernel-source:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bcmwl-kernel-source:i386

```

I looked around and found the x64 package, but that gave the same error as before

[https://launchpad.net/ubuntu/quantal/amd64/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu6.1](https://launchpad.net/ubuntu/quantal/amd64/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu6.1)

```
(Reading database ... 309639 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.2.0-24-generic
Building for architecture x86_64
Building initial module for 3.2.0-24-generic
Error! Bad return status for module build on kernel: 3.2.0-24-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
cryptsetup: WARNING: could not determine root device from /etc/fstab

```

---

### Post by mellery on 2012-05-01
> **chili555 said:**
> If kindly old Dr. Chili were the kind of person to curse, he'd start now. Your device is claimed by *three* competing drivers and none are b43! We have some work to do. First, let's try to get bcmwl-kernel-source going:```
sudo su
apt-get remove --purge bcmwl-kernel-source
apt-get install bcmwl-kernel-source
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
echo wl >> /etc/modules
exit
```If all this goes without drama, reboot and let us have your report.

I think there is a very slight possibility that one of the two that we blacklisted is correct. I hope I'm wrong.

[http://askubuntu.com/questions/12355/how-do-i-get-my-broadcom-bcm4313-working-correctly](http://askubuntu.com/questions/12355/how-do-i-get-my-broadcom-bcm4313-working-correctly)

I found this post, and it says to try brcmsmac, I'll try it tonight.  Where did you see that 3 drivers were claiming my card?

---

### Post by chili555 on 2012-05-01
> I found this post, and it says to try brcmsmac, I'll try it tonight. Where did you see that 3 drivers were claiming my card?In *modinfo*:```
chili@LAPTOP60:~$ modinfo wl | grep 4727
alias:          pci:v000014E4d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*
chili@LAPTOP60:~$ modinfo bcma | grep 4727
alias:          pci:v000014E4d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*
chili@LAPTOP60:~$ modinfo brcmsmac | grep 4727
alias:          pci:v000014E4d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*
```Your device is listed in the aliases for all three drivers. > Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] (rev 01)I have had several other cases where wl, the driver provided by the elusive brcmwl-kernel-source, works fine. That's not to say that brcmsmac wouldn't; we just haven't tried it. It should be easy to test:```
sudo modprobe brcmsmac
iwconfig
```Do you get a wireless interface? Can you connect?

Frankly, I don't understand how the answers at Askubuntu can be relied on without confirming the exact device in lspci. The pci.id, which was never listed there is, in my humble opinion, *everything*.

---

### Post by mellery on 2012-05-01
> 
Your device is listed in the aliases for all three drivers. I have had several other cases where wl, the driver provided by the elusive brcmwl-kernel-source, works fine. That's not to say that brcmsmac wouldn't; we just haven't tried it. It should be easy to test:```
sudo modprobe brcmsmac
iwconfig
```Do you get a wireless interface? Can you connect?


Success!  The above two commands got me working wireless, they didn't take effect after reboot so I had to run them again.  Is there a way to automatically modprobe the driver?  Thanks for all the help.

---

### Post by chili555 on 2012-05-01
Awesome! Did you blacklist as I suggested above? Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Make sure these lines appear:```
blacklist bcma
blacklist wl
```Proofread, save and close gedit. Now do:```
sudo gedit /etc/modules
```Make sure this appears:```
brcmsmac
```If any other Broadcom driver is in there except brcmsmac, remove it. Proofread, save and close gedit.

You should be all set. If so, please use thread tools at the top to Mark Solved.

---

### Post by mellery on 2012-05-01
everythings working great now, marking as solved.  Is there any reason to get the wl driver working in the future on my laptop (better support/stability/features, etc)?

Thanks again

---

### Post by chili555 on 2012-05-01
Not that I know of. If *brcmsmac* is working well for you, then I would't change it. Glad it's sorted!

---

