---
title: "Netgear WN511T and 9.10 trouble"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by Meyersgold on 2009-10-31
[SIZE=3]Ok, now this is ridiculous. I just upgraded to 9.1 and my wireless died. This is what I would expect in Windows. I have an IBM G-40 running with the new release and my Netgear WN511T is nowhere to be found. Is there any way to make it work or am I SOL?[/SIZE]

---

### Post by jethro00 on 2009-10-31
Same issue here with my Netgear WG511 - it was plug & play with 9.01, and DOA in 9.10... I did the Update Manager upgrade route.   Anyone have any thoughts?

---

### Post by davidkushner31@gmail.com on 2009-11-01
same problem here. WG511T DOA with 9.10 installation. Also used Update Manager. Maybe back out to 9.08?

help!

---

### Post by gt24 on 2009-11-01
Adding in, my Netgear WG511 card doesn't work in 9.10 either, worked flawlessly in 9.04.

It is a version 3 card and it worked with Prism 54 drivers.  Those drivers are blacklisted and replaced with p54pci.  The new drivers are supposed to work even better than the prism54 drivers and go figure that they don't work at all.  Unfortunately, when I blacklisted the p54pci drivers and went back to prism54, the card still didn't work.  I don't know how they broke it.

I will likely have to do ndiswrapper again and I haven't used those in a really long time (but they do work like a charm as I recall).  I will need to figure out how to make them work again.  :(

This really isn't a good year.  Ubuntu 9.04 kernel panic'ed on boot and took a very complicated procedure to make work on my laptop and now, while 9.10 at least boots on this laptop, the wireless is now broken.  Sigh...

---

### Post by jethro00 on 2009-11-01
OK - Just a little update...  Wiped the laptop and installed 9.10 from the CD ISO... Still no luck with the wireless.  Wiped it again and put 9.04 on, it detected and and connected fine.

---

### Post by Meyersgold on 2009-11-02
> **jethro00 said:**
> OK - Just a little update...  Wiped the laptop and installed 9.10 from the CD ISO... Still no luck with the wireless.  Wiped it again and put 9.04 on, it detected and and connected fine.
Jethro00, I couldn't get it to work in 9.04 either. Are we talking about the same thing, Netgear WN511T pcmcia wireless notbook adapter?

---

### Post by amberti on 2009-11-02
I have the same problem (NETGEAR card), as gt24 says prism54 drivers are blacklisted by default. I removed the blacklist on prism54 and added p54pci to blacklist. Now lshw reconize the card but still it is "DISABLED" and is not working.
Solutions?
Thanks

---

### Post by gt24 on 2009-11-02
Adding on to what the last poster said (since I left it out), the prism54 drivers once they were enabled did let the card at least be seen by Ubuntu but the card showed as disabled in the network manager in Gnome and from iwconfig.  I never got that error with a wireless card before, so I assumed that was a dead end.

For the p54pci drivers, it was recommended to try alternate firmwares to plug into the drivers but the most I got was a small blink of the busy light on card insertion with the absolute latest drivers.  I didn't try "extracting the firmware from a windows driver" yet.

---

### Post by jethro00 on 2009-11-02
> **Meyersgold said:**
> Jethro00, I couldn't get it to work in 9.04 either. Are we talking about the same thing, Netgear WN511T pcmcia wireless notbook adapter?

Sorry Meyersgold - I'm using the WG511 (V3 'made in china' rev) just to clarify...  But I believe 9.10 is displaying issues with multiple Netgear devices

---

### Post by parmruss on 2009-11-02
A look at the forum here and elsewhere on the net shows that wireless in 9.10 is generally borked across a wide range of hardware. One interesting post suggested is was a kernel issue (sorry,lost the post), and that using iwconfig to knock down the wireless link speed from 54 to 11mpbs solves the problem.

---

### Post by Meyersgold on 2009-11-06
Well I can't wait for a solution, I am going to install openSUSE 11.1 instead and see if it works

---

### Post by rlelina on 2009-11-13
> **jethro00 said:**
> OK - Just a little update...  Wiped the laptop and installed 9.10 from the CD ISO... Still no luck with the wireless.  Wiped it again and put 9.04 on, it detected and and connected fine.

Almost same experience with my WG511v2. Worked fine in Windows XP Pro and Ubuntu 9.04. After upgrading to 9.10 using the Update Manager, card still connects as before BUT drops connection after about a minute or so. I had to pull out the card and push it back in for it to reconnect. Someone mentioned in this thread about throttling back to 11Mbps but it's too late now because I just reinstalled 9.04 from CD. Now wireless is happy again :-) I think I'll wait some more time hoping someone figures out exactly what's going on with Ubuntu 9.10 regarding wireless.

---

### Post by rlelina on 2009-11-21
> **rlelina said:**
> Almost same experience with my WG511v2. Worked fine in Windows XP Pro and Ubuntu 9.04. After upgrading to 9.10 using the Update Manager, card still connects as before BUT drops connection after about a minute or so. I had to pull out the card and push it back in for it to reconnect. Someone mentioned in this thread about throttling back to 11Mbps but it's too late now because I just reinstalled 9.04 from CD. Now wireless is happy again :-) I think I'll wait some more time hoping someone figures out exactly what's going on with Ubuntu 9.10 regarding wireless.

I tried 9.10 again from CD because I got a new router Linksys WRTN160Nv3 with firmware v3.0.02 build 3 (my previous router was Netgear WGR614v4). Now, 9.10 is happy with my wireless setup -- no dropped connections so far.

---

