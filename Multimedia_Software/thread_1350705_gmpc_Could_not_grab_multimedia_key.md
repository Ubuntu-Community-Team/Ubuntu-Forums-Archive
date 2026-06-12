---
title: "gmpc: Could not grab multimedia key"
date: 2009-12-09
forum: Multimedia Software
---

### Post by Tookelso on 2009-12-09
Hello,

I'm using GMPC as a front-end for mpd.

I'm running Ubuntu 9.10, and when I start gmpc,
I get the error:

Could not grab multimedia key:
PlayPause: XF86AudioPlay
Ensure that your window manager (or other applications)
have not already bound this key for some other function, then
restart gmpc.

I'm using the Microsoft Natural Ergonomic keyboard 4000,
and it has a "Play/Pause" button at the top.  I looked
under the "System -> Preferences -> Keyboard/Mouse" settings,
and the Keyboard model says "Microsoft Natural".

It appears that some other application has grabbed the XF86AudioPlay, and the gmpc is complaining about it.

Has anyone had this problem?  I can re-map the gmpc settings, but I'd like to know if there's a better fix for this problem --
maybe I could find the program that is stealing the XF86Play buttons?

Thanks,
--Nate

---

### Post by sirdiego on 2009-12-26
Hi, I have the same problem. Dont know what to do. With Sonata (other mpd client) the keys work.

---

### Post by qball on 2009-12-27
add the gmpc-mmkeys plugin and disable gmpc's bindings.. 

This will make gmpc use gnome's keybinding thingy.

---

### Post by sirdiego on 2010-01-12
> **qball said:**
> add the gmpc-mmkeys plugin and disable gmpc's bindings.. 

This will make gmpc use gnome's keybinding thingy.

thank you, that worked for me! =)

---

### Post by David Valentine on 2010-03-11
> **qball said:**
> add the gmpc-mmkeys plugin and disable gmpc's bindings.. 

How do I do these?

UPDATE:  OK, to disable gmpc's bindings,  edit ~/.gmpc/gmpc.cfg, navigate to the KEYBINDINGS section and change all keybindings to "0" (zero).  I still can't find the gmpc-mmkeys plugin, but perhaps it's somehow hidden in the raft of plugins I installed when I installed gmpc.  At any rate, I no longer get the startup error.

---

### Post by Elcid247 on 2010-03-18
> **David Valentine said:**
> How do I do these?

UPDATE:  OK, to disable gmpc's bindings,  edit ~/.gmpc/gmpc.cfg, navigate to the KEYBINDINGS section and change all keybindings to "0" (zero).  I still can't find the gmpc-mmkeys plugin, but perhaps it's somehow hidden in the raft of plugins I installed when I installed gmpc.  At any rate, I no longer get the startup error.


i already had it at 0s and i can't find the gmpc-mmkeys plugin, any help?

UPDATE: i found the package in this repo [https://launchpad.net/~gmpc-trunk/+archive/ppa](https://launchpad.net/~gmpc-trunk/+archive/ppa)

---

### Post by Vlado P. on 2011-05-23
No need to use an external PPA for this: gmpc-mmkeys is already in gmpc-plugins - at least in Ubuntu 11.04. I still get the error message on gmpc startup, but the XF86AudioPlay key now works!
(make sure the "Gnome multimedia keys plugin" is enabled by clicking "**plugins:**" in the gmpc preferences).

---

