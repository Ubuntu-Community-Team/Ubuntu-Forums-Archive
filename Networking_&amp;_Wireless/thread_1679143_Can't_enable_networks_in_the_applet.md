---
title: "Can't enable networks in the applet"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by ElPeski on 2011-01-31
I'm using Ubuntu 10.04 on my old HP laptop, and I can't enable ANY networks (ethernet and wifi) with the NetworkManager applet.

This started after suspending the laptop. It wouldn't wake up, so I had to make a button shutdown.

The "Enable network" checkbox apperars unchecked, but when I click it it doesn't get checked.

The interfaces themselves are enabled and working, since the led on the ethernet plug is lit, and I can get a wifi AP list with iwlist scan (but I have to enable the wifi card first with ifconfig up)

I've tried reinstalling the network-manager packaged, but it didn't work

---

### Post by AlexQM on 2011-01-31
You might find that WICD Network Manager will work for you, find it on the Ubuntu Software Centre

Alex

---

### Post by grahammechanical on 2011-01-31
May I quote you something from the Wireless Trouble Shooting Guide? It may not be appropriate.

> Some  laptops have a controller chip on the motherboard that is only  accessible through a different OS.  If you have turned off your wireless  adapter in a different operating system, you may have to boot back into  that OS and enable the card before it is accessible to Linux. 

Regards.

---

### Post by ElPeski on 2011-01-31
> **AlexQM said:**
> You might find that WICD Network Manager will work for you, find it on the Ubuntu Software Centre

Alex

I'll have to look for the package, since I can't connect to the Internet without my networks enabled, and the Software Center refuses to install anything from the CD. But I'll give it a try.

> **grahammechanical said:**
> May I quote you something from the Wireless Trouble Shooting Guide? It may not be appropriate.

Regards.

I only have Ubuntu on this laptop, no other OS. And by the way, it doesn't have a Wifi on/off switch.

---

### Post by ElPeski on 2011-01-31
I installed WICD and now I can connect to my ethernet.

NetworkManager keeps telling that networks are disabled. I uninstalled it.

But now I can't connect to my Wifi network. I use a WEP 128bit 13 character passphrase. It accepts the pass, but the connection always fails during the IP assignation (if i'm using DHCP) or during the AP association verification (if i'm using static IPs).

If I set my router to not use encryptation, it connects without problems.

After some experiments:

I changed the passphrase to "abcdefghijklm", and it connected once! Then I disconnected, tried again and it wouldn't connect.

However I'm connecting with my Windows PC and any password works fine!

---

### Post by AlexQM on 2011-01-31
Try setting your passphrase to something simple like 'password' to ensure there's no typos.
Are other devices able to connect to your AP when you have DHCP enabled on it?

---

### Post by ElPeski on 2011-02-01
128 bit WEP passwords have to be 13 characters long, so "password" won't work, but somwthing like "passwordpassw".
I've also tried 64bit and 256bit WEP keys, but they don't work either.

I tried first with WICD and it didn't work. Then I tried from a live session on ubuntu 10.10 and it connected using NetworkManager.

Then I changed the router security settings to a preshared WPA key and used "password". My Windows PC connected without problems, but WICD didn't work with any options (WPA preshared or WEP) and I can't find any options to use WPA keys with NetworkManager.

---

### Post by ElPeski on 2011-02-07
No luck.

I've tried every option, but WICD won't connect unless there's no password.

Network Manager is totally broken, but I can't understand why. Everything looks fine!

And I really don't want to install 10.10. Having to reconfigure everything is a pain. Besides, I don't know how to use WPA keys with Network Manager.

---

