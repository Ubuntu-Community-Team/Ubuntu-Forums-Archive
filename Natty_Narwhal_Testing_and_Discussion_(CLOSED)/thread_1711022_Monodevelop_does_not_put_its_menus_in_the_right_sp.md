---
title: "Monodevelop does not put its menus in the right spot"
date: 2011-03-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by patrickaupperle on 2011-03-20
Every application except Monodevelop and VLC that I have tested on my install of Natty has put their menus (such as file, edit, view...) on the bar across the top of the screen like a mac. I am guessing VLC does not because it is Qt. I have not tested any other Qt applications so I can not be sure. I was guessing it was occurring with monodevelop because it is GTK#, but other GTK# applications work just fine.

(In case anyone was wondering, I added docky to the system myself because I thought it would complete the Mac-like feel I was getting from the system.)

---

### Post by mc4man on 2011-03-20
As far as vlc - the use of the panel appmenu (I only use unity login) disappeared for a bit - should be back now
Personally don't like media players using 'global' menu, always switch them back to the player on an individual basis.

Have a brand new install here on a laptop, installed vlc and a few libs that aren't inc. by default
screen shows vlc using the panel menu
(did add vlc to the  unity systray which I do like

The  lib I marked for install was appmenu-qt

Edit: after installing appmenu-qt + deps you'll likely need to logout/in

---

### Post by patrickaupperle on 2011-03-20
> **mc4man said:**
> As far as vlc - the use of the panel appmenu (I only use unity login) disappeared for a bit - should be back now
Personally don't like media players using 'global' menu, always switch them back to the player on an individual basis.

Have a brand new install here on a laptop, installed vlc and a few libs that aren't inc. by default
screen shows vlc using the panel menu
(did add vlc to the  unity systray which I do like

The  lib I marked for install was appmenu-qt

Edit: after installing appmenu-qt + deps you'll likely need to logout/in

Thank you. That worked. Now I just have to figure out Monodevelop,

---

### Post by cariboo on 2011-03-20
You could submit a bug about the lack of global menu.

---

### Post by patrickaupperle on 2011-03-20
> **cariboo907 said:**
> You could submit a bug about the lack of global menu.

Who would I submit this bug to? The GTK# application I wrote automatically used the global menu. This would suggest to me that Monodevelop would not have to do anything for it to work. This would suggest that it is a global menu bug. The problem with that theory is that global menu works fine with everything else. Almost suggesting that monodevelop purposefully doesn't use it. This also seems an implausible explanation. By the end of that train of semi-logic I get confused as to where to send the bug. So, where do you advise the bug be sent?

---

### Post by mc4man on 2011-03-20
The  Monodevelop used in natty was built in Sept. for maverick. Of some interest to explore would be the last changelog entry

> monodevelop (2.4+dfsg-3ubuntu2) maverick; urgency=low

  * debian/patches/no_appmenu:
    - no appmenu for monodevelop (thanks bratsche) (LP: #606470)

 -- Didier Roche <didrocks@ubuntu.com>  Thu, 30 Sep 2010 17:39:26 +0200

Maybe ck. out launchpad bug #606470 to see what's up

If you're using the natty repo version then
```
ubuntu-bug monodevelop
```
If there isn't a current bug on this then file one or comment in the above mentioned one

Edit: the patch is pretty simple, verbose and _true_ - 
> +# Monodevelop menus don't work with Ubuntu appmenu
+export UBUNTU_MENUPROXY=0
Without the export Monodevelop  will end up with no menus at all

---

### Post by patrickaupperle on 2011-03-30
> **mc4man said:**
> The  Monodevelop used in natty was built in Sept. for maverick. Of some interest to explore would be the last changelog entry



Maybe ck. out launchpad bug #606470 to see what's up

If you're using the natty repo version then
```
ubuntu-bug monodevelop
```
If there isn't a current bug on this then file one or comment in the above mentioned one

Edit: the patch is pretty simple, verbose and _true_ - 

Without the export Monodevelop  will end up with no menus at all

Interesting. Guess they already know about it, then. The question is why doesn't it work right.

---

### Post by cariboo on 2011-03-30
> **patrickaupperle said:**
> Interesting. Guess they already know about it, then. The question is why doesn't it work right.

If you're interested, this is the bug, #[lpbug]606470[/lpbug], it's on the wishlist, but it looks like if no-one steps up to do something about it, it'll stay the way it is.

---

