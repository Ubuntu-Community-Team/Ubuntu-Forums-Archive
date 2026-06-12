---
title: "Well,I tried"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by overly_verbose on 2010-11-16
Moving back to 10.04, I've been trying for DAYS to get my wifi working properly. I've been scouring the boards trying everything under the sun,including attempting to install a new kernal, also a complete wipe/reinstall.

I hope I have better luck with 10.04 or I'm ringing the bell on Ubuntu all together.

---

### Post by LeMeun on 2010-11-16
You are not alone

Please tell us what wifi adapter you are using and what are your issues?
In other terms verbose verbose ;)

---

### Post by deconstrained on 2010-11-16
The first step is identifying what your hardware is. I assume you've already tried 'sudo lspci -v | less', looking for your wireless NIC in that list, and modprobing the module corresponding to it? If the native Linux module(s) don't work, you'll need to look into configuring ndiswrapper to work with a vendor-supplied driver.

---

### Post by TBABill on 2010-11-16
Every version of Ubuntu and any other distro automatically detected and downloaded the correct driver for mine....till 10.10. The driver downloaded and installed fine, but apparently something Broadcom has done with their driver automatically enables it soft and hard blocked, so additional steps are required to unblock it. It's maddening and there is no way to know until someone trips over the answer and posts it for others to find.
 
I feel your pain. I had thought my problem with 10.10 was Ubuntu's fault and I was quick to state how I would not upgrade all my machines and 10.04 was better. However, once I got the answer to the problem I slowly (seriously...one machine one day, another a day or two later) started to upgrade each and deal with its issues. 10.10 was the most I have struggled with moving to a new version and I did not do the upgrade...fresh installs.
 
Anyway, knowing the frustration you are feeling if you can post some info some others can do some digging on your behalf as well and help you get it working without going back to 10.04. There is certainly nothing wrong with 10.04 and its support is much longer than 10.10, but if you want to use 10.10 there is lots of help here if you are patient enough to post the info and allow time for others to walk you through it. I now have 10.10 on all but 1 and it's finally working great for me but the trip getting there was not fun at all.
 
Best of luck either way.

---

### Post by linux-hack on 2010-11-16
as **deconstrained **said you can use the windows drivers with **ndiswrapper **. it work pretty well.

---

