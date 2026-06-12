---
title: "ID3 Tag Demuxer"
date: 2009-04-29
forum: Multimedia Software
---

### Post by ajohns95616 on 2009-04-29
I just upgraded to Jaunty, and once again, my mp3 files aren't playing. Each program I try says it needs to install an ID3 tag demuxer, and then goes looking for one, only to fail. I've looked all over as well, and I don't remember how I did it last time, or if I even had the same issue last time. If someone could point me in the right direction, that would be awesome!

---

### Post by ninjapirate89 on 2009-04-29
Have you installed the ubuntu-restricted-extras ?

---

### Post by ajohns95616 on 2009-04-29
Yeah, I did that. That's it, though.

---

### Post by ninjapirate89 on 2009-04-29
> **ajohns95616 said:**
> Yeah, I did that. That's it, though.

Sorry, that's the only idea I have. Maybe someone else will know.

---

### Post by ajohns95616 on 2009-04-29
I fixed it. One of the vast number of gstreamer plugins that I missed.

EDIT: I take it back. Movie Player and Exaile work fine. Audacity and Sound Converter still have the same issue.

---

### Post by CAsurfer on 2009-05-17
ajohns, could you please elaborate? Which gstreamer plugin contains the ID3 tag demuxer?

---

### Post by mc4man on 2009-05-17
It's probably in the 'good', which you already have.

Error messages aren't always exact, sometimes the same message appears for diff. reasons.

The main plugins
good
bad
bad multiverse
ugly
ugly multiverse 
ffmpeg
pitfdll

Note that the 2 bad and ugly versions don't replace the other, each is different

If you search gstreamer in synaptic you'll see them all, (there will be I believe 5 for bad and ugly, install the first and fourth

---

### Post by bardictiger on 2009-10-10
Could you please share how you fixed it for the benefit of others experiencing the same issue?  I'm having trouble finding any information at all about id3 tag demuxer except what it is.

---

### Post by Accelero on 2009-12-06
It really sounds like someone knows the answer to this. Could you please post?

---

### Post by stefanadelbert on 2009-12-23
I had this problem each time I opened Rhythmbox. As it turns out there were some MP3's, possibly corrupted, causing the problem. Rhythmbox lists* the files that it's struggling with, so I was able to identify those files and move/delete them from Rhythmbox's source folders and this solved my problem.

Even if you don't use Rhythmbox, I suggest setting it up and pointing it at your MP3's. This way you'll at least be able to identify those MP3's that are causing the "ID3 tag demuxer" issues.

* See Side Pane >> Library >> Import Errors

---

### Post by sohlside on 2010-01-18
@ stefanadelbert - Thx.  That was the most simple solution for me as I only had two files giving issue.

For others who have more than one or two files:
In Synaptic Package Manager find and install libid3tag0, libtag1c2a, and libtag1-vanilla.  That should handle most common ID3 tag issues occurring in Rhythmbox.

---

### Post by emyr42 on 2010-03-22
I already have  libid3tag0, libtag1c2a, and libtag1-vanilla and it still tries to find a demuxer.

I'll try some gstreamer packages...

---

### Post by zedster on 2010-03-22
The "ID3 tag demuxer" is located in gstreamer-plugins-good. 

For me, the issue was that after installing it, the gstreamer plugin registry was not updated. To check, run:

gst-inspect id3demux

This should return many details on this plugin. If it does, you should be good to go for players using gstreamer back end. 

If it doesn't find it, (as in my case), then delete the gstreamer plugin registry (located as $HOME/.gstreamer-0.10/registry.x86_64.bin in my install, Fedora Core 12) and run gst-inspect again. This should rebuild the registry.

---

### Post by dvhart on 2010-05-12
I'm still hitting this, even after installing all the suggested packages (already installed) and confirming that gstreamer has the id3 demux. Is there a bug opened?

---

### Post by HC48 on 2010-05-19
Hello,
I had all these gstreamer bits except for the **gstreamer0.10-plugins-ugly-multiverse** (2 packages popped up and I got them both.) These are needed by sound converter apparently. My MP3 files are now working in Rythmbox, VLC and Audacity. However I can't get the mp3 files I made in RipperX to work. Maybe I got the settings wrong?
H :)

Redid my mp3 files with RipperX and they now work!

---

### Post by butoyzki on 2010-05-20
yes, you are brilliant! there were some corrupted mp3s are they were all the ones causing this conundrum on my laptop! thank you so much!

> **stefanadelbert said:**
> I had this problem each time I opened Rhythmbox. As it turns out there were some MP3's, possibly corrupted, causing the problem. Rhythmbox lists* the files that it's struggling with, so I was able to identify those files and move/delete them from Rhythmbox's source folders and this solved my problem.

Even if you don't use Rhythmbox, I suggest setting it up and pointing it at your MP3's. This way you'll at least be able to identify those MP3's that are causing the "ID3 tag demuxer" issues.

* See Side Pane >> Library >> Import Errors

---

### Post by Toost Inc. on 2010-06-03
Another solution is to remove gnome-codec-install, but there's no way of telling when you might need that one again...

---

