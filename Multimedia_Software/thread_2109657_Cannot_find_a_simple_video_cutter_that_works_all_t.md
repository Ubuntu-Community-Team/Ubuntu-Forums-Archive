---
title: "Cannot find a simple video cutter that works all the time"
date: 2012-11-10
forum: Multimedia Software
---

### Post by twelve17 on 2012-11-10
> **michael37 said:**
> Just want to say +1 for ProjectX which has performed magnificently when using the latest version.

I use ffmpeg or mkvmerge to mux after projectx demux -- mplex fails too often.

Do use latest version of ProjectX though -- it's not available in repositories. More details (and vote for this bug) at [https://bugs.launchpad.net/ubuntu/+source/project-x/+bug/892671](https://bugs.launchpad.net/ubuntu/+source/project-x/+bug/892671)

I second this but will add one caveat.  I was working with a large mpeg TS file (~ 12GB).  Originally, I was just using ProjectX as a way to convert/demux the TS (doing its cleanup magic), then muxing the result with ffmpeg, then bringing it into avidemux for cutting.  

However, once in avidemux, I saw that the a/v eventually did get out of sync further into the clip.  

So, approach #2 as to do rudimentary cuts in ProjectX, ffmpeg mux the result, then bring in the rough cut file into avidemux, but still no luck.  

Thus, I changed the procedure again-- this time using ProjectX to do more refined cuts, which is a PITA, but I was curious about the outcome.  Unfortunately, the audio was *still* out of sync when it eventually got to Avidemux.  

What eventually became my a-ha moment was using an option in ProjectX (a button in the "Cut Points") which turns each cut into its own "collection".  Then, in the ProcessWindow, enabling the "process all collections" and "create collection number as subdirectory" options.  This makes ProjectX create separate sets of demuxed files for each cut.  I muxed each one together using the same ffmpeg command as originally, then brought all clips together in avidemux using the "append" feature.  For whatever reason, this approach kept a/v sync in all the files.  I presume there must be something that ProjectX is doing differently when it writes each cut as a file set vs. making a single file set with the cuts put together, or maybe avidemux is just not good at handling the resulting PS stream if it's one big large file.

EIther way, finally: hooray, a/v sync heaven!!

---

### Post by johnaaronrose on 2013-01-25
I've tried running avidemux 2.5.4 on the original .ts file & the .mpg file produced by using ProjectX followed by mplex - f 8. In both cases on an approx 4GB file, it gave a window displayed 'Could not open file'. I suspect that this could be due to not having the latest version of avidemux (i.e. 2.6.1) installed. Or perhaps it could be due to my using Precise 32 bit on a 4GB PC. Anybody cast any light on this?

---

