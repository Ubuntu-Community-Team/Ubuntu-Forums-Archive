---
title: "Broadcom 4322AG STA Drivers installed, but no connection."
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by Tucker2.0 on 2010-07-21
All right, at the risk of being called a n00b, I'm going to post this thread asking for help.

I'm not new to linux per say, but I'm by no means great at it.

OK, I have an HP Pavilion Dv6-1230US laptop that I bought from staples when it was on sale for 800 dollars with a 4 year accidental damage warranty.  It came with Vista Home Premium 64Bit installed.  It had Windows 7 Business 64Bit on it at one point, And the latest windows installation was Windows Vista Business 32Bit.  My trial period ran out on vista and I switched to Ubuntu 10.04 32Bit, and, as always, I have a problem with the wireless card.  I have looked it up and everything, i do have the drivers installed, and it looks functional, but its not.  

It will act like its going to connect to my AP (Netgear WNR3500L that is like 2 days old), but it eventually askes me for my WPA2-Personal AES key, which I have supplied, and is correct before hand, i type the exact same thing in and it still doesn't work.

I've tried sudo apt-get update, and sudo apt-get upgrade, but it doesn't work.  nothing has to update.  This installation was installed today, and updated about 6 hours ago to the fullest extent.

The wired works absolutely perfect (that's how i updated it).

Hardware:

Laptop has a Broadcom 4322AG b/g/draft-n wireless card from HP integrated into the laptop.
The router is a Netgear WNR3500L which i bought because we are switching ISP's soon and our old router is a modem, that will only work on a DSL connection.  

If you have any ideas, please let me know, and if you need any more hardware info, let me know and I'll get it, I want this to work, I'm sick of vista killing a 12 Cell battery in 3 hours.

---

### Post by corrytonapple on 2010-07-21
This happens to me when the computer can hardly connect to the internet because I am out of range. Try moving closer to your router.

---

### Post by Tucker2.0 on 2010-07-22
thats seems like its the problem, but it does it when I'm sitting right under the router. 

I'm in the same room with it right now and its 3 feet above me and its doing it still doing it :|

---

### Post by Tucker2.0 on 2010-07-22
See i am a noob, thanks for your help man, guess what it was though...

my version of this laptop has 3 touch buttons at the top of the keyboard, 2 for sound and one for wifi, well since it was linux and it didn't have drivers installed (or atleast i though) i never messed with them, so right after i read your post i started looking on google my self again, and it brought me back to a post on this forum, the first thing it said was to, reboot after the first reboot of the installation and cycle the wifi switch.

and that worked, now im getting a list of connections around me and its working, im typing this on it now, thanks guys.

---

