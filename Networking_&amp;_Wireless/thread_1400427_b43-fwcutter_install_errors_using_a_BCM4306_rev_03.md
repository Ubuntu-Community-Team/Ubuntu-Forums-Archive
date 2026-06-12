---
title: "b43-fwcutter install errors using a BCM4306 rev 03"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by CharlesWallace on 2010-02-06
Howdy
 
I'm getting started with linux and have run into some problems.  I have an HP pavillion zv5000 with a dual boot Win XP/Ubuntu 9.10.  My network card is a BCM4306 rev 03.  Looking at other forums it looks like i need b43-fwcutter to install the drivers.
 
Right now all i have is wireless (no direct connect to the internet).  I can access wirelessly fine in XP but not Ubuntu so any download i do has to be in XP then i restart in Ubuntu.  
 
I used this site to guide me on installing b43-fwcutter from my install cd but i ran into a problem
 
F:\ubuntu stuff\04[SOLVED] The Definitive 9_10 Broadcom Solution Guide - Ubuntu Forums.htm
 
When i apply changes to   Synaptic Package Mgr to install b43 i come up with the attached error message.
 
I rebooted after trying a few time and then when i went to hardware drives Ubuntu did see my wireless care for the first time.  I clicked on activate and it said downloading and installing drivers.   This lasted about 10 seconds and then the window disappeared.  I rebooted but my wirless card was still not activated.  I tried activating it many times but the same message came up and after 10 seconds disappeared and the drives always said this device is not activated.  
 
I'm atempting to download and install b43-fwcutter manually but since i'm new i'm just shooting in the dark and any guidence would be much appreciated.

---

### Post by puppywhacker on 2010-02-07
the firmware can not be delivered with ubuntu because of licensing issues. fwcutter will download the firmware from a website, but you will ofcourse need an internet to download, which you don't have because the wireless doesn't work without firmware. the endless circle ...

To break the circle use the wired connection or download the drivers yourself and then cut the firmware.

