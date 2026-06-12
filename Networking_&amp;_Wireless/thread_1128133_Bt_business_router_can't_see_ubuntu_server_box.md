---
title: "Bt business router can't see ubuntu server box"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by trstn on 2009-04-17
Like the title says really, does anyone else have this problem?

The ubuntu box is part of a small office network, it's connected (by ethernet cable) directly to the bt router.

Here's what I *can* do

I can access the internet from the ubuntu box

I can access phpmyadmin, webmin and other bits and pieces on the ubuntu box via browsers on other computers in the office

What I can't do:

Open port 50 on the router so we can access the ubuntu box from outside the office. No matter what I try the router just won't see the ubuntu machine.

And being a btrouter, you can't manually setup routes or port forwarding, the router has to see the machine to WYSIWYG connect to it.

Help!?

---

### Post by MaindotC on 2009-04-17
If the ubuntu machine can access the internet via the router then the router must be able to see the Ubuntu machine.  You should have a listing of "attached devices" in your router's administrative interface and it should show the ubuntu machine in there.

---

### Post by trstn on 2009-04-17
> **strAlan said:**
> If the ubuntu machine can access the internet via the router then the router must be able to see the Ubuntu machine.  You should have a listing of "attached devices" in your router's administrative interface and it should show the ubuntu machine in there.

Indeed, it stands to reason doesn't it? But I assure you, I know my way around routers and it's just not there. I thought I was going crazy but the machine just doesn't exist as far as the router is concerned.

I access phpmyadmin on the ubuntu box from any machine in the office using: [http://192.168.1.234/phpmyadmin](http://192.168.1.234/phpmyadmin)

I ping 192.168.1.234 from the router - all I get is a time out.
tracert from the router - time out
finger - time out

This is the weirdest networking problem I've ever encountered.

---

### Post by MaindotC on 2009-04-17
The machine does exist otherwise it wouldn't be able to acheive network communication.  You know your way around routers, so perhaps I'm suggesting what you already know, but I would check any packet filtering settings on the router.  It's very common to have ping and finger to be filtered because obviously this would let an attacker know that the device is present.  I don't know what a "bt router" is - it's nomenclature would really help - but there must be some settings for nat or pat.  I would advise setting a nat rule for port 50 to the address of the machine, regardless of whether or not the router "sees" it.

---

### Post by superprash2003 on 2009-04-17
use this online port scanner to see if port is open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/) .. do you have firestarter or anything similar running?

---

### Post by sidcypher on 2009-04-17
Okay, I know he isn't crazy, cause I am having the same problem with my router and a Ubuntu 8.1 server setup..

Have net access can ping and install and update...
can hit all the network computers with pings and whatnot

but can't setup port forwarding for access from outside network, my router just doesn't see the box. it is a older p3 dell and a 2wire router from AT&T for the DSL

when I had XP on it, the router could see it. now it doesn't and i can't setup forwarding without it.

any help would be great.

Newish to linux, used to use 7.04 on laptop, then back to vista, now been running 8.1 all the time and router is SEEING that connection.

---

### Post by timcredible on 2009-04-17
what do you mean "the router doesn't see the ubuntu box"?  do you mean it doesn't list it in it's dhcp list?  if so, just change your ubuntu box to static address, then the router shouldn't have any issue because it's not giving an ip address out and failing on whatever stupid thing it's looking for.  if you still have problems, contact your isp that gave you the router, explain the problem, and make them upgrade it to fix the problem or swap it out with something that works correctly, because this router is definitely doing something incorrectly with the dhcp rfc.

---

### Post by MaindotC on 2009-04-17
The router seeing your machine has nothing to do with the o/s as routers operate on a layer below applications (please tell me you don't run the software that comes with the router). The only thing that may be different is XP may be set to send its hostname and you can do the same in Ubuntu by modifying the dhclient.conf file if it may have been commented out. This has nothing to do with the type of o/s.

---

### Post by sidcypher on 2009-04-17
timcredible - 

It isn't on my list in the "devices" where everything else is listed, and I hate DHCP everything is already static, cept the wifi side of things, all hard-wired is setup with static ip's

strAlan - 

I don't run the software, but they do make good coasters for my drinks.  Since it was set as static AT install, would the dhclient.conf make any difference?

Anyway I installed lynx just to try to actually goto a website, since i am not running a gui of any sort, that worked. so it isn't just being able to ping and update/install and whatnot. 

DSL/Router [2wire 2701]("http://support.2wire.com/index.php?page=download")

I wouldn't think it would the be install, i have another nic laying around i can try...but i def think it is the router for some reason it won't show up under "Network Summary" where all the wired(static) and wireless (dhcp) devices are listed, and there is no feature to just manually add a port forward to a IP.

Thanks for your help

---

### Post by sidcypher on 2009-04-17
Update for me atleast.

Issue has been resolved had to go into the "management" connection into router and wipe the device list, seems I am only allowed 15 devices, oh well my HTC 8925 doesn't need to use wifi I guess.

---

### Post by MaindotC on 2009-04-18
> **sidcypher said:**
> 
I don't run the software, but they do make good coasters for my drinks.  

That deserves a LoL :D

As for your router's settings - that definitely deserves a daily wtf.  Check and see if there are any firmware upgrades because that kind of frustrating crap shouldn't happen.  Glad it's working for you now.  But, if you check the dhclient.conf you will see there is an option to send the hostname or not.  I figured that wouldn't be the issue unless you modified the file but I couldn't think of anything else.

---

### Post by trstn on 2009-04-21
Ok I've figured it out.

First off, it's a bt business router (british telecom), bit rubbish but it's what we use.

If I switch from static ip to using dhcp the router can see the ubuntu box fine, if i go back to static it disappears. 

I guess it's something to do with ubuntu not contacting the router to say it's there when it uses a static ip?

Is there anyway to contact the dhcp server but retain a static IP?

---

