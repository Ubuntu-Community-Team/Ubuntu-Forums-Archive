---
title: "Recording audio and video from a webcam"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by fabio.nb on 2007-03-06
Hi,

I want to record a video and audio using my webcam.

I'm be able to capture video with effectv or xawtv.
I'm be able to capture audio with:
cat /dev/dsp3 > test.raw
cat teste.raw > /dev/dsp2

But I want to record and the both at the same time!!! I tried dvr, but I didn't get successful with audio (if i choose 16 bit there is no sound, 8 bit there is a noise). And with this program I'm not be able to see the preview of the webcam.

I don't know what programs to use and how to record! I need some help!!!

Fabio

---

### Post by macewan on 2007-04-05
not sure if your question was answered else where if so please post the how to here

if not you might want to consider using the video blogging feature found on youtube or dailymotion

---

### Post by SGuntu on 2007-04-08
You should be able to do this with VLC player which can be installed from the repositories. It's extremely powerful and can let you view, stream or save video/audio from any source.

To create a file from your webcam... Go to "File" -> "Open capture device". Make sure the "Video device name" and "Audio device name" are correct (for me the dialog defaults to /dev/video when in fact my webcam it is /dev/video0" so do check this). Then under "advanced options" at the bottom of the dialog, tick "stream/save" then settings. Check the "file" option under "outputs" and adjust the desired output format to taste with the transcoding options and you're good to go. VLC won't show the webcam while it saves, so if you want to see if it is working go to where ever you set it to save and inspect the file.

Hope this helps.

---

### Post by scto on 2007-04-08
hi,

i've a logitech quickcam pro 5000 with uvc-video module.
for recording i use: 

ffmpeg -vd /dev/video1 -ad /dev/dsp2 -acodec mp3 -vcodec mpeg4 -vtag xvid -s 320x240 -r 25 -y webcam.avi

Regards
Tom

PS: ffmpeg from medibuntu (xvid/mp3)

---

### Post by fabio.nb on 2007-04-10
Thnks for reply guys...

With the command ffmpeg i got the error:
Could not find video grab device

With VLC I was able to record (video and audio)... I'll use VLC (i could be cool if it had the live exibition of the record, but its ok)...

Thanks again

---

### Post by osdesk on 2007-04-27
SGuntu, this has been very helpful.  

I searched hi and low for info on this.  Thank you, your instructions were superb.  :KS :KS :KS

---

### Post by DirtDawg on 2007-05-06
> **SGuntu said:**
> You should be able to do this with VLC player which can be installed from the repositories. It's extremely powerful and can let you view, stream or save video/audio from any source.

To create a file from your webcam... Go to "File" -> "Open capture device". Make sure the "Video device name" and "Audio device name" are correct (for me the dialog defaults to /dev/video when in fact my webcam it is /dev/video0" so do check this). Then under "advanced options" at the bottom of the dialog, tick "stream/save" then settings. Check the "file" option under "outputs" and adjust the desired output format to taste with the transcoding options and you're good to go. VLC won't show the webcam while it saves, so if you want to see if it is working go to where ever you set it to save and inspect the file.

Hope this helps.

When I select the "advance options" button, the window is so large, it's taller than the screen! When I use ALT+LMB to move it up, it's broken and I cant resize it as a result. I can't access the "stream/save" ticker as a result. Any suggestions?

Using Gnome interface, btw.

---

### Post by The J on 2007-06-13
I was searching Google for this issue and found [this]("https://answers.launchpad.net/ubuntu/+question/3743") Launchpad page.  Someone there suggested doing the following in the console:
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo trace=15
```
I tried it and it so far seems to work with ffmpeg and luvcview.  With ffmpeg, I used scto's example but removed the **-ad /dev/dsp2 -acodec mp3** part.  Playing it back gives audio without those options, but the video was grayscale (could be something on my end).  luvcview gives color video, but no audio.

To keep the above trace setting permanent, the poster in that link suggested adding the following to /etc/modprobe.d/options:
```
uvcvideo trace=15
```

Hope this helps someone.

---

