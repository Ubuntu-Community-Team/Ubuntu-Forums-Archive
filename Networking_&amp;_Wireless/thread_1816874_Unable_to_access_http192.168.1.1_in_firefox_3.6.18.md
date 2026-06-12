---
title: "Unable to access http://192.168.1.1 in firefox 3.6.18"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by arroy_0209 on 2011-08-02
In ubuntu 10.04 LTS I am currently unable to access the location [http://192.168.1.1](http://192.168.1.1) I have accessed it earlier. This is necessary for modem configuration. I am at a loss why this is inaccessible at present. Can anybody please advise what to do? I am configuring firewall but I doubt if that has anything to do with my problem. Or in case this may be due to faulty firewall configuration, please indicate denial of possible service/program which may cause this.   Also ping 192.168.1.1 reports 100% packet loss. What do I conclude?

---

### Post by wildmanne39 on 2011-08-02
Hi, it might should be 192.168.0.1

---

### Post by Iowan on 2011-08-02
From a terminal (Applications>Accessories>Terminal), you can use **ifconfig -a** to see what IP address the computer has. The modem *should* be in the same subnet. 

Alternately, System>Administration>Network Tools can be used to check the IP address of your interface (eth0?)

---

### Post by arroy_0209 on 2011-08-02
Thanks for your attention. 
Here is the result of ifcinfig -a. 

***************************************************************
eth0      Link encap:Ethernet  HWaddr 00:21:85:91:5a:43  
          inet6 addr: fe80::221:85ff:fe91:5a43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2463370 (2.4 MB)  TX bytes:309412 (309.4 KB)
          Interrupt:25 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14961 (14.9 KB)  TX bytes:14961 (14.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.194.35.75  P-t-P:117.194.32.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:6775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2307916 (2.3 MB)  TX bytes:269372 (269.3 KB)

***********************************************************
I have tried to load all of these one by one but failed: [http://117.194.35.75](http://117.194.35.75), 117.194.32.1, 255.255.255.255, 127.0.0.1, 255.0.0.0

So the problem remains.

---

### Post by Furball588 on 2011-08-02
I don't see an IPV4 address in there.  

That first set should have an inet addr entry like you see in the second (Local Loopback  )

Only suggestion I can think of is to manually set an IP of 192.168.1.2 with a subnet of 255.255.255.0 or reset your router (wihch I assume is what's handing out your address), but this would also reset any changes you made at that router.

---

### Post by dineshs on 2011-08-03
How do you connect to internet ? Using network manager DSL connection or running *pon* command in terminal?
If you are using network manager, disconnect DSL connection first , connect eth0 and try again.If there is no luck please run ```
sudo dhclient eth0
```and retry.

---

### Post by arroy_0209 on 2011-08-03
Thanks. The sudo command really solved the problem. Here is the report of the sudo dhclient eth0 command:
*************************************************
Listening on LPF/eth0/00:21:85:91:5a:43
Sending on   LPF/eth0/00:21:85:91:5a:43
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.9 from 192.168.1.1
DHCPREQUEST of 192.168.1.9 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.9 from 192.168.1.1
bound to 192.168.1.9 -- renewal in 34206 seconds.
***************************************************
Though surprisingly just after running the command, I was able to connect to 192.168.1.1, I was unable to access Internet. After I restarted modem, I was able to access both. Can anybody please check if the above statements are Ok or not. (I am yet to learn these issues.)

Regarding the question, how I connect to net: I run the command sudo pon dsl-provider in terminal. I am not sure why you asked but this info may help you. By the way, I use BSNL broadband and I used these commands when I configured modem:

sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.16.1.1 eth0
sudo pppoeconf

Then followed the instructions appeared. Did I do things right or was there any problem? 
Thanks a lot to everybody for your attention to my problem.

---

### Post by Furball588 on 2011-08-03
I think he was just asking if your modem was setup as a bridge or something else.  How you connect pretty much tells everyone what your modem is supposed to do.  I don't think I've ever had a need myself to use either pon or pppoeconf, but I know there's situations that require it..and admittedly, these things get over-thought a lot too. 

I think you're good with what you did.  I expect the output from ifconfig now to show 

eth0 Link encap:Ethernet HWaddr 00:21:85:91:5a:43 
inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0

and setting the gateway like you did (to 192.168.1.1) is telling your PC where to go look for the internet.  

I assume you're still seeing the internet and able to hit 192.168.1.1?

---

### Post by dineshs on 2011-08-04
> I think he was just asking if your modem was setup as a bridge or something elseFurball588 is right.
arroy_0209,
You can configure your modem in bridge mode or PPPoE mode.If your modem is in bridge mode you need to create a pppoe connection in your PC to connect/disconnect broadband.There are two methods
1)The terminal method
Run [COLOR="Blue"]sudo pppoeconf[/COLOR] command to create the connection.Then connect using [COLOR="blue"]pon dsl-provider[/COLOR] (disconnect using [COLOR="blue"]poff dsl-provider[/COLOR])
2)GUI method(At present your modem is in bridge mode and you are using terminal method to connect/disconnect but I suggest you try this)
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
If you want to access your modem,disconnect dsl connection then connect eth0 and proceed(Ensure this:click network manager icon on right top of the panel-edit connections-select eth under wired tab-edit-ipv4 settings-method=Automatic DHCP and apply.
If your modem is in PPPoE mode the internet connection will be always ON.Also you can access modem directly via firefox.Configuring different modems in PPPoE mode is explained [here]("http://ernakulam.sancharnet.in/ernakulam/bbservice.html") under CPE/modem config

---

