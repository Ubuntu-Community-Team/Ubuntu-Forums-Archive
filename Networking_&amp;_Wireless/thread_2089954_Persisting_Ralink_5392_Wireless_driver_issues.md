---
title: "Persisting Ralink 5392 Wireless driver issues"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by jgomez2 on 2012-11-30
Hello Ubuntu Community,

I am using Ubuntu 12.10.

I was able to download and unzip: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO

The file is sitting on my desktop. 

I did:

cd 2011*
emacs -nw os/linux/config.mk

I have changed the lines to look like this:

# Support Wpa_Supplicant
# i.e. wpa_supplicant -Dralink
HAS_WPA_SUPPLICANT=y


# Support Native WpaSupplicant for Network Maganger
# i.e. wpa_supplicant -Dwext
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

I closed and saved. Then I tried:

sudo su 
make

This was the error I got:

root@SJ:/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# make
make -C tools
make[1]: Entering directory `/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.5.0-18-generic/build SUBDIRS=/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make: *** /lib/modules/3.5.0-18-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

I understand that there is no directory there, but I dont imagine that is truly the source of the problem.

Can someone help please?

---

### Post by chili555 on 2012-11-30
> but I dont imagine that is truly the source of the problem.

Can someone help please?Oh, yes, indeed, it is! It's clear evidence you don't have the prerequisites installed. With an ethernet connection, please do:```
sudo apt-get install build-essential linux-headers-generic
```Then try again:```
make
sudo make install
```

---

### Post by jgomez2 on 2012-11-30
> **chili555 said:**
> Oh, yes, indeed, it is! It's clear evidence you don't have the prerequisites installed. With an ethernet connection, please do:```
sudo apt-get install build-essential linux-headers-generic
```Then try again:```
make
sudo make install
```


Should I then try modprobe rt5390sta? Or would a simple restart suffice?

---

### Post by chili555 on 2012-11-30
> **jgomez2 said:**
> Should I then try modprobe rt5390sta? Yes, please.

---

### Post by jgomez2 on 2012-11-30
Ok so i did
```
 sudo modprobe rt5390sta 
