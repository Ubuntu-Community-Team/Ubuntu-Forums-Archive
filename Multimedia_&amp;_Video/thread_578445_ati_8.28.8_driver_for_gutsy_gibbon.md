---
title: "ati 8.28.8 driver for gutsy gibbon"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by xeth on 2007-10-17
Running Gutsy Gibbon for a few weeks now and I've been fooling around with compiz and kde because the default driver won't enable the compiz effects. Something went wrong and the display became garbled or junky. I tried to use the default open source mesa driver and it has the same problem. Also did a dpkg-reconfigure, still the same.

It looks like my Mobility Radeon 9000 only supports the ati proprietary 8.28.8 fglrx driver but I cannot find any debian packages for it. I tried to recompile the driver from the ati website but I get a substitution error whatever that means.

Any ideas? Anybody has the time to teach me to compile the 8.28.8 driver? :)

thanks guys

---

### Post by bromix on 2007-10-17
have you tried the fglrx driver and xgl?

---

### Post by xeth on 2007-10-17
the fglrx drivers from the repositories doesn't support cards earlier than 9500.

I'm not familiar with xgl, I'll give it a try

---

### Post by bromix on 2007-10-17
There are multiple users who are using that card.  It does work.  I know the only way I could get compiz fusion to work with my ati card was to install xgl.  Let me know if you need any assistance. I'd be more than happy to help you.

---

### Post by ravalox on 2007-10-17
The problem is those drivers aren't compatible with the later versions of Xorg.  I recommend just using the open source ones; yeah the 3d performance sucks but it's likely going to improve now that ATI has opened up their specs.

---

### Post by xeth on 2007-10-17
I'm currently using the open source drivers but the display is still garbled.

---

### Post by hansie99 on 2007-10-19
I'm having the same problems with my ATI radeon 9000 card. It seems that this card is not longer supported because you need the ATI legacy driver. And the legacy driver is no longer supported by Gutsy. If tried to install it but no luck. Any one an idea how to solve this problem or do I really need to buy another graphics card?

---

### Post by Tarmatt on 2007-10-26
Same problem...
Still looking for a solution without any downgrade...

---

### Post by volty on 2007-10-26
Solution, assholes!

I have a Dell Inspiron 5150 with an outdated mobile radeon 9000. So the 8.28.8 drivers are my only choice. The good news, is that someone has a fix.

Go to: [http://www.phoronix.com/forums/showthread.php?t=4400](http://www.phoronix.com/forums/showthread.php?t=4400) and download the script mentioned (install-fglrx-debian.sh). When you start up your (K)Ubuntu install, ctrl-alt-f1 to get to the console, then run the script:

sudo sh install-fglrx-debian.sh -y (the -y flag is because the script is meant for a different Debian spinoff). It will take 5 mins to download the correct drivers for your card (8.28.8 for me), download the packages needed to compile the new drivers, then do everything and restart the computer. I am successfully running Kubuntu 7.10 with no problems. I'm going to guess that the fancy 3-d effects arent going to happen, but its no big deal.

---

### Post by Tarmatt on 2007-10-27
Well yes, the script install the drivers. And yes, it's impossible to deal with the 3D because :

```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 1.3.0.0
(WW) fglrx(0): detected X server is not compatible
(WW) fglrx(0): R200DRIScreenInit failed
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* * 
```

Will we loose a lot by downgrading to X.org 7.1 ?


PS: > Solution, assholes!
I'm not english, but isn't it quite rude ?

---

### Post by volty on 2007-10-27
Yes, it is quite rude. But you'll find that some people think juxtaposing rude words in strange places can be funny. (like me. ;) )

The solution is meant more for those who have difficulty even getting to the login screen (such as myself). Before this, I could not even load X. I think the fault lies with the age of the driver. It is so old that it does not support the fancy new effects. Short of contacting Ati and requesting that they support our outdated cards, I think you might be SOL.

---

### Post by jspangler on 2008-02-11
Thanks for this script! It makes everything oh so much easier. And yes, it is funny to put rude words in strange places.

---

### Post by edmondt on 2008-03-21
I have a 8500LE

wget [http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)
sudo sh ./install-fglrx-debian.sh -y

Looks like it is working on 7.10, with no 3D accel tho. If anyone can get it working please share :)

---

