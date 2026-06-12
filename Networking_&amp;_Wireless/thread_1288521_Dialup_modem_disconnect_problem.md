---
title: "Dialup modem disconnect problem"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by justamel on 2009-10-11
Here's what I'm using: Presario 2100 notebook w/256M of RAM, Linuxant HSF Modem at 56Kbps max. ,Ubuntu 8.04, Firefox 3 Beta 5 browser.
 
I did archive searches for previous posts about dialup connection problems and found several. Have implemented the suggested fixes and am now able to connect to the internet using ppp directly and thru wvdial, BUT I get disconnects after max. 14-15 minutes (or less at times).
 
Also browsing (loading a page) with Firefox is VERY Slow!
 
Questions: Could disconnect problem be caused by Firefox running SO slowly??
Do I need more RAM for Firefox, or a different browser?
 
If this is not cause of the disconnects, then what is???
 
Hope someone can help.

---

### Post by GeorgeVita on 2009-10-11
Hi **justamel**, some ideas:

**Slow** browsing could caused either from 'heavy' pages or from an 'automatic' update (firefox?) and also your real connected speed. You can check data traffic download & upload from:
**System > Administration > System Monitor > Resources** (Network History)
When you are not loading a new page and this page has NO active running components, the '**Receiving**' rate must be around zero.

**Disconnects** may come from '**inactivity**' so reload a page to see if this altered and try to find any 'inactivity timer' to disable it (**ATS30=0**). Other cause could be '**incoming call** notification' if exists and it is enabled (***43#** in Europe).

>>> Post your Init strings to check.
>>> Check with other O.S. or ask a neighbor using the same provider to find other reasons.
 
Regards,
George

---

### Post by justamel on 2009-10-15
Update on this problem:
 
Not getting very far.
Tried the suggestion to add: S30=0 in initialization of modem to shutoff any inactivity timer. --- this seems to have had no effect whatsoever.
 
Still able to connect, but still getting sudden disconnect after random lengths of time.
No helpful messages that I can find in any logs. Just says "modem hangup"
 
Still wonder if disconnects have something to do with the SLOWNESS of Firefox???
 
I am accessing this forum on a WIN 95 system and it is much faster than what I am getting with Ubuntu/Firefox!!! (and this system has less than 64MB of RAM and modem is 33.6K max.) So, not very impressed as of now.
 
Still hope someone might have some further suggestions.

---

### Post by sir_cheats_a_lot on 2009-10-15
this is a problem with the crappy "free" linuxant driver.  pay the fee and they'll give you the fix for it, and you'll be able to cruise at the speed you are supposed to be connecting at. but really i'd just invest in a real modem.  can get an external serial modem for like $10-15 off ebay, and it'll work every time with no special driver...assuming your laptop even has a serial port.  there are some external usb ones that do work with the smart-link package in the repository.

---

### Post by justamel on 2009-10-16
Dear "sir_cheats_a_lot",
 
IF you had read my complete post you would know that I DO have the full speed Linuxant driver!!
Also, external hard modems are NOT just lying around and readily available everwhere!

---

### Post by sir_cheats_a_lot on 2009-10-16
> **justamel said:**
> Dear "sir_cheats_a_lot",
 
IF you had read my complete post you would know that I DO have the full speed Linuxant driver!!
Also, external hard modems are NOT just lying around and readily available everwhere!

i DID ready your COMPLETE post...maybe YOU didn't read mine?  no where in your post did you say you had purchased the full driver from linuxant, you just stated what your modem was capable of.   I didn't even suggest that external hard modems were just lying around everywhere.    i specifically said EBAY.   calm down; relax.

since you obviously didn't look i'll even give you a couple links:

[http://cgi.ebay.com/Zoom-56K-External-Dualmode-Serial-Faxmodem-1144L_W0QQitemZ200386235464QQcmdZViewItemQQptZPCC_Modems?hash=item2ea7f34c48](http://cgi.ebay.com/Zoom-56K-External-Dualmode-Serial-Faxmodem-1144L_W0QQitemZ200386235464QQcmdZViewItemQQptZPCC_Modems?hash=item2ea7f34c48)

[http://cgi.ebay.com/Best-Data-External-56k-Mac-Serial-Modem-336FLXMAC_W0QQitemZ190340123461QQcmdZViewItemQQptZPCC_Modems?hash=item2c5127cb45](http://cgi.ebay.com/Best-Data-External-56k-Mac-Serial-Modem-336FLXMAC_W0QQitemZ190340123461QQcmdZViewItemQQptZPCC_Modems?hash=item2c5127cb45)

[http://cgi.ebay.com/US-Robotics-External-56k-Serial-Modem_W0QQitemZ130336829386QQcmdZViewItemQQptZPCC_Modems?hash=item1e58ae2fca](http://cgi.ebay.com/US-Robotics-External-56k-Serial-Modem_W0QQitemZ130336829386QQcmdZViewItemQQptZPCC_Modems?hash=item1e58ae2fca)

---

### Post by ModelM on 2009-10-16
justamel:

If you are in the US I'll send you an external hardware dialup modem at no cost. Just PM me if you're interested.

---

### Post by justamel on 2010-03-16
This post is just to "conclude" this thread (even though it has been sitting awhile)

I "solved" the problem by following the suggestion of one forum member and with the generosity of another member I am now using an external hard modem.

I struggled to make the internal Conexant HSF modem work using the latest version of the Linuxant HSFdriver - paid for version 56K.. It will connect just fine, but will NOT stay connected reliably and when it does stay connected for any significant time it "slows down to turtle speed ie: 4800 bps!!! At this point it invariably disconnects.

Linuxant Support suggested trying different modem init. strings with different modulation settings ie: V34,V90,V92. None of their suggested strings made any significant difference. After I reported back my trials and results they informed me that "my problem was no longer being worked on and that info had been passed along to the developers". (presumably suggesting that maybe in the future the problem might be solved)

To conclude, I am NOT impressed with the Linuxant HSFdriver, nor with Linuxant Support, although of course they explicitly state up front that there are No Guarantees.

My only 'question' at this point is: Could it be that Ubuntu 8.04 (specifically this ver.) is the source of the problem, and/or could Ubuntu (any ver.) be the source of the problem?? (and I don't mean to "blaspheme" by asking this question :-))

One further comment for others who may try the Linuxant drivers

Test, test, test, with the Free 14.4 version first. I tried it using minicom and it connected up fine to a long distance number in Victoria, B.C., but it was not using TCP/IP protocols, etc. and I did not try connecting to my ISP because they told me years ago that "14.4 bps will not work on our system, it is too slow" I have recently connected using my "old" USR 14.4 external modem and it seems to do just fine, although it is slow on pages with heavy graphics, etc. (so much for the honesty of my ISP!!)

So that's it for now.

---

### Post by sir_cheats_a_lot on 2010-03-16
not so sure if it is exclusively an issue with Ubuntu specifically or if this issue is present in other distros.  i know that way back when i was first playing with linux, i was using Xandros OCE v2.0, it had picked up my old winmodem without a problem.  guessing it had the driver included.  don't remember how good the performance was though. was back in '99, but im thinking it was pretty close to what i was getting in windows just slightly slower.  I'll look into it sometime; though it may be a while before i can.

---

