---
title: "wireless network"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by cyborgcey59 on 2010-01-05
I have updated my system to 9.10 it is show my connection but when I go into firefox its shows it can't get online.  What do I need to do?:(

---

### Post by changingstate on 2010-01-05
What do you see if you execute ifconfig in a terminal?

Does firefox have a proxy set ( Edit -> Preferences, Click advanced, then the network tab, then the settings button. Unless your ISP are a bunch of jokers, you want 'No Proxy' ticked. )

---

### Post by cyborgcey59 on 2010-01-05
everything is good in firefox, I get a lot of messages when I typed ifconfig a large amount of messages come up. what do I do now?

---

### Post by changingstate on 2010-01-05
Tell me what ifconfig said.

---

### Post by cyborgcey59 on 2010-01-05
inet 6 addr:1/128 scope: Host
up loopback running mtu:16436 Metric:1
Rx Packets: 0 errors:dropped:0 overruns:0 Frame:0
TX Packets: 0 errors:dropped:0 overruns:0 carrier: O
collisions: 0 TXqueuelen:0
RX Bytes: 0 (00B) TX BYTES: 0 (00B)

WLAN 0
LINK CAP: ETHERNET HWADDR: 00:11:95:92:F3:05
iner 6 addr: fe80:211:95ff:fe92:f305/64:scope: Link
up Broadcast Multicast Mtu1500 Metric: 1
RX Packets:16 errors:0 dropped:0 overruns:0 frame: 0
TX Packets 14 errors:0 dropped:0 overruns:0 carrier: 0
Collisions:0 Txqueuelen 1000
RX bytes:5197 (5.1) TX (3.0KB)

 WMASTER0
-00
     Link encap: UNSEC HWaddr
00-11-95-92-F3-0539-32-00-00-00-00-00
Up running MTU:0 metric:1
Rx Packets: 0 errors:dropped:0 overruns:0 Frame:0
TX Packets: 0 errors:dropped:0 overruns:0 carrier: O
Collision:0
RX Bytes:0 (0.0 KB) TX Bytes (0.0 )

---

### Post by Kevbert on 2010-01-05
Please post the output of
```
lspci | grep Network
iwconfig
```
(the | character may be found using Shift+\).
It may be that you need to install a firmware driver or that the wireless signal is poor, hence the large number of errors.

---

### Post by changingstate on 2010-01-05
Edit : I'll wait

---

### Post by cyborgcey59 on 2010-01-05
I am confussed do I type that into the terminal?

---

### Post by cyborgcey59 on 2010-01-05
I tryed tried the code and it said it could not be found

---

### Post by changingstate on 2010-01-05
Ok..picking up where I left off... 

Up on the grey bar on the top of the screen, between the speaker icon and the envelope icon on my system, is the network icon. Right click that and go to Edit Connections. Then click on Wireless, you should see your router's name ( I'm assuming you're using a router, tell me if I'm wrong, it should be the same name as your windows computer I assume your typing these posts on :) ), click on it to highlight it. Then click edit, then always allow on the pop up. Next, click on the wireless security tab, delete the Key field and retype it (this should be your wireless password. Make sure you get it right, we used to get loads of calls about this when I used to do this for my job :P ).

Apply and close, see if that fixes it.

---

### Post by cyborgcey59 on 2010-01-05
Done that several times no good also is is showing my router just nothing connects. Oh  the computer I am typing on is not my Linux machine its down in the basement and take me a while have bad arthritis so it take me some time to go back and forth.

---

### Post by changingstate on 2010-01-05
Sorry to have you moving back and forth so much. Human error was a huge issue with wireless keys when I was a phone monkey. 

Okay... if you could try : 

dhclient wlan0 

lshw -c network

and type up the results of each, we should be getting fairly close to a solution.

---

### Post by cyborgcey59 on 2010-01-05
dhclient wlan0   = can't creat/var/lib/dhcp3/dhclient leases: Premission denied
siocsifaddr: Premission denied
siocifaddr" : Premission denied
siocifaddr" : Premission denied
Open a socket for lpf operation  not premitted

lshw-c network comand not found

---

### Post by changingstate on 2010-01-05
Whoops. My fault, chatting to my housemate about her mum. Try

sudo dhclient wlan0

lspci

lsusb

---

### Post by cyborgcey59 on 2010-01-05
well I must stop for today thank both of you for your heip.

---

### Post by Kevbert on 2010-01-06
The commands in post #6 are for terminal. The lshw command should be
```
lshw -C network
```
as linux commands are case sensitive.
Please post the make and model of your wireless adapter. Can you connect the PC to the internet via a LAN cable ? If so, then connect it and then go to System-Administration-Hardware Drivers. This will look for third party/manufacturer's drivers for your hardware (wireless and display adapters usually) and install them.

---

