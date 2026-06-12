---
title: "No internet on 9.04 with Realtek RTL8139 card"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by evajulia on 2010-02-14
**[COLOR=Purple]*[FONT=Georgia][SIZE=2]Hi dear Ubuntu users,[/SIZE][/FONT]*[/COLOR]**

I'm new to this whole Ubuntu thing, so bear with me :) 

I have installed 9.04 ( I currently have it on dual boot with Windows XP) and my problem is that I have no internet connection. I have a Motorola modem with a  Realtek RTL8139 Family Fast Ethernet NIC network card ( it's a wired connection, btw) When I plug in the cable, there's a little animation, but after a while I get the message: Wired connection is not active (or something like that) Here's what I did so far:

1) I ticked the Wake-On-Lan option in XP, since I read it in the forums that I could solve my problem. It did not :(
2) I turned off my modem, rebooted my system.
3) I deleted the Auto Ethernet network, and plugged in the cable again...no use.
4) I did an ifconfig, since I know that is what you guys really want :)

evajulia@Derek:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:ab:2b:3a
          inet6 addr: fe80::218:f3ff:feab:2b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3336 (3.3 KB)  TX bytes:2520 (2.5 KB)
          Interrupt:20 Base address:0xb800 
 lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

What can be the problem? I really want to use Ubuntu but it's not the same without internet you know...please, I know that Google is my friend, but belive me, I searched for my problem, but could not find a working solution....

**[COLOR=Teal]*[FONT=Georgia][SIZE=2]Eva Julia[/SIZE][/FONT]*[/COLOR]**

---

### Post by chili555 on 2010-02-14
> I'm new to this whole Ubuntu thing, so bear with meOnce upon a time, so were we, so no worries. May we also see:```
sudo ethtool eth0
lsmod | grep 813
lspci -nn | grep Ethernet
```Thanks!

---

### Post by evajulia on 2010-02-14
Thanks for your fast answer:) Here are the results of the commands you requested: 
```

