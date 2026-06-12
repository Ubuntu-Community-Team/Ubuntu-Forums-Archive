---
title: "youtube videos"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by Balvinder25 on 2007-06-20
hi all,
          i use ubuntu these days and normally listen to online songs on youtube..but they are real drain of download ..like if i listen to a video of 8 mins it takes approx 12 mb download??now isnt it possioble for me to save those videos on the hdd and save them as normall videos..?

please guys help me on this..

balvinder:popcorn:

---

### Post by eggdeng on 2007-06-20
You can use the firefox video downloader extension [https://addons.mozilla.org/en-US/firefox/search?q=videodownloader&status=4]("https://addons.mozilla.org/en-US/firefox/search?q=videodownloader&status=4")
to grab video from youtube in .flv format. If you have Mplayer (MEncoder) on your system,you can google for a simple script to convert .flv to divX (.avi). If you have problems finding such, post again and I will attach one.

---

### Post by onero on 2007-06-20
I use the unplug firefox extension: [https://addons.mozilla.org/en-US/firefox/addon/2254](https://addons.mozilla.org/en-US/firefox/addon/2254)

There are a lot of video download extensions for firefox, but this is the one I like best :)

---

### Post by PinkBullets9 on 2007-06-22
I use the terminal command youtube-dl. You can install it with sudo apt-get install youtube-dl. I still don't know how to convert them with ffmpeg though.

---

### Post by Balvinder25 on 2007-06-22
hey thanx buddy...the plugin tht u gave worked great..i wish i had askked this question much earlier..
thanks all for ya concern.
balvinder

---

### Post by Balvinder25 on 2007-06-22
thanks all for the concern ,,,i have the problem sorted by the unplug feature in firefox.worked great.
thanks all:p

---

### Post by david_2001 on 2007-06-22
> **PinkBullets9 said:**
> I use the terminal command youtube-dl. You can install it with sudo apt-get install youtube-dl. I still don't know how to convert them with ffmpeg though.
Perhaps the following will get you started converting:
```
ffmpeg -i Some_YouTube_Video.flv -vcodec msmpeg4v2 -b 312k -mbd 2 Some_YouTube_Video.avi
```
The avi file will be more or less the same quality as the original, though it might be a little larger in size, and should be playable by more or less any player, including Windows Media Player.

---

