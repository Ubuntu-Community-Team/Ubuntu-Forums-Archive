---
title: "Yet another BCM4318 issue (Acer Aspire 3000 series w/ Jaunty)"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by uziel on 2009-11-26
I'm obviously not the first and certainly not the last one to have troubles with a wireless card on a BCM4318 (rev 02) chipset, but so far I haven't found a solution, thus I'm starting a new thread.

I've recently got a wireless router and thus wanted to get the wifi in my mother's laptop (Acer Aspire 3000 series, can't check which model exactly) working. (Luckily in my one the card is Intel's and has always worked without any tricks.) The card is enabled and working in Windows. In Ubuntu, I tried performing many random howtos and even got it working twice for a while (it connected to the network, same after a reboot, but failed the next day). Convinced that vehement and absent-minded application of magical solutions could mess my wifi config beyond recognition, I decided to reinstall the system so that I can at least describe the situation precisely.

I performed a fresh install of Jaunty from a CD, installed all available updates and rebooted. At this point Network Manager detected no wireless networks. I enabled the b43 driver in System»Administration»Hardware Drivers and rebooted, but nothing changed. Finally, I recreated all steps of [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) and now the networks are detected, but I can't connect to the (WPA encrypted) network set up by my router.

Now I feel somewhat stuck, because most of howtos either look exactly as the last one mentioned, or return to the use of b43, which has failed, too. There's also a possibility of compiling ndiswrapper from source, but it's a last resort and I'd rather avoid it.

I've read stories of people that rely on the manual configuration of networking, but in case of my mother's laptop this is out of question. I'd be happy to provide more info on the hardware and present config of that machine, but I'm not at it at this instant.

---

### Post by Metaljaz on 2009-11-26
Not the same Ubuntu version but give it a read:

[http://ubuntuforums.org/showthread.php?t=1291323](http://ubuntuforums.org/showthread.php?t=1291323)

change jaunty to karmic

---

### Post by uziel on 2009-11-30
That didn't work. But actually my problem is solved, and what is more irritating, it probably didn't ever need solving.

What happened? I undone all changes I did since updating all packages on the system, both from the topic linked by Metaljaz and the howto I linked in the first post here. I uninstalled ndiswrapper's driver, removed an update-rc script, restored config files to their previous form, and finally removed all packages that got installed in course of these two manuals. I reinstalled b43-fwcutter, and after a reboot, lo and behold, I have a wireless connection (even without specifically enabling the proprietary driver in jockey).

Yet again, after turning the laptop off and disconnecting it from the mains (the battery is doesn't function any more for a long time now), the card didn't scan the networks again. I became a little suspicious, and it turned out that after pressing the "enable wireless" button on the front of my laptop everything gets back to normal. If this was the case earlier too, then most of my activity here was not needed at all, with the system reinstallation in the first place.

So a subtle message for people in a similar situation: **if your wifi adapter works and then stops for no reason, try pressing the "enable wireless" button or ifupping it**, before you proceed to more drastic measures.

I doubt, however, that really many people will encounter such situation. Apparently the card got disabled after the laptop was disconnected from any source of current. Here it happened every day (the computer doesn't see the battery at all and the cord is plugged to a surge protector, turned off whenever the computer is not in use), and in normal case, where there is always a battery working with at least some residual voltage, this won't happen.

Now the last remaining thing is to force the card to be automatically enabled during bootup in any case.

---

