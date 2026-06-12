---
title: "Can't connect to network -key changes randomly"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by zebra100 on 2009-01-15
Well, I finally have my Broadcom card working, but now I have another issue.  I can't connect to the router.  When I put the security key in and press connect, the connect icon appears to be trying to connect, and then I get the message "Authentication Required by network". When I click on the show password box, the key has changed to some other random number :( .  The card is talking to the router, I just can't understand why the password changes by itself. 

I've had a look at the troubleshooting guide, and it seems disabling ipv6 may be an option.  Let's see........

Any Ideas?


Chris.

---

### Post by Absinthe Minded on 2009-01-15
Hi Chris,

Are you using the Network Manager for your wireless settings, or something else?

Ta,
Nick.

---

### Post by Favux on 2009-01-15
Hi zebra100,  	

It sounds like you've run into a NM bug a bunch of us have encountered.  We found a workaround, see:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

Hope this helps.

---

### Post by phantom3113 on 2009-01-15
From the sounds of it, your card can find the network, so I don't believe it's a driver issue or anything. My card is a different model (Realtek) but your problem is identical to one that I had initially. How did you get Ibex? (That is, assuming 8.10 *is* the version you have.) Either way, when I first got 8.10, I had downloaded the torrent file of the .iso and burned it to disc and had this same problem when I installed. (Identical situation) Not knowing what to do, I went to 8.04. A series of events caused me to need to reinstall 8.10 and luckily I had a copy that was sent to me (from the request a cd on the Ubuntu site) and after install, never had that problem.

*whew* (sorry for the long post) My point is, that problem appears to be a disc burning/.iso downloading error. I suggest you request a cd like I did, and although it may take a while to get to you, it should fix your problem.

---

### Post by zebra100 on 2009-01-16
> **Absinthe Minded said:**
> Hi Chris,

Are you using the Network Manager for your wireless settings, or something else?

Ta,
Nick.

Hi Nick,

I'm using network manager, and it's driving me mad.

Regards,

Chris.

---

### Post by zebra100 on 2009-01-22
Still no joy.  I can connect using a wireless network (BT Openzone), but I can't connect to my wireless modem/router using secure settings. 

I am using V8.10 installed from a disk from Linux Format magazine.  I have re-installed twice, and the problem still exists.

I have also tried the fix here [http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650) which didn't work for me. 

This is driving me mad............

---

### Post by zebra100 on 2009-01-24
I'm going to try installing wicd instead of network-manager.  Hopefully this should do the trick.

On the bright side, installing Ubuntu on my laptop and desktop, alongside Vista and XP respectively (Dual boot), has prompted me to install Firefox and Thunderbird in place of Internet Explorer and Outlook.  What a difference.  I didn't realise MS Internet Explorer had so much baggage!:D

---

