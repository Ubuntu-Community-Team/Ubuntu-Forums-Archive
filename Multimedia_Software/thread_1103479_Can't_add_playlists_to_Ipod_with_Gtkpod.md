---
title: "Can't add playlists to Ipod with Gtkpod"
date: 2009-03-22
forum: Multimedia Software
---

### Post by ahorne12 on 2009-03-22
Hi potential problem helper(s),

  I own a 4th Generation Ipod, Model M9282LL.  I've been trying for ages to get my ipod current with my new music, ever since I made the switch to Linux.  I'm working off of Hardy Heron, with Gtkpod 0.99.12.  Most of the tips for working within these programs are for older gtkpod versions, and nothing seems to work anyways. 

   So basically, my music directory has numerous subdirectories, each of which is a particular album.  Each subdirectory then is entered on my ipod as a playlist...that's how I set it up when I was on windows, with Itunes.  I'm trying to keep a similar level of organization here.  I can make a playlist on Local in Gtkpod with no problems, but when I try to drag that playlist into my Ipod, I get the following error message for each song within the playlist:

Music directory not found: '/media/ANDREW J__/iPod_Control/Music' (or similar).

(Andrew J_ being the name of my ipod)

When I explore the device itself, I can't even find the music directory - there are only /Device and /Itunes in /iPod_Control, but I can't even add another directory to make a /Music directory here (if that's what I need to do).

Also, I don't know if this is part of the problem, but whenever I eject the Ipod (by right clicking on the desktop icon), it doesn't appear to completely disappear from the /media directory - so for example today I've plugged and unplugged my iPod three times trying to figure out how to add songs, so now I have three Ipod mounts in the filesystem /media directory.  

Am I completely up the creek on adding music to my ipod?  Is there something I'm overlooking?  I'd be willing to reformat my Ipod and start over if that's an issue.  Please help.

I settled on gtkpod because I can't get anything to work with Rhythmbox or Amorok (plus I organize my music within playlists, and I gather you can't do that with these programs?).  If there's an easier way with another program I could try that instead, but I've gone down that road so many times, thinking another program would be easier, that I'm quite skeptical of that.  From what I read, gtkpod should work perfectly fine...


Thanks in advance,

Andrew

---

### Post by PrinceArithon on 2009-03-22
I don't know how open to suggestions you are about what program you use for your ipod, but I use Amarok which it works really well.

Here is a tutorial on how I got it to work.

[http://maketecheasier.com/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/2008/03/10](http://maketecheasier.com/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/2008/03/10)

By the way don't worry if you can't find both of those packages it says to download.  Just download whichever one you can.

---

### Post by ahorne12 on 2009-03-23
I've tried Amarok before, with no luck.  But I also haven't seen this link, so I thought I'd give it a try.  I ran into some problems along the way though:

1.  When I tried entering the following command into terminal:~$ sudo lsusb -v | grep -i Serial

It returned...none of which is a 16 letter serial number

  iSerial                 3 000000F1724C
  iSerial                 1 0000:00:02.1
  iSerial                 3 000F7J900154
  iSerial                 0 
  iSerial                 1 0000:00:02.0

2.  When I took the first one as my ipod Serial (12 letters), and tried to make a SysInfo file on the Ipod (as it didn't have one), it wouldn't let me save it to the Ipod, saying it was a read-only device.

  Maybe that's the problem, that my Ipod thinks its a read-only device.  But I'm not sure how to remove that restriction.  It's not checked on the "read-only" emblem when I right click on the device and search the properties.

---

### Post by PrinceArithon on 2009-03-23
Yeah if you are having that type of problem then I don't know either.  I believe you'd have to chmod something or another...but to be honest I have no idea what..

---

