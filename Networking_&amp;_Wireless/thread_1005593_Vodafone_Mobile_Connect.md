---
title: "Vodafone Mobile Connect"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by Roger Allott on 2008-12-08
Could someone run me through what's necessary in order to get a Vodafone dongle (Huawei E220) to connect in Ubuntu 8.10?

I've been onto the Betavine site and downloaded their .run file that is meant to install the Linux version of their connection software, but suffice to say that it's installation on my machine cocked up.

I've tried looking at bypassing VMC by going to the connection icon and trying to set up a new Mobile Broadband connection, but it wants me to tell it a password. It seems that Vodafone in the US (i.e. Verizon) have a blanket password that is something like 'vzn', but does anyone here know what the password is in the UK? Also, is a username needed like is needed for Verizon?

---

### Post by Roger Allott on 2008-12-09
When does forum etiquette suggest is a good time to bump one's own thread?

---

### Post by razy60 on 2008-12-10
Network manager in 8.10 should work,

I must admit i did cheat slightly i set up the password using xp which meant i had all the info i needed to set up network manager.

To get nm to connect i had to go to: System-network connections-mobile set up, enter details and it worked.

Raz

---

### Post by Roger Allott on 2008-12-10
Thanks for responding, but what are the details I need to set up through Network Manager, and how do I get these details?

Vodafone 'customer care' say they don't support Linux so refuse to help me. Betavine are a bit better but they are only interested in getting me connected via their VMC for Linux beta product.

---

### Post by razy60 on 2008-12-10
If you right click on nm-edit connection-click mobile networks-add, just fill in the info asked for, then restart. 
Have you registered the device with vodafone, if you cant do it at home get them to do it in the shop.

Raz

---

### Post by scottuss on 2008-12-10
Yep, when I set up a friend's modem (I work part time for Voda so get roped into doing all sorts! lol) it just worked on 8.10

Anyway plug it in and network manager should pick it up automatically. There is a wizard that sets everything up. You shouldn't need the Betavine stuff in 8.10 (To be honest the Betavine drivers are ok, but still a bit buggy I found)

---

### Post by NotTheVistaVirus on 2008-12-12
I've just unpacked my vodafone mobile connect usb stick model K3520 and plugged it in. I'm using ubuntu 8.10 since Vista Home Basic which came preinstalled on my new laptop locked up totally within 10 minutes of opening the box...

However, network manager doesn't seem to recognise it - I get 'o2' listed in the Mobile Broadband section when I left click the Network Manager icon in the top right corner of my desktop. But I don't have an o2 connection! And if I click it, it says 'A password is required to connect to o2' which I do not have.

Any help gratefully received and much appreciated.

---

### Post by NotTheVistaVirus on 2008-12-12
Sorted - I created a new connection to Vodafone as detailed above using System > Preferences > Network Configuration > Mobile Broadband > Add then restarted my laptop.

I then spent a couple of hours trying to get the password accepted - I found various posts saying that the password is 'web' but typing it didn't make anything happen, it just closed the password dialog.

Eventually I just tried pressing enter with a blank password and that was it! Just like that.

Hope this helps someone else. By the way, the USB modem is an E620 even though its part number K3520 appears to be the same for lots of different internal chip sets inside. I guess it just depends on which one you are given.

---

### Post by razy60 on 2008-12-12
> Eventually I just tried pressing enter with a blank password and that was it! Just like that.


Bizarrely enough that works with most progs/apps unless you have preset a password that is.

Raz

---

### Post by ubseamus on 2010-03-08
Hi guys, trying to setup Vodafone E620 & seem to be stuck at this exact point, any ideas?
 
see my post @
 
[http://ubuntuforums.org/showthread.php?t=1240240](http://ubuntuforums.org/showthread.php?t=1240240)

---

