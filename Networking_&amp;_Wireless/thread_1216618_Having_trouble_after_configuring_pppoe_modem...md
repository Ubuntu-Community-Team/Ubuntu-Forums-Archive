---
title: "Having trouble after configuring pppoe modem.."
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2009-07-18
After configuring my pppoe modem .. 
even though I was able to access Internet but I had some trouble with the network manager.

I used this command to configure the modem..
```
sudo pppoeconf
```

and followed the instructions..

But after configuration the options showed by my network manager changed and started looking like this.. (see the attachment)

so as a result.. I am unable to use the dhcp connections...(but modem works ppp0)
It doesn't respond at all and keeps on showing the internet disconnected symbol..

ne suggestions..??

---

### Post by shredder12 on 2009-07-19
Oh common guys..!! 
is there no solution to this problem..

---

### Post by ZhuaSD on 2009-07-21
I have this problem too, icon is x'd out.  But I am online with no big problems.  

Make sure pppoe is configured right, and read [this]("http://ubuntuforums.org/showthread.php?t=1147360") thread.

Check what plog gives you.  If nothing, then try my fix in that thread after jfbilodeau's fix.

If pppoeconf returns cannot make connection, you probably already have a connection running.

I just have to turn the connection off and then on again, and all is well...

:)

---

### Post by superprash2003 on 2009-07-21
hopefully this should sort out the device not managed error [http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html)

---

