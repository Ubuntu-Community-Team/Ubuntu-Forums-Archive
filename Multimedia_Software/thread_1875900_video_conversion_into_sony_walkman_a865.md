---
title: "video conversion into sony walkman a865"
date: 2011-11-05
forum: Multimedia Software
---

### Post by al.adab on 2011-11-05
As far as I know, the sony walkman a865 supports both wmv and mp4 video formats. When I bought it, the walkman came with some sample videos, all in .wmv format...

...whatever I do, the Sony won't play any video file I convert (for example) from .flv to .wmv (through VLC, WinFF, or Miro). I tried Blacklight3 though it doesn't seem to launch/work anyway.

is this a Linux/Sony compatibility issue? If it is, could you please help?

---

### Post by andrew.46 on 2011-11-06
> **al.adab said:**
> ...whatever I do, the Sony won't play any video file I convert (for example) from .flv to .wmv (through VLC, WinFF, or Miro).

Could you post one of the sample videos, this would give an idea of the type of file this device is happy with. Not so many details available online about video formats unfortunately. Perhaps a standard 'windows-compatible' file will play, syntax such as the following:

```

ffmpeg -i <infile> -vcodec wmv2 -b 512k \
        -acodec wmav2 -ab 128k -f asf \
         <outfile.asf>

```

might be enough?

---

### Post by al.adab on 2011-11-06
thank you Andrew.46

I'm trying (for instance) to save + run the video 
[http://www.youtube.com/watch?v=bZqFqFeA6UI](http://www.youtube.com/watch?v=bZqFqFeA6UI)
on the Sony. 

I'm using UnPlug (Firefox extension) to download it onto my HD. It gets saved as a .webm file. The whole name of the file is *Countdown Iran _ Israel War  part 1.webm*. It's saved in the folder Downloads (Xubuntu).

Sorry I'm completely lost as to using ffmpeg. I tried the syntax you suggested but it doesn't work...(ffmpeg is installed). Any chance you could give me a practical example with the file above? It'd finally help me make sense of the ffmpeg user guide...

thank you again!

---

### Post by al.adab on 2011-11-06
breakthrough: it works if I use Miro and I convert the .webm file into a Playstation Portable format...haven't tried converting .flv yet, though I suppose it'd work...

---

### Post by mamothh on 2013-03-08
If you want to play video on sony walkman a865 then you need to convert  it and for this you get the professional walkman video converter. it  allows you to convert video easily. 

Free Download : [http://www.video-converters.org/walkman-video-converter.php](http://www.video-converters.org/walkman-video-converter.php)

---

### Post by wildmanne39 on 2013-03-08
Old thread closed!

---

