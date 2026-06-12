---
title: "Removing hardcoded subs from .MKV video file"
date: 2011-07-22
forum: Multimedia Software
---

### Post by akand074 on 2011-07-22
Hey,

Is there a way to remove subs from an MKV (x264 if it matters) that seem to be hardcoded (VLC doesn't show any subtitles so I can't remove them). I don't mind re-encoding if necessary as long as the video quality remains the same and the video image isn't actually ripped out. Is it possible?

---

### Post by papibe on 2011-07-22
Usually the term 'hardcoded subs' means that they were embedded in the video stream, so there's no way to get rid off them (thus the term hardcoded).

If VLC doesn't show a different stream for the subtitles, there's no much hope (VLC -> Tools -> Codec information).

The only thing I can think of is to crop the lower part of the video, but that maybe unacceptable for most people.

Regards.

---

### Post by akand074 on 2011-07-22
Nope there isn't. It's not a big deal, I was wondering if it was possible (like if it was layered or something but it seems in this case it would be in a different stream, which it isn't). Thanks for the help!

---

### Post by andrew.46 on 2011-07-22
Have you had a look at the file with the mkvmerge gui? It may be possible to simply uncheck the subtitle stream (and this depends if it is actually hardcoded or not) and then allow mkvmerge to remux the file.

---

### Post by akand074 on 2011-07-22
I just installed and tried that. Shows only two tracks "type: audio" and "type:video". Looks like the subtitles are hardcoded right into the video like I thought. So I imagine it is not possible to remove?

---

### Post by andrew.46 on 2011-07-22
> **akand074 said:**
> So I imagine it is not possible to remove?

I would think not, perhaps obscure them but that would be more trouble than it is probably worth.

---

### Post by doas777 on 2011-07-22
it is almost impossible to work with hard coded subs. they are embedded on the video frame by frame, so all you can do is paint over them on each frame. not very useful. 
ripping hard subs is almost as impossible. there are some tools with OCR packages built in that try, but I've never seen one worth the trouble of using.

---

### Post by handy on 2011-07-22
> **akand074 said:**
> I just installed and tried that. Shows only two tracks "type: audio" and "type:video". Looks like the subtitles are hardcoded right into the video like I thought. So I imagine it is not possible to remove?

Finding another copy that has no subs, is for better or worse the easiest/only solution providing you have enough bandwidth.

---

### Post by BicyclerBoy on 2011-07-22
Long shot but..
Could try logo removal filter in ffmpeg/mplayer..
The logo filter may require the sub-title to "static" for too many frames to be workable.

---

### Post by akand074 on 2011-07-23
> **handy said:**
> Finding another copy that has no subs, is for better or worse the easiest/only solution providing you have enough bandwidth.

^ best approach. Though it's not a big deal. I was just wondering if it was possible.

---

### Post by shantiq on 2011-07-23
yes sadly hardcoded has the word hard in it:KS

and not any means of removal

the only plus of that type of file is that you can upload to youtube and retain your subs as they cannot be stripped **also** they are really good if you want to cut a section and retain subs


otherwise it is simply a limitation of use for all other users


no tricks for that one i have read of unfortunately

---

### Post by shelbydz on 2013-04-21
For everyone that keeps coming across this thread, here's what I discovered: 

Check to see if the subtitles are part of the video file. From the command line: 
$mediainfo file.mkv | more

You'll probably see a bunch of entries that look like: 
Text #1
ID                                       : 4
Format                                   : VobSub
Muxing mode                              : zlib
Codec ID                                 : S_VOBSUB
Codec ID/Info                            : The same subtitle format used on DVDs
Title                                    : HQ White
Language                                 : English
Default                                  : No
Forced                                   : No

To remove ALL of the subtitles, install mkvtoolnix:
$sudo apt-get install mkvtoolnix

then run mkvmerge to strip the subtitles off: 

$sudo mkvmerge -S -o outputFile.mkv inputfile.mkv

Should take a few minutes, but it will take all of the subtitle tracks off. See the man pages on mkvmerge for info on strategically removing 1 or 2 subtitles instead of all of them.

I find it's pretty rare that the subtitle text is emblazoned onto the actual video. Check with mediainfo to determine if it is or not.

---

### Post by oldos2er on 2013-04-21
Old thread closed.

---

