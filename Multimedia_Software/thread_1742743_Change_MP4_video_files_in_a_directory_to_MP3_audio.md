---
title: "Change MP4 video files in a directory to MP3 audio files"
date: 2011-04-29
forum: Multimedia Software
---

### Post by Sarteck on 2011-04-29
What would be a nice, simple command to go through all files in a directory (no sub-directories), and change all the MP4 Video files I have to MP3 audio files (keeping the original filenames except for changing the "mp4" extension to "mp3")?

The files in question were videos taken with one of those Flip cameras, but I only need the audio off of it.

Thanks in advance!

---

### Post by prshah on 2011-04-29
> **Sarteck said:**
> nice, simple command to go through all files in a directory (no sub-directories), and change all the MP4 Video files I have to MP3 audio files (keeping the original filenames except for changing the "mp4" extension to "mp3")?

To start you off: ```
find Videos/ -iname *.mp4 -execdir ffmpeg -i "{}" -vn -acodec copy "{}".mp3 \;
``` You can also use a for loop, but in this case even subdirectories are processed.

Also, the audio filename will become *.mp4.mp3 ; maybe someone else can point out how to change the extension.

---

### Post by andrew.46 on 2011-04-30
What audio codec is contained within the original mp4 files?

---

### Post by shantiq on 2011-04-30
well if you are already in the folder you can use this


```
for f in *.mp4; do ffmpeg -i "$f" -ab 128k "${f%.mp4}.mp3"; done

```

and if you want to remove the mp4 for good

```
**for f in *.mp4; do ffmpeg -i "$f" -ab 128k "${f%.mp4}.mp3"; done && rm *.mp4**

```


[COLOR="DarkRed"]and of course change the kbps to match your original video's audio kbps
[/COLOR]

if you are not in the folder but want to do this to multiple folders enter them and do this operation you can use this


```
for i in */
do
cd "$i"
for f in *.mp4; do ffmpeg -i "$f" -ab 128k "${f%.mp4}.mp3"; done 
cd ..
done
```


you say you do not need the videos any longer so you can add this to line four

```
&& rm *.mp4
```    so you have

```
for i in */
do
cd "$i"
for f in *.mp4; do ffmpeg -i "$f" -ab 128k "${f%.mp4}.mp3"; done && rm *.mp4
cd ..
done
```

---

