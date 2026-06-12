---
title: "iOs 5 + ubuntu 11.10 = bad combination"
date: 2011-10-18
forum: Multimedia Software
---

### Post by patriciad on 2011-10-18
So, I'm not a Ubuntu "newb", but I still don't know much. I should have realized, however, that it usually isn't wise to update your computer and iPod on the same day to brand new software versions.... Well, too late I already did ~_~.

I've searched the net, but there is literally nothing out there yet for support on this issue that I could find. I have an iOS 5 iPod touch 3rd gen and Ubuntu 11.10. I also have libimobile and sync was working perfect before the updates. The first time I tried to sync it to Banshee, it popped up with "Unhandled lockdown error (-4)". I then updated multiple things again with update manager and restarted. The error was gone, but this is where the real problem starts. Now, whenever I link to Banshee, it get's 10-30% through my music before crashing (this is not when it's actually syncing to the iPod, it's before it says "preparing to sync"). I tried using a smaller number of songs and, while they loaded ok, it crashed during "preparing to sync" and the iPod screen did not change.

I'm assuming this is a bug since it's so fresh after the release, but I want to make sure there isn't anything else I can do. Let me know whatever else information I can get to you.

-cheers

---

### Post by phantomn on 2011-10-19
Yeah I did this and well and I'm having the exact same problem, when just copying one song over Banshee needs to convert it, and then when it syncs to the iPod it can't see it.

---

### Post by monicod19 on 2011-10-21
I guess somethings still needs to be fixed. I am not sure what is happening as I am a newbie in ubuntu which i am starting to use heavily after someone from ACRYAN gave me this solution to access my ACRYAN properly against Windows7. 

Now for awhile I was happy using it as I can access all my devices at home including my Iphone. Now after the official release of Iphone4 IOS5 i came across several problems, 
1. Unhandled lockdown error (-4) but was fixed after some updates I did using Update tool of Ubuntu. It was working for a while with even the battery/power bar showing the progress/status of my notebook and my Iphone. However 2 days back for no apparent reason, your problem reported here is now happening whenever I attach my Iphone.
2. Unhandled lockdown error (-15) which happens all the time, I searched as well the internet but no such luck. libimobiledevice programs are at 1.1.1-1ibintu1 and I saw the thread that it is still being investigated.

I hope that someone could fix this as I am starting to like Linux desktop now after getting out of it for a couple of years now..

---

### Post by primalsmoke on 2011-10-21
I had the same problem today.
Fixed it.
As of October 20th, it is working.
History:
I upgraded to 11.10 and it was working with IOS4.
Last night I upgraded the phone to IOS5 and it broke (error 15)

Solution:
You need to re-associate the IOS phone with the Computer.
the program that "talks' to the phone is called libimobiledevice
make sure you have an updated version.
you will need to install a package with the utilities for libimobiledevice as well as another program called ifuse.

somebody already posted the solution at [http://ubuntuforums.org/showthread.php?t=1861617](http://ubuntuforums.org/showthread.php?t=1861617)

it works for me...;)
hope this helps

---

### Post by monicod19 on 2011-10-22
Hi thanks for the note. I have done this before but no luck, but today I am not sure what happened with my device but only because I did shut it down this morning and restarted it this afternoon my time. Executing the first line sudo apt-get... fails as apparently my device already have the packages (did not check my bad).. The second step of unpairing and pairing did the trick for me but I am again not sure as I've done this before but failed.

Thanks though as my device is back and seen by Ubuntu, now need to check on the other stuff like transfering things over to my Iphone..

cheerio...

---

### Post by phantomn on 2011-10-27
That helped slightly, now my laptop can see my iPod but cannot sync songs onto it that the iPod can see, so I still can;t sync any music...

---

### Post by Yogotiss on 2011-10-30
> **primalsmoke said:**
> I had the same problem today.
Fixed it.
As of October 20th, it is working.
History:
I upgraded to 11.10 and it was working with IOS4.
Last night I upgraded the phone to IOS5 and it broke (error 15)

Solution:
You need to re-associate the IOS phone with the Computer.
the program that "talks' to the phone is called libimobiledevice
make sure you have an updated version.
you will need to install a package with the utilities for libimobiledevice as well as another program called ifuse.

somebody already posted the solution at [http://ubuntuforums.org/showthread.php?t=1861617](http://ubuntuforums.org/showthread.php?t=1861617)

it works for me...;)
hope this helps

Thanks for the Link! It helped me with my iPod Touch 4th Gen running iOS 5

---

