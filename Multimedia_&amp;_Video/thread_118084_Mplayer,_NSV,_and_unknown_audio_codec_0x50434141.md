---
title: "Mplayer, NSV, and unknown audio codec 0x50434141"
date: 2006-01-16
forum: Multimedia &amp; Video
---

### Post by dolson on 2006-01-16
If you're trying to play an NSV file in Mplayer, and you get video, but no audio, along with a message box stating that audio codec 0x50434141 is unknown, then this is how I solved the problem.

sudo gedit /etc/mplayer/codecs.conf

Now search for "faad" in the file. You will find this section:

```
audiocodec faad
  info "FAAD AAC (MPEG-2/MPEG-4 Audio) decoder"
  status working
  fourcc mp4a,MP4A
  fourcc "AAC " ; Used in NSV
  format 0xff
  format 0x706D
  driver faad
  dll libfaad2
```

Now just modify that section so that it looks like this (make the changes in red):

```
audiocodec faad
  info "FAAD AAC (MPEG-2/MPEG-4 Audio) decoder"
  status working
  fourcc mp4a,MP4A
  fourcc "AAC "[color=red],"AACP"[/color] ; Used in NSV
  format 0xff
  format 0x706D
  [color=red]format 0x50434141[/color]
  driver faad
  dll libfaad2
```

Now save the file, and open up your video file in Mplayer.

Works_For_Me(tm). No recompile or anything. THE KEY THING TO DO is to NOT put that entire section at the end of the file (unless for some reason, your file is missing that section to begin with). If you do that, it won't work because you'll have the section in there twice, and the second one is ignored.

*BTW, this also worked for my version of XBMC. The config file needed exactly the same changes (since it uses mplayer). Just an extra bonus for those of you who use it too. Newer versions than the one I'm using might not require this change.*

---

### Post by mac.ryan on 2007-01-05
This is exactly the same problem I have, but I couldn't find the file I should modify (nor I could find a codec section in any of the configuration files in the directory). I also tried a

>  sudo find -name codecs.conf

from the / but without any success. Any idea? The funny thing is that with VCL I can hear the sound but can't see the video, and vice versa with mplayer...

Thanks in advance,
Mac.

---

