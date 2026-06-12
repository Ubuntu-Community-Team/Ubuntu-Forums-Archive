---
title: "SSH Woes"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by emanmcdow on 2013-07-08
(apologies for being noobly)
I'm trying to ssh from a Ubuntu laptop to a Mac. I can ssh from the mac to the laptop, but not vice versa. Whenever I try to ssh to the mac it always says connection refused. I'm not really sure, but I think there arent any firewalls set up. I can ping both ways, but I can't telnet from the Ubuntu to the Mac. 

      I'm not sure I have the user for the mac correct though, there are two different possiblities, the name displayed at the top right corner, or the name displayed from terminal. 

What is going on?

---

### Post by papibe on 2013-07-08
Hi emanmcdow.

Did you install/enable ssh server on the Mac?

Have you test connecting from the Mac to itself? For instance, any of these tests?
```
ssh localhost

ssh 127.0.0.1

ssh hostname_of_your_mac
```
Regards.

---

### Post by 1clue on 2013-07-08
+1.

On your mac, go to System Preferences, then Sharing.  You want to check the Remote Login check.

Speaking as someone who does exactly this, I would like to ask you to consider if that's what you really want to do.

Having ssh server on your workstation is unnecessary even if you can conceive of a situation where it might be convenient.  You can always open another terminal, and having a service exposed when not necessary is a security hole.

Having an unnecessary security hole on your workstation means that, if your network falls apart due to some sort of malware or some other problem, you might not even have a workstation to work from.  Ask me how I know.

---

### Post by emanmcdow on 2013-07-08
Thank you 1clue. That fixed it. And yes this is what I really want. I'm just messing around and trying to learn everything i can about ubuntu. This ssh setup is in no way permanent.

---

### Post by 1clue on 2013-07-08
OK been there done that.  Have fun, but don't say I didn't warn you.

I once had 5 or 6 boxes sitting around, and I had ssh hooked up on all of them.  I used to just ssh straight from one to the other, not really considering how many hosts I was going through.  I had something somewhere hang and wasn't getting any luck getting my terminal back, but didn't really know how to figure out which of the couple dozen ssh sessions to kill.  Killed the wrong one, the whole plate of spaghetti went down.

ssh tricks:  Use ssh -X <host> when going to hosts that have X installed.  You can run synaptic or firefox from your workstation that way.  But don't do it through nested ssh sessions or you'll get a mess when it breaks.

I had a bunch of boxes at my job, and from my desk I could see into the server room.  It was pretty much just a closet.  A new IT girl started working there.  I wrote a script to ssh into all the UN*X boxes (there was a sun sparc) and eject all the CDs at the same time, sleep a few seconds and then pull them back in.  It took awhile to get it right but it was hysterically funny to fire it off when she was in there.  It was like cockroaches were coming out of the boxes.  The drag of it was I was the only one in the company who would have had the knowhow or the inclination to do something like that, so she came at me when she was still pissed.

---

