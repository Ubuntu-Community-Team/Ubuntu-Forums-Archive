---
title: "Video sync problem - hardware issue?"
date: 2008-08-19
forum: Multimedia Software
---

### Post by sigdrifa on 2008-08-19
Hi all
I started with some video editing, and I'm running in some massive problems.

The files I have come from a DVD camcorder. The file type is vro, and vlc, kaffeine and the like play them just fine, eventhough they are around 1.3 GB.

But I had some trouble converting them into something that kdenlive can import. I used ffmpeg, and sound and video were out of sync. Some googling brought me to this command:

```

vro to avi (dvd):
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:aspect=4/3:acodec=ac3:abitrate=192 -ofps 25 -o outfile.avi infile.vro

```

That worked and resulted in a high quality avi, which again plays just fine in all the multimedia players.

I imported the file into kdenlive, and that worked, too. I just wanted a short sequence of the whole thing, since it's really just for testing yet, so I did some cutting and blending, and in the internal viewer it displays just fine.
However, when I try to export the edited video, it was out of sync again, no matter what format, quality or size I chose.

Then I wanted to try cinelerra. I couldn't import the avi, so I converted it to mpg with ffmpeg, which worked this time. The resulting mpg plays ok in the various video players. But in cinelerra's internal player it's out of sync again.

In all those situations, it was always video lagging behind.

So, now I'm wondering... could there be a hardware issue here?
Here's the configuration:
AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
2 GB RAM
Mainboard: MSI K9Neo v2
Hardy with 2.6.24-17-generic (I know it's not the latest, but that's a different story)

Any help would be greatly appreciated.

---

### Post by johnjoe on 2008-12-22
Hi
I had a similar problem with .VRO files on a DVD-RAM disk from a video recorder which I needed to edit and transfer to a DVD-R video disk. 

Below is the method I used, it may be of use to you.
I did try avidemux but had sound sync problems.

Intellistation M pro (Dual 933 Mz Intel)


Ubuntu Studio 7.10 (Kernel 2.6.22-14-rt) (gutsy) with VLC installed

Programs 
(1)vrosplit vrosplit_0.12_i386.deb(command line program)
(2)dvbcut_0.5.4_i386.deb
(3)qdvdauthor_1.0.0~rc1-0ubuntu1_i386.deb

1.I googled vrosplit and found an altair site which when translated in google gave access to a deb file and the source code. There was also instructions which I could only take a screen photo of to get a copy. I installed the deb file without problems and after working out the syntax have been able to extract to .mpg files for processing. 
2.
IMPORTANT NOTE dvbcut can work directly on the .VRO file but it needs to write an index file and will CORRUPT the file system on the DVD-RAM disk. If you copy the .VRO file to a hard drive you can then make the whole file into mpg or split it accordingly.

I am only six weeks into Linux and I could not compile the source, but I did compile it on PCLinuxOS2007 and it worked.

2. I downloaded the other two programs and their dependencies and have had no trouble so far

3. I have used qdvdauthor with the extracted file to produce DVD's that are playable on VLC and DVD players connected to TV


Also see additions to my other VRO posts

Hope this is of use

Regards John

---

