---
title: "ATI fglrx driver help"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by dlegend on 2007-12-02
I tried installing the fglrx driver using the article provided here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) but could not get it to work properly. I had to remove the driver and go back to the default settings. I have an older laptop (1.4 ghz with 32 mb video ram) and the card is a "Radeon RV250 [Mobility FireGL 9000]".

I couldn't tell from the article if my card is supported or not. I also tried installing Envy to automatically configure the ATI driver but got this:

```

python pulse.py ati
root@Se7en: /usr/share/envy# python pulse.py ati
Envy - Version 0.9.9
Ubuntu Gutsy 32bit
Your graphic card has been detected as a ATI Mobility / Radeon 9000
Your graphic card is supported by the legacy Driver
ENVY ERROR: ATI's legacy driver does not support your operating system

```

I was wondering then, is it worth installing the fglrx driver? Is there much performance difference then the default one provided? I have compiz fuzion running fine but I could use a boost in performance anywhere I can. Some effects like the water droplets in the background don't work for me (and open arena flickers to a black screen n back to normal when I play, though not sure if the fglrx driver will help).

I also read this article: [http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

I looked in my restricted drivers manager but couldn't find the "ATI accelerated graphics driver" option.

Anyway, I'm just looking for some help. It isn't 100% necessary but its something I'd like feedback on. This is also my first post on the forums. Thanks in advance =)

---

### Post by acoustibop on 2007-12-02
The current fglrx driver doesn't support your videocard/chip, dlegend.  The last one that did was the 8.28.8 one.

---

### Post by dlegend on 2007-12-02
> **acoustibop said:**
> The current fglrx driver doesn't support your videocard/chip, dlegend.  The last one that did was the 8.28.8 one.

Should I get/install the 8.28.8 driver then? Or should I just stick with what I got? Also, a link to the 8.28.8 driver would be nice. Thanks again =)

---

### Post by acoustibop on 2007-12-03
[This]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") should take you to the ATI page for the 8.28.8 driver, dlegend.

**Edit:** It will probably give better performance in 3D applications (games etc), but you won't be able to use Compiz etc at all.  Depends on which matters more to you, I guess.  If you want both, you could do as I do: have two Gutsy installations, one with each driver.  In my case, although the 7.11 driver is better for most things, installing it does seem to increase the sound latency for the system.  So an emulator like pSX, which depends more on low sound latency than video card capabilities, runs better on the 8.37.6 driver that installs with the Restricted Drivers Manager.

BTW thinking of it, AFAIK the Restricted Drivers Manager should show the 8.28.8 driver if your card can't use the 8.37.6 one.  It's possible that trying to install and remove the more recent driver has messed this up.  Perhaps reinstalling restricted-manager and restricted-manager-core might remedy this.  AIR I managed to do something like that once, and I think that's how I fixed it.

---

