---
title: "Total noob question re terminal window"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by TrafficPilot on 2011-06-29
Hi all

Sorry about this but I'm trying to find out why ubuntu wi-fi isn't working now on my laptop (it was last night).

I am following a tutorial that says to start..

[I]Open a terminal window (such as gnome-terminal), and enter the following command:

nm-tool[/I]

Umm..how do I open a teminal window? I know how to run a DOS prompt in Windows but no idea how to find "gnome-terminal" or run a command in ubuntu.

Help!

Thanks

Adam

---

### Post by zokratez on 2011-06-29
You need to run the console emulator, search it on menu or application launcher ;)

---

### Post by haqking on 2011-06-29
> **TrafficPilot said:**
> Hi all

Sorry about this but I'm trying to find out why ubuntu wi-fi isn't working now on my laptop (it was last night).

I am following a tutorial that says to start..

[I]Open a terminal window (such as gnome-terminal), and enter the following command:

nm-tool[/I]

Umm..how do I open a teminal window? I know how to run a DOS prompt in Windows but no idea how to find "gnome-terminal" or run a command in ubuntu.

Help!

Thanks

Adam

ctrl + alt + t

or it is under applications menu under accessories

---

### Post by TrafficPilot on 2011-06-29
Thank you both!

---

### Post by georgelab on 2011-06-29
That's why I think gnome-terminal icon must be fixed at desktop toolbar by default!

---

### Post by chili555 on 2011-06-29
> **georgelab said:**
> That's why I think gnome-terminal icon must be fixed at desktop toolbar by default!I agree. You can right-click the panel and add a launcher. Select Terminal and it will be at your elbow forever. If you are running 11.04 and Unity, it's only a bit more complicated. Open Applications and type in terminal. When it opens, right-click the icon at the left and select Keep in Launcher.

---

### Post by TrafficPilot on 2011-06-29
Thanks for the info..I've got the terminal up it confirms my wifi is disconnected.

ubuntu can "see" my wireless card in the laptop.

Not sure what to do next. In the Wireless taskbar window both "Wired Network disconnected" and "Wireless Networks disconnected" are greyed out.

Windows 7 wi-fi on same laptop works fine have just checked (it's dual boot).

Any ideas for next stage to check?

---

### Post by chili555 on 2011-06-29
> ubuntu can "see" my wireless card in the laptop.If it is a built in wireless card, i.e. PCI, please open the terminal and run and post:```
lspci -nn
```If it's easier, strip away all the lines that are not your wireless device. If it's a USB device, do:```
lsusb
```Once we have the data, we'll identify the driver needed and the best way to install it.

Off to Big City and lunch with Mrs. Chili; I be back in a couple of hours.

---

### Post by TrafficPilot on 2011-06-29
ok here's what it says in the terminal window on my netbook...

05:00.0 Network Controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727]  (rev 01)

hope I've written out the correct line!

thanks

Adam

---

### Post by chili555 on 2011-06-29
> hope I've written out the correct line!Exactly correct! This device works with the Broadcom STA driver. There are two ways to install it, but since we've discovered the terminal, let's go old school. Walk that laptop over to the router and get a wired ethernet connection. In the terminal do:```
sudo apt-get install bcmwl-kernel-source dkms
```When you type your password, for security purposes, it is not echoed back, not even ****. Just type it in and press Enter.

The program apt-get will go out to Ubuntu repositories on the internet and get the packages appropriate to your Ubuntu version and install them. It will only take a few moments. After it's done, detach the ethernet cable and do:```
sudo modprobe wl
```Then click the Network Manager icon, see your network and connect.

If everything goes as smoothly as I expect, post back with your wireless connection to tell us how well it's working.

Sadly, the terminal is almost never needed in the most recent versions of Ubuntu. This may be the last time you get to wear your geek glasses!

---

