---
title: "ndiswrapper prevents computer from restarting -Stuck on POST screen"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by fallingleaf on 2009-03-15
I've been having this problem for years over several versions of Ubuntu and I finally got a hint from another post on the forum that wireless might be causing it.

What happens is I restart the computer and the POST screen comes up but never goes beyond that.  If I shutdown and press the power button it works fine.  After reading it might be wifi related I tested it by unloading the ndiswrapper module manually and then restarting.  Problem solved!

So, my question is what's the best way to make this happen automatically on every restart?

---

### Post by chili555 on 2009-03-16
If your computer won't get beyond the POST stage, then, I believe it has nothing to do with ndiswrapper, wireless or Ubuntu. At the POST stage, no operating system has been recognized or loaded. 

I suspect you have an intermittent hardware issue. Does it happen only when the computer is cold, but not when it's hot?

Is your motherboard's speaker attached? Any beep codes?

[http://en.wikipedia.org/wiki/Power-on_self-test](http://en.wikipedia.org/wiki/Power-on_self-test)

---

### Post by fallingleaf on 2009-03-16
> **chili555 said:**
> If your computer won't get beyond the POST stage, then, I believe it has nothing to do with ndiswrapper, wireless or Ubuntu. At the POST stage, no operating system has been recognized or loaded. 

I suspect you have an intermittent hardware issue. Does it happen only when the computer is cold, but not when it's hot?

Is your motherboard's speaker attached? Any beep codes?

[http://en.wikipedia.org/wiki/Power-on_self-test](http://en.wikipedia.org/wiki/Power-on_self-test)

I'm sure it's an Ubuntu issue because it never happened with Windows when I had Windows on the computer.  Also it always fails to reboot when I leave ndiswrapper loaded and it always succeeds when I manually unload ndiswrapper before rebooting.

I suspect that ndiswrapper is failing to turn off the wireless card or something (I don't know how this stuff works exactly) and it causes the BIOS to get confused on reboot.  turning off the machine and and booting never has the same issue.

My computer is a Thinkpad T60 laptop and I don't think it does beep codes but uses the status LEDs to show problems?  Nothing unusual there.

I just tested it again and now it is not even getting to POST.  The screen just goes black and the power light stays on but it never restarts.  Shutdown still works fine and restart still works if I unload ndiswrapper.

---

### Post by chili555 on 2009-03-16
Well! I am replying from my T60! What wireless card are you using that requires ndiswrapper? Is it possible to uninstall completely ndiswrapper and try the native driver? 

I love my T60 and would hate to see it get sick and die, I hope you are right.

---

### Post by fallingleaf on 2009-03-16
This one has an Atheros AR5212 card.  I think some of them came with an Intel card.  By default Ubuntu uses the madwifi driver with it but it only works if I am within about 10 feet of the AP.  I finally gave up and used ndiswrapper.  I'm sure the computer's fine.  In fact I just had the motherboard and fan replaced under warranty.  This problem existed before I did that in case you're wondering.

Just for fun I did try it with ath_pci and ath_hal and it restarts with them  loaded - further evidence that ndiswrapper is the culprit.

I do love my T60 too except for the stupid ATI video card.  Is it too much to ask to be able to use Google Earth **and** watch fullscreen video **and** use Compiz?

---

