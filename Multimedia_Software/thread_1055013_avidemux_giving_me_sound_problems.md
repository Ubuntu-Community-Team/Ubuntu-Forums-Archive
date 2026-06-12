---
title: "avidemux giving me sound problems"
date: 2009-01-30
forum: Multimedia Software
---

### Post by Polygon on 2009-01-30
Im trying to encode some videos i recorded on my digitial camera, and while the video works, i cannot for the life of me get the sound in the resulting video to work properly

No matter what codec i choose for audio, something screws up

direct copy: sound works, but stutters every second
mp3: makes the sound unbearable to listen to, high pitched noise
vorbis: avidemux throws an error
aac: avidemux throws an error
ac3: avidemux throws an error
wav: i forget but i know it doesnt work

its REALLY annoying to have to reboot into windows just to use virtualdub, is there some way to fix this problem? =/

---

### Post by Cresho on 2009-02-03
ahh...........yes............hmmm

I run virtualdub in linux just fine.

my settings...

1.  sudo apt-get install wine.  (don't use the newer one since its beta)
2. install virtualdub or create a script to run the exe file from anywhere on your pc or right click on the exe and open with wine.  There you have it!
3. open winefcg in terminal, applications tab add virtualdub.exe and highlight it to specify what you want for it.  in graphics, change to "allow the window manager to decorate windoes" and "allow the window manager to cotrnol windows" and "emulate a virtual desktop 1750x800"  i have a 19200x1200 res so change accordingly.  THis is needed because it wont render video.  in virtualdub, under options and prefferences, in display you disable use for directx and ..well everything is disabled. save and ok it.  now you can import videos.

dont forget to install: 
ffdshow_rev2630_20090122_clsid.exe
Xvid-1.2.1-04122008.exe
or any other codec


Why do I use this?  I use winff with modified scripts to convert my videos from high definition mp4 passthrough to fix some header issues from my xacti hd1000.  I use avidemux to then correctly identify audio sync and timings of the video.  I use virtualdub and deshaker to remove the shakiness of the video and mainactor to video edit.  sometimes I use blender as ell depending.

in your case, your pc may not be as powerfull to render audio/video since you mentioned you hear problems with the footage streight off the camera.

Linux can do it but it takes time to get a workflow going.  In fact, video editing is very possible in linux.  I also have virtualbox running windowsxp and vegas video7 just in case but found the quality output to be poor and i can notice since my monitor is very sharp.  opensource does a way better job and I can't believe mainactor was discontinued.  It produces video output image quality better than vegas.


You need to work on your workflow and software configurations first before it can become fluid.

avidemux can do it but sometimes cannot read certain headers on a file.  I found out using winff passing through the video and converting the audio to mp3 fixed my issue but I had to make a config preset like this one..could help you.
-vcodec copy -acodec mp3 -ab 192k -ac 2 -ar 48000

here is a conversion tutorial i use for my xacti..
[http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27&page=1](http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27&page=1)

If you have questions or also creating a main menu launcher, just ask, i have virtualdub running like if it was on windows.  I currently use 1.9 and been using the software for like 10 years?

---