```

It is now up and running. Is there anything you suggest to do in order to make this a permanent fix? When I had 12.04 my WLAN would work until I would download a new release (or patch or whatever the term is) and then I would have to do the steps all over again. If no, thank you for your time and prompt replies.

---

### Post by chili555 on 2012-12-01
When a new kernel version, also known as linux-image, is installed by Update Manager, you will need to recompile for the later kernel version:```
cd Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
make clean
make
sudo make install
sudo modprobe rt5390sta
```Glad it's working!

---

### Post by jgomez2 on 2012-12-03
jgomez2@SJ:~/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ make
make -C tools
make[1]: Entering directory `/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
jgomez2@SJ:~/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ sudo make
make -C tools
make[1]: Entering directory `/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2


it appears to be a similar problem as before with the missing directory...

---

### Post by chili555 on 2012-12-03
> it appears to be a similar problem as before with the missing directory...Yes, indeed, and the fix is the same:```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by jgomez2 on 2012-12-03
jgomez2@SJ:~/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for jgomez2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libjasper1:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 linux-headers-3.5.0-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I then tried make with and got the same error. :(

---

### Post by chili555 on 2012-12-04
Please reboot. Next, post:```
lsb_release -a
uname -a
arch
sudo dpkg -s linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.

---

### Post by jgomez2 on 2012-12-04
```

jgomez2@SJ:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

```

```

jgomez2@SJ:~$ uname -a
Linux SJ 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```

jgomez2@SJ:~$ arch
x86_64

```

```

jgomez2@SJ:~$ sudo dpkg -s linux-headers-`uname -r`
[sudo] password for jgomez2: 
dpkg-query: package 'linux-headers-3.5.0-17-generic' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

---

### Post by chili555 on 2012-12-04
> package 'linux-headers-3.5.0-17-generic' is not installed and no information is availableVery interesting, especially in light of this:> The following packages were automatically installed and are no longer required:
libjasper1:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 [COLOR="Red"]linux-headers-3.5.0-17[/COLOR]
Use 'apt-get autoremove' to remove them.Clearly, in order to compile the driver, linux-headers matching the kernel version you are compiling the driver for are required. linux-headers-generic *_can't_* be installed correctly, no matter what it says here:> linux-headers-generic is already the newest version.Please do:```
sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get install --reinstall linux-headers-generic
```Now try to compile the driver again.

I have seen this missing headers mess a few times here on the forum and I'd love to know how it happens. I can't seem to trigger it myself.

---

### Post by jgomez2 on 2012-12-04
Ok, the WLAN card seems to be working.

I first restarted my computer (habit I guess). While it was rebooting I unplugged my cat5 and when the computer reloaded I connected to my wireless network. It connected for about 60seconds, in that time I tried to open Pidgin, and this forum so I could congratulate you again. Neither application seemed to be connecting, I was promptly disconnected from my network. I tried to reconnect and my computer froze. 

I restarted again..it connected to my wireless network and I got this error before it froze again:

> 
[B]Connection Activation Failed
[/B](4) Did not receive reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired or the network connection was broken


While yes you got the card working, do you have any familiarity with this? Since my network is useable on my windows boot I have a feeling this is a settings problem somewhere in ubuntu.

---

### Post by chili555 on 2012-12-04
Let's see:```
lsmod | grep -e rt2 -e rt5
dmesg | grep -e rt2 -e rt5
```Thanks.

I suspect a competing driver. Did you complete the driver compile or did the wireless connect magically?

---

### Post by jgomez2 on 2012-12-04
> 
I suspect a competing driver. Did you complete the driver compile or did the wireless connect magically?


....Yes??? I let the command line do its thing until text stopped scrolling and it asked me for the next command. It was at this point that I did the restart...did I goof?

```

jgomez2@SJ:~/Desktop$ lsmod | grep -e rt2 -e rt5
rt5390sta            1456505  0 
rt2800pci              18528  0 
rt2800lib              58685  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14475  1 rt2800pci
rt2x00lib              54891  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              539908  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              206566  2 rt2x00lib,mac80211
eeprom_93cx6           13302  1 rt2800pci

```

```

jgomez2@SJ:~/Desktop$ dmesg | grep -e rt2 -e rt5
[   14.012573] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x5392 detected.
[   14.012619] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   14.123756] rt5390sta: module license 'unspecified' taints kernel.
[   14.125248] register rt2860
[   16.245290] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_hdmi coretemp rt5390sta(PO) kvm ghash_clmulni_intel aesni_intel cryptd aes_x86_64 psmouse snd_usb_audio snd_usbmidi_lib snd_hda_codec_idt gpio_ich snd_hda_intel snd_hda_codec snd_hwdep microcode snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device joydev rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib mac80211 uvcvideo videobuf2_core videodev videobuf2_vmalloc mac_hid videobuf2_memops serio_raw radeon cfg80211 snd eeprom_93cx6 lpc_ich soundcore snd_page_alloc ttm drm_kms_helper drm i2c_algo_bit lp mei parport uas usb_storage hid_generic usbhid hid r8169
[   16.245348]  [<ffffffffa05e7710>] RtmpAsicSendCommandToMcu+0x780/0x8b0 [rt5390sta]
[   16.245359]  [<ffffffffa0567b59>] AsicSendCommandToMcuBBP+0x29/0x30 [rt5390sta]
[   16.245366]  [<ffffffffa053b3e9>] NICInitBBP+0x12c9/0x2b10 [rt5390sta]
[   16.245374]  [<ffffffffa05e75e1>] ? RtmpAsicSendCommandToMcu+0x651/0x8b0 [rt5390sta]
[   16.245384]  [<ffffffffa053d2eb>] NICInitializeAsic+0x30b/0x5b0 [rt5390sta]
[   16.245390]  [<ffffffffa053d729>] NICInitializeAdapter+0x199/0x6b0 [rt5390sta]
[   16.245405]  [<ffffffffa0544b14>] rt28xx_init+0x2a4/0x710 [rt5390sta]
[   16.245413]  [<ffffffffa05c35c5>] rt28xx_open+0x95/0x100 [rt5390sta]
[   16.245422]  [<ffffffffa0554ef3>] RTMP_COM_IoctlHandle+0x543/0x5a0 [rt5390sta]
[   16.245433]  [<ffffffffa05c2fe7>] MainVirtualIF_open+0x47/0xe0 [rt5390sta]
[   16.245441]  [<ffffffffa05c3530>] ? RtmpOSIRQRequest+0xe0/0xe0 [rt5390sta]
[   16.245449]  [<ffffffffa05c2f10>] ? RtmpNetEthConvertDevSearch+0x90/0x90 [rt5390sta]
[   16.314749] <==== rt28xx_init, Status=0
[   16.366608] <==== rt28xx_init, Status=0
[   16.536837] <==== rt28xx_init, Status=0
[   16.561812] <==== rt28xx_init, Status=0

