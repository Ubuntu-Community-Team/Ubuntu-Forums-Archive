---
title: "Install 3G modem"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by cazz on 2009-07-22
Hello everybody :)


After I have install Xubuntu 9.04 I install the Nvidia, The wireless card and everything else and it work right out if the box.

But when I trying to install and connect to my ISP (Telia) I have big BIG problem

First time I plugin the USB from my dongle (Huawei E220) the xubuntu find it and want to add it to the "Network connections" I did pick "Telia" from the list and then trying to connect but it just say "GSM Network Disconnected - you are now offline"
Nothing more happend.
Then I trying to add a username and a password (I dont need or have any but I did try it anyway) and now it just ask for a password that I dont have and that dont exist.

Then I trying "Vodafone Mobile Connect Card driver for Linux"
I did take sometime to install it (I did use the "vodafone-mobile-connect-card-driver-for-linux-2.0.beta3-ALL-i386-installer.run" and it did install everything.
But I can't start it, so I did trying to start it in terminal and find that was something wrong with the python-twisted.
I did search a little and find that I have to remove python-twisted from my system. I did do that and I can start but then I got a problem "Device setup not completed" and he say my device Huawei E870 is not properly registered with the kernel. But I have a E220?? 
So I have to close the program and nothing more I can do.

Then I find this
[http://ubuntuforums.org/showpost.php?p=5636892&postcount=5](http://ubuntuforums.org/showpost.php?p=5636892&postcount=5)
I did everthing it say but it just trying to send the password and nothing more.

Then I trying to through terminal connect with wvdial. I did change the config file and then trying to connect but it just trying and trying and trying.

I have no idea what to do.

If I can't get 3G modem to work with xubuntu I can't use it and have to go back to windows XP

---

### Post by solitaire on 2009-07-22
I might be wrong in this but what is the "APN" for your telco?

It might be something like "telia.internet.net" or something like that!
It's basically telling the 3G modem what provider to connect to. If it's not correct you will not get a data connection.

Check with your mobile operator for the APN information (It might be in the help pages on their website). You might have to add it manually to the network setting for the 3G usb dongle.

---

### Post by cazz on 2009-07-23
> **solitaire said:**
> I might be wrong in this but what is the "APN" for your telco?

It might be something like "telia.internet.net" or something like that!
It's basically telling the 3G modem what provider to connect to. If it's not correct you will not get a data connection.

Check with your mobile operator for the APN information (It might be in the help pages on their website). You might have to add it manually to the network setting for the 3G usb dongle.

it is "online.telia.se" and I have it right there.

But thanks anyway for you replay

---

### Post by NoReflex on 2009-07-23
Hello!

To easily connect to the Internet using Huawei's E220 you can use Network-Manager or Gnome-PPP.
Network-Manger always worked for me but if it doesn't work for you try Gnome-PPP as it will offer more control options.
After installing Gnome-PPP try to add a new connection using your modem (it's quite easy).
If your modem isn't detected properly you can try try to see what went wrong with **tail /var/log/messages**.
Good luck!

Best wishes,
NoReflex

---

### Post by jamb on 2009-07-26
Hi,
I'm running xubuntu (9.04) and with an E220 modem, with 3 as my ISP.
This setup works for me.
[http://ubuntuforums.org/showthread.php?p=7683661#post7683661]("http://ubuntuforums.org/showthread.php?p=7683661#post7683661")

---

