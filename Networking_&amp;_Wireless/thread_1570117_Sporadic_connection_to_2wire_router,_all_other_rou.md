---
title: "Sporadic connection to 2wire router, all other routers OK"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by ThatBum on 2010-09-07
I have this unfathomable problem. One day I lost my WiFi connection while doing nothing particularly interesting. OK then...I investigate, and I find that it only connects occasionally, and when it does, even then it will render a page almost none of the time. I can't even ping anything. I tried going to the router's config page (192.168.1.254 for this one) and found that even that won't load. I power cycled the router, and it did nothing. I thought that the router was dying, but I realized when I switched to Windows 7 (this is a dual boot machine) it works fine. Also, when I went back to Ubuntu and tried connecting to a neighbor down the block's WiFi, it also works fine (this is what I'm using to post this message.) I did all I could to fix this, even to the point of dismantling the machine and moving cards around and such, but it did nothing. I finally formatted my Ubuntu partition and reinstalled, and it also did nothing. It also doesn't work from the Live CD. The router works fine on all the other computers in the house, wired or wireless, and also my phone and PSP's.

While connected, in Firefox, sites sit at "looking up", "waiting for", or "connecting to". It seems to be at random which one. They all time out, none of them say server not found. I thought it was a DNS problem, so I tried some DNS's I know (Google's, OpenDNS, DNS Advantage etc.) but it did bupkis.

One thing I notice is that while connected, I have a fantastic signal strength of about 85%, when before any of this happened, it was more around 70%. I didn't move the antenna anywhere or anything having to do with the reception. Also, once connected, it stays connected, it's just getting it initialized that's the problem, but even while connected it doesn't seem to work well.

This is incredibly frustrating, as I did not change anything with the router at all, in any way shape or form. It just spontaneously decided to not like Linux. The router's model is 2700HG-B.

Could it be that my wireless card is dying? I've had the thing for 6 years, and had no sign of it failing. I'm thinking that can't be it because it works with the same computer and network, but with a different OS. Could there be something wrong with the Ubuntu driver for my card, ath5k? I was going to say there's something up with wpa supplicant, because I use WPA-PSK for authentication, but I turned that off from another computer and it still does not work.

Again, the problem is that Ubuntu works with every router I can connect to EXCEPT mine, and  Windows 7 on the same machine works with the same router. My router works with  every other device in the house. I have changed nothing networking related, and even reinstalling Ubuntu did nothing. I would try it with Ubuntu on another machine, but my machine is the only wireless one in the house (and I can't put Ubuntu on the wired ones, that would PO some people), and I would try it with a different wireless card/USB thingy, but I don't have another one. Someone please help, I want to stop mooching off of neighbors' WiFi!

EDIT: I got some other Live CDs out, I tried Kubuntu 10.04, and Ubuntu 9.10. NEITHER WORK!

---

### Post by stevebu56 on 2010-09-07
A couple tests that come to mind that helped me when I was dealing with similar issues... 

Are you able to run a wire from your router to the Ubuntu machine?  Ping [www.google.com](www.google.com) Does that work? 

Can you reset the router to factory defaults & then setup the wifi as completely open, does the Ubuntu computer connect via wireless that way? Can you ping [www.google.com?](www.google.com?)  

When you do connect wired or wirelessly are you given an ip by the router if it's using dhcp?  Run ifconfig & check that you got a valid ip.

---

### Post by ThatBum on 2010-09-07
> **stevebu56 said:**
> Are you able to run a wire from your router to the Ubuntu machine?  Ping [www.google.com]("http://www.google.com") Does that work?

I wish I could run a wire, but I don't have an Ethernet cable long enough; the router is at the other end of the house. As I said, if I'm connected the the router, I can't even ping anything reliably, not even the router itself, which would usually work. I left ping running for a few minutes to the router, and out of around 900 pings, it only got about 20 through.

> Can you reset the router to factory defaults & then setup the wifi as completely open, does the Ubuntu computer connect via wireless that way? Can you ping [www.google.com?]("http://www.google.com?")  I would do a factory reset, but that's an issue because I don't know the PPPoE login and password to get it going again.

> When you do connect wired or wirelessly are you given an ip by the router if it's using dhcp?  Run ifconfig & check that you got a valid ip.I'm pretty sure it's giving me an IP, because If it didn't I don't think I would be able to connect at all. It's really hard to connect, but when it's trying, the WiFi thing in the panel goes to the second stage of connection (waves lighting up from the bottom to the top and starting from the bottom again, instead of the first stage where it's up and down repeatedly), so I assume it's doing some negotiation with the DHCP server of the router. In the occasions where I can connect, it does give me an IP in the 192.168.x.x block...so...yeah...that factory reset is looking pretty good right about now.

EDIT: I tried turning on DMZ to get around DHCP...after a few tries I got connected, and got assigned the public IP, but it doesn't seem to care, and it shows same behavior. I really don't think the router's the problem, it's my client here...man, I really wish I had a different wireless NIC or USB dongle to use...

---

### Post by ThatBum on 2010-09-07
I just went and got a Netgear 802.11g USB dongle and tried it, it did NOTHING. I'm so frustrated I slammed my $70 keyboard and broke a key. I'm typing on my iPhone. The internal NIC now does not work with Windows. This problem defies all explanation. I'm beginning to think my motherboard has gone bad somehow, and I will need to buy another machine, which is not possible at the time. This is the one thing I'm good at, computing, and I fail a such a deceptively simple problem. Please, someone help me, college is starting, and I need Internet access for course material.

EDIT: Alright, I seem to have got it working. It seems the router (or 'gateway' I suppose it is) was having some kind of trouble. I figured out how to get into the Management and Development Console ([http://192.168.1.254/mdc](http://192.168.1.254/mdc) for those who also have a 2wire gateway). While looking at the logs, I found all kinds of craziness about two days ago when this started...some kind of emergency shutdown or something, I could see runlevels switching around. I think I got it working by deleting the router's memory of my machine, and connecting again. DHCP delt it a new private IP (it's had the same one for a long time, because it's on long enough each day to not have the lease expire). It's working with my original wireless NIC now, so yeah. I still am not sure what happened to the router/gateway, but it appears to be working for now. Now I have to go to RadioShack and return the USB dongle and tell them I'm an idiot. Fun! Oh, and I fixed my key with some Bondo :).

---

