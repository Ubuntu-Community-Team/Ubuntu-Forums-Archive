---
title: "HD Quicktime Over SMB Share Won't Play"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by Eddy5 on 2007-11-06
I'm having a very odd error in Gutsy.
I've got some HD quicktime movies which play fine when copied to my PC (IN both Totem and VLC< although VLC works properly and Totem plays them jerkily).
However when trying to play them off the Samba share they come up with the following error in Totem (VLC won't play them off a SMB share)

An error occurred
This file is incomplete and cannot be played.

I don't know why this is, as other files in the same folder (Like low res MOV files and WMVs) play fine from the same directory.
Any help would be much appreciated.

Just playing with it some more, it would seem to be an issue with files over around 65Mb.

---

### Post by Eddy5 on 2007-11-07
Further developments, if I mount the smb shares to a folder (/mnt/lan/smbfolder) then VLC will play them. However it plays them OK for around 30 seconds, then starts getting very very choppy, turning into a slideshow. Totem does the same, plays them for a bit then gets choppy.
These will all play fine to the PC when it was running Windows, so it's not the PC hardware or samba hardware.

---

