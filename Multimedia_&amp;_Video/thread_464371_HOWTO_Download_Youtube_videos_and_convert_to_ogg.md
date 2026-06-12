---
title: "HOWTO: Download Youtube videos and convert to ogg"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by minimoose on 2007-06-04
This is a simple way to convert Youtube videos from flv format to ogg format using Firefox and ffmpeg2theora. This also should work with other video websites (I have tried Google Video and Dailymotion and they work).

[LIST=1]
[*] Install ffmpeg2theora. This will convert the video from flv format to ogg.

```
sudo apt-get install ffmpeg2theora
```

[*] Retrieve the video file from /tmp and place it somewhere in your home directory once the video file is completely downloaded. Firefox conveniently stores Youtube videos in /tmp as long as the cache is turned on. The video file is named "Flash" followed by six letters and/or numbers.

[*]Convert the video file to ogg.

```
ffmpeg2theora (Filename of the video)
```

Type "ffmpeg2theora --help" for more options.
[/LIST]

This would probably be most helpful to those who don't have Flash. If anyone knows of a different way of retrieving Youtube videos, please help out.

---

### Post by blackened on 2007-06-04
> **minimoose said:**
> ...If anyone knows of a different way of retrieving Youtube videos, please help out.

Firefox+Greasemonkey+one of the video downloader scripts from userscripts.org (do a search for video or youtube, there are alot of em).

---

### Post by darwin81 on 2007-06-06
Also there is command line app in the repos called youtube-dl. All you have to know is the URL of the video on youtube. So you just go to the command line and type "youtube-dl url-of-video" without the quotation marks and it automatically fetches the video in flv format.

---

