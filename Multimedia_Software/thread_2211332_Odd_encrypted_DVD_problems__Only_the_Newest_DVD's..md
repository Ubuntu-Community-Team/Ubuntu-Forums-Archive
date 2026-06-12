---
title: "Odd encrypted DVD problems  Only the Newest DVD's. (99title issue maybe?)"
date: 2014-03-15
forum: Multimedia Software
---

### Post by Sxynerd on 2014-03-15
13.10 64bit  3.11.0-18.32-gen 3.11.10.4


I'm backing up my DVD's and I've discovered a problem with only the newest DVD's.  I've gotten past the 99 title DVD encryption on all of them except one.  Iron Man 3

Searching is a problem because it comes up with darn near a googleplex of the very basic, "How to play encrypted DVD's" and I guess my Google-fu is weak because I can't filter it any more.

the Symptoms.
Xine: wont respond at all
Totem Videos: immediately opens for a split second then closes.
VLC: just ignores me.  If I open from VLC, it closes.

$ vlc dvdsimple:///dev/sr0 :  Will play the video but will not time the movie correctly.

DVDrip won't even read the directory and outputs the error:  
> Job 'Read TOC (lsdvd)' failed with error message:
Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive.
Ubuntu crashes says: "[SIZE=3]*my libdvdnav4 is obsolete"*[/SIZE] but near as I can tell, it's the latest version for Saucy.  (libdvdnav4 4.2.0+20130225-3)

Handbrake will find and pick a title (3) but freezes so bad, I have to xkill.


thanks,
Nerd

---

### Post by Sxynerd on 2014-03-16
Anyone?

---

### Post by mc4man on 2014-03-17
vlc should be fine with it, actual movie is title 46 (region 1
if need be from terminal
vlc dvd:///dev/sr0#46:1
or
vlc dvdsimple:///dev/sr0#46:1

---

### Post by Sxynerd on 2014-03-20
Is there any way to get the apps to play the videos on their own instead of crashing?

Thanks for the reply.

---

### Post by Sxynerd on 2014-03-27
Anyone?

---

