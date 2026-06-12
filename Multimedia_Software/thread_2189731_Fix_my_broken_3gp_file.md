---
title: "Fix my broken 3gp file"
date: 2013-11-23
forum: Multimedia Software
---

### Post by byraldrinker on 2013-11-23
Hey guys, this is my first post on this forum, as i' m pretty noob with ubuntu.

Now, i got this issue: 

Today i was recording a 3gp file on my cyanogenmod samsung, when accidentaly i didnt press the right "done" button. The situation got pretty serious, and while searching i managed to find a way to recover this 3gp file using some window$ tools. There where 2 more files that i didnt manage to save accidentaly but about this, the third one, i got this problem: i didn't manage to "play" it. VLC manages to "read" the time length (1h 05m) of the file but cannot play it. (the other 2 files i recovered using this windows tool play properly on vlc)
So, now i got these two questions.

I think (if this is not true, just tell me so i will stop searching about this) that if i find a more powerful tool (thats the part where i trust linux) i'm going to recover the same file in a better, playable, state. I'm asking for some help on this

and of course, i'm asking for some MORE help on how am i supposed to repair this 3gp file and play, the whole of it, or even just a part. 

I am pretty desperate

Thanks in advance

---

### Post by byraldrinker on 2013-11-23
Sorry for my second post in a row on the same thread but these are my  ffmpeg -i file and avconv -i file , errors: 

chaos@chaos-SVF1521H1EW:/media/0EAC0D5BAC0D3EA9/Documents and Settings/user/Desktop/recovered$ ffmpeg -i \[000002\].3gp 
ffmpeg version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:08:00 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1a947a0] error reading header: -1094995529
[000002].3gp: Invalid data found when processing input

chaos@chaos-SVF1521H1EW:/media/0EAC0D5BAC0D3EA9/Documents and Settings/user/Desktop/recovered$ avconv -i \[000002\].3gp 
avconv version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:08:00 with gcc 4.6.3
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x20657a0] error reading header: -1094995529
[000002].3gp: Invalid data found when processing input

---

### Post by FakeOutdoorsman on 2013-11-23
Please provide a sample file.

---

### Post by byraldrinker on 2013-11-24
ok... how am i supposed to do this? sorry :oops:

---

### Post by byraldrinker on 2013-11-24
i did recover 2200 files using photorec, but i got no 3gp files here. i got a lot of .elf files though, that i dont know what kind of filetype this is...

---

