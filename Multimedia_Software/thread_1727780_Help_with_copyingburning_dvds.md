---
title: "Help with copying/burning dvds"
date: 2011-04-12
forum: Multimedia Software
---

### Post by mystmaiden on 2011-04-12
I just got my first dvd burner and want to make a copy of each of my dvds for backup. I used Brasero and made a raw cd image but it is too big to fit onto the dvd-r I have which is 4.7GB 120 minutes. Is there some way to compress the file size to make it fit onto the disc? 

thanks,

mystmaiden

---

### Post by K_45 on 2011-04-12
Does your DVD burner support DVD+/-DL? If it does, burn those 8.5GB images to a DL disc. Otherwise, you might be able to use Wine to run DVD Shrink to shrink the disc to DVD-5.

---

### Post by inobe on 2011-04-12
[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

---

### Post by mystmaiden on 2011-04-13
Thanks for the replies. My new burner supports dual layer so I'll probably just buy some dual layer discs. I tried some of the rip programs before when I was just trying to back up my discs to a hd and they are way over my head.

---

### Post by K_45 on 2011-04-13
> **mystmaiden said:**
> Thanks for the replies. My new burner supports dual layer so I'll probably just buy some dual layer discs. I tried some of the rip programs before when I was just trying to back up my discs to a hd and they are way over my head.

 Way over your head, how?

---

### Post by dnguyen1963 on 2011-04-13
K9copy works really well.  You might also try DVD95.

---

### Post by mystmaiden on 2011-04-13
K_45 - I've only used acid rip and dvd::rip I think, but I was really unsure about bitrates and codecs, etc. I did make one copy it was definitely not a good quality one. It turned out with pixels visible and just generally funky.

dnguyen - thanks for those suggestions as well. I'll have a look at them.

mystmaiden

---

### Post by K_45 on 2011-04-13
> **mystmaiden said:**
> K_45 - I've only used acid rip and dvd::rip I think, but I was really unsure about bitrates and codecs, etc. I did make one copy it was definitely not a good quality one. It turned out with pixels visible and just generally funky.

dnguyen - thanks for those suggestions as well. I'll have a look at them.

mystmaiden

 Ah, well for XVID you'd generally want a 2-pass bitrate, keep the aspect ratio 16:9/2:35/2:40 when you resize, or leave the resolution untouched, and rip the audio track down to stereo @ 128/160kb/s mp3. Youtube has more info if you look at encoding DVD's to XVID. If you use Firefox, you can also use one of addon's to download the Youtube clip in case you need it again.

---

### Post by VanillaMozilla on 2011-04-13
Why is this so complicated?  Your burner program, Brasero, should just have an option to duplicate a disk.  Period.  You don't have to mess with ripping or anything like that.  You just do it.  Just press the button.  Or maybe a couple of buttons, but it should handle any normal CD or a DVD.

One of those Gnome burning programs -- I forget which -- is brain-damaged, however.  If Brasero won't do the job, try K3b.  It's a KDE program, but it doesn't matter.  It works flawlessly, and it WILL make an exact copy without fuss.  (Your computer will have a few extra KDE files on it, but so what?  Sooner or later you'll probably need those anyway, so you won't have to be limited to Gnome programs.)

In the worst case, if the old disk is just ever so slightly larger than the new one, then you just copy the disk to an .iso file, which I'm pretty sure K3b will also handle.  Then you can cram it onto whatever medium you can find.

Now, CD's come in slightly different sizes, for example 650 MB or 700 MB (I think that's it--I forget the exact sizes).  I can't tell from your description, but maybe that's the problem.  You can't cram 700 into a 650 bag, so just buy the 700's.  Problem solved.  But single-sided DVD's only come in one size -- 4.7, so it should work.

EDIT:  DVD-R disks hold slightly more than DVD+R disks.  Try those.  See the Wikipedia article on DVDs.

---

### Post by mystmaiden on 2011-04-14
[/QUOTE]K-5 Thanks so much for the suggestions - solid information thats very helpful! There were so many settings, etc on dvd::rip to choose from its a bit overwhelming at first.

VanillaMozilla 

While your input is truly appreciated, I'm not sure we're on the same page here. You wrote - 

> "Why is this so complicated? Your burner program, Brasero, should just have an option to duplicate a disk. Period. You don't have to mess with ripping or anything like that. You just do it. Just press the button. Or maybe a couple of buttons, but it should handle any normal CD or a DVD."That's how this all started. Using Brasero to copy the movie disc - I wound up with a 6.9 GB iso that, yep - you got it - wouldn't fit into that 4.7 GB bag. So it was back to square one, ripping and encoding it to fit it onto a standard single layer disc. For the first timer, all that can be a wee bit intimidating. I did successfully rip a dvd and make (18 hours later because in this case I wanted the best sound possible) a really nice copy yesterday but I forgot one important thing - to check the little box that allows you to render the subtitles into the movie. Since the movie is in Korean, that is definitely a problem. Part of the learning process - but an example of how a small mistake can really muck up the works. 

