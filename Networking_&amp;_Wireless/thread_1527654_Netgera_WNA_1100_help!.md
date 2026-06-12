---
title: "Netgera WNA 1100 help!"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by Saeger on 2010-07-09
Okay I've got a Netgear N-150 WNA 1100 USB WiFi adapter, it doesn't work in Ubuntu it's not supported.  There should be a way to make it work with ndiswrapper.  I tried and failed before and due to other non related circumstances I had to reinstall Ubuntu.  Could someone please walk me through the steps to install ndiswrapper and it's dependency's on a fresh Ubuntu installation that cannot connect to the internet.  Thank you.

---

### Post by Saeger on 2010-07-09
btt

---

### Post by gordintoronto on 2010-07-09
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Saeger on 2010-07-09
I installed Ndiswrapper and the drivers as per the instructions.  Ndiswrapper says the driver is installed and the device is present, but no wireless networks appear in the wireless network applet.  What should I do to troubleshoot?  Thanks.

---

### Post by Saeger on 2010-07-10
btt.

---

### Post by Saeger on 2010-07-10
btt..

---

### Post by Saeger on 2010-07-10
output of iwconf if that helps anybody.

```
user@user-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:150 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Saeger on 2010-07-10
btt..

---

### Post by Saeger on 2010-07-10
bump yet again.

---

### Post by gordintoronto on 2010-07-10
"Connect to hidden network"

---

### Post by Saeger on 2010-07-10
Just tried "Connect to hidden network" with the same ssid I use in windows, no luck.  The graphic just spins and then it says disconnected.  Thanks for the attempt though.

---

### Post by Saeger on 2010-07-11
btt

---

### Post by flash63 on 2010-07-11
<hello,
i think this is a Wifi Stick witch Atheros-ath9k_htc Chipset. In this case you can use the latest Compat-Wireless driver package.

Show the output of
```
lsusb
uname -a
```

---

### Post by Saeger on 2010-07-11
```
user@user-desktop:~$ lsusb
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@user-desktop:~$ uname -a
Linux user-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

---

### Post by chili555 on 2010-07-11
How about letting us see:```
ndiswrapper -l
lsmod
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Lostboi45 on 2010-07-11
> **Saeger said:**
> I installed Ndiswrapper and the drivers as per the instructions.  Ndiswrapper says the driver is installed and the device is present, but no wireless networks appear in the wireless network applet.  What should I do to troubleshoot?  Thanks.

did you do a 'modprobe ndiswrapper' as root? That should get it going.

---

### Post by Saeger on 2010-07-12
[FONT=Verdana]Okay I ran the "modbrobe ndiswrapper" and got this error message
```
suuser@user-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for user: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```[/FONT]
What does that mean?

Then I ran chili555's code and got this
```
ser@user-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netathuw : driver installed
    device (0846:9030) present
user@user-desktop:~$ 
user@user-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
lp                      7028  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                674135  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
ppdev                   5259  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
parport_pc             25962  1 
soundcore               6620  1 snd
parport                32635  3 lp,ppdev,parport_pc
ati_agp                 5094  0 
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
ndiswrapper           184677  0 
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28820  0 
8139too                18545  0 
8139cp                 16186  0 
usb_storage            39425  0 
mii                     4381  2 8139too,8139cp
pata_atiixp             3148  3 
floppy                 53016  0 
sata_sil                6959  0 
user@user-desktop:~$ 
user@user-desktop:~$ sudo iwlist wlan0 scan
wlan0     No scan results


```

Thanks for your help.  I hope this can be fixed.

---

### Post by flash63 on 2010-07-12
> Bus 001 Device 002: ID 0846:9030 NetGear, Inc
Yep, Atheros ath9k_htc Chipset.

[http://www.linuxwireless.org/en/users/Drivers/ath9k_htc](http://www.linuxwireless.org/en/users/Drivers/ath9k_htc)

How to build the driver (iNet over LAN required):
```

sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2 
cd compat-wireless-2010*
./scripts/driver-select ath9k
make 
sudo make install

