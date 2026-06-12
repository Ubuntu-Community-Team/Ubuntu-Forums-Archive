---
title: "Gnome Subtitles, select audio track"
date: 2012-05-11
forum: Multimedia Software
---

### Post by gizmo720 on 2012-05-11
I am trying to sync a subtitle file using Gnome Subtitles to a video in .mkv format. The problem is the language against which I am syncing is on the second audio track, and I cannot find a way to change the one that is played. Is it possible to do so in gnome subtitles. If not, would it be possible to remove the other audio tracks in a seperate program?

---

### Post by shantiq on 2012-05-11
hi there gizmo


there is a program called mkvmerge and mkvextract


you install it this way  

```
sudo apt-get install mkvtoolnix

```


[B]THEN
[/B]

quick from commandline    > mkvmerge -o nosub.mkv **-S ** originalfile.mkv




This will remove all your subs   the -S command








[B]=======================

[/B]
**OR **   GUI  and extra info.... [long answer:]]      you will need to add gui


>  sudo apt-get install mkvtoolnix-gui



go to applications/sound and video


untick the ones you want to remove add attachments for the ones you want to add
and click on start muxing.   i just tested one and it removed both subs in 1mn26



if you want the commandline instructions these are available too

[CENTER][ATTACH]217705[/ATTACH]
[/CENTER]



_**EXTRA commandline INFO [might be of use sometime...]**_


> First, use mkvmerge to list the MKV file&#8217;s contents:

```
mkvmerge -i MovieFile.mkv

```
You&#8217;ll see a listing similar to this:

File 'MovieFile.mkv': container: Matroska
Track ID 1: subtitles (S_TEXT/***)
Track ID 2: audio (A_MPEG/L3)
Track ID 3: video (V_MPEG4/ISO/AVC)

Next, use mkvextract to extract certain tracks / attachments based on the output from the above command:

```
mkvextract tracks MovieFile.mkv 1:thesubtitles.srt
  2:theaudio.mp3 3:thevideo.mp4
```


**in your case just extract the movie file of course**


[B]to add a sub
[/B]
```
mkvmerge -o target-file-with-subtitles.mkv source-movie.mpeg subtitle-file.srt

```

[B]merge 2 mkv
[/B]
 ```
mkvmerge -o full.mkv 1.mkv + 2.mkv
```  


**PS**    amazing in-depth article on related matters [**here**]("http://sub.wordnerd.de/linux-subs.html")   and commandline
[**here**]("http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge.html")

---

### Post by gizmo720 on 2012-05-11
Thanks, that is exactly what I needed.

---

