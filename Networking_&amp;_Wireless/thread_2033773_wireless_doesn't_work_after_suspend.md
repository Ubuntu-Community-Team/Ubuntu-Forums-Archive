---
title: "wireless doesn't work after suspend"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by bramble07 on 2012-07-26
I'm a total newbie to Linux.  I just installed Lubuntu 11.10 (as a dual boot with Windows XP) a couple days ago to give some new life to my old laptop.  Everything has been working wonderfully so far, with one exception.  The wireless works fine at first, but when the computer comes back from hibernate or suspend, the wireless no longer works.  The computer still detects all the wireless networks and says it is connected to my network, but Chromium says there's some kind of DNS error and I can't load any webpages.  The wireless works again if I just reboot the computer.  

However, I saw something on one of the other forums that suggested for a similar problem (though in Ubuntu) to reload the driver by doing this:

sudo rmmod ipw2200
sudo modprobe ipw2200

(I ran nm-tool to get the name of the driver I used in these commands.)   After doing this, any attempt to load webpages in Chromium just times out, even if I reboot.  It doesn't seem like it should have created that kind of problem, but I also don't know anything about Linux yet.  As a total newbie, any help would be immensely appreciated.  Thanks!

---

### Post by nicolasdiogo on 2012-08-15
if you turn the wireless off and on using the network-manager should suffice to fix this issue

---

### Post by bramble07 on 2012-08-15
Could you show me the command-line to do that?  I'm a total newbie and I don't know yet what to do to follow your directions.  Thanks!

> **nicolasdiogo said:**
> if you turn the wireless off and on using the network-manager should suffice to fix this issue

---

### Post by kurt18947 on 2012-08-15
This might be the same problem I was seeing with RealTek USB WiFi adapters in earlier Ubuntu releases.  My problem was that the network was not disconnected prior to suspending.  Then when it came out of suspend it tried to connect and couldn't because it was never disconnected and can't just resume where it left off.  In my case the device was a USB and unplugging/replugging got it to connect.  Perhaps unloading/reloading the module has the same effect.  It appears that network devices need to disconnect prior to suspending then reconnect after coming out of suspend.  Here is what worked for me in Ubuntu 11.xx courtesy of Chili555:

Open a terminal in an account with sudo privileges and type this:

[B]sudo gedit /etc/pm/config.d/config
[/B]
Gedit will open with a blank page.  On the blank page type this:

**SUSPEND_MODULES=ipw2200** (or whatever the module name is that drives your wifi adapter.)  Save the file and restart.  Then suspend, wait a minute, resume and see if your WiFI comes alive

---

### Post by rfruth123 on 2012-10-21
Adding the SUSPEND_MODULES worked for me too.  I am using a Netgear G54/N150 Wireless USB Micro Adapter on Linux Mint 13/MATE. The name of my module was rtl8192cu.  Thanks for the information.

---

### Post by offgridguy on 2012-10-21
> **nicolasdiogo said:**
> if you turn the wireless off and on using the network-manager should suffice to fix this issue
  
Where would I find network manager in ubuntu 12.04 ?

---

