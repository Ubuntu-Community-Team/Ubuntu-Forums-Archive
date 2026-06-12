---
title: "Ndiswrapper 1.56 drivers installed   /modprobe.d/ problem"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by armadi on 2011-04-24
Hi I'm having some trouble getting my wireless card working. Here it is the outcome of different checks suggested in a troubleshooting guide from another post. Im' new with ubuntu so I don't really understand what all this mean. I'd appreciate if you can help me to figure it out.
There's something in bold that looks important!

armadi@ubuntu:~$ ndiswrapper -l
athfmwdl : driver installed
**WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.**
net5523 : driver installed
device (0D8E:7801) present
armadi@ubuntu:~$ uname -m
i686
armadi@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 90
serial: 00:0d:87:83:f4:f2
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list rom ethernet physical
configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 multicast=yes
resources: irq:5 ioport:cc00(size=256) memory:cffdc000-cffdcfff memory:cffa0000-cffbffff(prefetchable)
*-network
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:18:e7:45:70:0f
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+net5523 driverversion=1.55+,10/04/2004,1.0.1.4 multicast=yes wireless=IEEE 802.11g
armadi@ubuntu:~$ dmesg | grep -e ndis -e wlan
[ 19.414820] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 20.032221] ndiswrapper: driver ath

---

### Post by chili555 on 2011-04-24
This part is relatively trivial:> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.Let's fix it:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```This part is not trivial:> ndiswrapper -l
athfmwdl : driver installed
net5523 : driver installed
device (0D8E:7801) presentIt appears you have two, probably conflicting drivers installed.> dmesg | grep -e ndis -e wlan
[ 19.414820] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 20.032221] ndiswrapper: driver ath
There has to be more to it than that. I believe dmesg will tell us which one it likes and which it wishes would depart. When we find out, we'll erase the bad one:```
sudo ndiswrapper -e badone
```Can you please retry the dmesg command and see if we have more information?

---

### Post by armadi on 2011-04-24
I tried the dmesg code and this is whatI got:



dmesg | grep -e ndis -e wlan
[   35.038396] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   36.265503] ndiswrapper: driver net5523 (,10/04/2004,1.0.1.4) loaded
[   36.776100] wlan0: ethernet device 00:18:e7:45:70:0f using NDIS driver: net5523, version: 0x10000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0D8E:7801.F.conf
[   36.776168] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   36.776700] usbcore: registered new interface driver ndiswrapper
[   36.779392] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by chili555 on 2011-04-24
I believe, based on several Google searches, that both files are needed; sorry for my mis-step.

What difficulty are you having? Does it see networks when you click the Network Manager icon? What happens when you try to connect?

---

### Post by armadi on 2011-04-24
It's funny because before I did the whole procedure the icon was in in upper right corner saying there were no network connection, but now that you mentione it, it's gone. All I can tell you is that the led power of the usb wireless card is on but the one that blinks when is working is off. I opened the network manager thru in system tab but I don't see anything on the wireless tab it's like the card was not there.

---

### Post by armadi on 2011-04-24
I've been looking  around.it seems like I need to configure the network but I can't find how

---

### Post by chili555 on 2011-04-24
> It's funny because before I did the whole procedure the icon was in in upper right corner saying there were no network connection, but now that you mentione it, it's gone. Please right-click the panel at the top and Add to Panel a Notification Area. Does the Network Manager icon reappear?

---

### Post by armadi on 2011-04-24
It's not on the list of app to add up.

---

### Post by chili555 on 2011-04-26
Is Network Manager installed and running?```
ps aux | grep -i network
```If so, you should get something like:> root       715  0.0  0.2  26516  4664 ?        Ssl  08:21   0:00 [COLOR="Red"]Network[/COLOR]ManagerThen, please try:```
nm-applet &
```Does the icon appear or are there error messages?

If the icon appears, click it and see if you see your network and can connect.

---

### Post by armadi on 2011-04-26
I can see the icon now. But look,  it now says "Device not managed" in the Wireless Networks. What should I do then?

---

### Post by chili555 on 2011-04-26
Please post:```
ifconfig
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by armadi on 2011-04-26
Here:

eth0      Link encap:Ethernet  HWaddr 00:0d:87:83:f4:f2  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe83:f4f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:942600 (942.6 KB)  TX bytes:236622 (236.6 KB)
          Interrupt:5 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:e7:45:70:0f  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:18:e7:45:70:0f  
          inet addr:169.254.5.193  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

armadi@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

armadi@ubuntu:~$ sudo iwlist wlan0 scan
[sudo] password for armadi: 
wlan0     Scan completed :
          Cell 01 - Address: 00:18:9B:99:97:9A
                    ESSID:"57129694"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 4C:0F:6E:12:FE:60
                    ESSID:"7094"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

armadi@ubuntu:~$

---

