---
title: "Firefox is slow -- how do I approach this systemically?"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by xigen on 2010-10-25
Hi,

Is there a comprehensive guide to trouble shooting a slow browser?   

I am using firefox - and it is slow. (3.6.11,w/ ubuntu firefox modifications, better gmail, xmarks, downloadhelper;  ubuntu 10.4, fairly new AMD system w/ 4gig ram).

Specificaly, I would like to find out:
-- is the network / traffic
-- DNS
-- a firefox configuration
-- a plug in issue
-- Ads/junk 
-- Flash issues
-- *something I have not considered

Any suggestions on finding a systematic guide to figuring out what is making this so slow?

Cheers,

MW.:)

---

### Post by Perseverance on 2010-10-25
First of all define slow please.
State your Network adapter. There have been some problems with broadcom recently.

Recently there have been many topics about slow internet so here is what i figured out.
Test your connection with another browser (Chrome works great in terms of speed).

Outcome :
I. Still slow:
If your Look Up is slow(Stays for a good period of time at looking for [www.xxxx]("http://www.xxxx")....) disable all your IPv6 settings from the browser and system wide. Here is how to do it [http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html). I did them both.

 Change Your DNS to the one calculated for your best in here ([http://www.dnsserverlist.org/](http://www.dnsserverlist.org/) Works Great).

If you are using router to share connection with someone check his/her speed if it is slow call your network support center , else it may very well be plug in issue.

II. Works great in another browser.
Than it could be junk or flash problem. For the junk - Adblock Plus. If you are using x86 version of ubuntu than download(reinstall) flash player [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/).

Hope that helps.

---

### Post by Iowan on 2010-10-25
IPv6 is frequently blamed (sometimes guilty) for slow browsing. There are a few "How to disable" threads around - I'll try to find one...

---

### Post by piggyslasher on 2010-10-26
If your Firefox's download/network speed is slow, you might want to search around for IPv6 fixes.

However, mine (and a few others on this forum) was an all round slowness in the Firefox GUI (with 10-15sec lags!), and I upgraded the kernal as mentioned [here]("http://fb.me/we7tFztT"). Now the Meerkat is flying.

---

### Post by xigen on 2010-10-27
> **Perseverance said:**
> First of all define slow please.
State your Network adapter. There have been some problems with broadcom recently.


Slow = 25 sec to load 
[http://www.businessinsider.com/](http://www.businessinsider.com/)   or
[http://www.nytimes.com/](http://www.nytimes.com/)

My network adaptor ... where would I find that in Ubuntu 10.4?

---

### Post by Perseverance on 2010-10-27
> **xigen said:**
> 
My network adaptor ... where would I find that in Ubuntu 10.4?

```
sudo lshw -c network | less
```
We are probably interested in ethernet adapter

Also what are your results at my previous reply ?

---

### Post by TBABill on 2010-10-27
Lovinglinux has created a very thorough optimization of Firefox thread and several items within it could help with your issues.
 
[http://ubuntuforums.org/showthread.php?t=1193567&highlight=optimize+firefox](http://ubuntuforums.org/showthread.php?t=1193567&highlight=optimize+firefox)
 
If you are using 32 bit Flash on a 64 bit system, his firefox plugin will take care of getting you the right version of flash very quickly and will make upgrading to a newer version very simple. I didn't see a version (32 or 64 in your post).

---