The last bit is explained on the b43 wireless driver site
[http://linuxwireless.org/en/users/Drivers/b43#device_firmware_installation](http://linuxwireless.org/en/users/Drivers/b43#device_firmware_installation)

in short you have download
```
http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```

unpack the archive to find the wl_apsta_mimo.o file, and from that directory run
```
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```

P.S. don't follow the instructions for ubuntu, since those are the ones that will try to download the drivers from the non-existing network connection. Use the manual install instead

---

### Post by CharlesWallace on 2010-02-07
i've downloaded broadcom-wl-4.150.10.5.tar.bz2 and placed it in the downloads folder. I extracted it in the folder and found the wl_apasta_mimo.o file but i don't have permision to copy the wl_apsta_mimo.o file to w/lib/firmware/ folder. I figured this has to do with what you called "download the drivers yourself and then cut the firmware". I tried understanding the posted link you showed me but i'm not sure about the
tar xjf broadcom-wl-4.150.10.5.tar.bz2
command. It just comes up with errors. My guess is that i don't have the broadcom-wl-4.150.10.5.tar.bz2 in the right folder.
 
Error Message 
charles@charles-laptop:~$ tar xjf broadcom-wl-4.150.10.5.tar.bz2
tar: broadcom-wl-4.150.10.5.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

---

### Post by chili555 on 2010-02-07
You say you downloaded a file:> i've downloaded broadcom-wl-4.150.10.5.tar.bz2Did you do this on another computer and transfer it with a USB key, or do you have internet connectivity on your Ubuntu machine?

---

### Post by puppywhacker on 2010-02-07
wl_apsta_mimo.o is the driver that you need to cut open, it contains the firmware. The tar command unpacks a .tar.bz2 file on the command line, you can (and did) use the graphical tools instead ... that it failed for you is because you placed the file in the download folder and you tried to execute it in your home folder, that's why it says "file not found"

You still need to cut the firmware with this command, and you have to execute that in the same directory you put the wl_apsta_mimo.o file.
```
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```

this would result in around 38 smaller files in the directory "/lib/firmware/b43". By default you don't have modify rights in this directory so you have to "sudo" to get enough rights to put files in this location.

Once the firmware is in place you can load the module that enables the wireless.

```
modprobe b43
```

this should show you a driver in the hardware list
```
sudo lshw -C network
```

and iwconfig should show you a wireless interface
```
iwconfig -a
```

---

### Post by CharlesWallace on 2010-02-07
I'm still having issues with the sudo b43-fwcutter command.  i've tiped it many different ways but it still can't find the wl-apsta-mimo.o file.  Right now its on a the charles drive in the download folder (charles is the name on the computer).  I've moved it to the system drive but the only place i had access to move it to was system/temp but again it didn't work.  
 
I guess i'm just confused, i see the /lib/firmware as the destination but where does the command know where to look for the file unless the file is suppose to be in the lib/firmware forlder when i run the command?  Again when i try to copy the wl-apsta-mimo.o file to the /lib/firmare folder i get that right error and i can't.  I'm not sure how to get around that.

---

### Post by chili555 on 2010-02-07
If you go to your Home directory and see a folder called Downloads, then open a terminal and do:```
cd Downloads
ls
```Do you see the broadcom-wl-4.150.10.5.tar.bz2 file? Good! Now do:```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```Only root, also known as Super User, has permission to write in system files, so we will get root priveleges ("sudo") just long enough to execute a command. Notice the command tells b43-fwcutter where to place the firmware files.

It will do no good to move the wl_apsta_mimo.o file to /lib/firmware. It has to have the firmware extracted, or cut from it first.

Before you put the bulb in the socket, take it out of the container and the container out of the bag, etc.

---

### Post by CharlesWallace on 2010-02-07
Okay here's where i stand now.
 
I got the comands
tar xjf broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
to work. how ever when i go to /lib/firmware/b43 the b43 folder has a white "x" on it. when i open it i see no files (and get an error message). When i right clicked properties on the b43 folder it says under contents: unreadable. below is a copy of my teminal history
 
[COLOR=darkred]charles@charles-laptop:~$ sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o[/COLOR]
[COLOR=darkred]This file is recognised as:[/COLOR]
[COLOR=darkred]ID : FW13[/COLOR]
[COLOR=darkred]filename : wl_apsta_mimo.o[/COLOR]
[COLOR=darkred]version : 410.2160[/COLOR]
[COLOR=darkred]MD5 : cb8d70972b885b1f8883b943c0261a3c[/COLOR]
[COLOR=darkred]Extracting b43/pcm5.fw[/COLOR]
[COLOR=darkred]Extracting b43/ucode15.fw[/COLOR]
[COLOR=darkred]Extracting b43/ucode14.fw[/COLOR]
[COLOR=darkred]Extracting b43/ucode13.fw[/COLOR]
[COLOR=darkred]Extracting b43/ucode11.fw[/COLOR]
[COLOR=darkred]Extracting b43/ucode9.fw[/COLOR]
[COLOR=darkred]Extracting b43/ucode5.fw[/COLOR]
[COLOR=darkred]Extracting b43/lp0bsinitvals15.fw[/COLOR]
[COLOR=darkred]Extracting b43/lp0initvals15.fw[/COLOR]
[COLOR=darkred]Extracting b43/lp0bsinitvals14.fw[/COLOR]
[COLOR=darkred]Extracting b43/lp0initvals14.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g1bsinitvals13.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g1initvals13.fw[/COLOR]
[COLOR=darkred]Extracting b43/b0g0bsinitvals13.fw[/COLOR]
[COLOR=darkred]Extracting b43/b0g0initvals13.fw[/COLOR]
[COLOR=darkred]Extracting b43/lp0bsinitvals13.fw[/COLOR]
[COLOR=darkred]Extracting b43/lp0initvals13.fw[/COLOR]
[COLOR=darkred]Extracting b43/n0absinitvals11.fw[/COLOR]
[COLOR=darkred]Extracting b43/n0bsinitvals11.fw[/COLOR]
[COLOR=darkred]Extracting b43/n0initvals11.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g1bsinitvals9.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g0bsinitvals9.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g1initvals9.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g0initvals9.fw[/COLOR]
[COLOR=darkred]Extracting b43/b0g0bsinitvals9.fw[/COLOR]
[COLOR=darkred]Extracting b43/b0g0initvals9.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g1bsinitvals5.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g0bsinitvals5.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g1initvals5.fw[/COLOR]
[COLOR=darkred]Extracting b43/a0g0initvals5.fw[/COLOR]
[COLOR=darkred]Extracting b43/b0g0bsinitvals5.fw[/COLOR]
[COLOR=darkred]Extracting b43/b0g0initvals5.fw[/COLOR]
[COLOR=darkred]charles@charles-laptop:~$ modprobe b43[/COLOR]
[COLOR=darkred]charles@charles-laptop:~$ sudo lshw -c network[/COLOR]
[COLOR=darkred]*-network:0 [/COLOR]
[COLOR=darkred]description: Ethernet interface[/COLOR]
[COLOR=darkred]product: RTL-8139/8139C/8139C+[/COLOR]
[COLOR=darkred]vendor: Realtek Semiconductor Co., Ltd.[/COLOR]
[COLOR=darkred]physical id: 1[/COLOR]
[COLOR=darkred]bus info: pci@0000:02:01.0[/COLOR]
[COLOR=darkred]logical name: eth0[/COLOR]
[COLOR=darkred]version: 10[/COLOR]
[COLOR=darkred]serial: 00:0f:b0:00:f3:54[/COLOR]
[COLOR=darkred]size: 10MB/s[/COLOR]
[COLOR=darkred]capacity: 100MB/s[/COLOR]
[COLOR=darkred]width: 32 bits[/COLOR]
[COLOR=darkred]clock: 33MHz[/COLOR]
[COLOR=darkred]capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/COLOR]
[COLOR=darkred]configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s[/COLOR]
[COLOR=darkred]resources: irq:18 ioport:7000(size=256) memory:e8104000-e81040ff[/COLOR]
[COLOR=darkred]*-network:1[/COLOR]
[COLOR=darkred]description: Network controller[/COLOR]
[COLOR=darkred]product: BCM4306 802.11b/g Wireless LAN Controller[/COLOR]
[COLOR=darkred]vendor: Broadcom Corporation[/COLOR]
[COLOR=darkred]physical id: 2[/COLOR]
[COLOR=darkred]bus info: pci@0000:02:02.0[/COLOR]
[COLOR=darkred]version: 03[/COLOR]
[COLOR=darkred]width: 32 bits[/COLOR]
[COLOR=darkred]clock: 33MHz[/COLOR]
[COLOR=darkred]capabilities: bus_master[/COLOR]
[COLOR=darkred]configuration: driver=b43-pci-bridge latency=64[/COLOR]
[COLOR=darkred]resources: irq:17 memory:e8100000-e8101fff[/COLOR]
[COLOR=darkred]*-network DISABLED[/COLOR]
[COLOR=darkred]description: Wireless interface[/COLOR]
[COLOR=darkred]physical id: 1[/COLOR]
[COLOR=darkred]logical name: wlan0[/COLOR]
[COLOR=darkred]serial: 00:90:4b:5b:cf:83[/COLOR]
[COLOR=darkred]capabilities: ethernet physical wireless[/COLOR]
[COLOR=darkred]configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/COLOR]
[COLOR=darkred]charles@charles-laptop:~$ iwconfig -a[/COLOR]
[COLOR=darkred]-a No such device[/COLOR]
 
