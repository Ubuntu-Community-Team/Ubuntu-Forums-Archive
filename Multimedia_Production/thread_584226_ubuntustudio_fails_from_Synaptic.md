---
title: "ubuntustudio fails from Synaptic"
date: 2007-10-20
forum: Multimedia Production
---

### Post by Shlomir on 2007-10-20
When trying to upgrade my Gutsy with U-0studio, I keep getting all these failed dependencies..Shouldn't the software find them all? And why are they all broken since going to Gutsy??


ubuntustudio-video:
 Depends: cinepaint but it is not going to be installed
 Depends: dvgrab but it is not going to be installed
 Depends: ffmpeg but it is not going to be installed
 Depends: ffmpeg2theora but it is not going to be installed
 Depends: kino  but it is not installable
 Depends: stopmotion but it is not going to be installed

Is this because the main kernel is different, and is so,m how do you go about installing a new one that will play nice with the Ubuntu Studio suite?

---

### Post by TransitMan on 2007-10-21
From [http://ubuntustudio.org/](http://ubuntustudio.org/) front page:

**News:**

  **A Message From The Emergency Broadcast System. **

 *October 19th, 2007*
 UbuntuStudio.org is dealing with unforeseen hosting issues. Please be patient.


************************************************
So give it time to get sorted out.

---

### Post by Shlomir on 2007-10-21
Thanks for that useful info...I'll stay put for the next coupla weeks and stick to what I've got!

Cheers

:guitar:

---

### Post by MetalMusicAddict on 2007-10-21
> **Shlomir said:**
> Thanks for that useful info...I'll stay put for the next coupla weeks and stick to what I've got!

Cheers

:guitar:

The issue with the site is only a graphic one.

You can update Ubuntu Studio just fine. Post your sources.list. I'm almost willing to bet you changed the Ubuntu Studio repo line over to Gutsy. If so, remove it all together. Its unneeded as all of the packages are in the Ubuntu repos now.

---

### Post by TheFisherman on 2007-10-23
> **MetalMusicAddict said:**
> Its unneeded as all of the packages are in the Ubuntu repos now.

Almost all of them. The lowlatency kernel packages are in the Ubuntustudio repos. So you still need the Ubuntustudio repo line in the sources.lst. Only with Gutsy it doesn't work currently due to Ubuntustudio's hosting issues.

---

### Post by TheFisherman on 2007-10-23
> **TheFisherman said:**
> The lowlatency kernel packages are in the Ubuntustudio repos.

Just checked. In fact, MetalMusicAddict is right. The kernel packages  aren't marked lowlatency any more but rt (for realtime). They're in the Ubuntu repos.

---

