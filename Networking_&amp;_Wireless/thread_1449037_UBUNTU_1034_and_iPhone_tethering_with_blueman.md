---
title: "UBUNTU 10:3/4 and iPhone tethering with blueman"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by ugguk on 2010-04-07
hi everyone. I posted this same thing on the blueman forums (less of a population). I thought I'd post it here as well. I'm a recent convert and am a fanboi but my frustration with this bluetooth deal is getting out of hand.
 
Let me start by saying I'm a complete newb to ubuntu and blueman. 
 
My problem is trying to get blueman to work with iphone tethering, again. I've searched the forums and tried the restarting method; still no dice.
 
I managed to get the tether working properly at one point in time. I then tried to install some flash player which caused errors in other departments. I reinstalled ubuntu and fully updated it to fix the errors. I completely updated ubuntu and installed blueman through the software manager gui. 
 
I noticed a few things different this time when installing blueman. First, blueman didn't remove the gnome-bluetooth program like it did before. Second, both bluetooth managers appear in the tray up top. Third, blueman will not tether properly. 
 
I've managed to pair the decives properly and my iphone even says it's tethered when I select it as an access point in blueman. It will not actually tether providing interwebs to my ubuntu OS. 
 
1. What gives?! Before, any time I would select my iphone as an "access point" a little green ball would appear in the bluetooth icon and it would access the internet. 
 
2. Also, what do my settings under "local services" need to be set to? Do I need to allow blueman to manage all network activity? Do I need NAT enabled? Do I need DHCP checked? Do I need to set as an access point and/or a group network!? 
 
Any advice/recommendations to people working through this would be great. I've tried a lot of things.

---

### Post by ugguk on 2010-04-07
This is not the answer:
[http://ubuntuforums.org/showthread.php?t=1195655&highlight=iphone+blueman](http://ubuntuforums.org/showthread.php?t=1195655&highlight=iphone+blueman)
 
This sounds similar but is unanswered:
[http://ubuntuforums.org/showthread.php?t=1331070&highlight=iphone+blueman](http://ubuntuforums.org/showthread.php?t=1331070&highlight=iphone+blueman)
 
This is not the answer:
[http://ubuntuforums.org/showthread.php?t=1444253&highlight=iphone+blueman](http://ubuntuforums.org/showthread.php?t=1444253&highlight=iphone+blueman)
 
and this doesnt cover AT&T:
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)
 
The closest thing to a solution is:
[http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html)

---

### Post by ugguk on 2010-04-07
Here is a USB solution for jailbroken iphones:
[http://ubuntuforums.org/showthread.php?t=1364032](http://ubuntuforums.org/showthread.php?t=1364032)

---

### Post by ugguk on 2010-04-07
if you've installed it through the software manager - remove it and gnome-bluetooth
```

sudo apt-get remove gnome-bluetooth
sudo apt-get remove blueman
sudo apt-get remove bluez
```

In Ubuntu, add blueman repositories by issuing this command:
```
sudo add-apt-repository ppa:blueman/ppa
```

And to install it run:
```
sudo apt-get update
sudo apt-get install blueman
```

Now pair your iphone and your PC (other posts cover this)
Right click the blueman bluetooth icon --> bluetooth devices, ensure it's bonded, trusted and set to a network access point (in that order).

This worked for me please let me know if you run into problems.

---

### Post by ugguk on 2010-04-08
Should I make this into a HOWTO? I couldn't have been the only person with this problem.... or maybe I am that dumb.

---

