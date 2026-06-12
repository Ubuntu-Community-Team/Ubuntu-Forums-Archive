---
title: "ubuntu 10.10 won't connect to wlan"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by incompetent on 2010-10-07
the router is a linksys wrt54gs2 v1

for some reason, my wireless nic won't connect to the router. It will find it, but it won't connect.this has happened to every wireless network i've tried to join. ethernet rj-45 works fine(wired)

---

### Post by ragvaiv on 2010-10-09
> **incompetent said:**
> the router is a linksys wrt54gs2 v1

for some reason, my wireless nic won't connect to the router. It will find it, but it won't connect.this has happened to every wireless network i've tried to join. ethernet rj-45 works fine(wired)

I have the same problem (on a d-link router).
Trying with WEP or WPA, Open or Shared Key, 40 or 128 Bit, Hidden and Not Hidden SSID.
Everything i did, won't works.
The same Net is accessible using Windows XP or Ubuntu 10.04.

---

### Post by Erkunder on 2010-10-11
Same issue using an Intel 4965AGN and a D-Link DSL-2741 router, WPA2-PSK encryption. WLAN connection worked fine with Ubuntu 10.04 and is still working as usual with Win XP. Ubuntu 10.10 is able to see the network but cannot connect, asking for the WLAN Password after some time trying to connect. I am very sure I entered the correct password each time I tried to connect.

Subsequent entry: Here are my wireless specifications. Maybe they are helpful for solving this problem, though the amount of similar posts suggests that this is not a setup specific problem.

1 ) Machine Brand and Model (PC/Laptop): Bullman Laptop

2 ) Wireless Brand, Model and Wireless Chipset:
```
$ lspci
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

3 ) check interface:
```
$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"somename"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

4 ) Check for modules:
```
$ lsmod
Module                  Size  Used by
iwlagn                178948  0 
iwlcore               127415  1 iwlagn
intel_agp              26360  0 
mac80211              231541  2 iwlagn,iwlcore
agpgart                32011  3 ttm,drm,intel_agp
cfg80211              144470  3 iwlagn,iwlcore,mac80211
```

5 ) Kernel boot messages
```
$ dmesg
[   17.534817] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.534819] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   17.534985] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.535043] iwlagn 0000:0c:00.0: setting latency timer to 64
[   17.535173] iwlagn 0000:0c:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   17.580317] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   17.581026] iwlagn 0000:0c:00.0: irq 47 for MSI/MSI-X
[   17.990124] iwlagn 0000:0c:00.0: loaded firmware version 228.61.2.24
[   19.115524] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.717592] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.058831] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   40.063549] wlan0: authenticated
[   40.063566] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   40.087182] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   40.087185] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   40.087196] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
[   52.290409] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   52.296109] wlan0: authenticated
[   52.296169] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   52.300133] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   52.300139] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   52.300158] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
[   64.488867] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   64.492353] wlan0: authenticated
[   64.492370] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   64.504212] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   64.504215] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   64.504227] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
[   76.702278] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   76.706496] wlan0: authenticated
[   76.706514] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   76.709086] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   76.709092] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   76.709111] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
[   88.941391] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   88.944631] wlan0: authenticated
[   88.944679] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   88.953153] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   88.953162] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   88.953230] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
```

6 ) Network configuration
```
$ sudo lshw -C network
[   17.534817] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.534819] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   17.534985] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.535043] iwlagn 0000:0c:00.0: setting latency timer to 64
[   17.535173] iwlagn 0000:0c:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   17.580317] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   17.581026] iwlagn 0000:0c:00.0: irq 47 for MSI/MSI-X
[   17.990124] iwlagn 0000:0c:00.0: loaded firmware version 228.61.2.24
[   19.115524] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.717592] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.058831] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   40.063549] wlan0: authenticated
[   40.063566] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   40.087182] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   40.087185] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   40.087196] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
[   52.290409] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   52.296109] wlan0: authenticated
[   52.296169] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   52.300133] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   52.300139] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   52.300158] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
[   64.488867] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   64.492353] wlan0: authenticated
[   64.492370] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   64.504212] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   64.504215] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   64.504227] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
[   76.702278] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   76.706496] wlan0: authenticated
[   76.706514] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   76.709086] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   76.709092] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   76.709111] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
[   88.941391] wlan0: authenticate with 00:24:01:3f:7a:ba (try 1)
[   88.944631] wlan0: authenticated
[   88.944679] wlan0: associate with 00:24:01:3f:7a:ba (try 1)
[   88.953153] wlan0: RX AssocResp from 00:24:01:3f:7a:ba (capab=0x411 status=18 aid=0)
[   88.953162] wlan0: 00:24:01:3f:7a:ba denied association (code=18)
[   88.953230] wlan0: deauthenticating from 00:24:01:3f:7a:ba by local choice (reason=3)
```

