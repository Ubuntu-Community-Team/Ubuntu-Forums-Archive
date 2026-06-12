---
title: "lubuntu 13.04 fresh install, no wifi"
date: 2013-05-30
forum: Networking &amp; Wireless
---

### Post by soldierofapocalypse on 2013-05-30
I have freshly installed lubuntu 13.04 on my HP Presario V2000. The wifi is not working. It will not recognize any wireless networks. I executed "sudo apt-get install firmware-b43-installer" via the command line. The result is my wifi light will now turn on, but that is it. I am a novice, so please be patient. From what I've seen on some threads, I need to list some more info, so here it goes. If more info is needed please let me know. 

lspci- 

master@master-Presario-V2000-EP442UA-ABA:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS480/RS482/RS485 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS480M [Mobility Radeon Xpress 200]
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
   

lsusb- 

master@master-Presario-V2000-EP442UA-ABA:~$ lsusb
Bus 002 Device 002: ID 045e:00d2 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub





[COLOR=#000000][I]lshw -C network- 

[/I][/COLOR]master@master-Presario-V2000-EP442UA-ABA:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:29:4a:8f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.1.10.90 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:c0204000-c0205fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:71:57:58
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.8.0-22-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



[COLOR=#000000][I]ifconfig- 

[/I][/COLOR]master@master-Presario-V2000-EP442UA-ABA:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:29:4a:8f  
          inet addr:10.1.10.90  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe29:4a8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20519252 (20.5 MB)  TX bytes:2588481 (2.5 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94175 (94.1 KB)  TX bytes:94175 (94.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:14:a5:71:57:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


[COLOR=#000000][I]iwconfig- 

[/I][/COLOR]master@master-Presario-V2000-EP442UA-ABA:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


eth0      no wireless extensions.
 



lsmod- 

master@master-Presario-V2000-EP442UA-ABA:~$ lsmod
Module                  Size  Used by
hp_wmi                 17712  0 
sparse_keymap          13658  1 hp_wmi
joydev                 17097  0 
arc4                   12543  2 
b43                   351918  0 
snd_atiixp_modem       18585  0 
snd_atiixp             19309  1 
bcma                   39645  1 b43
snd_ac97_codec        105692  2 snd_atiixp_modem,snd_atiixp
bnep                   17669  2 
rfcomm                 37420  0 
ac97_bus               12670  1 snd_ac97_codec
bluetooth             202069  10 bnep,rfcomm
pcmcia                 39544  0 
radeon                870822  2 
snd_pcm                80890  3 snd_ac97_codec,snd_atiixp_modem,snd_atiixp
mac80211              526519  1 b43
snd_page_alloc         14230  3 snd_pcm,snd_atiixp_modem,snd_atiixp
snd_seq_midi           13132  0 
ttm                    71289  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         47545  1 radeon
snd_rawmidi            25114  1 snd_seq_midi
cfg80211              436177  2 b43,mac80211
yenta_socket           27095  0 
video                  18894  0 
drm                   228750  4 ttm,drm_kms_helper,radeon
pcmcia_rsrc            18191  1 yenta_socket
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
wmi                    18590  1 hp_wmi
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
i2c_algo_bit           13197  1 radeon
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
mac_hid                13037  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  10 snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_atiixp_modem,snd_atiixp
i2c_piix4              13066  0 
shpchp                 32129  0 
k8temp                 12842  0 
ati_agp                13177  0 
psmouse                81038  0 
serio_raw              13031  0 
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  1 lp
pata_acpi              12886  0 
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
ssb                    50834  1 b43
pata_atiixp            13058  2 
8139too                23071  0 
8139cp                 26557  0

---

### Post by Hadaka on 2013-05-30
hi , give this a try and see if it comes to life..
```
echo "blacklist hp_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv b43
sudo apt get install --reinstall b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
then boot.
is it alive??

---

### Post by soldierofapocalypse on 2013-05-30
Hi,thanks for the reply. I input those codes and rebooted. I can see the network now, but I am unable to connect to it. It will not authenticate the password. I know for a fact that I am inputting the correct password.

---

### Post by Hadaka on 2013-05-30
Probably just a matter of checking your settings...
let's look at a couple things first..
please COPY these commands into a terminal..
```
rfkill list all
ifconfig
iwlist wlan 0 scan
dmesg | grep b43
```
post the output..
thanks.

---

### Post by soldierofapocalypse on 2013-05-30
rfkill list all- master@master-Presario-V2000-EP442UA-ABA:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no 


ifconfig- 



master@master-Presario-V2000-EP442UA-ABA:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:29:4a:8f  
          inet addr:10.1.10.90  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe29:4a8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56958204 (56.9 MB)  TX bytes:1730904 (1.7 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62483 (62.4 KB)  TX bytes:62483 (62.4 KB)


wlan0     Link encap:Ethernet  HWaddr 00:14:a5:71:57:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



iwlist wlan 0 scan- master@master-Presario-V2000-EP442UA-ABA:~$ iwlist wlan 0 scan
iwlist: unknown command `0' (check 'iwlist --help'). 








dmesg | grep b43- master@master-Presario-V2000-EP442UA-ABA:~$ dmesg | grep b43
[   20.634499] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   20.684040] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   22.824101] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

---

### Post by Hadaka on 2013-05-30
ok, I have the same card in this machine.and i can reproduce your output by disabeling my wireless...
so..let's jump through a couple hoops here and see if we can get you going..
click the wireless icon...next to the envelope make sure "Enable wireless" is checked
then..click Edit connections..then Wireless....then Edit YOUR connection.
below are screen shots of what your settings should look like..   your security will of course be different..
see attached..
after you make thess changes..click SAVE
then..power down the computer...
power down the router....wait 3...4 minutes
power up the router...let it sync up to your modem
then..power up the computer..

---

### Post by soldierofapocalypse on 2013-05-30
Problem solved! You're really good! Thanks for taking the time to help me.

---

### Post by Hadaka on 2013-05-30
Great !! glad that worked for you...
please mark this thread solved..
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

