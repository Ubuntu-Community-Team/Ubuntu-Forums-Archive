---
title: "[SOLVED] CD to MP3 Help Please"
date: 2008-08-25
forum: Multimedia Software
---

### Post by bipolaric on 2008-08-25
hi people, 

I recently ripped a CD to my Hard Drive, (can't remember what program I used, it's all new to me).  The problem is that the CD has been ripped to a format called ogg, and I wanted MP3.  Are there any good FAST rippers out there that will do this ?

Thanks - Mark

---

### Post by Scunge on 2008-08-25
The already-installed application "*Sound Juicer*", at **Applications > Sound & Video > Audio CD Extractor** (or **Sound Juicer CD Extractor**) will do it, but it doesn't have MP3 installed as standard.

First, go to **System > Administration > Synaptic Package Manager** and search for *gstreamer*. Of the packages found, **Right-Click > Mark for installation** the following (and also "**Mark**" any others they ask for):
- gstreamer-0.10-ffmpeg
- gstreamer-0.10-plugins-bad
- gstreamer-0.10-plugins-bad-multiverse
- gstreamer-0.10-plugins-ugly
- gstreamer-0.10-plugins-ugly-multiverse

If they are not all there, you need to "enable multiverse repositories" and if they are all still not there (1 might be missing), you need to fiddle with the sources file directly to add exactly the additional repository you need. How to do that is covered elsewhere, but if you can't find any help, you can always ask back here.

So, having installed the MP3 codecs, go back into *Sound Juicer*, do **Edit > Properties**, click the **Help** button and scroll down to the yellow box in section 5.3. Follow the instructions there to create an MP3 profile. Restart *Sound Juicer* and select your new profile back on **Edit > Properties**.

Now when you rip CDs, you'll get them in MP3.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by mrtomservo on 2008-08-25
You probably used Sound Juicer.  If you go into Edit/Preferences then you should be able to change the format it encodes to.  You may not have an MP3 option.  If you don't, you'll need to install MP3 support by enabling the non-free repositories and downloading what you need.  You might want to install gstreamer related plugins, such as "good" "bad" "ugly". 

Oops!  Scunge just took the words from my mouth, and improved them significantly. :)

---

### Post by bipolaric on 2008-08-25
Thanks Guys, It Worked :)

---

