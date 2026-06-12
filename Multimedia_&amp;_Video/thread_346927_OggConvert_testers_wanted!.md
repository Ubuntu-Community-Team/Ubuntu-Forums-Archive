---
title: "OggConvert: testers wanted!"
date: 2007-01-26
forum: Multimedia &amp; Video
---

### Post by Tristan_B on 2007-01-26
Hi all,

I've written a small Python/PyGTK app which uses GStreamer to convert any old media format into Theora and Vorbis. It's basically a graphical version of ffmpeg2theora (screenshots attached!). This is basically a plea for testers -- please go out and tell me all the problems with it, so I can go and fix them!

The main selling points are:

* It's painfully easy to use: drag a file onto the source bar (or use the file chooser) and hit convert. Of course, you can also change the quality settings and the output filename if you like.

* It uses GStreamer, so it *should* be able to convert any file which Totem can play (though see "known issues" below)

* It can deal with audio-only files, video-only files, and files with many audio tracks (such as DVD rips with a commentary track).

* Thanks to the magic of GStreamer, metadata (for example, title and artist info on an MP3) is preserved

* Adheres to the Gnome HIG as much as possible

Of course, this is a brand new programme, so there are bound to be bugs. The main "known issues" so far are:

* It doesn't play at all well with the pitfdll/w32codecs for some reason that I haven't yet fathomed. Trying to convert files using these plugins causes OggConvert to hang in a fairly horrible way.

* Transcoding from certain containers (Matroska and ASF/WMV being the main offenders) will lead to very choppy audio with GStreamer 0.10.10 (the version on Edgy). This is fixed in GStreamer 0.10.11 (included in Feisty). 

* OggConvert will happily let you try and read from and write to the same file (though it will warn you that the output file already exists). Don't do this.

* I don't own the Fluendo codecs, so they're completely untested. In theory they should "just work" -- I'd be interested in hearing whether this is the case!

To use it, just unzip the attachment and run the "oggconvert" script. There's no .deb as yet, mainly because I don't know how to make one. If someone wants to put one together, I would be very grateful! It's written in Python, and so should work on any architecture: I've tested it on x86 and AMD64 installs of Edgy and Feisty.

EDIT: See post #6 for a hacked-together .deb. I'd still be very grateful if someone could package it properly!

And that's it: all comments, praise, criticism and bug reports gratefully received.

Thanks!

---

### Post by JGJones on 2007-01-27
It's stuff like this that make me keep visiting Ubuntu Forums even if I don't post much :)

Lovely one, just what the doc ordered - I'll give it a go with the Fluendo codecs - I did purchase them - they work perfectly with all the WMV's I've thrown at them so far, so that should make the wifey happy.

Will convert to ogg etc and let you know of problems.

Cheers

---

### Post by Tristan_B on 2007-01-27
> **JGJones said:**
> It's stuff like this that make me keep visiting Ubuntu Forums even if I don't post much :)

Lovely one, just what the doc ordered - I'll give it a go with the Fluendo codecs - I did purchase them - they work perfectly with all the WMV's I've thrown at them so far, so that should make the wifey happy.

Will convert to ogg etc and let you know of problems.

Cheers

Thanks -- as I say, it *should* work nicely with the Fluendo codecs, but it would be nice to know for sure.

Also, I forgot to mention that any bugs should be directed to Launchpad: 

[https://bugs.launchpad.net/oggconvert/+bugs](https://bugs.launchpad.net/oggconvert/+bugs)

Have fun!

---

### Post by Corbelius on 2007-01-27
Why you dont realize a [soundconverter](http://soundconverter.berlios.de/) for the video? :)

---

### Post by Tristan_B on 2007-01-27
> **Corbelius said:**
> Why you dont realize a [soundconverter](http://soundconverter.berlios.de/) for the video? :)

My aim with OggConvert is for it to remain as simple as possible: put any media file in, get an Ogg file out, and that's it.

That said, I've already had a request to implement a batch mode, which is something I'll give serious thought to -- if I can find a way to do it with a nice simple UI, then I will.

However, I don't have any plans to offer transcoding to other formats (for example Xvid or MP3), as Soundconverter does. Maybe in future I'll expand OggConvert into a more general MediaConvert or something like that -- but it's not on the roadmap at the moment. :)

---

### Post by Tristan_B on 2007-01-27
I've hacked together a .deb using a combination of distutils and Alien -- it's inelegant, but it works for me on Edgy.

If somebody out there who knows more about dpkg wants to create a proper package, I'd be very very grateful...

---

### Post by kircher on 2007-02-16
I've been waiting for something like this. I have been using ffmpeg2theora, which is a command line only application. It works fine, but I'd prefer a GUI. I was actually waiting for someone to make a gtk UI for ffmpeg2theora, but this seems to work fine. I have converted some files and haven't stumbled across any problems yet. Perhaps adding a queue like soundconverter, an option to automatically delete the input files, and showing the sound bitrate for the various numbers 1 - 10 would be good additions too. I worked out that 4 was 128, 5 was 160 going in increments of 32, but for other new users who don't know what "4" actually means it could be useful. Other than that, it's a good application. Nice and simple. If I find any bugs I'll forward them to the site above.

---

