---
title: "AT&amp;T Quicksilver &amp; 9.04???"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by Miakehl on 2009-07-24
Has anyone gotten a Quicksilver to work under Jackalope? I've tied the HSOconnect and Ozerodcoff method and It'll say it's connected but I can't connect to the GSM network. No mater what I try it says that... =\

Are there setting I don't know about to get it to work?


Really don't want to install windows to get GSM internet.....

---

### Post by williwinki on 2009-08-04
I tried for about 3 weeks (Quicksilver 867Mh).  Just doesn't work as far as I can tell.  Variety of issues.  Tried everything I could find here and elsewhere.

Tried to install from hard drive.  That failed too.  Seems that the drivers (ie for more than one device) just don't work.

I haven't gotten any replies to my posts.

This is my first try at installing Linux and it's left a pretty sour taste.  Guess this type of problem is why Mac platforms are no longer officially supported.

Going to try on an Intel based pc and see how it goes.  

Good luck anyway.

          Willi....

---

### Post by DonnieP on 2009-08-10
> **Miakehl said:**
> Has anyone gotten a Quicksilver to work under Jackalope? I've tied the HSOconnect and Ozerodcoff method and It'll say it's connected but I can't connect to the GSM network. No mater what I try it says that... =\
I did get the QuickSilver working with Jaunty using HSOconnect and Ozerocdoff.  What version of HSOconnect are you using and what did you enter in your connection profile?  I found that the HSOconnect 1.2 beta won't connect but the latest stable will connect - though not 100%.  Frequently I have to restart networking and reinsert the modem.

---

### Post by williwinki on 2009-08-10
It looks like I posted to the wrong thread.  I have a _Mac Powerpc Quicksilver_.  Sounds like the AT&T Quicksilver is a different platform.  I gave up trying to run Ubuntu on the Mac.  Trying on an i386.

Thanks for your reply.

---

### Post by DonnieP on 2009-08-19
> **Miakehl said:**
> Has anyone gotten a Quicksilver to work under Jackalope? I've tied the HSOconnect and Ozerodcoff method and It'll say it's connected but I can't connect to the GSM network. No mater what I try it says that... =\

Another way that I got to work is to use this command in terminal:
```
sudo pppd ttyHS1 460800 nodetach defaultroute noipdefault noauth lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','WAP.CINGULAR'" OK "atdt*99***1#" CONNECT' user WAP@CINGULARGPRS.COM password CINGULAR1
```

---

