---
title: "Gnomebaker fails to burn"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by spinstartshere on 2007-05-29
I want to use Gnomebaker to add some data to a DVD.  The disc is not finalised, and burns succeed in Windows.  When I try to import the previous sessions with Gnomebaker, I get this message:
[CENTER]The mount point (e.g. /mnt/cdrom) for the writing device could not be obtained. Please check that the writing device has an entry in /etc/fstab and then go to preferences and rescan for devices.[/CENTER]
How can I resolve this issue?

---

### Post by Ramaddan on 2007-06-03
That means that the fstab is setup wrong.

In Gnomebaker, go to:
> Edit->Preferences->Devices

You will see your detected devices.

Write down the what is in nodes somewhere.

Now go to a terminal and type:
> sudo gedit /etc/fstab

Look for something like:
> /dev/sr0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Adjust the [COLOR="DarkRed"]**/dev/sr0**[/COLOR] part to the node that you took earlier on from the devices in Gnomebaker.

You might have more than one line of this, depending on how many DVD/CD drives you have.
If you have more than one, then make sure that the [COLOR="DarkRed"]**/media/cdrom0**[/COLOR] part increments.

For example you have two drives, then the [COLOR="DarkRed"]**/dev/sr0**[/COLOR] will be slightly different for the first line and second line.
And the [COLOR="DarkRed"]**/media/cdrom**[/COLOR] part will end with [COLOR="DarkRed"]**cdrom0**[/COLOR] for the first line, and [COLOR="DarkRed"]**cdrom1**[/COLOR] for the second line.

**NOTE: You will have to restart for changes to take effect.**

Hope this helps.

---

### Post by spinstartshere on 2007-06-03
It's burning now.  Thank you.

---

