---
title: "Problems Playing Video Files."
date: 2011-05-01
forum: Multimedia Software
---

### Post by cynicalcylon on 2011-05-01
I am having problems viewing video files in all the players I have tried (Movie Player, Banshee & VLC).

In Movie Player & Banshee the video plays like it is being fast-forwarded through the whole file.
In VLC, the sound plays jerkily, sometimes completely without sound.

It just started today, after an update in 10.10 (don't think I did anything, but I'm really not sure :( )
I have just upgraded to 11.04, but the problem is exactly the same.

Any help would be appreciated.

I don't want to have to do a completely clean OS install, but that's the way it's looking :confused:

---

### Post by cynicalcylon on 2011-05-01
Tried a clean install of 10.10 (had the disc right there, so was easy enough ;)
Did nothing different from every other time I've done a clean install, but the problem was still there.

Am wondering if it may be a missing/superflous codec or driver problem, or are my sound or video cards giving up the ghost?

---

### Post by inobe on 2011-05-01
tell us about the formats you are trying to play.

---

### Post by cynicalcylon on 2011-05-01
Mostly .avi  & a couple of .flv files

---

### Post by inobe on 2011-05-01
ubuntu-restricted-extras may fix some problems, you can get it in software center, during the install you will have to agree to a license for one or more things.

---

### Post by cynicalcylon on 2011-05-01
Ouch! That was painful. When I tried to play a .avi file the sound went all squeaky & I got the following errors:

[IMG]http://i936.photobucket.com/albums/ad206/cynicalcylon/Misc/Screenshot2.jpg[/IMG]


Also my speakers seem to randomly give off the same squeaky, screechy sound even when not trying to view anything.

---

### Post by inobe on 2011-05-01
looks like you have a bug, search google for that error.

---

### Post by cynicalcylon on 2011-05-01
It seems to be this bug here - [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/644644](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/644644)

However, I've had a read through, and I don't think I'm nearly proficient enough to be able to spot a fix.
Oh dear :(

---

### Post by inobe on 2011-05-01
you can start here for adding a ppa or source [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20PPAs)

i believe the ppa is

**ppa:diwic/fighting-rewinds**

which was listed at the bug site.

listed in google too

[http://www.google.com/search?client=ubuntu&channel=fs&q=pa_stream_cork+ppa+bug+fix&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=pa_stream_cork+ppa+bug+fix&ie=utf-8&oe=utf-8)

---

### Post by cynicalcylon on 2011-05-01
Have tried both PulseAudio fixes & Alsa fixes, but I'm still getting intermittant jerky picture & sound.

---

### Post by trehanabhinav on 2011-05-02
if anyhting doesn't work, reinstall the media player you are using or switch to a new one

---

### Post by cynicalcylon on 2011-05-02
I've already reinstalled the players I had & downloaded a few more I'd never heard of before today.
VLC & Movie Player are still jumpy & static-y & the rest just don't work at all :(

---

### Post by cynicalcylon on 2011-05-07
Has this same bug been fixed in 11.04 yet?
If so, it may be time to upgrade...

---

