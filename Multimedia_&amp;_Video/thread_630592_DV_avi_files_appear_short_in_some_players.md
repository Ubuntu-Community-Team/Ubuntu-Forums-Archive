---
title: "DV avi files appear short in some players"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by rudlavibizon on 2007-12-03
Hi I recently noticed a problem with longer DV (PAL) clips. They appear to last only 9m27s in  MPlayer, VLC, Totem while in fact and in programs like Avidemux, Cinelerra they are much longer. These DV avi's are created in Windows and I suspect it has something to do with file system. 9m27s=567s , 567s*35Mbps is roughly 2GB. Does anyone have any solution for this? I need to make subtitles for them and this makes it  complicated.

---

### Post by Unterseeboot_234 on 2007-12-03
As I understand it, and mind you I'm just getting started in all this codec conversion, I don't have anything down concretely, but...

.AVI coming from a Microsoft environment can mean a thousand different things, because on a M$ machine .avi can have a codec that runs from the soundtrack, or it can have a codec that runs from keyframes with the whole goal being to compress the filesize. The same thing with .mov files (quicktime). Linux can only run an uncompressed Quicktime movie. The Mozilla plug-in for quicktime viewing works for the browser only, not for any of the video software.

Without having your files on my machine... I would try import and render the tracks out with Kdenlive to DV(Raw). Kdenlive seems to force clips' time "duration" and I suspect it is because Kdenlive is a frontend for ffmpeg. You could do the same conversion with just the ffmpeg command-line program (but you would have to know the options to type by reading the docs). Run short clip experiements at first. If you get "choppy" and/or frozen garbage for your results, you have to Demux. For that side trip (if it's necessary) cruise over to youtube and watch this howto:

[**DeBob filter in Avidemux**]("http://www.youtube.com/watch?v=xOGC5RkMBus&feature=user")

Okay, with DV(Raw) format you can subtract, add and multiply soundtracks. I've never added sub-titles, but it seems to me you will be authoring everything back into a movie with Cinelerra. When you're in the Cinelerra phase, keep it all DV(Raw) until you're ready to go out mpeg2 or 4 -- for that you have to use Quicktime4Linux option or let other software get you back to DVD capabilities.

I think, from what you describe, you have a fps change, a format change (ntsc to PAL) and stripping the codec. ntsc to PAL is fairly automatic. For doing the other changes, you have to gain experience with. I recall a similar timing problem and I surmounted the problem with an mpeg4 recorder before bringing the project into the Linux environment.

---

### Post by rudlavibizon on 2007-12-03
I think you're missing the point a bit here. That is, I don't really need fps change or anything like it. It's a simple PAL DV exported from Adobe Premiere. I need to make subtitles (as a separate text file) in Subtitle Editor but since it uses MPlayer (or VLC) it doesn't read the whole file.  Anyway I think you're right about ffmpeg though, I managed to solve the problem by re-encoding it with Avidemux 2.4rc3 (available from getdeb.net, the version in the repo cannot export to DV) to the same (?) DV codec. I wonder if this is a bug or just one more example of the lack of interoperability between Windows and Ubuntu. It seems that there is a 2GB limit for these kinds of files. Do you think this should be filed to Launchpad?

---

