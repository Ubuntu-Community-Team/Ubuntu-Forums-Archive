---
title: "[SOLVED] AutoPlay on Hardy"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Sonthun on 2008-05-11
Did the Multimedia and Storage tabs under Systems -> Preference -> Removeable Drives and Media get moved somewhere else?  I went to disable autoplay for cd's and all that is there Camera, PDA's, Printers, and Input Devices.  How do we disable Autoplay now?

Thanks.

---

### Post by mc4man on 2008-05-11
Go to edit menus and add  file management (in preferences), you'll find those options under media tab

---

### Post by Sonthun on 2008-05-11
Thanks.  That did it.

---

### Post by flowtron on 2008-06-01
True - the method does bring up a menu to change the settings. Altough the description could've been a bit more elaborate ... especially for people running Ubuntu in non-english language ... it took a bit of poking around to finally figure out what/where to click :-P
Anyway .. even with this new GUI I still can't change it to use VLC .. only gxine and movie-player are available (or "do nothing"-et-al).

I'd really appreciate if someone could elaborate on a CLI way modify the settings - using the gconf-editor I couldn't find any occurrence of "gxine" after having set it to use that via the mentioned menu ... so ... where's that setting been hidden ?!?

---

### Post by mikeh on 2008-07-28
Well, I'm a native English speaker, but I still don't understand.

I have the multimedia tab, but no DVD choice.
I tried gconf-editor and find /desktop/gnome/volume_manager/autoplay_dvd
is disabled.
  Why does totem keep launching when a DVD is inserted?

---

### Post by jfenn2199 on 2009-08-30
If you or anyone else is still having a problem with Totem launching when a DVD is inserted but gconf is showing DVD autoplay as disabled install vlc (if not already) got under system->preferences->preferred applications and under multimedia select vlc as the default DVD player and that should take care of it

---

### Post by mikeh on 2009-08-30
It is two releases later now, and I still don't see a DVD option there. What am I missing? You see that in Jaunty?

BUT, I can use Nautilus->preferences->media-tab and select a DVD option there.

---

