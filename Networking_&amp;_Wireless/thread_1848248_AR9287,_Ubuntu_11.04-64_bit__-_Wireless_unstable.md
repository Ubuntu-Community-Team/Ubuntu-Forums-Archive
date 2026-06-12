---
title: "AR9287, Ubuntu 11.04-64 bit  - Wireless unstable"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by g_knap on 2011-09-22
I ran an dist.upgrade on my laptop yesterday form 10.04 - 10.10 -11.04. (64bit)
The wireless connection worked flawless on 10.04, but i it's very unstable in 11.04.
Connects just fine, but then down-/upload drops to ~0, then disconnects.
And then the cycle repeat it self.

I'm green at this stuff, so please, any solutions have to be step-by-step.
[B]

1 ) Machine Brand and Model (PC/Laptop)[/B]:

 Acer Aspire 5742

[B]2 ) Wireless Brand, Model and Wireless Chipset:

[/B]```
xxxx@xxxx-laptop:~$ lspci -nn | grep "Atheros"
02:00.0  Network controller [0280]: Atheros Communications Inc. AR9287 Wireless  Network Adapter (PCI-Express) [168c:002e] (rev 01)
```[B]3 ) check interface:
[/B]
```
xxxx@xxxx-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"xxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:07:02:A3:67   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:87  Invalid misc:17   Missed beacon:0
```[B]4 ) Check for modules:

[/B]```
xxxx@xxxx-laptop:~$ lsmod | grep "ath"
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath
```[B]5 ) Kernel boot messages:

[/B]```
xxxx@xxxx-laptop:~$ dmesg | grep "ath"
[    4.798907] device-mapper: multipath: version 1.2.0 loaded
[    4.798910] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.489299] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.489310] ath9k 0000:02:00.0: setting latency timer to 64
[   15.578320] ath: EEPROM regdomain: 0x65
[   15.578323] ath: EEPROM indicates we should expect a direct regpair map
[   15.578325] ath: Country alpha2 being used: 00
[   15.578326] ath: Regpair used: 0x65
[   16.002974] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.003510] Registered led device: ath9k-phy0::radio
[   16.003523] Registered led device: ath9k-phy0::assoc
[   16.003537] Registered led device: ath9k-phy0::tx
[   16.003549] Registered led device: ath9k-phy0::rx
[  355.470289] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  355.470330] ath: Failed to stop TX DMA!
[  355.719555] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  355.719623] ath: Failed to stop TX DMA!
[  369.943709] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  369.943751] ath: Failed to stop TX DMA!
[  439.825532] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  439.825572] ath: Failed to stop TX DMA!
[  594.302798] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  594.302840] ath: Failed to stop TX DMA!
[  658.235594] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  658.235636] ath: Failed to stop TX DMA!
[  714.083321] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  714.083363] ath: Failed to stop TX DMA!
[  715.350959] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  715.351028] ath: Failed to stop TX DMA!
[  754.010170] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  754.010212] ath: Failed to stop TX DMA!
[ 1458.257192] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1458.257231] ath: Failed to stop TX DMA!
[ 1532.543922] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1532.543961] ath: Failed to stop TX DMA!
[ 1626.025933] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1626.025978] ath: Failed to stop TX DMA!
[ 1755.552178] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1755.552220] ath: Failed to stop TX DMA!
[ 1762.545620] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1762.545660] ath: Failed to stop TX DMA!
[ 2297.334785] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 2297.334823] ath: Failed to stop TX DMA!
[ 2409.433565] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 2409.433633] ath: Failed to stop TX DMA!
[ 2412.216785] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 2412.216825] ath: Failed to stop TX DMA!
[ 2806.120306] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 2806.120346] ath: Failed to stop TX DMA!
[ 2922.827896] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 2922.827935] ath: Failed to stop TX DMA!
[ 3587.277767] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 3587.277805] ath: Failed to stop TX DMA!
[ 3597.264499] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 3597.264538] ath: Failed to stop TX DMA!
[ 3859.642592] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 3859.642633] ath: Failed to stop TX DMA!
[ 3923.503450] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 3923.503489] ath: Failed to stop TX DMA!
[ 4062.479204] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 4062.479243] ath: Failed to stop TX DMA!
[ 4181.900783] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 4181.900823] ath: Failed to stop TX DMA!
```**6 ) Network configuration:**
```
xxxx@xxxx-laptop:~$ sudo lshw -C wlan0
PCI (sysfs)
```[B]7 ) Scan for networks:

[/B]```
xxxx@xxxx-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"xxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bba0d2188
                    Extra: Last beacon: 97150ms ago
                    IE: Unknown: 000D4E65787447656E54656C5F3638
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```[B]8 ) Ubuntu Version: 

