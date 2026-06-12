---
title: "Help needed setting up ubuntu server access point with wg311(v1)"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by roddyguk on 2010-01-15
Hi,

Ive spent the last couple of days looking for a way to set this up and cant find the solution anywhere.
Maybe someone here has either done it or has some ideas on how to get it done?

Right from what iv read so far i understand i have to set the card to master mode but when i try

```
sudo iwconfig wlan0 mode master
```
i get the error
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```

I read somewhere that the madwifi driver is up to the task but im still quite new to linux and not really sure how to change the drivers.

this is what iv done so far

```
 wget http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz
tar xvxf madwifi-trunk-current.tar.gz 
cd madwifi-trunk-r4108-20100115/
sudo make
sudo make install
sudo vi /etc/modules 
sudo modprobe ath_pci

```

I added ath_pci to the bottom of the modules file

This has added wmaster0 to iwconfig

But that is about as far as iv gotten 


If someone could please help me out i would be very grateful

Rod...

---

### Post by adam814 on 2010-01-15
[http://madwifi-project.org/wiki/UserDocs/UsersGuideExamples](http://madwifi-project.org/wiki/UserDocs/UsersGuideExamples)

MadWifi uses its own tools.  One of those is "wlanconfig".  I believe the first example is what you need.

---

### Post by roddyguk on 2010-01-16
cheers adam, 

im still not quite sure iv installed the driver and modules correctly as when i type in the first command 
```
wlanconfig ath create wlandev wifi0 wlanmode ap
```

i get an error
```
wlanconfig: ioctl: No such device

```

i wasnt sure if ath0 was ment to be on the end so i tried that too and get an error
```
wlanconfig: unknown create option ath0
```

il add some more info about my system 

lspci
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0a.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsmod
```
Module                  Size  Used by
arc4                    1660  2 
ecb                     2524  2 
ath_pci               197844  0 
wlan                  228720  1 ath_pci
ath_hal               397504  1 ath_pci
iptable_filter          3100  0 
snd_intel8x0           30168  0 
ath5k                 124580  0 
sis_agp                 6972  1 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
agpgart                35020  1 sis_agp
snd_pcm                75488  2 snd_intel8x0,snd_ac97_codec
mac80211              181236  1 ath5k
snd_timer              22276  1 snd_pcm
snd                    59204  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               7264  1 snd
i2c_sis96x              3936  0 
lp                      8964  0 
led_class               4096  1 ath5k
shpchp                 32336  0 
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
snd_page_alloc          9252  2 snd_intel8x0,snd_pcm
parport                35340  1 lp
ohci1394               30220  0 
ieee1394               86628  1 ohci1394
usb_storage            52608  1 
8139too                22716  0 
8139cp                 19612  0 
mii                     5212  2 8139too,8139cp

```

sudo lshw -C network
```
  *-network:0 DISABLED    
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wmaster0
       version: 01
       serial: **:**:**:**:**:**
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:ee000000-ee00ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 10
       serial: **:**:**:**:**:**
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:e200(size=256) memory:ee013000-ee0130ff

