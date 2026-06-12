---
title: "VLC Sound Not Working"
date: 2008-05-09
forum: Multimedia Software
---

### Post by condawg on 2008-05-09
Well, I'm trying to watch a video file in VLC Media Player, but the sound does not work.
It works in FF, though.

And yes, sound is enabled in the settings, and the volume on it is up.

I downloaded several other media players to try them out, but the video won't even play in them.

VLC was working like, last week, though.

I'm guessing it's probably a codec issue, but can't seem to find the proper fix.
Any help appreciated.

---

### Post by wampagingwabbits on 2008-05-09
I'm having the same issue.  It was working fine in the 8.04 initial install - it must be a bug in one of the recent patches.  Sound does not work for me while playing a dvd from totem-xine, vlc, or mplayer - although just a few minutes ago sound worked for a while but playing in Italian instead of English (although set to english in the menu!)  When I switched the language it stopped working in any language.

Sound works fine in firefox, and presumably other applications.

---

### Post by sdowney717 on 2008-05-09
for VLC make sure it is set to alsa audio out ( advanced options checked)

are you running x11 video out or xV?
I found x11 works when xV shows a black screen, This occurs when running compiz

---

### Post by condawg on 2008-05-09
> **sdowney717 said:**
> for VLC make sure it is set to alsa audio out ( advanced options checked)

are you running x11 video out or xV?
I found x11 works when xV shows a black screen, This occurs when running compiz
Where's also audio out? Have Advanced checked, and can't find it.

And what is the other stuff?
Haha

Sounds helpful, but I don't know what that stuff is. :P

Thanks =]

EDIT: Kaayyy... It just started working out of nowwhere.
But the problem's not solved. Why did that happen?

---

### Post by sdowney717 on 2008-05-09
click settings - preferences 
click advanced settings

on left side
for audio 
click audio 
click output modules 
select alsa audio output

for video 
select video
select output modules
select x11 video output

---

### Post by condawg on 2008-05-09
Thanks =]

And what did that do?

If I have any more problems, I'll post again.

---

### Post by wampagingwabbits on 2008-05-10
I reckon this is some sort of localization/i18n bug.  Perhaps a non-existent language channel is being used by the media players?

---

### Post by mcowdery on 2009-04-07
Hey this really helped me. I tried several things I read from forums and they didn't work. Finally I just tried to figure it out myself through trial and error and voila! I figured it out. All I did was check the "use S/PDIF when available" box under the audio settings section of preferences. Simple, yet a lucky guess too.

---

### Post by Meow27 on 2009-04-09
ty for the info. this helps allot for me, as i had this problem with vlc in jaunty (compiled 9.9a)

btw now its see 'all options,' not 'advanced'  anymore

---

### Post by GorgothNZ on 2009-12-02
I have the same (or at least a very similar) problem. Running Karmic i386 on a nVidia chipset worked fine under jaunty before upgrade, and all the other apps function fine tried re-installs (of apps) and every combo of settings i could think of. any idea's would be great otherwise I'm gonna have to make a bootable USBdrive and reinstall and i don't really want to.

---

### Post by Peashooters on 2011-07-14
> **mcowdery said:**
> Hey this really helped me. I tried several things I read from forums and they didn't work. Finally I just tried to figure it out myself through trial and error and voila! I figured it out. All I did was check the "use S/PDIF when available" box under the audio settings section of preferences. Simple, yet a lucky guess too.


This worked for me.  I had this same problem when I upgraded alsa to 10.23.?? or whatever it was.  Thanks!

---

