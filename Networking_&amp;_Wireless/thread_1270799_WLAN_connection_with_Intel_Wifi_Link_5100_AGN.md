---
title: "WLAN connection with Intel Wifi Link 5100 AGN"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by nafihsus on 2009-09-20
I have a brand new Fujitsu Lifebook A6220 with a Intel Wifi Link 5100 AGN. Neither a Hardy out of the box installation nor following this [thread]("http://ubuntuforums.org/showpost.php?p=5754065&postcount=62") solved the problem (even though the procedure ran without any problems).

My private WLAN remains invisible in the network config. So far I kept the MS Vista partition, where the WLAN works without problems.

Any idea?

---

### Post by nafihsus on 2009-10-08
2 weeks passed by without any proposals. I therefore add all info recommended for wan posts and hope this will help someone to dig deeper.

---

### Post by jward3010 on 2009-10-08
Firstly, this is odd.```
lspci -nn | grep Intel
18:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4232]
```

```
wlan0     Link encap:Ethernet  HWaddr 00:21:5d:a2:25:e6  
          inet addr:192.168.2.98  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
Did you set this manually, or connect to something.

```
cenk@cenk-lifebook:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
```
Do the above with "sudo" in front.

Tips from me, firstly run the following and post output:
```
nm-tool
```
```
sudo iwlist scan
```

Something that can often help:
```
sudo ifconfig wlan0 up
```
Then
```
sudo iwlist scan
```

---

### Post by tenmoi on 2009-10-08
What if you installed wifi-radar and then ALT+F2 -> gksu wifi-radar.

NOte: let your A.P assign IP for your lap by modifying your interfaces file
 
iface wlan0 inet dhcp

---

### Post by nafihsus on 2009-10-13
Sorry for the delay - I was on a business trip and had no time on the weekend. I had installed the driver based on the link in the first post of this thread. Here the posts:

cenk@cenk-lifebook:~$ nm-tool

NetworkManager Tool

State: connected

print_devices(): didn't get a reply from NetworkManager.
There are no available network devices.

cenk@cenk-lifebook:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:75:32:A0:C1
                    ESSID:"eldewlan"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=98/100  Signal level:-27 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=00000064444be2ea
                    Extra: Last beacon: 1660ms ago


cenk@cenk-lifebook:~$ sudo ifconfig wlan0 up
cenk@cenk-lifebook:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:75:32:A0:C1
                    ESSID:"eldewlan"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/100  Signal level:-69 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=0000006449185a99
                    Extra: Last beacon: 1552ms ago

---

### Post by jward3010 on 2009-10-13
OK, I may have had a similar problem with a Dell Vostro and an Intel 5300 AGN. The good news is that the kernel can talk to your wireless card, it wouldn't have returned those results if it didn't. This could be an rfkill problem. Post the output of ```
rfkill -list
```
 
Also you might want to try "wicd", another network manager. That is of course if you can get a wired internet connection somehwere.
```
sudo apt-get install wicd
```

My particular bug might help as well: [https://bugs.launchpad.net/bugs/441768](https://bugs.launchpad.net/bugs/441768)

---

### Post by nafihsus on 2009-10-15
The rfkill command is not found.
By the way - all the outputs posted are produced whilst being connected wired!

---

### Post by jward3010 on 2009-10-16
What version of Ubuntu are you using? Is it still Hardy?

---

### Post by nafihsus on 2009-10-16
yes. Hardy 8.04.

PS: Tomorrow I leave for a 1 week China private trip. No access to Internet. I'll be back Sunday 25th.

---

### Post by jward3010 on 2009-10-16
Maybe rfkill had no place in 8.04, it's prevelant in 9.04 and 9.10 and is the root of a few wireless problems at the mo. Enjoy China and hopefully we'll have something for you when you come back

---

### Post by jward3010 on 2009-10-16
Here's a mad one to try, it helped me, albeit in 9.10 and a Dell laptop. Go to Fujitsu Siemens site and see if there are BIOS upgrades, if yes, install. I had an Intel 5300 AGN which couldn't enable in Karmic, BIOS update did it.

The process rfkill (although not applicable to you, I don't think) couldn't read the BIOS status of the wireless switch and although it Ubuntu could understand the card it couldn't switch on the radio. Updating the BIOS fixed this "read-status" problem, maybe some other daemon that read's status is borked in your Hardy.

---

### Post by nafihsus on 2009-11-01
After a great week in Yunnan province, surrounded by 5500m mountains and a very busy week in office I am back to my WLAN problem. I checked the Fujitsu pages but could not find any link to a BIOS software, only OS drivers. My BIOS is V1.08. and I guess I a miss something much simpler to get WLAN running. 
I already have bad thoughts ... (Win7) - just a joke

---

### Post by jward3010 on 2009-11-02
Ah well, worth a try.

---

