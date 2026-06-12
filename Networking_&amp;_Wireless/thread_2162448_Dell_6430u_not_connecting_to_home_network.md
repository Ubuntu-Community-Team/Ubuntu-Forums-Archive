---
title: "Dell 6430u not connecting to home network"
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by easchmoe on 2013-07-14
Hello I have a new Dell 6430u work laptop with 12.04.
It has broadcom 4313 wireless and it's currently using the proprietary STA driver.
At this configuration, it works flawlessly at my work network but fails to connect to my home network (i use a linksys e1200 router).
It sees my SSID but never connects.
I tried some workarounds that I found online (using the open source driver) and I was able to connect but the connection disconnects every few seconds to the point that it's unusable.

I also tried plugging in my Rosewill RNX-EasyN1 usb dongle to see if it would work and it does the same thing... see the SSID but never connect.
I have a dell desktop with 12.04 and the Rosewill works perfectly without having to do anything.

Can somebody please help me get the broadcom or the rosewill to connect effectively to my home network?
Thanks.

---

### Post by Hadaka on 2013-07-14
Hi, please post the output of..
```
lspci -n | grep 0280
lsmod
cat /etc/modules
cat /etc/network/interfaces
```
thanks

---

### Post by easchmoe on 2013-07-14
```
[FONT=courier new]$ lspci -n | grep 0280[/FONT]
[FONT=courier new]02:00.0 0280: 14e4:4727 (rev 01)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]$ lsmod[/FONT]
[FONT=courier new]Module                  Size  Used by[/FONT]
[FONT=courier new]snd_hda_codec_hdmi     32476  1 [/FONT]
[FONT=courier new]snd_hda_codec_idt      70774  1 [/FONT]
[FONT=courier new]joydev                 17694  0 [/FONT]
[FONT=courier new]pci_stub               12623  1 [/FONT]
[FONT=courier new]vboxpci                23237  0 [/FONT]
[FONT=courier new]vboxnetadp             25671  0 [/FONT]
[FONT=courier new]vboxnetflt             27613  0 [/FONT]
[FONT=courier new]vboxdrv               320275  3 vboxpci,vboxnetadp,vboxnetflt[/FONT]
[FONT=courier new]bnep                   18240  2 [/FONT]
[FONT=courier new]rfcomm                 47562  12 [/FONT]
[FONT=courier new]binfmt_misc            17541  1 [/FONT]
[FONT=courier new]arc4                   12530  2 [/FONT]
[FONT=courier new]uvcvideo               78117  0 [/FONT]
[FONT=courier new]videobuf2_core         33025  1 uvcvideo[/FONT]
[FONT=courier new]videodev              125126  2 uvcvideo,videobuf2_core[/FONT]
[FONT=courier new]videobuf2_vmalloc      12861  1 uvcvideo[/FONT]
[FONT=courier new]videobuf2_memops       13405  1 videobuf2_vmalloc[/FONT]
[FONT=courier new]rt2800usb              22903  0 [/FONT]
[FONT=courier new]rt2800lib              59396  1 rt2800usb[/FONT]
[FONT=courier new]crc_ccitt              12708  1 rt2800lib[/FONT]
[FONT=courier new]rt2x00usb              20809  1 rt2800usb[/FONT]
[FONT=courier new]rt2x00lib              55575  3 rt2800usb,rt2800lib,rt2x00usb[/FONT]
[FONT=courier new]coretemp               13642  0 [/FONT]
[FONT=courier new]kvm_intel             137888  0 [/FONT]
[FONT=courier new]kvm                   422160  1 kvm_intel[/FONT]
[FONT=courier new]ghash_clmulni_intel    13221  0 [/FONT]
[FONT=courier new]aesni_intel            51134  0 [/FONT]
[FONT=courier new]cryptd                 20531  2 ghash_clmulni_intel,aesni_intel[/FONT]
[FONT=courier new]aes_x86_64             17256  1 aesni_intel[/FONT]
[FONT=courier new]mac80211              555272  3 rt2800lib,rt2x00usb,rt2x00lib[/FONT]
[FONT=courier new]btusb                  22432  0 [/FONT]
[FONT=courier new]bluetooth             211812  24 bnep,rfcomm,btusb[/FONT]
[FONT=courier new]ppdev                  17114  0 [/FONT]
[FONT=courier new]dell_wmi               12682  0 [/FONT]
[FONT=courier new]sparse_keymap          13891  1 dell_wmi[/FONT]
[FONT=courier new]dell_laptop            17426  0 [/FONT]
[FONT=courier new]dcdbas                 14491  1 dell_laptop[/FONT]
[FONT=courier new]snd_hda_intel          34063  3 [/FONT]
[FONT=courier new]snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel[/FONT]
[FONT=courier new]snd_hwdep              17765  1 snd_hda_codec[/FONT]
[FONT=courier new]snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec[/FONT]
[FONT=courier new]microcode              23030  0 [/FONT]
[FONT=courier new]snd_seq_midi           13325  0 [/FONT]
[FONT=courier new]lib80211_crypt_tkip    17391  0 [/FONT]
[FONT=courier new]psmouse               102506  0 [/FONT]
[FONT=courier new]serio_raw              13216  0 [/FONT]
[FONT=courier new]parport_pc             32867  0 [/FONT]
[FONT=courier new]snd_rawmidi            30750  1 snd_seq_midi[/FONT]
[FONT=courier new]snd_seq_midi_event     14900  1 snd_seq_midi[/FONT]
[FONT=courier new]snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event[/FONT]
[FONT=courier new]wmi                    19257  1 dell_wmi[/FONT]
[FONT=courier new]snd_timer              29990  2 snd_pcm,snd_seq[/FONT]
[FONT=courier new]snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT]
[FONT=courier new]wl                   3074942  0 [/FONT]
[FONT=courier new]i915                  535221  3 [/FONT]
[FONT=courier new]cfg80211              208382  3 rt2x00lib,mac80211,wl[/FONT]
[FONT=courier new]lib80211               14382  2 lib80211_crypt_tkip,wl[/FONT]
[FONT=courier new]drm_kms_helper         49259  1 i915[/FONT]
[FONT=courier new]mac_hid                13254  0 [/FONT]
[FONT=courier new]snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT]
[FONT=courier new]drm                   290595  4 i915,drm_kms_helper[/FONT]
[FONT=courier new]i2c_algo_bit           13565  1 i915[/FONT]
[FONT=courier new]lpc_ich                17145  0 [/FONT]
[FONT=courier new]soundcore              15092  1 snd[/FONT]
[FONT=courier new]snd_page_alloc         18573  2 snd_hda_intel,snd_pcm[/FONT]
[FONT=courier new]video                  19653  1 i915[/FONT]
[FONT=courier new]mei                    41410  0 [/FONT]
[FONT=courier new]lp                     17800  0 [/FONT]
[FONT=courier new]parport                46563  3 ppdev,parport_pc,lp[/FONT]
[FONT=courier new]e1000e                198734  0 [/FONT]
[FONT=courier new]ahci                   25869  3 [/FONT]
[FONT=courier new]libahci                27338  1 ahci[/FONT]
[FONT=courier new]sdhci_pci              18749  0 [/FONT]
[FONT=courier new]sdhci                  33145  1 sdhci_pci[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]$ cat /etc/modules[/FONT]
[FONT=courier new]# /etc/modules: kernel modules to load at boot time.[/FONT]
[FONT=courier new]#[/FONT]
[FONT=courier new]# This file contains the names of kernel modules that should be loaded[/FONT]
[FONT=courier new]# at boot time, one per line. Lines beginning with "#" are ignored.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]lp[/FONT]
[FONT=courier new]rtc[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]$ cat /etc/network/interfaces[/FONT]
[FONT=courier new]auto lo[/FONT]
[FONT=courier new]iface lo inet loopback[/FONT]
[FONT=courier new]
[/FONT]

```[FONT=courier new]
[/FONT]

