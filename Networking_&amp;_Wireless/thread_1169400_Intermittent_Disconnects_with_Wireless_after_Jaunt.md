---
title: "Intermittent Disconnects with Wireless after Jaunty Upgrade"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by bobnutfield on 2009-05-25
Hello Everyone,

I am having a problem with wireless disconnects after an otherwise smooth upgrade to Jaunty from Intrepid.  It is hard to diagnose because there are no log files and kernel messages reveal nothing.

Basically, the wireless connects just fine to my WPA-PSK network and stays connects for a period of time, but then unexpectly just notifies me that it has disconnected.  It easily reconnects with network mamager, but then will disconnects again some time later, which could be five minutes or 30 minutes, no set pattern.  It is definitely an Ubuntu problem as this laptop is triple booted with Fedora and Slackware, where the problems does not exist.  This started immediately after the upgrade to Jaunty and did not occur in Intrepid.

This is a wireless RTL8187B (internal USB which uses the RTL8187 driver).  

I am wondering if anyone knows how to start diagnosing this issue.  IPV6 is enabled and I am wondering if this could be the cause.   

Thanks for any replies for suggestions.

---

### Post by bobnutfield on 2009-05-25
Well, research suggests that it *might* be ipv6 causing this.  There is at least one other thread with the same issue.  I installed the 2.6.29.4 kernel from here:

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html]("http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html")

Followed the instructions to disable ipv6 and so far so good.  I will report back and tell everyone whether this fix works or not.  It may benefit those upgrading with similar hardware.

---

### Post by bobnutfield on 2009-05-25
Well, it has been up an hour now with no disconnects.  Before the fix, I was getting a disconnect approximately every 5-10 minutes.

So, I am giving this a *cautious* affirmative to the above fix if anyone else is having this issue with losing your wireless after an upgrade to Jaunty.

---

### Post by bigboss0101 on 2009-07-10
Using Jaunty, Netgear Wireless Router (WGR614 v7).
Similar problem here. But my disconnects are not so frequent. They happen once in every 3 or 4 hours. Whats the exact prob and whats the fix for this?

---

### Post by danevans29 on 2009-08-06
I am having the exact same problem with my Acer Aspire 5572 - intel wireless 3945ABG built in.  Connects fine but disconnects after 5-30 mins, then reconnects automatically.

Such a pain really.  Never had this issue with earlier versions of Ubuntu with same notebook.

---

### Post by Soldeace on 2009-08-06
I've been facing this problem with a RaLink RT61 PCI. The link quality was terrible and I was disconnected from time to time. I tried alternative drivers, network managers, Debian-based distributions and computers and the damn thing only worked with Windows XP.

Anyway, yesterday I did something really simple which should be the first in my list: disable DHCP. The wifi connection is now working magically well with a static IP. 

But it may be just coincidence. I'm gonna test it along the day and come back here in case of failure.

---

### Post by superprash2003 on 2009-08-06
there a lot of similar threads i think this is related to that [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

