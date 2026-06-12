---
title: "Windows Media codec 11 available?"
date: 2009-05-18
forum: Multimedia Software
---

### Post by Nixie Pixel on 2009-05-18
Hi, I believe that Windows Media 11 is available, but after installing ffmpeg, ubuntu-restricted-extras, and codecs from the Medibuntu repository, I still only have Windows Media 1, 2, 7, 8, and 9.  

Is 11 available for Ubuntu?  If so, where can I find it?

Thanks!

---

### Post by Arup on 2009-05-18
WMV is proprietary and that means it won't happen soon. Why not convert them to a free format and then watch.

Btw, do you still hate Ubuntu?

---

### Post by Nixie Pixel on 2009-05-18
Thanks!

Read the article and find out ;)

---

### Post by Arup on 2009-05-18
> **Nixie Pixel said:**
> Thanks!

Read the article and find out ;)


I did, was just pulling yer legs. Use WinFF to covert WMV11 movies, I do that and it works out well, just use the unstripped codec by doing 
sudo apt-get install ffmpeg libavcodec-unstripped-52

---

### Post by FakeOutdoorsman on 2009-05-18
> **Arup said:**
> I did, was just pulling yer legs. Use WinFF to covert WMV11 movies, I do that and it works out well, just use the unstripped codec by doing 
sudo apt-get install ffmpeg libavcodec-unstripped-52

The *ubuntu-restricted-extras* metapackage contains *libavcodec-unstripped-52*.  Is there such a thing as WMV11?  I know there is a Windows Media Player 11. WinFF won't be able to decode and encode WMV11 because FFmpeg can't:
```
$ ffmpeg -formats | grep wmv
DEVSD  wmv1            Windows Media Video 7
DEVSD  wmv2            Windows Media Video 8
D V    wmv3            Windows Media Video 9
```

---

### Post by psyke83 on 2009-05-18
What about the w32codecs package from Medibuntu?

P.S. Are you confusing Windows Media **Player **11 with a non-existent Windows Media 11 codec?

---

### Post by Arup on 2009-05-18
> **psyke83 said:**
> What about the w32codecs package from Medibuntu?

P.S. Are you confusing Windows Media **Player **11 with a non-existent Windows Media 11 codec?

I guess she meant WMV 11 runtime which are needed to play wmv and asf files.

---

### Post by Nixie Pixel on 2009-05-18
I could be mistaken, I thought there was a codec 11, but I might just be thinking of the player.  

Sorry!

---

### Post by mc4man on 2009-05-19
Definitely the player

The latest from wm is wmv3 with hd video(VC-1) and either wma2 or wma3(pro) audio.

ffmpeg can handle all of them as far as decoding and or converting.

mplayer is the best overall player, pretty much can handle anything in the 32 bit ver., some limitations on 64 bit.
```
 D A    wmapro          Windows Media Audio 9 Professional
 DEA    wmav1           Windows Media Audio 1
 DEA    wmav2           Windows Media Audio 2
 DEVSD  wmv1            Windows Media Video 7
 DEVSD  wmv2            Windows Media Video 8
 D V    wmv3            Windows Media Video 9

```

---

### Post by Arup on 2009-05-19
> **FakeOutdoorsman said:**
> The *ubuntu-restricted-extras* metapackage contains *libavcodec-unstripped-52*.  Is there such a thing as WMV11?  I know there is a Windows Media Player 11. WinFF won't be able to decode and encode WMV11 because FFmpeg can't:
```
$ ffmpeg -formats | grep wmv
DEVSD  wmv1            Windows Media Video 7
DEVSD  wmv2            Windows Media Video 8
D V    wmv3            Windows Media Video 9
```


Ubuntu restricted extras is fine in x32 but in x64, it installs the dreaded x32 version of Flash by default which along with nsplugin leads to all kinds of issues. The alpha Flash10x64 works fine and is quite easy to install and doesn't need nsplugin.

---

