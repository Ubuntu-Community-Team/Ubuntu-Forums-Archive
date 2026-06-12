---
title: "Jaunty (9.04) with WUSB11v4 problems"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by Quintinon on 2009-04-26
I recently decided to move from a windows only environment, to a windows and ubuntu dual boot. Everything is going great except for one problem. I cannot for the life of me get my WUSB11v4 usb wireless connection to SHOW up at all.

I've done this so far.

Installed amd64 ubuntu 9.04
Installed ndiswrapper, jaunty recommended version (I have to boot to xp, download, boot into ubuntu, and run the package to install).
Used ndiswrapper to install the recommended WUSB11v4 drivers.
"ndiswrapper - l" shows the driver (the only one i have installed with it) and  the hardware present message.

lsusb show that i do infact have it connected.

Though the trouble I get is that the Network Manager does not give wireless option(s) still, so I check iwconfig, all I get is "lo", "eth0", and "pan0", I do NOT get "wlan0". I don't know exactly what pan0 is but I assume its not my USB device because if i unplug it, its still there (I have a usb mouse,keyboard,gaming pad, and 2 flash drives all hooked up too).

Also, in the ndiswrapper gui (ndisgtk) when I start it with the WUSB11v4 plugged in, I get the message
"Unable to see if hardware is present".

If I click setup network connecitons, I used to get "Could not find a network configuration tool", which I read up and found out that I should install gnome-network-admin, which I did. But everything in the new window that pops up is grayed out, (only shows the 3 connections show in iwconfig, none of which are any real hardware connections).

This is where I am, I have tried just about everything I can find, and none of it seems to help.

Any ideas are welcome.

Also, I don't have a Live CD, I have a "Live USB" if that makes any difference in how I would do things if that comes up.

And yes, I am an ubuntu newbie, but a faily knowledgable computer person.

---

### Post by Quintinon on 2009-04-27
Initial problem above solved by changing from amd64 ubuntu to 32-bit ubuntu (i863 or whatever the intel one is).

Another problem has popped up with it not being able to USE the connection it gets.

I use WEP for my router, and wicd gets stuck in "obtaining ip" with normal settings, and with static ip it connects, but I cannot access the router page or the internet.

about 5% of the times i've tried i can get a manual connection setup with

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "ESSID"
sudo iwconfig wlan0 key 123456789A
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Though the other 95% of the time the last command just keeps sending packets to get an ip and fails.

---

