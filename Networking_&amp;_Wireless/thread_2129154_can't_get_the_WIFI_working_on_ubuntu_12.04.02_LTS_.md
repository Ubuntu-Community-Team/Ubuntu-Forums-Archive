---
title: "can't get the WIFI working on ubuntu 12.04.02 LTS / notebook presario v5207NR"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by lisi4ko on 2013-03-25
Hi,
First of all, I'm new to Ubuntu so pls don't give me a hard time :)

I just got rid off windows(es) and installed ubuntu 12.04.02 LTS. However the problem is that I cannot get my wifi working. I activated Broadcom STA drivers ... nothing happened. I installed b43 drivers via sudo apt-get install b43-fwcutter command. Again .. nothing happened.

Software and hardware are not forbidden.

Any idea how can i gen the WIFI on/off button flashing blue again ? :)

thanks

---

### Post by chili555 on 2013-03-25
Please see my signature below. The fact that a user is new is no excuse whatever to treat them with other than the utmost respect and kindness. I shall do my very best to do so.

Let's start by identifying your wireless device and determining which of several drivers is best for your device. Please open a terminal Ctrl+Alt+t and run and post these two separate terminal commands:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by lisi4ko on 2013-03-25
Hi,
thnx for help. Here we go:


lspci -nn | grep 028006:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

and


rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

just FYI when i hit the WIFI button it doesn't flashes, nor the wifi turns on or off but the "hard blocked" status changes to YES and NO everythime i make a hit.

---

### Post by chili555 on 2013-03-25
> but the "hard blocked" status changes to YES and NO everythime i make a hit. Perfect!

Please get a temporary wired ethernet connection and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```After a reboot, your wireless should be working.

---

### Post by lisi4ko on 2013-03-25
I don't know what all those lines mean bur this worked perfect mate. Wifi button turns on and off. Thanks :)

However, another problem came out from here and namely - when WIFI button is ON (flashing blue), then motior goes black and vice versa. 
Explaining: when i push the wifi button ON, then at the very same momment the screen turns black. I think only the backlight turns off as i'm seeing (hardly, but still seeing) some shadows of icons and the desktop at an apropriate angle. I can also see and move the pointer and the PC if fully operational...however cannot see a darn thing :)
Thereafter when i hit the WIFI button and switch it OFF, then the backlight of the monitor turns on again and everything is OK, exept the WIFI is OFF :)

My attempts to increase to increase brightness by FN keys were to no avail.
I can execute commands in the terminal (while display is black) and paste results, if needed.

Is this some kind of hardware issue ... or BIOS? ... should i move the thread in the hardware section?

P.S.
To be honest i had the same issue with the windows(es) (XP and 7) and when i moved to UBUNTU everything was fine ... until the WIFI started working ;)

---

### Post by chili555 on 2013-03-25
> should i move the thread in the hardware section?Yes, please. Our credentials do not allow access to the mysterious world of display drivers. We here in wireless have our own problems, neuroses and "issues."

---

### Post by lisi4ko on 2013-03-26
Note. Will open another thread in the hardware section ...

thanks for helping me solve my WIFI problem, mate!
Have a nice day.


P.S.
One last question .... how can i mark this thread "SOLVED"? :)

---

### Post by chili555 on 2013-03-26
> **lisi4ko said:**
> One last question .... how can i mark this thread "SOLVED"? :)You edit the title of the thread and change it from: [Ubuntu]can't get the WIFI working on ubuntu 12.04.02 LTS / notebook presario v5207NR to: **[SOLVED]**[Ubuntu]can't get the WIFI working on ubuntu 12.04.02 LTS / notebook presario v5207NR

---

