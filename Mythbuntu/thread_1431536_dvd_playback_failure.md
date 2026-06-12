---
title: "dvd playback failure"
date: 2010-03-16
forum: Mythbuntu
---

### Post by itlarson on 2010-03-16
My new mythbuntu  install refuses to play dvd's.  This is true for both the frontend, and Vlc.  The command line utility dvdbackup also fails.  I have installed xubuntu-restricted-formats.  I also tried sudo apt-get install libdvdcss2 libdvdread4 libdvdlso failsnav4 vlc per the multimedia howto,  Everything was installed except libdvdcss2, which apt-get claims doesn't exist.  Yes multiverse is enabled.   Some internet sources recommend running something like "sudo /usr/share/doc/libdvdread4/install-css.sh". This is new to me- in the past just installing restricted-extras worked.   It fails with ERROR 404: Not Found.  

I should also mention there is no /dev/dvd.  The only optical drive in fstab is /dev/scd0.  

Here is mythfronted log output:
libdvdnav: Using dvdnav version svnR1169
libdvdnav: vm: failed to open/read the DVD
2010-03-16 16:42:17.109 Failed to open DVD device at /dev/dvd
2010-03-16 16:57:58.881 TV: Attempting to change from None to Watching DVD
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat /dev/dvd
No such file or directory

Here is dvdbackup output:
itl@mythbox:~$ dvdbackup -i /dev/scd0 -o ~/dvd -M
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
The DVD-Video title on the disk is DVD_VIDEO, which is too generic; please provide a title with the -n switch

I am currently getting no feedback from vlc- it just sits there.

Can anyone help?

---

### Post by tgm4883 on 2010-03-17
libdvdcss2 is in medibuntu. The correct way to install it is with "sudo /usr/share/doc/libdvdread4/install-css.sh", i'm not sure why that is giving you a 404 not found error. Can you run the command again and post the full output?

---

### Post by itlarson on 2010-03-17
Thanks for the reply.  I tried "sudo /usr/share/doc/libdvdread4/install-css.sh" again this morning and it worked this time.  I am wondering if it is possible the repository was down?  I am also curious as to why this library is no longer included in "xubuntu-restricted-extras"?

Anyway vlc will now play dvd's, but mythfrontend still refuses to.  I set the path in settings->media settings->archive but it still doesn't work.  I will further investigate this evening.

---

### Post by klc5555 on 2010-03-17
> **itlarson said:**
> Thanks for the reply.  I tried "sudo /usr/share/doc/libdvdread4/install-css.sh" again this morning and it worked this time.  I am wondering if it is possible the repository was down?  I am also curious as to why this library is no longer included in "xubuntu-restricted-extras"?

Anyway vlc will now play dvd's, but mythfrontend still refuses to.  I set the path in settings->media settings->archive but it still doesn't work.  I will further investigate this evening.

If myth can't find anything at /dev/dvd, it usually means it should be looking for /dev/sr0. (Or some other /dev/srX). Try changing the DVD read device in the frontend setup from /dev/dvd to /dev/sr0 and see whether myth finds it.

---

### Post by itlarson on 2010-03-19
Finaly I got back to this- 

 The frontend is still trying to use /dev/dvd according to the frontend log. The only place I have been able to find to change this is in the settings for "archive", and changing it there has no effect on playback evidently.   Vlc plays fine using /dev/sr0 but is not ideal for a livingroom setup.  Is there a way to get mythfrontend to use /dev/sr0?  Maybe I could create a link to sr0,  but I am not sure how to do this.

---

### Post by klc5555 on 2010-03-19
> **itlarson said:**
> Finaly I got back to this- 

 The frontend is still trying to use /dev/dvd according to the frontend log. The only place I have been able to find to change this is in the settings for "archive", and changing it there has no effect on playback evidently.   Vlc plays fine using /dev/sr0 but is not ideal for a livingroom setup.  Is there a way to get mythfrontend to use /dev/sr0?  Maybe I could create a link to sr0,  but I am not sure how to do this.

Frontend. Setup. General settings. p. 3 "Location of DVD device" Change from /dev/dvd to /dev/sr0. 

At least that's the location in 0.21. May have been moved to a different page in 0.22.

---

### Post by itlarson on 2010-03-19
I take it you mean (from the top menue) utilities/setup->setup->general->hit enter three times.  this gives me the pin setup page, not dvd path.  They must have changed this in .22.

---

### Post by itlarson on 2010-03-19
Got it!  several pages further there is a page I hadn't noticed before called "media monitor".  If you check "monitor cd/dvd" and "use new media" it works.  Why this isn't checked by default, I don't know.  Anyway, thanks for the help.

---

### Post by klc5555 on 2010-03-20
> **itlarson said:**
> Got it!  several pages further there is a page I hadn't noticed before called "media monitor".  If you check "monitor cd/dvd" and "use new media" it works.  Why this isn't checked by default, I don't know.  Anyway, thanks for the help.

Well, at least in 0.22 it fails to work by default in a new and original way.  I suppose that's progress of a sort over 0.21 ...

---

