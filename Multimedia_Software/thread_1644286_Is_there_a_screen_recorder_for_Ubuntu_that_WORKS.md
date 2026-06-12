---
title: "Is there a screen recorder for Ubuntu that WORKS?"
date: 2010-12-13
forum: Multimedia Software
---

### Post by pseudocube on 2010-12-13
gtk-recordMyDesktop outputs a .ogv format, which Youtube interprets as a completely green video. And Istanbul can't manage to not crash long enough to squeeze out a file at all.

Running 10.04 here.

---

### Post by pickarooney on 2010-12-13
If there is, I haven't found it. I get the same results with those programs.

---

### Post by rachniqueen on 2010-12-13
Have you tried Kazam?

[https://launchpad.net/kazam](https://launchpad.net/kazam)

---

### Post by amsterdamharu on 2010-12-13
First install ffmpeg and winff:
```
sudo apt-get install ffmpeg winff
```I assume you have the needed codecs, now press alt + F2 and type winff.
The green + button will add the file to convert. Choose "websites" under "convert to" and next to "device presets" choose "flash video for web use fullscreen/widescreen".

After clicking convert a new file will be created converted to flv (youtube uses that) and has an flv extention.

I don't know how to directly record your desktop to flv.

---

### Post by nothingspecial on 2010-12-13
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1440x900 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```

To record your desktop with sound
```

ffmpeg -i output.mkv -acodec libmp3lame -ab 128k -ac 2 -vcodec libxvid -qscale 8 -me_method full -mbd rd -flags +gmc+qpel+mv4 -trellis 1 -threads 0 output.avi
```

To convert it to avi. Youtube will encode the avi video itself when you upload it.

---

### Post by ron999 on 2010-12-13
There's a tutorial here:- [http://ubuntuforums.org/showthread.php?t=1392026]("http://ubuntuforums.org/showthread.php?t=1392026")

---

