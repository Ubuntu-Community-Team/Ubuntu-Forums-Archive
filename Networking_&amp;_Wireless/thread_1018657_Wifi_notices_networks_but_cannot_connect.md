---
title: "Wifi notices networks but cannot connect"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by corn29 on 2008-12-22
Hello,

I've installed the driver for my wireless card with ndiswrapper.  When I enter ndiswrapper -l I get this response:

dogzilla@dogzilla-laptop:~$ ndiswrapper -l
rt2860 : driver installed
	device (1814:0681) present
dogzilla@dogzilla-laptop:~$ 

According to that response, I'm assuming the driver is installed correctly.

Also, after installing the driver, I loaded it into memory:

  sudo depmod -a
  sudo modprobe ndiswrapper

I didn't see any error messages:

  tail /var/log/messages

And I wan to load it at startup:

  sudo ndiswrapper -m

Given all that, whenever I start the computer, the network icon towards the upper right-hand portion of the screen says something like wireless networks detected.

I hide my SSID at home.  So when I try to connect, I click on the network icon towards the upper right-hand portion of the screen and select connect to a hidden network.

From the resulting screen, I enter the SSID, and my WPA key.  When that is applied, I see the network icon turn to two dots and a little blue comet circling around the two dots.  The dot towards the lower left turns green right away.  The other dot, towards the upper right, always stays grey.

The little blue swirl goes round and round in a circle but never seems to connect.  Every now and again, I get challenged with a prompt to "Enter password for the default keyring to unlock"... I've tried my account password and my WPA passkey here.  It always fails as I keep repeatedly getting the prompt.

How can I connect to my wireless network?  What steps am I missing which are preventing me from completing this task?

Thanks!

---

### Post by corn29 on 2009-01-02
Nevermind my last post about WiFi... I went back to Mandriva (v 2009.0). My install and using the wireless connection took about 20 minutes.

With Ubuntu, it seems like you're screwed if what you're trying to do doesn't explicitly fit their esoteric ways of operating... battling sudo and the package manager if one needs software which has to be built from source for example.

---

### Post by Favux on 2009-01-03
Hi corn29,

For a work-a-round to your wireless problem in Intrepid see:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

---

