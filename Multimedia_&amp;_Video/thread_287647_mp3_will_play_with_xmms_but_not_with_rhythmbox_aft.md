---
title: "mp3 will play with xmms but not with rhythmbox after cp from ntfs"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by phunkizm on 2006-10-29
I've successfully added my NTFS partition to /etc/fstab and I am able to read and copy files to my ext3 partition with ease, but I've come across something that I find rather confusing..

When I copy an mp3 from the windows partition to Ubuntu, I am unable to play it with rhythmbox.  After much thought, I came to a stand-still and decided "what the heck, I might as well install xmms and see if it will play the file.."

To my surprise, xmms plays the file just fine!  Sure, I'm happy that I can finally listen to the mp3's I had save under Windows.. and sure, xmms is a much nicer player than rhythmbox anyway.. but wth is going on here?  

Does anyone else find this strange, or am I missing something obvious here?

---

### Post by phunkizm on 2006-10-29
oh well, sorry for creating another abandoned thread.  ha..  :-?

---

### Post by muggins on 2006-10-30
Rhythmbox will not play mp3 files unless you install GStreamer from add/remove applications. I was wondering about that myself earlier.

---

### Post by phunkizm on 2006-10-31
Thank you for the reply, muggins.

But Gstreamer is installed and working.

I did get the mp3 files to play, but it still makes me wonder about Rhythmbox.
It seems Rhythmbox does not want to play the mp3 files by opening them by using menu "open with", or even with command line "rhythmbox filename."  It would, however, open these files when i go to the "play queue" tab in Rhythmbox and add the files there.

---

### Post by mopar126 on 2006-11-03
I was fighting with the same prob, found this thread and tried your trick phunkizm, works fine that way. I have a separate windoze box and copied the files for that box to this one, made a folder and separated all the albums. All I can say is I need to learn more about Linux cuz, WOW it aint windoze media player.

---

### Post by Wordcrasher on 2007-01-11
> **muggins said:**
> Rhythmbox will not play mp3 files unless you install GStreamer from add/remove applications. I was wondering about that myself earlier.

Oh boy, thanks, that worked !

---

### Post by lewt on 2007-11-08
Thanks worked for me too, Cheers

---

### Post by LobbyDizzle on 2007-11-08
I am still having no luck. I installed GStreamer, do I have to run any other code in order to install the codec?

---

