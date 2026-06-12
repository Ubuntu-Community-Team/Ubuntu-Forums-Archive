---
title: "Use an Android Phone as a Bootable Ubuntu &quot;USB Drive&quot;?"
date: 2014-10-12
forum: Mobile Technology Discussions (CLOSED)
---

### Post by promet on 2014-10-12
Hi, 

I have a handful of bootable Ubuntu usb drives which work great for "roaving" Ubuntu, rescuing friend's systems, etc.; I am wondering though, would it be possible to have a bootable Ubuntu install on an android phone? That is, to boot Ubuntu on an external pc, from the android via usb? While keeping the operational android functionality as well, of course. It would be A) awesome and B) one less bit of kit to carry around. I feel like it's doable, but it is a bit beyond my scope. Does anyone have any thoughts, or has heard of anyone pulling this off?

Thanks!

---

### Post by Vladlenin5000 on 2014-10-12
In older Android versions where the default was the mass storage protocol it was theoretically possible but in the real world it resulted almost impossible due to the way Android detected and activated access to its flash memory. In order to achieve the desired effect the phone would need to be already sharing when the user is about to choose the boot device in BIOS and most of the times that didn't happen.
Not really doable, in a nutshell.
Now, all the current Android versions moved to MTP/PTP protocols instead of the traditional mass storage, making it impossible.

---

### Post by Dose123 on 2014-10-25
[COLOR=#000000]from the android via usb? While keeping the operational android functionality as well, of course. It would be A) awesome and B) one less bit of kit to carry around. I feel like it's doable, but it is a bit beyond my scope.




Kool[/COLOR]

---

### Post by Vladlenin5000 on 2014-10-26
> **Dose123 said:**
> [COLOR=#000000]I feel like it's doable, but it is a bit beyond my scope.[/COLOR]

Hi, welcome.

I already explained why it isn't. Please read the previous post.

---

