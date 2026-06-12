---
title: "how to make a network in Ubuntu?"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by roshats on 2010-03-06
Hello. I'm new in Ubuntu. i have desktop and laptop. i have an access to Internet via wifi adapter in my desktop ( [http://ubuntuforums.org/showthread.php?t=1404496](http://ubuntuforums.org/showthread.php?t=1404496) ) . my questions are :
1) how can i create a a network between laptop and desktop?
Please, write a step-by-step instruction.
2) how can i create a repository at my laptop to update packages from laptop i.e.  for example there are some updates for some program at ubuntu repository. i've downloaded them from Internet to my laptop. i don't want to download them from Internet again. i want to download it from my laptop.

---

### Post by spiky001 on 2010-03-06
Hi I take it the desktop has a wired connection to internet?

---

### Post by roshats on 2010-03-06
Yes. Laptop connected to desktop via wifi and desktop connected to Internet via wire

---

### Post by Iowan on 2010-03-07
Glad you got the ICS working... If the laptop is going through the desktop to get to the Internet, then the connection must exist. You can check **ifconfig -a ** (from a terminal) to see if they have an interface in the same subnet (192.168.X.X?).

---

### Post by roshats on 2010-03-07
yes, now i have internet on laptop. thanks Iowan.
from laptop:
roman@roman-laptop:~$ ifconfig -a  
eth0      Link encap:Ethernet  HWaddr 00:1d:72:02:d6:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          &#1055;&#1088;&#1077;&#1088;&#1074;&#1072;&#1085;&#1086;:16 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1059;&#1079;&#1077;&#1083;
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:d9:57:80:40  
          inet addr:10.42.43.10  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:d9ff:fe57:8040/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4529 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:3973241 (3.9 MB)  TX bytes:737786 (737.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-D9-57-80-40-35-37-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

from desktop:
pavel@pavel-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:8f:50:e6:82  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe50:e682/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:319055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:271584 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:355805207 (355.8 MB)  TX bytes:30707643 (30.7 MB)
          &#1055;&#1088;&#1077;&#1088;&#1074;&#1072;&#1085;&#1086;:21 Base address:0x2000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1059;&#1079;&#1077;&#1083;
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:545 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:0 
          RX bytes:27829 (27.8 KB)  TX bytes:27829 (27.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:01:0c:5c:ad  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1ff:fe0c:5cad/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120311 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:13845928 (13.8 MB)  TX bytes:129840034 (129.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-01-0C-5C-AD-30-63-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[[COLOR=#339900]****[/COLOR]]("http://art.ubuntuforums.org/member.php?u=65323")

---

### Post by roshats on 2010-03-14
Does anybody know the answer?

---

### Post by spiky001 on 2010-03-14
Hi I take it you have your internet problem fixed then?
I have googled your 2nd question It looks like you want to download the updates save them somewhere then update both machines from 1 download? I googled how to update without internet which would basically be what you are doing the same princible have a look through this google
 [http://www.google.co.uk/#hl=en&source=hp&q=update+without+internet+ubuntu&btnG=Google+Search&meta=&aq=f&aqi=&aql=&oq=update+without+internet+ubuntu&fp=dd6458e1d4f196b6](http://www.google.co.uk/#hl=en&source=hp&q=update+without+internet+ubuntu&btnG=Google+Search&meta=&aq=f&aqi=&aql=&oq=update+without+internet+ubuntu&fp=dd6458e1d4f196b6)

[http://ubuntuforums.org/showthread.php?t=1428527](http://ubuntuforums.org/showthread.php?t=1428527)

should give you the idea you are after

---

### Post by roshats on 2010-03-14
Yes, it's a way. But i wanted something like [http://ubuntuforums.org/showpost.php?p=8959101&postcount=5](http://ubuntuforums.org/showpost.php?p=8959101&postcount=5)  or even repository on my laptop (when i add app package, desktop will update this package as it was at ubuntu repository) after network would be created.

---