I rebooted the computer and typed in 
 
[COLOR=darkred]charles@charles-laptop:~$ sudo lshw -c network[/COLOR]
[COLOR=darkred]*-network:0 [/COLOR]
[COLOR=darkred]description: Ethernet interface[/COLOR]
[COLOR=darkred]product: RTL-8139/8139C/8139C+[/COLOR]
[COLOR=darkred]vendor: Realtek Semiconductor Co., Ltd.[/COLOR]
[COLOR=darkred]physical id: 1[/COLOR]
[COLOR=darkred]bus info: pci@0000:02:01.0[/COLOR]
[COLOR=darkred]logical name: eth0[/COLOR]
[COLOR=darkred]version: 10[/COLOR]
[COLOR=darkred]serial: 00:0f:b0:00:f3:54[/COLOR]
[COLOR=darkred]size: 10MB/s[/COLOR]
[COLOR=darkred]capacity: 100MB/s[/COLOR]
[COLOR=darkred]width: 32 bits[/COLOR]
[COLOR=darkred]clock: 33MHz[/COLOR]
[COLOR=darkred]capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/COLOR]
[COLOR=darkred]configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s[/COLOR]
[COLOR=darkred]resources: irq:18 ioport:7000(size=256) memory:e8104000-e81040ff[/COLOR]
[COLOR=darkred]*-network:1[/COLOR]
[COLOR=darkred]description: Network controller[/COLOR]
[COLOR=darkred]product: BCM4306 802.11b/g Wireless LAN Controller[/COLOR]
[COLOR=darkred]vendor: Broadcom Corporation[/COLOR]
[COLOR=darkred]physical id: 2[/COLOR]
[COLOR=darkred]bus info: pci@0000:02:02.0[/COLOR]
[COLOR=darkred]version: 03[/COLOR]
[COLOR=darkred]width: 32 bits[/COLOR]
[COLOR=darkred]clock: 33MHz[/COLOR]
[COLOR=darkred]capabilities: bus_master[/COLOR]
[COLOR=darkred]configuration: driver=b43-pci-bridge latency=64[/COLOR]
[COLOR=darkred]resources: irq:17 memory:e8100000-e8101fff[/COLOR]
[COLOR=darkred]*-network[/COLOR]
[COLOR=darkred]description: Wireless interface[/COLOR]
[COLOR=darkred]physical id: 1[/COLOR]
[COLOR=darkred]logical name: wlan0[/COLOR]
[COLOR=darkred]serial: 00:90:4b:5b:cf:83[/COLOR]
[COLOR=darkred]capabilities: ethernet physical wireless[/COLOR]
[COLOR=darkred]configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/COLOR]
 
