---
title: "How to use Cowon iAudio 6 with Banshee?"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by Aleksandersen on 2006-11-22
Hi,

How can I get [Banshee](http://banshee-project.org/) (0.11.1) to recognize and allow me to synchronize with [Cowon's iAudio 6](http://www.amazon.com/gp/product/B000FJEY6M?tag2=bonaveonet-20)?

From what I have been able to gather from Banshee's Wiki pages it should have been recognized as a digital multimedia player by something called «HAL.» And it should also «just work» with Banshee.

But it does not. So how can I make the magic happen!? \\:D/

---

### Post by RAOF on 2006-11-23
From the manufacturer's page, it seems that that's a PlaysForSure device.  As far as I'm aware, that requires the (experimental) MTP support for Banshee.  I've built some packages with it enabled, but they're built for AMD64 so probably won't work for you.

I could probably add some i386 packages to my repository though, if you'd like to test the MTP support :).

---

### Post by Aleksandersen on 2006-11-23
I would really like to try that MTP package of your's, please!

---

### Post by RAOF on 2006-11-23
Ok.  There should be i386 builds of the Banshee development branch, and the development branch of libgphoto2 (needed for the mono bindings) in my repositories, distribution "edgy", section "multimedia".

Be advised, this will install the **development** version of libgphoto2 - that's the library that interacts with digital cameras, MTP devices, etc.  It **should** work, and if it doesn't it should also be reasonably easy to revert to the official versions.

---

### Post by Aleksandersen on 2006-11-23
Get: 1 [http://raof.dyndns.org](http://raof.dyndns.org) edgy/multimedia banshee-daap 0.11.2+cvs20061120-0raof1 [193kB]
Fetched 193kB in 8s (21.5kB/s)                                                 
Failed to fetch [http://raof.dyndns.org/falcon/pool/edgy/multimedia/banshee-daap_0.11.2+cvs20061120-0raof1_all.deb](http://raof.dyndns.org/falcon/pool/edgy/multimedia/banshee-daap_0.11.2+cvs20061120-0raof1_all.deb)  Size mismatch

---

### Post by RAOF on 2006-11-23
Bah.  Sorry.  I'll need to regenerate the repository indicies.  Should be fixed in a minute :)

Edit: should be fixed **now**.

---

### Post by RAOF on 2006-11-23
It might be nice to email the author (trick at vanstaveren.us) with your experiences with the MTP support (does it work, does something not work, etc).  He hasn't got a lot of user feedback, and would like to know what works and what doesn't!

---

### Post by Aleksandersen on 2006-11-24
I installed the updates trough your repository all fine.

But I still does not see my Cowon iAudio 6 (v. 1.14) appear in Banshee's source list.

So I guess it did not work. :p What should I write in the e-mail?

---

### Post by RAOF on 2006-11-25
You could check out this page: [http://tricky.vanstaveren.us/Projects/Open_Source/Banshee/MTP](http://tricky.vanstaveren.us/Projects/Open_Source/Banshee/MTP)
That might either help get it working, or tell you what he'd like to hear :).

---

### Post by felixruina on 2007-12-04
Perhaps you all have already figured this out, but I thought I would post the solution in case someone else came across this thread.

Basically, Banshee uses HAL to identify audio devices when they are plugged in.  The problem is that HAL may not have all the info on all audio devices to know to tell banshee that this is indeed an audio device.  In the case of the iaudio 6 and 7, HAL recognizes them as standard USB Mass Storage drives.  I've already submitted a patch in HAL for the iaudio 7.  I don't have an iaudio 6, so I can't send a patch for that.  If anyone does have an iaudio 6 and wants to help with that, let me know.  It won't take much info to get the patch done.

Until HAL is patched, there is another solution, thankfully.  First, make sure your iaudio device is in UMS mode (so that it acts like a normal usb drive).  Now, open it up to the root directory of the drive (e.g. /media/I AUDIO7).  You now need to create a new file in the root directory called ".is_audio_player".  Edit this file with your favorite text editor and add the following:

```
audio_folders=MUSIC/,RECORD/,VOICE/
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg,audio/x-flac
```

The first line tells Banshee where it should look for your music.  You can change these according to your tastes.  For example, I added a PODCASTS/ directory, as I like to keep podcasts separate from my music.

The second line tells Banshee what type of files the audio player can read (ogg, wma, mp3, and flac in that order).

Save the file, remount your iaudio device, and Banshee should pick it up the next time you run it.

Hope this helps!

---

### Post by Acuos on 2007-12-24
Thanks, this allowed my iAudio7 to be found by Banshee.

This may need to be placed on another thread, but I'll ask anyway.
How do I get the meta data to work in the iAudio7?  When I look at 'Artist' I only see "Unknown."  Is this were the above MTP packages will help?

---

### Post by Acuos on 2007-12-25
Update:

After upgrading the iAudio 7 to version 1.15, Ogg now shows the ID3 tag information.

---

