---
title: "How to record a streaming video using Ubuntu?"
date: 2015-06-11
forum: Multimedia Software
---

### Post by remmas-sido on 2015-06-11
Hello guys s
I want to know if there's a way to record a streaming video in Ubuntu? and if it makes a difference using Mozilla Firefox or Google Chrome? 
Thank you

---

### Post by ajgreeny on 2015-06-11
Recording from such as YouTube may be contrary to their T&Cs, so proceed with caution on this, but have a look at the extensions for both FF and chromium called **Video DownloadHelper** or something similar, which will work on some, but not all sites.
[URL="https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/?src=hp-dl-mostpopular"]https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/?src=hp-dl-mostpopular
[https://chrome.google.com/webstore/detail/fvd-video-downloader/gmngadifolibnaoikammfkfpfhoefadb?utm_source=chrome-app-launcher-info-dialog](https://chrome.google.com/webstore/detail/fvd-video-downloader/gmngadifolibnaoikammfkfpfhoefadb?utm_source=chrome-app-launcher-info-dialog)
[/URL]

---

### Post by shantiq on 2015-06-15
[[COLOR=#000000]remmas-sido[/COLOR]]("http://ubuntuforums.org/member.php?u=1959624") to actually copy as it is playing   in browser on your desktop   you can do this >>>



```
sudo apt-get install pavucontrol
```                    find pavucontrol in applications/sound and video

click on recording/click on box/[COLOR=#800000]pick monitor of internal audio   [/COLOR]

 *Nota Bene: [COLOR=Red]you will probably need to run[/COLOR]* the code below in your terminal once  **first** to bring up the options on pavucontrol 

**now we know sound will be included**

Then to run:

```
 ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x720 -i :0.0  -c:a  flac  -c:v  libx264  -threads 0 ./Desktop/mydesktop.mkv                      
```


1280x720    depends on what you wish for and size of your screen evidently
audio   can be ```
-c:a mp3 -b:a 128k
``` if you wish for smaller size file
     
 
   =================================
**DO NOT** forget to reset your pavucontrol at the end otherwise next time you try to do a microphone recording settings will be wrong
=================================

---

### Post by oldrocker99 on 2015-06-16
> **ajgreeny said:**
> Recording from such as YouTube may be contrary to their T&Cs, so proceed with caution on this, but have a look at the extensions for both FF and chromium called **Video DownloadHelper** or something similar, which will work on some, but not all sites.
[URL="https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/?src=hp-dl-mostpopular"]https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/?src=hp-dl-mostpopular
[https://chrome.google.com/webstore/detail/fvd-video-downloader/gmngadifolibnaoikammfkfpfhoefadb?utm_source=chrome-app-launcher-info-dialog](https://chrome.google.com/webstore/detail/fvd-video-downloader/gmngadifolibnaoikammfkfpfhoefadb?utm_source=chrome-app-launcher-info-dialog)
[/URL]

I use Video Download Helper (a plugin for Firefox) all the time, and it works perfectly well; I wholeheartedly recommend it; it works for You Tube and just about every other free streaming video source I've tried. I didn't have to run any commands nor install dependent software, either.

---

### Post by monkeybrain20122 on 2015-06-18
You can use youtube-dl. As said downloading from Youtube itself is a violation of their terms of use so not supported on this forum. But the application works on many other streaming sites where there is no such restriction. It is a command line tool but if you desire there is a third party gui callled youtubedl-gui. Both can be installed from webupd8's ppa.[https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)

---

