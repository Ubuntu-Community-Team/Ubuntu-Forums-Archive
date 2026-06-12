---
title: "No xmltv grabbers available in brand new Mythbuntu 10.10 backend install"
date: 2010-12-27
forum: Mythbuntu
---

### Post by hallew on 2010-12-27
Hello,

I have a new Mythbuntu 10.10 backend running on an Zotac ION ITX-F box, and when I go to MythTV Backend Setup->Video Source Setup->My video source->Listings Grabber, I see the following options:

North America etc
Transmitted Guide Only etc
No Grabber
Loading...

After 10 seconds or so, Loading... just disappears.  At no point are any xmltv grabbers offered. This happens no matter how many times I restart the backend setup or the box, or cycle through the grabbers menu with the arrows, or how long I wait at the Listings Grabber menu for xmltv grabbers to appear.

It is possible for me to exit backend setup and run tv_grab_uk_rt --configure successfully, so the issue isn't whether xmltv or the grabbers are installed, but something about mythtv being able to see them.  Grateful for any assistance here, since I can't use the box at all until this is working.

Thanks!

---

### Post by ian dobson on 2010-12-27
Hi,

Sounds as if the search for xmltv grabbers is timing out. Maybe try opening the menu several times, if your lucky Linux will cache enough information so by the third/fouth attempt it'll get all the information.

Regards
Ian Dobson

---

### Post by hallew on 2010-12-27
You're right, that was the issue.  Multiple opens/reopens didn't help, but removing all the unused grabbers helped.

---

### Post by ian dobson on 2010-12-27
Hi,

Good to see the problem is solved. Maybe they should increase the timeout abit.

Regards
Ian Dobson

---

