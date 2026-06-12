---
title: "suggestion for putting dvd onto hdd"
date: 2016-03-21
forum: Multimedia Software
---

### Post by yonnie on 2016-03-21
I'm wanting to put large amounts of DVDs (tv series) onto my HDD for viewing.  In the past I've tried this and ended up wasting many hours of recording and lost episodes.  I'm not interested in re-creating DVD's, I just want to be able to store the data on a HDD and watch it.  The DVDs I have are failing and evaporating before my eyes and I need to get them into a device where they can be more permanent.

What software application would be the easiest to use for this task?  What type of format?

---

### Post by howefield on 2016-03-21
Create iso files from the DVDs using xfburn ?. Playing the files back on the computer wouldn't be a problem but if you wanted to stream from a NAS type device it might be. Have also used vobcopy in the past but not sure how current that software is now.

If you want to transcode them I'd recommend Handbrake.

---

### Post by yonnie on 2016-03-21
One issue I ran into is copying iso files into same directory, there are file parts that think they already exist and then won't write, then after waiting an ungodly amount of time I might get an error message.  I'm trying to copy the dvds with episodes on them and it's just not working.  I'm not even going to pretend I understand the first thing about movie .iso's and there stupid file formats.  What does **** me off is when they go bad you can't find out who to contact to get replacements.  When they don't make them anymore, you're just screwed.

I've tried Handbrake, it's interface was unintelligible.  I don't want to burn a dvd, simply want to put the content onto an hdd.  I have a few hundred to do.

I suspect I have a new issue too!  It was working several months ago, now I think an update has removed the main part of reading/writing dvds.  I should probably figure out how to stop this damn updating mechanism too.  Updates should not be allowed to break things, you think?

---

### Post by yancek on 2016-03-21
> 
I've tried Handbrake, it's interface was unintelligible.

If you want to copy  movie files from a DVD to your hard drive Handbrake isn't the tool to use.  It's purpose is to create an mp4 video iso file from some other format, vob for example.  To use it, open Handbrake with your movie DVD in the drive.  In the Handbrake GUI, click on Source in the upper left and it default to /media/DVDVIDEO or something similar.  Highlight it to select it and click OK.  Below Source you will see Destination and just below that you will see File with an entry box to the right.  The box has a name already selected;  dvdvideo.m4v and that will default to the /media directory.  You can change that or just run Handbrake and rename the file later.   Below File, you will see a folder icon with  a drop-down arrow.  If you want the new iso in a specific directory, click the down arrow and select Other from the menu and then navigate to the folder you have created in which you want your iso.  Then go back to the top of the page and click Start.  It's a pretty slow process as you would image but it works fine.  If you just want to copy your files and not convert to mp4, don't use Handbrake.

If your movie files are in vob format, install vobcopy and run that.  You run vobcopy from the directory in which you want the movie copied to with:  vobcopy -m
It automatically gets data from a CD/DVD drive.

You need to indicate what the file format is on the movie DVDs for starters.  You also indicate in your initial post that you got an error message.  You didn't post it so that doesn't help.

---

### Post by SeijiSensei on 2016-03-21
I use Kubuntu with the KDE interface and suite of applications.  The K3b disc burning application can convert a video DVD to a .iso image if you have [libdvdcss installed]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"). 

I just ran a test this morning after reading your posting.  I opened the DVD with K3b and chose Tools > Copy Medium.  I then checked the box for Only Create Image and clicked on the Image tab.  The default destination is in the /tmp directory, but you can change that to the location and file name you prefer.  After it finished I now have a movie_name.iso file that plays when I use smplayer.

I also copied a DVD from a television series with multiple episodes and chapters within them.  When I opened the ISO file in smplayer, I was presented with the menu and could navigate just as I could with a DVD player.

You can install just K3b onto an Ubuntu system, but it will bring in a lot of "dependencies" with it.  Unless you're starved for disc space, this shouldn't be a problem.

---

### Post by yancek on 2016-03-21
Have you tried k9copy. K9Copy is a program that allows you to copy DVDs (and other audio-video media) in Linux from DVD to a directory on the HD.

---

