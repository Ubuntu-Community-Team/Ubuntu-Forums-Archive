---
title: "Asus Eee PC 1000HA / 9.04 / Atheros AR242x"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by tomwilsonfl on 2009-06-18
I've searched all of the net and keep coming up with answers to this problem that are either outdated or not working. Hopefully someone can nail this down in this thread.

I recently installed Ubuntu 9.04 on my 1000HA because I was unhappy with Eeebuntu and heard 9.04 worked perfect on the Eee PC now.

Well everything works great, except the wireless.

After I installed Eeebuntu I remember having a wireless problem and I searched up and down, recompiled some modules and voila it worked perfect (after 8 hours of research and screwing around). I'm hoping there is an easier fix for this by now.

Basically the wireless connects without a problem, but the latency/packetloss is all over the place. Pings (even to local machines) go from 5ms to 5000ms constantly. Loading a full page in Firefox is painful.

Interestingly enough, it seems to be better when the machine is idle. When I leave the ping running and the machine sits idle, after waking up the screen and viewing the list of pings the majority of them seem ok. [Maybe a hint towards fixing this issue.]

I tried activating the alternative madwifi driver using the Hardware Drivers interface, but after rebooting my wireless simply did not recognize. So I went back to the ath5_pci driver.

Ok, enough jabber. Here's the specs as requested by the forum guidelines:

Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

wlan0     IEEE 802.11bg  ESSID:"tridium" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:CD:D4:37:EA  
          Bit Rate=1 Mb/s   Tx-Power=20 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B  
          Power Management:off
          Link Quality=62/100  Signal level:-60 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

twilson@twilson-laptop:~$ lsmod | grep "ath5k"
ath5k                 107008  0
mac80211              217208  1 ath5k
led_class              12036  1 ath5k
cfg80211               38032  2 ath5k,mac80211

twilson@twilson-laptop:~$ dmesg | grep "ath5k"
[   10.673653] ath5k_pci 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.673674] ath5k_pci 0000:01:00.0: setting latency timer to 64
[   10.673873] ath5k_pci 0000:01:00.0: registered as 'phy0'
[   10.862031] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[  151.340255] ath5k phy0: unsupported jumbo
[  232.845751] ath5k phy0: unsupported jumbo
[  435.871583] ath5k phy0: unsupported jumbo
[  592.980045] ath5k phy0: unsupported jumbo
[  709.976339] ath5k phy0: unsupported jumbo

  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:4e:79:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.111 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

wlan0     Scan completed :
          Cell 01 - Address: 00:23:CD:D4:37:EA
                    ESSID:"tridium"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/100  Signal level:-59 dBm  Noise level=-100 dBm
                    Encryption key:on
                    IE: Unknown: 00077472696469756D
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 07065A5720010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F020101000002A34000
                    IE: Unknown: DD1A00037F03010000000023CDD437EA0223CDD437EA64002C011D08
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000007365683db
                    Extra: Last beacon: 4ms ago

twilson@twilson-laptop:~$ uname -mr
2.6.28-11-generic i686

---

### Post by rac56 on 2009-06-20
The only thing I've found that works on my 1000HA is the Windows driver with ndiswrapper.

To install:

1.  Download the wireless driver from the Asus site.

2.  Create a folder where you would like to keep the driver and unpack it there.

3.  Using Synaptic, install ndisgtk and the dependencies it picks for you.

4.  Open a terminal window and enter the command "sudo ndisgtk".  A Wireless Network Drivers window will appear.

5.  Click the Install New Driver button.

6.  Navigate through the folders for the driver you downloaded to the ndis5x folder.  Select the file "net5211.inf" and then click Install.  Ignore the error that comes up about not being able to detect the hardware.

7.  Close ndisgkt and then restart the computer.

You should then be able to connect to the network.  I get full 54 Mb/s speed with no errors.  It occasionally misses connecting on the first try, but it works on a second attempt.

Good luck!

---

### Post by irishlyrucked on 2009-07-18
i can confirm that the wireless works after following the previous post's instructions.

---

### Post by Katalog on 2009-07-26
I can second that, worked for me as well. You may also want to blacklist the default ath5k module in /etc/modprobe.d/blacklist to be on the safe side and make sure that it isn't able to possibly come back and haunt you later.

EDIT: FWIW. I gave Eeebuntu a try and didn't have much luck with it either. Installing vanilla UNR 9.04 and eee-control worked out much better for both myself on the 1000HA and also for my wife on her 901.

---

### Post by teferra on 2009-07-31
on 901 installed ndiswraper and xp driver. But get the no hardware found message in windows divers window. ifconfig shows wlan0 and network manager tries to connect to the wep network though without success.is there any ubuntu driver i have to remove?

---

### Post by Katalog on 2009-07-31
> **teferra said:**
> on 901 installed ndiswraper and xp driver. But get the no hardware found message in windows divers window. ifconfig shows wlan0 and network manager tries to connect to the wep network though without success.is there any ubuntu driver i have to remove?