i tried the hardware drivers program but it would just say downloading and installing then give an error that it could not get files. 
 
in my first post i showed an error i recieved (its in the attachment) when i installed b43-fwcutter from my ubuntu 9.10 install cd. could that have been the cause of the bad b43 folder in my lib/firmware folder or is that how it should look. 
 
i uninstalled b43-fwcutter and reinstalled it but got the same error and the same results when i went threw these process again. I've downloaded a copy of b43-fwcutter-11 but don't know yet how to install off a tar.bz2 file. Again i'm brand new to all this so my best is just shots in the dark. Thanks again for yalls help.

---

### Post by puppywhacker on 2010-02-08
You're done with then installation of the firmware. Wlan0 is your interface name. Congratz.

Next step is to setup wlan0 to use your basestation and then setup the ip-adress and name-server. Although the basesstation may already do that for you.

On the topbar on the right you will find two computer network icons. Use them to setup the wireless

---

### Post by CharlesWallace on 2010-02-08
Yes but when i click activate on Hardware drivers it still gives me an error and dosn't say active.  I'll look at it some more this afternoon and get back to yall.

---

### Post by chili555 on 2010-02-08
> **CharlesWallace said:**
> Yes but when i click activate on Hardware drivers it still gives me an error and dosn't say active.  I'll look at it some more this afternoon and get back to yall.However, it *is *active, because you have a wlan0 interface all ready to go! Can you click on the Network Manager icon at the top right of your desktop, see your network and connect? If you do:```
sudo iwlist wlan0 scan
```do you see your network?

---

### Post by CharlesWallace on 2010-02-08
Well it works now.  I'm not sure what changed.  I rebooted before but didn't see the networks but this time they popped right up.  I'm actually typing this from ubuntu instead of XP which is nice.  I guess i wasn't looking in the right spots.  The Hardware Drives still said the drive was not activated but I was surfing the internet.  For fun I did hit activate and it downloaded the drivers and now it says its activated.  I'm not sure what that did but i've rebooted and it seems to be working fine. Thanks Puppywhacker and Chili555 for yalls help.

---

### Post by maycom on 2010-02-21
Hi, Exellent articel for a new Ubuntu/Linux user!! I've the same HP PC (but with BCM4303 ?).
I have followed the above instructions, but mu wlan0 is inactive, and the option "Enable Wireless" by right- click the network icon is fuzzy (not able to select it...)

