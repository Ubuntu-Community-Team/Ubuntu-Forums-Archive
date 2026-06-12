---
title: "Wireless Failure with Verizion Westell A90-327W15-06 Router"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by lswartz on 2009-03-20
I can connect via ethernet but not wireless. There are no problems connecting wireless with other computers using windows xp pro with this westell modem. I can connect to 2 other hotspots with my mini so I think it is an issue between the mini & the westell modem. Although, it did take about 4 failed attempts to connect at a Panera Bread Cafe. After it connected for a few minutes I restarted it to see if it would connect, which it did right away.

I have followed this guidance [https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html) where possible as Dell doesn't let me see the hardware or the driver. I got down to IPv6 Not Supported & that command does not work.

On day 3 with Ubuntu so I don't know what to edit out below.

1. Dell Mini9 Ubuntu 8.04 hardy lpia & Westell A90-327W15-06 modem/wireless router for Verizon.

2.  lspci
deleated............

10. sudo /etc/init.d/networking restart

---

### Post by lswartz on 2009-03-21
YAHOO!!!!!!!!!!!! It is fixed. :popcorn::popcorn:

Verizon did a firm ware upgrade online & it works just fine.

---

### Post by fleasbaby on 2009-06-06
Hi! I have Ubuntu installed using Wubi and all looks fine, but like you before the upgrade I cannot connect wirelessly in Ubuntu. I can in Vista though...

I tried asking Verizon, but the first time I called the twit on the other end patched me through to westell's technical support which was closed for the day, and second time, a different person tried to remotely access me, but their software for this does not support Ubuntu, so she effectively gave up...

What were the magic words that got them to do the upgrade? Every time I mention it I get stony, confused silence on the other end of the line...

---

### Post by AUP on 2009-07-11
I too have experienced the same issue.  My wireless laptops worked well for months after having Verizon's A90 wireless router.  Suddenly, both laptops could no longer connect regardless to what I did with the router or the laptops.  Direct connection worked find.  A friend came over with a laptop and it connect ok with left me perplexed.  

One of my laptops was running Windows XP and the Other Vista Ultimate.  I could not find a common denominator to the problem.  Finally, I went on-line to Verizon and found this link to download a tool to search the problem.  [http://www22.verizon.com/ResidentialHelp/FiOSInternet/Troubleshooting/Connection+Issues/Connection+Issues.htm](http://www22.verizon.com/ResidentialHelp/FiOSInternet/Troubleshooting/Connection+Issues/Connection+Issues.htm)  

The troubleshooting tool ran it's course be appeared to no find a solution.  I then booted for the 12th time (no different from the first 11 times) and both laptops were able to connect.  I believe it scan somehow fixed the problem.

---

