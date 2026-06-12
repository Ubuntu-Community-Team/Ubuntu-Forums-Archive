---
title: "How do you burn DVD from DVD:RIP generated files"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by Wix on 2007-03-03
Newbie!!! Used dvdrip to create xxx.ifo & xxx.vob files. Files are stored on hard drive in the dvd ripped TMP (.ifo) and VOB (.vob) folders. In the vob folder, resides a number of files which represent the original dvd. When I double click on each, the video player kicks in and get audio with proper video for each file(1 gig in size). Need information on how to format these files (should only need the xxx.vob's) and merge them to burn a single or dual layer dvd. Trying to use K3B and it seems that I have a missing step to perform before I can burn the dvd.  Been digging through documentation and just can't quite put the puzzle together.

 Appreciate the help!! Thanks........

Wix

---

### Post by tagra123 on 2007-03-03
growisofs -speed=1 -Z /dev/dvd -dvd-video /path/to/your/dvd/structure/files

---

### Post by Wix on 2007-03-04
Here is the problem:   path/to/your/dvd/structure/files

It is my understanding that this path should be to a folder that contains 2 other folders (audio_ts  & video_ts).

The result of dvd::rip created a dvdrip-data folder.  In this folder there was created "moviex" folder.  "moviex" contains 3 folders: "AVI" , "TMP" and "VOB".

The "AVI" folder is empty.

The "TMP" folder contains a "IFO" folder + some other files.   The "IFO" folder contains files "vts_01_0.ifo" --------> "vts_04_0.ifo"

The "VOB" folder contains a folder "oo1".   "oo1" contains files "moviex-001.vob" ------> "moviex-005.vob" .  (when double on each file, they play a 1gig section of moviex)

So, what process do I use to create a folder that contains 2 other folders, audio_ts  & video_ts?  And what files are in each of audio_ts and video_ts folders?  Is there a routine I need to run or is it as simple of creating folders and copying files.   

Thanks Wix

---

### Post by tagra123 on 2007-03-04
You should be able to rename the vob files to mpg and then use dvd author to create the structure for you.

Depending on what you are doing there may be a better solution.

Check this link.

[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)      *** This works great especially on encrypted dvds ***

or

[http://www.debiantutorials.org/content/view/10/135/](http://www.debiantutorials.org/content/view/10/135/)

---

### Post by tinker123 on 2007-03-20
> **Wix said:**
> Newbie!!! Used dvdrip to create xxx.ifo & xxx.vob files. Files are stored on hard drive in the dvd ripped TMP (.ifo) and VOB (.vob) folders. In the vob folder, resides a number of files which represent the original dvd. When I double click on each, the video player kicks in and get audio with proper video for each file(1 gig in size). Need information on how to format these files (should only need the xxx.vob's) and merge them to burn a single or dual layer dvd. Trying to use K3B and it seems that I have a missing step to perform before I can burn the dvd.  Been digging through documentation and just can't quite put the puzzle together.

 Appreciate the help!! Thanks........

Wix

1.  Reopen your project
2.  Go to the "Transcode" tab
3.  Pick "AVI" in the upper left corner
4.  In the lower right corner hit the "transcode" button.

dvd:rip will then make you a single, large  *.avi file.

You can now go to google with the search string  "avi to dvd linux".    You should be able to get a number of step by step guides for converting a single avi file into an ISO suitable for burning to a DVD with K3B or other software that likes to start with an ISO.

Here are some I found:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/AVI_to_DVD](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/AVI_to_DVD)

[http://www.mepis.org/docs/en/index.php/AVI_to_DVD_MPEG_Conversion](http://www.mepis.org/docs/en/index.php/AVI_to_DVD_MPEG_Conversion)

---

### Post by volksolwagen57 on 2007-04-22
great! i've followed the second link you provided and it worked out fantastic. now i have a 4.5gb movie file that is ready to burn to dvd. now the only problem i'm having is that there is not a dvd out there besides one called BeAll Extreme that has up to a 4.6gb capacity. the dvds out for sale say they have a capacity of 4.7 gb when in actuality they can only hold 4.35. is there a way i can transcode to make my .avi file smaller?
i appreciate your help in advance.

---

### Post by tinker123 on 2007-04-22
I'm not sure I can help you.   

Some things are just too fat to fit onto regular DVDS.    All there is, is a windows program called "dvd shrink" that many linux people run on linux via WINE.    I tried it once a few years ago and did not get far, it may have improved since then.

The easiest, though not happiest away around this situation is simply to take only the tracts you really want.  I'm guessing you are already at that point.

---

### Post by volksolwagen57 on 2007-04-23
nah, i uninstalled k3b because it is essentially useless. i'm using tovid now and it's way better. i get my .avi files converted into .xml flawlessly. unfortunatley there is no gui, just terminal commands. also, there aren't any options, just process and burn. pretty easy though.

---

### Post by Sheik Yerbouti on 2007-04-26
Hey I am figuring out how to do this too. In my screwing around so far I have come to the conclusion that DVD::rip is not ideal for copying DVD to DVD. What you want I think is k9copy it is in the repositories (apt-get install k9copy). It will let you rip a DVD do titleset selection, audio track selection, subtitles etc.. author the dvd for you either to an ISO or directly start k3b for you and burn the resultant DVD. Seems to work a lot like DVD shrink did under Windows.

Cheers, Sheik

---

### Post by clinto on 2007-07-23
I'm using Ubuntu Feisty with Gnome and I couldn't get K9copy to work correctly. It started converting but only lasted for about 10 seconds before it told me it was finished. I checked and there was an .iso file about 1MB big. Is K9copy not gnome friendly?

---

### Post by bennyj on 2007-07-24
Install Automatix.Once installed start it up and look for DVDshrink. Install that.It does it all.rips from the original dvd and will burn a backup copy.This is by far the easiest and most reliable program i have used so far.

---

### Post by arcticFire on 2007-07-24
I found k9copy to work out of the box...

Install k9copy
-----------------
Open a terminal and type in: sudo apt-get install k9copy

Backup/Burn DVD
-----------------------
0 - Put in your DVD that you want backed up / copied
1 - Open k9copy
2 - Click File --> Open
3 - Check the uppermost box on left hand side of the TITLE window so that all boxes on tree are selected.
4 - Checked the lower righthand box 'Keep original menus' 
5- Ensure Output device is the same as your DVDRW Input device 
6 - Click DVD Copy.
7 - Go and make a cup of coffee.
8 - After about 20 mins it pops the DVD out, replace this with blank DVD disk  
9 - When finished - about another 20 mins - eject it and go and play DVD on normal DVD player.....

Hope this helps

---

### Post by izhitzza on 2007-07-26
Another way to fit the DVD on a single-layer disc can be like so:

1. use vobcopy to backup the main feature on the dvd:
    $ vobcopy -l

2. use vamps to shrink the resultant vob (let's call it here movie.vob),
    this way you will keep the first 8 audio and subtitle streams,
    you this formula to calculate the resize_factor:
    resize_factor = (size of movie.vob in Gb) / 4.6, then run
    $ vamps -e resize_factor -p -a 1,2,3,4,5,6,7,8 -s 1,2,3,4,5,6,7,8 < movie.vob > small.vob

3. and now just run dvdauthor on it to make the dvd structure:
    $ dvdauthor -o dvd -f small.vob

4. now create the ISO image for burning:
    $ mkisofs -dvd-video -V DVD_TITLE -o dvd.iso dvd

5. Now, open the dvd.iso file in nautilus (that the file browser) and burn it.

Possible problems:
        I've had the problem with VOBs when dvdauthor said SCR moving backwards, and that
         I need to remultiplex the input. If this happens... well, it depends on what you want,
         if you want to keep all audio, video, and subtitles, this may be non-trivial. Otherwise
         follow the standard transcode solution of splitting VOB into m2v and ac3. The problem
         you may get with that though, is that sometime you A/V will get out of sync. 

Alex.

P.S. the dvdauthor step, I didn't check, I think it should work, but if you have problems, check
out their site, dvdauthor.sourceforge.net.

---