### Post by johnaaronrose on 2013-01-28
Avidemux works fine. I installed it by removing avidemux and then following instructions at
[http://handytutorial.com/install-avidemux-2-6-in-ubuntu-12-10-12-04/](http://handytutorial.com/install-avidemux-2-6-in-ubuntu-12-10-12-04/)

It doesn't seem a good idea to me to put the version in the package name. It will cause confusion if Canonical put this version on their repos.

---

### Post by johnaaronrose on 2013-01-28
> **johnaaronrose said:**
> Avidemux works fine. I installed it by removing avidemux and then following instructions at
[http://handytutorial.com/install-avidemux-2-6-in-ubuntu-12-10-12-04/](http://handytutorial.com/install-avidemux-2-6-in-ubuntu-12-10-12-04/)

It doesn't seem a good idea to me to put the version in the package name. It will cause confusion if Canonical put this version on their repos.

I spoke too soon. avidemux 2.6.1 allowed me to append the second part of a movie to the first part,  and to save the full movie under a different name. However, ProjectX did not produce an audio (e.g. mp2) file though it did produce the video file (.m2v).

---

### Post by merc82 on 2013-01-28
johnaaronrose, I found mplex was only useful to mux .mpg files not .ts files. I have good success editting my ATSC source .ts files if I;
-run the .ts file through Project-X. This step is necessary for me to correct errors due to ATSC reception errors. Without this step I get audio sync problems. The latest version of Project-X works much better than the version in the repository.
-mux the .m2v and the audio file with tsMuxeR. The audio file for ATSC source is .ac3 not .mp2 like you get with a .mpg file.
-edit the muxed file with avidemux 2.6.

If you look around the avidemux forums you'll find the author stating 2.6 isn't a direct upgrade for 2.5. If I recall 2.6 is better to edit .ts files because it works on the timecode while the older version cuts based on frames. Avidemux 2.6 works much better for me to keep ATSC sourced .ts in audio sync.

---

### Post by johnaaronrose on 2013-01-28
> **merc82 said:**
> johnaaronrose, I found mplex was only useful to mux .mpg files not .ts files. I have good success editting my ATSC source .ts files if I;
-run the .ts file through Project-X. This step is necessary for me to correct errors due to ATSC reception errors. Without this step I get audio sync problems. The latest version of Project-X works much better than the version in the repository.
-mux the .m2v and the audio file with tsMuxeR. The audio file for ATSC source is .ac3 not .mp2 like you get with a .mpg file.
-edit the muxed file with avidemux 2.6.

If you look around the avidemux forums you'll find the author stating 2.6 isn't a direct upgrade for 2.5. If I recall 2.6 is better to edit .ts files because it works on the timecode while the older version cuts based on frames. Avidemux 2.6 works much better for me to keep ATSC sourced .ts in audio sync.

Can Avidemux 2.6 cut out parts of a movie e.g. previous TV programme end & adverts at start of movie?

 I'm using ProjectX (version 0.91.0) installed from the yaVDR Team's repository. Could you tell me the best place to download tsMuxeR? I don't see it in Precise's standard repos.

---

### Post by merc82 on 2013-01-28
Yes, Avidemux 2.6 can cut your .ts files for you to remove commercials. That's all I use it for. With Avidemux 2.6 you must perform your cuts (at least your input cut) on an i-frame. Just to be safe I only cut on i-frames.

You can find tsMuxeR here: [http://www.afterdawn.com/software/audio_video/video_editing/tsmuxer_linux.cfm](http://www.afterdawn.com/software/audio_video/video_editing/tsmuxer_linux.cfm) . You'll need to give the two executable files permission to be run as a program.

tsMuxeR hasn't been updated in quite sometime but it still seems to be recommended based on what I read in the doom9 forums.  It's also recommend as part of the video encoding package "Hybrid" ([http://www.selur.de/licence](http://www.selur.de/licence)).

You could try just using Avidemux 2.6 without Project-X and tsMuxeR. When I've done this I've had mixed results with regard to audio-synchronization. In my case this is a function of my signal reception and my tv tuner card. You may have consistently error free recording that allow you to only use Avidemux.

If you are compressing your recordings (with xvid or x264, for instance,) your audio-sync issue may only appear in the compressed file (the .avi/.mp4/.mkv) even though the edited .ts file looked good. I got caught by this a few time so now I run everything through the three programs.

---

### Post by johnaaronrose on 2013-01-28
I've downloaded tsMuxeR, installed it (by extracting the file, putting the executables in /opt & creating a Launcher for the GUI one). When I start it up I've specified the .m2v file (created by Project-X version 0.91.0.04 using the .ts file). However, it won't allow me to specify the .mp2 file (created by Project-X using the .ts file). I noticed that you said that "The audio file for ATSC source is .ac3 not .mp2 like you get with a .mpg file.".  My source was UK Freeview terrestrial transmission which is DVB-T. I haven't seen any setting in Project-X to specify an .ac3 file. Is there one or is there something else that I should do?

---

### Post by merc82 on 2013-01-28
I've used tsMuxeR with NTSC recordings as well. These are .ts with mp2 audio and they work fine.

When you say "it won't allow me to specify the .mp2 file" is this because the add file dialog doesn't include .mp2 as a supported file? If this is your issue just drag and drop the .m2v and .mp2 files or use the add file dialog and specify "all files".

I don't know what the DVB-T standards are but you could check the original file with mediainfo to determine if the audio is MPEG or AC3. If it's MPEG don't try to make it AC3.

---

### Post by johnaaronrose on 2013-01-29
> **merc82 said:**
> I've used tsMuxeR with NTSC recordings as well. These are .ts with mp2 audio and they work fine.

When you say "it won't allow me to specify the .mp2 file" is this because the add file dialog doesn't include .mp2 as a supported file? If this is your issue just drag and drop the .m2v and .mp2 files or use the add file dialog and specify "all files".

I don't know what the DVB-T standards are but you could check the original file with mediainfo to determine if the audio is MPEG or AC3. If it's MPEG don't try to make it AC3.

I can add the .mp2 file using "All files" but it seems strange that "All supported files" doesn't include .mp2.

I checked the original .ts and both video & audio are MPEG.

tsmuxer doesn't seem to include an option to create a .mpg file. Am I missing something?

---

### Post by merc82 on 2013-01-29
> **johnaaronrose said:**
> I can add the .mp2 file using "All files" but it seems strange that "All supported files" doesn't include .mp2.

I checked the original .ts and both video & audio are MPEG.

tsmuxer doesn't seem to include an option to create a .mpg file. Am I missing something?

If you've got the .m2v and .mp2 files added mux them now and save as .ts. Don't worry about the lack of an option to save as .mpg. 

TS (transport stream) is an MPEG2 used for broadcasting. If you were manipulating an MPEG2 from a DVD that would be PS (program stream) even if the file isn't .ps.

I still recommend you experiment with an untouched .ts file and by-pass Project-X and tsMuxeR and go straight to Avidemux 2.6. In my case I use Project-X because it performs error correction on the .ts file due to reception issues. Your reception or tv-tuner may be superior to mine.

In Avidemux 2.6 set "video output" and "audio output" to copy; and "output format" to MPEG TS muxer.

---

### Post by johnaaronrose on 2013-01-29
I've deviated from my original purpose, which was to convert the .ts to an .mpg since I couldn't find any Android apps (to run on my tablet) which would play my TV's recorded .ts files. I thought that I would have more success with Android on playing .mpg. Then I started reading about syncing of video & audio and editing video files. My TV tuner is soso being Kogan.  But I'll try Avidemux on its own. II'll then use HandBrake to create m4v or mkv files & see if they'll play on Android.

---

### Post by merc82 on 2013-01-29
Try changing the extension from .ts to .mpg. As I said .ts is MPEG2 so you may not need to do any of this.

---

### Post by johnaaronrose on 2013-02-01
When I rename the .ts to .mpg, my Android tablet's video player (and other Android apps that I've tried often have problems with it just like when it was a .ts). 

With avidemux 2.6 installed, it appears to keep video & audio in sync when saving to .mpg or .avi. However, sometimes it refuses to create a .mpg when reading a .ts. So I'm using ProjectX & mplex successfully then to create a .mpg.

---