Additionally, according to [https://help.ubuntu.com/community/Re...ts/RippingDVDs](https://help.ubuntu.com/community/Re...ts/RippingDVDs) there seem to be a good many other factors that can complicate the issue. I haven't run into those yet but it seems like they are saying that at the stage where you attempt to burn the disc, security protocols included by the dvd makers may make more steps necessary. Am I misunderstanding something here?

---

### Post by K_45 on 2011-04-14
The security protocols are CSS, Macrovision and other encryptions which you can crack by running DVD Decryptor in Wine. Most commercial DVD's have it.

---

### Post by mystmaiden on 2011-04-14
Thanks K-5 I wondered. I downloaded ripit4me, dvd decrypter and dvd shrink but the link on the manual page was dead so I had to use a different site for instructions to load ripit4me. Unfortunately, it is not working at all. Decrypter looks like it will work, but do I Have to use ripit4me or can I use something else to create the vob and then let decrypter work its magic on that? I just fiddled with it briefly today but I couldn't figure out how to get decrypter to work with just a vob rather than with ripit4me.

---

### Post by K_45 on 2011-04-14
You do not need anything except DVD Decryptor and possibly DVD Shrink. Install Decryptor in Wine (just double click the .exe) and then (from memory) go to the Preferences menu, file splitting tab, select none. Then when you rip a DVD, it will rip in a single fat .vob file, which you can then transcode. DVD Decryptor will create the .vob.

---

### Post by VanillaMozilla on 2011-04-15
> **mystmaiden said:**
> That's how this all started. Using Brasero to copy the movie disc - I wound up with a 6.9 GB iso that, yep - you got it - wouldn't fit into that 4.7 GB bag.
You're not making sense.  You said that you want to copy each of your DVDs.  You did NOT say anything about a 6.9 GB iso.  There are only two ways you could get that size from a DVD:
1. The original was a double-sided DVD, in which case the logical method is just to copy to another double-sided DVD.  One step.  You're done.  No ISO file needed.
or
2. You ripped a single-sided DVD, and with all your subsequent work you somehow increased the size.

If your problem is to copy a double-sided DVD onto a single-sided DVD, you should say so.  I don't know why you would want to do that, but it is a very different problem from just copying a DVD.

---

### Post by mystmaiden on 2011-04-15
K-45 Again, thanks. I'm about to give DVD Decrypter a whirl, I'll post my results. 

Vanilla - > 1. The original was a double-sided DVD, in which case the logical method  is just to copy to another double-sided DVD.  One step.  You're done.   No ISO file needed.

Correct. I did not specifically say it was 6.9 GB, but I did mention it was too big for the dvd I had purchased. However, to copy one dvd straight to another, don't you need at least a dvd burner and a separate dvd player? 

I just have one, thus the need for the iso

---

### Post by VanillaMozilla on 2011-04-15
> **mystmaiden said:**
> to copy one dvd straight to another, don't you need at least a dvd burner and a separate dvd player?
No.  Both Brasero and K3b can copy directly, using only one DVD burner.  I do it all the time.  The burner program does actually make a copy on the hard drive, of course, but it does it automatically.

There's nothing wrong with creating the iso and then deleting it, but it's an extra step.  There is DEFINITELY no need to use ripping programs, create menus, etc.  That's WAY too much work.

---

### Post by mystmaiden on 2011-04-15
No joy, unfortunately with my attempt to use dvd decrypter, K-5. I don't know why this is but wine can see my dvd rom but I get 'no device detected' in Decrypter :( I made a vob with vobcopy but I can't seem to get decrypter to deal with it either.

If you do run into troubles with the security stuff, does it simply make a bad copy of the movie or will show an error before its complete (during the ripping process)? Or does it wait to tell you after you've made a shiney new coaster out of a dvd blank?

---

### Post by K_45 on 2011-04-16
Decryptor will say something, what does the log file say when you open the program? Also, in Wine, set compatiiblity to XP or 98 and run Decryptor again. That may do it.

---

### Post by mystmaiden on 2011-04-16
Wine is set to XP - with the movie in the dvd drive it shows up on the drives list 

```
F:   /media/BATTLE_OF_THE_WARRIORS
```

Decrypter Log shows - 

```
I 09:16:44 DVD Decrypter Version 3.5.4.0 started! 
I 09:16:44 Microsoft Windows XP Professional (5.1, Build 2600 : Service Pack 2) 
I 09:16:44 Initialising SPTI... 
I 09:16:44 Searching for SCSI / ATAPI devices... 
W 09:16:44 No devices detected!
```

---

### Post by VanillaMozilla on 2011-04-16
I really don't know why I bother.
[[img]http://s1.postimage.org/m3k1ofic/Composite.jpg[/img]](http://postimage.org/image/m3k1ofic/)
Click on the image to view a bigger copy.

Use a dual-layer DVD and try it.  Two clicks and you have your copy.  Is there some reason you can't do this?  You'll waste hours or days doing this the hard way.

---

### Post by VanillaMozilla on 2011-04-16
Message deleted.  Forum is semi-broken.

---

### Post by mystmaiden on 2011-04-16
Vanilla 

dual layer disc = $1.50
single layer disc = $0.75

---

### Post by VanillaMozilla on 2011-04-16
OK, that explains it.  Here they are about $.20 and maybe $.40.

But you know, you will probably waste hours to days on this.  Just so you know.  On the plus side, you'll learn something.  For a start, you probably don't need any ripping software.  You can just copy the files directly from the CD.  What you do with them after that is another nightmare.  ;)  Good luck.

---

### Post by K_45 on 2011-04-16
Set Wine to a different compatibility option, but otherwise, install DVD Shrink and see if that will open the DVD. I'd leave Wine @ XP if you try Shrink.

---

### Post by VanillaMozilla on 2011-04-18
Note to self:

Interesting about DVD Encrypter, DVD Shrink, and K9copy.  One breaks copy protection; two of them allow discarding unwanted content or increasing compression to reduce the size.  DVD Encrypter and DVD Shrink have major legal restrictions, and it may be difficult to get copies.  Wikipedia has articles on all.

---

### Post by Nutria on 2011-04-18
> **mystmaiden said:**
> Vanilla 

dual layer disc = $1.50
single layer disc = $0.75

DL costs 2x as much, but... stores 2x as much.  Thus, the unit cost per GB is the same.

So what's the problem?

Us not being mind readers, we can't deduce from the ether what you're really trying to do.

---

### Post by VanillaMozilla on 2011-04-19
She's trying to save $0.75.  I'm rooting for a software solution, but I suspect that it's a waste of time.  Testimonials to the contrary will be happily accepted.

For occasional use it would be helpful, I suppose, if there were a *simple* software solution.  Those two Windows programs promise that, although it may be illegal to distribute them.

K9copy promises that, I guess, but to put it bluntly, I'm skeptical of most Linux DVD software until I see it do the job. :(

---

### Post by penguinv on 2011-05-05
> **VanillaMozilla said:**
> You're not making sense.  You said that you want to copy each of your DVDs.  You did NOT say anything about a 6.9 GB iso.  There are only two ways you could get that size from a DVD:
1. The original was a double-sided DVD, in which case the logical method is just to copy to another double-sided DVD.  One step.  You're done.  No ISO file needed.
or
2. You ripped a single-sided DVD, and with all your subsequent work you somehow increased the size.

If your problem is to copy a double-sided DVD onto a single-sided DVD, you should say so.  I don't know why you would want to do that, but it is a very different problem from just copying a DVD.


Dear VanillaMozilla,

I'm another person who's been confused and your scold "If...you should say so." ... well I didnt know that my Ponyo disk was a double sided disk so when I asked some questions (a couple of years ago) so I had no idea how to frame the question and the OP might be in the same boat. The existence of a "double-sided" DVD only came in to my consciousness last week. (I haven't been pursuing it, admittedly.)

I got the Japanese version of Ponyo with subtitles in English (before the Disney dubbed one came out). For some "lucky" reason I copied it to my hard drive, then somehow scratched the original so it wouldnt play at all.

It's a 7.2G disk-image. I assumeded it was something like what Sega did for video games, had a way of putting more on the disk than a non-commercial user could to keep one from copying it. I didnt know about "double-sided". Live and learn I say.

How can I tell if my burner can do double sided? If it can play a double-sided disk then will it burn one? What year did that come out? 

My Ponyo disk has/had the movie in Japanese, subtitles in both Japanese and English, two kinds of Dolby sound .AND. Ponyo in Chinese.

Yes there is a dubbed Chinese language version that has stronger color. I discovered it by trying to play it on an Ubuntu without the special *DVD decoder-ring* for what we call normal DVDs. A message box told me it couldnt be played and then, it just started playing, and in Chinese. How does this happen? Why was the color different? What files are on this disk anyway? They dont show in nautilus IIR.

And so I considered that there must be a lot of extra material on the disk, more than I need just to see it in English with-or-without subtitles.  That might even fit on a single-sided disk.

I'd appreciate it if you or anyone could help me - and or correct my thinking.

Thanks,

The Penguin of V.

---

### Post by K_45 on 2011-05-06
That sounds like a standard double layer DVD, play it in VLC, and see if it works if you have libdvdcss. installed.

---

