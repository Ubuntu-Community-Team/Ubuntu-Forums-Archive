---
title: "Wireless fail"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by Jannes. on 2010-05-30
I upgraded my ubuntu 9.10 to 10.04 and my Wireless Internet failed...
In 9.10 I had some problems with my Wireless Internet and then I solved it with this:

LSUSB:
```
jannes@jannes-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0681:001b Siemens Information and Communication Products WLL013
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


LSMOD:
```
jannes@jannes-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
at76_usb               71232  0 
snd_usb_audio          84224  0 
snd_usb_lib            16284  1 snd_usb_audio
snd_hwdep               7200  1 snd_usb_audio
snd_intel8x0           30168  5 
snd_ac97_codec        101216  1 snd_intel8x0
quickcam_messenger     11840  0 
usbvideo               25472  1 quickcam_messenger
gspca_stv06xx          24164  0 
ppdev                   6688  0 
gspca_main             22812  1 gspca_stv06xx
at76c50x_usb           37640  0 
psmouse                56180  0 
parport_pc             31940  1 
nvidia               7089800  34 
videodev               36736  2 usbvideo,gspca_main
mac80211              181236  1 at76c50x_usb
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
serio_raw               5280  0 
apm                    17240  2 
shpchp                 32272  0 
v4l1_compat            14496  1 videodev
cfg80211               93052  1 mac80211
snd_pcm                75296  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  5 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  19 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
intel_agp              27484  1 
agpgart                34988  2 nvidia,intel_agp
jannes@jannes-desktop:~$ 
```

Some detailed info:
```

us 002 Device 003: ID 0681:001b Siemens Information and Communication Products WLL013
```

```

at76c50x_usb           37640  0 
...
mac80211              181236  1 at76c50x_usb
```

What I had to do was blaclisting the at76c50x_usb...

This didn't help in Ubuntu 10.04

Someone said maybe a clean install (10.04) helps... So did I.

I still have the same problem... 
I cant even select,by networking, the option wireless...
At the moment I'm surfing wired... But this isn't the best solution so I want my wireless back...

Here are my LSUSB and LSMOD from my 10.04

```
jannes@jannes-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 003 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 0681:001b Siemens Information and Communication Products WLL013**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jannes@jannes-desktop:~$ 
```

```
jannes@jannes-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_usb_audio          75765  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_usb_lib            15658  1 snd_usb_audio
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_hwdep               5412  1 snd_usb_audio
quickcam_messenger     10014  0 
usbvideo               23703  1 quickcam_messenger
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
nvidia               7087672  24 
snd                    54148  18 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
usbhid                 36110  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
gspca_stv06xx          23274  0 
gspca_main             21199  1 gspca_stv06xx
soundcore               6620  1 snd
intel_agp              24177  1 
hid                    67032  1 usbhid
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
videodev               34361  2 usbvideo,gspca_main
v4l1_compat            13251  1 videodev
lp                      7028  0 
shpchp                 28820  0 
agpgart                31724  2 nvidia,intel_agp
parport                32635  2 ppdev,lp
ohci1394               26950  0 
8139too                18545  0 
8139cp                 16186  0 
ieee1394               81181  1 ohci1394
mii                     4381  2 8139too,8139cp
jannes@jannes-desktop:~$ 
```

---

### Post by purelinuxuser on 2010-05-30
Hello, please post the output of the following commands so that I can try to assist you. ;)
```
iwconfig
sudo iwlist scan
lshw -c network
dmesg | grep -i at76
```

---

### Post by Jannes. on 2010-05-31
Iwconfig:
```
jannes@jannes-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```
sudo...:
```
jannes@jannes-desktop:~$ sudo iwlist scan
[sudo] password for jannes: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

lshw -c network:
```
jannes@jannes-desktop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:0c:76:e1:38:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.19 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:23 ioport:c400(size=256) memory:df010000-df0100ff memory:20000000-2000ffff(prefetchable)
jannes@jannes-desktop:~$ 
```

dmesg | grep -i at76:
```
jannes@jannes-desktop:~$ dmesg | grep -i at76
[   12.890460] Atmel at76x USB Wireless LAN Driver 0.17 loading
[   12.890512] usb 2-2: firmware: requesting atmel_at76c503-rfmd.bin
[   12.957894] usb 2-2: firmware atmel_at76c503-rfmd.bin not found!
[   12.957898] usb 2-2: you may need to download the firmware from http://developer.berlios.de/projects/at76c503a/
[   12.957912] at76c50x-usb: probe of 2-2:1.0 failed with error -2
[   12.957949] usbcore: registered new interface driver at76c50x-usb
jannes@jannes-desktop:~$ 
```

