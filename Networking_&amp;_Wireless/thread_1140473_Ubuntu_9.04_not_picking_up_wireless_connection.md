---
title: "Ubuntu 9.04 not picking up wireless connection"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by jaime256 on 2009-04-27
Okay, I just did a clean install on my laptop, and the wireless doesn't pick up. Was working on 8.10 before I did the install. I also have two other open networks in the area and those won't connect either so are we back to square one on the wireless...ahhh..I know I have the settings correct for my network. The wireless balloon says I'm connected, but there are no bars on there and I got nothing on the browser. Anyone else bumping into this problem? I have also connected the laptop to a cable and got all the available updates. I rebooted and still, nothing. Thanks.

---

### Post by vistadude on 2009-04-27
Well u might want to try finding it if u did anything with the last version of ubuntu that made it work, and r u sure u have the right version? What I mean by that is did u download the 32 bit version or 64 bit version? And what wireless card do u have

---

### Post by jaime256 on 2009-04-27
Yup, laptop uses 32 bit, desktop 64 bit...and the 8.10 is the version that had the wireless working the best of all versions if I remember correctly. So I know there's something weird that's not working on the wireless with this version. I didn't do anything with the old one, just picked up. This one too, but it just doesn't work unfortunately. I was looking at all the other postings and it looks like I'm not the only one...not only that, I just posted about the 9 version and this already got 35 hits...so let's see what the end of the day has...that usually gives you an idea. I'm not trying to be mean, just pointing this out. I think the Ubuntu guys have done an awesome job...just wish this worked for me. That's all but I also know they'll get on it sooner rather than later so I'll wait a bit and see what happens.

---

### Post by jaime256 on 2009-04-28
Okay I decided to do a little more diggin today. Here are two attached screenshots. The first is the one when I connect to the wireless, but there's no access and the second is when I'm connected through my wire. I have circled the ips. For some reason the wireless has that weird IP. As you can see when I'm connected to the wire I get the normal DHCP address. WT? My ESSID is picked up fine, I just took that out.

---

### Post by jaime256 on 2009-04-28
Good news. I just got connected...all I changed was my essid. I noticed it's case sensitive, weird but yes. So make sure that's exactly correct, then wait for it...mine connected right up after I changed that and unchecked the enable then recheck the enable wireless. I also did the current updates but didn't see anything about the wireless on there before I did the above steps. Hope this helps. I may have also just been getting interference from other networks. Don't know, but now it works without tweaking anything. Also make sure you delete any other networks your wireless may have picked up just to be sure.

---

### Post by bfr420 on 2009-07-15
I'm completely new to Umbutu, and am having the same problem that you were having.  It says connected, sometimes, but I get no signal.  Please explain what the ESSID is, and where you got your screen shots.  Thank you.

---

### Post by superprash2003 on 2009-07-15
how far are you from your router? how is the signal in windows?

---

### Post by jaime256 on 2009-07-26
The screenshots are from the terminal window, kind of like DOS in windows. In other words, this is the non GUI (graphical user interface) that I used for the screenshots. 

The ESSID is the name your router has for the wireless access. Basically this is the name given to it when this is set up, and the rest would be like your password. Think of this as your credentials to log into your router, or for the wireless card on your computer to connect to the router so that you can then get on the Internet through the router. Whatever credentials are set up on the router need to be set up on the client (your computer) in order to connect to the Internet.

> **bfr420 said:**
> I'm completely new to Umbutu, and am having the same problem that you were having.  It says connected, sometimes, but I get no signal.  Please explain what the ESSID is, and where you got your screen shots.  Thank you.

---

### Post by montevjl on 2009-08-20
Hi,
I guess your posts are nearest to what I get:
- scrached my 8.10 turned 9.04 turned (bang!) 9.10 (dev)
Wireless was fine, all working, bluetooth, hsdpa, the whole bunch (except that... the Intel 2200BG ... so called Calexico never worked!)

Now the PC is clean, 9.04 from yesterday and... NO WIRELESS. The tick box is grayed out! I spent hours trying to find a solution. It's getting desperate since the HSDPA connection is also having trouble.

In the NetworkManager Applet (0.7.0.100) dropdown menu, eveything is grayed out except the Auto eth0
the rest, here is what the menu says:
- Wired network
- WIreless Network (IntelPro Wireless 200BG Calexico
- Wireless is disabled
- WIreless Network (Netgear WG111 wifi v2)
- Wireless is disabled

Has anyone a clue. I'm getting dumb!
tks
/jlm

---

### Post by jenkinsororo on 2010-09-18
I have the EXACT same problem. (Except im in 10.04)
So here's what happened.
I did a clean install of Ubuntu 10.04, and the first thing I noticed was that there was no internet. I clicked on the internet symbol, and it said:
 Wired Network: Disconnected
VPN connections >
The vpn connections thing is a menu, btw. So, all in all, it seems to want me to connect to a wired, but not a wireless. I'm hooked up to a wired right now, and when I'm not it says that the wired network is disconnected. Well, hello? what about wireless?! It simply refuses to pick up on a wireless connection, which I'm sure it should be seeing/connecting to.

---

