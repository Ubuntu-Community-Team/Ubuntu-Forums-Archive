---
title: "screencasting audio/video sync problems"
date: 2012-09-20
forum: Multimedia Software
---

### Post by wayover13 on 2012-09-20
Hi. I've been using recordmydesktop from the command line for a couple of years now to make lecture videos from my computer and it's been working pretty well. I also experimented successfully with ffmpeg's x11grab. But now both of those utilities have flaked out on me: with both, the audio and video are slightly out of sync. Weird thing is that the video ends up being a few seconds ahead of the audio when I use recordmydesktop, but video is slightly behind audio using ffmpeg's x11grab.

My screencasts are actually lectures within which I occasionally type text into a whiteboard on my computer screen. To test sync, I've made sample videos where I verbally say each letter of a word as I'm typing it. With recordmydesktop the text appears on screen already a few seconds before I've started verbally spelling. With ffmpeg, the letters start to show up in the test video only after I've started verbally spelling.

I've researched and tried a bunch of different switches with both recordmydesktop and ffmpeg's x11grab, but I can't get the sync to improve. Meantime, I discovered a pretty horrid looking hack of a bash script someone made that also uses ffmpeg but which records audio and video separately, then joins them together. It's a really clunky thing and I could only test it once I'd figured out that the way to stop the script is just to enter the file name, while it's recording, under which you'd like the output to be saved. Weirdest of all, this script gives me a file in which audio and video are pretty much in perfect sync.