---

### Post by purelinuxuser on 2010-05-31
[QUOTE=Jannes.]```
jannes@jannes-desktop:~$ dmesg | grep -i at76
[   12.890460] Atmel at76x USB Wireless LAN Driver 0.17 loading
[B][   12.890512] usb 2-2: firmware: requesting atmel_at76c503-rfmd.bin
[   12.957894] usb 2-2: firmware atmel_at76c503-rfmd.bin not found!
[   12.957898] usb 2-2: you may need to download the firmware from http://developer.berlios.de/projects/at76c503a/[/B]
[   12.957912] at76c50x-usb: probe of 2-2:1.0 failed with error -2
[   12.957949] usbcore: registered new interface driver at76c50x-usb
jannes@jannes-desktop:~$ 
```[/QUOTE]

There's your problem, the firmware's missing.  Here's how to reinstall it:

[LIST=1]
[*]Download the firmware package at [http://download.berlios.de/at76c503a/at76_usb-firmware-0.1.tar.gz](http://download.berlios.de/at76c503a/at76_usb-firmware-0.1.tar.gz).  Place it in your Downloads folder.
[*]Open a Terminal and run the following commands:
```
cd ~/Downloads
tar xvf at76_usb-firmware-0.1.tar.gz
cd at76_usb-firmware-0.1/
sudo cp *.bin /lib/firmware
```
[*]Reboot.  After that, you can delete the at76 files under Downloads.
[/LIST]
Hope this helps :)

---

### Post by Jannes. on 2010-05-31
I don't see a difference...
Here are your codes again...

```
jannes@jannes-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jannes@jannes-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

jannes@jannes-desktop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:0c:76:e1:38:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.19 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:23 ioport:c400(size=256) memory:df010000-df0100ff memory:20000000-2000ffff(prefetchable)
jannes@jannes-desktop:~$ dmesg | grep -i at76
[   12.753181] Atmel at76x USB Wireless LAN Driver 0.17 loading
[   12.753234] usb 2-2: firmware: requesting atmel_at76c503-rfmd.bin
[   12.915685] usb 2-2: using firmware atmel_at76c503-rfmd.bin (version 1.101.0-84)
[   12.916868] at76c50x-usb 2-2:1.0: downloading internal firmware
[   15.553205] usbcore: registered new interface driver at76c50x-usb
jannes@jannes-desktop:~$ 
```

---

### Post by purelinuxuser on 2010-05-31
Okay, I'm at a loss.  Firmware is loaded, driver is loaded, but the wireless interface is not created or recognized. :confused: Maybe someone who has experience with this card can step in...

---

### Post by Jurgen Oscar on 2010-05-31
Hi guys,

I am sure we all had to scratch our hair more frequently. :-) 

Got the same problem using WUSB11 v2.8 (linksys USB Wifi)
Ubuntu Lucid 10.04 (Desktop 64-bit)

