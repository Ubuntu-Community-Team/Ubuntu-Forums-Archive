---
title: "wifi connection problems acer 5536 laptop"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by mike279 on 2012-10-21
Hi all, just joined the club and installed newest version of ubuntu (12.10 i think).
I have been able to connect to Internet through wired but it simply wont on wireless.
I find my router, input my password then it sits doing something then a pop up says 'disconnected'.
here is the wireless info:
06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
Please remember I'm new to linux/ubuntu so be gentle with what you tell me - I'm already wearing my dunce hat so dont worry about being disparaging :wink:
Thanks guys

---

### Post by ahallubuntu on 2012-10-21
Personally, I recommend new users stick with Ubuntu 12.04 LTS (or 12.04.1) because it will be supported until 2017.  12.10 first of all is new and second will be supported only until April 2014; after that, you'll have to upgrade to something else.

You can grab 12.04 from here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

You could boot that live ("Try it") vs. install and if it picks up your wireless card automatically, I would just install 12.04 over top of 12.10 .  I read of others with your wireless card having good luck with 12.04.  Worth a try if you have another spare blank CD to burn...

---

### Post by huxtee on 2012-10-22
I too am having the same problem, fresh install of Ubuntu 12.10 64-bit and WiFi can't connect to the network though Ethernet works fine. Strange thing is WiFi has worked on 10.04 - 12.04.

[edit] btw I'm using the same laptop Acer 5536

[edit] I got WiFi to work by using b/g mode on router, n mode doesn't seem to work.

---

### Post by spandon on 2012-10-22
I was having problems with a Dell vostro and now a Toshiba saterlite with connecting via the machines own cards.
having read all posts (ending up frustrated) remember seeing on one of the posts that someone found that a usb wifi adapter worked without any hasle.
I did have a couple knocking around - tried them and wifi now working on both with no probs or terminal work req'd
Hope that helps?
Don

---

### Post by mike279 on 2012-10-22
sorry but what do you mean by boot that live?
I should have said that I downloaded the wubi installer and put that on a new partition, then using wubi installed 12.10 on that, when I restarted I chose ubuntu and it booted up - easypeasy.
It only lets me install 12.10 (even though the site says I can choose between the .04 and .10)
also why was the wubi file and install of 12.10 small and quick while the 12.04 DL is taking ages.
I currently have no spare discs or usb drives so I need to install to partition from in w7- like I said 12.10 did this and worked perfect except wifi so how do I do the same for 12.04

Sorry for being useless :? :roll: ](*,)

---

### Post by ahallubuntu on 2012-10-22
When you pop in a Ubuntu CD (not Wubi) and boot the CD, you can choose to "Try it" running off the CD instead of installing it.  I have not tried 12.10 yet, but on the older versions of Ubuntu (including 12.04), you can hit the Esc key as soon as Ubuntu starts booting and you get a menu with the "Try it" option.  Then you can run Ubuntu (a bit slow) entirely off the CD - as a "live CD."  That will let you see if wireless works in 12.04 or not. 

After you shut down from a live CD, your CD will be ejected and no changes made to the hard drive.  It's a handy way to test things out without committing to install anything.

---

