---
title: "Problem with Router and Ubuntu 10.4"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by violeta_col on 2010-05-13
Hello there,

First of all, I am very new to this world, so any "technical" word i wont understand please explain as if you were explaining to a little girl.

second, my problem. I have two computers, one Dell inspiron with WindowsXP and the other one is MEDION MD 96400. The latter was very slow since it has only 1MB, so I decided to install Ubuntu.

the installation went smoothly. everything seems to work, aslo the wireless card was detected. till there everything fine.

I usually connect throguh a Netgear Router (WGR614v5) and it was working very well until I tried to navigate with my new install Ubuntu and it didnt work. It did recognized the networks around but it doesnt navigate. Now, the router seems to have now a misconfiguration.
This is the usual way I connect (no linux installed and trying to get connectivity):
Modem > Router > DELL no problem.. but now I get an strange IP address (before was the usual 198.162.1.1...now 201.33....) and I cannot access to the router with my usual password and my ubuntu doesnt navigate.. ..


UPDATE: Ok, I connected the modem directly to my MD MEDION 96400 Ubuntu 10.4 and the ethernet works very good. Now the problem seems to be the combination Router, Modem- wireless connection. As I said before, there is something preventing the router to get internet connection. I know could access to my router config and restore it to original setup, it worked for a while but then when I tried to save the settings its said that 192.168.1.2 (the ip of my ubuntu) was managing the device and then everything went crazy again.... then I shut down the MD computer and tried to work around with my Dell and configurate the router again but the modem doesnt seem to recognize it anymore... i dont knwo what do  to make my 2 pc work with the same router....
hope you help me..

---

### Post by mrtomservo on 2010-05-13
If you're getting an IP other than the 192.168.x.x then you're probably bypassing your router and connecting directly to your modem.  I'm not a network guru, but on my LAN if the router refuses to be friendly with my DSL modem, I turn em all off, then power them on (waiting a minute between) in this order - modem, router, computer.

Now when you say you can't access your router with your usual password... do you mean that your password suddenly doesn't work at the router login screen?  Or are you not seeing the login screen for your router at all?

And also, when you got your internet did you install any software on your Dell to create an account or login?  If you did, that's probably why your dell is able to get an IP address and Ubuntu is not.

---

### Post by violeta_col on 2010-05-13
Hi.. to answer your questions. Yes, my password do not work suddenly..
and I received the following login screen 192.168.1.1:80 or sometimes i just dont get any login screen at all...I will try what u recommend to see how it works.. I didnt install anything into my DELL and Ubuntu gets an IP address... but it does navigate...and the whole combination Dell pc-ubuntu-router-modem get crazy!

---

### Post by violeta_col on 2010-05-13
UPDATE: Ok, I connected the modem directly to my MD MEDION 96400 Ubuntu  10.4 and the ethernet works very good. Now the problem seems to be the  combination Router, Modem- wireless connection. As I said before, there  is something preventing the router to get internet connection. I know  could access to my router config and restore it to original setup, it  worked for a while but then when I tried to save the settings its said  that 192.168.1.2 (the ip of my ubuntu) was managing the device and then  everything went crazy again.... then I shut down the MD computer and  tried to work around with my Dell and configurate the router again but  the modem doesnt seem to recognize it anymore... i dont knwo what do  to  make my 2 pc work with the same router....
hope you help me..

---