7 ) Scan for networks:
```
$ iwlist scan
wlan0     No scan results
```

8 ) Ubuntu Version: 
```
$ lsb_release -d
Description:    Ubuntu 10.10
```

9 ) Kernel/architecture (including 32 vs. 64 bit): 
```
$ uname -mr
2.6.35-22-generic i686
```

10 ) Restarting the network:
```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
```

---

### Post by fight2survive on 2010-10-11
i'm having the same problem. it detects my wireless network, tries to connect, but fails everytime and tells me the password is wrong. i am 100% sure the password is right and that the wireless router is properly working (i am using it right now on the same computer via windows 7 dual boot)...
help!

---

### Post by satismo on 2010-10-13
this is happening to me as well on my samsung N130
my neighbors' networks show up as well as my own
connections will not authenticate, keeps requesting the key


dmesg tells me this:
==>ieee80211_authentication_req():auth->algorithm is 0
Linking with STRJ4,channel:1 qos:1, myHT:1, networkHT:0
rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0,37

Update -- [Shift]ing into the Grub menu, and choosing previous kernel allowed me to connect.

---

### Post by etrem on 2010-10-13
Hey I was having the same problem after upgrading to 10.10 from 10.04. I just booted up choosing an older kernel (2.6.32-24-generic) from the grub boot menu and my wireless card seems to be working properly again.

---

### Post by s3r8i0 on 2010-10-13
> **fight2survive said:**
> i'm having the same problem. it detects my wireless network, tries to connect, but fails everytime and tells me the password is wrong. i am 100% sure the password is right and that the wireless router is properly working (i am using it right now on the same computer via windows 7 dual boot)...
help!

This happens to me too. My RTL8187SE Wireless LAN Controller stop working after a day of the Maverick instalation. I do remedy this, reinstalling the system(dumb) and now i'll do not update until have a fix in repository.

---

### Post by thingy87654321 on 2010-10-13
Happens to me too, on a new, fresh install of 10.10, i waited for this release, now im upset...because i dont want to tether my desktop with my laptop like i had to do before i got a usb wifi adapter... hopefully someone finds a fix NOW!!! please

---

### Post by fight2survive on 2010-10-13
> **satismo said:**
> this is happening to me as well on my samsung N130
my neighbors' networks show up as well as my own
connections will not authenticate, keeps requesting the key


dmesg tells me this:
==>ieee80211_authentication_req():auth->algorithm is 0
Linking with STRJ4,channel:1 qos:1, myHT:1, networkHT:0
rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0,37

Update -- [Shift]ing into the Grub menu, and choosing previous kernel allowed me to connect.

i'm using a samsung n130 as well. this computer uses the realtek rtl8192 network card. on 10.4 you had to install the driver manually to make it work, i tried that again but this time it doesn't make it work...

---

### Post by mjac on 2010-10-14
Ubuntu 10.10 has faulty wireless after upgrading Asus EEE PC 901 and also after doing a fresh install on a Asus EEE PC 1000. Any ideas how to solve this? The new interface is reasonable but I wasn't expecting such a regression in important features...

---

### Post by stan5001 on 2010-10-14
I had this; discoverd that if I brought the laptop closer to the router (DG834v5) it would connect.  Someone recommended changing the channel and that has worked.

Still a crappy workaround and it should be fixed.  Router channel setting was to "auto" which meant channel 13.

Toshiba A120 with wifi iwl3945

---

### Post by gerk on 2010-10-14
I have the same problem after upgrading from 10.04 to 10.10.
Notebook: Asus A7sn, wlan = 802.11n. Connecting at 54 mbps succeeds, connecting at N speed (5 GHz radio) fails.

Syslog for successful (10.04) wlan lists:

