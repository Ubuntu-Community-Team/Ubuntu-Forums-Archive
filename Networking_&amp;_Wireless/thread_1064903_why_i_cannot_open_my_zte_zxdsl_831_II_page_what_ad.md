---
title: "why i cannot open my zte zxdsl 831 II page? what address i should try?"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by q.dinar on 2009-02-09
hello.
why i cannot open my zte zxdsl 831 II page? what address i should try?
i tried to open [http://192.168.1.1/](http://192.168.1.1/) and ip address that is in "ifconfig ppp0" command's output.

---

### Post by dmizer on 2009-02-09
Before you can configure your modem, you'll have to make sure the router portion of your modem is handing you an IP address. Please post the output of:
```
ifconfig
```

---

### Post by q.dinar on 2009-02-10
```
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:b6:fd:c4  
          inet6 addr: fe80::20c:6eff:feb6:fdc4/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          &#1042;&#1042;&#1045;&#1056;&#1061; BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:581799 errors:1 dropped:0 overruns:0 frame:0
          TX packets:10180 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:215934834 (215.9 MB)  TX bytes:4209529 (4.2 MB)
          &#1055;&#1088;&#1077;&#1088;&#1074;&#1072;&#1085;&#1086;:22 Base address:0xe000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1059;&#1079;&#1077;&#1083;
          &#1042;&#1042;&#1045;&#1056;&#1061; LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28492 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:0 
          RX bytes:26107727 (26.1 MB)  TX bytes:26107727 (26.1 MB)

ppp0      Link encap:&#1055;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083; PPP (Point-to-Point Protocol)  
          inet addr:89.232.85.48  P-t-P:192.168.228.9  Mask:255.255.255.255
          &#1042;&#1042;&#1045;&#1056;&#1061; POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:7973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7926 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:3 
          RX bytes:2929686 (2.9 MB)  TX bytes:3960469 (3.9 MB)
```

---

### Post by dmizer on 2009-02-10
You probably won't be able to access your modem config page while you are connected to the internet. You should disconnect, and set a static IP of 192.168.1.100 for eth0. Then you should be able to access your modem config page at 192.168.1.1

---

### Post by q.dinar on 2009-02-12
thank you. i have not yet tried this. i do not need it now so much and do not want disconnect, i will try some day at time of day when no site visitors.
when i will do this:
"You should disconnect, and set a static IP of 192.168.1.100 for eth0."
i know that i will disconnect with "poff dsl-provider", i do not know how to do "set a static IP of 192.168.1.100 for eth0".

why i have wanted to connect to my adsl modem: i wanted to configure it for security, if possible, to configure its firewall features, and one day i thought may be it help to make torrent client working with configuring "forward" but i have made it without that, as i know it configures modem itself with "upnp" technology. by the way i have a question: should(must) something (ports) be opened in iptables for "upnp" can work?

---

### Post by superprash2003 on 2009-02-12
you could also try getting an ip by typing **sudo dhclient eth0**

---

### Post by q.dinar on 2009-04-10
hello.

is it possible to configure this modem so that it sends text like "this server is shut down till 5 am" when computer to that it is connected is shut down?

i have not tried to configure this modem yet.

---

### Post by q.dinar on 2009-12-23
i have tried now. i have opened 192.168.1.1 in browser, it just waits and waits.

---

### Post by q.dinar on 2011-12-09
i also had asked about this in [http://ubuntuforums.org/showthread.php?t=1053271](http://ubuntuforums.org/showthread.php?t=1053271) but was no answer but there is link to page with login and password.

today i have tried and managed to do this. but login and password from [http://smartinfo.com.my/IT/PC_Hardware/TM_Net_Streamyx_ZTE_ZXDXL_831_Modem.htm](http://smartinfo.com.my/IT/PC_Hardware/TM_Net_Streamyx_ZTE_ZXDXL_831_Modem.htm) do not work, even if i reset modem. i think it indeed was reset because i could not open 192.168.1.1 temporarily after i pressed that button.

i set 192.168.100 to eth1 this way:
sudo ifconfig eth1 192.168.1.100
then
sudo ifconfig eth1 0.0.0.0
to remove it.

so, this is whole my way:
sudo poff dsl-provider
sudo ifconfig
sudo ifconfig eth1 192.168.1.100
open 192.168.1.1 in browser, try to login
reset modem
try to login
sudo ifconfig eth1 0.0.0.0
sudo pon dsl-provider

---

### Post by q.dinar on 2011-12-09
i need not not to turn off ppp!

just

sudo ifconfig eth1 192.168.1.100
open 192.168.1.1
and it works and ping google.com works.

and there are other pasword in [http://broadbandforum.in/bsnl-broadband/20261-bsnl-broadband-zte-zxdsl-831aii/](http://broadbandforum.in/bsnl-broadband/20261-bsnl-broadband-zte-zxdsl-831aii/) .

---

### Post by q.dinar on 2011-12-09
username "admin" and password "admin" works.

---

