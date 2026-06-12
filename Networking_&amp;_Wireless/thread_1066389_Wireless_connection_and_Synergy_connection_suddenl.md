---
title: "Wireless connection and Synergy connection suddenly stopped working"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by LeeU on 2009-02-10
I am running a Dell Inspiron 530N with Ubuntu 7.10, using a D-Link 615 router. It is a desktop unit. Up until a few days ago, I was able to connect my Acer Aspire One netbook (Ubuntu 8.04) to the desktop; in addition, I was also able to use the [Synergy]("http://synergy2.sourceforge.net/") program on the desktop and a Windows XP desktop, sharing the mouse and keyboard on the desktop. (The hardwire network between the Linux and Window machines still works, though.) Suddenly, I am not able to connect to the Dell with the wireless netbook (the wireless is working on the netbook), nor am I able to connect from the Windows machine, using the Synergy software. One day it worked, the next morning it didn't.

Does any one know of something that might have been done to cause this to happen? I cannot recall changing anything before it happened.

Never mind. error on system .....

---

### Post by PointyHead on 2009-11-17
Hey all,

I realise this is an old thread, but I've just had the same issue so I thought posting my solution might help others who follow.

My problem was connecting to a Vista Ultimate lappie: it worked perfectly then, overnight, stopped working. Both ends [server, client] claimed to be connected. Firewalls were off on both systems for testing, and nothing helped.

Anyway, long story short: Windows updates were run automatically overnight on the lappie. I suspect that, post-updates, the system got it into it's head to run a scan and it invoked Windoze Defender. Defender [which I had left in its default configuration] identified Synergy, but didn't add it to the block list - but nor did it add it to a whitelist, nor offer me the opportunity to do so. I had a quick look, but found no way to manually add Synergy to a whitelist. Pathetic. M$ have feedback about this "feature" already. 

Anyway, to the solution: I shut down Defenders "real time" scanning craopla and Synergy came good instantly. 

For completeness: My desktop is wired to a local switch, which in turn is wired back to the ADSL modem/router. I have an AP hanging off the M/R, relaying DNS [DNS is via M/R] My lappie is on the wireless link provided by the AP. It's all working swimmingly now I've kyboshed Windoze Defacer.

So, it might be that simple for you too!

Cheers,
Pointy.

---

