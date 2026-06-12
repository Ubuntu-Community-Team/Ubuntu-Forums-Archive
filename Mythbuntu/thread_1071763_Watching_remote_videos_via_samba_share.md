---
title: "Watching remote videos via samba share?"
date: 2009-02-16
forum: Mythbuntu
---

### Post by BassKozz on 2009-02-16
I setup a READ-ONLY samba share on my NAS box to share videos on my MythTV box, I went into my frontend and added the path to "Utilities/Setup>Setup>Media Settings>Videos Settings>General Settings>Directories that hold videos:" to
/var/lib/mythtv/videos/ : /media/share/
Then I go back to the frontend's main menu and "Media Library>Watch Videos" still shows "No Videos" :(

What am I doing wrong here?

p.s. This share has multiple directories that contain video's (i.e. Movies, TV, Documentaries, etc...)
I have no trouble playing the videos by navigating to them and opening them up in nautilus.
p.p.s. Nothing is showing up in "Utilities/Setup>Video Manager" either :(

---

### Post by BassKozz on 2009-02-16
Figured it out thanks to foxbuntu on IRC...
There was a space between the colon, so:
```
/var/lib/mythtv/videos/ : /media/share/
```
doesn't work, but
```
/var/lib/mythtv/videos/:/media/share/
```
does work :D

---

