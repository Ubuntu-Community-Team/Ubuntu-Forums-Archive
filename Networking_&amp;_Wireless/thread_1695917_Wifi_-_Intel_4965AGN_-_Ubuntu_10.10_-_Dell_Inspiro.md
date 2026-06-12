---
title: "Wifi - Intel 4965AGN - Ubuntu 10.10 - Dell Inspiron 1525"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by countwalkerj on 2011-02-26
Others have posted similar posts on this but I haven't found anything exactly the same as my situation. The main differences are that I am on a Dell Inspiron 1525 and my wireless networking does work for a little while after Ubuntu starts, but stops working after a few minutes of light-weight web surfing.

I recently installed Ubuntu 10.10 on my Dell Inspiron 1525 fresh from an iso download. I'm dual booting Windows 7 on the same machine. 

I have a Dell Optiplex GX620 desktop that I have put Ubuntu 10.10 on and the wireless is working great! I just plugged in a Belkin USB adapter and the wireless started working just fine. I figured the built-in wireless on my laptop would work just as well but now I see that lots of people seem to be having issues with this Intel wireless device.

Oh yeah, just as an aside, the wireless light blinks which is quite annoying but I don't care if the wireless networking works. I can live with that. The main problem is that it stops working after just a few minutes. As I mentioned, I have another machine that is using the wireless router with no problem and the wireless card on my Inspiron 1525 is working okay when I used Windows 7.

So, having said all that, here is the obligatory diagnostic information. I really appreciate any help that someone knowledgeable about this stuff can provide. Thanks for your time.


```
$ lspci -nn | grep 'Wireless'
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)

``````
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"SKY32429"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:AC:03:F0   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
$ lsmod | grep iwl
iwlagn                178948  0 
iwlcore               127415  1 iwlagn
mac80211              231959  2 iwlagn,iwlcore
cfg80211              144694  3 iwlagn,iwlcore,mac80211

``````
$ ls /etc/modprobe.d
alsa-base.conf          blacklist-firewire.conf     blacklist-oss.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist.conf          blacklist-modem.conf        intel-5300-iwlagn-disable11n.conf

``````
$ dmesg | grep iwl
[   19.312837] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   19.312842] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   19.318489] iwlagn 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.318529] iwlagn 0000:0b:00.0: setting latency timer to 64
[   19.318608] iwlagn 0000:0b:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   19.393476] iwlagn 0000:0b:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   19.393697] iwlagn 0000:0b:00.0: irq 45 for MSI/MSI-X
[   19.480487] iwlagn 0000:0b:00.0: loaded firmware version 228.61.2.24
[   19.498163] phy0: Selected rate control algorithm 'iwl-agn-rs'

```
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3f:ad:76
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:72:f6:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-25-generic firmware=228.61.2.24 ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:fe7fe000-fe7fffff

``````
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:AC:03:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"SKY32429"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca43f4c1bf
                    Extra: Last beacon: 520ms ago
                    IE: Unknown: 0008534B593332343239
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

``````

$ lsb_release -d
Description:    Ubuntu 10.10

$ uname -mr
2.6.35-25-generic i686

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...

Ignoring unknown interface wlan0=wlan0.     [ OK ]