```

I dont know if this is relevant, but for the time being since it seemed to be freezing my computer, I turned the 'enable wireless' option to unchecked.

---

### Post by chili555 on 2012-12-04
A conflict, indeed. Please do:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us how it's working.

---

### Post by jgomez2 on 2012-12-04
I did those commands, restarted my computer and had the same issues...it connected much faster, but when i tried to open google.com ...it quickly disconnected me from my network, and came with the same message as before...

I checked my /etc/modprobe.d/blacklist.conf just in case the 5390 was blacklisted...it wasnt... i again did the check from before:

```

jgomez2@SJ:~/Desktop$ lsmod | grep -e rt2 -e rt5
rt5390sta            1456505  1 
rt2800pci              18528  0 
rt2800lib              58685  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14475  1 rt2800pci
rt2x00lib              54891  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              539908  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              206566  2 rt2x00lib,mac80211
eeprom_93cx6           13302  1 rt2800pci

```

```
jgomez2@SJ:~/Desktop$ dmesg | grep -e rt2 -e rt5
[   14.784189] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x5392 detected.
[   14.784237] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   14.914090] rt5390sta: module license 'unspecified' taints kernel.
[   14.915661] register rt2860
[   17.195276] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi coretemp kvm ghash_clmulni_intel aesni_intel cryptd aes_x86_64 snd_hda_codec_idt rt5390sta(PO) gpio_ich joydev snd_hda_intel snd_hda_codec snd_usb_audio snd_pcm snd_hwdep snd_usbmidi_lib snd_seq_midi snd_seq_midi_event snd_seq microcode snd_rawmidi snd_timer snd_seq_device uvcvideo videobuf2_core videodev videobuf2_vmalloc videobuf2_memops snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib mac80211 psmouse serio_raw lpc_ich mac_hid soundcore snd_page_alloc cfg80211 eeprom_93cx6 radeon ttm mei drm_kms_helper drm i2c_algo_bit lp parport usb_storage uas hid_generic usbhid hid r8169
[   17.195334]  [<ffffffffa0521710>] RtmpAsicSendCommandToMcu+0x780/0x8b0 [rt5390sta]
[   17.195345]  [<ffffffffa04a1b59>] AsicSendCommandToMcuBBP+0x29/0x30 [rt5390sta]
[   17.195352]  [<ffffffffa04753e9>] NICInitBBP+0x12c9/0x2b10 [rt5390sta]
[   17.195360]  [<ffffffffa05215e1>] ? RtmpAsicSendCommandToMcu+0x651/0x8b0 [rt5390sta]
[   17.195370]  [<ffffffffa04772eb>] NICInitializeAsic+0x30b/0x5b0 [rt5390sta]
[   17.195376]  [<ffffffffa0477729>] NICInitializeAdapter+0x199/0x6b0 [rt5390sta]
[   17.195384]  [<ffffffffa047eb14>] rt28xx_init+0x2a4/0x710 [rt5390sta]
[   17.195393]  [<ffffffffa04fd5c5>] rt28xx_open+0x95/0x100 [rt5390sta]
[   17.195402]  [<ffffffffa048eef3>] RTMP_COM_IoctlHandle+0x543/0x5a0 [rt5390sta]
[   17.195413]  [<ffffffffa04fcfe7>] MainVirtualIF_open+0x47/0xe0 [rt5390sta]
[   17.195422]  [<ffffffffa04fd530>] ? RtmpOSIRQRequest+0xe0/0xe0 [rt5390sta]
[   17.195430]  [<ffffffffa04fcf10>] ? RtmpNetEthConvertDevSearch+0x90/0x90 [rt5390sta]
[   17.279606] <==== rt28xx_init, Status=0
[   17.305478] <==== rt28xx_init, Status=0
[   17.517498] <==== rt28xx_init, Status=0
[   17.549241] <==== rt28xx_init, Status=0

