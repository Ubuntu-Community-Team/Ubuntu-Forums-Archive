---
title: "How to convert or play a WMV on a  website?"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by rem on 2008-02-25
Hello,

I'm having a WMV video file, can you please advice how to convert that into a FLV in order to play over the internet (or any other solution)? Also, a great freeware streaming multimedia player recommendation would be greatly appreciated.

Thank you!

---

### Post by terry_gardener on 2008-02-25
you can always try avdemux 

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/) and the wiki [http://www.avidemux.org/admWiki/index.php?title=Main_Page](http://www.avidemux.org/admWiki/index.php?title=Main_Page)

---

### Post by rem on 2008-02-25
thanks, i'll give that a try!

---

### Post by rem on 2008-02-25
> you can always try avdemux

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/) and the wiki [http://www.avidemux.org/admWiki/inde...itle=Main_Page](http://www.avidemux.org/admWiki/inde...itle=Main_Page)

the image is really great but the sound isn't ... do you have some tricks to share regarding sound output?

thanks.

---

### Post by terry_gardener on 2008-02-25
i have always usedthe mp3 format and the sound ok. 

for more information about the sound checkout this site.

[http://www.avidemux.org/admWiki/index.php?title=Audio_encoders](http://www.avidemux.org/admWiki/index.php?title=Audio_encoders)

---

### Post by rem on 2008-02-25
yes, i used mp3 as well but sound is pretty messy. thanks!

---

### Post by msarro on 2008-02-25
If you're trying to watch a video, download automatix
[http://www.getautomatix.com/](http://www.getautomatix.com/)

One of the utilities it can install is mplayer, along with the mplayer firefox plugin. This will work great for both embedded audio and video. You could probobly install mplayer yourself but I'm not sure if that will install the plugin or not, automatix handles it all for you.

---

### Post by terry_gardener on 2008-02-25
you can always try winff, it is the frontend gui to ffmpeg. 

this is a good converter. 

give it a go. might meet your needs better.

---

### Post by rem on 2008-02-25
thanks, but i don't need automatix.. not trying to watch a video, just trying to handle my wmv file to play it on my site...

---

### Post by rem on 2008-02-25
> **terry_gardener said:**
> you can always try winff, it is the frontend gui to ffmpeg. 

this is a good converter. 

give it a go. might meet your needs better.

yes, i already tried it (searched the ubuntu forums and found about it) but the image is very small and there's no sound ... :(

---

### Post by terry_gardener on 2008-02-25
according to the avidemux wiki i posted eariler lame mp3 is the standard audio format to convert to as most players will accept it but for higher quality sound use the vorbis option. 

i normally use this software or winff to convert video's and had no problems. 

hope you find the right setting or converter that you are looking for. 

sorry i cant be any more help.

---

### Post by rem on 2008-02-25
thanks for the help, greatly appreciated!

---

### Post by ubuntu-freak on 2008-02-25
I recommend WinFF/FFmpeg also. Worked perfect for me. Check out part 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) for info and intructions.
 
Nathan

---

### Post by terry_gardener on 2008-02-26
the only other tip i can give with regard to avidemux is that when it asked to remap/rebuild vbr rate say yes or build or ok cant remember which one it says. 

then it will say the frame is out-of date do you want to rebuild click yes.

---

### Post by stooshbunutu on 2008-03-11
if you use html
```
<embed src="./vids/mymovie.wmv" autostart="false" />
```
and then the viewers browser will handle it and handle any plugins

Alternatively upload the wmv to youtube, let them convert the file and the take it back as a flv format using tool suchas DownloadHelper

---