evajulia@Derek:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: yes
evajulia@Derek:~$ lsmod | grep 813
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
evajulia@Derek:~$ lspci -nn | grep Ethernet
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
evajulia@Derek:~$ 
```

---

### Post by chili555 on 2010-02-14
> 13312  2 [COLOR="Red"]8139too[/COLOR],[COLOR="Blue"]8139cp[/COLOR]Two different driver modules have grabbed the device and may be fighting for world domination. I am not sure which is more appropriate, so let's take a gamble and try one fix. Please open a terminal and do:```
sudo rmmod -f 8139too
```Now will Network Manager allow your ethernet to connect? If so, we can make this permanent.

If it doesn't work, please post:```
dmesg | grep 8139
```

Please post back so the searchers know what worked or not.

---

### Post by evajulia on 2010-02-14
Bad news: none of them worked :( 
I entered the first code and checked whether I could connect, but interestingly, I couldn't even find my connection. I mean, when I click on the networking icon (on the main bar) there used to be an Auto Eth0 option, but it had disappeared after I entered the code. ( I could still access it through the  options, though, I just though you should know it)
Anyways, still no internet.

I tried your second code, and got this message in the terminal:

```
evajulia@Derek:~$ dmesg | grep 8139
[    2.914043] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.914081] 8139cp 0000:02:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.917106] 8139too Fast Ethernet driver 0.9.28
[    2.917157] 8139too 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.919020] eth0: RealTek RTL8139 at 0xb800, 00:18:f3:ab:2b:3a, IRQ 20
[    2.919023] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   96.697433] 8139too 0000:02:00.0: PCI INT A disabled
evajulia@Derek:~$ 
```Thanks a million though for your help, really, I hope we (well, it's rather You) will find a solution to my problem :)

---

### Post by chili555 on 2010-02-14
> This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139tooHere's a clue. Let's try the other driver, instead.```
sudo modprobe 8139too
sudo rmmod -f 8139cp
```Now does it work?

---

### Post by evajulia on 2010-02-14
Hate to say this, but still no luck, nothing has changed, I entered the codes, but it's still the same, no wired connection

---

### Post by chili555 on 2010-02-14
Please do:```
sudo su
echo "blacklist 8139cp" >> /etc/modprobe.d/blacklist.conf
```Now reboot and let us know; hopefully, of your success.

---

### Post by evajulia on 2010-02-14
I don't even dare telling you this, but it still doesn't work... I'm slowly giving up the hope that some day I'll become an Ubuntu user ... :frown:

---

### Post by chili555 on 2010-02-14
> giving up the hopeAfter only an hour? We can do this! Hang in there. May we see:```
dmesg | grep eth0
dmesg | grep 8139
```Thanks.

---

### Post by evajulia on 2010-02-14
Ok, ok, I will not give up :) I just don't know how many ideas you have left, you've given me so many tips already :)

So, here's my results:

```
evajulia@Derek:~$ dmesg | grep eth0
[    3.367543] eth0: RealTek RTL8139 at 0xb800, 00:18:f3:ab:2b:3a, IRQ 20
[    3.367546] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   21.292281] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   31.828036] eth0: no IPv6 routers present
evajulia@Derek:~$ dmesg | grep 8139
[    3.362573] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.362612] 8139cp 0000:02:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.365633] 8139too Fast Ethernet driver 0.9.28
[    3.365684] 8139too 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.367543] eth0: RealTek RTL8139 at 0xb800, 00:18:f3:ab:2b:3a, IRQ 20
[    3.367546] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
evajulia@Derek:~$ 
```

---

### Post by northd_tech on 2010-02-14
> **evajulia said:**
> 
  dmesg | grep eth0
[    3.367543] eth0: RealTek RTL8139 at 0xb800, 00:18:f3:ab:2b:3a, IRQ 20
[    3.367546] eth0:  **Identified 8139 chip type 'RTL-8100B/8139D**'
[   21.292281] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   31.828036] eth0: no IPv6 routers present
dmesg | grep 8139
[    3.362573] **8139cp**: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.362612] **8139cp** 0000:02:00.0:** This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too**
[    3.365633] **8139too** Fast Ethernet driver 0.9.28
[    3.365684] **8139too** 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.367543] eth0: RealTek RTL8139 at 0xb800, 00:18:f3:ab:2b:3a, IRQ 20
[    3.367546] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'


Is it me, or is that 8139cp module still hanging around causing problems after that **sudo rmmod** command above, chili?

Could the 8139D chip not be entirely compatible with that 8139C/C+ module?

edit:  Can we see the results of another **lsmod** command Eva?

---

### Post by chili555 on 2010-02-14
> [    3.362573] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
This shouldn't happen, since we blacklisted it. Please check:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Is this line in there?```
blacklist 8139cp
```If not, please add it. Proofread, save and close gedit.


Reboot. 

Now, does Wired Network show when you click Network Manager? Can you ask it to connect?

---

### Post by chili555 on 2010-02-14
> is that 8139cp module still hanging around causing problems after that sudo rmmod command above, chili?Correct. Please see my reply above.

---

### Post by evajulia on 2010-02-14
Could you tell me what is this proofread thing? Is it an option in the Terminal or something? I'm asking this now, since it takes me a while to switch Operating Systems and I don't want to do anything wrong :)

---

### Post by chili555 on 2010-02-14
This proofread thing is where I, because of my ancient eyes and dirty glasses, have to check over my work carefully before I hit "Save" and commit a typographical error to the system. Some people are lucky enough to type correctly the first time, every time. Some others, including me, must proofread.

---

### Post by evajulia on 2010-02-14
ohh, proofread, ok, I got it :)

well, I made an lsmod again, here are the results:
```

Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
rfkill_input           12800  0 
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
joydev                 18368  0 
lp                     17156  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
arc4                    9856  2 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
ecb                    10752  2 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
b43                   131484  0 
mmc_block              17668  2 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 44748  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 b43
psmouse                61972  0 
ppdev                  15620  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
serio_raw              13316  0 
cfg80211               38032  1 mac80211
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
pcspkr                 10496  0 
input_polldev          11912  1 b43
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ati_agp                14988  0 
i2c_piix4              18448  0 
asus_laptop            24440  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
agpgart                42696  2 drm,ati_agp
led_class              12036  2 b43,asus_laptop
video                  25360  0 
output                 11008  1 video
shpchp                 40212  0 
usbhid                 42336  0 
ssb                    41220  1 b43
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

As for the blacklisting, it is listed ( I guess I should say unfortunately) 
```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist 8139cp
```

---

