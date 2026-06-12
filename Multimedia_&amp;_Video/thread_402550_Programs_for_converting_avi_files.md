---
title: "Programs for converting avi files?"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by Digitallysick on 2007-04-05
I need a program that can convert avi's to vob (full 4.7gb dvds) or kvcds, etc kinda like ffmpegx for mac. What linux program can do this?  Also how do i setup dvd:rip to get past css?

---

### Post by yabbadabbadont on 2007-04-05
Search these forums for the tovid howto thread.

Here is the tovid website:  [http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

You will want to install the SVN version as there have already been some bug fixes and useful new features added since the 0.30 release.

---

### Post by fenian on 2007-04-06
You can use ffmpeg...

> sudo apt-get ffmpeg

After it's installed encode it to .mpg for dvd,from the terminal run...
> 
ffmpeg -i myfile.avi -target ntsc-dvd /tmp/dvd.mpg

replace myfile.avi with the filename of your avi,replace /tmp/dvd,mpg with the path where you want the .mpg file to be saved to.Then you can use DVDStyler to create menus and the DVD structure (vob files).You can get the DVD Styler deb in the attachment below.More info on DVD Styler can be found [here]("http://www.dvdstyler.de/").

---

### Post by nerdman978 on 2007-04-06
I just use a Windows based app with Wine to convert my files to a format my Rockbox iPod can read.

---

### Post by Mithrilhall on 2007-04-06
ManDVD....:KS 

[http://kde-apps.org/content/show.php?content=38347](http://kde-apps.org/content/show.php?content=38347)

---

### Post by ruibernardo on 2007-04-07
I use two programs: [Avidemux]("http://fixounet.free.fr/avidemux/screenshots.html") and [DeVeDe]("http://www.rastersoft.com/programas/devede.html") (both on the repositories). You can just use DeVeDe to create VOB files, or an ISO file to burn to the DVD. The latest version [DeVeDe 2.12]("http://www.rastersoft.com/programas/devede.html") can put the subtitles the selectable way on the DVD (with spumux, also in the repos).

I usually edit the AVI files in [Avidemux]("http://fixounet.free.fr/avidemux/"). To work with Avidemux look at this page: [http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides](http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides).

After editing you can add the mpeg files in DeVeDe. Click "Advanced Options", select the "Misc" tab on the right and check the option "This file is allready in MPEG-PS format, ready to DVD/xCD.". Using this option DeVeDe will not reencode the files you created in Avidemux, but still insert the  subtitles as selectables and create the ISO file or DVD structure (if you don't use subtitles, forget this part).

Then you can create an ISO file or you can create the structure of the DVD on disk and then create menus and other things on DVDStyler.

To install DVDStyler add the following APT line in you repositories: 

[FONT=Fixedsys]deb [http://dvdstyler.sourceforge.net/repository/ubuntu/](http://dvdstyler.sourceforge.net/repository/ubuntu/) dapper main[/FONT]

Update your repositories and install the dvdstyler package. This works on Edgy, leave the dapper word there. Did not tested on Feisty.

I find all three programs simple to use. Hope you enjoy creating DVD's this way!! :)

---

### Post by reality_hunter on 2007-04-14
> **epimeteo said:**
> I use two programs: [Avidemux]("http://fixounet.free.fr/avidemux/screenshots.html") and [DeVeDe]("http://www.rastersoft.com/programas/devede.html") (both on the repositories). You can just use DeVeDe to create VOB files, or an ISO file to burn to the DVD. The latest version [DeVeDe 2.12]("http://www.rastersoft.com/programas/devede.html") can put the subtitles the selectable way on the DVD (with spumux, also in the repos).

I usually edit the AVI files in [Avidemux]("http://fixounet.free.fr/avidemux/"). To work with Avidemux look at this page: [http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides](http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides).

After editing you can add the mpeg files in DeVeDe. Click "Advanced Options", select the "Misc" tab on the right and check the option "This file is allready in MPEG-PS format, ready to DVD/xCD.". Using this option DeVeDe will not reencode the files you created in Avidemux, but still insert the  subtitles as selectables and create the ISO file or DVD structure (if you don't use subtitles, forget this part).

Then you can create an ISO file or you can create the structure of the DVD on disk and then create menus and other things on DVDStyler.

To install DVDStyler add the following APT line in you repositories: 

[FONT=Fixedsys]deb [http://dvdstyler.sourceforge.net/repository/ubuntu/](http://dvdstyler.sourceforge.net/repository/ubuntu/) dapper main[/FONT]

Update your repositories and install the dvdstyler package. This works on Edgy, leave the dapper word there. Did not tested on Feisty.

I find all three programs simple to use. Hope you enjoy creating DVD's this way!! :)

hey thanks for the info, 
I actually used the DeVeDe program today for the first time and yes it was simple.
I got an iso file which i put on the dvd and into the player

The only problem is that subtitles and video and audio are all there like  I was expecting, but however there is an AUDIO delay, lips are moving but the sound comes after about 1-2 seconds.
when I put the same dvd on the computer drive, there is no delay while playing on the computer.  
HOw do I fix this thing, because the view sample button shows everything good but the actual dvd in a stand alone dvd player has a delay????
Also, I know that there is a audio delay option...so I am assuming that number of others also have this issue?? anyways, if the audio is coming after 1-2seconds do I set delay to "+2" right? or "-2"? why do this delay happen anyways? 
Another thing is that the final ISO is only like 2.5 GB, why is the size so small, almost half?  because with windows whenever I created a similar movie, an ISO was created with more that 4 GB. why is the difference? 

thanks alot for help:)

---

### Post by Digitallysick on 2007-04-14
I like DeVeDe alot since i tried to , only issue i have, is when i convert files to iso, then play them in vlc, the video has horizontal lines through it. I'm not sure if its how my vlc is playing the movies, or if its a problem with how they convert. As for your timing issue on the audio im not sure my audio was in sync on mine after the convert

---

### Post by reality_hunter on 2007-04-14
> **Digitallysick said:**
> I like DeVeDe alot since i tried to , only issue i have, is when i convert files to iso, then play them in vlc, the video has horizontal lines through it. I'm not sure if its how my vlc is playing the movies, or if its a problem with how they convert. As for your timing issue on the audio im not sure my audio was in sync on mine after the convert

the VLC player on my computer plays the burned ISO file fine...no problem.  ONly with the home dvd player audio is out of sync.

---

### Post by fakie_flip on 2007-04-30
> **reality_hunter said:**
> 
Another thing is that the final ISO is only like 2.5 GB, why is the size so small, almost half?  because with windows whenever I created a similar movie, an ISO was created with more that 4 GB. why is the difference? 

Have you tried running that windows software in Wine? What is the name of it? You could also try ToVid instead of DeVede and search this forum for some other software.

---

### Post by reality_hunter on 2007-05-01
> **fakie_flip said:**
> Have you tried running that windows software in Wine? What is the name of it? You could also try ToVid instead of DeVede and search this forum for some other software.

ok I will give that a shot as well, thanks

---

### Post by ruibernardo on 2007-05-06
> **epimeteo said:**
> I use two programs: [Avidemux]("http://fixounet.free.fr/avidemux/screenshots.html") and [DeVeDe]("http://www.rastersoft.com/programas/devede.html") (both on the repositories). You can just use DeVeDe to create VOB files, or an ISO file to burn to the DVD. The latest version [DeVeDe 2.12]("http://www.rastersoft.com/programas/devede.html") can put the subtitles the selectable way on the DVD (with spumux, also in the repos).

I usually edit the AVI files in [Avidemux]("http://fixounet.free.fr/avidemux/"). To work with Avidemux look at this page: [http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides](http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides).

After editing you can add the mpeg files in DeVeDe. Click "Advanced Options", select the "Misc" tab on the right and check the option "This file is allready in MPEG-PS format, ready to DVD/xCD.". Using this option DeVeDe will not reencode the files you created in Avidemux, but still insert the  subtitles as selectables and create the ISO file or DVD structure (if you don't use subtitles, forget this part).

Then you can create an ISO file or you can create the structure of the DVD on disk and then create menus and other things on DVDStyler.

To install DVDStyler add the following APT line in you repositories: 

[FONT=Fixedsys]deb [http://dvdstyler.sourceforge.net/repository/ubuntu/](http://dvdstyler.sourceforge.net/repository/ubuntu/) dapper main[/FONT]

Update your repositories and install the dvdstyler package. This works on Edgy, leave the dapper word there. Did not tested on Feisty.

I find all three programs simple to use. Hope you enjoy creating DVD's this way!! :)

Hi reality_hunter,

I also did notice the problem of sound in video some files with DeVeDe. Avidemux is perfect with this.

About the size of the final ISO file (2.5 GB in this case), Avidemux has the option to make the file fit in DVD/CD/VCD or else. Don't know if DeVeDe has one, but aparently it hasn't.

That option is in the menu in Auto -> DVD. This option calculates a bitrate so that the resulting file fits the media you will use. If the resulting file is still too big because you want to put some more files in the DVD beside the one your working now, or too big because the original video file is longer then 2 hours, then click on the lateral bar, in Video -> Configure and change the value in "Average bitrate" before you click "Save". 

This way the size of file will change. Avidemux also let's you preview the results of the option you use. I use DeVeDe for the quick run, and Avidemux + DeVeDe to have quality. If you use this process, then when you add the resulting mpeg file from Avidemux into DeVeDe, don't forget to check the option "This file is allready in MPEG-PS format, ready to DVD/xCD." in the "Misc." tab in the "Advanced Options" in DeVeDe, so that DeVeDe don't reencode the file you just encoded with Avidemux.

Hope this help in some way :popcorn:.

---

### Post by cornish on 2007-05-08
I have tried avidemux and tovid they all seem to convert the film ok but when I play the file the length is 23 minutes instead off 1hr 56mins

---

