---
title: "coffee shop wifi"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by bishounen on 2010-11-05
Ran into an interesting problem last night.  I stopped by my local coffee shop to sit and have a cuppa and browse the internet on my laptop.  While the coffee was great, I could not for the life of me connect to the wifi when booted into Ubuntu (Dual-boot 7 and Ubuntu using Wubi) .  The wifi monitor would just spin and spin and then tell me it wasn't connected.

So I rebooted into 7 and when I tried to connect it started asking me to set up a router, wanting an 8 digit PIN.  At this point I just figured that the wifi was broken, but upon looking around me I could see other people online.

Now, this is an UNencrypted public network, so I shouldn't have been having problems.  I went to the cashier/order-taker person and told them about my issue, and they told me I needed an 8 digit PIN to access the wifi.  They handed me a slip of paper with the PIN printed out from a little machine next to the register and it worked when I fed it into 7.

I then rebooted into Ubuntu and tried again with PIN in hand.  No dice.  Ubuntu never prompted me to enter the PIN.  It would just spin and spin and then quit.

Has anyone else here ever run into this type of locked-down wifi?  What do you do with it in Ubuntu?

---

### Post by bishounen on 2010-11-05
I've done a bit of research, and this is apparently what is called a "Captive wifi portal".  There are two types of these.  One allows you to connect normally but redirects your traffic once you start to surf to a landing page where you have to sign in or pay up.  The other kind uses the PIN method I mentioned previously.

So what do Ubuntu users do about needing a PIN if the Wifi manager doesn't recognize this kind of setup?

---

### Post by grahammechanical on 2010-11-05
With a secured network it is not just the password that is encrypted but also the wireless traffic between the computers and the wireless access point. The network that you are trying to get access to is in fact secured. The PIN is a form of password. This method is also called WPS or Wifi Protected Setup. There are Wikis explaining it all.

Check out these links.

[http://sourceforge.net/projects/wpsd](http://sourceforge.net/projects/wpsd)  or

[http://wpsd.sourceforge.net]("http://wpsd.sourceforge.net/")    wpsd = Wifi Protected Setup Daemon. I do not vouch for this utility or recommend it. I found this link a few weeks ago when I was trying to help someone else with a problem like yours.

If Ubuntu is to have a future on mobile devices then WPS should be standard and easy to use. Maybe it is in the netbook versions. Maybe the developers need a hint of the direction to go in.

Regards.

---

