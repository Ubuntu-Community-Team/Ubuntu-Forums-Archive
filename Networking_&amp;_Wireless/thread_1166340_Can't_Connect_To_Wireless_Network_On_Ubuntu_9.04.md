---
title: "Can't Connect To Wireless Network On Ubuntu 9.04"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Danjay5291 on 2009-05-21
Hey everyone. I'm in need of some help. I've just installed Ubuntu 9.04 on my Asus F5R. Everything works perfectly except for my wireless card (Atheros AR5007EG). It detects my wireless network but won't connect, it just keeps reprompting me to enter the WEP key, which I am 110% is correct because my sisters laptop connects to it with that code fine (also running Ubuntu 9.04). Any help would be much appreciated.

---

### Post by nyjetgrl on 2009-05-21
i've had the some problem with random routers and have had to be relatively close to router to get it connect.  One I get the first connection though, it's fine from further... good luck

---

### Post by superprash2003 on 2009-05-22
try various combinations for encryption type like 64bit , 128 bit etc

---

### Post by lakair on 2009-05-22
I have the same problem with 9.04 netbook remix. When I run it on my ASUS EEEPC 701 it connects to the wireless network perfectly but it will not connect  when I try to use it on  an ASUS EEEPC 901. When running on the EEEPC 901 it trys to connect but eventually it will fail producing the password dialogue box.
Any ideas?

Thanks

---

### Post by killernat on 2009-05-22
its the most annoing bug on ubuntu i just fixed it 5 min ago there is a bug that wont let you connect to secured wireless network just turn off the security from your router and it works fine

---

### Post by lakair on 2009-05-22
Thanks, I'll try that.

---

### Post by growbo on 2009-05-22
Well I'm a noobie to Ubuntu,must admit was gettng a little frustrated until I found this thread, switching security off my netgear router did the trick. I was using wpa/psk.

Cheers
:D

---

### Post by NubeeUbun on 2009-06-05
I'm having the same issue with my ASUS laptop.
I can detect wireless networks but am unable to connect to them.
When I try to connect to my wireless network (which is working for 5 other non-linux machines) it keeps on trying and then times out.

I uninstalled network manager and installed Wicd based on input from similar threads.
However, I am still unable to connect.

I am running Ubuntu 9.04 x86_64 via a Wubi install on a Vista 64 bit.
My wireless connection and internet work fine on the same laptop when I boot in Vista.

Turning security completely off as suggested in this thread doesn't seem like a practical solution. Has any other solution become available?

Thanks!

---

### Post by cg49me on 2009-06-10
I'm in the same boat, though I haven't tried turning the security off yet.  I'll give that a shot tonight - if nothing else, I could impose MAC address filtering.
 
Dell 600m Notebook
Intel PRO/Wireless 2200 B/G card (I think...  Might actually have the Broadcom card.)
 
LinkSYS WRT54G Router
DHCP
WEP 128b Encryption
 
I tried typing in the hex code, and just doing the passkey with the right index - no dice either way.  Windows connects just fine.

---

### Post by larryf on 2009-06-10
I'm having the same issue with a Dell 5100 where it won't connect to the wireless network - Linksys WRT54G.

I can connect via wired port just fine.  I've also tried turning security off on the router but that doesn't work either.

One strange thing is that in some cases when I click 'Connect' I get a message in the top right corner that says "Wireless disconnected....".  Other times when I click 'Connect' nothing happens, no error message but it still doesn't connect.

I'd be interested in hearing any solutions anyone else finds that I can try.

---

### Post by cg49me on 2009-06-10
Been perusing the forums some more... Apparently some people have had luck installing a different network manager. I'll see if I can find the threads again...
 
*edit*
 
Check out post 9 by **juky** in this thread:
 
[http://ubuntuforums.org/showthread.php?t=1168561](http://ubuntuforums.org/showthread.php?t=1168561)
 
I'm gonna give that a crack tonight too.
 
*edit*edit*
 
Just thought I'd mention that wireless connectivity issues seem to be a widespread issue in Jaunty.  Do any searching at all, and you'll find a ton of people that can only connect to unsecured networks, or can only connect to WPA but not WEP (or vice versa), or can't connect at all.
 
Someone started a Launchpad bug report on this specific issue, and it's only a week or so old, so it is being looked at.

---

### Post by cg49me on 2009-06-10
Well, for whatever reason, it's not giving me any trouble anymore.  I didn't do a single thing.  *shrug*

One thing I've noticed in dinking around is that turning on and off the radio (Fn + F2 on Dell notebooks) doesn't bring up any sort of visual indicator, but it does in fact turn off the wireless card.

---

### Post by Sardonism on 2009-06-10
I've had this problem too, where network-manager would take my passphrase and turn it into hex and send that out instead of my real passphrase.

I corrected that by using Wicd.

---

### Post by chadk5utc on 2009-06-13
[http://ubuntuforums.org/showthread.php?p=7448204#post7448204](http://ubuntuforums.org/showthread.php?p=7448204#post7448204)

---

### Post by Richard Langford on 2009-06-13
I love Ubuntu - half an hour to load, and looks great...but until I read this post my wireless network connection was driving me mad. I had absolutely the right password, but have just turned off all security to get going...thanks.

My D-Link network adapter worked out of the box with no drivers to load, and I read on another post that the USB version is justs as good - too easy.

However, if someone has a fix for the password-protection that allows even simple encrypted logon (40-bit), I would be very happy :)

---

### Post by tenpennys on 2009-10-24
I have one similar to the above posts.  

I have a dell E1405 Laptop with a intel wireless card.  It work perfectly at my business, and at a friends house.  When I take it home however I can not connect to my wireless network.  I have tried different routers, and different types of encryption, different SSID everything I can think of.  It will connect once in a great while, (just enough to really tick me off.)

Other wireless computers (running Ubuntu on another desktop) seems to work fine from a house next door.  Its getting really irritating.  

I bring it to work or other places it sees the networks right away, at home it doesn't often see the network and even if it does it will keep asking for the key or passcode and then not connect.  I am 8 feet from the router in the same room.  Tried a linksys router and a belkin router and the problem is the same.  

I'm tearing my hair out and I can't afford that!

---

### Post by AFnetSuraj on 2009-10-28
I tried to connect to AirCruser N300, and it worked good. It was having the problem of antenna. I attached a wire and tested it, its detects other network.
step 1: install windows driver from [http://www.giga-byte.ca/Support/](http://www.giga-byte.ca/Support/)
step 2: install ndiswrapper , its easily available on net
                 follow instruction given in ndiswrapper INSTALL document.
step 4: and now try command iwlist scan
then you will find the detected network.

---

