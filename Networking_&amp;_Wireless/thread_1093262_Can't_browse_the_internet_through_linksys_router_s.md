---
title: "Can't browse the internet through linksys router since resetting to factory defaults"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by djrobthaman on 2009-03-11
Hi everyone,

I think I've gone and done something incredibly foolish.  I decided last night that I was going to try and see if I could set up some way to browse my home network from my PC.  That network is on one router while my computer is is connected to it through another linksys router.  I thought maybe trying a DMZ would work, but it didn't.  After changing all sorts of linksys settings I noticed I couldn't access the internet at all.  Since I wasn't sure where I went wrong, I just reset the factory defaults on the linksys router.  That seems to have been a killing move.  Since then, I've not been able to access the internet.  I even tried logging in to Windows and using the original set up CD to reinstate whatever settings I had when it was working.  No dice.  The set up process can't access the internet.

But, if I pull out my ethernet cable (which is coming from that other router I was talking about before) and plug it straight into my PC, I access the internet without a problem.

When I connect (or try to connect) through the linksys I can access the router itself and adjust its settings.  So I'm hoping that this is just a bad config problem.  Does anyone know what I could do to fix the problem?

Thanks.

PS.  Just in case this helps.  The ballsed up router in question is the Wireless-G 2.4GHz Broadband Router (WRT54G) and my PC is connecting through one of the wired ports.  But my phone can't access the internet through the wireless connection either.

---

### Post by MatthewMetzger on 2009-03-11
In the router setup (192.168.1.1), look at the status page. If there's zeros where a network gateway should be, release and renew your connection.

---

### Post by tomski on 2009-03-11
i work for an ISP & essentially by reseting to factory defaults the router will not know your dsl username & or password!

you WILL need to reconfigure your router.

I would recommend you call your ISP and ask them for the basic setting's for your router along with your ADSL usernmae & ADSL password

if you live in the UK then here are the basic's to get sync:

routing mode
pppoa encapsulation
vc-mux modulation
vci 0
vpi 38
if possible set it to 'nailed up connection' or set the 'time out value' to 0


if you have a STATIC IP ask them what it is & enter that into the wan config BUT if you have dynamic then select that or 'collect IP address automatically'

sync = hardware connection to local exchange...similar to the 'link' light on a network card

---

### Post by djrobthaman on 2009-03-11
I don't remember needing to configure user names or passwords.  What happened was I was already connected through another router.  Then I got my iphone and decided I needed wireless internet for it.  So I bought the wireless router.

I connect the ethernet cable that comes from the original router that connects straight to the internet into the lnksys.  Then I connect the PC to one of the ethernet out ports from the linksys.

In a setup like that, do I really have to worry about passwords and usernames and ISPs when I didn't have to before and all of that stuff should already be dealt with by the other router I have?

---

### Post by lindsay7 on 2009-03-11
Why no just use the wireless router?  The default admin and password should be "admin" and "password" respectively.  You can go to the Linksys web site and download or view the manual for this model. That should help you walk thru the setup. You may need to reset you devices with the new security info accordingly, i.e. key. passpharse, mac address, etc.

---

### Post by djrobthaman on 2009-03-11
There are other machines on the top router already.  I don't want to change that.  It was working fine last night.  Then I went and changed something and now it isn't.  So I know it's not supposed to be a problem to have this connection work.

Apparently the version of Linksys Easylink Advisor that came with my router no longer correctly reports whether the interne t is connected because of some change in the verifying URL.  Downloaded a later version and it is useless.  It reports everything as fine when I'm connected straight through the top router.  Then reports there being a problem when I connect through the wireless router.  I tell it to automatically fix the connection and it says retrieving new network address for 5 minutes and then says it can't fix it (because clearly it's resetting the router which is useless or just performing an ipconfig /renew call which again is useless)

Does anyone know how to get the right settings for this???????

---

### Post by djrobthaman on 2009-03-12
Figured I'd give an update.  So far I've got the router to think it's connected to the internet (It still isn't though) by supplying information for the "Domain Name" and "Host Name" fields in the basic setup section of the router's web based interface.  Also, I changed the router's IP from 192.168.1.1 to 192.168.2.1 because I remember that was what it was before I reset all these things.

I've been thinking that maybe I just need to figure out what address to put in to Host Name and Domain Name and then I'll have it working again.  Is that a fair assumption?  Another guess I'm making is that these adresses are going to be somehow linked to the address of the router that's directly connected to the internet.

When I connect through the top router and am able to access the net, this is the info I get from ipconfig (been doing most of this on Windows since I was trying to see if any of the linksys tools would automatically fix my problems):

Connection-specific DNS Suffix:
IP Address: 192.168.1.6
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1

Do you think that any of these values is/are the key to getting the wireless up and running again?

---

### Post by djrobthaman on 2009-03-13
I've marked this thread as solved because the problem is now fixed.  Unfortunately, I don't know how.  I was messing around with the Domain Name and Host Name last night and after a while noticed that my "ipconfig" information stopped changing.  So I deleted the values in both fields and restarted the router (and before you ask, yes I'd done this a million times before).  Then when it came back, all of a sudden I was getting responses from google and whoever else I tried to ping.  So now I have wireless.

Lesson learned.  From now on, whenever I want to browse my home network just switch the cables.  It's much less annoying than tearing hair out while waiting for settings to right themselves.

---

### Post by djrobthaman on 2009-03-13
Hang on.  I thought you could mark threads as solved.  Oh well.  I guess it will forever remain an unsolved problem.

---

### Post by boof1988 on 2009-03-13
> **djrobthaman said:**
> Hang on.  I thought you could mark threads as solved.  Oh well.  I guess it will forever remain an unsolved problem.

I haven't tried to do it yet... but I think you can edit your original post title and add "Solved" to the title or maybe add a "Solved" tag to the thread.

I added solved to the title of this post to see what happens.

---

