---
title: "Asus WL-138g (mrv8k51)"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by Mr. Picklesworth on 2006-06-01
Has anyone got Ubuntu Dapper's wireless stuff working with the Asus WL-138g wireless card, or another wireless card with mrv8k51 driver?
I had Breezy working with it once, and I never really figured out how. (It was incredibly painful). Seemed to involve following a magical tutorial, having the computer freeze when I tried to run a web browser as a failed test, and then it set up perfectly when I restarted. (Prompting me to download some really huge packages out of excitement, resulting in my installation getting slaughtered from lack of space... and that was the end of that!)

I believe Dapper was originally saying to be doing wireless with my card out of the box, but I never really had much success... may just be my driver version and the fact that I had never done a full reinstall, though.
What I've had is ndiswrapper accepting to install the driver, then when I called modprobe ndiswrapper, it didn't work.
I'll get the dmesg up here in a while...

---

### Post by Mr. Picklesworth on 2006-06-01
Okay, here is my experience so far:

Attempted installing Win2000 driver for my wireless card using ndiswrapper (on Dapper install CD).

Here is the log:
*Removed -- irrelevent*
As you can see, it didn't work.
Removed that driver, tried the XP one... modprobe just doesn't do anything for eternity. Attempting to remove old ndiswrapper modprobe entry (modprobe -r, I think) also causes it to eternally freeze. (That one is the most strange, since wouldn't it just tell me the entry doesn't exist, or did it actually write something the first time and leave it there in its broken state?)
Cancelled...
Restarted the computer to see if it would fix the problem, and now "Setting up network interfaces" freezes on startup.



Edit:
Looking at the ndiswrapper web site, I see that Dapper has already been added to the explanation for WL-138g:
(From [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List))> Other: Ubuntu Dapper (beta 2) comes with native Marvell driver mrv8k [[26]]. To use ndiswrapper, you must prevent it from loading at boot. I simply removed the mrv8k.ko file from /lib/modules/...kernel..., but there may be a nicer way. Otherwise works fine with DLink Win98 driver. 
I will try this when I get home today!

Edit 2:
Yay!
Upon following those directions exactly (and restarting the computer for good measure), I can do modprobe ndiswrapper without problem, and the wlan0 interface is available.
I can scan for access points, but that's about it...
Looking at dmesg, I appear to be getting the following noteable messages:
```
ndiswrapper (set_essid:61): setting essid failed (C0010015)
```And... Could this be my driver?:```
FAT: UTF8 is not a recommended IO charset for FAT filesystem, filesystem will be case sensitive!
```

Any ideas what this may be about?
I remember getting this error in previous failed attempts to set up with this card, and a web search tells me that a few other people with this card have had the error, too.

I have attempted setting up twice, both with the same result.

---

### Post by Mr. Picklesworth on 2006-06-04
First, sorry about all these bumps...
Honestly, I wouldn't be bumping this thread if I could help it... but editing posts constantly can get ugly. (Well, that's the excuse, anyway).
I hope this thread turns out helpful to others :)

Now, I still have the Setting Essid Failed problems, but now Dapper has become unable to start up due to unexpected termination of ndiswrapper when setting up network interfaces. Seems to freeze the entire startup.
I believe this was caused by me setting up and activating wlan0 to be talking to my wireless network, and it can't do that because it can't set the essid.

I found an old thread from the Dapper beta / alpha forums, here:
[http://ubuntuforums.org/showthread.php?t=144968](http://ubuntuforums.org/showthread.php?t=144968)
I will see if Asus's latest drivers work...

First, however, I have a startup problem to solve. I guess booting in recovery mode will stop that.


Edit:
Okay, the problem with setting up network interfaces on startup fixed itself the third time I restarted. Switching to text mode instead of displaying the usplash seems to have made the difference.
Got a different warning message, though...
Something along the lines of: NDISWrapper IO unimplemented.
I suppose that is confirmation that the above problem with UTF8 could be the source of my troubles. Not too hard to believe...

---

### Post by daveZ on 2006-06-07
removing the mrv8k.ko driver worked for me too. See my post about it [here]("http://ubuntuforums.org/showthread.php?t=190726").

~daveZ

---

### Post by Mr. Picklesworth on 2006-06-13
Yay, it works!
What I did:

-Deleted mrv8k.ko driver from /lib/modules/...kernel...
-Restarted computer.
-Installed latest ndiswrapper from source. I'm not sure how well the one that comes with Dapper works, but I decided to play it safe.
-Downloaded the latest WL-138g driver from Asus.com and used CabExtract (or maybe it was Unshield).
-Installed Windows 98 driver and configured Wifi.

No problems so far.


Thanks for the link, Dave.

---

### Post by veganalex on 2006-08-23
***i know this is an old topic...but***

hello,

i never got my wireless card with marvell chipset to work when i installed ubuntu dapper-drake. (i ended up giving up and installing the old version of ubuntu again...then that won't work - so i go to PClinuxOS (then install gnome ;))). well, i have a dynamode WL-GI-600XA (54g wireless card), and the driver is mrv8k51 - same as yours. (i have many, many problems with this card under windows xp too :() right, i haven't reinstalled ubuntu to try your steps but basically - would the other mrv8k51 drivers for other manufacturers cards work the same or better with both windows xp (hint, hint! i need help! lol) and linux.

veganalex (aka -|- awave)

---

### Post by eduif on 2006-10-02
I tried everything I could find in this forum to get my Asus WL-138G to work, and finaly, when I had actually given up, it did (work).
When I cleaned up and uninstalled my previous attemts ('ndiswrapper -e mrv8k51' uninstalled the Windows XP driver I tried) 
Then 4 steps to victory where:
1: cd to Windows 2000 driver on my Asus WL-138G installation dis.
2: ndiswrapper -i mrv8k51.inf
3: ndiswrapper -m
4: reboot (I didn't even dear to check if there where error messages).
After rebooting the 'mesg' command showed good initialisation, and I could connect to my AP (Wireless Access Point) with the networking config dialog under System > Administration menu.
Thanks for all advise and suggestions, and long live the Windows 2000 driver.

---

### Post by eduif on 2006-10-08
I think I must have done something more then just the above.
Because when I had to re-install ubuntu again, I did not get it working with the above steps...
So now I am back at trying all kinds of things I can find on website...

---

### Post by eduif on 2006-10-08
as it seems it was the removal of the mrv8.ko file as described somewhere in this page...
At least, I think so. Currently I am wireless connected again.

---

