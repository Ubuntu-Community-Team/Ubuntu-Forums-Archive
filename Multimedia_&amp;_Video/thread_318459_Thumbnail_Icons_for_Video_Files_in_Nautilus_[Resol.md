---
title: "Thumbnail Icons for Video Files in Nautilus? [Resolved!]"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by Hase on 2006-12-14
After fruitless searches here and elsewhere, I figured this out with the help of some others in a thread over at Linux Reality but thought it might be more helpful if I reposted the solution here.

On my Debian machine, I got nice little icons made from a frame in the video file when viewed in Nautilus.  I recently noticed that I do not get thumbnails from the same .xvid, .avi or .mov files when on my Ubuntu machine.  The Debian box is using Nautilus version 2.8 and Dapper is using version 2.14.3. In Sarge, all the aforementioned files got thumbnailed.

I looked in gconf-editor under desktop>gnome>thumbnailers, all the appropriate file types were enabled for thumbnailing.

I was using mPlayer to get playback but Totem would not play the file types in question, though it did play audio. To get Totem to playback video, I issued the probably excessive command:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

Now, Totem played back but still no thumbnails in Nautilus.  I had to clear out everything in /home/[username]/.thumbnails/fail/gnome-thumbnail-factory/.  The next time I entered the directory containing my videos, all the icons became thumbnails.

One thing I noticed in gconf-editor was that the command used to create the thumbs was:
```
/usr/bin/gnome-video-thumbnailer -s %s %u %o
```
Not relevant, just thought I'd include that for future reference.

Hope this helps someone else!

---

### Post by harvest316 on 2007-12-16
Very helpful.  A thousand thankyous!

I had all the codecs installed already, so it wasnt that.  I guess gnome-video-thumbnailer must have tried to generate thumbnails for my videos before, but failed, so logged placeholders for them in this /fail/ directory.  Just deleting these placeholders sorted me out.  And the good news is it didnt make gnome rebuild all thumbnails on my system, just the ones that failed.

---

### Post by nchase on 2007-12-25
This is great. Thanks for the info.:guitar:

---

### Post by electronox on 2007-12-29
Worked for me as well in Gutsy. Thanks. Now I wish my samba shares would load thumbs...

---

