---
title: "wireless not showing in nm-applet + wifi usb key not working"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by djahma on 2011-06-09
Hi there,

I've bought [this wifi key]("http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=FR_FRA&knowsPartNumber=false&productCategory=5&modelNumber=1699&partNumber=4338&downloadType=1&os=12") and when I first plugged it in (ubuntu 11.04) it worked but was very unstable: e.g. downloads would stop and not resume, pages were very long to display. (I tried it on win7 and it works perfectly)

So I tried to install the[ linux driver for it]("http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=FR_FRA&knowsPartNumber=false&productCategory=5&modelNumber=1699&partNumber=4338&downloadType=1&os=12"), unfortunately, there is a bug when I do $sudo make ([here, someone found about it but gave no guidance to resolve it]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=SMC_SMCWUSBS-N3")), and I end up with the following error:
```
 CC [M]  /home/djahma/programs_drivers/RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.o
/home/djahma/programs_drivers/RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/djahma/programs_drivers/RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.c:3709:2: error: implicit declaration of function ‘init_MUTEX’
/home/djahma/programs_drivers/RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.c:3710:2: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/djahma/programs_drivers/RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:5687:13: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
make[2]: *** [/home/djahma/programs_drivers/RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/djahma/programs_drivers/RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2
```Not being a computer expert, I tried a different path with ndiswrapper. I could install the Win7 32bit version of the driver. I followed this guide thoroughly, everything went fine till the part where we type lshw -C Network: the USB wifi key would not show. Here's what I get (the usb0 is my android phone whose USB Tethering I am using for the time being):
```
djahma@PCDjahma:~/programs_drivers/RT3070_Linux_STA_v2.1.1.0$ sudo lshw -c network
  *-network              
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: f4:6d:04:21:28:5c
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:febc0000-febfffff ioport:ec00(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: aa:31:bf:8b:39:21
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.213 link=yes multicast=yes
```When I do $lsusb, I get: (in green is my wifi key properly recognised)
> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b38:0003 Gear Head 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0d49:7410 Maxtor Mobile Hard Disk Drive (1TB)
[COLOR=DarkGreen]Bus 001 Device 002: ID 083a:a701 Accton Technology Corp. [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubI thought restarting would help but that was a bad idea as the wireless feature disappeared from nm-applet:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=194647&stc=1&d=1307632112[/IMG]
So now, the key doesn't work at all...
Here's the output from $nm-tool:
```
djahma@PCDjahma:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        F4:6D:04:21:28:5C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: usb0  [Auto usb0] ----------------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        AA:31:BF:8B:39:21

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.213
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129
```And $ifconfig:
> djahma@PCDjahma:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f4:6d:04:21:28:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97298 (97.2 KB)  TX bytes:97298 (97.2 KB)

usb0      Link encap:Ethernet  HWaddr aa:31:bf:8b:39:21  
          inet addr:192.168.42.213  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::a831:bfff:fe8b:3921/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:332509 (332.5 KB)  TX bytes:160212 (160.2 KB)Basically, the most important thing is to get the key working like the very first time (unstable) and showing in nm-applet.:) After, if someone knows a trick to get it working as fine as under Win7, that would be great.:KS

cheers

---

### Post by chili555 on 2011-06-09
> the most important thing is to get the key working like the very first time (unstable) and showing in nm-applet.It looks like it's in nm-applet to me. You have a wireless interface usb0 and an IP address. Maybe I don't understand; why do you want to get it working unstable. Please post:```
lsmod
ndiswrapper -l
```I suspect conflicting drivers are loading. I also suspect we don't need ndiswrapper, just a little blacklisting.

---

### Post by djahma on 2011-06-09
thanks for replying this quick...it's now 1 full day I'm on this problem and I started to feel helpless:wink:.

The usb0 is indeed in nm-applet, but it's not my wifi key. Instead, it's  my Android phone which I'm currently using to connect to the  internet...that's a temporary fix.

As for ndiswrapper, I've now removed it through synaptic. Do you want me to reinstall ndiswrapper?

lsmod gives:
```
Module                  Size  Used by
rndis_wlan             28293  0 
cfg80211              156212  1 rndis_wlan
rndis_host             13521  1 rndis_wlan
cdc_ether              13032  1 rndis_host
usbnet                 25175  3 rndis_wlan,rndis_host,cdc_ether
nls_utf8               12493  1 
isofs                  39571  1 
binfmt_misc            13213  1 
vesafb                 13449  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_via      56765  1 
snd_hda_intel          24140  2 
psmouse                73312  0 
ppdev                  12849  0 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ndiswrapper           192828  0 
snd_seq_midi_event     14475  1 snd_seq_midi
k10temp                12951  0 
serio_raw              12990  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sp5100_tco             13456  0 
i2c_piix4              13095  0 
fglrx                2434640  116 
joydev                 17322  0 
parport_pc             32111  1 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
asus_atk0110           17664  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  1 
uas                    17676  0 
atl1c                  36237  0 
ahci                   21591  3 
libahci                25548  1 ahci
pata_atiixp            12968  0 
```

---

### Post by chili555 on 2011-06-09
> do you want me to reinstall ndiswrapper?My, oh my no!

I think we just need to make a small change in your blacklist file. May I see:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/blacklist
modinfo rt2870sta | grep A701
```Thanks.

---

### Post by djahma on 2011-06-09
> **chili555 said:**
> My, oh my no!

I think we just need to make a small change in your blacklist file. May I see:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/blacklist
modinfo rt2870sta | grep A701
```Thanks.

Alors!... cat /etc/modprobe.d/blacklist.conf 
```
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
```

cat: /etc/modprobe.d/blacklist: No such file or directory

And finally:
```
djahma@PCDjahma:~$ modinfo rt2870sta | grep A701
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
```

---

### Post by chili555 on 2011-06-09
Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Detach your Android and plug in your USB wireless device and post back to report your findings.

---

### Post by djahma on 2011-06-09
Unfortunately, nothing has changed:(
I've tried again after a reboot, but it is the same.

Could the problem come from NetworkManager since nm-applet seems to take its input from it?... (I'm a beginner speculating on the source of the problem)

---

### Post by chili555 on 2011-06-09
Please show me:```
sudo modprobe rt2870sta
dmesg | grep rt2
iwconfig
```We're close, I think.

---

### Post by djahma on 2011-06-09
> **chili555 said:**
> We're close, I think.
:DI like that!

sudo modprobe rt2870sta:

Wooooooohhooooooooo! You made it working man! You are the man!:KS

I've tested the connection over one download and the streaming of the evening tv news and the quality of the connection is better than the very first time I plugged that dongle in and it's as good as under win7 where I installed the correct driver.

For my Linux education purpose, could you tell me where the rt2870sta module comes from? I mean when I tried 'make' on the linux driver I downloaded, it was to build this very module...

Thank you very much for your help, you've impressed me!

---

### Post by chili555 on 2011-06-09
The module rt2870sta has been in the kernel for several versions. It has conflicting modules, the rt2800usb suite; they need blacklisting.

Let's get rt2870sta to load on boot:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Enjoy!

---

### Post by djahma on 2011-06-11
That's perfect! It works perfectly after rebooting.
Many thanks again

---

