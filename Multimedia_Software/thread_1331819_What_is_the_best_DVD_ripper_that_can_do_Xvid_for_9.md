---
title: "What is the best DVD ripper that can do Xvid for 9.10?"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Captain_Glen on 2009-11-19
Hi,

I recently upgraded to 9.10 (with a fresh install).  Most of my favorite applications now work better.

Except for one: HandBrake.  They have removed Xvid support in 9.4 and 9.3 doesn't work on Ubuntu 9.10.

I have tried DVD::Rip and Acid rip.  I found DVD::Rip too complicated and I couldn't figure out how to rip my DVDs.  With Acid rip it kept saying I had interrupted it and it stopped ripping my DVDs.  I was only browsing the web while I waited for it to finish.  How can that interrupt it?

Can someone recommend an easy to use DVD Ripper for Ubuntu that has Xvid support.  I desperately need Xvid as it I play my movies on my xboxes running XBMC.  They only have a 700MHz cpu and can't handle H.264.

Thanks.

---

### Post by Captain_Glen on 2009-11-19
I've just found OGM Rip.  It doesn't come up in the software centre if you search for DVD Rip.  But it does rip DVDs.  It looks pretty good.  It seams to do everything I need.

---

### Post by knattlhuber on 2009-11-23
Thanks Capt'n ;) That really comes in handy now that Handbrake dropped DivX.
It seemed to me though that OGM Rip is quite slow compared to HB (with the same settings): Took me 4 hours yesterday to rip a 2h movie (at 2500kbps). HB usually did that in 2 hours.

---

### Post by tgaston34 on 2010-01-22
So I am brand new to Ubuntu and linux and I am looking for a good queality DVD ripper has anyone found one you would swear by for easy of use? Thanks Tony

---

### Post by knattlhuber on 2010-01-22
Welcome to Ubuntu!
Handbrake is a good DVD ripper, but as discussed in this thread, it doesn't do avi/XviD anymore.
OGMrip can do avi/XviD and then some, and has worked reliably for me since then but as I mentioned above, it seems slower than Handbrake.
My experience with DVD:rip (sp?) and acidrip weren't that great but maybe others view that differently.

Both Handbrake and OGMrip are in the repos:
```
sudo apt-get install handbrake
sudo apt-get install ogmrip
```

---

### Post by k.mooijman on 2010-01-23
Hi 

I'm using acidrip 
i like it becouse i copy the dvd's and the iso's to an temporary folder and setup Acidrip to do a queue so i can go to bed and let my coputer rip a DVD/ISO or 4 at the time 

I'm still looking for a way to do this automatically so i just have to copy the dvd.iso to a dir and later when its don ther are only .avi videos in the dir Would be nice :)

---

### Post by JC Cheloven on 2010-01-23
Also AcidRip here. I found in it an optimal compromise between flexibility and ease of use (for my needs). And I think it's fast enough. Encoding a dvd to a ~900Mb avi takes about 50 min for me.

@ the OP: Too bad it hangs for you. I'd try to tweak a little with the settings.

---

### Post by k.mooijman on 2010-01-24
There is one thing i really would like to have added to acidrip
a possibility to edit the queue list (delete faulty entries ) so when i make a mistake in one of the entries i would not have recreate the whole queue.
the only way to delete an entry ( as far as i found ) is to wipe the queue and start over.

---

### Post by tobemem on 2010-05-09
My suggestion to create AVI, Matroska, MP4 or OGM files from DVDs is ANDREW:

[http://tobemem.memebot.com/](http://tobemem.memebot.com/)

Currently it isn't in Ubuntu repositories, but all its dependencies are.

---

### Post by Statik on 2010-05-09
I would normally swear by K9Copy, which is in the repositories, but not in the ubuntu software list. You can install it through synaptic. However, I have found that it occasionally cannot handle a dvd here and there.

Some things that I have found that help with stubborn DVDs:
1. Clean the DVD
2. Try encoding to ISO first
3. Use Gnome's DVD copy to ISO first.

Thoggen DVD rip is the only one I have found that likes ISOs as much as K9Copy.

Still struggling with one DVD tho. Its fussy I guess.

I am encoding to XVid for XBMC on an xbox as well.

Statik

---

### Post by tobemem on 2010-05-10
As input, [ANDREW]("http://tobemem.memebot.com/") likes physical DVD discs, DVD ISO image files and directories containing DVD rips created, for example, with vobcopy or dvdbackup (someone reports that the latter manages with damaged discs better); if your input is a disc, [ANDREW]("http://tobemem.memebot.com/") can alternatively work on the fly or rip the DVD to your HD first, using vobcopy.

You can choose to encode the video using XviD codec (or the other MPEG-4 ASP codec, from FFmpeg libavcodec, which [ANDREW]("http://tobemem.memebot.com/") calls FMP4 and uses by default) in an AVI, Matroska, MP4 or OGM container; [ANDREW]("http://tobemem.memebot.com/") default XviD options are for high video quality (the same apply to FMP4 e x264 options), but, if you are familiar with MEncoder, you can obtain worse (faster) or even better (slower) encodings.

If you don't use to scream at the sight of a terminal window, I think [ANDREW]("http://tobemem.memebot.com/") is easy to use and quite good at preventing you doing «stupid» things.

---

### Post by JimmyInMD on 2011-02-18
> **k.mooijman said:**
> Hi 

I'm using acidrip 
i like it becouse i copy the dvd's and the iso's to an temporary folder and setup Acidrip to do a queue so i can go to bed and let my coputer rip a DVD/ISO or 4 at the time 

I'm still looking for a way to do this automatically so i just have to copy the dvd.iso to a dir and later when its don ther are only .avi videos in the dir Would be nice :)

How do you copy the DVD's to a temporary folder to queue?  Can you give me a little more info?  Thanks!

---