I am connecting using my other laptop with Ubuntu 10.04 (installed on a pen drive) 
with Wifi working fine. I don't know why it's working. :(

So please forgive me if I could not cut and paste the complete code.

lsusb:
Linksys WUSB11 v2.8 802.11b Adapter

lsmod:

at76c50x_usb           37726  0 
...
mac80211              238128  1 at76c50x_usb


iwconfig:
lo - no wireless extension
eth0 - no wireless extension
wlan0 - IEEE 802.11b  ESSID:off/any
    .... Tx-Power=20 dBm
    ... Power Management:off


sudo iwlist scan:
it scanned through, and list all (except mine, which is hidden)



sudo lshw -c network:
*-network
.... logical name: eth0
.... (no issue, i suppose)

*-network
... logical name:wlan0
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

*** in the configuration there is NO driver information (i could not get a way to guide me to install the atmel_firmware) 
*** currently downloading the new firmware from:
   ---  [http://packages.ubuntu.com/lucid/atmel-firmware](http://packages.ubuntu.com/lucid/atmel-firmware)
and I am going to copy it to /lib/firmware  (will post the result later)




dmesg | grep -i at76:
... Atmel at76x USB Wireless LAN driver 0.17 loading
... usb 2-1.1: firmware: requesting atmel_at76c505-rfmd2958.bin
... usb 2-1.1: using firmware atmel_at76c505-rfmd2958.bin (version 1.101.0-86)
... usbcore: registered new interface driver at76c50x-usb

 
I had tried to /etc/modprobe.d/blacklist.conf for BOTH at76c50x-usb AND at76c50x_usb,
but still NOT WORKING. And remove the blacklist.conf line for now.

Any help will be greatly appreciated.

Thank you so much.

J.O.

---

### Post by Jurgen Oscar on 2010-06-01
Hi,

I downloaded the atmel package for Lucid:
atmel-firmware_1.3.orig.tar.gz

Copied all the .bin files from the folder: images.usb to /lib/firmware (chmod 644 the files)

And rebooted.

NOT WORKING also.

Thanks.

---

### Post by Jannes. on 2010-06-01
Oké Im a step further...

I found on a German forum that i had to install backports module... So did I... I can see my wireless again. But when I try to connect, it fails after a long while of connecting...

link to the website: [http://forum.ubuntuusers.de/topic/at76-usb-treiber-nicht-mehr-verfuegbar/#post-2476872](http://forum.ubuntuusers.de/topic/at76-usb-treiber-nicht-mehr-verfuegbar/#post-2476872)

code to install the backports...
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```


Can i trust something like this?
[http://wiki.debian.org/at76_usb](http://wiki.debian.org/at76_usb)

---

### Post by purelinuxuser on 2010-06-01
I dunno... Debian is the distro Ubuntu is based on but they tend to use different software packages, so... try at your own risk ;)

---

### Post by purelinuxuser on 2010-06-01
> **Jurgen Oscar said:**
> Hi guys,

I am sure we all had to scratch our hair more frequently. :-) 

Got the same problem using WUSB11 v2.8 (linksys USB Wifi)
Ubuntu Lucid 10.04 (Desktop 64-bit)

I am connecting using my other laptop with Ubuntu 10.04 (installed on a pen drive) 
with Wifi working fine. I don't know why it's working. :(
[...]
I had tried to /etc/modprobe.d/blacklist.conf for BOTH at76c50x-usb AND at76c50x_usb,
but still NOT WORKING. And remove the blacklist.conf line for now.

Any help will be greatly appreciated.

Thank you so much.

J.O.

Exactly what doesn't work?  The wireless interface shows up and you can scan for wireless networks.  Have you tried connecting by clicking on Network Manager and selecting "Connect to Hidden Wireless Network?"

---

### Post by Jurgen Oscar on 2010-06-02
> **purelinuxuser said:**
> Exactly what doesn't work?  The wireless interface shows up and you can scan for wireless networks.  Have you tried connecting by clicking on Network Manager and selecting "Connect to Hidden Wireless Network?"


I did tried to connect to hidden wireless network. It won't connect.

I saw in the daemon.log there is something failed:
NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion 
`NM_IS_SETTING_802_1x (setting)' failed.

I am sure the WEP-128 bit key setting is correct, cause I followed
the wireless setting of my ubuntu 32-bit laptop (connected to the same router).


Also some message of syslog:
kernel: wlan0: direct probe to AP 00:22:XX:XX:XX (try 1)
kernel: wlan0: direct probe to AP 00:22:XX:XX:XX (try 2)
kernel: wlan0: direct probe to AP 00:22:XX:XX:XX (try 3)
kernel: wlan0: direct probe to AP 00:22:XX:XX:XX time out



I do not know what is going on. I was wondering that the driver is not installed 
correctly, as I never install any wireless driver for my WUSB11 EXCEPT,e
just COPIED some atmelxxx.bin files to the /lib/firmware.


Is there anything else I could do? Or is this because of the 64-bit version?
(Ubuntu 10.04 x86_64).


Really need help. :) 
Thank you so much.

---

### Post by Jannes. on 2010-06-02
for me backports wasn't the real solution at all... I deleted it and i reinstalled the at76... driver. Now my wireless is visible again so this is a quote what my ex-neighbour said:

> AT76.. module has been loaded at boot by a hotplugger...
There is a program which will start the wireless connection but it always fails because of his rights...

is there any solution to fix this?

---

### Post by purelinuxuser on 2010-06-02
"because of his rights" I have NO idea what that's supposed to mean :confused:

@Jurgen Oscar- not sure what to do here either.

It's possible that both of you could try ndiswrapper to get your wireless working.  Search for some tutorials (there are probably lots of them) on Google.

---

### Post by Jannes. on 2010-06-02
ndis isnt the famous solution ;)

I think he means, wireless connection has to be root or smth...

---

### Post by purelinuxuser on 2010-06-02
But Network Manager configures the network with root privileges :-s

---

### Post by Jurgen Oscar on 2010-06-04
> **purelinuxuser said:**
> But Network Manager configures the network with root privileges :-s

hello there,

after spending more 1.5 days in setting up ndiswrapper, 
linux-backports-modules-wireless-2.6.32-22-generic_2.6.32-22.13_amd64.deb,
STILL NOT working for me.

Please take note that I am using x86_64 bit. (Ubuntu desktop 64-bit)

I do not know if this will work for 32-bit version.

Any more suggestion please?

THIS IS PAIN ... !!!!! 

Oh dear..

---

### Post by purelinuxuser on 2010-06-04
@Jurgen

Yes, ndiswrapper has always worked perfectly for me in 64-bit :)

