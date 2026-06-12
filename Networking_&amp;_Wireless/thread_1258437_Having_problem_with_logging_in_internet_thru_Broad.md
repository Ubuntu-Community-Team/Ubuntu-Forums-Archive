---
title: "Having problem with logging in internet thru BroadBand line"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by Mahbub on 2009-09-05
[SIZE=3]Having problem with logging in internet thru BroadBand line. I configured my broadband connection manually and followed UbntuPocketGuide for it. Tested the connection using network information and it replied well. It shows the sending and receiving bits accordingly. But the browser doesnt open any web page. I'm all new in Ubuntu. Can anyone help me.[/SIZE]

---

### Post by lisati on 2009-09-05
Which browser are you using? Does it show a start page?

---

### Post by jnorthr on 2009-09-05
can you open a terminal session window ? That is where we enter our commands for playing with the system internals. Think it's an icon off the 'accessories' submenu.
Once there you can type in various commands. 
Type [COLOR="YellowGreen"]**ifconfig**[/COLOR] on a command line and press return. It will show something like this:

:ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
	inet 127.0.0.1 netmask 0xff000000 
	inet6 ::1 prefixlen 128 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet 192.168.2.1 netmask 0xffffff00 broadcast 192.168.2.255
	ether 00:19:e3:44:4d:66 
	media: autoselect status: inactive
	supported media: autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 10baseT/UTP <full-duplex,flow-control> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback> 100baseTX <full-duplex,flow-control> 1000baseT <full-duplex> 1000baseT <full-duplex,hw-loopback> 1000baseT <full-duplex,flow-control> none
fw0: flags=8802<BROADCAST,SIMPLEX,MULTICAST> mtu 2030
	lladdr 00:1c:b3:ff:fe:83:23:6a 
	media: autoselect <full-duplex> status: inactive
	supported media: autoselect <full-duplex>

then you can see the various settings under the hatch. You can also try the 'ping' command to various internet addresses. try 'ping 127.0.0.1' without quotes. this confirms your internal network within the o/s is working correctly. from there we can diagnose other issues. 

Hang in there - you'll love ubuntu once you reach full throttle :D

---

### Post by Mahbub on 2009-09-05
using firefox.

---

### Post by Mahbub on 2009-09-05
No, I dont know much about terminal session window, I'll try it now. I tested ping  and it replied accordingly. should I try localhost address 127.0.0.1 instead of my IP address ?

---

### Post by Mahbub on 2009-09-05
Yes I followed your instruction and got terminal window working. But how can I print or present it for you to see since I'm a dual user of Xp/Ubuntu at the same machine ?  I dont understand anything of the session. it shows *etho/ lo* connection. I guess I use *etho* ( ethernet) not *lo* (loop). can u help ?

---

### Post by Mahbub on 2009-09-05
I opened terminal window to see the result of ifconfig command. But how can I show it in the thread ? It shows  2 catagories eth0 and lo. I guess I'm using eth0 (ethernet). It gave no errors. ping result it ok, giving replies accordingly. But still suffering to get to the net.

---

### Post by shredder12 on 2009-09-05
> **Mahbub said:**
> Yes I followed your instruction and got terminal window working. But how can I print or present it for you to see since I'm a dual user of Xp/Ubuntu at the same machine ? 

why don't you copy all that you need in a file and keep it in your shared partition..
go to "Places"  there you will see all your disk partitions and you can place ur file there and access it thru windows and paste it here..

---

### Post by Mahbub on 2009-09-07
This doesn't work. If I copy the file and paste it on the ubuntu desktop and then try to move it to a shared directory such as d: or e: or f: it doesnt work. Is there any other way to do it ?
 Anyway, I was looking forward to get a solution about problems in internet browsing through Broadband connection. Can anyone pull me out ?

---

### Post by Mahbub on 2009-09-07
[SIZE=3]Still Having problem with browsing internet thru BroadBand connect.. I configured my broadband connection manually and followed UbntuPocketGuide for it. Tested the connection using network information and it replied well. Ping[/SIZE] [SIZE=3]shows the sending and receiving bits accordingly. But the browser  (firefox) doesn't open any web page. It just shows Ubuntu help as start page. I tried terminal window but couldn't understand anything from it. it shows  eth0 and lo catagories.I guess I'm using ethernet. I'm all new in Ubuntu and know very little about networking. Can anyone help me.[/SIZE]

---

### Post by shredder12 on 2009-09-07
Even though you are connected to internet you might be having issue with resolving hosts (names not getting converted into IPs).
Run this command in your terminal and see if you get some replies..
```
ping google.com
```

---

