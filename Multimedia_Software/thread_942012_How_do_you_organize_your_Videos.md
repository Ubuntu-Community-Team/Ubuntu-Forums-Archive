---
title: "How do you organize your Videos"
date: 2008-10-08
forum: Multimedia Software
---

### Post by Acoshi on 2008-10-08
Since there isn't really a program in Ubuntu that organizes video files, I was wondering how everyone else organizes their video collection. Do you store files manually in a video folder? Or do you use special program or method to keep track of videos.

---

### Post by aeiah on 2008-10-08
right now i just store them in a folder. if i back them up to dvds, i create an empty dummy file and put it in a subfolder called backup (done with a script).

im slowly working on a film cataloging program because unless you want to use a media center app, the choices are pretty limited right now. my program is really gonna just be for movies though. at least to start with.

---

### Post by lovinglinux on 2008-10-08
I organize TV Shows using a specially configured Firefox profile (see tutorial on my sig), which allows me to create thumbnails with pics (wallpaper of the show) linking to folders, playlists or single files. 

[[IMG]http://img526.imageshack.us/img526/4857/screenshotfinishedxl5.th.png[/IMG]](http://img526.imageshack.us/img526/4857/screenshotfinishedxl5.png)   [[IMG]http://img233.imageshack.us/img233/2977/screenshot2jp1.th.png[/IMG]](http://img233.imageshack.us/img233/2977/screenshot2jp1.png) 

Each TV series has it's own folder and playlist. I still can't organize them automatically, so I have to create the playlist and the thumbnails manually. Nevertheless, I keep all new TV recordings on the same folder, so I can open it with a single command, to play all new videos without creating a playlist. After watching the show I move it to the show private folder if I want to keep it.

I'm still searching for a script to automatically create a playlist based on folder content and to watch for content modifications. Then I will be able to link each TV show thumbnail to a single playlist file that update itself.

You could use Miro (it is in the repos) to organize your videos, but I don't know if it can automatically organize them by category (show). I don't like Miro because of the embedded player limitations (can't play subtitles for example).

Note: I have posted in the other thread, but I guess this is the right one.

---

### Post by lovinglinux on 2008-10-08
I forgot to mention that you could also use [GCStar]("http://www.gcstar.org/index.en.php") to catalog the TV shows. It has an option to create a group for each tv show and you can link directly to the video file, to play them from the catalog. The only issue is that you have to create a new entry for each episode. A solution would be creating only a single entry for each show and link to a playlist instead.

---

### Post by Acoshi on 2008-10-08
I am trying Miro now, it seems pretty cool actually. I will download GCStar next, from the looks of it this might be what I am looking for.

---

### Post by Acoshi on 2008-10-08
Does anyone know how to create a group in GCStar?

---

### Post by lovinglinux on 2008-10-08
> **Acoshi said:**
> Does anyone know how to create a group in GCStar?

In the "Details" tab, put the name of the tv show in the "Series" field. Then you can use the "Group by" in the big menu, selecting the option "Series".

---

### Post by Acoshi on 2008-10-09
Thanks for the heads up!

---

### Post by Acoshi on 2008-10-09
GCStar is great for Movie collections but not so great for TV Shows. Anyone have any idea of a collections manager that would work really well for both. Since I over a 100 tv episodes all out of their respective folders and all I can see is their titles, Hopefully if there isn't a program that can organize these is there a script that can?

---

### Post by lovinglinux on 2008-10-09
> **Acoshi said:**
> GCStar is great for Movie collections but not so great for TV Shows. Anyone have any idea of a collections manager that would work really well for both. Since I over a 100 tv episodes all out of their respective folders and all I can see is their titles, Hopefully if there isn't a program that can organize these is there a script that can?

Do you need to retrieve embedded category tags form the video files or you just need to organize and play them?

I had a lot of help [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=942164") and finally managed to created a script to generate playlists based on files extensions, but you could modify the script to get files based on titles. Depending on how do you name your videos you could even create playlists automatically, based on series name and seasons.

You can see examples how I'm using this script in my Firefox Media Center tutorial (link in my sig) on Section 9.

---

### Post by Acoshi on 2008-10-09
Thanks for the help. I think I might have found my solution. 
I now use GCStar to organize my movies as well as videos.

---

### Post by lisati on 2008-10-09
(slightly embarassed) :oops: I use the Windows software that came with my camcorder - it organises footage by date - and some $NZ300 editing software as well.

Otherwise I give the file a name relevant to who I recorded it for and/or the ocassion, often with the date, and save it in a generic "videos" folder on an external USB hard drive. Largely manually......

---

### Post by lovinglinux on 2008-10-09
> **Acoshi said:**
> Thanks for the help. I think I might have found my solution. 
I now use GCStar to organize my movies as well as videos.

Glad to hear that. I would like to know what was preventing you from using GCStar and how did you solved the limitations?

---

### Post by SuperSonic4 on 2008-10-09
/media/Video

It is a separate partition on my media drive (3 hard drives are handy :p)

Otherwise it's subdivided into folders which I use dolphin to view except for Video Converter which is like a temporary folder for videos before re-encoding/audio rip

---

