---
title: "Linksys WPC600N Card- EAccessViolation"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Link64x on 2009-01-01
I'm fairly new to Linux, just to let you all know.  I know basics and that's about it.

Anyway, for Christmas a friend of mine got me a Linksys WPC600N Duel Band Wireless-N Notebook Adapter card.  My CD drive is broken (it's an old laptop, Inspiron 4100 with the most recent xubuntu on it), so I downloaded the driver off of the Linksys website.  I go through the installation.  Starts with a "Get started!" button, followed by the license agreement, then installation, then plugging in the card, then the "Finish" screen.

I plug in the card at the appropriate time, however when I do so and click "Next", the installation crashes and a screen pops up with the title "WLAN_cfg" and the error message reading "EAccessViolation" with the typical red X icon to the left of it.  I thought maybe that it was because i didn't have NDiswrapper or whatever it's called installed.  I downloaded it, became completely confused, and started searching online.  I was recommended to try DriverLoader.  I did so, and, though with a lot of trouble, was able to install it.  I went to re-install the card's driver.  This time it begins by uninstalling the original installation, and ended with the same error message.  I once again searched the error message in google, but to no avail.

So I figured i'd just post... any suggestions?


[EDIT]: Also forgot to mention that the card isn't even lighting up... I'm thinking that it's probably some sort of hardware issue, but it would have to be a problem with the card, because my current D-Link Ethernet Connection express-card is working just fine when i plug it in. So... yeah.. idk if it makes a difference, i thought it would light up once everything was properly installed, but idk for sure.  My D-Link one lights up only when connected to the internet, so I also figured that the wireless one would light up once connected as well.

~Nick~

---

### Post by Link64x on 2009-01-01
Nevermind, called up a friend who's fantastic with Ubuntu, and he ran me through what to do.  Used ndisgtk... i'll post steps below for anyone having a similar issue, even though it's probably already posted somewhere else:

1.) Open Terminal
2.) Enable the root account (may not be necessary for everyone, but was required for me.  Apparently my computer's retarded or something).  Do so by typing:
```
nick@billy:~$ su root
```
You'll be asked for the root password.  If it's denied, put sudo in front of the command.  It should work then.
3.) Enter the command line:
```
root@billy:~$ sudo apt-get install ndisgtk
```
4.) Run ndisgtk either by going into "Applications > System > Windows Wireless Drivers" or by typing the following into Terminal:
```
nick@billy:~$ sudo ndisgtk
```
(Note: If you still have the root account enabled, you will not need to use the sudo command).
5.) Click "+ Install New Driver"
6.) Locate the driver you have downloaded (if you haven't downloaded your driver yet, go to the company website of the card you're using, find the correct driver, and download the Windows XP version; save it to your desktop, and unzip it).  Make sure that the file you select is a .inf file.  Do not use the autorun.inf file that comes with most driver packages.
7.) It should install fairly quickly.  Restart your computer, plug in your card, and configure it by right clicking the icon in the top right corner of your screen.  The wireless connection you are trying to access should appear.  Click on it. For some this is the last step.
8.) For others, you will be prompted to give a WEP Key (Verizon FIOs users, this is you.  You can find this WEP Key on the side of your wireless router).
9.) Congrats, you should be connected.

Hope it helps those who have problems like I did.

~Nick~

---

### Post by nimrodwebdesign on 2009-11-10
Thanks Nick, this worked great on 9.10. Better than using the proprietary Broadcom STA driver I had before. I now get a 130Mb/s connection rather than just 54Mb/s, and it uses the traffic light, not just the power one.

The only problem with it is that I can't get it to connect using WPA or WPA2, only WEP. But it's better than the open network I had before, and I don't really need either out in the woods were I live.

Thanks again,
Nimrod

---

### Post by Theplumber657 on 2010-03-25
Hey, Just wanted to add that the above is correct. Though I had already installed all the required stuff. It only works in WEP key mode. Is there any other way to get it going encrypted as WPA PERSONAL, or WEP ENTERPRISE? Thanks

---

