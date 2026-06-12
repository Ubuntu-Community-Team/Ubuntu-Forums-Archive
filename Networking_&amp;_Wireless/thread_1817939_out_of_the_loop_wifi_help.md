---
title: "out of the loop wifi help"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by garyhibdon on 2011-08-04
i know this is probably listed somewhere, but after several hours looking around, noone has this same issue. long story short, my girlfriends gateway laptop (bleh) had a hdd fail and crashed. best buy said shed have to wait ANOTHER week, after she had already been out a comp for  2 weeks, to get the factory install windows 7 disc. so she asked me to put ubuntu on it. finished it yesterday, updated etc. heres the issue.

its a gateway nv55c w/ built in wifi card ( not sure on type) attempting to connect to a wrt54g linksys wifi router. it tries to connect, takes 3 mins then says disconnected. any ideas?

comp is running 11.04 natty.

---

### Post by garyhibdon on 2011-08-04
no one has any ideas? ive tried just about everything i could find or think of and im out of ideas. could REALLY use some help here.



p.s. the card is an 802.1 a if i read correctly

---

### Post by linuxman94 on 2011-08-04
Please post the results of these commands.  They will help us determine what exact card you have

```
ifconfig
```
and
```
lspci
```

---

### Post by garyhibdon on 2011-08-05
```
 ifconfig 
```showed

