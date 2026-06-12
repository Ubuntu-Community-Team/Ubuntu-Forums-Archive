---
title: "iPhone 2.2.1 Sync with ubuntu"
date: 2009-02-14
forum: Multimedia Software
---

### Post by SoniXuS on 2009-02-14
I want to sync my iphone with ubuntu using the next hack.

> For 2.2 firmware on making the above change to /System/Library/Lockdown/Checkpoint.xml I needed to reboot my Ipod Touch before tracks could be seen. Reboot by holding the power button down for approx 10 seconds. To restart your touch press the power button down again. After this the "Music" app on the touch worked fine and tracks sync'd via gtkpod were visible. PwnPlayer was not required (in fact it just crashed on startup every time, Google search shows this is a common problem) (16-Jan-2009) 

The big problem is, I followed the steps to get ssh and mounted the thing. It shows up as iPod with the correct icon on my ubuntu 8.10 desktop but rythmbox nor gtkpod recognize it.

Anyone in for some help?

If this actually works we could try to include a script in the ipod-convenience package that asks which version you uses and patches the Checkpoint.xml file if wanted.

---

### Post by SoniXuS on 2009-02-15
This is a tutorial to sync your iphone 2.2.1

CAUTION: YOUR iPhone should be jailbroken!

On your iPhone:

# Click Settings &#8594; General and set Auto-lock to Never. This will ensure the iPhone keeps the WiFi connection open.
# Click Settings &#8594; WiFi and select your WiFi network. Click the Static button and change the IP Address to an address that's outside the dynamically assigned range of your network. This will ensure your iPhone is always contactable at the same address for syncing.
# Open Installer.
# Click All Packages &#8594; BSD Subsystem &#8594; Install
# Click on All Packages &#8594; OpenSSH &#8594; Install.
# Reboot
# Check your iphone's IP-address, write it down.

On ubuntu:

# Open gftp and enter the iPhone's ip address. The root username and the password "alpine". Use the ssh2 connection.
# Browse to /System/Library/Lockdown/
# Download Checkpoint.xml
# Edit it on your local pc. Search the section DBVersion. Change the number from 4 to 2.
# Upload Checkpoint.xml
# sudo apt-get install --no-install-recommends ipod-convenience
# Enter your IP-address, enter the mount point.
# Mount with iphone-mount, unmount with iphone umount
# Install your favorite linux app to sync. GtkPod syncs music and pictures!

NOTE: I CAN'T GET MY IPHONE VISIBLE IN RHYTHMBOX, IF SOMEONE KNOWS WHY, PLEASE ANSWER.

---

### Post by SoniXuS on 2009-02-16
Noone knows how to make it visible in Rhythmbox?

---

### Post by Treinspore on 2009-03-12
does syncing the device on ubuntu delete apps and videos synced with another computer or downloaded from the device itself?

---

### Post by darkvad0r on 2009-03-13
> **Treinspore said:**
> does syncing the device on ubuntu delete apps and videos synced with another computer or downloaded from the device itself?
No it doesn't

> Noone knows how to make it visible in Rhythmbox?

I've tried to find about it but since sync works with gtkpod and amarok I just used gtkpod. I guess it'd be worth trying to get in touch with the developers (perhaps filling a bug report)

---

### Post by adriannome on 2009-05-27
know this is an old thread, but i just gotta say how happy i an right now. no more need for windows:D tanks guys.

---

