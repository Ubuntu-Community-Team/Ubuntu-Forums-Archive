---
title: "Asus M50VM-X1, Wireless networking broken.  Help!"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by painterh on 2008-12-31
I have a new Asus M50VM-X1 with Vista pre-loaded and a fresh install of Intrepid. I set up additional partitions so that my 250 GB hdd has 4 nearly equal partitions. Vista was already setup with one for the Vista OS and one for data and I set up the other 2 as ext3 and did my install. I used "Easy BCD" for bootloader and the install went flawlessly. I now have a major issue.  Wireless Networking

This notebook uses the Atheros 928x internal card/chip. In network manager, when I enable wireless networking, It sees my gateway but wont seem to connect. I have checked out the wireless switch on the front of computer and it is on. I would think that if bluetooth is working, (bluetooth icon is visible in panel when switch is in on position), and it sees my network in network manager that the wireless is indeed turned on. It seems to have difficulty with WEP key. It seems to prefer WPA as network security, and wont remember my WEP key. My home network is set up with 64 bit WEP passphrase, and that choice is not given in network manager. It always gets to the point of acquiring a network address and then fails to connect. I have seen other posts about the Atheros 928x driver not working properly in Intrepid (or linux in general), so I think it is a driver issue but don't know what to do at this point.

I have looked at some posts concerning this issue, but the info seems to be more for Hardy than for Intrepid.  If there is anyone who is familiar with this notebook or is really up to speed on wireless networking (especially on notebooks), and could dialogue with me a little to help solve this issue,  It would be wonderful.  I really don't want to try another distro because I have been using Ubuntu on my desktop PC and it works great.  I do know from the hours I have spent on the net trying to get this sorted that notebook hardware is quite different to set up (and the problems are unique to individual manufacturers and hardware).  I eagerly look forward to some help with issue.  Thanks in advance.

---

### Post by Zerimas on 2009-01-27
I am having the exact same problem as you.  :(

---

### Post by SketchyClown on 2009-02-11
Painterh,

I have the M50VM-A1 with the Atheros 928x and I recently had an issue with networking as well, but seems to be working fine afterwards.

That "switch" you speak of on the front of the laptop is the same one that I have, I believe.

That switch is not just a bluetooth power switch, it also turns your wireless card on or off as well.

If you turn it off, after a couple minutes all the detected wireless networks will all disappear until it is turned back on again.

I spent a whole night trying to figure out why my wireless card was seen and apparently functional but wouldn't pick up any networks. Then I flipped the switch (didn't know it had been switched off) and within 60 seconds it had detected all the networks again and could connect..

---

### Post by ARam1024 on 2009-02-11
I've been having the same problem as you, and I found a partial solution.  Take a look at [this ticket]("http://ubuntuforums.org/showthread.php?t=1051255&highlight=ASUS+M50VM").  It also shows how I fixed the sound on my ASUS M50VM-B1.

Best of luck to you.

---

### Post by ARam1024 on 2009-02-11
to make it clear, that last post also fixes the wireless problem.  Took a lot of searching to find all the problems though.

---

