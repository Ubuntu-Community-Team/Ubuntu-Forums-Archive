---
title: "Rediculous internet speed"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by xtremesupremacy3 on 2009-10-31
Well, this problem occured while using Jaunty and now in Karmic it seems to be getting worse.

Heres the background.
I have wireless (wlan0), and a nice router in the livingroom. My ISP has given me nice Fibrepower internet which means 60Mbs.
I got incredibly slow internet on here and when on Windows its perfect.
So I learned about ipv6 problem and got rid of that so ipv6 is disabled and it appeared to work. But not so fast.
Now it seems to work with bursts of energy. One moment its nicely flying through pages of internet or downloading, the next its taking 2/3 mins to load up a google page. It's so for taken me 1/2 hour to send an email with 52Kb attachment...and its only halfway.
Downloads are the worst...I used to be able to get about 1.5 to 2 Mbps now its refusing to go above 15kbps.
Please help this is not funny anymore, and btw, I have a lovely atheros card :-S

---

### Post by xtremesupremacy3 on 2009-10-31
Hey just an update to my case.
This problem is not caused by Ubuntu, neither by hardware.
It was and still is my lousy ISP.

If you live in the Netherlands by the way, do not even think about UPC Fibrepower. What a joke!

Anyway, as far as I'm concerned: Solved

---

### Post by xtremesupremacy3 on 2009-11-20
Unfortunately, I was wrong, and it was not my ISP.

I am still having problems.

Anyone have any ideas?

---

### Post by wilee-nilee on 2009-11-20
I would try using a live Cd to see if the problem persists, I think you can download to a USB while using a live CD to check speed.

---

### Post by Logan1985 on 2009-11-20
is the first DNS server in /etc/resolv.conf what you would expect it to be?

This ain't going to cause such slow downloads..but I did have an issue with DNS when I first installed 9.10 on my work PC...a recent change to the DNS servers in the office didn't affect windows PC's but it was waiting to time out in Ubuntu before trying the next DNS entry.

Made loading pages painfully slow. 

Worth a look I guess.

---

### Post by xtremesupremacy3 on 2009-11-23
Well, I have tried the DNS change, and although the DNS was set up wrong, changing it made no difference at all.

As for a live cd, well, I have a sister who has switched to Ubuntu about a week ago and she has the same trouble. So I don't think a live cd will help much.

One interesting this however is this...up until now it was thought that the internet was the big problem, whether it was Ubuntu having wrong settings, or whether my ISP was being a pain in the *****...well, now my impressions have moved slightly.

I have a usenet account and these speeds are greatly affected, so I wanted to route the port in my router...it took me 5 minutes to connect to the router. Now if it has problems reaching the router, not the internet, then surely theres a problem here with Ubuntu?

Well, this is my plan: I am going to see if there are any documented cases with my ath9k, and see what I can do, I'll post my findings.

In the meantime, if anyone has any ideas, please let me know

Arthur

---

### Post by Marogian on 2009-11-23
What wireless card & driver is it?

Run "lspci" in terminal to determine the wireless card (if its a PCI card).
Right click on the wifi panel => connection information for the driver.

Once you find that out you can search the forums for problems specifically with your wireless card/driver...

Edit: Oh sorry, you said you have ath9k driver. Coincidentally thats the same driver the laptop I'm using is on and it works fine... ^_^

Sorry I can't help...

---

### Post by xtremesupremacy3 on 2009-11-23
Marogian: No need to apologise, sometimes its just nice to know people actually listen like all you fantastic people.

After some research which only took 10 mins...weird.

I noticed this is in fact a common problem, and some suggest that installation of the backports of karmic may fix it.
Let's hope so, that's what I'm trying.

Anyway, for those experiencing similar problems, check this page:

```
http://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg02159.html
``` for the problems and possible solution is found here:

```
http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1819359.html
```

Momentarily I cannot confirm nor deny the fix, but will edit accordingly once I have tested it.

EDIT: Well, after having tested this possible solution, I didn't notice any changes.
However, I disabled the ath9k module and used a driver for windows using ndiswrapper and this has now changed my status:
I have fast internet, increased signal strength, a steady connection and all is well... SOLVED

---

### Post by bean1945 on 2009-11-23
I  had similar problems with ath9k (see slow wireless adaptor). When I switched to ndiswrapper the speeds increased even though ndiswrapper did not load the n driver.
There is something very wrong with ath9k!

---

