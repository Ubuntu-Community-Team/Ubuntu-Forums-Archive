---
title: "Sound Problem in Firefox"
date: 2014-08-04
forum: Multimedia Software
---

### Post by er00ic on 2014-08-04
This issue seems to exist only for Firefox. For the most part I can't get sound to work for video files, but occasionally a video will have sound. For example, I can't get sound on any video on Youtube, but I can get sound for videos at The Onion. I'm at a loss as to what to do to correct the problem.

---

### Post by Vladlenin5000 on 2014-08-05
Is it only with Firefox or the same video also doesn't work in other browsers?

---

### Post by er00ic on 2014-08-05
The videos play with sound when I use Chromium.

---

### Post by Vladlenin5000 on 2014-08-05
If it works in Chromium (not Google Chrome) without you installing any additional/alternative flash then the problem is in your Firefox profile. Try backing up (or removing) the profile/config folder. It should be something inside /home/yourusername/.mozilla/firefox/.

---

### Post by er00ic on 2014-08-05
I went there and found a file called profiles.ini so I copied it to my desktop and deleted the original file. I restarted Firefox and it was with a fresh profile, none of my previous history or bookmarks were present. I went to youtube and clicked on the first video I saw to test sound and while the video played I heard nothing. To be certain that it was the same issue I checked a random video at the onion's webpage and sound worked for it. I deleted the new profile and moved profiles.ini back into the .mozilla/firefox folder so I am now back with my original profile.

---

