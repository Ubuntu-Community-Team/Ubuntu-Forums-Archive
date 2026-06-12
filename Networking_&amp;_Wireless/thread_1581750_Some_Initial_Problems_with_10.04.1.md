---
title: "Some Initial Problems with 10.04.1"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by Billsey on 2010-09-25
I (just in the last couple of days) upgraded my P4 to 10.04.1 and ran into some problems:

**Samba Log-in Problems**

One of these is a rather odd and very annoying problem with shared folders. I first tried using the "Sharing Folders" item under the Administration menu, only to discover that it only seems to allow NTFS shares (which I would seem to be a complete and total dunderhead at). Not one of these attempted shares even showed up on my little home LAN (of 4 Ubuntu systems, 2 (old) Mac systems—one OSX and one OS9—and a network printer). I then used the "Sharing Options" method from the pop-up menu that comes up when you right-click a folder icon or folder name (in list view). The result of this was that my account log-in kept getting rejected whenever I tried to mount one of the new shares (using one of the other Ubuntu boxes; this one using 10.04 as well). This is an annoying problem, and I would love to see a real fix for it. I have, however, found a usable workaround which, for those who don't use passwords on their home LANs, could be a permanent workaround; I, however, prefer password protection—even if it is scant. The workaround is very simple (though I might lose a slight amount of sleep over it): go to each of those shares, and open the sharing options dialog, and click the option for allowing guest log-ins. This should allow you (and others, unfortunately) to access your shared folders.

**The Cheshire Mouse Pointer**

On my P4 I use a screen resolution of 2048x1536, and this problem might be related to that screen resolution (though I can't imagine why). Quite simply, the mouse pointer appears and disappears at odd times (and it might be connected to the screen blanker). Given the CTRL key locator option of the mouse preferences, I am able to find this somewhat amusing, but I would get more enjoyment out of a permanent fix to the problem. :)

**In Conclusion**

I am still running into things that I thought were a default of the OS, but that I must have configured myself—and I am solving as I go. All that being said, however, I am glad to have another box up to the latest LTS and plan to upgrade the remaining two as I find the time (though you might consider making the configuration option for the position of the window gadgets easier to find; perhaps by making it a selectable option in the theme or appearance preferences). All in all, so far, good job.

---

### Post by Billsey on 2010-09-27
Well, I ran into the same scanner problem that other Epson users keep running into, but researched the forums and got that solved (again).

Now, I have an update to the "Cheshire Mouse" problem. I have been able to repeat a method of getting it to appear. This is going to sound really, really, REALLY strange (and some steps might be unnecessary), but here goes:

log in
struggle to find pointer
Launch gFTP
set local folder to /home/<username>/temp
go to remote site password gadget
type in password
mouse appears

I know that REALLY sounds strange, but, so far, it works. I hope it helps the experts here to find out what the real cause of the problem is. :-D

---

