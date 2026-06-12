---
title: "Audio noise from DVD made by manDVD from xvid file"
date: 2008-02-03
forum: Multimedia Production
---

### Post by raj727 on 2008-02-03
I wanted to make a DVD from an xvid avi file.  I read about manDVD and then downloaded it and installed it on my Ubuntu 7.10 PC.  It was very easy to use with many neat features such chapters, personalized DVD menu, audio syncronization, etc.

After finishing, I tested the file.  The video was fine but the sound was nothing but garbled noise.  I got a similar garbled noise problem six months ago  when I tried to convert an avi file to DVD using DeVeDe.

I read there was sound problem that was caused by mencoder (I'm not sure why since I'm fairly new to video editing in Ubuntu).  The solution was posted as:

-click the link to download the archive [http://www.rastersoft.com/descargas/..._fixed.tar.bz2](http://www.rastersoft.com/descargas/..._fixed.tar.bz2) on your home folder
- extract the content
-now on the terminal type :
sudo chmod 777 ~/mplayer_fixed/m*
sudo cp ~/mplayer_fixed/m* /usr/bin/

My questions:

1)  Is this solution suppose to work with Ubuntu 7.10?
2)  I tried the first sudo command above after downloading and extracting the file but got the response that file could not be located (The file may have been extracted to the \ directory).  Have I extracted the file correctly or is there something else I should be doing?

---

### Post by raj727 on 2008-02-05
Anybody who can help?

---

### Post by gtrtx on 2008-02-05
I make DVD's from AVI files all the time and they work great.

I use this guide found here:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/AVI_to_DVD](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/AVI_to_DVD)

The only drawback is that there are no chapters and menus. Using this method I only get a simple DVD of the movie that I can watch in any player. 

I can only really answer your second question...

If you extracted the file correctly you should have a directory called mplayer_fixed in your home directory. It should contain all the files of your archives. 

After reading the README in the archive it just appears to be an older version of mplayer and mencoder(from edgy). It also includes an install script that will replace your existing files on your system. It also seems as if this was written for feisty. I'm not sure that I would even use it with gutsy(7.10)

---

### Post by raj727 on 2008-02-07
Thanks gtrtx.

I followed your suggestion on converting an avi to a DVD.  I went to the site and used the guide.  Unfortunately, I got an error in step 3 (putting the video and audio files back together).

raj@raj-desktop:~$ mplex -f 8 -o dvd_movie.mpg movie.m2v movie.ac3
   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
**ERROR: [mplex] Unable to read from movie.m2v.

Do you know what I did wrong?

BTW.  I took a screenshot of all of the steps but I can't seem to paste it into my posting.  I've tried copy and paste and also insert image but no luck.  Again, do you know what I've done wrong in trying to insert my terminal screenshot into this posting?

---

### Post by gtrtx on 2008-02-07
I'm not quite sure what went wrong. I've  never gotten such an error. 

The only thing I'm guessing it could possibly be, is if you did step 2. I normally skip this one as it is only applicable to avi files with 5.1 sound. All of the ones that I've done only have stereo sound. 

Another possibility is your version of mencoder. If you used the files you mentioned in your earlier post, you may have down-graded mencoder.  

This is really just speculation. For me it's always "just worked" One thing however.  Whenever I use the commands, I rename my avi file to movie.avi and simply cut and paste the commands from that guide. Actually now I just have a script. 

In regards to posting images, I think they need to be hosted somewhere, like photobucket or something similar.

---

### Post by raj727 on 2008-02-07
gtrtx.

I didn't use step 2 because I'm was sure the file did not have 5.1 sound.

I checked the version of mencoder and found it was the latest version.  I reinstalled it to ensure it wasn't downgraded or corrupted.  I went through the process again and got the same error message.

Would it help if I posted the results for step 1?

I notice a lot of posts where people include their terminal results after using a command.  Is that something that is done through photobucket?

---

### Post by gtrtx on 2008-02-08
Not sure how things are posted.  Maybe you could use the "Attach Files" 

I'm not sure what to suggest next. Be sure that the "movie.m2v" file exists after completing step 1. I guess you could also check it's permissions although I doubt that to be an issue. 

After completing Step 1 you should have 2 files:

movie.m2v (video)
movie.ac3 (audio)

