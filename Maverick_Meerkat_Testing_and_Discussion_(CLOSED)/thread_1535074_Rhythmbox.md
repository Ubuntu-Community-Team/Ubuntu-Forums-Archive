---
title: "Rhythmbox"
date: 2010-07-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by eTM_ on 2010-07-20
Is there a reason that rhythmbox not just plays the AUDIO of every format gstreamer supports? e.g. the audio in flv oder mp4 or mov files? Would be useful.

Or am I missing something?

---

### Post by cj.surrusco on 2010-07-20
That's because Rhythmbox doesn't support watching videos. You need a program like Movie Player or VLC Player to watch videos.

---

### Post by zekopeko on 2010-07-20
> **eTM_ said:**
> Is there a reason that rhythmbox not just plays the AUDIO of every format gstreamer supports? e.g. the audio in flv oder mp4 or mov files? Would be useful.

Or am I missing something?

If you want a MEDIA player as opposed to a MUSIC player then use Banshee. It supports both video and audio.

---

### Post by mc4man on 2010-07-20
> That's because Rhythmbox doesn't support watching videos

Actually it does, watching one now in rhythmbox (though why one would want to....

Previously it would play the audio only, if it could decode,  which was preferable I'd guess.

EdiT:
if you turn off the visualization (edit -> plugins )  then it will only play the audio (though no timeline control

should play audio from all supported gstreamer formats

---

### Post by eTM_ on 2010-07-21
@mc4man: you are right, i just found out that when I call rhythmbox with the path of a video-file it will play. Drawbacks:

* The files are not shown in the media library (0.13 from maverick repos)
* no timeline control

@cj.surrusco: i know. not converting downloaded music vids (youtube et al), just playing the audio in a normal playlist would be nice though

@zekopeko: banshee is not working well for me. stuttering audio, high resource usage. And I just dont like it.

I think having videos with audio from youtube, vimeo, dailymotion on the disk is a very common usecase. Sometimes i want to watch the vids, sometimes i just want to listen to the audio:

* Rhythmbox to have all files that are supported by gstreamer in den media lib would be awesome.

---

### Post by mc4man on 2010-07-21
If it wasn't rhythmbox (probably)...  you can take some media players and make a new audio only version. (or other custom purposes. 
 Pretty simple

As an  ex. vlc ( I use a built one in /usr/local, repo one would be in just /usr

```
cp /usr/[COLOR="Blue"]local/[/COLOR]share/applications/vlc.desktop  ~/.local/share/applications/vlc-audio.desktop
```


 ```
gedit  ~/.local/share/applications/vlc-audio.desktop
```

Change the Name=Vlc to something like Name=Vlc Audio Player

Change the Exec=vlc %U to 
```
vlc --vout dummy %f
```
Save and it will be a new right click choice and in your Applications  - Sound & Video

Other apps can also be 'duped' with  new names and Exec's/configurations, ect., ect.

---

