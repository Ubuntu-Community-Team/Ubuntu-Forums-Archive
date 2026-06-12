---
title: "Wifi connection drops"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by loghete on 2010-05-01
I'm having a really strange problem with my wifi connection on my laptop. The ethernet connection works fine and so does the wifi connection - as long as I sit within one meters range from my router! As soon as I take the laptop further away the connection drops. The router is still being found by network-manager and the signal is just below 100%, but when I try to establish a connection it fails.
I'm sitting here on a fresh Ubuntu 10.04 install, and I had exactly the same problem with 9.10. That time I went through a lot of different procedures, and in some strange way the problem was solved. I haven't been that lucky this time though, I've tried reinstalling network-manager, using ndiswrapper, installing the wireless backports package, tried all kinds of drivers.. nothing works.

There shouldn't be any problem with the connection itself; I've had a perfect connection downstairs but now I can't even connect if I stand two metres from the router!

Has anyone experienced anything like this and managed to fix it?

My wireless card is Atheros AR2413.

This is an example from daemon.log
> Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Wester'
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Wester' requires no security.  No secrets needed.
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Config: added 'ssid' value 'Wester'
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Apr 30 00:45:51 petter-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Apr 30 00:45:53 petter-laptop wpa_supplicant[859]: Trying to associate with 00:23:cd:d7:9d:7c (SSID='Wester' freq=2437 MHz)
Apr 30 00:45:53 petter-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 30 00:45:53 petter-laptop wpa_supplicant[859]: Association request to the driver failed
Apr 30 00:45:58 petter-laptop wpa_supplicant[859]: Authentication with 00:23:cd:d7:9d:7c timed out.
Apr 30 00:45:58 petter-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 30 00:45:58 petter-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 30 00:45:59 petter-laptop wpa_supplicant[859]: Trying to associate with 00:23:cd:d7:9d:7c (SSID='Wester' freq=2437 MHz)
Apr 30 00:45:59 petter-laptop wpa_supplicant[859]: Association request to the driver failed
Apr 30 00:45:59 petter-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 30 00:46:04 petter-laptop wpa_supplicant[859]: Authentication with 00:23:cd:d7:9d:7c timed out.
Apr 30 00:46:04 petter-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnectedHere's some more raw info:

```
05:01.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)[/QUOTE]> Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```ifocnfig
```
wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:ef:2b:88  
          inet6 addr: fe80::2c0:a8ff:feef:2b88/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1250284 (1.2 MB)  TX bytes:268017 (268.0 KB)

```iwconfig
```
wlan0     IEEE 802.11bg  ESSID:"Wester"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```lsmod
[QUOTE]ath5k                 122144  0 
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
cfg80211              126517  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
dmesg
> [   10.190421] ath5k 0000:05:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.190492] ath5k 0000:05:01.0: registered as 'phy0'
[   11.402357] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
lshw
>  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:ef:2b:88
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:40600000-4060ffff
```
wlan0     Scan completed :
          Cell 01 - Address: 00:23:CD:D7:9D:7C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"Wester"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d6164181
                    Extra: Last beacon: 876ms ago
                    IE: Unknown: 0006576573746572
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706464920010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000023CDD79D7C0223CDD79D7C64002C010808

```uname
> 2.6.32-21-generic-pae i686> petter@petter-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by loghete on 2010-05-02
I've added some more info.

Thanks for any help!

---

### Post by loghete on 2010-05-03
Update: I've tried 5 different Windows drivers through ndiswrapper, none of them work. I can't even find my router with any of them, so I've reverted back to ath5k.

---

### Post by Brandon.Viking on 2010-05-05
bump ... any updates? 

I have a laptop of my moms which works fine for a little while then drops out and it never used to ...
My question ... what has changed? Worked fine in 9.10 just since the upgrade has the drop outs been occurring. Is there a timeout parameter which has been lowered or switched off or something? Anyone?

Regards,
Brandon.

PS . 
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
is the listing of the wireless adapter for the laptop.

---

### Post by Ozcan008 on 2010-05-09
I had a similar problem after upgrading from 9.10 to 10.04.  I have an Acer Aspire 5670 laptop and after upgrading to 10.04, after 1+ hours, Ubuntu would drop the wifi connection and the only way I could get it to reconnect was to reboot.  I followed the instructions on the following link, and it has fixed the problem (i.e. install linux-backports-modules-wireless-lucid-generic):

[http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html](http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html)

---

### Post by loghete on 2010-05-10
I've tried installing the backport modules but it changed nothing.. but thanks anyway.

I'm still not having any luck, and I've ran out of ideas! Has anyone got any?

---

### Post by chili555 on 2010-05-10
First, let's rule out radio frequency interference. Can you please change the channel in the router to 11? Also, see if there is an option to increase the transmit power in the router.

Mine has such a setting and it was set at 50% by default; I increased it to 100%.

There is a parameter we might try, although it looks non-relevant. Who knows what might help. Please try```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```If this works, I will be surprised and then we will have to write a one line file to make it permanent.

---

### Post by loghete on 2010-05-10
Thanks for the help.

I tried changing the channel to 11, but that doesn't appear to have changed anything, it acts just as before. I can't find any transmit power setting but my Nintendo Wii can connect without problems from downstairs so the signal should be fine..

I also tried your code but it rather made it worse; it disabled the wireless completely until I restarted the computer.

I don't know if this is relevant but I get a warning when I enter the code
> all config files need .conf: /etc/modprobe.d/ndiswrapper/

---

### Post by ebike on 2010-10-29
I have a similar issue with network manager, my connection drops every now and then. If I use Wicd instead, my network stays up all the time ... try Wicd and see how you get on..

---

### Post by bigfootnmd on 2010-10-30
Here is a trick to try.  Download any of the Ubuntu 10.10 versions (including NBR) and make a startup USB disk.
Book off of the USB disk into Ubuntu 10.10.  If you are told that there are network connections available and you are then prompted to choose one then you should move to 10.10 and forget 10.04.
Ubuntu 10.10 has NATIVE LINUX drivers for many Atheros cards.
My netbook as the Atheros 5x chip.  I used the NDSIwrapper drivers and they did work.  But now things are even better with Ubuntu 10.10.  

Good luck

---

### Post by pabc on 2010-11-08
except 10.10 has unity which I dislike....
 
my wifi is fine for low volumes but as soon as I try to move a 200MB file to my NAS drive it drops. I have to transfer files to a thumb drive then use my hardwired desktop PC to move them across.
 
Still, that's prefereable to unity.

---

