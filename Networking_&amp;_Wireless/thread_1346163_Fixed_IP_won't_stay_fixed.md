---
title: "Fixed IP won't stay fixed"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by sptrsn on 2009-12-04
for whatever reason, I cannot figure out how to manage the IP address on Ubuntu 8.1.
It seems that no matter what I do, it somehow reverts back to a dynamically assigned address.
Is there an idiots guide someone can point me to?
I appreciate any input.

---

### Post by Iowan on 2009-12-04
[Here]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") is a How-To for static addresses in Intrepid.[This]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html") one didn't mention which version.
What are some of the things you tried that didn't work?

---

### Post by smilingralph on 2009-12-04
If the problem is Network Manager not remembering your settings it could be because of [this]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214") bug.
Ralph

---

### Post by sptrsn on 2009-12-04
ok I gave a quick read through the bug description and tried the tick off/on trick to no avail. Upon reboot got a crazy black screen with several pages of errors that made no sense, (noob) did a three finger salute to have another crack at it. 

UI came back this time. Here's what I get...
1. A new "Auto eth0" with both tick boxes checked. (connect automatically and system setting) Set for DHCP.
2. My original "Auto eth0" is still there (exact duplicate names)with my static settings, but the system setting box now unchecked. 
3. Plus "Wired connection 1" with neither box checked. And it is config'd with my static settings though.

I deleted the new dhcp "Auto eth0", at which point it reconnects with the appropriate static settings.

Not sure how long it will keep this setting. It just seems to revert back at some point.

Thanks for the input. I'm going to go through the How To now. Typical guy. Instructions are for girls! Read them last after all other options have been exhausted.

5 mins later...
I deleted all network connections and added a new one. (default name is Wired Connection 1) config'd it for my static settings. then restarted with this... > sudo /etc/init.d/networking restart per the How to. Upon restart Wire Connection 1 is set to DHCP. POS. Sometimes it seems like it's working and you can ping it internally, but it won't resolve from outside my network.(small web server)

5 mins later...
re edited the settings and restarted networking multiple times, and it finally resolves properly. I don't know if it's a bug or not. (not smart enough to know). But it sure seems like that should be easier. At least now it resolves from outside.

---

### Post by lisati on 2009-12-04
My $0.02: I prefer to control the IP address in my home network with my routers, both of which can assign a specific address to a specific machine. (it's part of their job description, isn't it?)

---

### Post by sptrsn on 2009-12-04
I will say this...
There is not another forum I've ever been on that has been as helpful and nice as this forum. Thanks to you all for everything you do the help the community!

---

### Post by uncaspi on 2009-12-04
Ubuntu 8.10 is very very bugged. Do an upgrade to 9.04

---

### Post by sptrsn on 2009-12-04
lisati, I just found the spot where you can do that. Didn't know the router could do that. Great idea. thank you.

---

### Post by sptrsn on 2009-12-04
Uncaspi, I would like to upgrade. I get a message saying that my video card is not supported in the latest rev. I'm afraid to try since that last time I had video problems and had to do a complete reinstall. 
That wouldn't be an option for me since I've been using this machine as a file server.

---

### Post by uncaspi on 2009-12-05
Anyway 8.10 is not recomended so I would do an exchange on the hardware first i.e replacing the videocard if its possible. I don't know if this is a laptop or what and if it possible to replace the videocard.

---

### Post by sptrsn on 2009-12-05
Good advice. It is a desktop and I can swap out the video card.
This has been a test on an older machine to see if I could actually make the full switch from MS. I've been running this almost exclusively for several months now. Turns out, I really like it, and will continue to run 3 or 4 linux boxes for various things. Web and file server, IP PBX and aux desktop. I'm also considering firing one up as fw/router/domain/dns. 
Recently though, I built an MS7 machine and I'm seriously thinking that I'm going to move to that as my primary desktop. For the most part it just seems so easy. That said, Ubuntu support on this forum blows MS away, and without question MS is a more expensive route. 
I think having both and leveraging their respective strengths is the best answer to the age old question. Which OS should I use? I think for me the answer is BOTH!

---

### Post by uncaspi on 2009-12-05
Be sure the videocard also is supported in 8.10 and not only in 9.04 if you buy a new one. 8.10 was released in Oct 2008.

---

