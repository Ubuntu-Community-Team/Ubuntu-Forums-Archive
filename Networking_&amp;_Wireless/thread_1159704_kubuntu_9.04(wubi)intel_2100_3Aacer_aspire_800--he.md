---
title: "kubuntu 9.04(wubi)/intel 2100 3A/acer aspire 800--help greatly appreciated"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by piro133a on 2009-05-14
Hey guys, im kind of at the end of my rope. Im new to linux/ubuntu but i have been working with computers as a tech for a long time, i have just never taken the jump.
I installed kubuntu 9.04 through wubi and I am eventually going to make it independant through LVPM....but heres the problem: i cannot for the life of me get my (crappy old) intel 2100 wifi card to work. at first i tried to find drivers for it and got the needed tar packages from ipw2100.sf.net ieee80211.sf.net etc. I couldnt find any documentation that i understood for those packages...i tried running the "Load" scripts from those. they made some changes i dont understand. I read something about installing restricted modules...did that, but didnt know how to install the ones i need. NOW i am finding that my card is supposed to be supported right from the install!!!!!! im going to go and do lshw to see whats up and post it....but here is my ending questions: since i ran those scripts should i just remove the wubi install and start again (might be easier for me as a newbie), and what should i do to get the thing running if i did...or as it is now how would i get it running?
 
I remember being frustrated by IRQ conflicts in windows 3.11 when i was 10, but this.....this takes the confusion cake.
 
 
thanks guys, i reeallly really appreciate the help.

---

### Post by chili555 on 2009-05-15
> since i ran those scripts should i just remove the wubi install and start again (might be easier for me as a newbie), and what should i do to get the thing running if i did...or as it is now how would i get it running?I am always the optimist. Try the native driver and see if any errors are thrown up (no pun intended). Open a terminal and do:```
sudo modprobe ipw2100
```Any errors or warnings? Next do:```
sudo lshw -C network
```Does you wireless device show an interface, eth1, hopefully?

---

