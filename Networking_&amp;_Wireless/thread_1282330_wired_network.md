---
title: "wired network"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2009-10-04
hi ppl hav been using ubutu 9.04 for about 3 weeks now. i'm havin problems with networkin as it seems all newcomers are, I hav 1 laptop runing on net ok using a mobile dongle from 3. i now need to connect my 2nd laptop via ethernet cable so as to use net as well both machines hav ubuntu 9.04 on them, i wld appreciate some help in setting this up plz

---

### Post by Bölvaður on 2009-10-04
> **spiky001 said:**
>  i now need to connect my 2nd laptop via ethernet cable

[LIST=2]
[*]Get the cable
[*]Plug it in to the computer.
[*]Right click on the internet sign, in the notification area
[*]Take the mark sign off the wireless box
[/LIST]

if it works you are done.
if it doesnt continue:

[LIST=4]
[*]right click on the internet sign, in the notification area
[*]press *edit connection*
[*]under wired, edit the currect setup.
[*]go to IPv4 settings
[*]Change method to *automatic (DHCP)*
[*]Click *Apply*
[/LIST]

If that didnt work you should play around with the settings and get to know from your ISP which settings to change.

---

### Post by spiky001 on 2009-10-04
no this dosn't work both machines set to automatic on ipv4 (eth0)

---

### Post by spiky001 on 2009-10-04
hi guys can any1 help

---

### Post by ikisham on 2009-10-04
That may be some idiosyncrasy of your Internet provider. Say its name and maybe someone that uses it may tell you how to enable it.

---

### Post by spiky001 on 2009-10-04
ok  i hav a usb dongle from the 3 network, just that when i used it with winows b4 switching it al worked ok, i know things run different on ths system, i ned to use 1 laptop as a gateway so the other can use  the net as well

---

### Post by hal10000 on 2009-10-04
> i now need to connect my 2nd laptop via ethernet cable
Where does the cable go to? Directly to your dsl modem or to a router box or what else?
Is your ethernet card recognized by ubuntu (you can verify this with [COLOR="Red"]lspci[/COLOR]). Some cards can be deactivated in the BIOS

> no this dosn't work both machines set to automatic on ipv4 (eth0)
what exactly does not work? Can you post a screen image or some more information?

---

### Post by ikisham on 2009-10-04
I get it. spiky001 wants to connect one laptop to the other through an ethernet cable to share the connection.
If it's that what you want I think you can't do it. I think that what you can do is download any files in the computer with the 3g connection and transfer them to the other one.
You can even do this with files to upgrade your system since Synaptic has this feature.
(but I don't know how to do the transfer of files since I have just one pc)

---

### Post by antony.s on 2009-10-04
It should be very possible.  internet - laptop1 - laptop2  spiky001, when you connect laptop1 to laptop2, does ubuntu recognise a connection on both laptops?  If so, did each laptop get an IP address for this connection?  You should be able to see this by right clicking on the network icon in the top right and "connection information". Please tell us the IPs here.

---

### Post by spiky001 on 2009-10-04
sort  of ikisham, i just need both machines to be able to use internet at once, normally in windows i get the ip addres of gateway pc then just fix static ip on 2nd pc just that on ths system i dont hav an ip address on etho just mac address



eth0      Link encap:Ethernet  HWaddr 00:14:22:a8:19:bf  
          inet6 addr: fe80::214:22ff:fea8:19bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2222 (2.2 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:b7:b0:a8  
          inet6 addr: fe80::216:6fff:feb7:b0a8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:84 (84.0 B)
          Interrupt:17 Base address:0xe000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:94.196.208.56  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1440  Metric:1
          RX packets:3993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4626664 (4.6 MB)  TX bytes:489266 (489.2 KB)

hope this can help coz i need it

---

### Post by antony.s on 2009-10-04
Ah, so you already know the principle of what you need to do :) 

Knowing that, you should be able to do everything through the network manager gui    

First, sudo apt-get install dnsmasq-base    (on laptop1)

Then on laptop1, edit the ethernet connection with laptop2 and set it to "shared with other computers" like in this screenshot, [http://jeremy.visser.name/wordpress/wp-content/uploads/2009/03/nm-nat.png](http://jeremy.visser.name/wordpress/wp-content/uploads/2009/03/nm-nat.png)    

Set the internet connect on laptop2 to automatic/dhcp    

I believe that should do it

---

### Post by spiky001 on 2009-10-04
i,m on it will let u  know how it all gose

---

### Post by spiky001 on 2009-10-04
o anthoney done that it said i had the latest verson of that, but changed the settings in laptop1 which is on the net to share with other computers but still un able to make the connection

---

### Post by antony.s on 2009-10-04
Can you post the output of ifconfig on laptop2?

---

### Post by spiky001 on 2009-10-04
this is ifconfig laptop2

  	 	 	 	 	 	   eth0      Link encap:Ethernet  HWaddr 00:08:74:3e:97:f0   
           inet6 addr: fe80::208:74ff:fe3e:97f0/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:10 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:11 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:1836 (1.8 KB)  TX bytes:2178 (2.1 KB) 
           Interrupt:11 Base address:0xac00  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:648 (648.0 B)  TX bytes:648 (648.0 B) 
  
 pan0      Link encap:Ethernet  HWaddr 8a:45:3f:1a:f9:4d   
           BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 



cheers antoney

---

### Post by spiky001 on 2009-10-04
hav been looking through the network forum, wld i be btter fixing an ip address on laptop1 wld this help?

---

### Post by antony.s on 2009-10-04
I suppose so

The "shared with other computers" thing is supposed to do that and dhcp for laptop2, but I'm not able to test it myself

But.. as that doesn't seem to be working, set a static ip for laptop1 and another for laptop2, set the gateway of laptop2 to laptop1 and see what happens!

---

### Post by spiky001 on 2009-10-04
Hi ppl i hav a problem i wld like to solve hope u can help, i hav osted this in the beginers section but still unable to solve. I hav 2 laptops whch i want to use on the net at the same tie both using ubuntu 9.04 laptop1 is connected to net with a usb dongle from the 3 company all works well there. i now need laptop 2 to conect via etheret cable to 1st laptop & sare the same connection plz help

---

### Post by Iowan on 2009-10-04
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for connection sharing. Maybe you've already seen it.

---

### Post by cariboo on 2009-10-04
Please don't double post on the same subject. threads merged.

---

### Post by spiky001 on 2009-10-04
sorry about double posting

---

### Post by spiky001 on 2009-10-04
i followed the link iowan put hav now got 2 laptops connected,but got lost with the code eth1 will that still be the same for a usb connection, & also the ip address i put in changed? but we hav made some progress any advice

---