---

### Post by Hadaka on 2013-07-14
Hi, please first remove the usb wifi stick then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf wl
sudo modprobe -v brcmsmac
```
thanks

---

### Post by easchmoe on 2013-07-15
> **Hadaka said:**
> Hi, please first remove the usb wifi stick then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf wl
sudo modprobe -v brcmsmac
```
thanks

```

$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 libgomp1:i386 libcroco3:i386 libgettextpo0:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,274 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 250198 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-36-generic


$ sudo modprobe -r wl
FATAL: Module wl not found.


$ sudo modprobe -v brcmsmac
[blank]

```

---

### Post by Hadaka on 2013-07-15
Hi, this..

FATAL: Module wl not found. 

was probably removed by the first command...
not to worry..
continue with the next command please.
thanks.

---

### Post by easchmoe on 2013-07-15
> **Hadaka said:**
> Hi, this..

FATAL: Module wl not found. 

was probably removed by the first command...
not to worry..
continue with the next command please.
thanks.

Hi. It returned blank.

---

### Post by praseodym on 2013-07-15
Which kernel is in use? Please show
```

uname -a
```
Does LAN work?

---

### Post by easchmoe on 2013-07-15
> **praseodym said:**
> Which kernel is in use? Please show
```

uname -a
```
Does LAN work?

I was connected to my work wifi the whole time and it's still working.
I didn't notice anything change connection wise.
I'll have to test this at home later to see if it connects.

$ uname -a
Linux orlando-laptop1 3.5.0-36-generic #57~precise1-Ubuntu SMP Thu Jun 20 18:21:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by praseodym on 2013-07-15
Install the following (copy/paste):
```

sudo apt-get install --reinstall linux-headers-generic-lts-quantal build-essential dkms linux-backports-modules-cw-3.6-$(grep CODE /etc/lsb-release | cut -c18-28)-$( uname -r | cut -c10-23) 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```
Clean up the configuration:```

sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Shutdown for 10 minutes without any current source and restart.

---

### Post by easchmoe on 2013-07-15
> **praseodym said:**
> Install the following (copy/paste):
```

sudo apt-get install --reinstall linux-headers-generic-lts-quantal build-essential dkms linux-backports-modules-cw-3.6-$(grep CODE /etc/lsb-release | cut -c18-28)-$( uname -r | cut -c10-23) 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```
Clean up the configuration:```

sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Shutdown for 10 minutes without any current source and restart.


Hi praseodym. Could you please explain the gist of what these commands do? 
What is this that I'm installing and why?
What are these that I'm deleting and why?
Thanks.

---

### Post by praseodym on 2013-07-15
First three commands: Updating the driver, installing the firmware which is missing and installing the compilation tools.

Second three: Deleting the config files of the already uninstalled STA driver

---

### Post by easchmoe on 2013-07-15
> **praseodym said:**
> First three commands: Updating the driver, installing the firmware which is missing and installing the compilation tools.

Second three: Deleting the config files of the already uninstalled STA driver

OK I did that.
The config files are already non-existent when I tried the deletes.
Shutdown the laptop. Removed the battery. Restarted.

I'm getting a connection here at work but it's sputtery just like what I described in the original post. (connect 3 seconds, disconnect for another 4).
I'm downloading a large file and I'm monitoring the network activity.
Video streaming is also affected. 
Using the original STA drivers, I consistently got solid connections with no disconnect.

UPDATE: I just tried connecting to my home wifi and it still won't connect.

---

