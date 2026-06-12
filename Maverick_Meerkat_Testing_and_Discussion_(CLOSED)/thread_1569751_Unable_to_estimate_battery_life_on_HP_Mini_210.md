---
title: "Unable to estimate battery life on HP Mini 210"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ljrmorgan on 2010-09-07
Hi,

I've just upgraded my HP Mini 210 from Lucid to Maverick. The battery indicator in gnome no longer tells me how long/how much charge the battery has left, instead it just says "Laptop battery (estimating...)".

This feature worked fine in Lucid.

The netbook does still detect when I plug in the charger, though again the battery indicator does not seem to know how charged the battery is.

Any suggestions on how I might fix/troubleshoot this or where to file bugs?

Thanks,

Louis

---

### Post by KdotJ on 2010-09-07
Hey, I have the same netbook as you and I'll check when I'm home if I'm getting this bug too. I know that under lucid it never showed me the actual time remaining, but just a percentage. Is this the same for you?

Also, while talking of the HP Mini 210, does your right-click work? Mine doesn't work at all and my mousepad isn't all that great for clicking. 

I'll check your issue on mine and report back

---

### Post by glasen on 2010-09-07
This is not a bug of Ubuntu. It is ACPI-bug. Windows XP also doesn't show the time, only the percentage.

The ACPI-table of this netbook only exports the percentage of battery, not the remaining capacity.

---

### Post by ljrmorgan on 2010-09-07
The battery indicator does not show the time or charge left (it used to show the percentage charge left). It simply says "Laptop battery (estimating...)". I don't know if this is a bug with the indicator, or something deeper.

@KdotJ: My right click/clickpad is a disaster, nothing works properly, it's practically unusable. I tracked down a kernel patch & an X patch that might fix it, but I don't want to mess everything up trying to apply them. I tried using utouch, but that didn't work.

---

### Post by ljrmorgan on 2010-09-07
> **ljrmorgan said:**
> The battery indicator does not show the time or charge left (it used to show the percentage charge left). It simply says "Laptop battery (estimating...)". I don't know if this is a bug with the indicator, or something deeper.

@KdotJ: My right click/clickpad is a disaster, nothing works properly, it's practically unusable. I tracked down a kernel patch & an X patch that might fix it, but I don't want to mess everything up trying to apply them. I tried using utouch, but that didn't work.

On the plus side, the light on the mute key now works properly. :-D

---

### Post by KdotJ on 2010-09-07
> **ljrmorgan said:**
>  My right click/clickpad is a disaster, nothing works properly, it's practically unusable. I tracked down a kernel patch & an X patch that might fix it, but I don't want to mess everything up trying to apply them. I tried using utouch, but that didn't work.

It's such a pain! It *worked* under Lucid (although the fix only came at RC release time, and came along in a normal update from the Update Manager). I say "worked" loosely though, as even though I was able to right-click, the performance and usability of the mousepad was overall quite terrible.

I hope we at least get rigt-click by the time of release

---

### Post by Casey R on 2010-09-13
Having the same problem here.

I have resorted to using the battery applet in Docky to see the battery percentage.

---

### Post by kouter on 2010-09-19
Problems with touchpad and battery also present on HP dv7t.  Touchpad and left/right-click are one piece, so when I need to click and drag, cursor jumps around the screen with second finger moving on the touchpad.

---

### Post by KristinaK on 2010-09-23
will it be fixed in 10.10 rc? or should I stay with my windows 7?

---

### Post by ljrmorgan on 2010-09-23
> **KristinaK said:**
> will it be fixed in 10.10 rc? or should I stay with my windows 7?

If I were you I would install Lucid (10.04) on your mini 210. The trackpad is a little hard to use (but there is a fix in the forums), but the battery indicator works and the wireless works (basically everything works).

The only problem I had with lucid was that the LED on the mute key was always lit (whether or not the netbook was muted) (note the sound etc. worked fine, it was just the led that didn't). This has been fixed in Maverick.

However, Maverick does seem to introduce a few problems, so if I were you I'd install Lucid (which is LTS) instead of the beta of Maverick. You can always upgrade easily to Maverick later on once the issues have been fixed.

I personally am using Maverick on my 210 having upgraded from Lucid. This battery thing is the only problem I have, and it's more of an annoyance than anything else. Other people seem to have different problems though, so I would stick to Lucid if you want to avoid breakage.

---

### Post by KristinaK on 2010-09-24
thanks, is this bug reported to developers?

---

### Post by ljrmorgan on 2010-09-24
> **KristinaK said:**
> thanks, is this bug reported to developers?

I haven't reported it, but only because I don't know with which package the problem lies. That's why I started this thread actually - to see if anyone could help me track it down.

---

### Post by plun on 2010-09-24
> **ljrmorgan said:**
> I haven't reported it, but only because I don't know with which package the problem lies. That's why I started this thread actually - to see if anyone could help me track it down.
 
This is existing bugs with gnome-power-manager, sorted "Newest first".

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Howto file a new one:

```
ubuntu-bug gnome-power-manager
```

Good luck !

---

### Post by ljrmorgan on 2010-09-24
> **plun said:**
> This is existing bugs with gnome-power-manager, sorted "Newest first".

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Howto file a new one:

```
ubuntu-bug gnome-power-manager
```

Good luck !

Thanks, this looks like the right bug - very similar netbook and the same problem.
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/645220]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/645220")

---

### Post by Quackers on 2010-09-24
Same symptom on Sony Vaio AR51SU.

---

### Post by plun on 2010-09-24
> **ljrmorgan said:**
> Thanks, this looks like the right bug - very similar netbook and the same problem.
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/645220]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/645220")

Yup......

Please note that all affected can add themselves to the bug !

[IMG]http://img843.imageshack.us/img843/9764/snapshot49.png[/IMG]

Someone must also confirm the bug running this hardware... !

Maybe also nominate this bug for Maverick ?

---

### Post by ljrmorgan on 2010-09-24
> **plun said:**
> Yup......

Please note that all affected can add themselves to the bug !

[IMG]http://img843.imageshack.us/img843/9764/snapshot49.png[/IMG]

Someone must also confirm the bug running this hardware... !

Maybe also nominate this bug for Maverick ?
Yeh, I clicked the "affects me too" and mentioned the netbook in a comment - should I post any files or anything?

Thanks for your help.

---

### Post by CoolJohnB on 2010-09-24
Same bug with Dell Vostro 3700

---

### Post by Quackers on 2010-09-25
After installing all the available updates today it seems that my battery indicator is now working. I'm not sure it's accurate though. I've had a few odd readings but it seems to have settled down now.
I only get "estimating" now when it is charging.

---

### Post by magicfab on 2010-09-28
I've chosen this bug as the master one for this issue, as it was filed earlier:
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/629258](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/629258)

If anyone feels they should, please go ahead and mark as "affects me too".

I've confirmed it and marked as "Medium" importance.

---

