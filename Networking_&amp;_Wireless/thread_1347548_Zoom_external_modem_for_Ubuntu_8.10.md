---
title: "Zoom external modem for Ubuntu 8.10"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Cariboukayak on 2009-12-06
I have a Compaq Presario with the tricky HSF modem and Ubuntu 8.10. Being a nooby and having tried to get it working several times, I have given up because I dont really understand what I'm doing and am quite sick of the hassle.  I want to get an external modem, and want to buy this one today. Is there any reason this one wont work? Should I anticipate more troubles in trying to get this to work or is this likely to be a good way to go?

[http://www.bestbuy.com/site/Zoom+-+56K+V.92+USB+Mini+External+Data/Fax+Modem/8397923.p?skuId=8397923&ci_src=14110944&ci_sku=8397923&ref=06&loc=01&id=1186004321251](http://www.bestbuy.com/site/Zoom+-+56K+V.92+USB+Mini+External+Data/Fax+Modem/8397923.p?skuId=8397923&ci_src=14110944&ci_sku=8397923&ref=06&loc=01&id=1186004321251)

---

### Post by gordintoronto on 2009-12-06
The manufacturer claims it's compatible with Linux.  From their web site, some useful links:
[http://www.zoom.com/techsupport/dial_up/linux.shtml](http://www.zoom.com/techsupport/dial_up/linux.shtml) 

At best, connecting to the Internet using a dial-up modem is painful.  An HSF modem is even more so.

Did you look at this thread:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8225398](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8225398) 

It is tagged as "solved," so it might be worth one more try.

---

### Post by Cariboukayak on 2009-12-06
My hope that this would be straightforward have been dashed. the instructions say if my exact kernel is not listed, to update my kernel. BUt my kernel appears more recent than the drivers, and I dont see how to get a driver for my kernel which is 2.6.27-7. In fact I'mnot even sure which files are the drivers, but I know there are no folders higher than 2.6.20-xx

I have no freaking idea what to do. 

I have read that thread before, but thanks, but thats even worse. I'm a noob. I dont understand most of this stuff.

---

### Post by Cariboukayak on 2009-12-06
I installed the most recent driver that came with it. Gnome ppp can find and initialize the modem but does not connect. In the log I get

"Check permissions or specify a "pppd path" (xxxx) in wvdial.conf      

(xxx) is a word where I cant read my own writing. :p

Dont know what to do! Starting pppd hoping for the best

Unable to run /usr/sbin/pppd."

---

### Post by almack1 on 2009-12-06
Walk away from it for today. Go back to it tomorrow, it always works for me to take a break. Your mind will be still working on it in your sleep and the answer may just pop into your head.

---

### Post by _duncan_ on 2009-12-07
> **Cariboukayak said:**
> I installed the most recent driver that came with it. Gnome ppp can find and initialize the modem but does not connect. In the log I get

"Check permissions or specify a "pppd path" (xxxx) in wvdial.conf      

(xxx) is a word where I cant read my own writing. :p

Dont know what to do! Starting pppd hoping for the best

Unable to run /usr/sbin/pppd."


You need to add your user ID to the 'dip' group by entering the following command in a terminal:

```
sudo adduser [COLOR="Blue"]userID[/COLOR] dip
```

where [COLOR="Blue"]userID[/COLOR] is your actual user ID.

[edit] logout and login again for the changes to take effect.

---

### Post by Cariboukayak on 2009-12-07
That got me connected, thanks. But my connection speed is 1KBs....

---

### Post by _duncan_ on 2009-12-07
Sorry, I have no experience with that specific modem. I'll just bow out and let someone else take over from this point.

I'm glad you are at least connected though.

---

### Post by Cariboukayak on 2009-12-07
I got the modem working faster, at least temporarily. Zoom will not support it for Linux. ](*,)

But now my wireless stopped working....:???:

Edit (its working again...dont know why)

---

