---
title: "Problems connecting to home wireless network"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by PianoMan256 on 2010-08-14
Hi all,

My problems started when I inadvertently "autoremoved" a bunch of apparently vital packages when I ran an "aptitude" command. The next time I booted up my laptop, it started the splash screen for a few moments, then went blank, then hung. I was able to sidestep the boot and get into the recovery menu, where, to my delight, I saw an option reading "dpkg ... Repair broken packages", but, unfortunately, around this time, the home network was having problems of its own, so I was left GUI-less and internet-less. When the home network problem was sorted out, I tried it again, but it wouldn't connect. As 'root', I started giving myself a crash course in network-relate command line tools, but I'm a complete beginner when it comes to networks, and I couldn't make any headway.

Then, one morning, BAM! ifconfig, iwconfig, etc, suddenly did what they were supposed to, and I had internet again. I repaired the broken packages, but it didn't change the fact that it still hangs on startup. And after another reboot, I DIDN'T have internet again! I tried to retrace my steps, and reproduce my lucky fluke, but I seemed to be back at square one. I thought maybe I was doing the commands out of sequence, but nothing I try seems to work.

Here is the output of various commands: hopefully they make more sense to someone than they have so far to me...

```
root@mylaptop:~# ifconfig wlan0
wlan0    Link encap:Ethernet HWaddr 00:21:63:6d:4d:4f
         BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets: 0 errors:0 dropped:0 overruns:0 frame:0
         TX packets: 0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@mylaptop:~# iwlist wlan0 scan
wlan0    Scan completed :
         Cell 01 - Address: XX:XX:XX:XX:XX:XX
                   Channel:11
                   Frequency:2.462 GHz (Channel 11)
                   Quality=70/70  Signal level=-3dBm
                   Encryption key:on
                   ESSID:"HOMENET"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6Mb/s
                             12 Mb/s; 24 Mb/s; 36 Mb/s
                   Bit Rates:9 Mb/s;18 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=000004bf28551078
                   Extra: Last beacon: 412ms ago
                   IE: Unknown: 0003505941
[ 4x more lines of IE: Unknown: SOMENUMBER ]

root@mylaptop:~# iwconfig wlan0 essid HOMENET key XXXXXXXXXX
root@mylaptop:~# iwconfig wlan0
wlan0    IEEE 802.11bg  ESSID:"HOMENET"
         Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Encryption key:XXXX-XXXX-XX
         Power Management:off

root@mylaptop:~# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, pleae visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:21:63:6d:4d:4f
Sending on   LPF/wlan0/00:21:63:6d:4d:4f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```I did notice that iwlist gave a "Master" mode, while iwconfig was set to "Managed", but 

trying to change it only yielded:

```
root@mylaptop:~# iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```
I'm running Ubuntu 10.04 on a Toshiba Satellite Pro. Any help would be appreciated!
Cheers

---

### Post by AlphaLexman on 2010-08-14
Make sure NetworkManager is running:
```
sudo NetworkManager
```
Although I think it would be if you are getting good wlan0 output.

---

### Post by PianoMan256 on 2010-08-14
Done. Checks out ok:

```
root@mylaptop:~# NetworkManager

** (NetworkManager:1925): WARNING **: NetworkManager is already running (pid 709)
```

---

### Post by AlphaLexman on 2010-08-14
I missed this the first glance at your post:
>  No working leases in persistent database - sleeping.
The DHCP client doesn't have a 'lease' to an IP address. Usually your router will lease an IP  address for 24 hours, then assign a new one, but on a small home network, that IP address usually doesn't change.

Check your router settings to make sure your lease renews.

---

### Post by PianoMan256 on 2010-08-14
I would love to... [ahem]... did I mention I was a beginner? :( I'm afraid talk of routers without mentioning which commands are needed to check them is a bit beyond me...

What I failed to mention previously was that when I type "iwconfig wlan0 essid HOMENET key XXXXXXXXXX" when the network is "down", and then "iwconfig wlan0", it tells me (among other things...)

```
ESSID:"HOMENET"
Access Point: Not-Associated
Encryption key: XXXX-XXXX-XX
```

... as (I suppose) it should. (?)

BUT... when I type "ifconfig wlan0 up", followed by "iwconfig wlan0", it tells me:

```
ESSID:"\x05\xEF\xF7\x00\xE9\xA1:\xE5\xCA [ ...more garbage here ... ] C5^Kyc"
Access Point: Not-Associated
Encryption key:off
```

I'm pretty sure that's not meant to happen.

Thanks, by the way, for your help so far... keep it coming! :)

---

### Post by AlphaLexman on 2010-08-14
Your router should have a 'settings' page you can access with a web browser. For me it is 198.162.0.1 It might be printed on the back of the router or in the manual that came with it. It most likely will still be the default setting unless you changed it. Some models require you to be hard wired to the router to even gain access to the settings. This can be changed, but it may be the default. 

Just enter ->
```
http://198.168.0.1
```into a browser replace the numbers you have for mine.

You'll be asked for a password, if not, your network is NOT secure! If you haven't set a password, the manual should tell you the default password. (You'll want to change it).

You'll have to find the settings page for the DHCP leases and set up your router properly.

Read your manual thoroughly. I don't want the thread to get too far off topic, so if you need help with passwords or understanding DHCP, then start a new post.

Oh, and it's a good idea to bookmark your settings page in your browser

---

### Post by PianoMan256 on 2010-08-14
I'll just mention again that the network itself is running fine and normally. It is successfully tested on other wireless laptops--albeit ones running windows--and, as I said, was previously working on my ubuntu machine too. No router settings have changed before or since. I'm afraid it's only my local settings that seem to have come unstuck.

New development: No problems at all connecting via ethernet cable: just plugged it in and suddenly the internet works, so apparently the problem is definitely with my local wireless settings.

It has been brought to my attention that the network setup here is not typical of "home wireless networks". We have a proper LAN operating, complete with servers etc, not just one of those "direct link to internet" minimalist jobs. Don't know if it's relevant, but there it is.

Thanks

---

### Post by AlphaLexman on 2010-08-14
Well, you still don't have a DHCP lease. That can only be fixed by the router.

---

### Post by PianoMan256 on 2010-08-14
Well, thanks for taking an interest, AlphaLexman. I'll have to pick this up again another time. No luck yet, I'm afraid. The router settings all appear to be as they should, given the setup here. I can only stress the fact that since I did (luckily) manage to establish a working connection *at least once* (earlier today), that the router and everything else external to my laptop *must* be behaving as it should be. The only changing variable has been me and what I've typed at the bash prompt on my woebegone laptop. I'm hoping this logic is sound...

---

