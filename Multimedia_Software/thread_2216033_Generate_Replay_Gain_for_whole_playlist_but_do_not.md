---
title: "Generate Replay Gain for whole playlist but do not touch mp3 files themselves"
date: 2014-04-09
forum: Multimedia Software
---

### Post by deneb2014 on 2014-04-09
Hi folks,

I am looking for an audio player under ubuntu that can do this (like foobar already can do):
Generate the replay gains for all mp3 files in a playlist, but DO NOT write the replay gains in the ID3 tags of the mp3 files. In other words: Don't touch the mp3 files! Keep their original checksums (e.g. sfv)! If the generated replay gain information gets lost after closing the audio player it will be okay.

I know running foobar under wine would be a solution, but i like a native linux audiplayer with this capabilities better.

thanks for your response
kind regards

---

### Post by andrew.46 on 2015-03-28
I believe that foobar uses meta tags for the replaygain information and linux applications such as mp3gain will do the same.

**Edit**: Hmmm... perhaps I am talking rubbish here: he tag information is to allow undo of mp3gain's work which sounds more like normalising than use of replaygain..... Waiting for somebody who knows what they are talking about now :).

[https://www.mairlist.com/forum/index.php/topic,5508.msg39630.html?PHPSESSID=c0s5mu42fodmp8n8hlbkola9n6#msg39630](https://www.mairlist.com/forum/index.php/topic,5508.msg39630.html?PHPSESSID=c0s5mu42fodmp8n8hlbkola9n6#msg39630)

---