Okay... take a break... take a deep breath... then post the output of the following commands:
```
ndiswrapper -l
lshw -c network
```

---

### Post by Jurgen Oscar on 2010-06-05
> **purelinuxuser said:**
> @Jurgen

Yes, ndiswrapper has always worked perfectly for me in 64-bit :)

Okay... take a break... take a deep breath... then post the output of the following commands:
```
ndiswrapper -l
lshw -c network
```

@Purelinuxuser,

thank you for your time and patience. :)

-. ndiswrapper -l: 
wusb11v4 : driver installed

-. lshw -c network:
*.network
        description: Ethernet interface
        product: RTL8111 .... 
        logical name: eth0 
        ..... .
*.network
        description: Wireless interface
        physical id: 1
        logical name: wlan0
        serial : 00:0f... 
        capabilities: ethernet physical wireless
        configuguration: broadcast=yes  multicast=yes   wireless=IEEE 802.11b



Okay, hope i do not miss out important info.

Thanks.

J.O.

---

### Post by purelinuxuser on 2010-06-05
That is weird, ndiswrapper isn't recognizing your device!  Try a different driver...

After that, post those two commands again.  And be sure to include the FULL output :)

---

### Post by Jurgen Oscar on 2010-06-06
> **purelinuxuser said:**
> That is weird, ndiswrapper isn't recognizing your device!  Try a different driver...

After that, post those two commands again.  And be sure to include the FULL output :)

tried again with 2 different drivers:


1. Driver: netusb.inf
```

jo@jodsk64:~$ ndiswrapper -l
netusb : driver installed
jo@jodsk64:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:11:18:fa:31:62
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:c800(size=256) memory:fafff000-faffffff(prefetchable) memory:faff8000-faffbfff(prefetchable) memory:fbcf0000-fbcfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:11:41:79
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

```2. lspmusb.inf 

```

jo@jodsk64:~$ ndiswrapper -l
lspmusb : driver installed
jo@jodsk64:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:c800(size=256) memory:fafff000-faffffff(prefetchable) memory:faff8000-faffbfff(prefetchable) memory:fbcf0000-fbcfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

```:confused:
J.O.

---

### Post by purelinuxuser on 2010-06-06
Jurgen, try using this driver: [http://homedownloads.cisco.com/downloads/WUSB11-v2.8_dr.zip](http://homedownloads.cisco.com/downloads/WUSB11-v2.8_dr.zip).  Then post the output of those commands again.  Also, next time use the [CODE] tag ;)

---

### Post by Jurgen Oscar on 2010-06-06
> **purelinuxuser said:**
> Jurgen, try using this driver: [http://homedownloads.cisco.com/downloads/WUSB11-v2.8_dr.zip](http://homedownloads.cisco.com/downloads/WUSB11-v2.8_dr.zip).  Then post the output of those commands again.  Also, next time use the ```
 tag ;)

Hello again purelinuxuser,

I tried with your driver. STILL not working. :)

netusb.inf:


[CODE]
jo@jodsk64:~$ ndiswrapper -l
netusb : driver installed
jo@jodsk64:~$ sudo lshw -c network
[sudo] password for jo: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:11:18:fa:31:62
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:c800(size=256) memory:fafff000-faffffff(prefetchable) memory:faff8000-faffbfff(prefetchable) memory:fbcf0000-fbcfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:11:41:79
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