In Terminal window i type:
sudo lshw -c network
And here's the output:
> 
 *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0204000-d0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:06:1d:83
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:a000(size=256) memory:d0208800-d02088ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:90:4b:5a:d9:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b



I'll be glad for any help! Thanks..

---

### Post by bkratz on 2010-02-21
> **maycom said:**
> Hi, Exellent articel for a new Ubuntu/Linux user!! I've the same HP PC (but with BCM4303 ?).
I have followed the above instructions, but mu wlan0 is inactive, and the option "Enable Wireless" by right- click the network icon is fuzzy (not able to select it...)

In Terminal window i type:
sudo lshw -c network
And here's the output:


I'll be glad for any help! Thanks..

Well your's is a bit different--the 4303 uses the b43legacy driver not the current b43. Here is a lot of information regarding the BCM4303

[http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy](http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy)

---

### Post by maycom on 2010-02-21
Thanks for reply! I've followed the instruction from [http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy](http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy). Also Activated the "Broadcom B43legacy Wireless driver" Under ***System -> Administration -> Hardware Drivers*** 

iwconfig in terminal:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

On my HP Pavilion zv5000 I've no light indicating that the wifi is turned on....

thanks :)

---

### Post by northd_tech on 2010-02-21
Can we see the results of these terminal commands:

```
lsmod

ifconfig

iwconfig

sudo iwlist scan
```

---

### Post by maycom on 2010-02-21
> **northd_tech said:**
> Can we see the results of these terminal commands:

```
lsmod

ifconfig

iwconfig

sudo iwlist scan
```


OK :) 

**lsmod**
```

Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
nls_utf8                1568  1 
ppp_deflate             4732  0 
zlib_deflate           20088  1 ppp_deflate
bsd_comp                5436  0 
ppp_async               8860  1 
crc_ccitt               1852  1 ppp_async
isofs                  31620  1 
binfmt_misc             8356  1 
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  2 
snd_atiixp             15720  2 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_atiixp_modem       11940  0 
snd_seq_midi            6432  0 
b43legacy             117752  0 
pcmcia                 36808  0 
snd_ac97_codec        101216  2 snd_atiixp,snd_atiixp_modem
ac97_bus                1532  1 snd_ac97_codec
snd_rawmidi            22208  1 snd_seq_midi
snd_pcm_oss            37920  0 
iptable_filter          3100  0 
snd_mixer_oss          16028  1 snd_pcm_oss
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
mac80211              181140  1 b43legacy
snd_pcm                75296  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
option                 23232  1 
usbserial              36264  4 option
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_atiixp,snd_seq_oss,snd_atiixp_modem,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_atiixp,snd_atiixp_modem,snd_pcm
psmouse                56500  0 
serio_raw               5280  0 
yenta_socket           24296  2 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               9932  0 
shpchp                 32272  0 
ppdev                   6688  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
b44                    28684  0 
8139too                22620  0 
ssb                    35364  2 b43legacy,b44
8139cp                 19260  0 
mii                     5212  3 b44,8139too,8139cp
usb_storage            52576  1 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  1 
agpgart                34988  3 ttm,drm,ati_agp

```

**ifconfig**

```

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:06:1d:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:89.8.103.93  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:24401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:18156022 (18.1 MB)  TX bytes:19948035 (19.9 MB)

```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**sudo iwlist scan**
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

---

### Post by bkratz on 2010-02-21
The drivers are there--did you unplug the wired connection when running these?

---

### Post by maycom on 2010-02-21
Yes, no cable connection... Just my mobile USB modem

---

### Post by northd_tech on 2010-02-21
> **maycom said:**
> 
**lsmod**
Module                  Size  Used by

**b43legacy **            117752  0 
mac80211              181140  1 **b43legacy**
cfg80211               93052  2 **b43legacy**,mac80211
led_class               4096  1 **b43legacy**

**[COLOR=DarkGreen]b44                    28684  0 [/COLOR]**
8139too                22620  0 
ssb                    35364  2 **b43legacy**,b44
8139cp                 19260  0 
mii                     5212  3 **[COLOR=DarkGreen]b44[/COLOR]**,8139too,8139cp

