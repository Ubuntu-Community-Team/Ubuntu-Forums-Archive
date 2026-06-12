---
title: "Gconf-editor - This key is not writable!"
date: 2011-02-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-02-04
I am in alpha2 desktop running unity 2D with the experimental 3D driver.
I am having desktop issues, ie anything saved to my desktop doesn't appear on it!
I suspected that nautilus was not drawing my desktop any more (not that I'm sure it should be any more!). So I opened gconf-editor and travelled to the /apps/nautilus/preferences/show_desktop key and indeed the box is unchecked. Aha! I thought, I'll just check that box (like I've dine before), but no :-(  I get the above error.  Oh dear, maybe that isn't the answer then. 
Does anybody know why I get the error? Or whether nautilus doesn't draw my desktop any more? Please see full error below. Thanks :-)

---

### Post by ronacc on 2011-02-04
did you invoke gconf-editor as a normal user ? mabye that key needs root .

---

### Post by Quackers on 2011-02-04
I'll be back :-)  Didn't need root before as far as I remember.

---

### Post by Quackers on 2011-02-04
Oh dear, as root the show_desktop key is ticked! What's happening?

---

### Post by coffeecat on 2011-02-04
I'm fairly sure it's not a good idea to run gconf-editor as root, but I'm happy to be contradicted. Personal settings in ~ shouldn't need root privileges.

I wonder if it's to do with 2D Unity and/or the experimental driver. I'm running a fully updated (as of an hour or so ago) 3D Unity with the Intel video driver and I can uncheck and check that gconf option - see screenshot. It would be interesting to see what people running 2D Unity are getting.

**EDIT**: just seen your root screenshot. Have I just been contradicted? :? :-k

---

### Post by Quackers on 2011-02-04
Lol, I don't know :-)
I'm wondering whether something has not gone well with the re-install of alpha2. I kept the first version of /home and I think I will re-install over-writing it and starting again and see what happens.
I'm at a loss to explain why the root version shows show_desktop as ticked, but the normal user version shows it as unticked, and un tickable! Maybe a user problem? Dunno.
And why is Nautilus not drawing my current desktop?  And what program is drawing it now?  My head hurts.

---

### Post by coffeecat on 2011-02-04
This is why I never bother with a separate home. If something gets mucked up, it can take an age to track down and it takes me less than half an hour to configure a fresh install the way I like it. Whatever, I think a penny may have dropped, at least about rooty stuff....

> **Quackers said:**
> I'm at a loss to explain why the root version shows show_desktop as ticked, but the normal user version shows it as unticked, and un tickable! Maybe a user problem? Dunno.

Running gconf-editor as root will configure root's desktop. That's why you shouldn't run gconf-editor as root and why the ticked root version is not fixing  your ordinary user desktop.

Not that this helps you with the untickable box in a non-root gconf-editor. :(

---

### Post by Quackers on 2011-02-04
Yes I see that. My problem is, as you say, what's wrong with my user desktop, and what's drawing that desktop at the moment? gdm?
I also have some doubts about a spearate /home parition to be honest. It's not all it's cracked up to be imo. It can cause problems too, particularly when upgrading. Anyway, I digress :-)  I'll re-install with everything bog standard and see what happens. Thanks for the input people :-)

---

### Post by cariboo on 2011-02-04
I did a fresh install on my home system this past weekend, with a separate /home the first time I booted nothing worked properly, after removing all the gnome configuration files and directories, and rebooting, everything is working the way it should so far.

**Note:** I haven't updated any packages that start with X :)

---

### Post by Quackers on 2011-02-04
> **cariboo907 said:**
> I did a fresh install on my home system this past weekend, with a separate /home the first time I booted nothing worked properly, after removing all the gnome configuration files and directories, and rebooting, everything is working the way it should so far.

**Note:** I haven't updated any packages that start with X :)

Lol, a wise move, no doubt :-)
I've just re-installed alpha2 with no separate /home and......... still no right-click and Nautilus doesn't seem to be drawing the desktop, although gconf-editor says it is :-(

---

### Post by Quackers on 2011-02-04
An update
I ran all available updates and rebooted. Now Nautilus is definitely drawing my desktop and I can right-click again :-) That's good :-)
Conky is up and rolling. Cairo dock next - maybe.

---

### Post by coffeecat on 2011-02-04
> **Quackers said:**
> I ran all available updates and rebooted. Now Nautilus is definitely drawing my desktop and I can right-click again :-)

1 - Insoluble problem that makes no sense at all.
2 - Run updates and reboot.
3 - Insoluble problem that makes no sense at all now fixed.

Yup. We're still definitely in alpha. :p

---

### Post by Quackers on 2011-02-04
Lol, even cairo dock works - but the animations are really slooooooooooow  :-)

---

