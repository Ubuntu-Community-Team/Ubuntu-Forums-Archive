---
title: "Trouble with Broadcom in Lucid"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by p.s. on 2010-11-07
I just installed Lucid off an official CD onto a Dell Inspiron 1521 and the wireless doesn't work. It worked out of the box on 9.04, which is what I was most recently using.

The wired connection does not work either. I'm not sure why. 

I'm aware that I probably need some sort of driver for my Broadcom card. I read that I could get the drivers off the cd, and I think I did it (although possibly not correctly.)

I got what I think is the correct driver, bcmwl-kernel-source, and also something called fwcutter I think maybe by accident. They both show in the Hardware Drivers list, but when I try to activate them I get "System Error: installarchives() failed".

I tried using:

```
jockey-text -e
```but got the same result.

Synaptic is not open, nor is anything else.


Output of ```
jockey-text -l
``` is:

firmware:b43 - Broadcom B43 wireless driver (Free, Disabled, Not in use)
kmod:wl - Broadcom STA wireless driver (Proprietary, Disabled, Not in use)

My card is a Broadcom BCM4311.

Any help would be much appreciated, because I'm at a loss right now.

---

### Post by garvinrick4 on 2010-11-07
Here is a fix for that card a Dell thing with their proprietary drivers. Pain isn't it.
There are a lot of Broadcom driver posts that end in success, lot of Dells out there
and Ubuntu has it's own Dell forum. Enjoy your Ubuntu

Here is a link and also a post with success.
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)
[http://ubuntuforums.org/showthread.php?p=10055569#post10055569](http://ubuntuforums.org/showthread.php?p=10055569#post10055569)

---

### Post by p.s. on 2010-11-08
I managed to get the wired connection to work, got on Synaptic, and removed-and-reinstalled the drivers, and now it works.

Thanks for your response.

It's worth noting that if I hadn't been able to get on Synaptic I'd still be stuck. I still don't understand why I couldn't activate the drivers I pulled off the install CD. If anyone who has any ideas wants to comment, it may be helpful for a future user who doesn't have access to the internet on their machine.

---

