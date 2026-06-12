---
title: "swapped 2nd tuner card, now neither work (2 PVR-150)"
date: 2008-09-17
forum: Mythbuntu
---

### Post by aalh on 2008-09-17
I had a pvr-150 and a wintv tuner card in my dvr

I acquired a 2nd pvr-150 so I removed the tuner card and installed the new pvr-150

I deleted all cards and added 2 150's (video0 and 1)

Channels are detected during scan in setup

I select watch tv, and screen is blank for a couple seconds then I am back at the menu.

I look in mythfrontend.log and I see:
EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo

why is it looking for 1969????

is this why I dont get live tv?

---

### Post by aalh on 2008-09-18
NOTE
The bios is set to correct time
the desktop clock shows correct time
date returns correct time
mythfilldatabase retrieves correct data

but live tv tries to get listings from 1969??
am I reading the log correctly?

if so, is this the cause of my dilemma?

or is something else broken?

when I look in system info it says tuner 3 & 4 instead of tuner 1 & 2

how do I clear the setup data without erasing the recording database?

---

