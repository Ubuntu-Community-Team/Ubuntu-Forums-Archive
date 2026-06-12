---
title: "Intermittent wireless connection"
date: 2012-12-15
forum: Networking &amp; Wireless
---

### Post by lurgee on 2012-12-15
Hi,

Last night I decided to try and set up my wireless again.  I hadn't bothered for months, having pretty much given up on it.

I'm using lubuntu, so processes might be a bit different from unbuntu, but don't be put off, ubuntu users.  Any advice is appreciated.

I went into Peferences > Software Sources > Additional Drivers.  I was informed I had a 'Broadcom 4312 802.11b/g LP-LHY' but the device was using a 'Broadcom linux STA wireless driver source from bcmwl-kernel-source (proprietary)'.  There wasa radio button allowing me to toggle between the latter and 'Do not use this device.'  I toggled to 'Do not use this device' then reinstalled the STA driver by toggling back to it.  The wireless light came on and I was able to connect to the internet!  Success!

BUT ...

I have to go through that process EVERYTIME I boot up.  It's like Lubuntu forgets what driver to use, and I have to go through the manual reinstallation to remind it.  then it owrks okay.  I'm using it just now.  No problem.  But when I switch off ...

So, what is happening?  I'm sure I'm missing something pretty obvious, but don't be afraid to spell it out for me in really obvious terms.  Having got thus far, I'd quite like to make this work properly.

---

### Post by haleleonj on 2012-12-15
There are extensive Broadcom tutorials available. These wireless cards are some of the most complicated to get working from my own experience. Read the tutorials carefully and only use a comprehensive tutorial. 

There are more tested more Linux friendly cards available which are approved by the free software foundation's Hnode project ([http://h-node.org/wifi/catalogue/en](http://h-node.org/wifi/catalogue/en)).

---

### Post by lurgee on 2012-12-15
Seems to have been resolved with this, courtesy of Wild Man:

> **Wild Man said:**
> Hi, please do:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

Now seems to be operating normally from boot up.

Thank you, might Wild Man!

---

