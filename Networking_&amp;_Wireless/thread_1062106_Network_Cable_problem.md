---
title: "Network Cable problem"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by toothlost on 2009-02-06
Hi... I have a weird problem...[sorry first post on buntu forums]
 
  Because I running my Ubuntu box as a server and because I like wires I have done an ~40 feet long cat5e extension with two female ends wich I use to plug two ethernet wire one into my Asus WL-500g router and into my unbuntu box. I'm using the onboard network card of my Asus M3N78-VM.

 
   So here is the problem: I'm not able to connect my Ubuntu to my router... sometimes it won't even recognized the network or it will recognized but it won't connect. It's like not able to assign an ip... I hope I'm missing a little something here...

Here is a few interesting facts

1 - I can connect my XP laptop to that long wire and network will work perfectly.

2 - If I plug my box directly into the router, it will work.

3 - I have put a 3com network card in and tried it but it never worked (the card was recognized).

4 - I have run this box for 2 - 3 weeks with a dollars store ethernet extension plug directly into the router and it has been perfect...
 
 
       So if you have any idea... I would really appreciate your help... 

       I thought the next step would be to install an another os(Winnie-dose) but if I could stay away from that my forehead would really appreciate...
 
            Thank you...

---

### Post by puppywhacker on 2009-02-06
using 3 wires for ethernet patching may work fine, or it may cause interference. e.g. when the cable runs close to power cables. That your laptop is working is a good sign, but your asus onboard network card may be less sensitive. In general a computer to a router should require straight utp cables (green to green and orange to orange). Your laptop may support switching to crossover, while your computer doesn't

Ok, so on your router you should have a green light when somehthing is plugged in into the port. Your computers network plug should light green aswell.

the command "mii-tool" In linux checks if the ethernetspeed has been negotiated, and you can also force your server into a mode. 10Base-FD is a good slow speed, which should work.

ifconfig should show the device sent TX and received RX some packets

next you should be abled to set an ip-address in your router in the same range as your router and try firefox to browse to your router

sudo ifconfig eth0 inet 192.168.1.2
[http://192.168.1.1/](http://192.168.1.1/)

if you get to see a login page you know you can connect. So you can try to retrieve an dhcp address directly.

sudo dhclient eth0

---

### Post by toothlost on 2009-02-06
I'm going with the 'less sensitive' opinion on that too...

I'll double check my colors orders and I'll have a look at blinking lights... I don't really remember if the router was blinking... Then I'll read on "mii-tool"
 
actually I'll try your tools and command lines you gave me and I'll come back on that.. 

tkx

---

### Post by cariboo on 2009-02-06
I have essentially the same setup, although the cable is actually 4 conductors fo an eight conductor telephone line. My cable runs from a linksys router to an SMC router converted to a wireless access point and then to an 8 port unmanaged switch. There is a crossover cable between the AP and the switch. When using connectors make sure the the wires match. In a lot of cases even if the cabling is wrong the connect lights will light up, so that really isn't a good indicator.

Jim

---

### Post by toothlost on 2009-02-08
Thanks for replying...
 
    First,
 
             I didn't plug the wires the right way as I didn't know that for the interference importance of the twisted pair... now, the patch (with both female) works but it seems that I have a problem with one of the other patch cable. So I just bought on ebay for 15$ CAD and I'll see if it fixed all my problems...

  Thanks again... I'll close the thread once It will be fixed (I hope duh)...

---

### Post by toothlost on 2009-02-27
Yeap... 

 with a 50 feet long ethernet cat5e cable bougth on Ebay for less then 20$ CAD, everything works fine...

thanks for the time...

---

