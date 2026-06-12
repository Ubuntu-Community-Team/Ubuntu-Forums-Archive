---
title: "Seeking Advice: Move Tivo Programs to Linux Box"
date: 2018-03-14
forum: Multimedia Software
---

### Post by m9ke2 on 2018-03-14
Hi all:

I have been using cTivo to move and transcode TiVo content on my 8-year old Mac laptop (1.8 GHz Intel Core i7, 4MB RAM).  It works perfectly, but is very slow on that old hardware. cTivo is a MacOS only program.

Therefore, I am exploring ways to move content from the TiVo to my Linux box (3.5 GHz AMD 8320 8 core CPU, 16GB RAM) running  17.10.

I want to 1-move the files to my Linux box; 2-decrypt/transcode into mp4; 3-automatically skip commercials

So far I have looked at:

1.  Use cTivo by running VMware+Mac OS on my Linux box.  Cons:  This requires an unlocking hack on VMware to support MacOS.
2.  Use cTivo by running VirtualBox+Mac OS on my Linux box.  Haven't really explored this much yet
3. Use kmttg on my Linux box.  Pros: requires no virtualization. Cons:  There is a thread in the Ubuntu forums by michael37 which explains how to set this up, but the instructions and software they describe date back to 2011. At the time this was written, Comskip was a Windows-only program, though there is now a Linux version, so maybe Wine wouldn't be required.

I would prefer #2 or #3 above, if possible.

So far I have not chosen a method.  I would appreciate any comments from the community that will help me decide on how best to move, transcode, and delete commercials from my TiVo content. 
And i would *especially* appreciate any comments from someone who is actually moving TiVo content from the TiVo to a Linux box!!

If you have read this far, thanks!  i would appreciate feedback and comments!

---

### Post by TheFu on 2018-03-14
Good luck.

I stopped using my TiVo-S2 a long time ago.  Back then, I used **kmttg** to get the files off it, then used **comskip** to mark potential commercial locations.  Comskip isn't perfect, so manually correcting the cut points is necessary.  **vidcutter** can read a format that comskip puts out, but it isn't very user friendly. 

A very long time ago, I purchased VideoRedo Plus which embeds a version of comskip that is better at finding commercial breaks, has fairly intuitive controls and quick cut-points. It is Windows-only but one of the 2 remaining reasons I have Windows still.

I remember kmttg being slow, but my S2 TiVo was G-only wifi and didn't support hi-def anything. I just had some patterns that pulled the files off. Didn't use any of the other settings for processing. The S2 was mpeg2, so after the commercials are removed, transcode using handbrakeCLI (or the GUI or an ffmpeg script), and you might want to use ccextractor to get captions/subtitles out and include them back in the h.264/h.265 mkv files.  The resulting files would be about 30% the size of the original.

---

### Post by m9ke2 on 2018-03-14
Thank  you for both replies!  Very informative,

---

### Post by m9ke2 on 2018-03-15
I got kmttg running on my Linux box (but no comskip yet).  It's downloading the TiVo files and transcoding them nicely, and much faster than before on my Mac laptop.  I will figure out comskip at some point, marking this thread solved.

---

### Post by TheFu on 2018-03-15
You probably don't want to transcode until after removing commercials.  Video editors really prefer MPEG2.  AVC/h.264/h.265 editors aren't frame accurate - they only cut on GOP boundaries, which aren't intuitively obvious.

However, if you don't plan to remove commercials and all your playback devices/software support .EDL files, then you could continue transcoding and let comskip make some EDL files (edit decision lists) for playback.  Kodi honors these, if the .edl file is available. Plex does not. Most commercial players do not either. mplayer and mpv do as well.

And if you want any captions (subtitles are technically different), then pulling the SRT files out after removing commercials is best.  Keep the time sync points for all those tracks correct gets harder once it isn't mpeg2 anymore.  With h.264, the only editor I've found that deals with all tracks correctly is mkvmerge.  Others seem to ignore .srt or alternate audio tracks.  Don't get me started on multiple language support!

---

