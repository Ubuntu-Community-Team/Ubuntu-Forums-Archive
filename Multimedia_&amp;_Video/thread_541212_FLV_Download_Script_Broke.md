---
title: "FLV Download Script Broke"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2007-09-02
I used to have a script 'ytr' that downloaded YouTube videos and converted to MP3 with simulated stereo. The script is now bombing out in the part where it looks for the FLV file. It appears that YouTube recently changed their download sequence, breaking my script. However, a site like [COLOR="Red"]**[Tech Crunch has a link]("http://www.techcrunch.com/get-youtube-movie/")**[/COLOR] that works in letting me download the FLV file. If anyone has this working, please let me know. I know it can be done -- in fact, given enough time I might figure it out, myself.

Here's the old script and perhaps you can recommend the fix:

```
#!/bin/bash
bu="http://youtube.com/get_video.php?"
mkdir -p ~/mp3
cd ~/mp3
read -p "YouTube url? " ur
read -p "Name? " nv
echo;echo;
wget ${ur} -O /tmp/y1
uf=${bu}`grep player2.swf /tmp/y1 | cut -d? -f2 | cut -d\" -f1`
wget "${uf}" -O /tmp/y.flv
ffmpeg -i /tmp/y.flv -f mp3 -vn -acodec copy "/tmp/${nv}.mp3"
ecasound -i "/tmp/${nv}.mp3" -etf:8 -o "${nv}.mp3"
echo;echo;
rm -f "/tmp/${nv}.mp3"
echo "File is saved in your home directory in the 'mp3' folder. Press Enter to exit."
read
```

---

### Post by Gremlinzzz on 2007-09-02
I use Firefox Add-on  Extension called DownloadHelper
Then i covert with DeVeDe
sudo apt-get install devede

---

### Post by Gremlinzzz on 2007-09-02
> **Gremlinzzz said:**
> I use Firefox Add-on  Extension called DownloadHelper
Then i covert with DeVeDe
sudo apt-get install devede

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)
:guitar:

---

### Post by SuperMike on 2007-09-02
I actually need this in a script so that I can update not just 'ytr', but:

yt2mp3
[http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/)

So, if anyone knows the trick with the wget's and grep's, it would be much appreciated.

---

### Post by SuperMike on 2007-09-04
Anybody? Nobody knows how to do the proper wget's, greps, and cuts to get this working from Bash? On the web, the last I heard is that this stopped working on Aug 20th or somewhere near then.

---

