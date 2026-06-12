---
title: "WUSB600N unable to connect despite able to see networks!"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by badbob32 on 2011-01-03
Hi,

I'm a newbie, and I've managed to install my WUSB600N on 10.10 (which was NOT easy!!) and I can see all my local wireless networks, but I can't connect - it attempts to connect then disconnects after what I guess is timing out.

I know that you can place these cards in broadcast mode (I think), where you can see networks but not connect. Considering that to get this card working I had to attempt about four different sets of instructions to get this far, could I have placed the card in a broadcast mode?  

I've been at this for about three days, and unless I go out an buy another network card (I'm currently connected using it through windows) then I'm going to have to give up on Linux, which I really don't want to :-(

Any help would be really appreciated.

Thanks

---

### Post by badbob32 on 2011-01-03
Here's the sys data:

Using a PC - Asus Motherboard

Wireless Device:

Bus 001 Device 002: ID 1737:0079 Linksys WUSB600N Wireless-N USB Network Adapter with Dual-Band ver. 2


ifconfig:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8544 (8.5 KB)  TX bytes:8544 (8.5 KB)

ra0       Link encap:Ethernet  HWaddr 68:7f:74:77:0b:21  
          inet6 addr: fe80::6a7f:74ff:fe77:b21/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:678991 (678.9 KB)  TX bytes:82716 (82.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:aa:cc:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ifconfig:

ra0       Ralink STA  ESSID:"linksys_SES_36564"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:-76 dBm  Noise level:-76 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


lsmod:

rt2800pci               8565  0 
rt2800lib              28897  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  1 rt2800pci
rt2x00lib              27275  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               2633  1 rt2x00lib
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              231541  3 rt2x00usb,rt2x00pci,rt2x00lib
rt3572sta             619595  1 
cfg80211              144470  2 rt2x00lib,mac80211
asus_atk0110           11423  0 
k10temp                 2607  0 
snd                    49006  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6            1345  1 rt2800pci


Network Config:

  *-network               
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:aa:cc:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:22 memory:fe7f0000-fe7fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 20:cf:30:e2:ed:c6
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:c800(size=256) memory:cffff000-cfffffff memory:cfff8000-cfffbfff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 68:7f:74:77:0b:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA


Kernal:

2.6.35-22-generic i686

---

### Post by badbob32 on 2011-01-03
And when I run: $ sudo iwlist ra0 scan

I can see all of the local networks, including mine:

ra0       Scan completed :

          Cell 02 - Address: 00:18:39:29:F2:B5
                    Protocol:802.11b/g
                    ESSID:"linksys_SES_36564"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/100  Signal level=-79 dBm  Noise level=-74 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


But when I put the WEP key in, it won't connect...  And I can't get Ubuntu on the net - I'm posting all this via my XP (dual boot).

---

### Post by PatchesTheCaveman on 2011-01-03
Try running:
```
sudo iwconfig
```
and copy/paste the output.

---

### Post by jaaronson on 2011-01-17
How did you install wusb600n on 10.10?? I've been looking all over for the answer. Please help me!

---

### Post by writeb on 2011-01-25
Any luck guys? I have the same problem - got the drivers to install on 11.04, rebooted - no blue light, BUT able to browse and select wireless networks. 

I select mine (WPA2) enter password and it spins for a while and then re-asks me to authenticate again. Mix repeat. 

Curious if It would connect to an open network, and it did not connect to that one as well. Driver issue perhaps?

---

### Post by sbrandon on 2011-01-25
I have the same USB and this is where there is an issue with Linux/Ubuntu or more directly with the manufacturers of the USBs. I will try to move my network from WEP to WPA2 tonight and see if that helps.

---

### Post by CrocodileShoes on 2011-02-12
> **writeb said:**
> Any luck guys? I have the same problem - got the drivers to install on 11.04, rebooted - no blue light, BUT able to browse and select wireless networks. 

I select mine (WPA2) enter password and it spins for a while and then re-asks me to authenticate again. Mix repeat. 

Curious if It would connect to an open network, and it did not connect to that one as well. Driver issue perhaps?

I have exactly the same issue.  Haven't been able to fix it yet.

---

### Post by Gunner2677 on 2011-05-03
I'm in the exact same boat! After fighting for hours to get the USB working, now I can't log on to my network!! Frustrating.

---

### Post by Gunner2677 on 2011-05-03
"How did you install wusb600n on 10.10?? I've been looking all over for the answer. Please help me!"

Try this link for install the USB: [http://ubuntuforums.org/showthread.php?t=1590144](http://ubuntuforums.org/showthread.php?t=1590144)

Got to #3, skip over the first section and follow everything the poster said under "This worked for me"

---

### Post by amiliv on 2011-05-04
There's two revisions of WUSB600N, and they use two different chips.  You need to find out which one you have (lspci is your friend, they have different PCI IDs).

rev 1: rt2870
rev 2: rt3572

There's also three sets of drivers, one provided by ralink, one included in kernel's staging directory (rumors are that this one will be removed, if not already removed upstream) and one also included with standard kernel developed by rt2x00 project (this should be your preferred driver).  You must blacklist the driver(s) you do not want to use, otherwise both will be loaded which can cause havoc (for example, lsmod output from badbob32's post above shows both of them loaded -- not good).  The one provided by ralink and the one in staging dir are called the same, rt2870sta (and I think rt3572sta for rev 2).  The one you should first attempt to get working is the same for both rev 1 and rev 2 cards and consists of multiple modules (rt2x00lib, rt2800lib, rt2800usb).

I have the rev 1 card (rt2870 chip), so here are my experiences:

If you upgraded to Ubuntu 11.04, you should be fine.  rt2x00 drivers included in 2.6.37 kernel work just fine.  There's one small annoying bug that most users will not notice, and there's an easy workaround for it.  Mainly, firmware for rt2870 will not wake up device when in power save mode to receive next beacon, the driver is supposed to do it.  If you notice latency spikes, or you happen to notice in the log files that card is re-connecting to AP every few minutes or so, then you are hitting that problem.  The workaround is to simply disable power-save mode (something like "iwconfig wlan0 power off" will do the trick, but you'll have to do it after every reboot).  Ivo just developed fix for this last week, and I'd be surprised not to see it included in the next upstream kernel release.  Again, make sure to blacklist old rt2870sta (or probably rt3572sta for rev 2) driver.  If it loads, it'll likely be the reason things are not working for you.

If you are still on previous Ubuntu release, the rt2x00 drivers from 2.6.35 kernel are simply way too old.  You'll need to compile them by hand.  Since it is about the same task to compile ralink's drivers and rt2x00 drivers, you should try rt2x00 drivers first.  You can download nightly tarball from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download).  This will actually give you *newer* version of the driver than the one included with Ubuntu 11.04.  I used this one for a long time on both 10.04 and 10.10, and they worked perfectly with my rev 1 card.

---

### Post by Gunner2677 on 2011-05-04
From all the searching I've done, there seems to be no workaround for version 2 of the adapter. I was able to manually compile a driver and I got the adapter to turn on and view networks, however, it won't connect. I've seen in other forums that users with version 2 are having the same problem. The odd person who is able to get it working can only use draft G instead of N. These adapters have been out for a quite a while now, there's no reason why the proper driver shouldn't be available. Even in Windows 7, the driver from the CD doesn't work properly. You have to hardwire to your router to download the proper driver. 

I just wish that option was available in Ubuntu.

---

### Post by amiliv on 2011-05-04
I stand corrected about the chipset in rev 2 cards (rt3572).

Said that, there were some very recent patches on rt2x00-users and linux-wireless mailing lists regarding rev 2 of WUSB600N and its rt3572 chip (as in last week or two).  Might be worth giving the latest nightly build a try and reporting results back to the rt2x00-users mailing list, if you happen to have rev 2 card.

The rt2x00 drivers seem to be the driver of choice for all ralink's chipsets (including rt3xxx and rt5xxx), and looking at the rt2x00-users mailing list they are actively developed and maintained, and you can spot people from ralink chiming in on the mailing list from time to time as well.

---

