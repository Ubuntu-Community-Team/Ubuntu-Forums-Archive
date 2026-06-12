---
title: "Strange Wifi Issues after upgrade from 11.04 to 11.10"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by Nir Friedman on 2011-11-01
Hey,

wifi worked just fine for me in 11.04. I upgraded to 11.10 and the situation now is really bizarre. My connection at home still works fine (although strangely all network information had been wiped so I had to type everything in), it's WPA2 personal. I came to work, and I can't detect either of the networks at work, one is WPA2 enterprise the other one is open. I then activated the network from my cellphone tether which is WPA2 personal as well, the computer managed to find this. However after deactivating the cellphone network the computer continued to see it for more than 10 minutes after, at which point I put the computer in sleep and then brought it back out, at which point it didn't see the network any more.

I read one one thread something about the new kernel, version 3 something having bugs. So I booted into grub, and from there selected the old kernel from 11.04 which was version 2.6.38-11. This did not solve the problem.

Help please? Thanks very much.

Nir

---

### Post by Nir Friedman on 2011-11-01
A update in this continuing and bizarre chain of events: after getting fed up with debugging this, I decided to try to move some files from the laptop to my desktop and just work there. I connected the computer to my cellphone's wireless and ran an rsync command, which worked successfully. I then turned off my phone's wireless. I was just preparing to move to the word desktop when all the wireless connections that exist in the area popped up on my laptop. I connected to my preferred one, and it worked perfectly (WPA2 enterprise).

In conclusion, wireless is black magic.

---

### Post by Nir Friedman on 2011-11-03
Ok, to continue upgrading: this problem is systemic and reproducible. Every day I come in with the laptop, the same thing happens: can't detect any wifi networks. I activate my phone's network, connect to it, and then immediately all the other networks show up. 

In addition, knetworkmanager is not storing secrets for any networks despite the fact that I have checked off "store secrets in unencrypted file". I found another link about this at [http://ubuntuforums.org/showthread.php?p=11416056](http://ubuntuforums.org/showthread.php?p=11416056) but I'm a little nervous to follow the advice given there without more information on which packages I'm removing and how to check if they're necessary or not.

---