```

just in case you wanted the info.

---

### Post by chili555 on 2012-12-04
Let's see:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
ls /etc/modprobe.d
```This just keeps getting weirder!

---

### Post by jgomez2 on 2012-12-04
```

jgomez2@SJ:~/Desktop$ cat /etc/modprobe.d/blacklist.conf 
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
blackist rt2800pci

```

```

jgomez2@SJ:~/Desktop$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc

```

```

jgomez2@SJ:~/Desktop$ ls /etc/modprobe.d/
total 40K
-rw-r--r-- 1 root root 2.5K Oct  7 20:34 alsa-base.conf
-rw-r--r-- 1 root root  325 Mar 18  2011 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1.6K Dec  4 10:29 blacklist.conf
-rw-r--r-- 1 root root  210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r-- 1 root root  677 Oct  1 08:26 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Oct  7 20:34 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 Nov 30 21:12 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1.1K Mar 18  2011 blacklist-watchdog.conf
-rw-r--r-- 1 root root  347 Oct  1 08:26 iwlwifi.conf
-rw-r--r-- 1 root root   30 Aug  2 03:21 vmwgfx-fbdev.conf

```

---

### Post by chili555 on 2012-12-04
I honestly haven't any idea if rt5390sta or rt2800pci will work better. The only way to find out is to try first one and then the other. Obviously, you downloaded and compiled rt5390sta because rt2800pci wasn't working as expected, so let's eliminate it first. We see from your readings that it is properly blacklisted but loads anyway! Let's try a bit harder:```
sudo su
echo "blacklist rt2800lib" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00pci" >> /etc/modprobe.d/blacklist.conf
exit
```Now reboot and run and post:```
lsmod | grep -e rt2 -e rt5
```We hope and we pray that rt2800 and its entourage is not loading now.

I see you have a file /etc/modprobe.d/iwlwifi.conf. It is for the driver iwlwifi that covers Intel devices. I doubt it is doing anything to help you. I suggest you remove it:```
sudo rm /etc/modprobe.d/iwlwifi.conf
```

---

### Post by jgomez2 on 2012-12-04
```

jgomez2@SJ:~$ lsmod | grep -e rt2 -e rt5
rt5390sta            1456505  1 
rt2800pci              18528  0 
rt2800lib              58685  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14475  1 rt2800pci
rt2x00lib              54891  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              539908  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              206566  2 rt2x00lib,mac80211
eeprom_93cx6           13302  1 rt2800pci

```

And I trustingly took your advice with the removal of that file.

```

jgomez2@SJ:~$ cat /etc/modprobe.d/blacklist.conf 
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
blackist rt2800pci
blacklist rt2800lib
blacklist rt2x00lib
blacklist rt2x00pci

```

---

### Post by chili555 on 2012-12-04
Ah, ha! I see it! Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change this line:```
blackist rt2800pci
```To this:```
black[COLOR="Red"]l[/COLOR]ist rt2800pci
```Proofread, save and close gedit and reboot.

---

### Post by jgomez2 on 2012-12-04
Unsurprisingly you were correct:

```

jgomez2@SJ:~$ lsmod | grep -e rt2 -e rt5
rt5390sta            1456505  1 

```However, when I rebooted without the ethernet, I got to my desktop and not too long after my screen went black with an extensive list of what looked like errors on it and froze...so i had to hold down the power button to hard shutdown, rebooted, and the second time when it went black i took a few pictures. Since my monitors are widescreen to get the whole image would take a while but here is the clear one.

---

### Post by jgomez2 on 2012-12-04
Im certainly glad you like problem solving cuz this is driving me crazy.

---

### Post by chili555 on 2012-12-04
If you reboot *with* the ethernet connected, can you remove the driver?```
cd Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
sudo su
make uninstall
modprobe -r rt5390sta
exit
```I fear we must then troubleshoot rt2800pci.

---

