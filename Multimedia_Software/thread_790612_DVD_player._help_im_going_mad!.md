---
title: "DVD player. help im going mad!"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Fenris_rising on 2008-05-11
hi all
well ive been playing with different linux based OS's just for the hell of it on my laptop. now im back on xubuntu 7.04 (clean install), set up my wireless, realplayer easy peasy. but now i am at a complete loss as to playing commercial DVD's on it. i had had it playing them before my little sojourn with the other OS's and now i cant for the life of me get it going again. the first time i did it it took 30 mins to search and find the answers and implement them. now i cant find the simple straightforward method i used last time. i have the libdvdcss in my repo but it wont install because its giving me this message.

Depends: libc6 (>=2.6-1) but 2.5-0ubuntu14 is to be installed

this didnt happen last time. ive been up and down the interweb, added medibuntu as a repo. paled at the long winded methods here and there, down loaded this that and the other tried this that and the other all to no avail. i really had no problem the first time i tried it so i have no idea whats going on. at this point i have uninstalled all movie players and all the codecs associated with them for a clean start. can some genius please sort me out before i do something terminal to my laptop. a nice look here you idiot type direction would be appreciated.

---

### Post by 4Orbs on 2008-05-11
My 2 cents worth... I did a new install of xubuntu 8.04 and followed the Comprehensive Multimedia sticky thread at the top of this forum, and dvd playback works flawlessly. Vlc is now my default dvd player, mplayer handles the mkv video and gxine plays the avi video. Not sure, but I think the xine library made a difference in the ability to play dvd. I also enabled the restricted driver, but not until after I had all the multimedia stuff installed. So I suggest following the how-to sticky thread from top to bottom.

---

### Post by mc4man on 2008-05-11
Go to software sources and check under 3rd. party - it sounds like you're using the medibuntu repo for gutsy, you need the feisty one. Use the repo source from this page to add 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Fenris_rising on 2008-05-11
cheers everybody. got so far as directed then added all the xine bits and that clinched it. the crow (original and best) is playing perfectly. now i really should write all this down like i have for realplayer and my wireless card and dongle. thanks all much appreciated. please observe i have used the 'thanks' button now i know how to use it cheers all.

---

### Post by Cap'n Skyler on 2008-05-11
> **Fenris_rising said:**
> cheers everybody. got so far as directed then added all the xine bits and that clinched it. the crow (original and best) is playing perfectly. now i really should write all this down like i have for realplayer and my wireless card and dongle. thanks all much appreciated. please observe i have used the 'thanks' button now i know how to use it cheers all.
make sure to watch this thread :) then if you ever need to,come back here and 
log in and go to your user CP and read how to get back to where you were :P
scott

---

### Post by Fenris_rising on 2008-05-12
yus. already noted this time :lolflag::lolflag:

---

