---
title: "Maverick x86_64 TP-LINK TL-WN321G"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by roobinatube on 2011-01-24
I solved this myself, but in case someone is searching for the same thing, this would save them them some effort. Also im confused at why!

I use a usb wireless card in my desktop, model in title, which uses the rt73usb module. Well how slow was that?! Actually, the downloads were fast, but browsing and loading pages was slow, firefox would just hang on "looking up......" for ages before finally loading the page.

So I thought, might as well give ndiswrapper a go. Wow! What a change! No difference on the fast downloads, and I get full speed browsing too!

Why would this be? I would understand it if my downloads were also slow...

Roob

PS I am using the x64 WinXP rt73.inf from TP-LINK's website.

---

### Post by Omegus on 2011-01-31
That is great that you enjoy the product but how did you get it working? I bought the same product but can do anything with it.

---

### Post by roobinatube on 2011-01-31
Hi, I hope I can be helpful here!

First of all, on the back of the USB wireless card, there is a model number labelled as FCC ID: (mine is TE7WN321GV2) the bit you want to notice are the last 2 letters, in my case V2. Now you know this, go to [TP-Link download section here]("http://www.tp-link.com/en/support/version.aspx?mid=01030301&pid=671") and get the appropriate version of the driver.

Now to install ndiswrapper.

```
sudo apt-get install ndisgtk
```Now before we start trying ndiswrapper, remove any conflicting drivers. For me there were two, generally modules named "rtxxx" are ralink. So to have a look and see what shouldnt be loaded:
```
lsmod | grep rt 
```My result was rt2500usb and rt73usb. To remove these modules to stop them interfereing, and do this for all of them.

```
sudo rmmod rt73usb
```and to blacklist them to stop them loading again

```
sudo nano /etc/modprobe.d/blacklist.conf
```and add the following line(s)

blacklist rt73usb
blacklist rt2500usb
blacklist <name of module>

Now to load the ndiswrapper module

```
sudo modprobe ndiswrapper
```And to make sure it always starts

```
sudo nano /etc/modules
```and add the line:

ndiswrapper

Now start trying drivers! So I use Kubuntu, ndiswrapper is under "system" in the menu - I guess in gnome it would be in system>administration

Now remove any entries already shown, and add the driver that you downloaded. For me, the 64bit XP driver worked, it might be different for you. Each time a driver fails, remove it, and try again. This might crash your computer. If it does, restart and try a different one.

Remember you have to add the .inf file to ndiswrapper, NOT the .exe or the .sys

Good luck!

Roob

---

### Post by roobinatube on 2011-01-31
Also just remembered that to get the most out of it, I turned off power management for wireless.

```
iwconfig
```

to find the device name, mine is wlan0, could be eth1 etc.

```
sudo nano /etc/rc.local
```

and before the end, add this line:

iwconfig wlan0 power off


substituting wlan0 for whatever you found above.

---

### Post by NarfZilla on 2011-03-07
thank you so much for this walk through!

if weren't for you i wouldn't be to restore the connection on my girlfriends computer :)

five stars for you:
:KS:KS:KS:KS:KS


:lolflag:

---

