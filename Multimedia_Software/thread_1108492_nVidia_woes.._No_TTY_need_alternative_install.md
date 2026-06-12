---
title: "nVidia woes.. No TTY need alternative install"
date: 2009-03-27
forum: Multimedia Software
---

### Post by VastOne on 2009-03-27
Everything nVidia X suddenly quit (Avant, Emerald, Compiz) so I decided to upgrade or reinstall the nVidia driver per advice from nVidia...

Only to find out for whatever reason I no longer have any TTY capabilities....Ctrl-ALT-F1-7 are dead in the water...

Is there another method to installing nVidia drivers?

Need assistance or a complete reinstall is in order....And I do not want to go there

THis is bizarre....No apparent changes to X or anything new and suddenly my puter is acting almost viral

---

### Post by lensman3 on 2009-03-27
Can you get to a text terminal?

1) Reboot and on the grub screen you need to edit the bootup lines.  The first line will look something like:

	kernel /vmlinuz-2.6.27.19xxxxxxxxxxxxxxxxx.  

At the end of the line add the word "single" without the quotes.  You can delete the words quiet and rbxx.

2) This should boot to single runlevel.  Single means a single user system.  After entering the super-user password a very DOS looking screen comes up.  The last line has "try to fix x windows".  Try that to see if it fixes anything.

---

### Post by VastOne on 2009-03-27
> **lensman3 said:**
> Can you get to a text terminal?

1) Reboot and on the grub screen you need to edit the bootup lines.  The first line will look something like:

	kernel /vmlinuz-2.6.27.19xxxxxxxxxxxxxxxxx.  

At the end of the line add the word "single" without the quotes.  You can delete the words quiet and rbxx.

2) This should boot to single runlevel.  Single means a single user system.  After entering the super-user password a very DOS looking screen comes up.  The last line has "try to fix x windows".  Try that to see if it fixes anything.

I figured it out...Never before seen or obviously used on my keyboard is an F Lock key that one of my cats MUST have stepped on :P ....

I can now TTY

Thank you!

---

### Post by VastOne on 2009-03-27
> **VastOne said:**
> I figured it out...Never before seen or obviously used on my keyboard is an F Lock key that one of my cats MUST have stepped on :P ....

I can now TTY

Thank you!

Is the solved button back?

---

