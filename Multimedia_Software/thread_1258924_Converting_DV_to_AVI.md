---
title: "Converting DV to AVI"
date: 2009-09-05
forum: Multimedia Software
---

### Post by gemmahenchmen on 2009-09-05
I've been having problems with Ubuntu video editing software so I decided to pass my work over to Vista, and I'm trying to use it with Windows Movie Maker. The problem is, the video is in .DV format, which is incompatible. I need to get it into .AVI format. I've been given a command from another forum on how to do this, and I'd like to make sure it's not damaging to my computer in any way (I've heard some people are giving harmful terminal instructions out):
 
sudo ffmpeg -i test.dv -vcodec xvid -acodec mp3 -b 2000k -ac 2 -ab 128k -vtag DX50 -qmin 5 test.avi
 
Thanks

---

### Post by jordilin on 2009-09-05
Well, I'm not an expert on ffmpeg, but if I were you, I would double check each one of these options in the ffmpeg manual page. Just type "man ffmpeg".

---

### Post by gemmahenchmen on 2009-09-05
Thanks, I checked the man page and it's safe. Thanks

---

### Post by jordilin on 2009-09-05
Well, just saw that you are using "sudo". You shouldn't do that for just converting video formats.

---

### Post by andrew.46 on 2009-09-05
Hi gemmahenchmen,

> **gemmahenchmen said:**
> 
 
```
sudo ffmpeg -i test.dv -vcodec xvid -acodec mp3 -b 2000k -ac 2 -ab 128k -vtag DX50 -qmin 5 test.avi
```

A few comments..... 

[LIST=1]
[*]As has been already mentioned you do not need to use sudo for this command.
[*]Depending on your version of FFmpeg '-acodec mp3' may very well fail, newer versions will use '-acodec libmp3lame'. The [Fakeoudoorsman's guide]("http://ubuntuforums.org/showthread.php?t=1117283") is also well worth a look at for encoding to the so-called 'restricted' encoders.
[*]I see you have specified a video bitrate '-b 2000k' *as well as* a quantizer setting '-qmin 5', you might be better to stick with the quantizer setting and experiment with the settings between 0 and 31 and settle on the quality/size that suits you. You might be better again with a setting such as '-crf 22' but I am a little lost with the comparative benefits of constant rate factor vs the older qmin/qmax settings. 
[*]I see you use '-vtag DX50', you could as well use '-vtag XVID' but this is a simple labelling issue.
[*]You are using xvid encoding, you might find better results with using '-vcodec mpeg4 -vtag XVID' which I believe gives better results under FFmpeg and will also play under Windows Media Player.
[/LIST]

But I am not an expert in this area, hopefully the Fakeoutdoorsman will have some thoughts :).

Andrew

---

### Post by Gen2ly on 2009-09-05
Good tip andrew, I'll have to write that down.

---

### Post by andrew.46 on 2009-09-05
Hi Gen2ly,

> **Gen2ly said:**
> Good tip andrew, I'll have to write that down.

Please remember I am an FFmpeg n00b so nothing I have written here should be considered authoritative, simply some extra material to experiment with :-). My own FFmpeg usage is always guided by my 2 best friends Trial and Error...

Andrew

---

### Post by michael37 on 2009-09-05
If you choose a GUI tool, I recommend [Avidemux]("http://www.getdeb.net/app/Avidemux"), [WinFF]("http://winff.org/html_new/") (better control over encoding) or [Handbrake]("http://handbrake.fr/") (better GUI and great preview).  Both are able to translate DV into AVI.

Follow links to the respective sites for download instructions, and be sure to read [thread=766683]THE FAQ[/thread].

Avidemux:
[IMG]http://www.getdeb.net/media.php?id=139&type=screens&w=425&h=350[/IMG]

Handbrake:
[IMG]http://trac.handbrake.fr/raw-attachment/wiki/LinGuiScreenshots/HandBrake-Pic.jpeg[/IMG]

---

