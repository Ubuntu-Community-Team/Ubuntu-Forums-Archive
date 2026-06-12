---
title: "wifi detected but not connecting"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by nbulchandani on 2010-04-01
hello,
I just installed ubuntu 9.10 in my freinds laptop and it has a realtek 81878 wireless card...it detects the wireless networks but when i connect it just keeps on asking for the authentication key again and again...
To help you more,,,
lsusb gives me
RTL8187B wireless 8;odba:8189
Thanks..

---

### Post by timjayko on 2010-04-01
what does ifconfig -a give you for you wireless card should be labeled wlan0 something like that.  is it being assigned an inet address?

---

### Post by nbulchandani on 2010-04-02
Yes,,,there is a Wlan1...but no inet address assigned:(
Thanks

---

### Post by nbulchandani on 2010-04-02
I downloaded the official driver from realtek site...now ifconfig -a
gives wlan2 with an inet address assigned but does not connect...now what?
Thanks

---

### Post by Irv2 on 2010-04-02
Sorry this is not immediately solving your problem, but I hope it may shed some light.

I have a similar problem, but I can make it appear and make it go away by switching the kernel when I boot.

I have several kernel releases on my PC from 2.6.28.13 up to 2.6.31.20

If I boot from 2.6.28.13, my wifi connection works instantly with no problems.  When I switch to any more recent version I can "see" my wifi router, but it refuses to make a connection.  As soon as I reboot back to 2.6.28.13, everything works again without my making any changes.

If you have that kernel, it would be really interesting if you could try it.

I wonder if anyone knows of any log files that the wireless software might create while it is making connections?  That might give a clue to what is happening.

---

### Post by nbulchandani on 2010-04-02
Please help me some one....don't we have any wifi experts over here
thanks

---

### Post by nbulchandani on 2010-04-02
can anyone tell me if i use xp driver with ndiswrapper....ny guide for it?
Thanks

---

### Post by nbulchandani on 2010-04-02
any ideas nyone....m fed up:(

---

### Post by eltonw on 2010-04-19
> **nbulchandani said:**
> any ideas nyone....m fed up:(

A look through the **[COLOR="Red"]sticky[/COLOR]** post at the _top of *this* forum_ might be of help:[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

HTH...:)

---

