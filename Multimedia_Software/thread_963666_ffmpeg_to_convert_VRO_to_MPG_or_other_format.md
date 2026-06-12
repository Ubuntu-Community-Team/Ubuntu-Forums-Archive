---
title: "ffmpeg to convert VRO to MPG or other format"
date: 2008-10-30
forum: Multimedia Software
---

### Post by mateoc15 on 2008-10-30
My digital video camera creates VRO files which I understand are some variation of an MPEG.  Simply renaming the file does not work.  I am able to play the file in Movie Player, although unstable (I can't move the seek bar to a spot to go to a certain point, etc).

I'm using the following statement to convert to MPEG and it works but no audio comes through.  From what I understand the "copy" parameter just tells ffmpeg to use the same audio and video codec that is used in the input file.  Is there something else I should be doing?

The file is really long and just to test it out I'm outputting just the first one minute so I don't have to wait for a 5GB file to convert.

```
ffmpeg -i VR_MOVIE.VRO -acodec copy -vcodec copy -t 00:01:00 VR_MOVIE1.mpg
```

Also, I want to be able to get the best possible quality out of this thing.  What is the best codec to use and can you provide a command line example?  I also eventually want to burn this thing to a DVD so I guess maybe I want a VOB file too?  Any suggestions on how to do that?  The codec may be the same or different, who knows.

Thanks in advance!  I love these forums.  My life has been saved more than just a few times.

---

### Post by FakeOutdoorsman on 2008-11-01
What version of Ubuntu are you using?  Show the complete ffmpeg output of:
```
ffmpeg -i VR_MOVIE.VRO
```

---

### Post by johnjoe on 2008-12-22
Hi
I had  a similar problem with .VRO files on a DVD-RAM disk from  a video recorder which I needed to edit and transfer to a DVD-R video disk. 

Below is the method I used, it may be of use to you.
I did try avidemux but had sound sync problems.

Ubuntu Studio 7.10 (Kernel 2.6.22-14-rt)  (gutsy) with VLC installed

Programs 
(1)vrosplit  vrosplit_0.12_i386.deb(command line program)
(2)dvbcut_0.5.4_i386.deb
(3)qdvdauthor_1.0.0~rc1-0ubuntu1_i386.deb

1.I googled  vrosplit and found an altair site which when translated in google gave access to a deb file and the source code. There was also instructions which I could only take a screen photo of to get a copy.  I installed the deb file without problems and after working out the syntax have been able to extract to .mpg files for processing. 
2.
IMPORTANT NOTE  dvbcut can work directly on the .VRO file  but it needs to write an index file and will CORUPT the file system on the DVD-RAM disk. If you copy the .VRO file to a hard drive you can then make the whole file into mpg or split it accordingly.
 
I am only six weeks into Linux and I could not compile the source, but I did compile it on PCLinuxOS2007 and it worked.

     2.  I downloaded the other two programs and their dependencies and have had no trouble so far
		   
     3.   I have used qdvdauthor with the extracted file to produce DVD's that are playable on VLC and  DVD players connected to TV

Hope this is of use

Regards  John

---

### Post by johnjoe on 2008-12-22
Further to my previous post

NOTE 
I have found that if the VRO file has been edited with the original recorder it is more difficult to process.

John

---

### Post by JGT on 2008-12-23
Hi

Just to note that I have suffered almost indentical problems. The windows program Womble MPEG Video Wizard can handle the VRO files, but nothing else seems to work reliably.

Any simple solutions to convert and stabiliable the VRO files would be most welcome.

---

