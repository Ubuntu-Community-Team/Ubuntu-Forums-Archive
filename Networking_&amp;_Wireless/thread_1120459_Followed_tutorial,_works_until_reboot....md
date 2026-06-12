---
title: "Followed tutorial, works until reboot..."
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by stevenrushing on 2009-04-09
I followed this tutorial:  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I have the bcm4306

It works!  You will notice that it talks about a hardy bug or whatever there at the bottom, and you have to add some commands to make the changes permanent...  BTW, I have 8.10.  I followed the commands, but after restart I lose wireless again.  Any thoughts? =)

---

### Post by rlzyoner on 2009-04-09
Bcm's can be a pain. I've one myself.

I usually follow this tutorial, note though, you will need internet access to follow it, use an ethernet.
This normally works for me.

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Just do it, then run

sudo ifconfig wlan0 up (replace wireless adaptor wlan0 with whatever your wireless is)

---

### Post by Ayuthia on 2009-04-09
> **stevenrushing said:**
> I followed this tutorial:  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I have the bcm4306

It works!  You will notice that it talks about a hardy bug or whatever there at the bottom, and you have to add some commands to make the changes permanent...  BTW, I have 8.10.  I followed the commands, but after restart I lose wireless again.  Any thoughts? =)

Can you post the results of lspci -nn and lshw -C network?  I just want to see what wired ethernet card you have.  It just might be a matter of using version 0.2 from the no-fluff guide.

---

