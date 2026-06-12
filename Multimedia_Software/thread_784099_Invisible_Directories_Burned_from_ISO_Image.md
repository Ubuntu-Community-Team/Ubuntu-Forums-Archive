---
title: "Invisible Directories Burned from ISO Image"
date: 2008-05-06
forum: Multimedia Software
---

### Post by dstampf on 2008-05-06
Hi

I have 3 systems running Hardy Heron and see this on all 3 - a dell, a homebrew and a dell laptop.

I rip a DVD using K9Copy - this appears to be successful. I can mount the ISO image and I see the video_ts & audio_ts directories and the correct files within.

If I burn a DVD either from the ios by right clicking the file or using a program like Brasero, I don't get any error messages. Brasero checks the write and is happy.

If I play the DVD on a regular DVD player, there is no problem - it plays fine, all of the menus work, etc.

However, if I put the DVD on any computer - Mac, Ubuntu, Windows nothing happens. The disk shows up (df -k) as having the right size, the but top level directories - video_ts & audio_ts are not visible on any of the systems. If I "cat" the mount point, I see the words video_ts and audio_ts, but it appears as if the directory is not properly formatted for any of the computer systems (but is it ok for the desktop player).

Any suggestions about how I can make a disk playable on a computer would be appreciated.

Dave

---

### Post by alegallo on 2008-06-17
Almost the same problem for me.

I acquired a 1-hour DV avi file from my Sony videocamera using Windows XP.
I cut the unwanted parts and converted it in .mpg using Avidemux2.
Then I made a nice :) menu with ManDVD, produced all standard folders, and also an ISO image of the same. 
Mounting the image on Hardy works fine, although it is reported as CD and not DVD (I guess it's my fault, but it works nonetheless). 
VLC reads the menu and all the rest, skips chapters flawlessly, music plays OK (it is a concert of my choir).
Then I buned the image file to a DVD+RW using Brasero, all OK.

When I put it in a stand-alone player it works, with menu and so on.
I tried to play it on Win XP, and it only sees an empty media.
Tried it back to my 64-bit Hardy, and it works.
Tried it in another PC, with a host Win Xp and a guest 32-bit Hardy under a xVM Virtual Box machine: it works under Ubuntu, but looks empty under Windows.
That's weird!

The problem is that I need the DVD to be copied, because I will have to pass it to the other choir members.

I really can't understand it, any help would be greatly appreciated.

Alessandro
Florence, Italy

---

