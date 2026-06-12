---
title: "gnomad2 stopped working to manage Creative Zen Micro"
date: 2010-05-01
forum: Multimedia Software
---

### Post by Barbalras on 2010-05-01
Hi everyone!

I'm using ubuntu karmic 9.10. I used to transfer songs to/from my Creative Zen Micro (firmware 1.11.01) using gnomad2 2.9.4 with no problem at all. Suddenly it stopped working. Gnomad2 seems to detect the zen micro but it hangs when "retrieving metadata from jukebox". The zen micro doesn't appear in "places" menu but I'm not sure whether this is an issue...

when I enter lsusb in a terminal it gets
Bus 001 Device 004: ID 041e:411e Creative Technology, Ltd Zen Micro

so it's detected...

I tried reinstalling gnomad2 but it didn't do any good

any ideas? thanks in advance

---

### Post by RTrev on 2010-05-01
What I normally do with things like cameras, GPS devices, and so on, is just treat them as a mass storage device.  I can copy files back and forth, delete, etc.  And that's normally all I want to do.

I plug them in, with no special software, and they show up the same as a USB thumb drive.

Don't know if that's possible in this case, but I hope the idea helps.

---

### Post by Barbalras on 2010-05-01
hi!

Thanks for the input but unfortunately the zen micro doesn't appear as a mass storage device. In fact, when I plug it I have no popup in ubuntu asking me what application do I want to use to open it. lsusb has it, though (?)

no clue what's happening

---

### Post by RTrev on 2010-05-01
Is it possible that the "Gnomad" software you spoke of is interfering in some way?

Are there any settings on the device itself related to USB?  For example, I have a cell phone which has three settings, Music Sync, Mass Storage, and one other I forget.

Can't think of why your device wouldn't at least show up in Nautilus, unless one of the above it the problem.

Sorry..  maybe someone smarter (which is darn near everybody) will show up. <g>

---

### Post by Barbalras on 2010-05-01
Settings are just fine, it was working last week with the very same configuration.

Some more evidence: some times gnomad2 gets through the "retrieving metadata from jukebox" dialog and I can see my music in it. But when I try to transfer some songs they don't get transferred to the zen micro.

---

### Post by TracyO on 2010-05-02
I've been having a lot of trouble with Gnomad and my Zen Sleek lately.  I think things were fine in 8.04...  I'm currently using 9.04 and Gnomad 2 2.9.1.  If nothing else, it's good to know it doesn't seem to be getting better with the Ubuntu upgrades.

Someone else posted on another thread that if you plug in the Zen to the USB, log out of Ubuntu and log back in, then open up Gnomad, it works.  So far, that's been helpful, but now I'm having the same problem you are where it's not transferring files.  

When I was having issues the first time, I tried to add files like a mass storage device, and it didn't work.  

The device says it is Docked.  

So far, I haven't gotten RhythmBox to scan it.

---

### Post by Barbalras on 2010-06-30
bump

---