### Post by chili555 on 2011-04-26
Network Manager is designed to default to wired if it's available. You have a working wired connection:> eth0 Link encap:Ethernet HWaddr 00:0d:87:83:f4:f2
inet addr:[COLOR="Red"]192.168.0.11[/COLOR] Bcast:192.168.0.255 Mask:255.255.255.0Please detach the ethernet cable, wait a few moments for NM to notice the change in state and see if wireless is now available and will connect.

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> **The computer should use the wired network connection when it's plugged in**, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for them

---

### Post by armadi on 2011-04-26
This might be useful. I just found in the Administrator tab a Windows Wireless Drivers. I opened it and  there I saw  the 2 driver we already know it's need: athfmwdl and net5523. The first one says "hardware present: no" and the second one says "hardware present: yes"

---

### Post by chili555 on 2011-04-26
> **armadi said:**
> This might be useful. I just found in the Administrator tab a Windows Wireless Drivers. I opened it and  there I saw  the 2 driver we already know it's need: athfmwdl and net5523. The first one says "hardware present: no" and the second one says "hardware present: yes"You have a working wireless interface. You can scan and see networks. I don't think we need to fix the driver.

---

### Post by armadi on 2011-04-26
I tried that to see what'd happen but the problem seems to be where I told you. about the wired connection, I had to plug it in so I could look for information and try it out right away since I had to restart and boot windows in order to access internet and then come back to ubuntu to try stuff out. But I need to work wireless, that's why I'm doing this.Now I'll keep that in mind to check when we work things out

---

### Post by chili555 on 2011-04-27
> it now says "Device not managed" in the Wireless Networks. What should I do then?Please do:```
sudo gedit /etc/network/interfaces
```The file should contain only:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```If there are any extra lines in there for wlan0 remove them. Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```Change "managed=false" to "managed=true". Proofread, save and close gedit. Reboot. Now is your wireless device available in Network Manager?

---

### Post by armadi on 2011-04-27
You're a genius buddy, it appeared and networks too. but now there's a problem after I rebooted it was all gone I can't find the wireless connections anymore.Wired is the only option I get know. Any idea what might have happened? But we're getting really close.

---

### Post by chili555 on 2011-04-28
Please do:```
sudo gedit /etc/modules
```Make sure ndiswrapper is listed. If not, add it. Proofread, save and close gedit. Now do:```
sudo modprobe gedit
```Is your wireless back?

---

### Post by armadi on 2011-04-29
Yes, it is. Thanks, but now there are no networks available like the first time. Should I reinstall everything to see if it works out? What do you think?

---

### Post by chili555 on 2011-04-29
> sudo modprobe geditWhat a goof! I really meant:```
sudo modprobe ndiswrapper
```Let's conduct some tests:```
dmesg | grep ndis
iwconfig
sudo iwlist wlan0 scan
```Thanks.

Are you running the latest release, Natty 11.04?

---

### Post by armadi on 2011-04-30
---- something strange: When I turn on my pc with the cable pluged, Wireless con. appears normally. Connections are there and when I try to connect I prompted to type a keyring pw which I don't have.
---- But when I turn it on with out the cable, wired connections appears as disconnected, of course, but that's when wireless conn. won't appear.
So this what I get when I conduct the test in this situation, from what I manage to understand, it seems as if the wireless device was not hooked up.

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
armadi@ubuntu:~$ dmesg | grep ndis
[   84.257000] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   85.939662] ndiswrapper: driver net5523 (,10/04/2004,1.0.1.4) loaded
[  100.984833] ndiswrapper (NdisWriteErrorLogEntry:190): log: C0001389, count: 4, return_address: eeaead1b
[  100.985334] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xcf907800
[  100.985678] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x28
[  100.986003] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xee971000
[  100.986346] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xee971000
[  100.987061] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[  100.987072] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  100.987093] ndiswrapper (mp_halt:262): device d034eba0 is not initialized - not halting
[  100.987099] ndiswrapper: device eth%d removed
[  100.987148] ndiswrapper: probe of 1-4:1.0 failed with error -22
[  100.987433] usbcore: registered new interface driver ndiswrapper
[  160.816136] Modules linked in: binfmt_misc snd_wavefront snd_cs4236 snd_intel8x0 snd_wss_lib snd_ac97_codec snd_opl3_lib ac97_bus snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_mpu401 snd_mpu401_uart snd_seq_dummy snd_seq_oss snd_seq_midi fbcon snd_rawmidi tileblit font bitblit softcursor snd_seq_midi_event vga16fb snd_seq vgastate snd_timer snd_seq_device sis_agp i2c_sis96x snd snd_page_alloc agpgart shpchp soundcore ppdev ns558 ndiswrapper parport_pc gameport lp parport usbhid hid floppy sis900 mii
armadi@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

armadi@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

---

### Post by armadi on 2011-05-06
I worked it out. the problem appeared to be to version I was running. Since I had first installed the wubi version, I had been having problems not only with wireless but also with other conf settings so I decide to try installing it from a Live USB and things have been working really well ever since. Thank you Chili for your help, time and patience. One last question how do I report this thread solve??

---

### Post by chili555 on 2011-05-07
> how do I report this thread solve??Click Thread Tools at the top of the thread and click Mark as Solved.

Glad it's working!

---

