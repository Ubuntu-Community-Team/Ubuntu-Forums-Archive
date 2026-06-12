---
title: "Avidemux lavc (== libavcodec?) MJPEG not playing in Windows with ffdshow (tryouts)"
date: 2008-05-29
forum: Multimedia Software
---

### Post by hopla on 2008-05-29
Hi,

Like the subject says: I'm trying to play some MJPEG AVIs in Windows XP (with [ffdshow-tryouts]("http://sourceforge.net/projects/ffdshow-tryout/") codecs installed). I created the MJPEG AVIs in Ubuntu with Avidemux choosing "MJPEG (lavc)" as video output format. I can play the files under XP using VLC, but not in a player using DirectShow, even though a DirectShow MJPEG decoder is installed (the ffdshow-tryouts libavcodec). The video opens, the first frame is shown, but it does not play any further.

I was under the impression that lavc == libavcodec. If so, the files should work on both my Ubuntu and Windows installations since in both cases the same encoder/decoder library is used. Can anyone confirm that lavc == libavcodec?

If this is not the case (lavc != libavcodec), what can  I do to make it work? Are there any other options for sharing MJPEG AVIs between Ubuntu and XP? Mind you, I need a solution that works with DirectShow! Just being able to view the video in VLC is not enough, I want to use the video in a specific program that only supports extra codecs via DirectShow (like most Windows video progs).

Thanks in advance for any helpful clues given!

Hopla

---

### Post by xc3RnbFO8P on 2008-05-29
Try to install **K-Lite** codec mega pack (google it).

---

### Post by Dynamo_Joe on 2008-05-30
Try VLC for Windows ...

---

### Post by hopla on 2008-05-30
> **Ringi said:**
> Try to install **K-Lite** codec mega pack (google it).

I'm a little reluctant to install K-Lite, for me it belongs in the spyware/malware category... Besides I think it ships with the libavcodec from the ffdshow project, so I would get the same result.

> **Dynamo_Joe said:**
> Try VLC for Windows ...

Thank you Joe, but you might want to read my post again :) :

"Just being able to view the video in VLC is not enough, I want to use the video in a specific program that only supports extra codecs via DirectShow (like most Windows video progs)."

That's the big deal: I don't just want too view the video, I need to use it in a certain program!

---

### Post by Dynamo_Joe on 2008-05-30
Sorry, hopla, my bad! :) 

Try the doom9.org forums ... there's a thread on Avidemux and "Lord Mulder" usually post links and builds from the SVN tree or you can try the Avidemux forum itself. 

Can't help with the "Directshow filters" as I find myself spending more time in Linux than Windows ... the only time that I go back to Windows is to extract my (remaining) VCD collection onto the HD (these were brought before DVDs even existed and you can still buy "laser discs").

---

### Post by hopla on 2008-05-30
I GOT A WORKING SOLUTION!

This is what I have been doing:

I eventually gave K-Lite a try (I reviewed my opinion about it, seems it was mostly based on shady poser sites like this one: [http://www.k-litecodecpack.com/](http://www.k-litecodecpack.com/)). It kinda worked, it played the files created with Avidemux, but it didn't work well (slow or just didn't 'jump') on random seeks, which I really need. Why it played at all and not with ffdshow-tryouts is still a mystery to me, since I confirmed with GSpot that K-Lite also uses the ffdshow library to decode the MJPEG. Well, maybe they use a different (older) version... Or it does some preprocessing on it...

Anyway since this wasn't really a solution I decided to try another approach. In my Windows days I used a program called SUPER to encode my files to MJPEG before editing them in VirtualDub. In VirtualDub I would then do a direct stream copy when saving my edited file.
Now SUPER uses ffmpeg libraries to encode to MJPEG! So installed ffmpeg in Ubuntu and encoded the file to MJPEG. Then I edited in Avidemux (just some cutting) and did a direct copy when saving my edits. The resulting file worked perfectly in Windows! In fact it worked better than the files encoded with SUPER. Because they now even worked with the MJPEG decoder from Windows (quartz.dll)! They also worked just as well with ffdshow, which is a good thing since I still need that for my old files that where encoded with SUPER.

I will be SOL however, when I want to do some editing in Avidemux that goes beyond simple cut and past operations. Because most of the time things like sharpen/contrast/... require a re-encode. But then I can just re-encode that resulting file with ffmpeg again. I might get some quality loss, but at least its better than nothing.

> Sorry, hopla, my bad! :) 

No problem, people tend to overlook the details in my lengthy posts :)

> Can't help with the "Directshow filters" as I find myself spending more time in Linux than Windows ...

Hehe, yesterday was the first time in weeks since I booted back into Windows. That one program is the only thing I need Windows for and I'm quite happy about that :) However, I must say I was impressed by the boot time XP has on a Core 2 Dou. It booted in under 15 secs!

---

