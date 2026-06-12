---
title: "Today's hoarkage"
date: 2010-12-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by psusi on 2010-12-18
Tested today's daily build and found some new breakage that was not there the day before yesterday.

1)  Right clicking the icons in the Unity bar to try and make one sticky makes the whole bar vanish instead of showing the semi transparent menu.  Clicking anywhere else brings it back.

2)  Pop up menus being shown behind the owning window.  When manually partitioning with ubiquity, clicking on the drop down lists of filesystems or devices to install grub to causes them to be shown BEHIND the ubiquity window.  In the case of the filesystem choices, it is tall enough that you can see the first few entries above the ubiquity window, but the rest is hidden by it.  The devices to install grub to list box is entirely hidden.  This also seems to affect the shutdown/logout menu.  Logging out and back in with the classic desktop instead of Unity sometimes seems to fix it ( and then you can switch back to Unity and be fine ).

3)  Alt tabbing frequently crashes compiz.

This one may have been here before:

4)  When you do switch to the classic desktop, all panel objects exit unexpectedly and need restarted.

---

### Post by MacUntu on 2010-12-18
> **psusi said:**
> Tested today's daily build and found some new breakage that was not there the day before yesterday.
At least 1 and 2 were there before the day before yesterday. :P Restarting compiz should fix it for the session.

---

### Post by mc4man on 2010-12-18
> 4) When you do switch to the classic desktop, all panel objects exit unexpectedly and need restarted.

Atm you should only see that when switching from Desktop login to Classic login. Subsequent logins to Classic (gnome-panel) should load cleanly as far as panel applets
No issues here with 3 (Desktop login), though again, atm, the unity interface can occasionally 'misbehave' in various ways

As far as 2 - it does seem to happen once and awhile (only twice here ever)
Here's the bug report (originally lead to compiz - 0ubuntu4 

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461)

---

### Post by psusi on 2010-12-19
> **MacUntu said:**
> At least 1 and 2 were there before the day before yesterday. :P Restarting compiz should fix it for the session.

They didn't happen the last time I tested the daily live cd, which was no more than 2 or 3 days earlier.

---