kernel: [   58.512090] wlan0: deauthenticating from 00:23:69:1a:9c:34 by local choice (reason=3)
kernel: [   58.512126] wlan0: direct probe to AP 00:23:69:1a:9c:34 (try 1)
kernel: [   58.513403] wlan0: direct probe responded
kernel: [   58.513406] wlan0: authenticate with AP 00:23:69:1a:9c:34 (try 1)
kernel: [   58.514693] wlan0: authenticated
kernel: [   58.514705] wlan0: associate with AP 00:23:69:1a:9c:34 (try 1)
kernel: [   58.516111] wlan0: RX AssocResp from 00:23:69:1a:9c:34 (capab=0x11 status=0 aid=1)
kernel: [   58.516113] wlan0: associated
kernel: [  184.674606] iwlagn 0000:03:00.0: iwl_tx_agg_start on ra = 00:23:69:1a:9c:34 tid = 0

syslog for failing 10.10 lists (and this is repeated many times):

kernel: [   64.834524] wlan0: authenticate with 00:23:69:1a:9c:34 (try 1)
kernel: [   64.835628] wlan0: authenticated
kernel: [   64.835645] wlan0: associate with 00:23:69:1a:9c:34 (try 1)
kernel: [   64.837052] wlan0: RX AssocResp from 00:23:69:1a:9c:34 (capab=0x11 status=18 aid=0)
kernel: [   64.837055] wlan0: 00:23:69:1a:9c:34 denied association (code=18)
kernel: [   64.837067] wlan0: deauthenticating from 00:23:69:1a:9c:34 by local choice (reason=3)

Looks like the RX AssocResp is different with status and aid.

---

### Post by MilkeySUFC on 2010-10-15
I seem to have a similar problem to Gerk on my Samsung Q45 (Intel 4965agn) that I can connect to the 802.11g network but not to the 802.11n network.

It finds the network but will not connect - I can 100% confirm the password is correct. It was working on the 10.10RC but the upgrade after full 10.10 release does not work. Nor does full install of 10.10 either.

Router has 802.11g on 2.4GHz, 802.11n on 5GHz.

Milkey

---

### Post by alopinho on 2010-10-15
Hi, I had similar issues with my Hama 54mpbs b/g USB 2.0 wireless device after installing 10.10. Network manager found all SSIDs but failed to connect after entering the Passphrase. In my case, the reason was a driver conflict. I solved it after reading this thread (for those of you who understand German - maybe there's someone around with the ability to translate it ;) ) [http://forum.ubuntuusers.de/topic/funknetzwerk-laesst-sich-nicht-aktivieren-1/](http://forum.ubuntuusers.de/topic/funknetzwerk-laesst-sich-nicht-aktivieren-1/) and doing the following:

```

sudo modprobe -rf rt2800usb
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
sudo depmod
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo service network-manager restart

```It worked after restarting my system.

Afaik I unloaded the drived that caused the trouble. :roll: Just a hint, but I hope it is helpful.

---

### Post by Janghou on 2010-10-17
Can't connect to WIFI-N, only G on my Acer 1810TZ
Intel Wireless N 1000

~$ iwconfig wlan0 
wlan0     IEEE 802.11bg  ESSID:off/any 

Found this for 10.10:

**802.11n support** for the iwlagn driver has been **temporarily disabled.** Intel is actively working to get this properly fixed up in the firmware. This workaround should be reverted once updated firmware is available. (630748)

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

---

### Post by madap on 2010-10-20
I had this problem too. 
Dual boot, Windows 7 and fresh install of Ubuntu 10.10
Would not take my password despite knowing for a fact it was correct. 
After beating around the bush for a while, all it took was to change the SSID of the network an try again.

However I am now having 2 strange issues:
1- The WLAN light is blinking on my laptop. This didn't use to happen at all. I'm looking into this but it's a minor annoyance.

2- This is a bit major, my WLAN speed is really, really slow, compared to what it should be. The Network properties for the wlan0 say the connection is 2 mbit. In Windows it's 36. I am suspecting a bad driver here, which is weird because if my memory doesn't fail me, when I tried the Ubuntu live CD, it worked properly.
My wlan device is Intel Corporation PRO/Wireless 4965 AG. 

Any suggestions/further testing?

---

### Post by julianof on 2010-10-20
I am having the same issue on my Acer 5740G laptop with an Atheros 928X Wireless adapter.

It used to work great on Ubuntu 10.04. I think i'll be downgrading soon.. What bothers me is that I can't connect even on the older kernel installed on my machine (2.6.32-25-generic-pae)

This is a bummer, since I use Linux quite a lot for my research.

I hope this gets fixed soon!

---

### Post by jarmore on 2010-10-20
Could not connect ... found it but pw was rejected. My stupidity ... I had rebooted my Linksys, ISP modem and VOIP on many occasions. Also had another power adaptor there, not sure what for. I had the wrong power adaptor (incorrect input DC) into the Linksys. Lucky didn't fry it. Once the correct power to Linksys .... worked! Like I said ... my stupidty. Long shot but check it out.

---

### Post by eynestyne on 2010-10-20
I thought i was the only one who think 10.10 has wifi issues. now i kno i'm not crazy.

---

### Post by puca mor on 2010-10-21
Same problem for me on my Samsung N150. 
Upgraded to 10.10 - now the wireless finds the networks - but will not connect, asks for the pass repeatedly etc..

Interestingly the wireless was working on the second day after upgrade... it didn't work after upgrade, and it stopped working again. 

Is the solution going to be downgrading? 
:confused:

---

### Post by luisc80 on 2010-10-21
having the same problem with connection to n only mode in my wireless network and for some reason everything seems to be slower in 10.10  i have a dell insprion 1525 with intel 5300 mini pci with wrt610n router:

0b:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
    Subsystem: Intel Corporation Device 1001
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fe7fe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

the only way to connect to my wireless network is to log into my router and change the wireless mode in either 2.4/5 ghz to mixed mode, or gn for 2.4 ghz and mixed a, or an in 5 ghz.  in either case the wireless rate is alway 54 M/ps.  patiently waiting for a fix.  thanks i love ubuntu though...:P

---

### Post by ajmatson on 2010-10-21
I had the same issue after upgrading. As mentioned before it seems to be an issue with the latest kernel. I just use the previous kernel until a fix is done :)