### Post by chili555 on 2010-02-14
> 8139too                32128  0 
[COLOR="Blue"]8139cp[/COLOR]                 27776  0 
mii                    13312  2 8139too,[COLOR="Blue"]8139cp[/COLOR]Man, oh man! Please try this again: ```
sudo rmmod -f 8139cp
```Wait a few moments and do:```
lsmod | grep 8139
```If 8139cp is still there, I am going to fly directly to Hungary and cry. If it is gone, what does Network Manager say about wired ethernet?

---

### Post by northd_tech on 2010-02-14
> **evajulia said:**
> 
well, I made an lsmod again, here are the results:

Module                  Size  Used by

[COLOR=Red]**b43 **                  131484  0 
mac80211              217208  1 **b43**
cfg80211               38032  1 mac80211
ssb                    41220  1 **b43**[/COLOR]
8139too                32128  0 
**8139cp **                27776  0 
mii                    13312  2 8139too,**8139cp**

As luck would have it, I've been reading up and working with Broadcom wireless for a couple of years now (that's what brand my laptop has).

You appear to have a Broadcom "b43" wireless driver module loaded (along with its associated mac80211, cfg80211, and "ssb" modules- everything in [COLOR=Red]red[/COLOR] above) in addition to those 2 Realtek modules.  Does your wireless connection work?

You could run these commands to get rid of that Broadcom stuff if necessary:

```
sudo rmmod -f b43
[COLOR=Black]
sudo rmmod -f  [/COLOR][COLOR=Black]mac80211 

sudo rmmod -f [/COLOR][COLOR=Black]cfg80211  [/COLOR]

sudo rmmod -f ssb 
```Then we could blacklist all that "b43" Broadcom wireless stuff too.  That would need you to run this command again:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```Then add the following lines to your blacklist file and save it, then exit gedit and reboot.

```
blacklist b43
blacklist mac80211
blacklist cfg80211
blacklist ssb
```Hopefully, that will move things in the right direction.

edit:  Actually, you might have a Broadcom wireless interface- is your wireless connection working?  We probably need to see the full output of the following commands:

```
lspci

sudo lshw -C network 

ifconfig

iwconfig
```

Maybe you should leave the Broadcom wireless stuff and see if we can get that working first.

---

### Post by northd_tech on 2010-02-14
duplicate post removed by author

---

### Post by evajulia on 2010-02-15
Sorry for the slow reply, but I wasn't at home till now. Soo...here are my results :)

@chili555
```

evajulia@Derek:~$ sudo rmmod -f 8139cp
[sudo] password for evajulia: 
evajulia@Derek:~$ lsmod | grep 8139
8139too                32128  0 
mii                    13312  1 8139too
evajulia@Derek:~$ 

