---
title: "Upgraded to 9.10 but Myth is STILL 0.21"
date: 2009-11-04
forum: Mythbuntu
---

### Post by dibuntux on 2009-11-04
After being into a little mess (see my post No more networking), I decided to upgrade to 9.10. My system was a 9.04 AMD64 with VDPAU extensions. I had some problems, but finally the upgrade went through - but even if everything is Karmic and myth is working as before, it is still 0.21!
I've tried the procedure for upgrading on the Mythbuntu page:
1) Install the Mythbuntu Repos package and select MythTV 0.22
2) Run "sudo apt-get update && sudo apt-get upgrade"
3) Start MythTV Frontend, you will be prompted to upgrade the database schema. 
Point 1 &2 seems to go well, on point 3 nothing happen; I am not prompted to anything, mythfrontend just start - 0.21 version.

What can I try, besides a fresh install? TIA

---

### Post by jyavenard on 2009-11-04
I assume you were running the avenard repo...

The 0.21 packages in the repo have a higher version number than the 0.22 shipping with ubuntu...

If you want to upgrade to 0.22 there are a few options.
If you want to continue using the avenard repo, activate the "testing" repository ; you will then be automatically updated to 0.22..
0.22 is still in "testing" because it hasn't been released officially.

The 2nd option, is uninstall all mythtv related packages ; disable the avenard repo, then re-install mythtv .

Note, if using the avenard repo you must do the following:

-Activate the avenard repo
-Update the nvidia drivers, and *only* the nvidia drivers
-Apply the changes
-Then update mythtv, mplayer etc...

If you update all at once, you will get error during the installation about libvdpau being present in both the libvdpau package and nvidia-185-libvdpau.

Note 2: none of the option I mentioned earlier will make you loose any data ; even if you uninstall mythtv, your settings and database are still there; safe

---

### Post by dibuntux on 2009-11-04
Wow, a reply from Mr.Avenard in person! Thank you for helping and expecially thank you very much for your magnificent work on VDPAU (BTW: I use it with an Optoma DLP at 720p and the result is fantastic).

"I assume you were running the avenard repo...": yes, of course.

"If you want to upgrade to 0.22 there are a few options.
If you want to continue using the avenard repo, activate the "testing" repository ; you will then be automatically updated to 0.22..": yes, this seems to be the preferred option - but how exactly do I activate the testing repository and trigger the update to 0.22? Something in the details is escaping me...

TIA

---

