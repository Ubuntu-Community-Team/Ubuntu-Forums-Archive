---
title: "Scheduled recordings are recorded but don't show in recorded list"
date: 2009-04-29
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-04-29
Using Jaunty, fresh install from the release CD (not upgrade), updated to today.

Programs are recorded on schedule, Commercial detection job runs post-recording (auto transcoding not enabled), and the programs show up in "Previously Recorded." But, none appear in the recordings list and cannot be selected to be played.

FWIW, this box (master backend plus frontend) has the problem at boot time that the backend isn't started right, so I have to exit the front end, restart the back end from commandline, and restart the front end. Don't know if this impacts the recording vis-a-vis the backend and SQLDB. Trying to fix this and will post when done.

Anyway, recording programs isn't much use in this condition. Anyone else have this problem?

-- DJ

---

### Post by DrJohn999 on 2009-04-29
Added: just checked MythWeb, and all the recordings show up correctly there, so it's not likely a DB problem. I haven't had much success with streaming them from there (and they're not transcoded anyway), so I can't tell if the files themselves are OK.

---

### Post by SiHa on 2009-04-29
Could be the display filter? Press 'Menu' when in the watch recordings screen.

---

### Post by DrJohn999 on 2009-04-29
Thanks, SiHa, that was it! I don't understand how the filter got changed, but there you go.

-- DJ

---

