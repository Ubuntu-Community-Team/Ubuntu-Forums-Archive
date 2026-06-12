---
title: "Terminal Service Client SLOW over VPN"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by adrian.h on 2011-02-07
Hi, I was trying to connect to my machine over the internet through a VPN.  I was able to connect, with a fairly high ping (30-40 ms), then when I use Terminal Service Client to connect, just the login screen takes FOREVER!!  Using a Virtualbox WinXP, I connect to the VPN and use its Remote Desktop and it is super fast.  Any idea why the discrepancy?  Is there some settings I should be setting?

Thanks,

A

---

### Post by Kirboosy on 2011-02-07
30-40 ping shouldn't be that slow...I wonder if you ran a speed test on your internet how good it would be. You might not have the bandwidth to have a good connection.

[http://speedtest.net/](http://speedtest.net/)

---

### Post by adrian.h on 2011-02-07
BTW, I am using 9.10 Karmic Koala, PPTP, disabled all authentication except MSCHAPv2 and have tried using all manner of combinations of selection of checkboxes under Security and Compression.

I've tried RPD, RPDv5 with no noticeable difference.

Also, when using the VPN and Terminal Service Client, I've noticed my Skype connection goes in and out sometimes.  Not sure if that means anything.

Thanks,


A

---

### Post by adrian.h on 2011-02-07
Oh VPN also it fracks up my internet connection.  Makes it go slower than molasses. :(

---

### Post by adrian.h on 2011-02-07
> **Caboose885 said:**
> 30-40 ping shouldn't be that slow...I wonder if you ran a speed test on your internet how good it would be. You might not have the bandwidth to have a good connection.

[http://speedtest.net/](http://speedtest.net/)
No, that is why I said it works great under the VBOX WinXP.  This is running WITHIN my Ubuntu.

---

### Post by Kirboosy on 2011-02-07
You are using OpenVPN correct?

Also what ports did you forward for VPN?

---

### Post by adrian.h on 2011-02-07
> **Caboose885 said:**
> You are using OpenVPN correct?

Also what ports did you forward for VPN?
Um, isn't that Ciccos?  I'm using "Point-to-Point Tunneling Protocol (PPTP)" which is "Compatible with Microsoft and other PPTP VPN servers".

As for what ports...?  I have no idea... actually, I'm not entirely sure what you are asking.

---

### Post by Kirboosy on 2011-02-07
Well there are ports and protocols that you have to forward to the VPN Server in order for things to work properly. IF you didn't forward things properly then that it a big reason why your VPN isn't working correctly.

If it's **PPTP **then you will need to forward TCP/1723, and Protocol 47 (GRE)

For **IPSEC **you will need UDP/500 and Protocol 50 (ESP)

---

### Post by adrian.h on 2011-02-07
> **Caboose885 said:**
> Well there are ports and protocols that you have to forward to the VPN Server in order for things to work properly. IF you didn't forward things properly then that it a big reason why your VPN isn't working correctly.

If it's **PPTP **then you will need to forward TCP/1723, and Protocol 47 (GRE)

For **IPSEC **you will need UDP/500 and Protocol 50 (ESP)
How do I do this?  Don't recall seeing anything about this when looking into VPN.

---

### Post by Kirboosy on 2011-02-07
You have to log into the router. There should be a section in the router for forwarding ports and protocols.

---

### Post by adrian.h on 2011-02-07
But why would I need to do this?  On XP this is not necessary and it is on the same network as this linux box and there is no problem what so ever.

---

### Post by Kirboosy on 2011-02-07
Oh...well I guess Cisco VPN is different than Open VPN. I'm not really sure. 

I just know from my experiance with VPN I had to forward ports. Maybe someone else has a suggestion.


Local connections are different that Internet connections.

---

### Post by adrian.h on 2011-02-07
Oh, yeah, Cisco is quite different.  I am not using Cisco, I'm using the MS VPN.  But thanks for the help.

If anyone else has any ideas, that would be great!

Thanks,


A

---

### Post by Artur Oliveira on 2012-10-28
Hi,

Exact same question here ... I'm struggling with these for years ...

I believe the problem is with the RDP implemention on Linux.

I start the VPN and I have a very good response from the server that I want to connect  to (15 ms) but any time I start the connection using or Remmina or 
remote Desktop Viewer the ICMP response increase to 450 to 500 ms and keep 
on these values during all the time that I have the RDP connection established.

The RDP Linux implementation "eat" the available bandwidth.

As focused, and I already make the same experience, if using a XP VM on same Linux machine that I have the prob, RDP is lightning fast so the problem isn't in the network itself nor the port fowarding config at router level as suggested.

Also I already use the same Linux machine using RDP directly on LAN (without VPN) where the Server that I want connect lives. Of course the connection is faster because I have 100 Mbps available but sluggish that a native XP to 2003 RDP connection.

Since I need a reliable RDP/VPN I still to continue to use and keep a  Windows machine to do the job in a workable way...

All the Best

---

