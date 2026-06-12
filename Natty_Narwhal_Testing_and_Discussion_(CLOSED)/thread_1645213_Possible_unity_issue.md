---
title: "Possible unity issue"
date: 2010-12-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2010-12-14
I don't think I've seen this one on here so far. After installing I was politely informed that I am not using 3D acceleration and the system booted into Gnome. I enabled the graphics drivers and rebooted. The system then displayed the background and the spinning circle mouse cursor was displayed for eternity, the computer never finished logging in.

I can log in via safe graphics mode and have been performing daily updates, now it lets me log in but I have a blank background and no menus of any kind. If a USB stick is plugged in it shows up on the desktop and I have created launchers for firefox, update manager, terminal etc so my system is usable, sort of!

So does anyone have any theories and is there anything I can do to kick my laptop back onto the rails?

I'm running a HP TX1000 which is running an Nvidia card.

---

### Post by Quackers on 2010-12-14
I suspect there may be a few more compiz updates waiting for you in Synaptic

---

### Post by MacUntu on 2010-12-14
The spinning cursor thing is a Compiz crash: [https://bugs.launchpad.net/unity/+bug/685418](https://bugs.launchpad.net/unity/+bug/685418)

AFAIK this should be fixed this week.

---

### Post by mc4man on 2010-12-14
The crashing on login to unity thru Ubuntu Desktop Edition should have been fixed with the 2nd compiz update late yesterday. (logging in thru Classic first probably would  allow a one time subsequent login thru "Ubuntu.." prior to this update
> compiz (1:0.9.2.1+glibmainloop3-[COLOR="Blue"]0ubuntu2[/COLOR]) natty; urgency=low

  * debian/patches/000_workaround_gconfbackend_init_hang.patch:
    - workaround in delaying the plugin init as the gconf backend hangs when
      trying to contact/launch the gconf daemon. This only happens when you
      don't change your current profile, at session start.
  * debian/patches/060_move_checks_to_compiz.patch:
    - adapted regarding previous patch



---

### Post by MacUntu on 2010-12-14
Not exactly sure this is the same bug as the one I linked to only happens after a boot (not after every session start).

---

### Post by mc4man on 2010-12-14
What I saw yesterday between compiz updates was that logging in to unity thru Ubuntu Desktop caused unity to crash. If you then logged out and in thru the Classic login (whether to panel or unity interface), you could then login to unity thru the Ubuntu D. option once.

Though this could be something diff.

Atm, fully updated unity is working fine here thru the Ubuntu D. option.
unity (3.2.6-0ubuntu2, compiz 0ubuntu2

Did also notice that most compiz setting were unset from the 1st. update, (or possibly from restarting unity), though the compiz settings for a classic login were untouched

---

### Post by macroshaft on 2010-12-14
I have no idea what the Ubuntu D. option is!

I've always been told never to do a partial upgrade during testing so I guess I've just been too cautious about my updates this time round.

I'm running them now and we'll see what happens.

---

### Post by cariboo on 2010-12-14
> I have no idea what the Ubuntu D. option is!

Ubuntu Desktop?

---

### Post by mc4man on 2010-12-14
> Ubuntu Desktop?
Yeah, referring to the log in option "Ubuntu Desktop Edition" vs the login option "Classic...."

(never learned to type too well so..

---

### Post by macroshaft on 2010-12-14
> **mc4man said:**
> Yeah, referring to the log in option "Ubuntu Desktop Edition" vs the login option "Classic...."



I still have no idea what you are going on about!

I have applied all the updates and still have no UI at all.

---

### Post by mc4man on 2010-12-14
> I still have no idea what you are going on about!
At the login screen where you pick the user and enter a password - after highlighting your username look at the bottom of the screen, you'll see a dropdown with various login options

---

### Post by macroshaft on 2010-12-14
> **mc4man said:**
> At the login screen where you pick the user and enter a password - after highlighting your username look at the bottom of the screen, you'll see a dropdown with various login options

Mine is set to auto login so I have never seen this, but from the way they read the two options mean the same thing, desktop edition and classic.

---

### Post by macroshaft on 2010-12-14
> **mc4man said:**
> At the login screen where you pick the user and enter a password - after highlighting your username look at the bottom of the screen, you'll see a dropdown with various login options

Mine is set to auto login so I have never seen this. However you say the options are desktop edition or classic, aren't they the same thing?

---

### Post by cariboo on 2010-12-14
> **macroshaft said:**
> Mine is set to auto login so I have never seen this. However you say the options are desktop edition or classic, aren't they the same thing?

The Classic Desktop, is the classic gnome two panel desktop, while the Ubuntu Desktop uses Unity.

---

### Post by macroshaft on 2010-12-14
> **cariboo907 said:**
> The Classic Desktop, is the classic gnome two panel desktop, while the Ubuntu Desktop uses Unity.

Or doesn't use unity, in my case!

---

### Post by cariboo on 2010-12-14
You have to have the Unity plugin enabled. You'll have to install compizconfig-settings-manager in oder to enable it, and set autohide/intellihide.

---

### Post by macroshaft on 2010-12-14
> **cariboo907 said:**
> You have to have the Unity plugin enabled. You'll have to install compizconfig-settings-manager in oder to enable it, and set autohide/intellihide.

I thought it was supposed to be enabled by default. And you're saying if it's not I get the stripped down no menus version? I assume that's going to be fixed before the big day.

---

### Post by macroshaft on 2010-12-14
Aah! there we go! Thanks

---

### Post by rajeev1204 on 2010-12-14
> **macroshaft said:**
> I thought it was supposed to be enabled by default. And you're saying if it's not I get the stripped down no menus version? I assume that's going to be fixed before the big day.


Yes it is supposed to be enabled by default if you have 3d support.

  You dont need to enable unity from the compiz settings manager to enable it.And neither will that package (compiz settings manager) be installed as an official package.

If unity is not enabled at login,then its highly unlikely it can be enabled from the settings manager.Something is wrong or missing which prevents unity from starting .

I caught a brief glimpse of unity yesterday with some updates but its gone into hiding again.

The only way i can login to classic desktop is by deleting the .gnome2 and .gconf folders under home.

---

### Post by macroshaft on 2010-12-14
> **rajeev1204 said:**
> Yes it is supposed to be enabled by default if you have 3d support.

  You dont need to enable unity from the compiz settings manager to enable it.And neither will that package (compiz settings manager) be installed as an official package.

If unity is not enabled at login,then its highly unlikely it can be enabled from the settings manager.Something is wrong or missing which prevents unity from starting .


But the problem here is that many systems, like mine, must boot once without 3D support and have the 3D driver installed, then you are just left with a background and no menus. Either Unity needs to try to enable itself on every boot or it needs to revert back to the gnome desktop with an obvious option to try again when you have fixed the issues. As it works now it rendered my system unusable.

---

### Post by rajeev1204 on 2010-12-14
> **macroshaft said:**
> But the problem here is that many systems, like mine, must boot once without 3D support and have the 3D driver installed, then you are just left with a background and no menus. Either Unity needs to try to enable itself on every boot or it needs to revert back to the gnome desktop with an obvious option to try again when you have fixed the issues. As it works now it rendered my system unusable.


Well, that is how it works , if 3d is available unity is enabled at boot , else you install the drivers and later on next login you get the option.

But considering the alpha state of natty, things will keep changing .In fact if you update your system now, the visual effects tab also is missing now from appearances.

---

### Post by macroshaft on 2010-12-14
> **rajeev1204 said:**
> Well, that is how it works , if 3d is available unity is enabled at boot , else you install the drivers and later on next login you get the option.

But considering the alpha state of natty, things will keep changing .In fact if you update your system now, the visual effects tab also is missing now from appearances.

Of course I'm not going to get worried about any of this at such an early stage. Actually everything is running correctly now which is surprising, I usually find alpha versions near unusable.

---