### Post by jgomez2 on 2012-12-04
```

jgomez2@SJ:~$ cd Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
jgomez2@SJ:~/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ sudo su
[sudo] password for jgomez2: 
root@SJ:/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# make uninstall
make -C /home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 uninstall
make[1]: Entering directory `/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt5390sta.ko
/sbin/depmod -a 3.5.0-17-generic
make[1]: Leaving directory `/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
root@SJ:/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# modprobe -r rt5390sta
FATAL: Module rt5390sta not found.
root@SJ:/home/jgomez2/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# exit
exit

```

Should I go ahead and un-blacklist the rt2800?

---

### Post by chili555 on 2012-12-04
> **jgomez2 said:**
> 

Should I go ahead and un-blacklist the rt2800?Yes, please and all its cousins, too. Then do:```
sudo modprobe rt2800pci
```Does it connect? Freeze? Etc.?

---

### Post by jgomez2 on 2012-12-04
```

jgomez2@SJ:~/Desktop$ lsmod | grep -e rt2 -e rt5
rt2800pci              18528  0 
rt2800lib              58685  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14475  1 rt2800pci
rt2x00lib              54891  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              539908  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              206566  2 rt2x00lib,mac80211
eeprom_93cx6           13302  1 rt2800pci

```

It did not freeze. I removed the modules, added rt2800, restarted with the ethernet...works fine. Restarted with ethernet unplugged, works fine. However now there is absolutely zero WLAN connectivity. At least we got the black screen gone :D

---

### Post by chili555 on 2012-12-04
> **jgomez2 said:**
> 
It did not freeze. I removed the modules, added rt2800, restarted with the ethernet...works fine. Restarted with ethernet unplugged, works fine. However now there is absolutely zero WLAN connectivity. At least we got the black screen gone :DBefore I take a powerful tranquilizer, are you saying the *_wireless_* works and connects with the ethernet connected but not otherwise? How are you sure it's the wireless connection and not ethernet? Does wlan0 have an IP address?```
ifconfig
```:confused: :confused:

---

### Post by jgomez2 on 2012-12-04
NO TRANQs!!!

To be more clear. After we did modprobe rt5390sta the wireless did come on. It did work....when the ethernet was plugged in. On windows I have had trouble in the past using LAN/WLAN when the other is active. Which is why I would restart my comp without the ethernet in order to test the wireless. It is when I would restart without the cable that the comp would go black with that error. When I would plug in the ethernet and restart, it would work fine.

Now, without rt5390sta it is getting nothing.

---

### Post by chili555 on 2012-12-04
Let's troubleshoot rt2800pci.```
dmesg | grep rt2
iwconfig
sudo iwlist wlan[COLOR="Red"]0[/COLOR] scan  [COLOR="Red"]<-or whatever iwconfig says your interface is, if not wlan0[/COLOR]
rfkill list all
```

---

### Post by jgomez2 on 2012-12-05
```

jgomez2@SJ:~/Desktop$ dmesg | grep rt2
[   15.546747] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x5392 detected.
[   15.546797] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.

```

```

jgomez2@SJ:~/Desktop$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

```

---

### Post by chili555 on 2012-12-05
> phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x5392 detected.That's very weird because the driver does include your device:```
$ modinfo rt2800pci | grep 5392
alias:          pci:v00001814d0000[COLOR="Red"]5392[/COLOR]sv*sd*bc*sc*i*

```The driver was patched some time ago to add your device: [http://www.spinics.net/lists/linux-wireless/msg90992.html](http://www.spinics.net/lists/linux-wireless/msg90992.html)

Let's build the compat-wireless suite and see if we can fix this. Hook up the ethernet temporarily and do:```
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1.tar.bz2
tar -xvjf compat-wireless-3.5.4-1.tar.bz2
cd compat-wireless-3.5.4-1
./scripts/driver-select rt2x00
make
sudo make install
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
```Any improvement?

---

### Post by jgomez2 on 2012-12-05
Nothing has changed that I can see. I cant dis/enable wireless.

---

### Post by chili555 on 2012-12-05
That's a stubborn wireless device you have there! Let's have a look at:```
sudo modprobe rt2800pci
dmesg | grep rt2
modinfo rt2800pci | grep 5392
```Thanks.

---

### Post by jgomez2 on 2012-12-06
> 
			 		   		 		 		That's a stubborn wireless device you have there!


Its always me :(


```

