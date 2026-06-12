---
title: "Can't Connect After Using NDISWrapper"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by chessnerd on 2010-01-01
My wireless card (an Atheros AR928x) was not performing very well. At the suggestion of a friend I tried to use NDISWrapper (using the ndisgtk GUI interface) to see if a Windows driver would work better. I found the XP drivers online, tried several versions and, after none worked, I decided that I might as well settle with the crappy quality of the Linux driver and let it go. Sadly, that may not be possible. 

I removed the drivers (again via ndisgtk) and now the laptop can't use the card at all. It won't detect any networks (even when just five feet from the router) and I'm not sure what's causing this. I've tried rebooting and rebooting into an older kernel. I checked lspci and it still recognizes the card.

Any idea what's up and how I could fix it?

---

### Post by chessnerd on 2010-01-02
Well, I seem to have fixed the issue (sort of).

I got the same Windows XP drivers on another computer and brought them to this one via flash-drive. After trying NDISWrapper again it seems to have fixed my issue after a reboot. The driver doesn't seem to be much better than the one that I had (in fact, I have a hunch that it's the same one) but it works at least.

If someone can still come up with a reason for my issue I would appreciate it in case this set-up fails.

---

### Post by peepingtom on 2010-01-02
check /etc/modprobe.d/blacklist.conf

See if the native linux driver is blacklisted. If you want to use it again, remove it from that list and add ndiswrapper.

---

### Post by chessnerd on 2010-01-02
> **peepingtom said:**
> check /etc/modprobe.d/blacklist.conf

See if the native linux driver is blacklisted. If you want to use it again, remove it from that list and add ndiswrapper.

The native Linux driver wasn't blacklisted, but I blacklisted ndiswrapper and now it seems to be using the native Linux driver again. 

Sure, the driver through ndiswrapper was usable, and was a bit better when it came to having a weak signal, but it took much longer to connect to the network and wouldn't work after a suspend so I'm glad to be using the Linux driver again. It may not be perfect, but it's okay. 

Thanks for the help.

---

### Post by coffeecat on 2010-01-02
> **chessnerd said:**
> I'm glad to be using the Linux driver again. It may not be perfect, but it's okay. 

I fixed my Atheros AR928X flaky wireless in Karmic by the simple expedient of installing the two packages:

linux-backports-modules-karmic-generic.
linux-backports-modules-wireless-karmic-generic.

You probably only need one, but it doesn't hurt to mark both for installation. They bring in the backported drivers to match the running kernel. This has worked just fine for me with the 2.6.31-14, -15 and -16 kernels. If you search the forum you'll find other AR928X users have had success with the backports. You don't need to enable the backports repository. They're in main - I think.

---

### Post by chessnerd on 2010-01-03
> **coffeecat said:**
> I fixed my Atheros AR928X flaky wireless in Karmic by the simple expedient of installing the two packages:

linux-backports-modules-karmic-generic.
linux-backports-modules-wireless-karmic-generic.

You probably only need one, but it doesn't hurt to mark both for installation. They bring in the backported drivers to match the running kernel. This has worked just fine for me with the 2.6.31-14, -15 and -16 kernels. If you search the forum you'll find other AR928X users have had success with the backports. You don't need to enable the backports repository. They're in main - I think.

Thanks, CoffeeCat. I did have to uncomment the backports repository in the sources.list to get those packages to install, but it was a painless procedure nonetheless. 

After a reboot, my wireless is working great. It has held steady at 70-72% for over 45 minutes. Usually it was bouncing erratically between 30% and 70%. When working it was offering pathetic speeds for downloads, which failed half the time anyway. On a bad day it would also cut in and out every 15 minutes or turning a simple browsing session into a living nightmare unless I moved to another room closer to the router.

This will let me use Ubuntu a lot more often now that I have a reliable Internet connection. I hope these drivers are included by default in Lucid so that everyone can benefit from them.

My original post was about just getting back to square one. PeepingTom accomplished that. Now you've advanced me to my destination of stable wireless support. So I guess I'll marked this thread as solved.

Thanks again.

---

### Post by coffeecat on 2010-01-03
> **chessnerd said:**
> I hope these drivers are included by default in Lucid so that everyone can benefit from them.

I've got Lucid Alpha 1 one another partition on the laptop with the AR928X wireless, and wireless has been working fine. My guess is that the backported Karmic modules are from the version of the kernel that comes in Lucid so I wasn't surprised, but pleased nevertheless.

I'm glad the backported modules were helpful.

---

### Post by gwu777 on 2010-02-15
> **coffeecat said:**
> I fixed my Atheros AR928X flaky wireless in Karmic by the simple expedient of installing the two packages:

linux-backports-modules-karmic-generic.
linux-backports-modules-wireless-karmic-generic.


I didn't really understand what just happened, but it worked a charm. Although I would love to understand what those backport modules do, I am very thankful to have a steady wireless connection on my laptop...

Thank you

---

### Post by crazi2k on 2010-02-23
Were you able to get the N-channel router running @ 40 Mhz wide band to work with the ARB591 client/laptop?

For some reason it won't connect to N-channel (works on wireless G fine) & i'm not sure how to move forward to a resolution. My N-network (LinkSys 600N Router) does not have any security & it controlled by MAC access list. Tried the linux-backports-modules & the mad-wifi driver

I would highly appreciate if someone could send me specific instruction to have it work in 11N mode. I'm running Karmic Koala on 2.6.31-16 kernel

---