```


thanks.

J.O.

---

### Post by purelinuxuser on 2010-06-06
This is starting to annoy me, I got the EXACT driver for your card.  Post the output of
```
lsusb
```so we can find out the EXACT chipset it uses.

---

### Post by Jurgen Oscar on 2010-06-06
> **purelinuxuser said:**
> This is starting to annoy me, I got the EXACT driver for your card.  Post the output of
```
lsusb
```so we can find out the EXACT chipset it uses.

Yes, it is annoying. I tried all drivers included in your 2.8 version,  linksys' version 2.8 and version 4.1 drivers. NOT working.

lsusb:

```


jo@jodsk64:~$ lsusb
Bus 002 Device 005: ID 046d:0a13 Logitech, Inc. 
Bus 002 Device 004: ID 046d:c053 Logitech, Inc. Laser Mouse
[SIZE=2][COLOR=Red]
Bus 002 Device 003: ID 1915:2233 Linksys WUSB11 v2.8 802.11b Adapter[/COLOR][/SIZE]

Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```Beside that i do   dmesg | grep -i at76 :

```

jo@jodsk64:~$ dmesg | grep -i at76
[    4.596211] Atmel at76x USB Wireless LAN Driver 0.17 loading
[    4.596226] usb 2-1.1: firmware: requesting atmel_at76c505-rfmd2958.bin
[    4.730588] usb 2-1.1: using firmware atmel_at76c505-rfmd2958.bin (version 1.101.0-86)
[    4.774627] usbcore: registered new interface driver at76c50x-usb

```


Is there anything to do with /etc/modprobe.d/blacklist.conf also? 
Do we need to blacklist the at76c50x-usb at all? 

I tried to put the blacklist and restart, it cannot detect my wlan0.


???.
Thanks pal.

---

### Post by purelinuxuser on 2010-06-06
No!  Don't blacklist that module!  In fact, if it is blacklisted, remove it! :D

Repost ndiswrapper -l and lshw -c network.

---

### Post by Jurgen Oscar on 2010-06-06
> **purelinuxuser said:**
> No!  Don't blacklist that module!  In fact, if it is blacklisted, remove it! :D

Repost ndiswrapper -l and lshw -c network.


It was the same, tried the blacklist and had put it back since.

So, nothing change since the last post of ndiswrapper -l and lshw -c network.

:confused:

---

### Post by purelinuxuser on 2010-06-06
Hmm... post the output of
```
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by Jurgen Oscar on 2010-06-07
> **purelinuxuser said:**
> Hmm... post the output of
```
iwconfig
sudo iwlist wlan0 scan
```

okay, i posted these info before, and re-posted here.

iwconfig:
```


lo    no wireless extensions.

eth0    no wireless extensions

wlan0     IEEE 802.11b  ESSID:off/any
             Mode:managed   Access Point: Not-associated   Tx-Power=20 dBm
             Retry   long limit:7   RTS thr:off     Fragment thr:off
             Power Management:off


```


sudo iwlist wlan0 scan: it scanned through with dozen of wifi network appeared.

:(

---

### Post by purelinuxuser on 2010-06-07
> **Jurgen Oscar said:**
> okay, i posted these info before, and re-posted here.

iwconfig:
```


lo    no wireless extensions.

eth0    no wireless extensions

wlan0     IEEE 802.11b  ESSID:off/any
             Mode:managed   Access Point: Not-associated   Tx-Power=20 dBm
             Retry   long limit:7   RTS thr:off     Fragment thr:off
             Power Management:off


```sudo iwlist wlan0 scan: it scanned through with dozen of wifi network appeared.

:(

[S]Hey, check out this link: [http://ubuntuforums.org/showthread.php?p=9306475](http://ubuntuforums.org/showthread.php?p=9306475)!  Looks like exactly what you need :)[/S]

Wait NEVERMIND, I *just* noticed your post there '](*,)

---

### Post by purelinuxuser on 2010-06-07
*sigh* sorry, I have no idea how to proceed from here :( I don't have experience with this card, and Google yields nothing.  You should probably wait until somebody a bit more knowledgeable comes along...

---

### Post by rony_cpu on 2010-06-07
hello,
i'm rony.. i have a problem when i install ubuntu 10.04 on my notebook
wireless cannot connect, firmware is fail :(
oh ya, my notebook is compaq cq40, Processor AMD Turion RM 75, and wireless is broadcom 

if you have solution, please share with me

thanks

---

### Post by Jurgen Oscar on 2010-06-08
> **purelinuxuser said:**
> *sigh* sorry, I have no idea how to proceed from here :( I don't have experience with this card, and Google yields nothing.  You should probably wait until somebody a bit more knowledgeable comes along...

Thanks anyway. :)

Anybody else please..... help me :)

---

