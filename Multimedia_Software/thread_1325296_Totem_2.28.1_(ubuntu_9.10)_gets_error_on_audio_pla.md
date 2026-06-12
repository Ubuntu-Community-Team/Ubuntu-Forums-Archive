---
title: "Totem 2.28.1 (ubuntu 9.10) gets error on audio playback"
date: 2009-11-13
forum: Multimedia Software
---

### Post by kennedyjch on 2009-11-13
Installed 9.10 and noticed that when I use Totem to playback large audio (mp3s) from my NAS device (mounted with Samba i.e., smb://...) I get "An error occurred. Could not read from resource" after several minutes (e.g., 10 minutes or more). Please note that this only seems to occur when I playback large (> 25mb) mp3s. 

If I copy the file to local hard disk and playback, all goes well - same if files are on USB external disk. Further, if I mount the drive with nfs, seems to work without errors. No errors if I stream with Squeezebox over network with "player" on my Ubuntu box. Also, I never noticed this problem with 9.04 or earlier versions of Ubuntu.

I'm starting to get the impression that it could be a problem with Samba shares and the way the media player reads these files...

Any ideas of how to make it right?

---

### Post by kennedyjch on 2009-11-17
Reinstalled 9.10 fresh (I have a separate partition for /home and this is a Godsend). Believe it or not, the problem has gone away... So, my quick lessons are...

1) Fresh installs
2) Separate partition for /home
3) If no comments on posting, then maybe it is a site-specific problem...
:D

---

