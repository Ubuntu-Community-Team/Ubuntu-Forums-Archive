---
title: "WiFi disconnects when laptop is closed"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by tlehmann on 2011-01-06
I've tried searching Google with no relevant results, so here's my problem:
I have a Dell Studio 1737 running Ubuntu 10.04 LTS.  My WiFi was working fine a few days ago until I tried to boot into another mode that allows me to boot into my other Ubuntu 10.04 or Windows Vista.  I booted into that Ubuntu, which I thought had been overwritten when I was having problems and installed the one I am currently using.  I shut down since it didn't have anything of any use to me at the moment, and I booted back into this current Ubuntu.  Now, whenever I shut my laptop screen and open it back up to login, the WiFi is disconnected.  How can I solve this?  (I was also having this problem on the Ubuntu that I booted into earlier, but that WiFi did this from the start on that one.)

---

### Post by PatchesTheCaveman on 2011-01-07
Is your computer configured to go to sleep when you close to lid?  To check, go to System > Preferences > Power Management.  Check the setting next to *When laptop lid is closed:*.  It's probably set to *Suspend*, which turns off most of your computer's parts except the memory (RAM) to save power, including the wireless card.  If you change it to *Blank screen*, it won't do that.

Note that there are separate settings for when it's plugged into the wall and when it's on battery that you can select from the top.  You'll need to change it for both.

---

### Post by tlehmann on 2011-01-07
Except I want it to suspend, I just want Wi-Fi to come back when it's opened, too.  I've had Wi-Fi working normally with 10.04 in suspend mode before, but now it doesn't.

---

### Post by PatchesTheCaveman on 2011-01-07
Do you have the *Connect automatically* box checked in your wireless connection settings?

---

### Post by tlehmann on 2011-01-08
Thank you!  All is good now!  :)

---

