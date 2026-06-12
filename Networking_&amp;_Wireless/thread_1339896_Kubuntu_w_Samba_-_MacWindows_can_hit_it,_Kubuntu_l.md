---
title: "Kubuntu w/ Samba - Mac/Windows can hit it, Kubuntu laptop cannot."
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-11-28
I have a Kubuntu 9.04 desktop running Samba. My windows and mac computers can hit the server and browse accordingly, but my Kubuntu work laptop cannot. 

What do I need to do in Kubuntu to see my server? I open Dolphin and hit network and I see Samba shares there. I double click it, and I see nothing.

How do I connect to my Samba server?

---

### Post by Roasted on 2009-11-28
Fixed.

Turns out it was a problem with the way I had my networking settings set up.

You see, my laptop running Kubuntu is primarily for imaging computers at work using FOG, an open source free imaging program for imaging Windows computers. FOG requires a static IP, so as of 2 weeks ago when Ubuntu was on this laptop, I just edited the network interface file so it was static to IP address 192.168.1.100 and netmask was 255.255.255.0. I didn't use a gateway since I was plugging into a switch on my desk and that was it. No external access needed. That worked for about a year with Ubuntu just fine.

So here I am curious with KDE and now I'm firing out Kubuntu on all of my computers, including my work laptop that's used for FOG. So, again, I edit the network interface file to be identical to what I used on Ubuntu, and something went wrong. I left wireless alone, so I can connect with DHCP just fine. But I couldn't connect to my gateway at home, proof I had a problem. So I commented out the settings in the network interface file, rebooted, and presto - Samba is back online.

So, my Samba problem is fixed, but it doesn't clear my head as to what was wrong. Why? Like I said, I had this same exact setup with Ubuntu and I had no issues. Yet with Kubuntu I do. Yet I know enough about Linux to really feel strongly that it's not a Kubuntu/Ubuntu difference here. These are networking problems and networking questions, not desktop environment questions.

Confused...

---

