---
title: "Can't watch Rio DVD on VLC"
date: 2011-09-17
forum: Multimedia Software
---

### Post by getmeoutofhere on 2011-09-17
I bought a new, legitimate, boxed copy of the film Rio and I can't watch it on a computer.  I have tried different computers, one running Windows, the other Ubuntu 10.04.  I have tried VLC and other programs.  It just won't work.  But other DVDs do work.

However I can watch it on a dedicated DVD player, so I haven't bought a dud disk.  

Rio is a recent release.  Has something changed, in terms of encryption, that is preventing me from watching it?  Is there any way I can watch it?  Thanks.

---

### Post by mc4man on 2011-09-17
Haven't tried that title but it may use a structure protection scheme.
In some cases SP can confuse a player as to what/where is the actual movie title and or other such nonsense.

If your standalone can report the title # once the main movie starts then possibly try vlc either from cli based on this or in Media > Disc > no dvd menus & enter the correct title # there

```
vlc dvdsimple:///dev/[COLOR="Blue"]sr0[/COLOR]@[COLOR="Red"]X[/COLOR]
```\
Where X is the real main movie title #, also assumes the drive is /dev/sr0 (adjust blue if different

---

### Post by getmeoutofhere on 2011-09-17
Thanks, I'll give that a go.  As I said, it doesn't seem to be a specifically Ubuntu problem, as I couldn't get it to work on two different XP computers.  However I did get it to work, on XP, when I downloaded a trial version of PowerDVD.  It would seem that the paid-for software developers have kept ahead of the curve.  But I didn't want to buy this program, but I don't watch DVDs very often.

---

### Post by cowb0y on 2011-09-17
See this thread for a possible explanation (new copy protection scheme): [http://ubuntuforums.org/showthread.php?t=1844512]("http://ubuntuforums.org/showthread.php?t=1844512")

To clarify, the link relates to a new copy-protection "trick" affecting libdvdread (ex., Thor on DVD).

---

### Post by mc4man on 2011-09-17
I still  maintain a bit  of interest in Sp's post involvement so decided to take a look.
As far as a region 1 Rio, there is no Sp.scheme on the title (i see some read errors on the disk but may just be condition, not intentional. In any event it does playback in vlc, totem, totem-xine

So if you are R1 then there should be no playback issues. You could go ahead and try as previously posted. If still no go & want to there is some libdvdcss debugging that may prove informative
(am assuming libdvdcss2 is installed based on orig post

If in another region then there may be Sp, regions 2/4 can get 'special' treatment

---

