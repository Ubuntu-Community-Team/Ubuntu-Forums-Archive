---
title: "Mythtv new user remote and config questions!"
date: 2008-02-14
forum: Mythbuntu
---

### Post by franck3d on 2008-02-14
Hey, everyone!  I setup my first myth box this past week and I am loving it!.
I finally bought a HDTV and since it had a digital tuner I started picking up our local stations OTA in HD.  
What better way to celebrate than building an open-source DVR!
I bought the Kworld 115, since i only needed digital tv and it's been working great!  I learned for researching (mostly here) that the remote included with the tuner wasn't working with lirc yet, so I picked up another:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16880125001]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880125001")

According to a reviewer on newegg:
 "Wow, worked out of the box! Yes, that was all I had to do. Ubuntu Gutsy, MythTV, installed LIRC and chose ""Windows MCE Remote"" and all the buttons work."

This has not been my experience.  some of the buttons work(navigation, record and whatnot) but there are some dedicated buttons on the top of the remote for Live TV, Recorded TV, Music, Videos, etc that don't function properly.
Here is (one of) my question(s):  Are there dedicated keyboard commands that I could remap these keys to or are these mythtv functions only accessible via the menu.

Also, I'm now questioning my hard drive setup.  I have a 160GB system drive and a 300GB "media drive" mounted at
 /var/lib/mythtv/recordings
so my live tv is ending up on the larger drive, but do transcoded archive videos end up on the system drive?

Is there a better way to set this up?
It sounds like .21 will have some new storage options available, should I just hold off until then?

Thanks for reading this rediculously long post!:oops:

---

### Post by Zero7 on 2008-02-15
Check if this thread is helpful [http://ubuntuforums.org/showthread.php?t=479897]("http://ubuntuforums.org/showthread.php?t=479897")

---

### Post by newlinux on 2008-02-15
You can actually setup jump points in Myth for many things, such as liveTV, Recordings, Videos, Gallery, Music, etc. You can do it from mythweb or from one of the setup menus in the frontend (I'm not at my box now, so I don't remember exactly where). Then you can use LIRC to map those keys to the jump point keys. I did this for quite a few functions.

The answer to your second question depends on how you transcode. You can definitely setup transcode jobs to archive to different locations. How are you currently transcoding and archiving?

---

### Post by franck3d on 2008-02-15
Thanks newlinux, jump points sounds like exactly what I'm looking for!

as far as the transcoding part, I'm having some strange issues.
I believed that my database was corrupted, so I rebuilt it and now burning videos to DVD is not working right.  I don't get the screen where you get to setup the dvd menu, it just jumps straight to transcoding and from the log it looks like it is trying to transcode a file that I lost when I rebuilt the database.:(

I'm thinking I might do a re-install this weekend, as I'm not that deep in yet.

---