```

@northd_tech

I followed the instruction after the "edit"

```
evajulia@Derek:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
evajulia@Derek:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:ab:2b:3a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:73:ad:c8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:f6:91:39:64:f7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
evajulia@Derek:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:ab:2b:3a  
          inet6 addr: fe80::218:f3ff:feab:2b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11425 (11.4 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:20 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

evajulia@Derek:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

evajulia@Derek:~$ 
```


Just a quick question: If I remove that broadcom thing, will I be able later to use wireless internet? Currently I don't have any, and I don't know of any I could/would join nowadays...Btw, the wireless networking option is ticked, but it is not availabe. I don't know if that helps...

---

### Post by chili555 on 2010-02-15
> If I remove that broadcom thing, will I be able later to use wireless internet?Not without going back in to reverse the changes. Frankly, I highly doubt it has anything to do with our problem. I suggest you not make those changes quite yet, at least until we can determine that the wireless is somehow interfering with wired ethernet. So far, I have seen no evidence that it is.

Once you successfully removed 8139cp, is there any option to connect in Network Manager? May we see:```
dmesg | grep eth0
```Thanks.

Please do:```
sudo gedit /etc/rc.local
```Add a line:```
rmmod -f 8139cp
```Proofread, save and close gedit. This will make the removal of the module permanent, hopefully.

---

### Post by northd_tech on 2010-02-15
> **evajulia said:**
> Sorry for the slow reply, but I wasn't at home till now.  sudo rmmod -f 8139cp
[sudo] password for evajulia: 
  
lsmod | grep 8139
**8139too **               32128  0 
mii                    13312  1 **8139too**
  
lspci
02:00.0 Ethernet controller: **Realtek** Semiconductor Co., Ltd. **RTL-8139/8139C/8139C+** (rev 10)
02:03.0 Network controller: **Broadcom Corporation BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:ab:2b:3a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=**b43**-pci-bridge latency=64 module=**ssb**
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:73:ad:c8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:f6:91:39:64:f7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:ab:2b:3a  
          inet6 addr: fe80::218:f3ff:feab:2b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          **RX packets:172** errors:0 dropped:0 overruns:0 frame:0
          **TX packets:10** errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          **RX bytes:11425 (11.4 KB)  TX bytes:1836 (1.8 KB)**
          Interrupt:20 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr off   Fragment thr=2352 B   
          Power Management off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Just a quick question: If I remove that broadcom thing, will I be able later to use wireless internet? Currently I don't have any, and I don't know of any I could/would join nowadays...Btw, the wireless networking option is ticked, but it is not available. I don't know if that helps...

Let's leave the Broadcom 4318 wireless as it is currently- it really should not interfere with the ethernet (cabled) interface.  The "b43" is usually the proper driver for the Broadcom 4318 WiFi (I've been working with a few people who have those 4318 wireless, and my laptop computer has a Broadcom 4321AG).

Looking at the RX/TX that I have bolded above, you do appear to actually be receiving (Rx) and transmitting (Tx) a little traffic over the ethernet now.  The 8139too does appear to be the proper module for that Realtek network/ethernet card (NIC), and the 8139cp module/conflict does actually appear to be gone for good now- so that looks correct.

Are you able to enter the following command in a terminal and get any results?  You will likely need to press Ctrl-C to stop the **ping**s (or it will run continuously):

```
ping www.stanford.edu

ping www.google.com
```Also, are you able to find any webpages in an internet browser now?  Does your ethernet show to be connected in Network Manager?  You might need to restart ubuntu, and you still might need to do a little configuration work.

edit:  If you search for "Broadcom 4318" you should be able to find several threads here about the wireless.  Do you know of any internet cafes (or possibly a library) nearby that have wireless service available?  I know that there weren't many wireless access points when I was in Germany a few years ago.

---

### Post by evajulia on 2010-02-15
@chili555:
```
evajulia@Derek:~$ dmesg | grep eth0
[    2.925077] eth0: RealTek RTL8139 at 0xb800, 00:18:f3:ab:2b:3a, IRQ 20
[    2.925079] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   20.841918] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   31.192030] eth0: no IPv6 routers present
evajulia@Derek:~$ 

```


I entered that line you have mentioned, but I'm not sure I put it in the right place, that's how it looks like now:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
rmmod -f 8139cp
```


@northd_tech I cannot ping anything :( I can type it in the terminal, but I don't get any results...I tried it in the network tools as well, but it had no use...

---

### Post by chili555 on 2010-02-15
> [    2.925077] eth0: RealTek RTL8139 at 0xb800, 00:18:f3:ab:2b:3a, IRQ 20
[    2.925079] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   20.841918] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   31.192030] eth0: no IPv6 routers present
All this looks very normal and very hopeful.> --- snip ---
# By default this script does nothing.

exit 0
rmmod -f 8139cpSorry, I wasn't clear. Please amend it to:```
# By default this script does nothing.

rmmod -f 8139cp

