---
title: "Where can I find html/text decoder so I can play videos"
date: 2009-06-18
forum: Multimedia Software
---

### Post by sprogmeister on 2009-06-18
I am try to play some video files but they request the html/text decoder that remains unfound. Can anyone tell me out to install it. I have looked through the forums and google but any answers do not work. Please help

---

### Post by andrew.46 on 2009-06-18
Hi sprogmeister,

> **sprogmeister said:**
> I am try to play some video files but they request the html/text decoder that remains unfound. Can anyone tell me out to install it. I have looked through the forums and google but any answers do not work. Please help

Can you give an example of one of these files?

Andrew

---

### Post by hansdown on 2009-06-18
Hi sprogmeister.

I think the```
 ubuntu-restricted-extras
``` package in synaptic covers this.

---

### Post by sprogmeister on 2009-06-19
Thanks for the advice the restricted extras are already installed. The files are .flv that appear with a film canister symbol. Others just work with a small thumb nail indicating what the file contains. I hope this helps!

---

### Post by hansdown on 2009-06-19
Have you tried playing them in VLC? It's supposed to have the plugin.

Also, do you have ```
flashplugin-nonfree
``` installed?

---

### Post by sprogmeister on 2009-06-20
Thanks hansdown, I've tried VLC and have flahplugin-nonfree installed and it still fails to play. Any ideas?

---

### Post by hansdown on 2009-06-20
You could try converting the files with ```
DeVeDe
``` or ```
avidemux
```

I have no experience with this, so all I can offer are a couple tutorials.

[http://blogcritics.org/scitech/article/making-dvds-with-devede-in-linux/](http://blogcritics.org/scitech/article/making-dvds-with-devede-in-linux/)

[http://www.videohelp.com/forum/archive/how-to-get-started-with-avidemux-edit-and-convert-any-video-format-t357763.html](http://www.videohelp.com/forum/archive/how-to-get-started-with-avidemux-edit-and-convert-any-video-format-t357763.html)

---

### Post by sprogmeister on 2009-06-20
Thanks for all your help Hansdown, greatly appreciated. I will continue trying.

---

### Post by andrew.46 on 2009-06-20
Hi sprogmeister,

> **sprogmeister said:**
> I've tried VLC and have flahplugin-nonfree installed and it still fails to play. Any ideas?

Can you identify the file with FFmpeg? Run the following from the commandline:

```
ffmpeg -i *myfile.flv*
```

and just have a quick look at:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

which will show how to install a decent copy.

Andrew

---

### Post by sprogmeister on 2009-07-04
Thanks Andrew, I tried it but it failed to work. I fell it might be a layer 8 issue ie: me! I'll keep trying!

---

### Post by sohel001 on 2009-07-04
With the auto *HTML* file with FLV, Flash Player embedded, it is going to be an **...** the benefit is as obvious as you *can* see in *text* &logo watermarking for *video* **...** FLV to *Video* Converter *can* dare to say it will benefit every portable device **...** How to make FLV *videos play* in Windows Media Player? **..**

---

### Post by sprogmeister on 2009-08-06
Sorry, don't quite understand that one?

---