The script is as follows: ```
#!/bin/bash
#vzybilly
#these are temp files
aud="aud.mp3"
vid="vid.mp4"
#grab audio & pid
ffmpeg -f alsa -ac 2 -i plughw:0,0 $aud &
audPID=$!
#grab screen & pid
ffmpeg -f x11grab -s "1366x768" -r "24" -i :0.0 -threads 0 -sameq -an -f mp4 $vid &
vidPID=$!
#wait, till name given (that means stop)
read -p "Stop by giving an Output video name?" out
#stop audio and video with pids
kill -n 2 $audPID
kill -n 2 $vidPID
echo "Saving to $out"
#combine to the target output file
ffmpeg -i $aud -i $vid -acodec copy -vcodec copy "$out"
#purge the temp files
rm $aud
rm $vid
``` It was posted about on these forums at [http://ubuntuforums.org/showthread.php?t=2003738](http://ubuntuforums.org/showthread.php?t=2003738)

Can anyone either suggest any improvements to this script or else provide some other tips or leads for getting recordmydesktop and/or ffmpeg's x11grab to give me better synchronization between audio and video?

Thanks,
James

---

### Post by FakeOutdoorsman on 2012-09-21
I recommend the method shown here: [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719)

It records lossless video. The advantage is that it should capture "faster" and more likely reach your desired fps (or you could increase the fps for a smoother video). The disadvantage is that you should probably re-encode the resulting file due to the potentially large file sizes of lossless videos.

The script you posted unfortunately uses *-sameq*. This is the most abused ffmpeg option as it does not mean "same quality" and is not designed to be used between formats that do not share the same "quantizer scale". You should ignore this option since it does not do what you think it does. Also, the encoder the script uses is ambiguous since it will rely on the default encoder for .mp4 output. FFmpeg default will change to *mpeg4* if *libx264* is not available. These are not equal in terms of performance, quality, or format.

---

### Post by wayover13 on 2012-09-21
Thank you for your input, FakeOutdoorsman. I am familiar with that thread and the helpful pointers you've given within it and I even introduced from there certain tweaks to ffmpeg x11grab as I was using it, but the sync problem persisted nonetheless. I can only understand fairly superficially your criticisms of the script I've posted about in this thread since I am not well versed in the technicalities of computer video capture and processing. I have no grounds for disagreeing with anything you say except that I can attest that the script actually works, keeping audio and video in very good sync, while I have been unable to get ffmpeg x11grab on its own to sync properly.

In case you might be able to help me understand why the ffmpeg incantation I've come up with is not giving me accurate sync between audio and video, let me post the line I've been using and to which I've tried various modifications. It is ```
ffmpeg -f alsa -ac 2 -i plughw:1,0 -f x11grab -r 15 -s 830x660 -i :0.0+227,130+nomouse -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 output.mkv
``` (although I found I needed to use flac instead of pcm_s16le owing to some problem that's cropped up in 12.04). Can you spot anything there that could be causing my audio/video sync issues? I have tried varying framerates, by the way, from 10 through 25.

Also, could the script I found be improved by introducing modifications that would make it record losslessly? I do need to re-encode since the site where I upload my videos have fairly low file-size limits.

James

PS This is a non-standard Ubuntu installation. I do not have pulseaudio installed, as you may note.

---

### Post by wayover13 on 2012-09-21
On a somewhat tangential note, I've always preferred using recordmydesktop over ffmpeg's x11grab because the former allows pausing while the latter does not. Nonetheless I've continued to look into any sort of pseudo-pausing methods that might be used with ffmpeg's x11grab.

I say you have to do pseudo-pausing with ffmpeg's x11grab because your only choice, should you need to disrupt video capture, seems to be to quit and restart ffmpeg's x11grab, then concatenate the separate files you end up with. Well, I've just tested out a script called mmcat someone wrote and have tried it on a couple of test files: the results were quite good. Should you be interested you can find that script posted at [http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20(join,%20merge)%20media%20files](http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20(join,%20merge)%20media%20files)

James

---

### Post by wayover13 on 2012-09-21
I've gone ahead and tweaked the script for lossless recording as follows:```
#!/bin/bash
#vzybilly
#these are temp files
aud="aud.**flac**"
vid="vid.**mkv**"
#grab audio & pid
ffmpeg -f alsa -ac 2 -i plughw:0,0 **-acodec flac** $aud &
audPID=$!
#grab screen & pid
ffmpeg -f x11grab -s "1366x768" -r "24" -i :0.0 -threads 0 **-vcodec libx264 -preset ultrafast -crf 0** $vid &
vidPID=$!
#wait, till name given (that means stop)
read -p "Stop by giving an Output video name?" out
#stop audio and video with pids
kill -n 2 $audPID
kill -n 2 $vidPID
echo "Saving to $out"
#combine to the target output file
ffmpeg -i $aud -i $vid -acodec copy -vcodec copy "$out"
#purge the temp files
rm $aud
rm $vid
```That does cause it, I believe, to produce the sort of lossless files to which FakeOutdoorsman was alluding (they come in at about 6 MB/minute on this machine). Those--should there be multiple files owing to pausing--can then either be concatenated using mmcat, then re-encoded, or just re-encoded. 

It was also suggested to me that replacing the line ```
read -p "Stop by giving an Output video name?" out
``` with ```
out="`zenity --entry --title="Video muxing script" --text="Please type a file name (sans extension) in the blank to stop the recording"`.mkv"
``` (provided you have zenity installed) makes for a somewhat less kludgy solution to the halting of the recording and beginning of the joining process. It causes a pop-up window to appear which has a blank for the file name in it: once that's filled in and "Ok" is clicked, the recording stops and the joining begins.

James

---

### Post by FakeOutdoorsman on 2012-09-21
Unfortunately my mouse died and I had to borrow an old, terrible 5 buttoned rat. Accidental clicks of that mal-placed side button will cause the browser to go back a page, and any content in "quick reply" upon clicking the forward button will no longer exist despite being seconds away from finishing... So I'll be less verbose on this attempt.

Did moving the audio as a separate encode as shown in your latest script resolve the sync issue? If not then some things to try:

Compile ffmpeg. The version from the repository is often buggy. See [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).

Change *flac* to *pcm_s16le* or *copy* (*copy* is worth trying since your input is probably detected as pcm_s16le, but I don't know if it will work). Muxing the separate audio and video tracks into matroska (.mkv) container, as your script now does, will probably avoid the issue you mentioned earlier. Don't forget to change aud="aud.flac" to aud="aud.wav" if you try pcm_s16le or copy.

There was a third item from last time, but now I've forgotten it...

Thanks for the mmcat pointer. I know the author, but haven't seen that wiki page before. One pausing method is shown [here](http://ubuntuforums.org/showpost.php?p=9505604&postcount=48).

Re-encoding the lossless output to something more manageable is easy. Are you uploading to your own server, or something like YouTube? If it's something like YouTube, then you want to provide the highest quality that is practical to upload since it will re-encode anything you give it. See the CRF section of: [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide). Change the crf value to 18, and also re-encode the audio with something like "-c:a libmp3lame -q:a 2" or "-c:a libfdk_aac -flags +qscale -global_quality 5 -afterburner 1". If the resulting file is too big then use a higher crf value (an increase of +6 is roughly half the bitrate).

---

### Post by wayover13 on 2012-09-22
> **FakeOutdoorsman said:**
> Unfortunately my mouse died and I had to borrow an old, terrible 5 buttoned rat. Accidental clicks of that mal-placed side button will cause the browser to go back a page, and any content in "quick reply" upon clicking the forward button will no longer exist despite being seconds away from finishing... So I'll be less verbose on this attempt.
I can sympathize: I've had the same happen to me many times due to varying circumstances.
> Did moving the audio as a separate encode as shown in your latest script resolve the sync issue?
That script has worked fine for me every time I've used it, despite its crudeness. I just tweaked it a bit to make it produce lossless files, and it continues to work for me as well as it did the first time I tried it. I plan to stick with it.
> Compile ffmpeg. The version from the repository is often buggy. See [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).
Thanks for the link--I'll keep that in mind in case I run into other problems.
> Change *flac* to *pcm_s16le* or *copy* (*copy* is worth trying since your input is probably detected as pcm_s16le, but I don't know if it will work). Muxing the separate audio and video tracks into matroska (.mkv) container, as your script now does, will probably avoid the issue you mentioned earlier. Don't forget to change aud="aud.flac" to aud="aud.wav" if you try pcm_s16le or copy.
As I mentioned, there's some problem with the pcm_s16le codec either in the current Ubuntu or in its version of ffmpeg. I was getting error messages when I tried using that codec and some googling revealed it's been a problem for others as well (error message "[matroska @ 0x8160300] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1 >= 1 av_interleaved_write_frame(): Invalid argument"). That's why I decided to go with flac instead.
> Thanks for the mmcat pointer. I know the author, but haven't seen that wiki page before. One pausing method is shown [here](http://ubuntuforums.org/showpost.php?p=9505604&postcount=48).
It's a pretty complex script for someone with my limited experience but it's worked pretty much out of the box for me. I did decide to edit the switches passed to ffmpeg to the same ones I use in recording my videos, which is I hope is correct.
> Re-encoding the lossless output to something more manageable is easy. Are you uploading to your own server, or something like YouTube? If it's something like YouTube, then you want to provide the highest quality that is practical to upload since it will re-encode anything you give it. See the CRF section of: [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide). Change the crf value to 18, and also re-encode the audio with something like "-c:a libmp3lame -q:a 2" or "-c:a libfdk_aac -flags +qscale -global_quality 5 -afterburner 1". If the resulting file is too big then use a higher crf value (an increase of +6 is roughly half the bitrate).
I upload my files to an educational site where I teach. A good median between quality, upload size limits, and upload speed is when my videos come in at about 1-2 MB per minute. I found a good incantation in the thread you referred to earlier, one that allows me to re-encode these matroska files to flv's that are about the right size. That said, I'll experiment a bit with the varying values you've proposed here.

Thanks,
James

---

