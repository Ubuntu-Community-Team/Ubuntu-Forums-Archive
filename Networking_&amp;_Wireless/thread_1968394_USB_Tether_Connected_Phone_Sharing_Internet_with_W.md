---
title: "USB Tether Connected Phone Sharing Internet with Wired Network"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by cwwilson721 on 2012-04-29
Let me explain my setup (LAN-wise), and what I wanted todo.

My "main" Ubuntu box is connected to a LAN thru Ethernet to a WiFi router, and the rest of the LAN connects to the router (wired and wireless, computers, Tablets, Phones). I usually have a working Cable Internet connection, and all this runs fine. My main box also does not have WiFi.

Recently, my modem stopped working, and would be a week/two weeks to get another (gotta love cheap/small ISPs). I have a Android phone running Froyo (2.2), and it was REAL simple to tether this to my main box. I also have the option of "wifi tethering" the phone, thru a ad-hoc network. However, I couldn't do both at the same time. Plus, I use repeater access points on the WiFi portion of my LAN, and the remote computers cannot connect to the phone.

So, how to have my phone USB tethered to my main box, and still share this connection thru my already-tuned/working LAN?

After much searching, I finally combined many articles (and figured out WHY they were saying what they were saying).

I first started out by "sharing" the ethernet connection on my main (Rt clicking on Network Manager, edit the ethernet connection, then IPv4, "Shared to other computers". IPv6 was already set to "ignore"). All fine and dandy, but nobody was getting Internet except my main. So that didn't work.

All the "how-tos" I found kept mentioning "..setup a DHCP server..". Why? My router does a FINE job. It gives out selected IPs to MACS that I choose, port forwards, everything. So why do I need a DHCP server?

Then I had a "lightbulb" moment. DUH! THE REST OF THE NETWORK DID NOT KNOW THAT ETHERNET CONNECTION WAS THE GATEWAY IP! Nor, on my router, was there an "easy" way to do this. So the simple solution: [COLOR="Red"]Connect the ethernet cable to the Internet port on the router! With the "Shared to other computers" selected on that connection, all the other computers can now have Internet.[/COLOR] (Luckily, I have 2 ethernet ports on my box).

I know. Simple, right? 

So here it is:
[LIST]
[*]Connect USB tethered Phone (or any type of Internet connection, be it a Cell Dongle, built-in 3g/4g, USB Modem, whatever), and make sure you can get on the Internet with that connection (sometimes, you have to disable all other LAN connections for it to work)
[*]Connect ethernet from computer to Internet Port on Router
[*]Go to Network Manager > Edit Connections > Ethernet you just connected > IPv4 tab > Dropdown box change to "Shared to other computers"
[*]IPv6 Tab set to "Ignore" (You may need to go to a terminal, and type "sudo killall dnsmasq".)
[*]Back out, enable that connection, and you're all set.
[/LIST]

It's that easy.

One small issue on my setup: I can't have a "regular" connection to my LAN at the same time (won't get Internet on my main if I do so). I know it's something stupid on my end, and I'll figure it out. In the meantime, I just leave it disabled. If I need to admin routers/etc, I just re-enable it, and temp disable the "internet" connection. I'll post if/when I get it straight.

---

### Post by Con89roe on 2012-06-03
Thank You So Much For The Help been spending days googling this any update on how to enable LAN while doing this again TY SO MUCH

---

### Post by cwwilson721 on 2012-06-03
Not yet. My new modem came in, so I haven't dealt with this issue lately.

I'll look into it when I have some time, but for now, work and family stuff comes first.

---

### Post by Con89roe on 2012-06-04
indeed tys for the update ill be keeping my eyes open for update when available thanks again

---