exit 0
```What is Network Manager saying and doing about wired ethernet?

---

### Post by northd_tech on 2010-02-15
Just as a thought- that small amount of network traffic might just be your computer communicating back & forth with the ethernet switch.  It is possible that a router/cable modem setting or firewall is blocking your access to the "outside world" on the back side of that ethernet switch/hub.  Have you checked with whoever provides the internet connection?

The results you posted look to me like that Realtek 8139 ethernet is ready to work, but there may be a problem external to the computer now.  Also, those settings for the Broadcom 4318 wireless don't look very far off from what I remember, either.  It is possible that WiFi might work if you could find an access point. 

Some of the routers and gateways that I have worked with had an option to connect to the router and "learn" or to enter a particular machine's MAC address in its "known clients" list as a security measure (and it often ran faster that way as the machine was "recognized" almost instantly).

---

### Post by evajulia on 2010-02-15
Ok, I changed my those lines in the gedit...umm what Netwok Manager? Sorry, I couldn't find that option...I just found Network Tools and Network Connections , but not Network Manager. Sorry if I'm hopeless, I don't really know my way about Ubuntu...(yet :) ) I still cannot acces to the internet, however, if that counts...

  "Have you checked with whoever provides the internet connection?"
 I called my internet provider, but they said that they are sorry but they can only give advice in connection with Windows OSs...

---

### Post by chili555 on 2010-02-15
If the cable is plugged in, there should be a small icon at the top right of your desktop that looks like a wall jack with a cable nearby. When you left-click it, the attached should appear. As you can see, when the pointer is hovered over the icon, it reports that 'Auto Ethernet' is active. If you are unable to find it, let's try the old fashioned way:```
sudo /etc/init.d/network-manager stop
sudo dhclient eth0
```I will be especially interested in the outcome.

---

### Post by evajulia on 2010-02-15
Here's what I got:

```
evajulia@Derek:~$ sudo /etc/init.d/network-manager stop
sudo: /etc/init.d/network-manager: command not found
evajulia@Derek:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 3466
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:18:f3:ab:2b:3a
Sending on   LPF/eth0/00:18:f3:ab:2b:3a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

edit: I couldn't find that jack icon you mentioned, that's what I can show you

---

### Post by chili555 on 2010-02-15
> sudo: /etc/init.d/network-manager: command not found
Please run:```
ls /etc/init.d | grep -i network
```It may be, on some systems, NetworkManager instead of network-manager, as on one of my laptops. Whatever it is, stop it and run the dhclient command. If it still doesn't get an IP address, you will need to restart it.```
sudo /etc/init.d/NetworkManager start
```You found the Network Manager icon! Are you able to put a dot in the circle next to 'eth0?' Does that help us connect?

What does this tell us:```
cat /etc/network/interfaces
```Thanks.

---

### Post by evajulia on 2010-02-15
```
NETWORK MANAGER
evajulia@Derek:~$ ls /etc/init.d | grep -i network
networking
NetworkManager
evajulia@Derek:~$ sudo /etc/init.d/NetworkManager stop
[sudo] password for evajulia: 
 * Stopping network connection manager NetworkManager    [ OK ] 
evajulia@Derek:~$ dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
wmaster0: unknown hardware address type 801
Open a socket for LPF: Operation not permitted
evajulia@Derek:~$ sudo /etc/init.d/NetworkManager start
 * Starting network connection manager NetworkManager    [ OK ] 
evajulia@Derek:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

 As you can see, I stopped and restarted my Network Manager, and tried to connect,
with no success. If I click on that circle next to eth0, it tries to connect (little animation) but it says that my Wired Connection is inactve.

---