Just a quick question: Why are you having to use ndiswrapper on a 901? I have a 901 (or rather my wife does) and the RaLink 2860 wireless card worked just fine straight out of the box, and connects to our WEP without any problems (WPA/WPA2 don't work very well though), didn't have to install or remove drivers for it that I can recall. Does yours have a different card than the standard 901?

---

### Post by hetx on 2009-07-31
Installed eeebuntu on my friend's 1000HA EEEPC, downloaded the latest kernel deb package and installed it manually via USB disk. That did the trick for me, working wifi.

---

### Post by romanyiv on 2009-08-02
> **hetx said:**
> Installed eeebuntu on my friend's 1000HA EEEPC, downloaded the latest kernel deb package and installed it manually via USB disk. That did the trick for me, working wifi.

Could you give some more detail on what you did?   And can you verify that your wireless is working fine?  I have fought this issue for several months and the only way to get wireless to work  is ot use NDISWRAPPER.....the typical problem is you can't connect - or if you can you have very poor connectivity....

---

### Post by carloshiga on 2009-08-03
Here is what I did to get my Atheros AR242X working on my Eee PC 1000 HA:

Create a directory to save the driver:

```
mkdir madwifi
```

Then, download the driver here (you'll need a wired connection or you can download it using another computer and copy it to the madwifi directory):

[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

The madwifi-hal-0.10.5.6-current.tar.gz is the one that worked for me. Once you extracted the files in the .tar.gz file, enter in the directory extracted:

```
cd madwifi-hal-0.10.5.6-r4068-20090705/
```

Next, install the build-essential:

```
sudo apt-get install build-essential
```

Run the make script:

```
make
```

Install the driver:

```
sudo make install
```

Edit the file /etc/modules adding "ath_pci" (without the quotes) to its end. Finally, reboot your Eee PC.

---

### Post by Katalog on 2009-08-03
> **hetx said:**
> Installed eeebuntu on my friend's 1000HA EEEPC, downloaded the latest kernel deb package and installed it manually via USB disk. That did the trick for me, working wifi.


From what I've been reading the most recent kernels seem to have way better Atheros drivers. Makes me look forward to Karmic.

---

### Post by hetx on 2009-08-04
I've looked everywhere for the post with the kernel that makes it work, will just have to wait until my friend gets back (let's hope he kept the kernel deb!)

---

### Post by hetx on 2009-08-04
[COLOR=#CC0000]**[SIZE=3][/SIZE]**[/COLOR][FONT=Arial][SIZE=2][COLOR=#000000]linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb[/COLOR]
l[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]inux-headers-2.6.30-02063003-generic_2.6.30-02063003_i386.deb[/COLOR]
[COLOR=#CC0000]****[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]linux-image-2.6.30-02063003-generic_2.6.30-02063003_i386.deb

It's a bit like getting Karmic Koala innit? No guarantees that this is a good idea, it works for wireless but might not interact well with Jaunty. If you want to be sure, put in the extra effort and do the more complicated fix from the above post.
[/COLOR][/SIZE][/FONT]

---

### Post by aatyler on 2009-08-21
Hey there all,
 
I have the same eeePC and I plan on putting ubuntu 9.04 on it later this week, I was wondering, does the eeepc use (sorry, im new to linux and im not sure if this is the correct term) the device config/drivers /sys/devices/platform/asus-laptop  ??? I have the asus m50vm with the same brand of wireless and 
 
```
echo 1 > /sys/devices/platform/asus-laptop/wlan
```
 
as root worked like a charm...
 
 
Adam

---

### Post by bdash on 2009-10-02
Did anyone try Karmic on a 1000HA, to tell us if the wireless works out of the box without having to install drivers manually?

---

### Post by Katalog on 2009-10-04
> **bdash said:**
> Did anyone try Karmic on a 1000HA, to tell us if the wireless works out of the box without having to install drivers manually?

I've tried all the alphas and the current beta and it's worked fine so far without any manual configuration on my part (knock on wood). The most recent kernels seem to have resolved the issues with Atheros in the wireless stack because the Karmic UNR (and more recently Kubuntu Netbook on live USB, although it didn't work until Alpha 5, but that was because Kubuntu's network manager was acting up) alphas and most recent beta have detected my wireless card on first boot and found my access point right away. I can't speak for how well it will work with a router that has a more sophisticated security set up, but it works fine with my almost 5 year old Netgear router (I live more than a quarter mile from my nearest neighbor, so I'm pretty lazy about wireless security).

---

### Post by macabro22 on 2009-10-26
```
[24011.847733] ath5k phy0: unsupported jumbo
[24253.545379] ath5k phy0: unsupported jumbo
[24401.532626] ath5k phy0: unsupported jumbo
[24403.846784] ath5k phy0: unsupported jumbo
[24551.208284] ath5k phy0: unsupported jumbo
[24724.967800] ath5k phy0: unsupported jumbo
[24917.555155] ath5k phy0: unsupported jumbo
```

This bug is still alive in karmic!

---

### Post by James Little on 2010-01-20
This still seems to be a problem in the final release of v9.10 (UNR version). I have the new Eee PC 1005PE which has the Atheros AR2427 chip. Wifi does not work. I have built from the latest cutting edge source available at [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) and when I try to modprobe the driver I get the following error:

james@netbook:/lib/modules$ sudo modprobe ath5k
FATAL: Error inserting ath5k (/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
james@netbook:/lib/modules$ dmesg | tail
[ 5715.282448] ath5k: Unknown symbol ieee80211_stop_queue
[ 5715.282744] ath5k: disagrees about version of symbol ieee80211_stop_queues
[ 5715.282751] ath5k: Unknown symbol ieee80211_stop_queues
[ 5715.283212] ath5k: disagrees about version of symbol ieee80211_unregister_hw
[ 5715.283219] ath5k: Unknown symbol ieee80211_unregister_hw
[ 5715.283513] ath5k: disagrees about version of symbol ath_regd_init
[ 5715.283520] ath5k: Unknown symbol ath_regd_init
[ 5715.284483] ath5k: Unknown symbol ieee80211_beacon_get
[ 5715.285901] ath5k: disagrees about version of symbol ieee80211_rts_duration
[ 5715.285908] ath5k: Unknown symbol ieee80211_rts_duration


Does anyone have any ideas on how to fix? Thank you.

**UPDATE**
Modprobe now works after reconfiguring compilation, but device is still not seen (even after a reboot). Nothing seems to be in dmesg or lspci output.

---

### Post by Windy Peaks on 2010-02-07
I have tried everything to get the wifi working on My Daughters eee 1000ha. The first thing was that the wifi card was not even recognised, I tried your madwifi approach and it worked great. Thanks for that :)

But in order to get the wifi working I have to go to the hardware drivers screen and deactivate the athos driver then reactivate it.

My question to You is, if You had this problem how did You get around it. Did You write a Daemon process to start it for You or do You know another way around it ???

Thank You is advance for Your help.

Windy





> **carloshiga said:**
> Here is what I did to get my Atheros AR242X working on my Eee PC 1000 HA:

Create a directory to save the driver:

```
mkdir madwifi
```

Then, download the driver here (you'll need a wired connection or you can download it using another computer and copy it to the madwifi directory):

[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

The madwifi-hal-0.10.5.6-current.tar.gz is the one that worked for me. Once you extracted the files in the .tar.gz file, enter in the directory extracted:

```
cd madwifi-hal-0.10.5.6-r4068-20090705/
```

Next, install the build-essential:

```
sudo apt-get install build-essential
```

Run the make script:

```
make
```

Install the driver:

```
sudo make install
```

Edit the file /etc/modules adding "ath_pci" (without the quotes) to its end. Finally, reboot your Eee PC.

---

### Post by Windy Peaks on 2010-02-07
> **Windy Peaks said:**
> I have tried everything to get the wifi working on My Daughters eee 1000ha. The first thing was that the wifi card was not even recognised, I tried your madwifi approach and it worked great. Thanks for that :)

But in order to get the wifi working I have to go to the hardware drivers screen and deactivate the athos driver then reactivate it.

My question to You is, if You had this problem how did You get around it. Did You write a Daemon process to start it for You or do You know another way around it ???

Thank You is advance for Your help.

Windy

Sorry I forgot to mention that I have install netbuntu 9.10 on the ASUS EEE 1000HA, not the standard 9.04 Ubuntu.

---

### Post by khunter1 on 2010-04-08
> **James Little said:**
> This still seems to be a problem in the final release of v9.10 (UNR version). I have the new Eee PC 1005PE which has the Atheros AR2427 chip. Wifi does not work. I have built from the latest cutting edge source available at [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) and when I try to modprobe the driver I get the following error:

james@netbook:/lib/modules$ sudo modprobe ath5k
FATAL: Error inserting ath5k (/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
james@netbook:/lib/modules$ dmesg | tail
[ 5715.282448] ath5k: Unknown symbol ieee80211_stop_queue
[ 5715.282744] ath5k: disagrees about version of symbol ieee80211_stop_queues
[ 5715.282751] ath5k: Unknown symbol ieee80211_stop_queues
[ 5715.283212] ath5k: disagrees about version of symbol ieee80211_unregister_hw
[ 5715.283219] ath5k: Unknown symbol ieee80211_unregister_hw
[ 5715.283513] ath5k: disagrees about version of symbol ath_regd_init
[ 5715.283520] ath5k: Unknown symbol ath_regd_init
[ 5715.284483] ath5k: Unknown symbol ieee80211_beacon_get
[ 5715.285901] ath5k: disagrees about version of symbol ieee80211_rts_duration
[ 5715.285908] ath5k: Unknown symbol ieee80211_rts_duration


Does anyone have any ideas on how to fix? Thank you.

**UPDATE**
Modprobe now works after reconfiguring compilation, but device is still not seen (even after a reboot). Nothing seems to be in dmesg or lspci output.

Did you open a bug report?

I think this is the one:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/521967](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/521967)

---

### Post by James Little on 2010-04-08
The driver from bleeding edge now works, so don't have this problem now. Although the driver shipping with the  kernel in Lucid Beta1 still seems to be outdated, so compilation is necessary.

---

