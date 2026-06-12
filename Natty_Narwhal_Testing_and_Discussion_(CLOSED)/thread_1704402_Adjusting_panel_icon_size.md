---
title: "Adjusting panel icon size"
date: 2011-03-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-03-10
In the chanelog for the new unity (3.6.4, later today) didn't see [this inc. yet ]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/713087")so decided to try on the current source (3.6.2
Very nice, hope they work out any issues (haven't seen any yet), would be really good on my laptop where the default 48px is much too large

The new min. is 32 px, not sure if that is the technical min or just decided on.
screen is on a desktop where the 48 was ok., 38 is better. (new install so launcher isn't populated

edit: screen 2 on a fresh install on a  small laptop - 32 is much better, a bit smaller would be ok, will have to try adjusting source to see if possible

---

### Post by mc4man on 2011-03-10
While it wasn't in the changelog (unless i'm missing it), the new 3.6.4 unity does have the launcher icon resize applied, very nice touch.

---

### Post by beew on 2011-03-10
A patch will be included in some future updates to do that. In the meantime there is a hack for it (actually the hack is the patch)
[http://www.webupd8.org/2011/02/unity-launcher-will-support-icon.html]("ttp://www.webupd8.org/2011/02/unity-launcher-will-support-icon.html")

---

### Post by mc4man on 2011-03-10
> A patch will be included in some future updates to do that.

It's included in the new unity as of today (3.6.4

---

### Post by kerry_s on 2011-03-10
it's nice, did you guys notice scroll now works in applications ?
also there is a new section "apps available for download".
i clicked on preview, but software center just crashed.

---

### Post by mc4man on 2011-03-10
> **kerry_s said:**
> it's nice, did you guys notice scroll now works in applications ?
also there is a new section "apps available for download".
i clicked on preview, but software center just crashed.
Yeah, there seems to be quite a number of small bug fixes and some things added,to the places.
(worth reading thru the changelog

On one install clicking on something from apps available for download opens SC., on the other it crashes out.

---

### Post by kerry_s on 2011-03-10
> **mc4man said:**
> Yeah, there seems to be quite a number of small bug fixes and some things added,to the places.
(worth reading thru the changelog

On one install clicking on something from apps available for download opens SC., on the other it crashes out.

i just noticed there's right click menu's, yay!

---

### Post by webme on 2011-03-10
Yes, nice improvements!

---

### Post by kansasnoob on 2011-03-10
I wonder what the plan is for "managing" similar adjustments on Unity 2D? I haven't worried much yet because the applications menu still fails to "populate".

---

### Post by kerry_s on 2011-03-10
> **webme said:**
> Yes, nice improvements!

you must have a large screen, mines 1024x768 & my menus always use the full screen, i've never had the corner size adjust icon. :confused:

---

### Post by mc4man on 2011-03-10
> **mc4man said:**
> 

On one install clicking on something from apps available for download opens SC.,_ on the other it crashes out_.

Have figured out why it crashed on one machine which was  a 1 day old install.
That machine (nvidia 7800 AGP), was using nouveau 3d drivers due to the current memory issue w/ nvidia-current (the machine only has 1GB mem so nvidia-current is pretty much unsuitable till fixed, if it ever is.

It turns out (at least w/ the hardware here), that some other updates today have made Software-center segfault w/ the mesa 3d drivers. Haven't had a chance to see if anything else is affected.

---

### Post by mc4man on 2011-03-10
> **kerry_s said:**
> you must have a large screen, mines 1024x768 & my menus always use the full screen, i've never had the corner size adjust icon. :confused:

The dash falls under the 75% threshold to maximize windows when opened, so if it is 75% or larger of the available display area it (dash or any window), will open maximized. (the only diff is dash can't be resized by the user to fall under the 75%

Here on a 13" laptop I'd need to move the threshold up to probably around 85 % to keep dash windowed.

---

### Post by VinDSL on 2011-04-09
> **kerry_s said:**
> you must have a large screen, mines 1024x768 & my menus always use the full screen, i've never had the corner size adjust icon. :confused:
Try forcing it into desktop mode...

```

gsettings set com.canonical.Unity form-factor Desktop

```


If you want to switch back to full screen...

```

gsettings set com.canonical.Unity form-factor Netbook

```

---