```Oh yeah, I have also connected by a wired connection and gotten the latest updates but my wireless is still disconnecting after just a few minutes of web surfing.

Thanks again for taking the time to look at this.

---

### Post by ddr71m on 2011-02-26
hey,i am a beginner with ubuntu. i have installed..9.10 using an usb  stick on my dell inspiron 1525 laptop. i have a dual boot system with  ubuntu 9.10 and windowws 7.initially, my wireless was not detected....so  i tried installing some .deb files from POOL folder in the image of  ubuntu 9.10 cd as recommended in ubuntu forums as it had worked for  them.i installed the packages-
POOL>D>DKMS>dkms_2.1.0.1-0ubuntu1_all.deb
then POOL>RESTRICTED>B>BCMWL>bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
the i rebooted the sys.....but now the network manager..shows  no wireless options at all.
somebody do help..

---

### Post by countwalkerj on 2011-02-28
Just giving a little bump. 

Just to re-iterate, I'm dealing with Ubuntu 10.10. My wireless connection works after booting up but only lasts for a few minutes of light web surfing before being dropped. The connection speed also does not appear to be as quick as it should be. 

Additionally, I can disconnect and re-connect the wireless connection by clicking on the wireless icon at the top right-hand corner of my desktop. However, again it drops after a few minutes of surfing.

All details are in my original post. 

Please help!

Thanks

---

### Post by countwalkerj on 2011-03-04
Another bump.

I've also read some people talking about how a bad battery might be somehow related? Is there any truth in this? The interesting thing about this is that I do get a message when Ubuntu starts up telling me that the battery is bad and should be replaced. However, I just ignore it since I always keep my laptop plugged in. When I say always I mean 99.3% of the time.

Does anyone knowledgeable have ANYTHING to say on this topic?

For anyone who is NOT knowledgeable, please do not post anything about about how you are having the same problem on Ubuntu version 0.8 on a Timex Sinclair. I am sympathetic but it doesn't help me. Please start a new thread for that. Thanks.

---

### Post by chili555 on 2011-03-04
> **ddr71m said:**
> hey,i am a beginner with ubuntu. i have installed..9.10 using an usb  stick on my dell inspiron 1525 laptop. i have a dual boot system with  ubuntu 9.10 and windowws 7.initially, my wireless was not detected....so  i tried installing some .deb files from POOL folder in the image of  ubuntu 9.10 cd as recommended in ubuntu forums as it had worked for  them.i installed the packages-
POOL>D>DKMS>dkms_2.1.0.1-0ubuntu1_all.deb
then POOL>RESTRICTED>B>BCMWL>bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
the i rebooted the sys.....but now the network manager..shows  no wireless options at all.
somebody do help..Your question has nothing to do with the subject of this thread, except you also have a Dell 1525. I suggest you start a new thread and include:```
lspci -nn
```If you have an Intel 4965, follow along here. bcmwl-kernel-source is wrong for an Intel but correct for some Broadcoms.

---

### Post by chili555 on 2011-03-04
> Does anyone knowledgeable have ANYTHING to say on this topic?
I guess we'll find out!

The only things I see that are suspicious are:> wlan0     IEEE 802.11abg  ESSID:"SKY32429"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:AC:03:F0   
          [COLOR="Red"]Bit Rate=1 Mb/s[/COLOR]   Tx-Power=15 dBm   
Normally, the wireless card and router negotiate the highest rate that's reliable, which yours isn't. You might try forcing it higher:```
sudo iwconfig wlan0 rate 54M
```If that helps, we can write a change to one file and make it permanent, hopefully. I also see:> wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:AC:03:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    [COLOR="Red"]Quality=46/70[/COLOR]  Signal level=-64 dBm  
                    Encryption key:on
That's a bit low, but it ought to work. In several wireless devices I've used, there is a provision to increase the broadcast strength. Is yours at 100%? Please see attached.

Last, I see that your network is on channel 6, like 95% of your neighbors, cordless phones, microwaves, etc. I have the best luck on channel 11.> on Ubuntu version 0.8 on a Timex Sinclair.ROFL. +100

---

### Post by countwalkerj on 2011-03-07
Thanks a lot for the post Chili. I did some tinkering on the weekend but it's still plaguing me unfortunately. I've decided not to lose any more sleep on it. When I want to use Ubuntu on my laptop I'll just make sure I have a wired connection. I use Windows on the laptop most of the time anyway and then I have Ubuntu on my desktop where the wireless is working well so this is just a minor annoyance in the large scheme of things. 

Thanks for your time on my query. Glad you got the Timex Sinclair reference! ha ha ha

It would be good to know if anyone out there is using a Dell Inspiron 1525 with an Intel wireless card and NOT having problems. Then again, what are the chances that anyone who is not having a problem will be reading this forum? Sigh... Oh well.

Cheers

---

### Post by durale on 2011-03-09
Same issue. I can t believe that no one ever got working the wireless card on ubuntu.

Is there a chance to point towards the right driver or module so we fully enjoy ubuntu

I haven t found any solution on Internet so far ... got stuck!

regards

alex

---

### Post by steaksauce on 2011-03-09
I might be stepping out ona limb here, and I didn't buy it the first time I read anything on it, but it may be IPv6. It may need to be disabled. The easiest way I know how to is through firefox. At the top type about:config in the URL and click "I'll be careful, I promise!" Then type IPv6 in the filter and set the value to true. I have a 1525 as well, but mine came with 4312 and works fine. I had to disable IPv6 because my Internet got realllllyyyyy slow and I seen where your connection was 1Mbps speeds so I thought this may help ;)_ _

---

