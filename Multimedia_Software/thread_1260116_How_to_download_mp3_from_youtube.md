---
title: "How to download mp3 from youtube"
date: 2009-09-07
forum: Multimedia Software
---

### Post by bagy on 2009-09-07
1. Open terminal and install ffmpeg   sudo apt-get intsall ffmpeg
2. Install Download Helper add-on for mozilla.

---

### Post by BadBoy4Live on 2009-09-07
I think it would we a lot easier with the site [http://www.listentoyoutube.com/](http://www.listentoyoutube.com/).

You only have to insert your youtube link and it will extract the audio for you

---

### Post by SuperSonic4 on 2009-09-07
1. ```
sudo apt-get install ffmpeg
```
2. As above

3. Select the video to download and choose a place to save it to (~/dwhelper in my case)

4. Use ffmpeg to convert the video (one line at a time):

```
cd ~/dwhelper
ffmpeg -i input.flv -vn -ac 2 -ab 96k -acodec libmp3lame output.mp3
```

[list]
[*]-vn = Do not encode video
[*]-ac <num> = number of audio channels (1=mono, 2=stereo)
[*]-ab <num>k = audio quality in kbps
[*]-acodec = audio codec, libmp3lame for mp3, libvorbis for ogg, libfaac for m4a
[/list]

---

