---
title: "NetGear WNA3100 trouble (yet another)"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by Light Knight 22 on 2011-09-06
Hello,

I know these problems are very redundant, so I excuse myself in advance.

I have a Netgear WNA3100 (Not WNAD3100) on my new desktop; it works fine on windows. When it comes to running it on Ubuntu, things weren't as smooth as expected. Please note that I only have internet connection on windows, and I have no Wired connection on Ubuntu. I've downloaded some packages on the windows partition and had to install them from there.

I have Ubuntu 11.04 64 bit, it has never been connected to the internet.

I've read a few other threads on the subject (notably [this one]("http://ubuntuforums.org/archive/index.php/t-885520.html")), and this is what I've done so far with their help:


[LIST]
[*]Downloaded **ndiswrapper-common**, **ndiswrapper-utils-1.9**, and **ndisgtk** on my windows partition, booted into Ubuntu and installed them successfully.
[*]Opened **Windows Wireless Drivers**
[*]Add driver
[*]Found my .inf at **C:\programfiles (x86)\netgear\wna3100\drivers\win764\bcmwlhigh6.inf**
[*]I made sure my Dongle is connected and the LED is on
[*]It says** unable the detect hardware** or something of the like.
[/LIST]
I suspect most of the problem is due to the 64 bit? Anyway, any help is appreciated. I have some experience with Ubuntu, but not much. Also, as much as possible I would like to use windows to download needed items instead of going up to the router, but if it is really needed I can go upstairs and use the wired connection for crucial steps. 

Thanks a bunch!

---

### Post by walt.smith1960 on 2011-09-07
What Windows OS did you get the files from?  NDISwrapper only works with XP drivers.  Vista or Win7 drivers may appear to install but won't work. If you're using Ubuntu 64 bit you'd need XP 64 bit drivers.  Ditto 32 bit.  Sorry in advance if you already know this. Here is a success story using NDISwrapper including a driver source:
[http://ubuntuforums.org/showthread.php?p=11199585](http://ubuntuforums.org/showthread.php?p=11199585)

---

### Post by praseodym on 2011-09-07
Can you show the outputs of

```
uname -a
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

Edit: One of your links shows the **WNAD3100** which you noted out _not_ to have.

---

### Post by Light Knight 22 on 2011-09-07
Thanks for the fast response. 

> **walt.smith1960 said:**
> What Windows OS did you get the files from?  NDISwrapper only works with XP drivers.  Vista or Win7 drivers may appear to install but won't work. If you're using Ubuntu 64 bit you'd need XP 64 bit drivers.  Ditto 32 bit.  Sorry in advance if you already know this. Here is a success story using NDISwrapper including a driver source:
[http://ubuntuforums.org/showthread.php?p=11199585](http://ubuntuforums.org/showthread.php?p=11199585)

I did not know that! I'm running Win7, and that's where I took my drivers. I tryed using the Netgear drivers found in that link you posted, but obviously they weren't for my Adapter. 

So what you're saying is if I can get the XP .inf and .sys files for WNA3100, it 'should' work?

> **praseodym said:**
> Can you show the outputs of

```
uname -a
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```Edit: One of your links shows the **WNAD3100** which you noted out _not_ to have.

Yes, I'm aware that thread was about the WNAD3100, I was simply using it as a guide. Thanks. Here's the output:

```


darcy@Absolution:~$ uname -a
Linux Absolution 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
darcy@Absolution:~$ 
darcy@Absolution:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0b05:179c ASUSTek Computer, Inc. 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 0846:9020 NetGear, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c218 Logitech, Inc. Logitech RumblePad 2 USB
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
darcy@Absolution:~$ 
darcy@Absolution:~$ lsmod
Module                  Size  Used by
ndiswrapper           249811  0 
isofs                  40283  1 
parport_pc             36959  0 
ppdev                  17113  0 
rfcomm                 47694  8 
snd_hda_codec_hdmi     28103  4 
binfmt_misc            17565  1 
sco                    18131  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
joydev                 17606  0 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nouveau               682322  2 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
eeepc_wmi              19323  0 
sparse_keymap          13898  1 eeepc_wmi
snd_timer              29602  2 snd_pcm,snd_seq
btusb                  18600  2 
bluetooth              72448  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
ttm                    76664  1 nouveau
drm_kms_helper         42136  1 nouveau
drm                   227495  4 nouveau,ttm,drm_kms_helper
xhci_hcd               77643  0 
i2c_algo_bit           13400  1 nouveau
video                  19438  1 nouveau
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
hid_logitech           17693  0 
ff_memless             13097  1 hid_logitech
usbhid                 46956  1 hid_logitech
hid                    91020  2 hid_logitech,usbhid
ahci                   25951  4 
libahci                26642  1 ahci
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
e1000e                159096  0 
darcy@Absolution:~$ 
darcy@Absolution:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

darcy@Absolution:~$ 
darcy@Absolution:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
darcy@Absolution:~$ 
darcy@Absolution:~$ sudo iwlist scan

```

---

### Post by praseodym on 2011-09-07
Try this driver alternatively:

[http://media.cdn.ubuntu-de.org/forum/attachments/2612284/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2612284/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

---

### Post by Light Knight 22 on 2011-09-08
> **praseodym said:**
> Try this driver alternatively:

[http://media.cdn.ubuntu-de.org/forum/attachments/2612284/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2612284/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

I'm sorry, it didn't work. I added the 64 bit inf file with windows wireless driver and my screen showed the attached picture. Every time I boot into Ubuntu, all I see is this. I can still use the key board and mouse, I just can't see a thing I'm clicking on. I guess I can still open up the terminal via hot key and type something to reset or stop it, I'm just not sure what.

Thanks.

---

### Post by praseodym on 2011-09-08
Reboot/Hard-Reset it and hold the SHIFT-Button during booting, you will enter the grub menu with this. Choose "recovery mode" and "root"-mode there and type the following (without "sudo"):

```
modprobe -rf ndiswrapper
rm /etc/modprobe.d/ndiswrapper.conf
rm -r /etc/ndiswrapper/*
depmod -a
shutdown -r now
```
Type carefully :!: especially the second one. These command remove the module and its configuration.

---

### Post by Light Knight 22 on 2011-09-12
Thanks! Ubuntu is up an running again. 

I reinstalled ndiswrapper and ndisgtk, now I need to find a working driver.

---

### Post by Light Knight 22 on 2011-09-13
If anyone can find one in the wild, that would be great! I was unable to find one. I have found a ton of 32 bit XP drivers (bcmwlhigh5.inf) but no 64 bit **XP** (bcmwlhigh6.inf). 

In theory, if I had a friend who ran XP 64 bit, I could install the driver on that computer and then get the inf and sys file right? Unfortunately, I don't know anyone with that specific OS.

---

### Post by Light Knight 22 on 2011-09-29
Ok, I think I made some progress, but I need some help. 

I hadn't had my computer connected to the Internet when I first installed Ubuntu, and I never got any updates. 

Now that I've brought it to a wired connection and ran the update manager for the first time, things have changed. Namely, that screen that I posted above does not present itself when I try to use a windows driver. Now when I try installing the Broadcom bcmn43xx64.inf file (while the dongle is plugged in) I get this message: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

Any ideas would be appreciated.

---

### Post by praseodym on 2011-09-29
Rename the file:

```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```
and reboot.

---

