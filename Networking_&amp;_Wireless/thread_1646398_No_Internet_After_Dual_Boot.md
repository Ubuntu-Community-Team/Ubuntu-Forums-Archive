---
title: "No Internet After Dual Boot"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by Pandalcc on 2010-12-15
I run Windows 7 64 bit on my main harddrive. I have a second hard drive that I gave a 350gb partition to, and installed Ubuntu 10.10 there. (dual booted) At first, the internet worked fine, until I booted back to windows, my internet does not work whatsoever, even when I want back to ubuntu, it did not work. I then formatted the partition with ubuntu on it, hoping to fix the problem. but it still persists in windows 7.
 
I need to know why this happened and how can I fix it?

---

### Post by Bucky Ball on 2010-12-15
Ubuntu has nothing whatever to do with your Windows partition. If your internet works in one and not the other, you have a problem with one of your OSs. If internet doesn't work in either, I imagine you have a problem with your internet connection external to your computer and any problems with either operating system's setup (especially if all was fine before).

I'd say it is purely coincidental that your internet went down after booting into Windows then Ubuntu and would perhaps start investigating router and modem. I am presuming you are talking about your wireless rather than direct cable connection.

If this is your setup, remove the router from the equation by plugging a cable directly from modem to computer and see how you go. If the cable works, plug a cable from your computer directly into the router, log on to the router's setup and check everything is right on the wireless setup.

Main point: if a cable from modem to computer gets you online, you probably have something amiss on your wireless router rather than your computer (as BOTH OSs can't connect wirelessly).

Again, your setup in Ubuntu has no effect or connection whatever with your setup in Windows. Good luck digging. :)

(ps: 10.04 is the LTS (long term support) release fyi.)

---

### Post by Pandalcc on 2010-12-15
Thing is, internet works on every other computer in my house, and it ONLY stopped working after I dual booted. This has happened before as well, I reinstalled windows the time before. I dont understand how they can be connected, but they are somehow.

---

### Post by Pandalcc on 2010-12-15
And I am on a wired connection.

---

### Post by Bucky Ball on 2010-12-15
Change your cable and see if it makes any difference.

---

### Post by Pandalcc on 2010-12-15
Yep I changed cables, tried the same cable on my PS3 which connects to the internet just fine. Somehow ubuntu changed the internet settings it seems, this is just a conclusion im jumping too-but it makes sense.

---

### Post by msandoy on 2010-12-15
Take a look at your DHCP settings in your router, There might be a DHCP lease problem. Linux will never change windows settings, and windows will never change linux settings.

---

### Post by Pandalcc on 2010-12-15
How do I go about doing that?

---

### Post by msandoy on 2010-12-15
If your IP address is 192.168.0.20 or something similar, the address to your router is most probably 192.168.0.1. In your web browser, enter this IP in the address field.
Depending on the router make, and since you do not know how to do this, I'm assuming it has the default user name and password. Different brands have different combinations, but you can try to log in with some of the following:
user: admin
pass: admin

user: admin
pass: password

user: admin
pass:

some routers even do not use user names, just passwords, then admin or password, or the brand name of your router might be it.

---

### Post by freacert on 2010-12-25
same here. Had to boot in windows xp, to try a windows cd, and after that no internet connection in ubuntu 10.4. 
wired internet connection to a hub. when i boot back into windows internet works. Had this experience before with ubuntu 8.10, and suddenly it appeared again, altough i know that the internet in ubuntu kept on working fine lately after the windows boot. 

one solution is to keep your computer turned off, and totally powered off, if laptop, no battery aswell, during several hours... one night of sleep solved the problem last time.

---

### Post by pmed on 2011-11-21
Hi [Pandalcc]("http://ubuntuforums.org/member.php?u=1206672"),

           I just had this same problem after installing Wubi. I'm pretty much sure that my wireless network card's MAC address was blocked by the router immediately after Ubuntu started. I don't have physical access to the router, but I could fix the problem by changing the network card's MAC address. It worked under both OS. There are a couple of softwares you can use for doing that in Windows. For Linux, you can do like it is explained in the following link:

[CENTER] [http://linuxhelp.blogspot.com/2005/09/how-to-change-mac-address-of-your.html](http://linuxhelp.blogspot.com/2005/09/how-to-change-mac-address-of-your.html)

[LEFT]     You'll have to do that every time you boot with Ubuntu. I'm sure there should be an way of making it permanent, I just can't look at this issue right now. I hope it will help you!
[/LEFT]
[/CENTER]

---

### Post by Bucky Ball on 2011-11-21
Wubi is a totally different kettle of fish so you're problem is not related and this thread is nearly a year old and quite dead.

You should post a new thread about your problem and you will have more luck.

---

