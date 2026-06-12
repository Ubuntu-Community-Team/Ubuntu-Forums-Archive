---
title: "Two newbie questions"
date: 2008-02-17
forum: Mythbuntu
---

### Post by Caps18 on 2008-02-17
1. [SOLVED, I think]When I am watching Live TV and then switch to watch recordings, the live TV that I was just watching (along with some of the other channels I flipped through) show up in the watch recording list.  Is there any way to disable this?
                  -There is an option under TV Settings -> General or Playback that says "Show 'LiveTV' recordings when using 'All Programs' filter"

2. I have found out how to transfer video and pictures to my Linux machine from Windows, it is actually way easier than I thought it would be.  I just had to type //mythbuntu from the Run dialog box in Windows and the hard drive popped up.  But, how do I get the videos to show up in MythTV?  I can access and play them in Mythbuntu using VLC, but they haven't shown up like my pictures have.  I am putting them in /var/lib/mythtv/videos, and they are AVI files.  Do I have to setup MythTV to look in this directory or something?

3.[SOLVED] Is there any way to un-install a plug-in?  I wrongly picked the default installation instead of going through and selecting individual plug-ins this time.  I would like to remove the phone, netflix and games ones.  I have found it in the control panel, but do I need to restart before MythTV is updated?
                 - I clicked Quit instead of Apply, then Quit.

---

### Post by newlinux on 2008-02-17
You need to put the videos in your mythvideo folder (which by default I believe is /var/lib/mythtv/videos. Then you need to run video manager from the setup menu to scan them in. For pictures you need to put them wherever the picture directory you have specified in the mythfrontend setup, but you don't need to do a scan when you add new pictures.

---

### Post by Caps18 on 2008-02-17
Thanks, that fixed the problem.  

I am now trying to add covers to the video files, but it doesn't seem to find any pictures.  I have put the pictures in the video/movie name/picture.jpg (or .png) directory.

Or is there some other way that it is done that I haven't realized?

---

### Post by newlinux on 2008-02-17
> **Caps18 said:**
> Thanks, that fixed the problem.  

I am now trying to add covers to the video files, but it doesn't seem to find any pictures.  I have put the pictures in the video/movie name/picture.jpg (or .png) directory.

Or is there some other way that it is done that I haven't realized?

I don't think mythvideo automatically reads cover art like that. YOu can specify a directory where all cover art is supposed to go in the setup, and then in video manager you can select the cover art image, or you can manually edit the dbase, or have video manager manually search for it imdb, or there are a number of scripts that will pull stills from the video and insert them as cover art.

---

### Post by Caps18 on 2008-02-17
I am still working on it, but changing the picture name to folder.jpg will make it show up on the folder when you choose the Watch Videos option.

I'll have to search on how to get IMDB to automatically work, that would be nice.

---

### Post by locoHost on 2008-02-18
I'd like to know how this works myself. Do I have to go through every video and add metadata and cover art by hand?!?! What is the point in searching IMDB, manually entering IMDB number, etc, if nothing is looked up? Follow?

---

### Post by newlinux on 2008-02-18
> **locoHost said:**
> I'd like to know how this works myself. Do I have to go through every video and add metadata and cover art by hand?!?! What is the point in searching IMDB, manually entering IMDB number, etc, if nothing is looked up? Follow?

If your video is in imdb, the cover art and description information will be downloaded and automatically inserted in the database. So you can have video manager search imdb for the title or directly enter the imdb number yourself. But from video manager you have to do this for each video. There are scripts that automate this out there...

---

### Post by locoHost on 2008-02-18
> **newlinux said:**
> If your video is in imdb, the cover art and description information will be downloaded and automatically inserted in the database. So you can have video manager search imdb for the title or directly enter the imdb number yourself. But from video manager you have to do this for each video. There are scripts that automate this out there...

You're contradicting: First sentence says "the cover art and description information will be downloaded and automatically inserted in the database" but then next to last sentence says "But from video manager you have to do this for each video"...

So which is it? Is there a process that I can somehow start up that will go get the movie inof? Or do I have to enter the coverart and metadata by hand?

Thanks for the reply :)

Mark

---

### Post by larsolav on 2008-02-18
Let's say you have a file called Alice_in_wonderland.iso in the MythVideo folder. When you go to video manager and highlight the file, just press your menu button on the remote (or m on a keyboard?) and select look up IMDB or something like that. Myth will automatically look up Alice in Wonderland and insert the poster and description (you may have to select which version you have on a list of Alice In Wonderlands). You have to do this for each file in the folder. If the film is in IMDB you do not have to enter meta data manually. If it is not there you may have to enter your own info, and some movies may not have a poster on IMDB.

---

### Post by locoHost on 2008-02-18
Hmmm, that doesn't work for me. Does the lookup use the file name as it reference or the title that I enter and save in the database? Like for example a DVD rip folder will have VIDEO_TS.IFO as the start up file. Is the lookup trying to find VIDEO_TS rather than the correct name that I entered in the metadata?

Thank you very much for your help! :)

---

### Post by larsolav on 2008-02-18
Someone correct me if I am wrong, but I think that it looks up based on the tilte you entered, because when I have in the past had an ISO called HNMO.ISO (or something like that), I would change the movie title (not the file name) on the top line of the metadata edit menu from "HNMO" to "Home on the range" and then select search IMDB and it would be found by Myth in IMDB. I am not knowledgeable enough to know why it is not working for you. Hopefully someone else may know... :confused:

---

### Post by newlinux on 2008-02-18
> **locoHost said:**
> You're contradicting: First sentence says "the cover art and description information will be downloaded and automatically inserted in the database" but then next to last sentence says "But from video manager you have to do this for each video"...

So which is it? Is there a process that I can somehow start up that will go get the movie inof? Or do I have to enter the coverart and metadata by hand?

Thanks for the reply :)

Mark

The automatic part is the metadata insertion into the database after you get a match with imdb. The not automatic part is you have to initiate this match for each video via video manager. What about that is contradicting?

It *should* use the title you enter in video manager if you've entered one, otherwise the filename:

[http://www.mythtv.org/wiki/index.php/MythVideo#Metadata_Lookup](http://www.mythtv.org/wiki/index.php/MythVideo#Metadata_Lookup)

I wonder what is going wrong in your case... Perhaps just input the imdb number and be don..

---