```
Get the Firmware:
```
http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree
```
Klick on "snapshot", save and extract the archive. Copy **ar9271.fw** as root into /lib/firmware

(btw. files ar7010.fw and ar7010_1_1.fw are not present in this archive and i don't know why)

Modulinfo:
```
modinfo ath9k_htc
filename:       /lib/modules/2.6.32-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       ar9271.fw
firmware:       ar7010_1_1.fw
firmware:       ar7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     5BD8A0F78B87B5DF3CF4100
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,compat_firmware_class,mac80211,led-class,ath9k_common,ath,cfg80211
vermagic:       2.6.32-23-generic SMP mod_unload modversions 586 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)

```

Test it
```
sudo modprobe -rf ndiswrapper
sudo modprobe ath9k_htc
dmesg | grep ath
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by chili555 on 2010-07-12
> Okay I ran the "modbrobe ndiswrapper" and got this error message
Code:

suuser@user-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for user: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored...That's not an error; it's a warning. You can fix it with:```
sudo cp /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```

---

### Post by Saeger on 2010-07-12
I did what chili555 suggested and I still get the same warning message.  I don't know why.  I would like to try the Compat-Wireless solution but I don't have a LAN connection.  My only internet access is through WiFi.  I have WiFi access on the desktop computer that I am trying to fix through Windows XP and I also have WiFi access on a laptop running Ubuntu.  Is there some way I can download the necessary files for Compat-Wireless on another computer copy them to the Ubuntu desktop then install them?  Thanks.

---

### Post by Saeger on 2010-07-12
Is there some way to download the Compat-Wireless application and dependencies on one computer and install them on another?  Instructions on how to do this would be much appreciated.  Thanks.

---

### Post by Saeger on 2010-07-12
btt

---

### Post by flash63 on 2010-07-13
Hello,
you can download the deb-Package here: [http://forum.ubuntuusers.de/post/2505448/](http://forum.ubuntuusers.de/post/2505448/)

You need compat-wireless-2010-07_11_ath9k_ath_htc__2.6.32-21_i386.deb in this case for the installed Kernel.

Installation of the firmware as described.

---

### Post by Saeger on 2010-07-13
Well, all that managed to do was corrupt my Linux kernel!  I had to reinstall Ubuntu.  I'm not sure what happened, but I bet It had something to do with Compat-Wireless.  Could it be incompatible in some way?  Is there anything else I could try to make the WiFi work that WONT corrupt the Linux kernel?

---

### Post by flash63 on 2010-07-13
> I had to reinstall Ubuntu.
This is not required. Start with the Root Recovery Console and remove the new Modules:
```
sudo rm -r /lib/modules/$(uname -r)/updates/*
sudo depmod -a
```
Restart

Install Kernel 2.6.32-22-generic (i386) for an alternativ selection: [http://packages.ubuntu.com/lucid/linux-image-2.6.32-22-generic](http://packages.ubuntu.com/lucid/linux-image-2.6.32-22-generic) and install [http://media.ubuntuusers.de/forum/attachments/2505448/compat-wireless-2010-07_11_ath9k_ath_htc__2.6.32-22_i386.deb](http://media.ubuntuusers.de/forum/attachments/2505448/compat-wireless-2010-07_11_ath9k_ath_htc__2.6.32-22_i386.deb)

The driver ath9k_htc is included in the package linux-image-2.6.35-020635rc4-generic_2.6.35-020635rc4_i386.deb (Mainline-Kernel)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc4-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc4-maverick/)

All versions can be selected in the Grub boot menu if the shift key is pressed during the boot process.

---

### Post by Yellow Pasque on 2010-07-23
Bump. Having the same issue. I'm using maverick and I want to use the native atk9k_htc driver. ndiswrapper isn't working for me on maverick because of the 2.6.35 kernel and this bug [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/590090](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/590090) .

So I've completely removed ndiswrapper (and its config files), blacklisted it, and set ath9k_htc to load at startup (i.e. I put it in /etc/modules). The firmware was already in /lib/firmware. The module loads fine, but I cannot seem to get an interface for it. iwconfig and ifconfig -a just show loopbak (lo) device. How do I get an interface? (wlan0 is set for dhcp in /etc/network/interfaces)
EDIT: I am not using network-manager.

---

### Post by Yellow Pasque on 2010-07-26
Ok. The latest compat-wireless tarball fixes it.

---

