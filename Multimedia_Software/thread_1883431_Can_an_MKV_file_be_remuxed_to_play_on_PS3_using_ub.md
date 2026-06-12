---
title: "Can an MKV file be remuxed to play on PS3 using ubuntu?"
date: 2011-11-19
forum: Multimedia Software
---

### Post by Dáire Fagan on 2011-11-19
Hello

I have 10 .mkv videos I would like to *'remux' to a format that will work on the PS3 like MPEG-2, XviD , x264 etc - preferably whatever is the smallest and easiest to accomplish.

I was able to remux a single different .mkv file to 'vob' successfully (many of these terms are new to me) using the Windows program mkv2vob under Wine in Xubuntu - but it's giving out errors on the said 10 videos, and also causes them under Windows.

I have found some Windows software that will re-encode the files but it will take hours and hours - where as when mkv2vob actually works for me it does a 60 minute video in 2/3 minutes.

*I understand this to be because remuxing changes something about the video to make it work on PS3 without having to go through a full re-encode.

What's the best way to do this on linux? If there is one...

---

### Post by shantiq on 2011-11-19
you can use ffmpeg for that task


```
for f in *.mkv ; do ffmpeg -i "$f" -acodec copy -vcodec copy "${f%.mkv}.mpg"; done 
```


and if command line is not your thing there is easier software


like  **winff **   which is in your synaptic and uses ffmpeg   [ easy to choose settings]


```
sudo apt-get install winff
```

---

### Post by Dáire Fagan on 2011-11-20
Thanks!

---