```

---

### Post by imrazor on 2010-01-16
You're using mac80211 drivers for your ath5k card, which will not allow you to set master/AP mode with iwconfig (or wlanconfig apparently.) You need to use hostapd, a daemon for managing access points. see here...

[http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)

I've used it to set up an open access point, but I'm having issues with WPA. Good luck...

EDIT: Found some additional info about the ath5k driver. See below...

[http://en.gentoo-wiki.com/wiki/Atheros_5xxx](http://en.gentoo-wiki.com/wiki/Atheros_5xxx)

Looks like you might have to install MadWifi. Not sure if it's available in the repos or not.

---

### Post by adam814 on 2010-01-16
Try editing your /etc/modprobe.d/madwifi.conf file.  Make sure you have "blacklist ath5k" uncommented and all the other lines commented.  Also comment the line it /etc/modprobe.d/blacklist-ath_pci.conf so it isn't blacklisted.

---

### Post by roddyguk on 2010-01-16
imrazor:
   ive given hostapd ago but i get stuck wile trying to compile it, ive followed the site you suggested up to 

> Next, compile hostapd:

make

if this fails with errors like:

driver_nl80211.c:21:31: warning: netlink/genl/genl.h: No such file or directory
driver_nl80211.c:22:33: warning: netlink/genl/family.h: No such file or directory
driver_nl80211.c:23:31: warning: netlink/genl/ctrl.h: No such file or directory
driver_nl80211.c:24:25: warning: netlink/msg.h: No such file or directory
driver_nl80211.c:25:26: warning: netlink/attr.h: No such file or directory

you need to install/update libnl-1.0pre8 (or later). If all goes well and the compilation finishes, try the minimal hostapd again. I'd recommend creating a seperate hostapd.conf file with this configuration in it called hostapd-minimal.conf, for testing use.

hostapd # ./hostapd ./hostapd-minimal.conf
Configuration file: ./hostapd-minimal.conf
Using interface wlan1 with hwaddr 00:0d:0b:cf:04:40 and ssid 'test'

If that starts as the example here shows, you can move on to configuring hostapd. If it fails to start with errors about the driver not being found, review the steps listed above for compiling hostapd again.



and thats where i get stuck.
i get 1000s of lines scroll up then 1 error at the bottom

```
../src/crypto/tls_openssl.c:2479: error: ‘struct tls_connection’ has no member named ‘ssl’
../src/crypto/tls_openssl.c:2483: error: ‘struct tls_connection’ has no member named ‘ssl’
../src/crypto/tls_openssl.c:2486: warning: implicit declaration of function ‘EVP_CIPHER_key_length’
../src/crypto/tls_openssl.c:2487: warning: implicit declaration of function ‘EVP_MD_size’
../src/crypto/tls_openssl.c:2488: warning: implicit declaration of function ‘EVP_CIPHER_iv_length’
make: *** [../src/crypto/tls_openssl.o] Error 1

```

as its not a driver error im not sure on what to do about it?

i thought i had already installed the madwifi current trunk driver, but the second link you said to look at says use the madwifi-hal driver.
should i get rid of the first on? if so how?

adam:
   i dont have the files your talking about, all i have in /etc/modprobe.d/ is 
blacklist-ath_pci.conf  
blacklist-firewire.conf    
blacklist-watchdog.conf
blacklist.conf          
blacklist-framebuffer.conf

---

### Post by adam814 on 2010-01-16
In that case you should be fine with making sure ath_pci isn't blacklisted in blacklist-ath_pci.conf or blacklist.conf and add ath5k to the end of blacklist.conf.

---

### Post by roddyguk on 2010-01-16
ath_pci is the only 1 in blacklist-ath_pci.conf but its already been commented out, and its not in blacklist.conf

ive added ath5k to the end of blacklist.conf, but not sure what to do now?
if i run

```
wlanconfig ath create wlandev wifi0 wlanmode ap
```

again i still get the error

```
wlanconfig: ioctl: No such device
```

---

### Post by adam814 on 2010-01-16
That particular error just means you don't have a device named wifi0.

To get one you need to pull the ath5k module and try to use the madwifi modules:
```
sudo modprobe -r ath5k && sudo modprobe ath_hal && sudo modprobe ath_pci
```

Then run "iwconfig" to see if you have a device named wifi0.

---

### Post by imrazor on 2010-01-17
AFAIK, it is not necessary to compile hostapd from scratch. Just install it from the repos:
 
sudo apt-get install hostapd
 
assuming it's not already installed. I wouldn't compile unless you need bleeding edge features or support for a device that's not built-in the binaries. 
 
I should also point out that I'm using a Broadcom BCM4318 chip, so I won't be much help configuring Atheros drivers. Broadcom is in it's own special level of Hades. From my limited reading, it appears that some Atheros drivers are handled through the mac80211 stack and some are proprietary. If you're using ath5k or ath9k I think hostapd is the appropriate method for you to use. I've never used madwifi myself. It looks like you've been playing with both, which can cause conflicts. If worse comes to worse, do a fresh install of Karmic and start clean.
 
Additionally, this page may come in handy once/if you get hostapd up and running:
 
[http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)
 
Try the minimal config first to make sure you can get your AP up in open mode, then try playing with security.

---

### Post by adam814 on 2010-01-17
Yeah, those are two separate routes.  With the madwifi drivers you don't need hostapd as they have the functionality built-in.  With the ath5k driver you'll need hostapd.

---

