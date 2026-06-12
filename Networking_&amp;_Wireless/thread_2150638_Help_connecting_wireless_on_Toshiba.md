---
title: "Help connecting wireless on Toshiba"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by Peredur111 on 2013-06-01
Hello!

I have a Toshiba Satellite C855-S5115 and have loaded Ubuntu 12.04. So far all is well but I cannot for the life of me figure out how to set up a wireless connection. Can anyone help me do this through the Terminal?* (Note: I am a total Linux noobie and don't understand most of this but I am trying to learn as much as I can.)*

I appreciate any and all help that can be offered!

Cheers! :D

---

### Post by wildmanne39 on 2013-06-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Peredur111 on 2013-06-01
Here ya go!

---

### Post by wildmanne39 on 2013-06-01
Hi, do everything in post 6 of this link and report back.
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)

Also change your wireless settings in network manager to match the screenshots.

Disconnect your wired connection and reboot, if it does not connect please run the script again and post the results so we can see if the changes took effect.
Thanks

---

### Post by Peredur111 on 2013-06-01
> **Wild Man said:**
> Hi, do everything in post 6 of this link and report back.
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)

Created the gedit file....

> **Wild Man said:**
> Also change your wireless settings in network manager to match the screenshots.

Problem here. Tried to change to these settings but could not Save for some reason. Any ideas?

---

### Post by wildmanne39 on 2013-06-01
When you entered the dns server it would not let you save it or you could not enter the information?
Thanks

---

### Post by Peredur111 on 2013-06-01
Clicked Edit Connections - Wireless tab - Add - went to IPv4 and IPv6 tabs and entered information as per screenshots. The Save button remained greyed out and could not be clicked. Am I supposed to put anything under the other tabs?
Thanx

---

### Post by wildmanne39 on 2013-06-01
> Am I supposed to put anything under the other tabs
No.

If you can not save the settings you can reboot and see if that allows you too, if not you have other issues with your system and you should start a new thread on why you can not save settings.

The file you created did it help?
Did you do this?  > Also go into your router settings and change 802.11bgn to 802.11bg.
Thanks

---

### Post by Peredur111 on 2013-06-01
As far as I can tell, the file didn't change anything.

> Did you do this?   	 		 			 			 				Also go into your router settings and change 802.11bgn to 802.11bg. 			 		

I don't have a router. I'm trying to set up wifi so I can use the computer on the road at wifi hotspots.

---

### Post by wildmanne39 on 2013-06-01
Are you at a hotspot now?

My friend Hadaka pm'd me he noticed that > Clicked Edit Connections - Wireless tab - Add - went to IPv4 and IPv6 tabs and entered information as per screenshots. The Save button remained greyed out and could not be clicked.

You should have assuming you have a connection setup which you probably do not since you do not have a router > Clicked Edit Connections - Wireless tab - then double click on the network connection you want to connect too then go - to IPv4 and IPv6 tabs and entered information as per screenshots. The Save button remained greyed out and could not be clicked.

It is possible if network manager does not have a network to find it will not let you save those settings but I am not sure of that.
Thanks

---

### Post by Peredur111 on 2013-06-01
I believe one of my neighbors has wireless, not sure if I'd be able to pick it up. Unfortunately, I can't talk to you and be at a hotspot. As it stands, when I check on my network connections, no wireless option is listed at all. In looking at other threads (for example: [http://ubuntuforums.org/showthread.php?t=2123074](http://ubuntuforums.org/showthread.php?t=2123074)), it seems this is an issue with the Toshiba but there are ways around it. I tried doing some of the stuff in the attached thread but some of my results were a little different and, being new to this and not overly savvy with Ubuntu (or computers in general, for that matter), I decided not to take the chance of screwing everything up.

---

### Post by wildmanne39 on 2013-06-01
When you get to a hotspot hopefully it will connect, there is not much else we can do for now.

That is a good link you posted and chili555 is the best at wireless issues.

The first thing you did in the link I gave you hopefully will make it work but that driver is problematic.
Thanks

---

