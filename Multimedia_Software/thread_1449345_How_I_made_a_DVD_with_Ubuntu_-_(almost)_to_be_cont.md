---
title: "How I made a DVD with Ubuntu - (almost) to be continued..."
date: 2010-04-07
forum: Multimedia Software
---

### Post by texla on 2010-04-07
Here are ramblings about how tough but ultimately successful it was (I hope) to make a DVD using Ubuntu Studio from files that were transferred from another homemade DVD.  I don't have any pressing questions but I do have a wishlist on the bottom if any one has any tips on how to get them into this project, I would appreciate it. 

I have been working on two DVDs of live concert videos from an old band I was in that the video maker gave to me to use with his permission.  The main problem with them is that he did not edit between songs at all. My goal is to get them on to one DVD with nice transitions and I thought I would mention some of the things that have worked or not worked for me along the way.  

First, I copied the VOB files to my hard drive.

KDENLIVE - Edited them flawlessly.  Great transitions, no crashing (I opened it in my terminal - supposedly this helps),  But in the end I had nothing because I could not render anything in any format - did many searches for fixes but came up empty.

KINO - was next.  It transferred every VOB to DV files and then I didn't know what to do with them there so I transferred them to Cinelerra. 

CINELERRA - looked really good.  But I found out that several of the DV files transferred from Kino had the sound out of sync.  Even though I was able to sync some of them, I gave up.  I messed around with KINO some more and found out how to do the transitions I needed and liked it just fine.  But I did not like the way it converted my files out of sync so on to Handbrake.

HANDBRAKE - I took all of my files and loaded them into the Queue.  The cool thingwas that I was able to crop out a weird line at the top of all of the files and limit the resulting size of each file to a 500 GB for each file - thinking I could later cram two DVDs of files onto one.  The only bad thing was that I couldn't save them in anything but m4v files.  I needed them in DV to use them in Kino so on to WinFF. :)

WINFF - converted all of my nicely cropped m4v files into DV files overnight 

KINO - Came on strong with fast editing and transitions for all 26 songs.  It took a while and a lot of consulting with the guide to understand how transitions work and later to join the transition clips to the end or beginning of songs to make them index better on my DVD later.  But it was worth it.  Very few if any crashes - just when I tried to play with adding my own JPG during a wipe transition - crash!  Alsp, I would have liked to bring a lot of JPEGs into the video but it just hung up forever saying it was converting them to DV files that I never saw - so I stuck with the video only.

Export - I chose to export to mpeg files in DVD quality and to split every scene (song).  This takes forever (3-5 hours) but when I am done I'm going to use DVD styler to make a cool DVD.

DVDStyler - My first attempts at burning a DVD kept crashing saying *libdvdread Couldn't find device name dvdstyler* - but I found out that if I turned off the preview - voila, it worked!  But I also tried to add the error correction and that has failed.  My first test DVD was weird because it didn't like to pick all of my selections.  But I had used a Play All button and that worked great.  Then it got weird at the end of the last song, too and basically showed a merge of the menu with a still from the last song with nothing working.  So I pressed menu and I got back to the menu no problem.

So far, everything I've done with these files on Ubuntu has worked whereas I tried in vain with every piece of free Microsoft software out there and could barely budge with these files.  Now I may eventually take my cleaned up Kino Mpegs to another OS to create my DVD but I am stubborn so I will keep at this for a while first.  to be continued...

**Wishlist - **

DVDSTYLER - 1. To get background music on to my main menu
2. to add mp3 files as bonus tracks to my DVD styler layout - it doesn't seem to want to add any mp3s or wavs  just vids.  I tried using Devede and all I gor was some weird 36 MB iso (from 12 GB of DV files) - but it did pretend like it would give me those features - but DVD styler is bunbinng good DVDs right now for me...

KDENLIVE - Render anything at all from my VOB files! 


:guitar:

---

### Post by Keith1212 on 2010-04-07
i haven't done anything as extensive as what your trying to do. But i am all but satisfied with the dvd burning in linux. It seems to take for ever and i've tried at least 4-5 programs including Nero Linux. I had Mandvd working for along time then one day none of the dvds would read in my dvd player. 

So to say the least i burn my dvds on windows with nero and they burn much faster with no coasters.

---

### Post by 2hot6ft2 on 2010-04-07
> **texla said:**
> 
**Wishlist - **

DVDSTYLER - 1. To get background music on to my main menu
2. to add mp3 files as bonus tracks to my DVD styler layout - it doesn't seem to want to add any mp3s or wavs  just vids.  I tried using Devede and all I gor was some weird 36 MB iso (from 12 GB of DV files) - but it did pretend like it would give me those features - but DVD styler is bunbinng good DVDs right now for me...

QDVDAuthor may be what you're after. It's not in the ubuntu repos. but it's in the repo. for Ubuntu Ultimate Edition. I guess you could do a search and see if you can find it for regular Ubuntu.

EDIT: Here's the sourceforge page for it: [http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

---

### Post by texla on 2010-04-08
Thanks but I ran out of download and learn time so I stuck with the DVD Styler with some great results - it was finished an hour ago and it looks great!  I found out the music can be added by checking out the properties of any menu and adding a music file (in mp2 form - used audacity to convert some cool old cd trax for this) to loop in the background.  Dont know about anyone else but I had to take off any advanced features like preview or write error checking to get my dvds to burn flawlessly.  Also able to save the iso this way.  Preview was really crashing it bad.  Also when making menu buttons or song titles list I had to find the buttons to choose to point each song to - the auto feature was skipping every other song - otherwise - very nice program!  OK, hope some of this can be useful to somebody in the future... peace

:popcorn:

---

### Post by NightwishFan on 2010-04-08
I use DeVeDe to get the final ready-to-burn iso. If you check a box under advanced options it optimizes for multi core. It is in the repos.

---

