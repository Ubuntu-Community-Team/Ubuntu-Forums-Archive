---
title: "Wireless Constantly drops out"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by D.horse on 2010-09-15
Hello,

I have been running Ubuntu for 2 years and have not had a problem like this.  Randomly one day my wireless dropped out.  I can see other networks on my laptop, but they are all locked so i cant test and see if i can connect to them so i went to my friends house and was connect fine for over an hour.  

Also my PS3 and my windows box connect to my router and internet just fine.

I then assumed that this was a hardware issue then with my wireless card on my laptop.  So i called up lenovo and they sent me a new wireless card.  I installed it and still had the same problem.


Lenovo t400
Intel 5300 Wireless
Ubuntu 10.4

Router
Dlink-655

I realixe i am not giving to much information, let me know what you need  and i will provide it.

I tried buying a new router now and it worked great!!!..... for an hour.  Now it is doing the same thing.

---

### Post by boarder428 on 2010-09-16
how close are you to your router?  I have one labtop that gets a poor signal/connectivity and it took me a while to figure it out because the same computers wireless works fine when booted to windows.  It just seems that the adapter is not supported well under linux.  I'm still trying to figure out a solution.  I suppose purchasing a usb wireless adapter that is known good with linux may be a better option.

---

### Post by kreggz on 2010-09-16
Are you saying it drops out randomly?

If so, how frequently.

Can you post the output from when you do:

Ubuntu Menu\Accessories\Terminal

Type: dmesg 

Just copy the lines which say wlan0

---

### Post by zacharyr on 2010-09-16
I'm having similar issues. This is my dmsg output: [http://pastebin.org/879623](http://pastebin.org/879623)

It definitely looks like something is going wrong.

---

### Post by kreggz on 2010-09-16
Looks like the WiFi card isn't compatible with Linux but was made for Windows. There is a bug report created for this WiFi chip, looks like others have had the same problem.

Typically Intel/Broadcom cards are the best.

You should look into [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

But it is fairly complex to setup.

---

### Post by zacharyr on 2010-09-16
I have two wifi cards running right now and my connection keeps dropping. The built-in card is a Broadcom BCM4306 802.11b/g that I believe is not usually expected to work with Ubuntu. The USB card is a Belkin F5D7050 ([http://linuxsoftwareblog.com/blog/?p=30](http://linuxsoftwareblog.com/blog/?p=30)) that worked natively when I first plugged it in.

Now it can see wireless networks, but it can't get an IP address.

---

### Post by zacharyr on 2010-09-16
I followed the instructions in this article: [http://linuxsoftwareblog.com/blog/?p=30](http://linuxsoftwareblog.com/blog/?p=30)

I now get a different kind of output from dmesg: [http://pastebin.org/887132](http://pastebin.org/887132)

Trying to make heads or tails of this...

---

### Post by kreggz on 2010-09-16
What is your Wifi channel set to? Maybe change it to something like 7.

---