jgomez2@SJ:~/Desktop$ sudo modprobe rt2800pci
[sudo] password for jgomez2: 
jgomez2@SJ:~/Desktop$ dmesg | grep rt2
[   15.140221] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x5392 detected.
[   15.140262] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
jgomez2@SJ:~/Desktop$ modinfort2800pci | grep 5392
modinfort2800pci: command not found
jgomez2@SJ:~/Desktop$ modinfo rt2800pci | grep 5392
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*

```

Dont thank me, Im the cause of your ongoing war against this WLAN card :P

---

### Post by chili555 on 2012-12-06
Let's double-check the integrity of the required firmware:```
md5sum /lib/firmware/rt2860.bin
```Here is what I get: ```
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin
```If the driver is not defective and the firmware is not defective, then I wonder if the device may be defective. Does it work in other computers and operating systems?

---

### Post by jgomez2 on 2012-12-06
```

jgomez2@SJ:~/Desktop$ md5sum /lib/firmware/rt2860.bin
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin

```

The device works when I boot up windows.

---

### Post by chili555 on 2012-12-06
> **jgomez2 said:**
> The device works when I boot up windows.We may try the Windows driver, then. May I see:```
lspci -nn | grep 0280
```Thanks.

---

### Post by jgomez2 on 2012-12-06
```

jgomez2@SJ:~/Desktop$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Ralink corp. Device [1814:5392]

```

---

### Post by chili555 on 2012-12-06
I wonder if this is actually a 64-bit issue. I have been researching this extensively and, so far, found several cases where the device works well either with the driver you compiled that froze your computer or with the default in-kernel rt2800pci driver; all in 32-bit. Are you willing to download and burn the 32-bit version and try it live ('Try Ubuntu') so we can see if your device works?

I am continuing to search for the 64-bit XP Windows files. No luck so far.

---

### Post by jgomez2 on 2012-12-06
I honestly don't know the difference between the 2 (64 v 32 bit). I would not mind. The hardest part would be to remember how to do port forwarding.

---

### Post by jgomez2 on 2012-12-07
Ok,

I have reinstalled ubuntu, I believe in 32bit form this time.

Now how should I proceed?

---

### Post by chili555 on 2012-12-07
Let's have a look at:```
sudo modprobe rt2800pci
dmesg | grep rt2
iwconfig
```Thanks.

---

### Post by jgomez2 on 2012-12-09
```

jgomez2@SJ:~/Desktop$ sudo modprobe rt2800pci
[sudo] password for jgomez2: 
jgomez2@SJ:~/Desktop$ dmesg | grep rt2
[   12.728432] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x5392 detected.
[   12.728435] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
jgomez2@SJ:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```


Should I perhaps try getting the other drivers again?

---

### Post by chili555 on 2012-12-10
> **jgomez2 said:**
> Should I perhaps try getting the other drivers again?Yes, please. If you need assistance, please post back and I'll be glad to help.

---

### Post by jgomez2 on 2012-12-11
Succcess! 

Chili... Thanks a bunch. Sorry for giving you a headache.

I hope Ubuntu knows their 64-bit version is goofing up!

---

### Post by chili555 on 2012-12-11
Awesome! I'm very glad it's working.

---

### Post by tdruiva on 2013-07-10
One thing that resolved for me was:
- After install Ubuntu 13.04 x86 on Dell Vostro 3500 I made all updates using a open wireless network;
- Restart;
- Applied this solution: [http://ubuntuforums.org/showthread.php?t=2140211&p=12625902#post12625902](http://ubuntuforums.org/showthread.php?t=2140211&p=12625902#post12625902)
- Restart again;
Now I can connect with closed wireless network :lolflag:

---

### Post by chili555 on 2013-07-10
> **tdruiva said:**
> One thing that resolved for me was:
- After install Ubuntu 13.04 x86 on Dell Vostro 3500 I made all updates using a open wireless network;
- Restart;
- Applied this solution: [http://ubuntuforums.org/showthread.php?t=2140211&p=12625902#post12625902](http://ubuntuforums.org/showthread.php?t=2140211&p=12625902#post12625902)
- Restart again;
Now I can connect with closed wireless network :lolflag:I suppose I may be confused. The subject of this thread is a Ralink 5392 card; however, the link you gave is for a Broadcom card. What am I missing?

---

