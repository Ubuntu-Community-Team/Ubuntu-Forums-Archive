---
title: "unstable wireless connection"
date: 2005-03-17
forum: Networking &amp; Wireless
---

### Post by bryan986 on 2005-03-17
I have a netgear wg111v2 usb adapter for wireless g internet

I got it to successfully connect to the inernet using ndiswrapper and the windows drivers that came on the cd with it, even though the result of ndiswrapper -l shows "hardware not present"

For the most part it seems to work ok, then once in a while it will just stop working alltogether, nothing will load

When it stops working, different things happen, never the same:
-sometimes when I go into the network settings the wlan0 is disabled, I try enabling it again, but that does not help, it just gets disabled again when I go back in, other times it starts working again
-other times I have to restart to get it to work again, which it does help most of the time, but even then it sometimes gets hung up on the part where it is configuring the network interfaces (or whatever that is called)

I have been unable to find when it stops working, it just seems to stop randomly, and I cant find any error messages, but I am a linux newbie, so if anyone wants me to run some command to find the messages to help debug, im all ears

Im using Ubuntu 4.10 (warty) with whatever came with it, the only extra thing I installed was the ndiswrapper tools to get the adapter working

This is my first real attempt to run linux, trying hard to get off windows, but its fustrating spending so much time configuring stuff, the usb adapter works just fine in windows without a hitch (I am dual booting with winxp pro)

---

### Post by bryan986 on 2005-03-17
I am using the wireless with dhcp and a wep key

attached is a screenshot when the internet craps out, there is nothing I can tell that says it is not working other than stuff not connecting

---

### Post by bobmitch on 2005-03-17
I have a netgear wg311v2 - I think the same as what you have, or at least the same chipset.

The latest Hoary kernels have drivers for this chipset built-in, and so do not require ndiswrapper.  

Assuming you are on Warty, it may be time to upgrade - or hold off for a few weeks till Hoary final comes out. :)

---

### Post by bryan986 on 2005-03-17
Decided to try out Hoary

Still needed to use ndiswrapper, but at least it detects the hardware as present this time, hoary uses the ndiswrapper tools 0.12 where warty used 0.10, so hopefully that helps...

so far so good, will post if I get anymore disconnections

---

### Post by bryan986 on 2005-03-17
Well scratch that, it was working for a while, but now the same problem started cropping up again, and now it takes 2 restarts to get it working again, what a pain!

---

