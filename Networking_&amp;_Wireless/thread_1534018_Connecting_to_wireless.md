---
title: "Connecting to wireless"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by mohanms on 2010-07-18
Hi. I'm currently new to Ubuntu. I'm doing as a research for my project in my company. Before this I was connecting to the wireless connection in my office and was browsing away. But during the weekend I went back home and connected to broadband connection using pppoe and now when I came back to my office I cant seem to be able to browse the net. The wireless connection is showing connected but I cant browse.
 
Now I'm using another laptop to write here. Could anyone help me out with this prob? You could actually say I'm a NOOB when it comes to Ubuntu. I'm just learning. Please help me out.
 
Previously I tried some methods given by others in this forum and also others. But to no avail. So if someone could help me out in this prob, I would appreciate it very much. Thank you so much.
 
Regards,
Mohan

---

### Post by drpjkurian on 2010-07-18
Hi Mohan
Since you have used wireless earlier in your machine, it is supposed to work.
Please try this open network manager by double clicking it and enter ath0

Usuually in my machine a dell vostro laptop fired by kubuntu Lucid with AR5001 wireless chipset and Madwifi drivers was solved by the above mentioned method ie enter ath0 for wireless and eth0 for wired

---

### Post by mohanms on 2010-07-18
Hi drpjkurian.
 
> **drpjkurian said:**
> Please try this open network manager by double clicking it and enter ath0
 
 
I don't clearly get what you mean here. Could you please explain abit more breifly? I'm sorry for any inconvinience caused

---

### Post by mohanms on 2010-07-19
I get this output when I type iwconfig.
 
[EMAIL="mohan@mohan-laptop:~$"]mohan@mohan-laptop:~$[/EMAIL] sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11g  ESSID:"Wincom IT Solutions"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:5E:42:CB:56   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:7769-6E63-6F6D-3154-4164-6D69-6E   Security mode:open
          Power Management:off
          Link Quality=85/100  Signal level=-45 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
 
from here its shows that the connection is established without any problem right?
pls help me. im stuck with this

---

### Post by mohanms on 2010-07-19
oops... i didnt know bout the emticons... lol... sorry... here is the real output... sorry...
 
[EMAIL="mohan@mohan-laptop:~$"]mohan@mohan-laptop:~$[/EMAIL] sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11g  ESSID: "Wincom IT Solutions"  
          Mode: Managed  Frequency: 2.412 GHz  Access Point: 00:25:5E:42:CB:56   
          Bit Rate:54 Mb/s   Tx-Power= 20 dBm   Sensitivity= 8/0  
          Retry limit: 7   RTS thr: off   Fragment thr: off
          Encryption key: 7769-6E63-6F6D-3154-4164-6D69-6E   Security mode: open
          Power Management: off
          Link Quality= 85/100  Signal level= -45 dBm  Noise level= -92 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

---

### Post by mohanms on 2010-07-19
Hi again...
 
I tried connecting to the broadband connection at home and it worked fine. I could connect and also browse the net. But not when I come to the office and connect using wireless. Please help. Need it desperately

---

### Post by drpjkurian on 2010-07-19
Hi
The output shows that your wireless is dead

---

### Post by mohanms on 2010-07-19
> **drpjkurian said:**
> The output shows that your wireless is dead
 
could you please show me where it shows that? and how to activate it? isit because there is a pppoe connection active? im really blank with this. thank you

---

### Post by drpjkurian on 2010-07-20
> **mohanms said:**
> could you please show me where it shows that? and how to activate it? isit because there is a pppoe connection active? im really blank with this. thank you

Hi 
What I've understood from your output is that there is no wireless extension
See the line 'eth0 no wireless extension'....
It also shows that you have a wireless card known as eth1 IEEE 802.11g ESSID: "Wincom IT Solutions" but not active usually because of driver problem.

If you have an active wireless, you will be having output like 
ath0 or wlan0
which you do not have...

---

### Post by mohanms on 2010-07-20
The Wincom IT Solution is the connetion name. not the wireless card name
 
and IEEE 802.11g ESSID is the wireless connection type

---

### Post by dineshs on 2010-07-20
Can you post the contents of the following (in your laptop having problem)
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
and
```
gksudo gedit /etc/network/interfaces
```

---

### Post by mohanms on 2010-07-21
> **dineshs said:**
> Can you post the contents of the following (in your laptop having problem)
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
and
```
gksudo gedit /etc/network/interfaces
```
 
 
Hi.
 
This is the output:
 
for gksudo gedit /var/lib/NetworkManager/NetworkManager.state =>
 
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```
 
for gksudo gedit /etc/network/interfaces =>
 
```

auto lo
iface lo inet loopback

```
 
thank you

---

