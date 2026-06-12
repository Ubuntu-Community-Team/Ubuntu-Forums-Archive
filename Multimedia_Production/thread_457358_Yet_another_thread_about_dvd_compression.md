---
title: "Yet another thread about dvd compression"
date: 2007-05-28
forum: Multimedia Production
---

### Post by juxtaposed on 2007-05-28
Ok. I have many dvds on my computer (in .iso, I can mount them to get the video_ts folder though) that I want to encode to H.264, with probably vorbis audio and either ogg, ogm, or matroska as a container.

I tried thoggen; great program (though the file was undersized). I just wish it could encode to H.264 instead of theora; the web site says it will be added sometime in the future, but I think the it might be dead or something since it was last updated October 2006.

I tried ogmrip; I think everything was fine, just the video wasn't synced with the audio and it was undersized by 40MB Or so.

I tried dvd::rip; So many settings, but it doesn't seem to do many things automatically (it and vlc didn't agree what framerate my movie was). It made a movie with a higher resolution then should have been made (I don't think there is any place to set it to set the resolution, or to tell it to do it automatically) and the aspect ratio was off, and the file was over a hundred MB oversized.

I tried k9copy on a small file, and even though I set it to x264 it still used xvid, and the only container I found was avi, and I couldn't set the audio codec (which I think is a limitation of avi).

Is there any secret encoder frontend or something that I am missing? I've been searching for the last few days. I know there are the command line ones, but i've always found that they don't do many things automatically, it's all manual (which is fine, to an extent).

Nero Recode was good on windows, but it isn't available for linux - and WINE doesnn't seem to work. I don't want to use it in vmware - I only want to use windows for my MP3 player and printing (well, I wish I could do those in linux, but you know what I mean).

I know things like this have been asked so many times, but I am hoping that there is some secret program that just got released or not many know about that someone will know about and say it or some mod to thoggen that supprots x264.

If I can't find anything to try next, i'll probably try the one that might work better - ogmrip - as I doubt that a developer would release something without testing it for a bug that big, so it might have been a one time thing and only on my computer.

---

### Post by robertpolson on 2007-05-30
Try 

[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

---

### Post by eye208 on 2007-05-30
MEncoder is probably the best tool for the job. It can read titles from DVDs or DVD images, select specific chapters, apply postprocessing (crop, scale, deinterlace, etc.), and encode to a large number of formats (including H.264) and containers (e.g. MP4). It also supports 2- or 3-pass encoding. It has many options, but there are only a few you need for the job. Check out the examples at the bottom of MEncoder's manpage.

---

### Post by juxtaposed on 2007-05-30
> 
Try 

[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)


Arnt those video editing?

I tried avidemux and I don't think it accepts DVDs as input.

> MEncoder is probably the best tool for the job. It can read titles from DVDs or DVD images, select specific chapters, apply postprocessing (crop, scale, deinterlace, etc.), and encode to a large number of formats (including H.264) and containers (e.g. MP4). It also supports 2- or 3-pass encoding. It has many options, but there are only a few you need for the job. Check out the examples at the bottom of MEncoder's manpage.

I looked at that, but it seems so complicated - telecine, 2:2 pulldown, all that stuff. (Hey, isn't a telecine a machine to copy film to digital? :P)

I did just read this:

> You may also have no choice but to use harddup with container formats that are not too tightly linked with MEncoder such as the ones supported through libavformat, which may not support frame duplication at the container level.

So, maybe I shouldn't use matroska as a container for ogmrip anymore.

I don't know... The syncing seemed to be fine when I accidently used the 2 channel directors comments audio part instead of the 5 channel normal one. I'll encode another movie with 2 channel audio and see what happens. If that doesn't work, I guess i'll try OGG or MP4.

---

### Post by billl on 2007-05-31
> **juxtaposed said:**
> So, maybe I shouldn't use matroska as a container for ogmrip anymore.

I don't know... The syncing seemed to be fine when I accidently used the 2 channel directors comments audio part instead of the 5 channel normal one. I'll encode another movie with 2 channel audio and see what happens. If that doesn't work, I guess i'll try OGG or MP4.
OGMRip uses harddup when necessary. A/V desync is a recurrent issue. When desync are fixed with a container, desync appear with another. I suspect there are issues with progressive/telecine movies, but I can't be sure since I don't have a lot of such DVDs. I also suspect some issues when ripping the audio tracks on slow systems but I need some feedback about this. Can you have a look at this thread: [http://sourceforge.net/forum/forum.php?thread_id=1712519&forum_id=258033]("http://sourceforge.net/forum/forum.php?thread_id=1712519&forum_id=258033") ?

Thanks,

Olivier

---

### Post by eye208 on 2007-05-31
> **juxtaposed said:**
> I looked at that, but it seems so complicated - telecine, 2:2 pulldown, all that stuff. (Hey, isn't a telecine a machine to copy film to digital? :P)
Just because an option is there, it does not mean you have to use it. That's why I told you to look at the examples at the bottom of the page. They are very very simple.

If you prefer options to be hidden from you, use this: [http://dvdripomatic.sourceforge.net/](http://dvdripomatic.sourceforge.net/)

---

### Post by juxtaposed on 2007-05-31
> I also suspect some issues when ripping the audio tracks on slow systems but I need some feedback about this. 

My computer is fairly fast, though I do run azureus when I am encoding.

I wouldn't think a slow computer would change how it is encoded - it would just take longer.

> Can you have a look at this thread: [http://sourceforge.net/forum/forum.p...orum_id=258033](http://sourceforge.net/forum/forum.p...orum_id=258033) ?

Someone on that thread said that setting the video to 720x480 or 640x480 would fix it. I normally set it to something under that.

Another person said that it happened when selecting only certain parts of the movie and I don't do that (unless you could excluding extras as that).

> Just because an option is there, it does not mean you have to use it.

I thought I had to do something to find if the source DVD had a 2:2 pulldown or something like that and tell mencoder whether it did or not.

> If you prefer options to be hidden from you, use this: [http://dvdripomatic.sourceforge.net/](http://dvdripomatic.sourceforge.net/)

I wan't options - I just want it to automatically do the stuff that I don't want.

> If you prefer options to be hidden from you, use this: [http://dvdripomatic.sourceforge.net/](http://dvdripomatic.sourceforge.net/)

That seems to only allow mp3 audio, xvid video, and avi container.

---

### Post by eye208 on 2007-06-01
> **juxtaposed said:**
> That seems to only allow mp3 audio, xvid video, and avi container.
Correct. MEncoder on the other hand gives you the option to choose from several formats/containers. That's all you need to do. Specify source device/image, codecs, output format and file name. If the results are not satisfactory for some reason, _then_ you can dive deeper and apply additional parameters to fix it. MEncoder is a complex tool, but it has reasonable defaults for everything that you don't specify on the command line.

---

### Post by juxtaposed on 2007-06-01
Ok, I guess i'll try that next as I just encoded another movie with ogmrip and it was yet again, out of sync (though not as much, and the movie was really long).

But for mencoder do I need to choose the video bitrate and all, or can I just set it to do like... Vorbis -q1 and the file size and have it do the video  bitrate automatically?

---

### Post by ivesjd on 2007-06-06
You could try acidrip, I'm not sure if thats what your looking for or not. But it seems to work pretty well.

---