---

### Post by eynestyne on 2010-10-22
> **ajmatson said:**
> I had the same issue after upgrading. As mentioned before it seems to be an issue with the latest kernel. I just use the previous kernel until a fix is done :)

How did you get this done? I installed 10.10 and tried to install an earlier kernel but it did not work for me.. I'm a newbie to linux

---

### Post by SatishP on 2010-10-25
> **ajmatson said:**
> I had the same issue after upgrading. As mentioned before it seems to be an issue with the latest kernel. I just use the previous kernel until a fix is done :)

Thanks!! Choosing an earlier kernel worked for me. Awaiting fix ...

---

### Post by baldy4eva on 2010-10-25
Getting the same thing on an HP G60. Network Manager is not showing my network... Windows machines working fine. I did notice that Network Manager is not showing the MAC address of my Atheros card when i tried to edit the auto connect.

---

### Post by Peter09 on 2010-10-30
Same problem on my Samsung N150 - any time scale for a fix for this?

---

### Post by plasma-engineer on 2010-11-01
I have a similar problem but with a small extra clue.  My laptop is a Zoostorm 8227DMP 64 bit dual core machine with Intel Corporation PRO/Wireless 4965 AG or AGN.

I installed the 64-bit version of 10.10 last week and the connection to my Linksys WAG160N (horrid unstable thing that it is!) via WPA works fine.  However, trying to connect to the WEP network at work does not work.  As everyone else is reporting here, I can see the network name but it will not accept the password and give me a connection.  (The network is working as I was able to connect from another machine with 10.04 NBR running, and the password is so simple that even I cannot get it wrong.) 

I'm not an Ubuntu expert, but I have been using it since 7.10.  I keep trying to make a clean break from Windows but . . . can't quite bring myself to do it!

---

### Post by Peter09 on 2010-11-02
I have discovered that for the Samsung n150 which has a RTL819XE card there is a kernel problem which means that the card will not connect using the latest kernel.
 
By going into the grub menu (hold shift while booting) and selecting the earlier kernel to boot from I can get a connection - although the card will not survive a suspend/resume cycle.
 
I am trying to find whats happening about a fix - but no information so far.

---

### Post by gabriel403 on 2010-11-02
> **Peter09 said:**
> I have discovered that for the Samsung n150 which has a RTL819XE card there is a kernel problem which means that the card will not connect using the latest kernel.
 
By going into the grub menu (hold shift while booting) and selecting the earlier kernel to boot from I can get a connection - although the card will not survive a suspend/resume cycle.
 
I am trying to find whats happening about a fix - but no information so far.