schookiebear@schookiebear-NV55C:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:14:79:c1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e75:8ff:fe14:79c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2809030 (2.8 MB)  TX bytes:582386 (582.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:5f:d1:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f8560000-f8560100 

schookiebear@schookiebear-NV55C:~$ 
and 
```
lspci
```showed

schookiebear@schookiebear-NV55C:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller (rev ff)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
schookiebear@schookiebear-NV55C:~$


p.s. yes im aware this comp sucks. thats why i wont put money into it. lol

---

### Post by garyhibdon on 2011-08-06
i tried installing the drivers from gateway.com and it stopped even acknowledging that there even WAS a wireless card.

---

### Post by garyhibdon on 2011-08-06
i REALLY could use some help here. the light on the laptop saying that the wireless card is working is off and there arent any switches to turn it on and its not searching  for or registering and wireless connections...

---

### Post by nm_geo on 2011-08-06
Try these two commands paste results please

```
lspci -nn | grep 0280
```

```
sudo lshw -C network
```

---

### Post by nm_geo on 2011-08-06
Duplicate

---

### Post by garyhibdon on 2011-08-06
*-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:14:79:c1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 memory:b1400000-b140ffff

---

### Post by nm_geo on 2011-08-06
That was all you got from the?  i am concerned that we got no wlan0 listed. in the lshw command.  

```
sudo lshw -C network

```Try this please

```
lspci -nn 
```Also 

```
modinfo rtl8192se
```We will check your kernel with that one..

```
rfkill list all
```some switch will be tested with this command

```
lsmod 
```that will give us drivers and modules running

---

### Post by garyhibdon on 2011-08-06
2 of those didnt do anything but heres the full printout

schnookiebear@schnookiebear-NV55C:~$ sudo lshw -c network
[sudo] password for schnookiebear: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:14:79:c1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 memory:b1400000-b140ffff
schnookiebear@schnookiebear-NV55C:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
schnookiebear@schnookiebear-NV55C:~$ modinfo rtl8192se
ERROR: modinfo: could not find module rtl8192se
schnookiebear@schnookiebear-NV55C:~$ rfkill list all
schnookiebear@schnookiebear-NV55C:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
i915                  450969  3 
binfmt_misc            13213  1 
videodev               75143  1 uvcvideo
snd_timer              28659  2 snd_pcm,snd_seq
sparse_keymap          13666  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
psmouse                59039  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   184133  4 i915,drm_kms_helper
intel_ips              17769  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
usb_storage            43946  1 
uas                    17676  0 
tg3                   131476  0 
libahci                25548  1 ahci
schnookiebear@schnookiebear-NV55C:~$

---

### Post by garyhibdon on 2011-08-06
on a side note, trying to figure this out is REALLY giving me alot of time to beat supertux, so i cant say its ALL bad. lol thanks for all the help ive gotten/ am getting. i really do appreciate it.

---

### Post by nm_geo on 2011-08-06
You are running a fresh install of Natty 11.04 and connected with ethernet cable?

```
cat /etc/lsb-release; uname -a
```Makes repositories work.
```
sudo apt-get update
```Updates all the missing files (hopefully)
```
sudo apt-get upgrade
```This will take some time I imagine.

---

### Post by garyhibdon on 2011-08-06
yes i just redid it again. originally i had installed the files directly from gateway.com, but they never and actually had made it worse so i deleted and reinstalled about 4 hours ago. and yeah its on a hardline atm.

heres the whole printout

schnookiebear@schnookiebear-NV55C:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux schnookiebear-NV55C 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011 i686 i686 i386 GNU/Linux
schnookiebear@schnookiebear-NV55C:~$ sudo apt-get update
[sudo] password for schnookiebear: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
schnookiebear@schnookiebear-NV55C:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
schnookiebear@schnookiebear-NV55C:~$

---

### Post by nm_geo on 2011-08-06
Okay 

```
sudo ifconfig
``````
sudo iwconfig
``````
rfkill list all
```If we get no response from the rfkill list all again

```
sudo apt-get install rfkill
```The rerun 
```

rfkill list all
```

---

### Post by garyhibdon on 2011-08-06
i hate $250 comps lol

schnookiebear@schnookiebear-NV55C:~$ sudo ifconfig
[sudo] password for schnookiebear: 
eth0      Link encap:Ethernet  HWaddr 1c:75:08:14:79:c1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e75:8ff:fe14:79c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82629376 (82.6 MB)  TX bytes:3534217 (3.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

schnookiebear@schnookiebear-NV55C:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

schnookiebear@schnookiebear-NV55C:~$ rfkill list all
schnookiebear@schnookiebear-NV55C:~$ sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rfkill is already the newest version.
The following package was automatically installed and is no longer required:
  linux-headers-2.6.38-8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
schnookiebear@schnookiebear-NV55C:~$ rfkill list all
schnookiebear@schnookiebear-NV55C:~$

---

### Post by nm_geo on 2011-08-06
Let see what this one does. 


```
sudo ifconfig wlan0 up
```

---

### Post by garyhibdon on 2011-08-06
schnookiebear@schnookiebear-NV55C:~$ sudo ifconfig wlan0 up
[sudo] password for schnookiebear: 
wlan0: ERROR while getting interface flags: No such device
schnookiebear@schnookiebear-NV55C:~$ 


looks like its BACK to best buy. again
this thing is such a piece. if the wlan is down then this thing goes back for the third time in a month and she gets a new comp. any other ideas? other wise im gettin rid of this issue

---

### Post by nm_geo on 2011-08-06
Gary here is my concern

When linuxman asked you to run 

```
lspci
``` We got this line.

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller (rev ff)

When i asked for```
 lspci -nn
```we get no report of the Wireless Realtek card.  All we are trying to do is see the pci:id or number of the card.. But it doesn't appear.

Run this please
```

dmesg | grep wlan0
```

---

### Post by nm_geo on 2011-08-06
Maybe chili555 will have an idea tomorrow or he could drive over and fix it..:)

Amended shheeeshh... I drove to much today the obvious escapes me..
Boot into your Bios when you first start the computer and hit the special key or keys ..
Then in the Bios check to make sure the wireless is enabled.

---

### Post by garyhibdon on 2011-08-07
theres no response whatsoever. it just starts a new command line. i know that its there, and when i first turned the comp on after finishing the install, it worked for a very brief time, then turned off and hasnt worked since.

---

### Post by garyhibdon on 2011-08-07
and i just came from  the bios and i didnt even see an option for it. didnt see it anywhere actually. its very unusual. this computer had windows 7 and had a hdd fail. best buy swapped it out and "didnt have the gateway install disk" so my girl wanted me to install ubuntu on it. i worked for a couple days, though it would not connect wirelessly, and then it stopped altoget. i just REALLY hather after i installed the gateway drivers.  i thought for sure a destructive re-install would fix it but i just dont know. i followed a couple of other ideas other people had and then when it stopped responding at all so ill retry again i suppose. i just REALLY hate acer products. lol

---

### Post by garyhibdon on 2011-08-07
im sorry for that poor excuse of an explanation on the last post, not sure what happened, the last few lines got scrambled. basically, i tried some other ideas fokes had on similiar machines and it made this one worse off. i redid natty again and NOTHING is showing up about a wireless adapter so i think this one is fried. wouldnt surprise me at all. its already been back to best buy twice. next time she goes back under warranty and she gets a new comp, so yeah. still hoping not to lose this one though. any test can be run to text it otherwise? 


EDIT: ok so while i tried to load supertux again, the damn comp froze. wouldnt respond top anything. i did a hard kill and the wifi is working again . . . ?  someone help quick before it takes a crap on me again . lol

---

### Post by garyhibdon on 2011-08-07
ok so i reran all the tests and here are the results. it appears to be on, but still will not connect.


schnookiebear@schnookiebear-NV55C:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
schnookiebear@schnookiebear-NV55C:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:14:79:c1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e75:8ff:fe14:79c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12392960 (12.3 MB)  TX bytes:3583694 (3.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:5f:d1:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f8568000-f8568100 

schnookiebear@schnookiebear-NV55C:~$ modinfo rtl8192se
ERROR: modinfo: could not find module rtl8192se
schnookiebear@schnookiebear-NV55C:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  450969  3 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
sparse_keymap          13666  0 
psmouse                59039  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
r8192se_pci           482548  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184133  4 i915,drm_kms_helper
serio_raw              12990  0 
cfg80211              156212  1 r8192se_pci
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              17769  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
tg3                   131476  0 
schnookiebear@schnookiebear-NV55C:~$ sudo ifconfig wlan0
[sudo] password for schnookiebear: 
wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:5f:d1:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f8568000-f8568100 

schnookiebear@schnookiebear-NV55C:~$

---

### Post by garyhibdon on 2011-08-11
tried several times with many different plugins and updates and still nothing is working. are there any preliminary test to check and make sure the damn thing is even working properly.

---

### Post by garyhibdon on 2011-08-12
ok so i guess im a noob. lol i forced it to look for more updates, installed them, and im on wifi now. thanks for the help, but this one is solv-ed.

---

