---
title: "[SOLVED] High CPU/lock up when viewing video list"
date: 2008-06-13
forum: Mythbuntu
---

### Post by moodog on 2008-06-13
I have 8.04 installed, and I've found that when going to watch videos, and Myth tries to display the video list, the application basically locks up. Checking top, the mythfrontend.real process is maxing CPU. I eventually left it for long enough, and the list was then displayed and I could play a video. I read somewhere that this could be caused by files in the video folder having wrong permissions. I've tried setting all of the permissions on files in the video folder to 777, but the problem still persists.

---

### Post by moodog on 2008-06-18
Anyone else experiencing this problem? It is still causing issues - I basically have to hit enter on the video list menu item and wait about 30 seconds before I can then do anything.

I may try apt-get purging mythvideo and then reinstalling tonight.

---

### Post by moodog on 2008-06-19
ok - my bad... and unfortunately it was a bit silly. It appears that I had a symlink from /var/lib/mythtv to my data directory (lvm), and then within the videos directory i had another symlink to itself... no wonder there was a bit of CPU usage. all fixed now. go back to what you were doing...

---

