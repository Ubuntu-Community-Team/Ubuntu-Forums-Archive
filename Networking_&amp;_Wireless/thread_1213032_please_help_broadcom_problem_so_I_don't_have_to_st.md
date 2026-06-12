---
title: "please help broadcom problem so I don't have to stick with windows ;("
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by brodymcd on 2009-07-14
To all:

I hope SOMEONE can PLEASE help me - I'm so frustrated... I think this is my last stab at staying with Ubuntu or even linux...

Here's the deal...

-I have a DELL Inspiron 1526 Laptop with Broadcom BCM4312 wireless
-I first got into Linux with Ubuntu 8.04... went through heck and finally got the Broadcom going.
-Upgrade to 8.10 was heaven... wireless jamming
-9.04 brought wireless DEATH... nothing worked... so I finally downgraded with a fresh 8.10 install, but then that was buggy, but it got fixed.
-I had to blow my whole lappy away and re-image from factory. Vista back (sigh) but working, I then got a wild hair and tried a fresh 9.04 install - wireless was FLAWLESS!
-within 48 hours wireless went to NOT WORKING at all... so I thought it must be an update.... finally got frustrated and went BACK to 8.10... now it won't work either.
-Had previously tried Mandriva 2009.1 with good luck, now it isn't working...
-Have a new eeepc 1000HA on which I put eeebuntu, which has run in a stellar fashion right out of the box, wireless is flawless... and it is eeebuntu 3, which is based on 9.04... 2.6.26.9-netbook

Can someone help me PLEASE slay the Broadcom monster or else I will have to use Vista?!?! I would PREFER to stay with Ubuntu, but will use any distro that works. Honestly, I would pay to fix this, just not the $250 Canonical fee... that's way more than necessary to fix something that should work... and almost the price of a new lappy.

THANKS for taking mercy on me in advance - I really am at wit's end.

---

### Post by drudogg on 2009-07-14
i have had the same problem. found a thread which helped me for a bit. reloaded and can't get back to where i was. it is broadcom.

here ya go:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by superprash2003 on 2009-07-14
also check out system->admin->hardware drivers

---

### Post by brodymcd on 2009-07-14
you mean you have fixed the problem in Jaunty using these steps?

---

### Post by drudogg on 2009-07-15
i got it working once, after also installing backport modules. it works for some people. 

also may need to search for b43-fwcutter there is another method with that. i have not yet tried it though.

---

### Post by drudogg on 2009-07-15
just got my stuff working. looks  like your card may be supported, a few different versions, so i am not sure... but it only took me one command to get it going. read the info on this link.

[http://www.linuxwireless.org/en/users/Drivers/b43?action=show&redirect=en/users/Drivers/bcm43xx#devicefirmware](http://www.linuxwireless.org/en/users/Drivers/b43?action=show&redirect=en/users/Drivers/bcm43xx#devicefirmware)

---