**sudo iwlist scan**
wlan0     Interface doesn't support scanning : **Network is down**

I believe you've got an extra module in there- I think the "b44" is for a Broadcom 4401 network interface from what I read earlier this morning at Broadcom's website- I posted this morning about it on one of the recent "broadcom 4318" threads that I need to update soon.

Also that "Network is down" makes me think you might need to run one of those "sudo ifdown... sudo ifup wlan0" kind of command sequences (but I'm not sure what the commands are for the older Broadcoms- I use the Broadcom STA driver).

If you are interested, there is a newer open source Broadcom "b43" wireless driver available for the older (pre-802.11n) Broadcom chips.  If you want to try that, you can read about it here:

**Open Source Firmware for b43 **
[http://ubuntuforums.org/showthread.php?t=1055078](http://ubuntuforums.org/showthread.php?t=1055078)

If you decide to try that, we will probably need to remove those b43legacy drivers and possibly blackist some stuff.

edit:  That "8139" stuff above is for your Realtek wired ethernet connection.

See post #10 here for info and links on the "b44" stuff that I found today:

[http://ubuntuforums.org/showpost.php?p=8859816&postcount=10](http://ubuntuforums.org/showpost.php?p=8859816&postcount=10)

---

### Post by maycom on 2010-02-21
Hi folks! Thanks for nice posts. As I'm new to Ubuntu I've to go slow here.... Have I messed it up here? I'll try to delete the b43legacy stuff.... :|

Thanks again for helping out!
Ubuntu looks so nice :)

---

### Post by northd_tech on 2010-02-21
First, let's try just getting rid of the "b44" stuff- I don't think that should be there (but bkratz would probably know better than I do- I think he has an older Broadcom- mine's a "4328" Broadcom).

We can always insert that module if we need it later.

Try this in a terminal:

```
sudo rmmod b44
```Let's also see the output when you enter this in a terminal:

```
cat /etc/modules

lsmod | grep b4 
```After you remove that "b44" module, you should restart the ubuntu and see if anything improved.  If it still doesn't give you a Network Manager option for wireless (usually just left of the volume control, which is just left of the system clock at the upper right screen), then we could try removing those b43legacy modules (but bkratz seemed to think that's what your Broadcom needs).  If you see your wireless network, then click it and see if it will connect.

---

### Post by maycom on 2010-02-21
So, I've done the the command: sudo rmmod b44
After reboot, by klicking the network icon, it says; "Wireless is disabled". Right click the icon and the "Enable Wireless" is fuzzy.... Can't click it...

here is the result fot the other commands:

```

roy@roy-ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```

```

roy@roy-ubuntu:~$ lsmod | grep b4
b43legacy             117752  0 
mac80211              181140  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
b44                    28684  0 
mii                     5212  3 8139too,b44,8139cp
ssb                    35364  2 b43legacy,b44

```

---

### Post by northd_tech on 2010-02-21
> **maycom said:**
>  **lsmod | grep b4**
b43legacy             117752  0 
mac80211              181140  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
**b44 **                   28684  0 
mii                     5212  3 8139too,b44,8139cp
ssb                    35364  2 b43legacy,**b44**

Hmmm. that "b44" is still there- it must be getting loaded from somewhere else.

Can you post the results of this terminal command:

```
cat /etc/modules.conf

cat /etc/modprobe.d/blacklist

cat /etc/modprobe.d/blacklist.conf

sudo rmmod -f b44

lsmod | grep b4

```

---

### Post by maycom on 2010-02-23
> **northd_tech said:**
> Hmmm. that "b44" is still there- it must be getting loaded from somewhere else.

Can you post the results of this terminal command:

```
cat /etc/modules.conf

cat /etc/modprobe.d/blacklist

cat /etc/modprobe.d/blacklist.conf

sudo rmmod -f b44

lsmod | grep b4

```

OK, this is the results

```

**roy@roy-ubuntu:~$ cat /etc/modules.conf**
cat: /etc/modules.conf: No such file or directory

[B]
roy@roy-ubuntu:~$ cat /etc/modprobe.d/blacklist[/B]
cat: /etc/modprobe.d/blacklist: No such file or directory


**roy@roy-ubuntu:~$ cat /etc/modprobe.d/blacklist.conf**
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

# Remove the b44 driver
blacklist b44


**roy@roy-ubuntu:~$ sudo rmmod -f b44**
[sudo] password for roy: 
ERROR: Removing 'b44': No such file or directory


**roy@roy-ubuntu:~$ lsmod | grep b4**
b43legacy             117752  0 
mac80211              181140  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
ssb                    35364  1 b43legacy

```
:confused:

---

### Post by bkratz on 2010-02-23
I looked back at an earlier posting (#15) and it say mode managed (which is good), but it also says TX power off ( not so good). I remember seeing something about that somewhere and will search and respond.

---

### Post by bkratz on 2010-02-23
I think I found what I was looking for, it won't take long to at least see if you are suffering from this!

Please see this thread and see if you are suffering from rfkill

[http://ubuntuforums.org/showthread.php?t=1334195&highlight=rfkill](http://ubuntuforums.org/showthread.php?t=1334195&highlight=rfkill)

post 18 is using the same card as you.  If you are showing this-- follow the link Chili555 provided for a possible solution (in post 19).

Good luck.

@northd_tech--sorry for intruding, but I thought this was important. By the way I actually have a DWA-130 (but would like to buy a Broadcom unit to play with, hence the interest!)

---

### Post by maycom on 2010-02-23
Hi, thanks!
Hmmmm.... think I have tha same problem.... "rfkill"-thing....
info in /var/log/messages;
```

----------------------------------------
Feb 23 17:10:17 roy-ubuntu kernel: [  784.542085] b43legacy-phy1: Broadcom 4301 WLAN found
Feb 23 17:10:17 roy-ubuntu kernel: [  784.640110] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
Feb 23 17:10:17 roy-ubuntu kernel: [  784.650660] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
Feb 23 17:10:17 roy-ubuntu kernel: [  784.659799] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
Feb 23 17:10:18 roy-ubuntu kernel: [  784.768033] b43legacy-phy1: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Feb 23 17:10:18 roy-ubuntu kernel: [  784.868926] Registered led device: b43legacy-phy1::tx
Feb 23 17:10:18 roy-ubuntu kernel: [  784.868975] Registered led device: b43legacy-phy1::rx
Feb 23 17:10:18 roy-ubuntu kernel: [  784.869025] Registered led device: b43legacy-phy1::radio
Feb 23 17:10:18 roy-ubuntu kernel: [  784.869179] b43legacy-phy1: Radio hardware status changed to DISABLED
Feb 23 17:10:18 roy-ubuntu kernel: [  784.928023] b43legacy-phy1: Radio turned on by software
Feb 23 17:10:18 roy-ubuntu kernel: [  784.928031] b43legacy-phy1: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
Feb 23 17:10:18 roy-ubuntu kernel: [  784.928227] ADDRCONF(NETDEV_UP): wlan0: link is not ready
-----------------------------

```

Sure I've a switch for WiFi on/off, works under MS Windows.....

---

### Post by bkratz on 2010-02-23
> **maycom said:**
> Hi, thanks!
Hmmmm.... think I have tha same problem.... "rfkill"-thing....
info in /var/log/messages;


Sure I've a switch for WiFi on/off, works under MS Windows.....




Could you copy/paste the outputs that Dr. Chili555 asked for in postings 4 and 7 of this thread?

[http://ubuntuforums.org/showthread.php?t=1334195&highlight=rfkill](http://ubuntuforums.org/showthread.php?t=1334195&highlight=rfkill)

---

### Post by maycom on 2010-02-23
I'll reinstall the whole thing first.... :|

---

### Post by bkratz on 2010-02-23
> **maycom said:**
> I'll reinstall the whole thing first.... :|

OK, but I really think we were close. Did you ever attempt posting 20 of that thread?

---

### Post by maycom on 2010-02-23
I moved this thread to [http://ubuntuforums.org/showthread.php?p=8871997#post8871997](http://ubuntuforums.org/showthread.php?p=8871997#post8871997)

---

