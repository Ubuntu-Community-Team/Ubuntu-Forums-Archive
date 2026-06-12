---
title: "Editing .MTS or .avi files"
date: 2013-03-04
forum: Multimedia Software
---

### Post by dkolars on 2013-03-04
Using XUbuntu 12.04... have used Avidemux since I switched to Linux... usually works well... BUT, my Canon video camera records to .mts files...  When I open them for editing in Avidemux, the sound is good, but the video is about half speed.  So, I used ffmpeg to convert them to .avi files.  When I open those in Avidemux, the audio and video are out of sync, and adjusting the Audio Shift does nothing.  

These are vidoes of a concert I played with a couple of friends, and would like to cut the extraneous bits out and then make DVD's... but not working with Avidemux... I tried Open Shot Video Editor, but it's a screwy program... once I start to play the video, there is no way to stop it!!  I deleted some of the beginning before we started playing, and then exported the file, and the program did not delete what I thought I had deleted, but saved it as blackness on the screen.  So, that program fails...

Are there ANY decent programs for video for Linux?  I've searched and have come up pretty empty...   I might be forced to actually use the Windows 7 that came on my laptop just for this... I haven't even run it yet in the year that I've had it... running XUbuntu on there as well...

Anyway, video editing NOT a Linux strong suit, imho....

---

### Post by sudodus on 2013-03-04
> **dkolars said:**
> Using XUbuntu 12.04... have used Avidemux since I switched to Linux... usually works well... BUT, my Canon video camera records to .mts files...  When I open them for editing in Avidemux, the sound is good, but the video is about half speed.  So, I used ffmpeg to convert them to .avi files.  When I open those in Avidemux, the audio and video are out of sync, and adjusting the Audio Shift does nothing.  

These are vidoes of a concert I played with a couple of friends, and would like to cut the extraneous bits out and then make DVD's... but not working with Avidemux... I tried Open Shot Video Editor, but it's a screwy program... once I start to play the video, there is no way to stop it!!  I deleted some of the beginning before we started playing, and then exported the file, and the program did not delete what I thought I had deleted, but saved it as blackness on the screen.  So, that program fails...

Are there ANY decent programs for video for Linux?  I've searched and have come up pretty empty...   I might be forced to actually use the Windows 7 that came on my laptop just for this... I haven't even run it yet in the year that I've had it... running XUbuntu on there as well...

Anyway, video editing NOT a Linux strong suit, imho....

I have a similar camera, that makes MTS files, and I use script files with ***ffmpeg*** to decrease the bitrate of my video clips to make them playable also on computers with less horsepower. It works for me either with the default codec for mp4 or with the x264 codec. I also use ***Openshot*** to edit and compose video clips and photos to a nicer movie. 

I use them in ***Ubuntu Studio***. Maybe the software comes better set up in Ubuntu Studio, which uses the Xubuntu desktop environment (with XFCE). And to get snappy graphics I install LXDE

```
sudo apt-get install LXDE
```

---

### Post by sudodus on 2013-03-04
And I should add, that I like to play video with ***mplayer (mplayer2)*** or ***VLC*** with the desktop environment LXDE. This makes the video clips run the well on my aging hardware.

---

### Post by dkolars on 2013-03-04
Well, I don't know how to use script files with ***ffmpeg*** to decrease the bitrate of my video clips... have no clue about this...  My equipment is less than 1 yr. old, so thinking that I shouldn't have to do anything like that?  Never had to before...  

I took my .mts file and converted it to .wmv.   WMV2 Generic was terrible quality, very pixelated...  WMV for Web Use gave a much better quality video.  BUT, when I edit that file with Avidemux, cutting out the 1st 4 mins of video (on the I frames, of course) on the first file and then save it (.avi or .mpg) the sound and video are out of synch.  I'm starting to detest Avidemux!!

OpenShot...  I was able to cut the 1st 4 mins from the file.  But, when it comes to saving it, the Help file says:  " Choose from one of the many preset export options, and click the Export Video Button".    There are 54 choices there!!  I know what some of them are and know I don't want PAL, or anything for CD.DVD, but I never went to video editing school, so will just start trying them and seeing what happens.  The program assumes you know about video editing already!!

Are you referring to Ubuntu Studio Controls?  That is the only thing in the repository that comes close to Ubuntu Studio?

---

### Post by sudodus on 2013-03-04
> **dkolars said:**
> Well, I don't know how to use script files with ***ffmpeg*** to decrease the bitrate of my video clips... have no clue about this...  My equipment is less than 1 yr. old, so thinking that I shouldn't have to do anything like that?  Never had to before...  

I took my .mts file and converted it to .wmv.   WMV2 Generic was terrible quality, very pixelated...  WMV for Web Use gave a much better quality video.  BUT, when I edit that file with Avidemux, cutting out the 1st 4 mins of video (on the I frames, of course) on the first file and then save it (.avi or .mpg) the sound and video are out of synch.  I'm starting to detest Avidemux!!

OpenShot...  I was able to cut the 1st 4 mins from the file.  But, when it comes to saving it, the Help file says:  " Choose from one of the many preset export options, and click the Export Video Button".    There are 54 choices there!!  I know what some of them are and know I don't want PAL, or anything for CD.DVD, but I never went to video editing school, so will just start trying them and seeing what happens.  The program assumes you know about video editing already!!

Do you want to make something that will play on a standard DVD player, or something that will play on (almost) any computer and a modern TV set from a USB pendrive?

- DVD player: Select profile DVD (and NTSC or PAL depending on country)

- Computer: New and powerful computers that are properly configured can play your MTS files, that might be 1920x1080-50p (50 frames/s progressive) or 1920x1080-50i (50 frames/s interlaced). Older or less powerful computers need something that is easier to play.

. Standard DVD, but that has much lower video quality than the original video clip.

. 1280x720-50p, select profile 'All formats' and video profile 'HD 720p 50 fps' with an mp4 container.
> 
Are you referring to Ubuntu Studio Controls?  That is the only thing in the repository that comes close to Ubuntu Studio?

No to the Ubuntu Studio flavour that can be installed. See this link [[COLOR=#ff0000]http://ubuntustudio.org/[/COLOR]]("http://ubuntustudio.org/")

But this task should work with Openshot installed into your present Ubuntu too.

---