### Post by chili555 on 2010-02-15
Please try:```
sudo rmmod -f 8139too
sudo modprobe 8139too use_io=1
```Next, let's try again:```
sudo /etc/init.d/NetworkManager stop
sudo dhclient eth0
sudo /etc/init.d/NetworkManager start
```Any improvement?

If not, then do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file, dmesg.zip in your /home/user directory that you can move with a USB drive or similar and post here as an attachment to your reply.

---

### Post by evajulia on 2010-02-15
> Any improvement?

nope...so here's my .zip file.

Have I mentioned that I'm really grateful for your help? :) I really am, no matter that the solutions didn't work so far, I belive that we're getting closer and closer to the  solution :)

---

### Post by chili555 on 2010-02-15
Your very first post says you enabled Wake on LAN in XP. I saw this:  [http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/)

It refers to 'Wake on LAN [COLOR="Blue"]after shutdown[/COLOR].' Can you confirm that is the function you enabled?

Next, I see this in your dmesg:> [    0.542241] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.542417] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.542590] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.542763] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.542939] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.543113] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.543282] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.543455] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.That is a lot of disableds! You might check in your computer's BIOS and check the section that assigns interrupts, or IRQs. My laptops work best with 'Auto Select.' Please see attached.

Finally, does this computer plug into a router, DSL modem or cable modem?

---

### Post by chili555 on 2010-02-15
> I have a Motorola modemIs this by chance a DSL modem where (at least with DSL providers I am familiar with here in the USA) you must give a user name and password?

---

### Post by evajulia on 2010-02-15
Damn it, my bad...it was NOT Wake On Lan after shutdown , but a simple "Allow this device to bring the computer out of standby" option...I must have misread something in the post...I checked it, however, and my network card does not have the WOL option, unlike here: 

[IMG]http://www.energystar.gov/ia/products/power_mgt/marvell_yukon.jpg[/IMG]

I do not have such option, that must be a problem I guess...but what can I do in this case??


Yes, it is a modem, but I have cable net (I have no idea how you say it in English) so I don't need any passwords and usernames, I just plug in the cable , get an IP address, and I'm enjoying my internet connection. Well, not in Ubuntu. :)

---

### Post by chili555 on 2010-02-15
I would love to see the result of the IRQ issue I raised. Also I notice your kernel version is 2.6.28-11.42-generic, which corresponds, if I remember correctly, to Ubuntu 9.04. If you download and try the Live CD for the latest version, 9.10, I wonder if the ethernet driver works better.

I am beginning to be skeptical that the XP 'wake on' issue is our problem because your *ethtool* reports link=yes.

I am running low on ammunition.

---

### Post by evajulia on 2010-02-15
I will definitely try that BIOS method, there's only one problem, I don't really know how  to do that :) Which option to pick to see those IRQ lines? 

> If you download and try the Live CD for the latest version, 9.10, I wonder if the ethernet driver works better.


I doubt it, unfortunately. I have tried several Ubuntu versions (not the 9.10 though) and my problem was always the same: no internet...

> I am running low on ammunition.May I start giving up my hopes now ? :)

---

### Post by chili555 on 2010-02-15
> Which option to pick to see those IRQ lines? Highlight an IRQ line, press Enter and several choices will appear. Use the arrow key to select the one that closest approaches 'Auto Select' for every line and press Enter. Usually F10 will save and continue to boot.> May I start giving up my hopes now ?Oh, no! We haven't yet discussed replacing the ethernet card altogether or methods to use wireless!

---

### Post by chili555 on 2010-02-15
Let's see if the card will work with a static IP address instead of DHCP. While booted into XP, get all your network details, especially IP address and gateway. Boot into Ubuntu and do:```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 <ip_address> up
sudo route add default gw <gateway_address>
ping -c3 <gateway_address>
```Does the modem reply with ping returns?

FWIW, one of my desktop machines has:> 02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)It works perfectly with Ubuntu 9.10.

---

### Post by evajulia on 2010-02-16
I tried the BIOS method, and I must be really dumb as I couldn't find the IRQ options in my BIOS. I have and AMI BIOS, and I made some screenshots, hoping you could show me where and what to do :)
 I tried the tips you mentioned in your last post, but it did not work...when I entered the codes in the Terminal, I got the following: No such directory. I tried to set my connection in the network manager manually: I set my connection type to manual instead of DHCP and entered my IP, Gateway and Mask...but no success. Although it said Ethernet is connected, I could not open any page in FF and I couldn't ping anything either.


EDIT: I updated my Realtek driver and could set the option Wake On Lan option, - now REALLY :) - but the problem is still up: no internet on Ubuntu.

---

### Post by chili555 on 2010-02-16
> it said Ethernet is connected,Am I mistaken or is that a new development? When it says you are connected, please do:```
ifconfig
```Is an IP address showing?> when I entered the codes in the Terminal, I got the following: No such directory.I am guessing you meant for the first command. We found the NetworkManager command successfully in post #31. Please try my most recent commands again.> couldn't find the IRQ options in my BIOS.I couldn't either. I also searched the internet for IRQ settings in AMI BIOS and, as far as I can tell, some may not have it.

---

### Post by evajulia on 2010-02-17
My ifconfig when my ethernet is "connected" dhcp with address, but interestingly my maks and ip is not the same as what I had entered to the "routes" window.

```
Link encap:Ethernet  HWaddr 00:18:f3:ab:2b:3a  
          inet addr:169.254.5.206  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::218:f3ff:feab:2b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52368 (52.3 KB)  TX bytes:20858 (20.8 KB)
          Interrupt:20 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16448 (16.4 KB)  TX bytes:16448 (16.4 KB)
```

Here's my result for the ( got it work, the problem was that I left those < signs in the code) code you mentioned before:
```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 <ip_address> up
sudo route add default gw <gateway_address>
ping -c3 <gateway_address>
```
and my result:
```
PING 79.121.16.1 (79.121.16.1) 56(84) bytes of data.

