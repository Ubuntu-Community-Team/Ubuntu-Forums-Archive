---
title: "Nvidia Restricted Driver Problem"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by monsieurdozier on 2007-10-28
I just installed Gusty Gibbon on a PIII with a Nvidia MMX Video Card.  It said that I should use the restricted drivers, so I followed the onscreen commands and when I rebooted, all I get is a black screen.

It worked fine until I used the restricted Drivers.  What can I do to get this to work, or to get it back to the way it was?

Monsieur Dozier

---

### Post by Kool_Kat on 2007-10-28
You could edit your xorg.conf file and replace the driver "nvidia" with "nv". That will get you back to a default state. However, if you want to get your nvidia drivers to work properly - I wish you luck - there are a quite a few of us who can't get them to work properly with Gutsy Gibbon - just search for posts on Nvidia.

---

### Post by monsieurdozier on 2007-10-28
> **Kool_Kat said:**
> You could edit your xorg.conf file and replace the driver "nvidia" with "nv". That will get you back to a default state. However, if you want to get your nvidia drivers to work properly - I wish you luck - there are a quite a few of us who can't get them to work properly with Gutsy Gibbon - just search for posts on Nvidia.

That worked.  I'll just cruise around looking for answers.  Thanks.

---

### Post by Kool_Kat on 2007-10-28
If you find one that works - let us all know - as many of us are currently struggling.

---

### Post by geezerone on 2008-03-23
> **Kool_Kat said:**
> ...there are a quite a few of us who can't get them to work properly with Gutsy Gibbon.

That would be me too trying to get a 6600 gfx card to work with proprietary drivers and just get the usual blank screen. :(

---

