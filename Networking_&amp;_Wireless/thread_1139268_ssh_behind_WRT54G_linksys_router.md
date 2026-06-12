---
title: "ssh behind WRT54G linksys router"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by renkinjutsu on 2009-04-26
i recently set my modem to "bridge mode" hoping that i can set up an SSH server so that i can take care of things while away from home..
but the thing is.. i can't seem to keep my ports opened

i have a WRT54G linksys router with the latest firmware: v4.21.1 

ssh works for a little bit, then after a while, i am returned with a "connection reset" error when i try to connect.
I am still able to ping my IP address on the WAN side, but i can't ssh, so i assume my port is blocked... my only solution right now is to hard reset my router and configure everything again.. but even that isn't a permanent solution, i've tried and it goes haywired again after a couple of hours.

is this a model specific error? or is it time to get a new router?

---

### Post by renkinjutsu on 2009-04-27
i set my router to be a DMZ node for my computer, but even that loses its effect after a few hours..

I notice that whenever my setup doesn't work anymore, my computer has a different IP on the DHCP server.. I can still connect to the internet and I am able to ping my IP.. everything should be fine.. but when i direct my forwarded ports or DMZ to the new DHCP IP, i still can't ssh into my computer.  Hard reseting the router can't be the only option right?

---

### Post by HeegeMcGee on 2009-04-27
It'll be easier to do NAT on the router. You can find HOWTOs out there pretty easy, but this is the general concept. Use this to find more information on google:

1. Give your computer a static IP, outside of the range of IPs used for DHCP. So if your router (or other dhcp server) hands out ips from 192.168.2.100-200, set your computer to 192.168.2.201, .250, .98, etc.
2. Confgure NAT (Network Address Translation) on the router to forward inbound connections on port 22 to port 22 on your ubuntu box. You can use whatever port you want in NAT; i use 922 to reduce the number of nmap / brute force attacks i have to deal with. If you use a nonstandard port, don't forget that you'll have to specify it when setting up your client. 

So, lets say you configure inbound 922 on your router to forward to 192.168.2.99. From work, configure putty to connect to your internet IP address (use DynDNS if you need to) and port 922. The router should pass the inbound connection directly to your ubuntu box.

Also, keep in mind that the WRT54G is a consumer grade router. It's great at splitting the internet up for everybody in your tiny LAN, but if you're going to be doing a lot of custom stuff, you're better off getting something beefier or trying a Shorewall implementation on some old desktop hardware.

Hope that helps.

---

### Post by renkinjutsu on 2009-04-27
that was the first thing i tried actually.. 
i currently have my LAN ip static, my desktop chooses one for itself.
i'm still having problems with my router though, with the ports forwarded to the write IP, i can get good results for maybe a couple of hours, but after that it stops working... and canyouseeme.org reports that my ports are closed (works perfectly before) even though i'm positive i forwarded them correctly

DMZ was my last resort D; .. even that doesn't stay permanent

my lan IP is static, and my router has DynDns support, so my router's IP changing shouldn't be the problem.. 

this is really just so i can manage my desktop when i'm out, or if i want to pull files onto my phone through ftp or whatever... but my ports seem to close automatically after a while.

---

### Post by HeegeMcGee on 2009-04-28
I've got a few WRT54Gs, and i've yet to have a problem like you're having. Here are 3 ways you can go, with varying amounts of effort involved:

1. Buy a new router and see if that fixes the problem. Those wrt54gs are $50 max, and you can get refurbs for $15 if you look hard enough. Maybe you can even get Linksys to replace yours.

2. Packet capture at the server level. Get everything working, then do a tcpdump port 22 on the proper interface. See what happens; you may see that packets simply stop flowing. If this is the issue, you can squarely blame the router. If you see the handshake terminate, you need to check your server configs.

3. Update the firmware on the router. Make sure it's the latest version from linksys, and maybe re-flash just in case. Failing that, give DD-WRT or Tomato a shot.

---

### Post by renkinjutsu on 2009-04-29
i honestly do not know how to follow your procedure, with the tcpdump

but i did notice that my internet disconnects just a little bit and reconnects right before everything stops working..

---

### Post by chadjohnson on 2009-04-30
My server has the same issue with SSH (inside AND outside my network), but I can always connect via FTP.

---

