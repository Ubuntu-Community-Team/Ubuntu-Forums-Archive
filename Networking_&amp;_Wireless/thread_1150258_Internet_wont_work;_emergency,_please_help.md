---
title: "Internet wont work; emergency, please help"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by thingy87654321 on 2009-05-05
ok, i have a meeting tomorrow morning  and i have to present a presentation and i NEED internet, but when i started up my ubuntu laptop, the little wifi icon said it was connected, but when i tried to access the internet, it wouldn't work, so i immediatly tried to get on msn to contact Xreaper, but it couldnt connect, please tell me how to fix this, i have to get this fixed, my job is on the line. please


and i tried a different wifi connection, still didnt work, and i tried other ways to, no luck

---

### Post by BastardNamban on 2009-05-05
First of all, calm down. I know what it's like- I've been in the same situation.

I, and no one here will be able to help you unless you give us details. I'm no networking master myself, but I do know this: to help you, people will need the make & model of your laptop, and the name of your wireless card. Look here[http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")

Give us more info, like what type of router, wireless card, linux version, and someone can help you. I don't mean to sound like an ***, if there's anything I could do, I would. But noone can help if we don't have your specifics.

---

### Post by thingy87654321 on 2009-05-05
ok   --the nerd part of me kicks in--



IBM Thinkpad R40 (with a R51 chassis and screen)

Trendnet router (tew-311 something)

intel WM3B2200BG <ONLY ONE THAT WORKS IN THIS MODEL WITHOUT A BIOS SECURITY ERROR>

ubuntu 8.10 intrepid ibex

1.5 GHZ pentium m processor

1 gb of ram

dvd/cd-rw drive

---

### Post by thingy87654321 on 2009-05-05
Anyone out there?
Help please?

---

### Post by BastardNamban on 2009-05-05
ok, I'm going to admit again, I probably can't help with the immeadiate problem. I'm a newbie, but I can help narrow down the problem for others.

First, if your job is on the line, I'd go for the temporary fix, and use a wired connection to your router for internet. If you don't have a spare cable laying around for this, you should keep one there in the future in case of this happening again. Any stores nearby that sell a cable? Might want to buy one quick just in case someone can't help you in time tonight, it is late.

Second, have you had a working wireless connection before? Maybe your card fried. If you use someone else's network, they may have updated to a passkey that you don't have.

Most OBVIOUS thing, to me? Try reseting your router and modem- unplug them for a couple minutes, and plug them back in, modem first, router second. A reset like that often fixes lapse in service for me.

If those don't do it, let us know.

---

### Post by BastardNamban on 2009-05-05
On a side note, having never posted in this part of the forums before, it seems like a LOT of people, myself currently included, are having networking problems, but very few replies come in this area.

I hope I was able to help you some, at least. No one at all has tried to help me yet, in 2 posts!

---

### Post by thingy87654321 on 2009-05-06
i have tried a wired connection, i think something is blocking it, my friend installed foxyproxy and i uninstalled it, it may be a proxy or something

---

### Post by JK3mp on 2009-05-06
An emergency would be dying ;) . But i guess for ubuntu related, this will do. You stated that it say's its connected, but then doesn' show internet. Does your router show up as getting internet? Perhaps your connected locally but your rrouter is not recieving internet. Make sure the router is recieving internet. Do you use a static IP or is your router porting the default DHCP. This bit of info and narrowing out a router problem, will help me and other to figure out the problem.

---

### Post by thingy87654321 on 2009-05-06
no, i thougt the same thing, but it is connected on my desktop
even the modem is still loged on, so i know it is something with the os

---

### Post by jim87410 on 2009-05-06
Hi,
Let's check some basics.  Run the following in a terminal:
ifconfig  (check what IP address is assigned to wlan0)
netstat -r  (dumps the IP routing table)

jim

---

### Post by thingy87654321 on 2009-05-06
didn't work
AHHHHHHHHHHHHHH WHY DOES IT HAVE TO HAPPEN TODAY OF ALL DAYS

---

### Post by thingy87654321 on 2009-05-06
WHAT HAPPENs if i remove iptables from synaptic

---

### Post by whewell on 2009-05-06
Does it work if you ip addresses directly? 
I'm having networking problems with Ubuntu too. It's a dns issue. 
when I ping [www.google.com](www.google.com) I get nothing. but it's fine when I ping 66.249.89.147 (one of the google ip).

if that's the case, try adding the ip address of your isp dns server to /etc/resolv.conf.

---

### Post by thingy87654321 on 2009-05-06
what is the isp dns server ip, how would i find it

---

### Post by Dngrsone on 2009-05-06
Try [this](http://ubuntuforums.org/showthread.php?t=571188).

---