unless you didn't rename the original avi file. Then it would have the same name name as the avi file with the above extensions.

---

### Post by raj727 on 2008-02-08
gtrtx.

I've attached the terminal printout in the attachment.

I did change the name of my file as you suggested to "movie.avi".  However, I'm not seeing any files called:

movie.m2v (video) or 
movie.ac3(audio)

I also tried using DeVeDe again, but I got the same results.  Good video but a noisy incoherent scrambled audio.

I was thinking of trying Avidemux but thought it might also use mencoder.  Is there anything that doesn't use mencoder?

Would this be something I could refer to the Ubuntu technical support (is it called launchpad?)  or to someone else?

---

### Post by gtrtx on 2008-02-08
Ahh... I see that your getting a Segmentation Fault in the first step.  That's the problem.  The first step is not completing. Normally it would be quite a lengthy process....on my system it takes about 30-45 minutes. 

When getting a segmentation fault the first thing you need to do is make sure that you don't have any hardware issues....mainly memory ( RAM).  While I say this, I have had many Seg Faults that where not hardware related, but I'm thinking if you report this as a bug,  that will be the first suggestion they give.  If I'm not mistaken, the ubuntu live CD has a utility you can use. See this here:

[https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

Unfortunately a segmentation fault can be difficult to trouble shoot. However...as it states there is a "core dump". Usually this is a file that gives more information for the cause of the error. Where it puts these I'm not sure. 

Later if I have time, I will check more into this. 

Sorry I can't be of more assistance.

---

### Post by raj727 on 2008-02-08
gtrtx.

Thanks for your help.  I've started the memory test by going back to the grub menu and selecting the memory test.  I think I did this before but found it took so long I aborted it.

The first step in your program didn't take more than a second to run on my computer.  I should have mentioned that earlier.

I do have a second computer with Ubuntu 7.10 on it.  I'll try to run your dvd program on it tonight and see what happens.  At least we'll know if it's a problem specfic to my first computer or not.

Thanks again for you help.

---

### Post by gtrtx on 2008-02-08
No problem.

I wish I had more to offer in the way of a solution.

Let me know how the other computer works.

---

### Post by raj727 on 2008-02-09
gtrtx.

I started the memory tested but after 12 hours it was still not complete.  The program was memtest 86+ V1.70.  It was indicating Pass 72%, Test 43 % and Test # 7.  It also indicated Pass 7 and Errors 0.  I decided to stop the test because I needed to transfer an avi file to my other computer.

How long is the test supposed to take?  Should I run it again?

I tried your avi conversion program again on my other computer.  It failed again.  I've attached the terminal print-out.  i think it's similar to the results from my first computer.

I also tried DeVeDe again and got the same results of good video but loud incoherent noise for audio.

I have a "Matroska" video file which comes with the ".mkv" extention.  I understand this another codec but is open source.  Do you know if there is another program that would convert this fie to DVD?  It wouldn't help solve my avi to DVD problem but it might indicate I don't have a hardware problem? 

Any suggestions would be much appreciated.

---

### Post by gtrtx on 2008-02-09
Raj, 

Just for the heck of it, I tried to convert an avi to DVD. 

GUESS WHAT?

I got the same Segmentation Fault. 

I suspect that this needs to be filed as a bug report or something needs to be changed in the parameters of the commands. 

I know I just converted an avi to dvd just last week and it worked fine, however there have been some updates since then.

I'll look into it and let you know what I find.

---

### Post by raj727 on 2008-02-09
Thanks again gtrtx.  I'd love to know what the problem is.

---

### Post by gtrtx on 2008-02-09
Well,

Now it looks like I'm in the same boat as you....and probably others.

I suspect some update messed something up....not really sure. 

However, I'm encoding with avidemux right now....and so far so good. 

If I'm successful getting a playable DVD, I will definately let you know how I did it.


You can get avidemux from the repositories, and I found a guide to use it for creating dvds here:

[http://www.avidemux.org/admWiki/index.php?title=Converting_to_DVD](http://www.avidemux.org/admWiki/index.php?title=Converting_to_DVD)

hopefully this will work well....right now it's converting and appears to be a lengthy process...however...doesn't look as if it's going to take as long as the other guide I used. 

I'll keep you updated......we will find a solution....no worries

****EDIT******  at this point I wouldn't worry about testing the RAM. Especially since it's happened on 2 of your systems and my system. My RAM is pretty much brand new. While it could be a remote possibility....I really doubt it.

---

### Post by gtrtx on 2008-02-09
Well,

Good news. 

Avidemux works really well.

However, it really doesn't seem to be any faster than the other method I linked to. It did produce a very good dvd and there alot of options. Probably can be tweaked to better suite your needs if you wanted. 

There is an interactive guide here:

[http://mulder.dummwiedeutsch.de/etc/adm_wink/avi2dvd.htm](http://mulder.dummwiedeutsch.de/etc/adm_wink/avi2dvd.htm)

This produces the mpg file. I then followed step six of the original guide, changing file names where appropriate. 

Hopefully this will help you get started. 

Let me know if you have any problems or questions. If you do run into difficulties, run avidemux from the command line so we can see any errors that may arise.

Good Luck!

---

### Post by raj727 on 2008-02-10
I think I have good news.

I've used Avidemux and created a .mpg file which has good video and good audio.  This may be a stupid question but would I use QDVDAuthor to create a DVD for the .mpg file?  I'm guessing there's still a couple of steps that I need to do before I create an iso image for burning on a DVD.

---

### Post by gtrtx on 2008-02-10
Qdvdauthor should work. I know very little about it except that it is a front end for dvdauthor.  I messed around for it a bit and it looks like it will work fine.  It actually looks like you could add menus and all of that fun stuff i you where inclined. 

As  I mentioned in my previous post, I just used step six of the original guide that I posted:

create a file named dvdauthor.xml in the same directory as the mpeg file that you generated. The dvdauthor file should contain the following:

```
<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>
```

make sure the "vob file="dvd_movie.mpg" matches the name of your mpeg file. 

Then in a console, go to your working directory and type the following:

```
dvdauthor -x dvdauthor.xml
```

this will generate the DVD files and directories.  You can use a program like k3b or Braseo to burn to dvd...or you can simply do:

```
"growisofs -Z /dev/dvd -dvd-video DVD/"
```   

you may need to change the name of your dvd burner. ie: mine is /dev/hda

That is all you need from there. If your mpg file came out good, the bulk of the work is done. Now you just need to author the dvd.

***EDIT:  The above steps don't create and iso file. They simply create the DVD directory structure that include the VIDEO_TS and AUDIO_TS files.  I suspect you could use genisoimage  to create an iso image if you wanted.

---

### Post by raj727 on 2008-02-11
gtrtx.

Thanks for the instructions.  I should have looked a little more closely at your earlier post where you suggested using step 6 of the guide to create a DVD.

I've been using a small avi file (90 meg) to work with.  This was so that I didn't waste a lot of time creating a file that didn't work.  I thought I would try ManDVD to create the DVD to see if it would work with the mpg file that I created with Avidemux.  I was familiar with ManDVD because I had used it before.  It also created a file that I could test before having to burn a DVD or creating an ISO file. 

It worked!!!

I then decided to convert a larger file (1,000 meg).  I used Avidemux to create an mpg file.  I tested it after creating it and it worked as before.  I then used ManDVD to create the DVD.  It first created a file that I could test, which worked.  I then attempted to create an ISO that I could test before burning a DVD.  The size of my avi file caused two problems.  I long conversion time and the use of a lot of harddrive space.  I had forgotten how little space I had remaining on my harddrive (or at least the partition I was using for Ubuntu).  The original output mpg file (3.8 gig), a gibvideo0.mpg file (4.2 gig),  DVD audio TS and video TS files (4.2 gig) and an ISO file (2.0 gig) combined to max out my harddrive.  This created an incomplete ISO file of only 2 gig.  I then had go in and delete files to create more space on my harddrive.  All this took a lot of time.

One thing I noticed with my larger avi file was that the subtitles in it did not get into the final test file.  I'm now looking to see how I can keep subtitles.

Another thing I noticed was that an mkv file I had, did not work with Avidemux.  I had the latest stable version (2.3) but only a newer (unstable?) version (2.4) would convert mkv files.  Maybe after I get comfortable with converting I'll try version 2.4.

Thanks again for your help.  I may not be able to get back to it for a couple of days but I'll let you know it it went.

---