Trouble is for those of us who installed 10.10 fresh we cant select an earlier kernel, is there someway we can add one?

---

### Post by Peter09 on 2010-11-02
bless someones cotton socks - just picking up an upgrade for my N150 as I type which involves a new kernel and a new driver - fingers crossed for a solution.

---

### Post by grahammechanical on 2010-11-02
I do not have any networking problems with 10.10. Am I forbidden to post to this thread?

It started out as a request for help and it has become a survey for those with networking problems. How can anyone give advice when so many are talking all at once. Who am I being asked to give help to? 

I saw this thread days ago and I left it straight away. It seemed a mess. I hope things get sorted out. If you find something that works for you, then share it with some else when they are asking for help.

regards.

---

### Post by Peter09 on 2010-11-03
Well after the upgrade of last night which involved a new kernel and driver I now have wireless networking on my Samsung n150, I hope others have also found this resolution worked for  them.
 
Now to get the regression involving recovery from suspend sorted.

---

### Post by Peter09 on 2010-11-05
Well may have been a bit hasty on this. Yes I can now connect to the internet and once established it all works OK, but dammit, sometimes it will just refuse to connect and takes a couple of power cycles (3-4) before it works. Just keeps asking for the password. Obviously the update did not fully resolve the issue.
 
So on my Samsung N150 current regressions are
 
