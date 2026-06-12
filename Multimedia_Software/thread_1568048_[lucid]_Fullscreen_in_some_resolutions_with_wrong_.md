---
title: "[lucid] Fullscreen in some resolutions with wrong ratio, stuff beyond screen."
date: 2010-09-04
forum: Multimedia Software
---

### Post by Mr. Jack on 2010-09-04
Hi, i need you help please, I have been using Ubuntu since Karmic and i love it.
However i have now a problem that I can't solve myself :(

Sorry for any writing mistake, English isn't my main language 

Some of my software (mainly old) have low resolutions that can't be changed and in fullscreen they have the wrong ratio and the missing stuff appear "beyond" screen where i can't see it.

My native resolution works fine.

This started when i installed the nvidia x server, for the graphic drivers, that i need to run some stuff.

One thing I notice is that, in the nvidia x server settings, on the resolution field the resolutions that work have "60 hz" as the only option for the refresh rate (besides auto) however the "faulty" resolutions have "60 hz (DoubleScan)" as the only option, so maybe it's the refresh rate.
And is know that these resolutions work well in my laptop, they worked well in before the driver install 

Is there any way to force "60 hz" in all the resolutions as the only option or something like that to help solve my problem?

Thanks for your help and support. :p

---

### Post by Mr. Jack on 2010-09-04
Please i really want to solve this :(

Maybe it will help if I post something more about my system or something?

I dunno... ;_;

EDIT: Solved it.
Added the line

Option         "ModeValidation" "NoXServerModes"

in the section

Section "Device"

of the xorg.conf file.

Lost some (useless for me) resolutions, but now the ones i need are fine now.
Will just leave here, just in case someone have the same problem.
Thank you for your non-help ;)

---