### Post by Mahbub on 2009-09-08
[SIZE=3]Unfortunately I followed the following commands-

[SIZE=2]cat /etc/network/interfaces
sudo infonfig eht0 up
sudo dhclient eth0
sudo lhw -c network

I was put in rather worse situation and not getting any ping replies now.... here is the  result of ifconfig command


[/SIZE][/SIZE]@mahbub-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:ea:fc:e0:64  
          inet6 addr: fe80::20f:eaff:fefc:e064/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3685128 (3.5 MB)  TX bytes:35032 (34.2 KB)
          Interrupt:20 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62516 (61.0 KB)  TX bytes:62516 (61.0 KB)

Here are the output of Network toos-  can anyone help come out with the problem ?


[SIZE=3][SIZE=2][IMG]http://ubuntuforums.org/attachment.php?attachmentid=127909&stc=1&d=1252432087[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=127910&stc=1&d=1252432087[/IMG]
[/SIZE]
[/SIZE]

---

### Post by shredder12 on 2009-09-09
I think unable to access internet after running those command is just a temporary issue.. Restart your system and you will be fine. 

Many a times unable to browse is an IPv6 issue.. I don't know the exact reason but probably turning it off in your browser might help.

before that you might want to check.. if you have IPv6 enabled in your machine..
enter this command in your terminal

```
lsmod | grep inet6
```

if there is no output then probably it is not an IPv6 problem but if there is an output then post it and proceed down to fix it in our browser

open firefox.. in the URL bar write  "about:config" and press enter.
then in the filter bar.. enter this

"network.dns.disableIPv6"
it will filter out a single result
double click on it and turn the value to "true"

then try opening a website in firefox..
if it doesn't work.. then try restarting firefox..

I hope it helps..

---

### Post by Mahbub on 2009-09-15
Shredder,  I followed your instruction lsmod | grep inet6to check IPv6 . But it didnt give any result except the command prompt. So it's not an IPv6 issue. Although I dont understand what it refers to, I can give some more info for those who can help to overcome this helpless situation.... everything shows that the connection is active and fine but bowser doesnt open any page....... here is the network information window shows when I open Ubuntu, ( network device : loopback is shown untill I manually change it to ethernet)_

Network device:    eth0
Hardware address:    00:0f:ea:fc:e0:64
IP address:    192.168.1.145
Netmask:    255.255.255.0
Broadcast:    192.168.1.255
Multicast:    Enabled
MTU:    1500
Link speed:    not available
State:    Active
Transmitted packets:    54
Transmission errors:    0
Received packets:    78393
Reception errors:    0
Collisions:    0


Network device:    lo
Hardware address:    Loopback
IP address:    127.0.0.1
Netmask:    255.0.0.0
Broadcast:     
Multicast:    Disabled
MTU:    16436
Link speed:     
State:    Active
Transmitted packets:    1020
Transmission errors:    0
Received packets:    1020
Reception errors:    0
Collisions:    0

:( can anyone solve this problem, I'm really at my wits end..

---

### Post by shredder12 on 2009-09-16
Has any one suggested you to change the mtu values 
have a look at this article...

[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

Now, one more thing.. still try toggling the IPv6 disable value (as i mentioned in the last post)

and have you tried using another browser..
(konqueror, opera etc.)

---

### Post by Mahbub on 2009-09-18
Nobody suggested to or I didn't change any MTU value, in fact I even dont know wht it refers to. Neither I tried other than firefox browser. should I try ? I'll follow your last post and let you know the latest result soon. Well, I couldnt try other features of Ubuntu because of this hotchpotch situation with net connection. 
Thank you.

---

### Post by shredder12 on 2009-09-18
Actually I too don't know much about MTU values.. I was googled a bit for your problem and found a solution where changing the values fixed a guy's problem who was having a similar "unable to browse" problem..

It probably means the max. packet size that can be transmitted on a network..

---

### Post by Mahbub on 2009-09-18
I went through the website about MTU. I can follow it . I'll let you know

---

### Post by Mahbub on 2009-09-19
Shredder12, I followed the steps to change the MTU value to 1450 first and then 1200 but got no positive result about the problem. ifconfig command shows the changed MTU value quite ok. But still running out of network. And how can i change the browser. 
Thank you.

---

### Post by shredder12 on 2009-09-19
Well, I really don't know the solution to ur problem..
but I hope using other browswers work for you..

You can try Opera, Netscape navigator, Konqueror..
You will probably have to download packages of Opera and Netscape from their native sites but konqueror can be downloaded and installed through the repos..

run this command
```
sudo apt-get install konqueror
```

---

