---
title: "Converting VIDEO_TS to format that can be streamed to an XBox 360 with ushare"
date: 2010-01-17
forum: Multimedia Software
---

### Post by slapnutz on 2010-01-17
Yes, this thread has an oddly specific title, but I feel if I can get it working with a dvd rip I can extrapolate and get it working with anything I need.

So on to the actual question:

I currently have an ubuntu 9.10 server running. I have a 1 TB raid 5 setup and it has a lot of DVDs on it. I typically just rip the dvds I get to either .iso or just keep the dvd structure [AUDIO_TS and VIDEO_TS]. 

I also recently purchased an XBox 360 and want to stream to it. I've got it to work using uShare, but the only video that I've seen work is one that is xvid w/ ac3 audio. The audio I feel probably isn't an issue for the XBox, but the Video I think is. 

Is anyone aware of a way to go from dvd structure to xvid [or any other format that should stream to a 360]. I can work either command line or gui, although command line is preferred so that I can batch script it. 

So far, I've tried using HandBrake, ffmpeg, mencoder, transcode, and maybe one other thing that I can't think of atm. I'm sure that it can be done with those tools, but I probably just tried to skip a step.

Thanks for any help,
~Mike

---

### Post by slapnutz on 2010-01-19
> **slapnutz said:**
> Yes, this thread has an oddly specific title, but I feel if I can get it working with a dvd rip I can extrapolate and get it working with anything I need.

So on to the actual question:

I currently have an ubuntu 9.10 server running. I have a 1 TB raid 5 setup and it has a lot of DVDs on it. I typically just rip the dvds I get to either .iso or just keep the dvd structure [AUDIO_TS and VIDEO_TS]. 

I also recently purchased an XBox 360 and want to stream to it. I've got it to work using uShare, but the only video that I've seen work is one that is xvid w/ ac3 audio. The audio I feel probably isn't an issue for the XBox, but the Video I think is. 

Is anyone aware of a way to go from dvd structure to xvid [or any other format that should stream to a 360]. I can work either command line or gui, although command line is preferred so that I can batch script it. 

So far, I've tried using HandBrake, ffmpeg, mencoder, transcode, and maybe one other thing that I can't think of atm. I'm sure that it can be done with those tools, but I probably just tried to skip a step.

Thanks for any help,
~Mike

Alright well I got this figured out today.

To anyone who may get this on google or is just interested here was my procedure:

1. Install uShare [either from source or from .deb]
1*. In Ubuntu < 9.04 I had to kill some ports on ufw, but in 9.10 I just allowed all LAN connections and it seems to have done the trick.

2. Download/Install Handbrake 0.9.3...yes it being 0.9.**3** is important. I used the XVid codec instead of H.246 (or whatever it was) because all of the working videos I had were xvid, and w/ 0.9.4, H.246 wasn't being opened by XBox. 

3. In handbrake, I used the XBox 360 preset, but changed it from mp4 to avi (xvid). 

3 (ALT). I just found out that the DVDFab (Windows only) XBox 360 option worked just as well, so I would also recommend that. 

4. Restart ushare and poof it ought to work.

Feel free to contact me if you get stuck on any of these options as this was a 4 day endeavor.

---

### Post by nerdzero on 2010-01-20
Thanks for this, slapnutz.  I have an almost identical setup and have been looking for a good solution for some time.  One question though:  Did you compile 0.9.3 from source or did you find a deb from somewhere?

---

### Post by slapnutz on 2010-01-20
I cheated. My ubuntu box is a server w/ samba. My main rig is windows. There shouldn't be a problem comipiling it from source (I would have done this if I NEEDED to do it in linux). I think I got the binary from a dvd ripping website, but a quick search of HandBrake 0.9.3 will help find it.

---

### Post by nerdzero on 2010-01-22
Hey hey, thanks to the presets from this other thread, [http://ubuntuforums.org/showthread.php?t=1350522](http://ubuntuforums.org/showthread.php?t=1350522) , I got the latest version of handbrake from the PPA able to create playable m4v files for my 360.  Thanks!

---

