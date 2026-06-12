---
title: "Edimax EW-7811Un"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by ppjdee on 2013-04-25
Anyone know a "work around" or something to make the wireless adapter work in Ubuntu 13.04? I haven't found anything from googling it. It keeps losing internet connection and clicking to reconnect every 10mins is getting old.

---

### Post by tjeremiah on 2013-04-26
I have a Edimax too and it uses Realtek drivers. For weeks now I have been looking for a solution for 13.04 because in my case the driver wont compile with kernel 3.8. I was told by one user I have to wait for Realtek to update their drivers for the new kernel. Still waiting.. 

I followed these instruction in the past but like mention above, they dont work in 13.04. 
[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

---

### Post by ppjdee on 2013-04-26
Yeah, I seen to stumble across the same info as you. Waiting is not my strong point lol. Hopefully soon they will release a updated driver, cause 50ft cables through the house isnt what the old lady really likes lol.

---

### Post by tjeremiah on 2013-04-26
im away from ubuntu until tomorrow but if you can, can you try this to see if it works. Its post 9 in this thread. 

[http://ubuntuforums.org/showthread.php?t=2092934&p=12620866#post12620866](http://ubuntuforums.org/showthread.php?t=2092934&p=12620866#post12620866)

---

### Post by ppjdee on 2013-04-27
> **tjeremiah said:**
> im away from ubuntu until tomorrow but if you can, can you try this to see if it works. Its post 9 in this thread. 

[http://ubuntuforums.org/showthread.php?t=2092934&p=12620866#post12620866](http://ubuntuforums.org/showthread.php?t=2092934&p=12620866#post12620866)

Hmm, it will be a few days, I lost my edimax adapter :( I think my cat hide it..(stupid spawn of satan cat)

---

### Post by tjeremiah on 2013-04-27
SOLVED with this post. Easier with the DEB. [http://ubuntuforums.org/showthread.php?t=2092934&p=12621449#post12621449](http://ubuntuforums.org/showthread.php?t=2092934&p=12621449#post12621449)

---

### Post by ppjdee on 2013-04-27
Awesome to hear. Still looking for my adapter but will try that asap. Thanks for the update.

---

### Post by juicyoner on 2013-08-10
Did that solution work for anyone?

---

### Post by kurt18947 on 2013-08-10
> **juicyoner said:**
> Did that solution work for anyone?

It has worked very well for me.  The only thing I've noticed is sometimes I see messages during software update/upgrade events.  I suspect they're something to do with DKMS in the .deb file.  Nothing has malfunctioned as a result AFAIK.  They flash by so quickly I can't read them, I just get the occasional word.

---