--- 79.121.16.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms


ifconfig: eth0      Link encap:Ethernet  HWaddr 00:18:f3:ab:2b:3a  
          inet addr:79.121.17.86  Bcast:79.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::218:f3ff:feab:2b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18511 (18.5 KB)  TX bytes:11679 (11.6 KB)
          Interrupt:20 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:952 (952.0 B)  TX bytes:952 (952.0 B)

```

> some may not have it. 

Hah, it wouldn't be my laptop if it had it... :)

---

### Post by chili555 on 2010-02-17
> inet addr:169.254.5.206 A 169.254.x.x address is plugged in, more or less as a placeholder, when the system can't get a valid IP address, either static or DHCP, from the gateway/router/access point. 

Let's summarize. The card works in Windows perfectly, so we know it's not defective. I don't think Windows is leaving the card disabled, because it is recognized and link=yes. All the signs under ethtool look perfectly well, as far as I can see. It has grabbed a driver, 8139too, and created an interface, eth0. It won't work, either with Network Manager, nor, after NM is stopped, with either DHCP or static. It won't work with a variety of Linux Live CDs. (May I assume you have tried SUSE and Mandriva, or at least one non-Debian Live CD?).

I only have two thoughts left. First, you might double-check the settings in Windows that you referred to in your first post. Enable everything that looks likely with regard to your ethernet card. Second, consider a wireless access point.

This card, as in my desktop machine, is almost always, with the exception of the 8139cp and 8139too conflict, absolutely reliable out of the box in Linux.

I am completely mystified.

---

### Post by northd_tech on 2010-02-20
> **chili555 said:**
> 
This card, as in my desktop machine, is almost always, with the exception of the 8139cp and 8139too conflict, absolutely reliable out of the box in Linux.

I am completely mystified.

Well, if Eva can budget it- it sounds like it might be time to look for an ubuntu-compatible 802.11n USB wireless adapter then.

Just a thought- my wireless worked "out of the box" with PCLinux a long time ago (based on Mandriva, which evolved from Mandrake, which came from Red Hat, which... )- that might be worth a shot to download a LiveCD and try it out with her hardware:

[http://pclinuxos.com/?page_id=10](http://pclinuxos.com/?page_id=10)

I remember Linux Mint having basically the same problems as Ubuntu (in a green-colored sort of way) from my experience.  SUSE was pretty good (but I don't like their "corporate factor" very much).

edit:  It might be worth poking around this Linux/FreeBSD website a little:

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Dener on 2010-04-09
Hi I have the same rtl-8139cp problem. I used to have ubuntu 8.10 a year ago and it worked perfect from the os instalation. now with 9.10 I have the sabe problem as Eve.

---

### Post by decaff on 2010-09-14
Hi there  just installed my first Ubuntu Studio 10.04.  I have been using Windows for 20 years+ but I was always craving to use an open-source steady environment like Ubuntu.  Unfortunately so far no luck with both my wired and wireless adaptors. It's been a week now...   I've given up on my WL-727N wireless, but at least I must make the wired work!    It's a realtek card (integrated, as it's a laptop). I can't even install ethtool, when I try to to: sudo apt-get install ethtool   I get  E: couldn't find package ethtool Any help would be greatly appreciated :) decaff

---

### Post by cafeduranpty on 2011-02-18
If anyone is curious, I have this same network card and can confirm it works on Lucid 10.04 LTS without any configuring.

---

### Post by sforte on 2011-02-18
I'using ubuntu 10.10 and want to use this box as a ADSL router/ network sharing instead of use the Modem. I had the same problem trying to use a RTL8139D as a second network card. After try a lot of good suggestions I could solve my problem. I cant say you that this will solve your problem too because my system begin to work and I couldnt do it stop of work to redo. So this is what I believe makes my system work:
sudo rmmod 8139cp
sudo rmmod 8139too
sudo modprobe 8139too media=0x08

I'm not sure about the last line. I am a newbie. But I grab this "media=0x08" from my network README. There was a description:
media=
    10-half     0x01 
    10-full     0x02 
    100-half 0x04 
    100-full 0x08
But it was to be used in insmod not in modprobe. I dont know the difference between modprobe and insmod but I tried that command with modprobe as insmod wasnt able to find 8139too.
It worked to me even after reboots.

---

