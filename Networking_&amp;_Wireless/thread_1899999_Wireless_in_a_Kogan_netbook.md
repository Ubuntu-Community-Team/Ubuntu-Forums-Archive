---
title: "Wireless in a Kogan netbook"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by NewNerd99 on 2011-12-25
brushing some dust off a netbook and trying to work out why the wireless is not working....

The wireless detects my home network but it won't authenticate. Triple checked the password and confirmed a number of times.

I can't even see a wireless card in the list below?!?! What am I missing (glasses?)

Works fine in Windows 7

Hope I can get it running again.

Cheers
Chris

ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
ubuntu@ubuntu:~$

---

### Post by praseodym on 2011-12-25
Hi,

maybe its an (old) PCMCIA-card or an internal USB. Please show:

```
pccardctl info
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by NewNerd99 on 2011-12-25
Thanks Praseodym,
I can see in the lsusb that it thinks I have a *VIA Technologies, Inc. VIA VNT-6656 [WiFi 802.11b/g USB Dongle]* Its a built in wireless so I'm unsure if I should be treating it as a USB dongle or installed? 

Reading the sticky gives a different path to follow for each.

Also funny how it can see my network but not *authenticate*, could I be missing something in the settings?

I will try to find an updated driver for that chipset though.

Thanks again and Merry Christmas.

de Chris

**pccardctl info:**
ubuntu@ubuntu:~$ pccardctl info
ubuntu@ubuntu:~$ 

**lsusb:**
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05dc:a731 Lexar Media, Inc. 
Bus 001 Device 004: ID 160a:3184 VIA Technologies, Inc. VIA VNT-6656 [WiFi 802.11b/g USB Dongle]
Bus 001 Device 005: ID 0ac8:3420 Z-Star Microelectronics Corp. Venus USB2.0 Camera
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
ubuntu@ubuntu:~$ 

**lsmod:**
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
dm_crypt               22565  0 
parport                40930  3 parport_pc,ppdev,lp
uvcvideo               67271  0 
snd_hda_codec_realtek   254125  1 
vt6656_stage          204441  0 
snd_hda_intel          24262  2 
videodev               85626  1 uvcvideo
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  1 
uas                    17699  0 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
r8169                  43104  0 
video                  18908  1 i915
ubuntu@ubuntu:~$

**iwconfig**
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11-a/b/g  ESSID:""  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=0/255  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ 

**rfkill list**
ubuntu@ubuntu:~$ rfkill list
ubuntu@ubuntu:~$

---

### Post by praseodym on 2011-12-25
Here it is:
```
Bus 001 Device 004: ID 160a:3184 VIA Technologies, Inc. VIA VNT-6656 [WiFi 802.11b/g USB Dongle]
```

> vt6656_stage 204441 0 
The driver is loaded. Check:

```
dmesg | egrep 'vt6|vnt|country'
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
cat /var/lib/NetworkManager/NetworkManager.state
sudo iwlist scan
iwlist chan
```
Which Ubuntu version is that? Mark your network in "sudo iwlist scan"

---

### Post by NewNerd99 on 2011-12-25
Running 11.10 from a USB stick.

***Mark your network in "sudo iwlist scan*** Not sure what you mean on that point?

Thanks again for your help so far.

Chris

ubuntu@ubuntu:~$ dmesg | egrep 'vt6|vnt|country'
[   48.669414] vt6656_stage: module is from the staging directory, the quality is unknown, you have been warned.
[   48.938048] usbcore: registered new interface driver vt6656
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

ubuntu@ubuntu:~$


ubuntu@ubuntu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain BigPond
search BigPond
nameserver 10.0.0.138
ubuntu@ubuntu:~$


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
ubuntu@ubuntu:~$


ubuntu@ubuntu:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
ubuntu@ubuntu:~$


ubuntu@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : Invalid argument

ubuntu@ubuntu:~$


ubuntu@ubuntu:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

eth1      14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.437 GHz (Channel 6)

ubuntu@ubuntu:~$

---

### Post by praseodym on 2011-12-25
Which encryption mode do you use? First try unencrypted, then WEP, WPA, mixed WPA/WPA2, and finally WPA2-AES if possible.

---

### Post by NewNerd99 on 2011-12-25
Unencrypted and WEP connect OK.

I have a Thomson TG782T router supplied by my ISP (Bg Pond).
The options I have are:
1.   Disabled
2.   Use WEP Encryption
3.   Use WPA-PSK Encryption

It appears that the wireless in 11.04 can't deal with the WPA-PSK encryption as that's where the play goes down.

Once the WPA-PSK Encryption gets turned on then I have the following security:
Security mode:         WPA-PSK
WPA-PSK Encryption:    TKIP
WPA-PSK Version:       WPA

In 11.04 I can only turn on "WPA & WPA personal" and it doesn't connect.

I can select "WPA+WPA2" in the router but it still won't connect.

I have also tried "WPA & WPA Enterprise" in 11'04 with no luck.

But with encryption disabled or using WEP I can connect.


Chris

---

### Post by praseodym on 2011-12-26
Looks like the driver/firmware combination only works with WEP.

---

### Post by NewNerd99 on 2011-12-26
Yes, its a pity. I would have liked to have returned to linux (Ubuntu) but I'm afraid I will have to stick with Windows 7 as both home and work use that encryption.

Thanks for your help and time. I always enjoy playing in the terminal as I learn a bit more each time I do.

Thanks again.

Chris

---

### Post by praseodym on 2011-12-26
Alternatively try the windows driver with ndiswrapper

---

### Post by pytheas22 on 2011-12-26
I'd give ndiswrapper a try too.  In addition, it might be worth installing wicd from Ubuntu Software Center and trying to connect to your network using WPA with that program rather than NetworkManager (the wireless connection manager that's installed by default).  wicd does WPA negotiation in a different way and sometimes works better in tricky driver situations like this.

Before using wicd you should turn off NetworkManager by typing:
```

sudo killall NetworkManager
sudo /etc/init.d/network-manager stop
```

If wicd doesn't work any better just reboot and NetworkManager will be running again.

---

### Post by praseodym on 2011-12-26
You can install additionally the Add-On from one of the developers for Wicd. It ships a lot of encryption templates, too:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
```
Stop the NM as decribed by pytheas22. See here:

[http://wicd.sourceforge.net/templates.php](http://wicd.sourceforge.net/templates.php)

and here (in German):

[http://elektronenblitz63.de/html/wicd.html](http://elektronenblitz63.de/html/wicd.html)

---

