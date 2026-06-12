---
title: "HP 6535b and Ubuntu 11.10 Wireless Issue"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by dubtdi on 2012-03-15
I'm relatively new to Ubuntu and finally came across this issue that I can't resolve on my own even with all the online posts.  I have a HP Compaq 6535b with 11.10 64-bit installed.  Wired networking works fine but wireless does not.  I'm not able to turn on the wireless adapter on the laptop touch panel and within gnome I can't see any wireless networks even though wireless networking is turned on (or so it says).  During the install, Ubuntu recognized my wireless adapter (Broadcomm but I can't seem to locate the actual number...BIOS says BRCM1306).  I've spent several hours pouring through posts on several forums but haven't found anything that would help.  I'm an IT guy and know my way around Windows and MacOS but a bit of a fish out of water with Linux.

Funny thing is that I had wireless fully operational under 11.04 just 2 days ago.  Then one evening, the machine's video went beserk during an update.  A series of boot issues followed and I tracked it down to a bad primary SODIMM.  I replaced all the RAM tonight, 11.04 booted fine time after time but no wireless.  Knowing about a buggy 11.04 kernel, I thought I'd try 11.10 but to no avail.  I'm quite stuck with my limited knowledge to troubleshoot.

I suppose it could be a bad network card and whatever zapped the RAM affected the card but I thought I'd try an OS fix first.  

Any help would be greatly appreciated.  Thanks in advance.

Alex

---

### Post by Athena's Owl on 2012-03-15
Hey there, I'm having my own struggles with 11.10 and a broadcomm wireless card. I'm assuming you tried out the solution where you connect with ethernet, install the Synaptic Package Installer and then load the firmware-b43-lpphy-installer? that's the first thing I tried, but it didn't work for me.

ETA: that driver may not work depending on the specific model number of your broadcomm card. check out [http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44) for a nice initial troubleshooting list so you can find out exactly what model number of broadcomm card you have.

And I must say that after this experience, none of my future computers are *ever* going to have a piece of hardware made by this company. I carry computer hardware grudges to my grave.

---

