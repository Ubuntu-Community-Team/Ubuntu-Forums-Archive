---
title: "[SOLVED] Screen Blanks at Bootup"
date: 2008-06-18
forum: Mythbuntu
---

### Post by tonyr1988 on 2008-06-18
I just put a fresh install of Mythbuntu 8.04 on my desktop (It previously ran 7.10, but was so botched I just restarted). I checked the CD for defects (there were none) and everything installed perfectly.

However, when I boot it up, it goes all the way through GRUB and to the splash screen (Mythbuntu logo + progress bar). As soon as the progress bar goes to the end, it stops any and all output. My monitor goes to hibernate mode. I've tried this over VGA and S-Video (which it's configured to use), getting the exact same result.

Any idea what would be causing this? I'm using the new nvidia drivers (I think nv_new during setup), which is exactly what I was using before.

P.S. Recovery mode does the same thing.

---

### Post by CrimsonEclipse on 2008-06-18
I had a similar problem when I installed the first time using the 
modified drivers box. I re installed using the Live CD feature and 
leaving the modified drivers box unchecked. I then updated the drivers
after the install was complete (after restart).

Just so you know, I'm still new at this so there's probably a better explanation.

Cheers

CE

---

### Post by tonyr1988 on 2008-06-19
> **CrimsonEclipse said:**
> I had a similar problem when I installed the first time using the 
modified drivers box. I re installed using the Live CD feature and 
leaving the modified drivers box unchecked. I then updated the drivers
after the install was complete (after restart).

Just so you know, I'm still new at this so there's probably a better explanation.

Cheers

CE

Thanks for the help. I've reinstalled it, left everything unchecked, and it's working fine now. I'm ready to "re-enable" it.

One question: when you updated your drivers to the new ones, did you do so through the Mythbuntu setup (like when you're installing it), or through Ubuntu's normal Restricted Driver Manager?

---

### Post by CrimsonEclipse on 2008-06-19
> **tonyr1988 said:**
> Thanks for the help. I've reinstalled it, left everything unchecked, and it's working fine now. I'm ready to "re-enable" it.

One question: when you updated your drivers to the new ones, did you do so through the Mythbuntu setup (like when you're installing it), or through Ubuntu's normal Restricted Driver Manager?

I updated after the installation. An updated drivers window popped up. 


CE

---

### Post by tonyr1988 on 2008-06-19
> **CrimsonEclipse said:**
> I updated after the installation. An updated drivers window popped up. 


CE

Was it the one that looked like this?

[http://www.michaellarabel.com/external/restricted-1.jpg](http://www.michaellarabel.com/external/restricted-1.jpg)

Or the one that looked the same as when you installed it?

Also, do you use S-Video, DVI, etc output or just normal VGA?

Thanks for the help, man.

---

### Post by CrimsonEclipse on 2008-06-19
That looks like it. 

Honestly, I'm just starting up so I haven't hooked up my TV
or cable yet. I'm still researching a capture card.

I'm still new to Linux over all. It's been a fun learning experience.

CE

---

### Post by tonyr1988 on 2008-06-19
> **CrimsonEclipse said:**
> That looks like it. 

Honestly, I'm just starting up so I haven't hooked up my TV
or cable yet. I'm still researching a capture card.

I'm still new to Linux over all. It's been a fun learning experience.

CE

Gotcha. I've done MythTV and Mythbuntu before, but never had this problem - something must have broken in the 8.04 release.

Thanks for your help - you've at least given me hope that only the installer was broken, and not the graphics card driver. :)

---

### Post by tonyr1988 on 2008-06-20
For future reference, I simply installed the proprietary drivers (through Ubuntu's Restricted Drivers Manager) and everything worked perfectly through my S-Video port. Absolutely nothing had to be configured. I was amazed, impressed, etc....

Mythbuntu 8.04 looks good.

---

