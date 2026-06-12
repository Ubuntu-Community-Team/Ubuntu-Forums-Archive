---
title: "M4P music files to work in Linux"
date: 2016-03-03
forum: Multimedia Software
---

### Post by Paul_Alexander on 2016-03-03
Can anyone throw me a bone about how to convert hundreds of my itunes m4p music files to drm-free? Been a week and I cannot find a single linux-based solution to help me. Other than buying a Win or Mac OS so I can try some of the tools advertised to convert these, any suggestions? I've already tried opening these songs on my itunes account on win xp and trying the download which should remove the drm, but no go. My files are pre-'09 so I'm guessing not supported to remove the drm in this fashion. I also tried burning them to CD and then ripping them via itunes, but no go either since it simply rips the files as m4p which will not play on linx. I've tried handbrake on ubuntu, but it only has mkv format as an option. This does not play on linux either. I tried renaming the output mkv file to m4a, mp3, aac, but still it will not play on linux. Frustrated.

---

### Post by Yellow Pasque on 2016-03-03
Can't you run some of the Win tools through wine?

---

### Post by coldraven on 2016-03-03
> I've tried handbrake on ubuntu, but it only has mkv format as an option.  This does not play on linux either. I tried renaming the output mkv  file to m4a, mp3, aac, but still it will not play on linux. 
I'm not an expert in this field but do I understand that you managed to convert using handbrake? If somehow this is true then surely you can easily *convert a mkv file to mp3 with ffmpeg.
Edit: That should say "*Extract the audio from a mkv container and save it as mp3"

---

### Post by yancek on 2016-03-03
You certainly should be able to create mp4 using handbrake.  I've used it in the past with no problems and that is it's primary purpose defined in Synaptic.  I'd be curious as to how old your Ubuntu system is, what version.  Did you read any documentation or tutorials on the use of handbrake?  Are you actually still using xp?

---

### Post by Paul_Alexander on 2016-03-04
> **yancek said:**
> You certainly should be able to create mp4 using handbrake.  I've used it in the past with no problems and that is it's primary purpose defined in Synaptic.  I'd be curious as to how old your Ubuntu system is, what version.  Did you read any documentation or tutorials on the use of handbrake?  Are you actually still using xp?

Ubuntu 14.04 LTS, all up to date, along with handbrake.

No, I'm not using any other OS to try to find a solution - I'm figured there was something here in linux.
I have read the handbrake docs but I'll go read again to see if I missed anything - it seems others above may have solutions for me.

I tried ffmpeg from command line and tried apps VLC Player and WinFF, but can't get any output file to play the song. I even tried burning the song to local disk and trying to rip the song out as a new format, but nothing works. Any other suggestions? Kind of a summary of what I tried. And again, I own all of this music. Of the 400 m4p files I have, 130 or so will not convert through typical windoze means (e.g., burning them to CD and then ripping them to mp3) likely because these are the pre-'09 era songs with older drm. Anyway I could sure use some help:-).


[LIST=1]
[*]Burn the m4p music file to an ISO on disk. I use the built in CD/DVD Creator and choose to burn the song.m4p file to an image  file on hard disk. This creates a file, /home/me/brasero.iso. 
[*]I mounted the newly created ISO after creating a dir to hold it.         sudo mount -o loop /home/me/brasero.iso /media/iso 
[*]I converted to FLAC, MP3, OGG, WAV. 
[*]After trying the gui apps, I hit the ffmpeg command directly. Below that is the last few dozen lines of the stdout failure. I even tried passing the bitrate and sample rates directly through  the ffmpeg command like this. 
[/LIST]

```
/usr/bin/ffmpeg -y -i "/media/iso/song.m4p" -vn -ar 44100 -b:a 160k  "/home/paul/Music/song.mp3"
```

