---
title: "converting DVD video from PAL to NTSC"
date: 2009-05-28
forum: Multimedia Software
---

### Post by spip on 2009-05-28
Hi all,

I am trying to convert a DVD video from PAL to NTSC.  Here's what I did:

- Used dvdbackup to extract the contents.  The DVD actually wasn't encrypted, I don't know if a straight file-by-file copy from the DVD would have sufficed instead.  This gave me the typical AUDIO_TS VIDEO_TS structure.

- I then converted each .VOB file using ffmpeg like so: ffmpeg -i inputfile.vob -target ntsc-dvd outputfile.vob in the VIDEO_TS folder (replacing the old .vob files)

-  I then burned the directory structure as is.

The problems I'm seeing along with the questions I have (!!) are the following:

1.  On my playstation 3 (north american unit), when I insert and attempt to play the disc, I get an immediate error that this ps3 cannot play PAL content.  BUt all the VOB file are NTSC.  Is there some info in one of the various .IFO (or non VOB files) that indicates whether this DVD is PAL or NTSC that a dvd reader can look at to immediately determine if this DVD is supposed to be NTSC or PAL?  If so, this is something I would have to change in the .IFO file, perhaps using dvdauthor?

2.  On a european DVD player I borrowed which is able to handle both PAL and NTSC and output both as well, I correctly get the DVD intro movie.  Because I see this on my NTSC TV I know the videos were correctly converted to NTSC.  However, once I reach the main menu, *the menu navigation is entirely gone*.  I can't change the selection to any of the menu items (I actually don't even see the usual default selection) Any idea why would that be?

3.  A more overall question is, if I am not changing any of the content, number of chapters, etc, should I normally be able to burn the whole DVD as is with the original .IFO files, with just the .VOB files being different (NTSC instead of PAL) ?

I appreciate any pointers.  Thank you!
spip

---

### Post by ricardisimo on 2009-06-29
And I am trying to do exactly the opposite: extract video from an NTSC-formatted DVD and create a PAL copy. There's a twist, however... I'm extracting the video from numerous mini-DVD-Rs from our Sony Handycam. Each of these is a finalized disc, producing a DVD ISO image, with functionally one half-hour video file comprised of numerous chapters (one for each time you hit "Start" and then "Stop" on the camera.)

I have managed to extract 21 VOB files (one for each "chapter") from the first mini-DVD with dvd::rip. I imagine I will get similar numbers from the other three discs I have. The goal is to take what will eventually be four, five or six mini-DVDs and produce one regular-sized DVD in PAL format for the grandparents in Spain.

How do I do this? Do you think DeVeDe would be a good app for this purpose?

Also, I'm taking issue with the quality of the extracted VOB files from dvd::rip. On some of the videos there is some slight pauses, or lapses in the video, at least when viewing directly from the disc. The VOB files freeze up and even shut down the player at times. Any other options here?

Thanks in advance for any recommendations.

---

### Post by ricardisimo on 2009-07-01
Does no one else have one of these Sony mini-DVD Handycams?

---

### Post by mnavasuk on 2009-07-01
I hope you get to the results you want. Although I'm not an expert by any stretch of the imagination, I can tell you that maybe the framerate you're using is tripping up the player.
You might want to have a look in the handbrake help pages online [http://trac.handbrake.fr/wiki/FramerateGuide](http://trac.handbrake.fr/wiki/FramerateGuide) It's not overly technical.
And I have used kino in the past to transfer my camcorder clips to PC, but must mention that I haven't had any need to change the region at the end.
Good luck.

---

### Post by spip on 2009-07-03
Not sure how this was related to the original post!  I haven't tried the tools you mentionned.

What I was really curious to know, and the reason I started the thread, was what kind of attention needs to be given to the preservation of a the DVD files.  Can you just extract the contents of the DVD (.VOB and the various other files) and convert them to/from PAL/NTSC and just dump the file structure into a new DVD, or will you need to reauthor the DVD once the .VOB files have been converted?

---

### Post by roberto.eiberle on 2009-07-03
You can't convert mpeg compressed files such as VOB from PAL to NTSC as you cannot change neither the framerate nor the screen resolution which differ in those  two formats. Only way possible is convert to a series of individual images  take these to your editor and export for the norm you want. That's days or weeks of work so the job had better be important. On the contrary, converting NTSC to PAL is absolutely unnecessary, as any modern PAL equipment can read and display (but not copy or transform in any way) NTSC movies and DVDs

---

### Post by spip on 2009-07-04
Hi Roberto,

Not sure I follow.  Not possible to convert VOB from PAL to NTSFC?  What about 'ffmpeg -i file_pal.vob -target ntsc-dvd file_ntsc.vob' ?

Did I miss anything?

I realize it is another matter to convert the entire DVD (including menus, etc) as any offsets won't be meaningful anymore.  But for a single vob file, how is this not possible?

---

### Post by roberto.eiberle on 2009-07-04
Have a look at the differences NTSC - VOB

# Image size

    * Mpeg-1 352x240 (NTSC) or 352x288 (PAL/SECAM)
    * Mpeg-2 720x480, 704x480, 352x480 (NTSC)
      720x576, 704x576, 352x576 (PAL/SECAM) 

# Frame rate

    * coded - 24fps progressive, 29.97fps interlaced (NTSC only), 25fps interlaced (PAL/SECAM only)
    * displayed - 29.97 (NTSC) and 25fps (PAL/SECAM) 
GOP max

    * MPeg-1 18 frames (NTSC), 15 frames (PAL/SECAM)
    * MPeg-2 36 fields (NTSC), 30 fields (PAL/SECAM) 

 VOB is not a videoformat it's a container and if you change the container for a different norm but not was is inside the only result is it won't work in either PAL or NTSC. If you can get an output that exactly matches specifications, fine, I never could and been videoprofessional for years.

---

### Post by spip on 2009-07-05
I understand VOB is just a container.

I just converted part of a PAL DVD to NTSC and successfully played it in an NTSC only player.

What I did was extract the contents of the PAL DVD using dvdbackup.  I then used ffmpeg (same command line as quoted above) to encode the mpeg video contained in the VOB to NTSC still using VOB as an output container.  Using dvdauthor I created a dvd file structure to immediately play the DVD upon disc insertion (I did bring across the menus and everything) and it worked.

I understand the frame rate and image sizes are different, but I don't see why it can't be carried across.  Sure, you lose a bit on the resolution, but it works.

What do you mean then?

---

### Post by jeff.sadowski on 2010-03-07
I'm trying to convert a disk from pal to ntsc I think the original method posted may work. I will give it a try. One thing I don't see mention of how to covert the VIDEO_TS.IFO file. I think this the issue you (spip)  are having troubles with? I see it mentioned in the following post.

[http://ubuntuforums.org/showthread.php?t=1008962](http://ubuntuforums.org/showthread.php?t=1008962)

they mention that the VIDEO_TS.IFO file was written wrong by k9copy in this artical.  However since I see no  mention of VIDEO_TS.IFO I'm guessing it was not touched and may contain the original info that the disk is pal still. Once I have all the files correct what do I use to create an iso that I can burn to disk? mkisofs? or is it some other file system other than iso9660 I'd think. and then I can burn it with cdrecord right?

---

