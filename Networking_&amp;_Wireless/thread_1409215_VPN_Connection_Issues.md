---
title: "VPN Connection Issues"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by CptBlack91 on 2010-02-17
Hi,
I wrote a thread detailing my problem, but it appears to have been lost in the cyber-ether. I will try to remember everything needed here!

I am trying to connect to a university computer using a VPN so I can work on the files from home. The guide I am following to set up this VPN appears to have been written for 9.04 whereas I'm using 9.10 and there seems to be some difference between the network managers.
[http://www.bristol.ac.uk/is/computing/advice/homeusers/uobvpn/howto/linux/ubuntu.html](http://www.bristol.ac.uk/is/computing/advice/homeusers/uobvpn/howto/linux/ubuntu.html)
In particular, I have noticed that the MPPE encryption box resets it self to 'unselected' each time I view the settings box.

I'm pretty sure that I can talk to the desired computer as when I try to ssh to it, the connection hangs until it times out. If I miss-spell the address, it rejects it instantly. I therefore believe it is my settings.

Can anyone help? I may need pointing in the right direction to supply further information.

Cheers,
C.

---

### Post by CptBlack91 on 2010-02-18
Slight update, I have installed 8.04 so I now have a triple boot. I have installed the advised package:
"VPN Connection Manager (PPP Generic)"
and I can now connect as desired.

I would prefer to use 9.10 for my work, so is it possible to install the correct package on 9.10, or is there a newer version that will work?

Many thanks,
C.

---

### Post by mathyou on 2010-02-18
Having the same problem with 9.10 64-bit.

Have tried editing in gconf-editor but no joy.

---

### Post by mathyou on 2010-02-19
Interestingly, it now works. Must have required a restart ;-)

---

### Post by CptBlack91 on 2010-02-19
Hmm, I got it to work by uninstalling all VPN packages from both add/remove and synaptive then installing the PPTP generic VPN from add/remove - no complaints as it works now, but took its time!

---