```
[aac @ 0x30dfdc0] Sample rate index in program config element does not match the sample rate index configured by the container.
[aac @ 0x30dfdc0] Remapped id too large
[aac @ 0x30dfdc0]  is not implemented. Update your FFmpeg version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
[aac @ 0x30dfdc0] If you want to help, upload a sample of this file to ftp://upload.ffmpeg.org/incoming/ and contact the ffmpeg-devel mailing list. (ffmpeg-devel@ffmpeg.org)
Error while decoding stream #0:0: Not yet implemented in FFmpeg, patches welcome
[aac @ 0x30dfdc0] channel element 3.8 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] channel element 2.14 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] Reserved bit set.
[aac @ 0x30dfdc0] invalid band type
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] channel element 2.15 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] Number of bands (13) exceeds limit (6).
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] SBR was found before the first channel element.
[aac @ 0x30dfdc0] channel element 3.15 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] channel element 2.6 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] SBR was found before the first channel element.
[aac @ 0x30dfdc0] Pulse tool not allowed in eight short sequence.
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] Sample rate index in program config element does not match the sample rate index configured by the container.
[aac @ 0x30dfdc0] Inconsistent channel configuration.
[aac @ 0x30dfdc0] get_buffer() failed
Error while decoding stream #0:0: Invalid argument
[aac @ 0x30dfdc0] channel element 2.0 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] Prediction is not allowed in AAC-LC.
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] Sample rate index in program config element does not match the sample rate index configured by the container.
[aac @ 0x30dfdc0] Remapped id too large
[aac @ 0x30dfdc0]  is not implemented. Update your FFmpeg version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
[aac @ 0x30dfdc0] If you want to help, upload a sample of this file to ftp://upload.ffmpeg.org/incoming/ and contact the ffmpeg-devel mailing list. (ffmpeg-devel@ffmpeg.org)
Error while decoding stream #0:0: Not yet implemented in FFmpeg, patches welcome
[aac @ 0x30dfdc0] Number of bands (23) exceeds limit (11).
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] Reserved bit set.
[aac @ 0x30dfdc0] channel element 3.1 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] Sample rate index in program config element does not match the sample rate index configured by the container.
[aac @ 0x30dfdc0] Inconsistent channel configuration.
[aac @ 0x30dfdc0] get_buffer() failed
Error while decoding stream #0:0: Invalid argument
[aac @ 0x30dfdc0] channel element 3.15 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] Prediction is not allowed in AAC-LC.
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] channel element 3.13 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] channel element 2.1 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] Reserved bit set.
[aac @ 0x30dfdc0] Number of scalefactor bands in group (52) exceeds limit (49).
Error while decoding stream #0:0: Invalid data found when processing input
[aac @ 0x30dfdc0] channel element 2.6 is not allocated
Error while decoding stream #0:0: Invalid data found when processing input
size=      20kB time=00:03:41.19 bitrate=   0.7kbits/s speed=33.7x    
video:0kB audio:20kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 1.210938%
Conversion failed!
```

> **coldraven said:**
> I'm not an expert in this field but do I understand that you managed to convert using handbrake? If somehow this is true then surely you can easily *convert a mkv file to mp3 with ffmpeg.
Edit: That should say "*Extract the audio from a mkv container and save it as mp3"

Maybe you can give me some advice on this...see my longer reply above...again thank you.

Oh and I yes I also tried using the MKV file I get out of handbrake as the source, but nothing I throw at it outputs a target file (ogg, flac, mp3, wav, etc) that plays the song.

---

### Post by shantiq on 2016-03-05
Hi Paul   could you upload on  of those files and link it so we can see what could be tried maybe   thanx shan

---

### Post by Paul_Alexander on 2016-03-05
Fixed! See the solution, last post here.
[http://emby.media/community/index.php?/topic/32125-removal-of-drm-from-m4p-itunes-files/?p=309113#entry309113](http://emby.media/community/index.php?/topic/32125-removal-of-drm-from-m4p-itunes-files/?p=309113#entry309113)

---

### Post by Yellow Pasque on 2016-03-06
Yeah, if paying ransom money to Apple to free your music is an acceptable solution to you, mark the thread solved.

---