[/B]```

xxxx@xxxx-laptop:~$ lsb_release -d
Description:    Ubuntu 11.04
```[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 

[/B]```
xxxx@xxxx-laptop:~$ uname -mr
2.6.38-11-generic x86_64
```[B]10 ) Restarting the network:

[/B]```
xxxx@xxxx-laptop:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 *  Reconfiguring network  interfaces...                                                                    Ignoring unknown interface wlan0=wlan0.
```

---

### Post by praseodym on 2011-09-22
The driver ath9k often makes these problems in 11.04. Shut off the hardware encryption:

```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo service network-manager restart
```
If it works, make it permanent at boot-up:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

---

### Post by g_knap on 2011-09-22
Thank you.
Seems to be working better (longer between stops), but it still stops, disconnects and starts again.

---

### Post by praseodym on 2011-09-22
The encryption mode looks weird, try pure WPA2-AES (CCMP) if possible, other encryption modes often make problems with the network-manager. If the router only allows mixed WPA/WPA2, WPA(1) or WEP, or other clients need other modes, try Wicd instead of the network-manager:


```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo servcie wicd restart
```
Choose **wlan0** as interface name and **wext** as driver and disable the NM in autostart.

---

### Post by g_knap on 2011-09-22
Ok tried to set router to pure WPA2-AES and wireless seems to work fine 80% of the time.
And thats not perfect but its ok.
I'm happy.

Thank you for your help.

---

### Post by coverman on 2012-03-28
I also had to deal with an unwilling Atheros ar9287 driver on a Kubuntu 11.10 install.

In rare occasions it would connect at startup but didn't last long, very unstable.

Tried many things but the one which ultimately seemed to solve (for the last half hour though but that's still way better than it was) it was to change my AP setting from Mixed mode 11b+11g+11n to Mixed mode 11g+11n

---

### Post by kallosz on 2012-04-04
I have the same problem :( Anyone can help?

lspci -k | egrep -iA2 'Network|Wireless'
```

08:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e034
	Kernel driver in use: ath9k
```

ifconfig 
```

eth0      Link encap:Ethernet  HWaddr 88:ae:1d:81:9b:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25420 (25.4 KB)  TX bytes:25420 (25.4 KB)

wlan0     Link encap:Ethernet  HWaddr 5c:ac:4c:1d:5e:bd  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5eac:4cff:fe1d:5ebd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:246172292 (246.1 MB)  TX bytes:13468164 (13.4 MB)
```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Siec"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:7F:61:C6:08   
          Bit Rate=300 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:10   Missed beacon:0

```

iwlist
```

wlan0     Scan completed :
          Cell 01 - Address: 00:50:7F:61:C6:08
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Siec"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a0168ff152
                    Extra: Last beacon: 101284ms ago
                    IE: Unknown: 00094D6F64657261746F72
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706545720010D10
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000101103B00010310470010BC329E001DD811B2860100507F61C6081021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000100

```

---

### Post by wildmanne39 on 2012-04-04
Hi, please see post 2 and do what it says then report back.
Thanks

---

### Post by kallosz on 2012-04-05
Not work for me :(

---

### Post by praseodym on 2012-04-05
Change the encryption mode to pure WPA2-AES instead of mixed mode.

---

### Post by kallosz on 2012-04-05
not everyone has access to the router to change these things.

---

### Post by kallosz on 2012-04-08
Any other ideas?
This problem has plagued me for nearly a year and only distracts from Linux

---

### Post by praseodym on 2012-04-08
Tried Wicd?

---

### Post by kallosz on 2012-04-08
> **praseodym said:**
> Tried Wicd?

Yes, no effect.

---

### Post by praseodym on 2012-04-08
Uninstalled the NM, too?

---

### Post by kallosz on 2012-04-10
Yes. Problem is still present.
I found something like this: [https://bbs.archlinux.org/viewtopic.php?id=129344](https://bbs.archlinux.org/viewtopic.php?id=129344)

"After many days of searching I see that this adapter works only with linux kernel version < 2.6.35."

I am convicted of older versions of Ubuntu and other distributions that such kernels have? Is it somehow goes with the latest kernel patch to work as in that old?

---

### Post by kallosz on 2012-04-14
Anyone ?

---

### Post by eiriksm on 2012-04-26
Hello. I am not sure I have a solution for you kallosz, as I had the same problem, and tried every tip I found (including the ones in this thread).

However, today I upgraded to 12.04 and applied the fixes suggested on page 1, and wifi now seems completely stable (or so it seems anyway.)

You could try that?

And while I am at it, thanks to those posting solutions earlier, as this helped me (now that I am on 12.04)

---

### Post by kallosz on 2012-06-30
eiriksm, i have 12.04 but this not help me. WIFI is still unstable.

---