1 Wireless is still flakey
2 Resume from suspend = dead (or at least unresponsive)
 
 
:(

---

### Post by gabriel403 on 2010-11-07
> **Peter09 said:**
> Well may have been a bit hasty on this. Yes I can now connect to the internet and once established it all works OK, but dammit, sometimes it will just refuse to connect and takes a couple of power cycles (3-4) before it works. Just keeps asking for the password. Obviously the update did not fully resolve the issue.
 
So on my Samsung N150 current regressions are
 
1 Wireless is still flakey
2 Resume from suspend = dead (or at least unresponsive)
 
 
:(
I went back to lucid, my wireless works lovely now. It's just a shame that I'm now subject to a kernel scheduler bug which increases wakeups-from-idle :/

---

### Post by sukharevd on 2010-11-10
I had a little bit similar problem. Maybe this:[ http://ubuntuforums.org/showpost.php?p=10099497&postcount=5]("http://ubuntuforums.org/showpost.php?p=10099497&postcount=5") can help you.

---

### Post by plasma-engineer on 2010-11-11
I'm almost embarrassed to say that I have discovered the best possible solution to the problem I referred to above.  I found that using the correct (new) password was a great deal more effective when trying to connect to the WEP network at work.  Ubuntu 10.10 networking works really well for me now, both at home and at work!

---

### Post by iradi8 on 2010-11-20
I to have now experienced this same issue. Just upgraded from 10.04 to 10.10 and wireless stopped working. I also had an issue with initramfs causing issues with modules.dep, but I fixed that here <http://ubuntuforums.org/showthread.php?t=1587411>. The wireless issue though peeves me off. Booting into the old kernel worked for getting me back online. What I am wondering is, if it looks like a driver conflict, how do I determine which one so that I can try blacklisting? Does anyone have any thoughts on that?

---

### Post by elias.alberto on 2010-11-22
I run Ubuntu 10.04 in a Dell inspiron 1525 with wireless card Broadcom BCM4312. Until I installed Quicktime into Wine, it was working normally using driver "Broadcom B43 wireless driver" which is licensed as open (and seems to be made using fwcutter). 
I installed Wine, then installed Rosetta Stone in Wine, and THEN wirelessly donwloaded latest version of quicktime from apple's website and installed it in Wine. Only noticed wifi wasn't working when I logged back to my user, because it was asking me for WPA2 key. The wpa key was right, but it won't connect. I've searched for network configurations under wine, but it won't show me any. Another point I find intriguing is none of those programs (quicktime and rosetta stone) shows up when I log as an user other than that who installed the program, so I think this shouldn't affect the behavior of the system for those users.
Restarted the laptop many times, tried switching the wifi on and off sometimes, tried another proprietary broadcom driver, tried to connect to another router which has a chipset from other brand, powercycled my routers... and none of this would work.  I'm still able to connect via ethernet cable, though.
I have a good knowledge about Windows, but decided to give ubuntu a try less than 2 months ago. This is the first time I'm having a issue I can't solve quickly using the help of the internet. I have no idea how to manage processes in linux, but under the System Monitor I haven't found processes named sugestively as wine or quicktime; the closest name I could find is wnck-applet.  I don't really know how to work my way through problems in ubuntu yet, so I would appreciate some advice.

Edit: tried to uninstall quicktime. It won't get uninstalled at all, so I pulled the plug for wine and uninstalled the whole wine. Rebooted the pc and it told me it should scan my HDD for errors (???) and even after that, I'm still not able to connect to my wifi, Symptom is the same: after a lot of waiting for it to connect, it drops me a dialog asking for the correct password.

Edit 2: Removed the driver, rebooted, added the driver again and rebooted again. Now it seems to be working normally again. I'm even afraid of trying to reinstall Wine, though. Guess I'll give up learning german, unless someone knows how to make Wine work properly with quicktime.

---

### Post by gabriel403 on 2010-11-25
Not really similar to the problems in the rest of this thread dude, perhaps start a new thread rather clogging up this one, wrong ubuntu version for a start

---

### Post by erkerb on 2010-11-26
My netbook has a Dual-Band card [Intel Advanced N 6200], and i can connect router(s) with 2.4GHz radio but not the 5GHz radio. I had no issues with 9.10.

---

### Post by NexusN on 2010-12-15
Sad to see it is ubuntu 10.10 to disable the n function, it is quite important to me who BT crazily.........

I felt strange to see the speed is limited to 2 MB/s........i see now.
Hope to see the fix soon:popcorn:

---

### Post by Gyoja on 2010-12-18
i have a broadcom 4311 wireless card on an HP pavillion dv9000. like many here i had some issues when upgrading to 10.10. wireless stopped working and i got a message that the password was incorrect when it wasn't. for me the solution was pretty simple. i use Wicd as my network manager. i opened Wicd -> preferences -> advanced settings. here there is a drop down to select WPA Supplicant (i use WPA-2 encryption on my router). i switched from the default Wext driver to the nl80211 driver and presto - connection problem solved. hopefully this helps

---

### Post by cray0rb on 2010-12-18
and for those of us using WEP, still no solution?

---

### Post by scarleo on 2010-12-18
I think 10.10 came with some power management features for the NIC which many NICs seem to have a lot of trouble with, at least my Broadcom did. I used to have a lot of the issues reported in this thread with slow internet or wouldn't connect to WLAN.

If your NIC is being power maneged doing 'iwconfig' would show 'PowerManagement:All packets accepted' or something similar. When in this state my network was really slow. However, if you turn this PowerManagement off all was back to normal. I'm not saying this is your problem, but might be worth a shot. To turn PowerManagement off just do:
'sudo iwconfig wlan0 power off', of course change wlan0 to whatever your actual connection is (like eth0, eth1 or whatever).

---

### Post by cray0rb on 2010-12-18
iwconfig is showing Power Management Off. Still no luck getting connected stably

---

### Post by ionplay on 2011-01-10
Similar to everyone else in this thread - minus a few tangential posts

I have installed 10.10 on my laptop and experiencing unexpected and uncommon wifi connection issues
lsb_release -d
Description:    Ubuntu 10.10
uname -mr
2.6.35-24-generic-pae i686

I am using an ASUS X72D laptop
with a AR9285 Wireless Network Adapter

and basically as I read this thread, the solution is to downgrade to 10.04, and/or to downgrade just the kernel
but does anyone know if there is a way to isolate what changed in the kernel to cause this problem in the first place???
who is working to correct this problem and how do we help??


```

sudo lshw -C network

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:fa:5e:a5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=2.6.35-24-generic-pae firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fea00000-fea0ffff

```
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``````

lspci | grep Wireless
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```
```

lsmod | grep ath
ath9k                  89076  0 
ath9k_common            5982  1 ath9k
ath9k_hw              292297  2 ath9k,ath9k_common
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
led_class               2633  2 ath9k,asus_laptop

``````

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:44:0C:4B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"hemlockadventure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006ba5bf4d183
                    Extra: Last beacon: 14760ms ago
                    IE: Unknown: 001068656D6C6F636B616476656E74757265
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F4000000

``````

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
I have done a fresh install of 10.10, and I have only installed the  default updates, The only additional package outside of default 10.10 I  installed was the WICD packages.

Is it possible there is a driver conflict for wireless by default which  would explain why so many users are experiencing the same problem.  And I  would wager that for each post in this thread there are a hundred more  in the same boat but unable to find this thread.

---

### Post by ionplay on 2011-01-10
the other thing I would add that I have seen in my logfiles and in the logs others have posted on this matter from
syslog
and
messages

 kernel: [31926.193065] ADDRCONF(NETDEV_UP): wlan0: link is not ready

and I am not sure how to make it ready when all the commands above appear correctly

---

### Post by oddious on 2011-02-21
> It will find it, but it won't connect.this has happened to every wireless network i've tried to join. ethernet rj-45 works fine(wired)

Had a quite similar problem on ubuntu 9.10

this:

```
sudo aptitude install wpasupplicant
```

worked

---

### Post by ionplay on 2011-02-21
I am on 10.10
still no wlan love - using external D-Link wifi adapter until I figure out how to use built-in wifi on laptop


```

K72Dr:~$ sudo aptitude install wpasupplicant
sudo: aptitude: command not found

K72Dr:~$ sudo apt-get install aptitude
Reading package lists... Done

K72Dr:~$ sudo aptitude install wpasupplicant
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.                                         
K72Dr:~$ 

```

no fireworks
no love
still using D-Link
:(

---

### Post by richwales on 2011-04-09
I'm seeing a similar (?) problem with 10.10 on a Dell Latitude D620.  This machine has a builtin Intel 3945ABG wireless adapter, and Ubuntu is using the iwl3945 driver.

I can connect just fine to 802.11g access points (at work, or at my mother's home).  And I can connect just fine (in 802.11a mode) to my Netgear WNDR3300 access point (with DD-WRT firmware) at home, **provided** I configure the access point's 5-GHz radio to "A-only" mode.

However, in hopes of enabling 802.11n capability at home, I tried last night to reconfigure my Netgear's 5-GHz radio to "AN-only" mode (using a wide, 40-MHz channel) — without making any configuration changes on my Ubuntu laptop — and after I did that, the laptop was unable to connect at all.  The logs showed an endless repetition of messages like the following:

[FONT="Lucida Console"]Apr  9 00:20:44 rde-richw-2 NetworkManager[1321]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 00:20:44 rde-richw-2 kernel: [168861.354918] wlan0: authenticate with 00:1f:33:b6:cd:82 (try 1) 
Apr  9 00:20:44 rde-richw-2 kernel: [168861.355625] wlan0: authenticated
Apr  9 00:20:44 rde-richw-2 kernel: [168861.355669] wlan0: associate with 00:1f:33:b6:cd:82 (try 1) 
Apr  9 00:20:44 rde-richw-2 kernel: [168861.357320] wlan0: RX AssocResp from 00:1f:33:b6:cd:82 (capab=0x11 status=18 aid=0)
Apr  9 00:20:44 rde-richw-2 kernel: [168861.357328] wlan0: 00:1f:33:b6:cd:82 denied association (code=18****)
Apr  9 00:20:44 rde-richw-2 kernel: [168861.357359] wlan0: deauthenticating from 00:1f:33:b6:cd:82 by local choice (reason=3)
Apr  9 00:20:54 rde-richw-2 NetworkManager[1321]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 00:20:54 rde-richw-2 NetworkManager[1321]: <info> (wlan0): supplicant connection state:  disconnected -> scanning[/FONT]

Note the [FONT="Lucida Console"]denied association (code=18****)[/FONT] error, similar to what other people have reported seeing.

My wife's Windows 7 machine, with a Linksys AE1000 dual-band wireless-N adapter, can connect to the AP without difficulty while it's in either "A-only" or "AN-only" mode.  And when I reconfigured my AP back to "A-only" mode, my laptop was once again able to connect to it.

Since my wife's computer was able to connect just fine in all cases, I'm assuming the problem is most likely a bug in the Ubuntu code (or possibly a failing in the laptop's Intel wireless adapter), and **not** a problem in the Netgear WNDR3300 access point or the DD-WRT firmware.

This isn't a horrible showstopper problem for me, since I **can** connect — but I'd like to find a fix if possible, since the problem is preventing me from upgrading my home network for possible future 802.11n capability.

As I said, this problem appears at first glance to be similar, but please accept my apologies if it turns out to be something completely different that belongs in a new thread.

---

### Post by richwales on 2011-04-15
I've reported my version of this problem as Ubuntu bug #759051 ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/759051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/759051)).

---

