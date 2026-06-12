---
title: "[SOLVED] How to edit metainfo in video files (Ogg Theora)?"
date: 2008-10-23
forum: Multimedia Software
---

### Post by phenest on 2008-10-23
There are many apps to edit tags in audio files but I can't find any that edit metainfo in video files. Are there any?

---

### Post by Achetar on 2008-11-17
I need this too.

64bit Intrepid

---

### Post by phenest on 2008-12-13
I found a solution:

Look at the videos properties to determine the codec for the audio within the file. Then, rename the file with an extension to match, i.e. if the audio is an mp3, rename the file to whatever.**mp3**. Then you can use a tag tool such as easytag or exfalso, et voila! Then rename the file back to what is was before.

This doesn't work for every file and some have to be guessed.

---

### Post by phenest on 2008-12-13
Ok. This doesn't seem to work for Ogg Theora videos if the audio is Vorbis. But I found this that **does** work.

[tagtheora]("http://open-source.ecchi.ca/?voir=projets/tagtheora")

I'll mark as solved.

---

### Post by phenest on 2008-12-25
It would seem that my workaround for files other than .ogv (Theora), does not come without side-effects. I will use an AVI file as an example:

File extension: .avi
Video container: AVI
Video codec: Xvid MPEG-4
Audio codec: mp3

To change the meta data in this video file, I changed the file extension to match the audio codec, i.e. .mp3. I then used an audio tag editor to change the meta data of the video file, and changed the file extension back to what it was, i.e. .avi.

The side-effect:
Although the AVI file plays perfectly with Totem, mplayer complains it does not recognize the audio codec. AviDemux, which created the AVI file in the first place, refuses to open the file complaining it does not recognize the video codec.

If I use the audio tag editor to remove the meta data, AviDemux will open the file without issue, but mplayer still complains.

I will research this further to find a solution, but I would like some technical input as to what went wrong with my workaround. Perhaps if there is no current solution, I might try to create something myself using any information I get.

---

### Post by Bramkaandorp on 2010-01-27
With the risk of being flamed for "necromancy":

Have you made progress? I don't seem to find any reference to a video editor, and I would love to use one, since I don't want to do anything unusual to the video files.

Cheers,

Bram

---

### Post by cor2y on 2010-01-27
ffmpeg and mencoder allow you to edit metadata info in video files

[http://ubuntuforums.org/showpost.php?p=8031373&postcount=5](http://ubuntuforums.org/showpost.php?p=8031373&postcount=5)

---

### Post by poikiloid on 2010-02-25
here is a great project that has an installable deb package for ubuntu that lets you edit xmp (the wave of the future of metadata) data right from nautilus, the file browser:

DigiWF

[https://launchpad.net/digiwf](https://launchpad.net/digiwf)

---

### Post by chitowner2 on 2012-05-17
This thread has gotten old, but I don't believe the core issue is solved properly, eg, how to edit metadata in video files. 

ogg/theora is simply a tiny percentage of the video arena, in fact, I've never even seen one and I have literally thousands of video files in my library.

I am currently using either 11.04 or 12.04 kubuntu. I like nautilus for it's nice icon displays of photos and vids. I typically use Gwenview and gimp for photos and VLC and avidemux for video. These tools work for most things, but occasionally, as the thread-starter said, there is a video that has wrong metadata and it is extremely difficult to edit that stuff. 

VLC has an option that purports to work in some cases, but is not reliable, so I am looking for a Swiss-army-knife solution that can handle various formats (avi/wmv/mpg/mp4/etc/etc) in the manner that exfalso does for audio files.

Is there any video geek out there in Ubu-land that has a known solution? 

Thanks,
CT
:confused:

---

### Post by oldos2er on 2012-05-17
Old thread closed; please start a new thread for your question.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

