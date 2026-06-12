---
title: "What do you use for your video editing suite?"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by bitterbug on 2008-01-31
I've been pulling my hair out for a few days trying to do some simple video editing, and I was wondering what other people are using for their video editing suite setups.

I've got a dual core 2.6 with 2 gig of RAM which should be more than sufficient for most editing.

What's your favorite software?


Now gratuitous history and bitching follows :)

I installed Ubuntu Studio with the realtime kernel on top of my ubuntu a while back so I could see how stable it was before hooking my dad up with it for his music composition. All in all, I haven't had any problems except when I'm attempting to edit video.

Kino just wants DV files. I can convert my video to DV but then the window has a lot of blackspace around the 320x240 video. (I'm editing videos to be posted on metacafe).

Pitivi is a bit lightweight feature wise, and crashes if I drag stuff on to it.

Cinelerra. As close to Premiere as I've found, but I have a few issues with it. I can't locate a way to add an mp3 track as audio (maybe I just need to convert to wav), it crashes randomly, it spits about quicktime errors constantly even though I'm not working with quicktime files, and I can only get it to render to raw DV files (resolution too big once again) or as ogg containers. Mpeg 4 rendering doesn't work, and the error message is useless.

Open Movie Editor: Seems like the best option so far. Repository version is way out of date and requires that video be 25fps. Converting for that doesn't seem like a bad option except that importing from the ogg container had a LOT of artifacting. I compiled the latest from source and it now has no problem loading videos with other framerates but spits errors at me that audio needs to be in quicktime format to import. Very annoying.

---

### Post by philc on 2008-01-31
> **bitterbug said:**
> 
Open Movie Editor: Seems like the best option so far. Repository version is way out of date and requires that video be 25fps. Converting for that doesn't seem like a bad option except that importing from the ogg container had a LOT of artifacting. I compiled the latest from source and it now has no problem loading videos with other framerates but spits errors at me that audio needs to be in quicktime format to import. Very annoying.

I've been using Open Movie Editor and haven't had such problems. I also built from source and can happily import files with a variety of audio. [Here's a review]("http://stream0.org/2008/01/open-movie-editor-surprisingly.html") I wrote.

My understanding is that Open Movie Editor uses FFmpeg for decoding files. So, it's probably worth installing from source the latest version of FFmpeg. You'll need to grab this from SVN. [Here's how.]("http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html")

Libquicktime is used for encoding and I also installed this from source, using the --enable-shared option during configure so that it would recognise additional libraries such as x264, libfaac and libmp3lame. Obviously these need to be installed too.

I'm pretty happy with Open Movie Editor, compared to a number of other Linux video editors I've tried. The interface needs some work, and the depth of functionality could be better, but what's there works fine and the application doesn't crash very much.

---

### Post by eye208 on 2008-01-31
Try Blender.

---

### Post by bitterbug on 2008-01-31
Blender?

Is there a Blender other than the 3D modeling and animation tool?

---

### Post by philc on 2008-01-31
> **bitterbug said:**
> Blender?

Is there a Blender other than the 3D modeling and animation tool?

The very same Blender has a thing called Sequence Editor. You can edit video with this.

[http://wiki.blender.org/index.php/Tutorials/Video_Sequence_Editor](http://wiki.blender.org/index.php/Tutorials/Video_Sequence_Editor)

---

### Post by keykero on 2008-02-01
I can honestly say that Windows Movie Maker is far, far better than any of the video programs currently available for Linux.  Shame really.

---

### Post by eye208 on 2008-02-01
> **bitterbug said:**
> Blender?

Is there a Blender other than the 3D modeling and animation tool?
The short movie "[Elephants Dream](http://www.elephantsdream.org/)" was modelled, rendered _and edited_ with Blender on Linux. The program includes not only a fully functional video editor with FFMPEG integration and HD/HDR capability but also a node-based compositor. Additionally, Blender's modelling and rendering tools can be used to create overlays, logos, subtitles and special effects. For example you can use any video clip as a texture on an object in 3D space. Want to zoom, rotate or warp video on screen? Star Wars style opening credits etc.? Blender can do it without additional plugins. And it's fully scriptable too (using Python).

It's the best video editor you can get for Linux. Why people still waste their time trying to install Cinelerra is beyond me. Maybe it's because they have no idea what Blender can do. Windows Movie Maker is not even in the same league.

---

### Post by faintscrawl on 2008-02-07
i can't get open movie editor to accept mpeg files. Is there an editing suite than can handle them? Kino can't--at least not for me.

---

### Post by faintscrawl on 2008-02-07
i installed ffmeg through synaptic pack manager and now kino is finally doing something with the mpeg.  says it's 'importing', though the file was already on desktop.  it's taking a long time.  i'll post a follow-up later ...

---

### Post by faintscrawl on 2008-02-07
kino seems to have converted the mpeg into .dv format and i can, or rather could, proceed to edit.  however, sound and vid are now out of sync!  grrr....

---

