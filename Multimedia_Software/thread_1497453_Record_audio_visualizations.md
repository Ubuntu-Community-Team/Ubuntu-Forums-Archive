---
title: "Record audio visualizations"
date: 2010-05-30
forum: Multimedia Software
---

### Post by Kenjitamura on 2010-05-30
[SIZE="2"]Just curious if anyone has a good way to record the techno like video that comes from using media player audio visualizers.  What I'm looking for is something like projectM but with the capability to save to a video file for later use, sounds easy but I haven't found a single way yet.  I've tried some screen capture devices to try and record but they have all been failures, xvidcap when it does record freezes, can only get 43 seconds, and even when I set the fps to 30 it only manages 18.  This would be very easy if mplayer had audio visualizers but I haven't found one for it so I can't just use the -dumpfile option.

Anyone know if when I'm running audacious with projectM if the streaming video is getting saved to a cache?[/SIZE]

---

### Post by Kenjitamura on 2010-05-31
I've seen this question asked before but as far as I know on these forums it's never been answered.  Well I figured it out myself and got great results.

When I ruled out screen capture devices as ineffective I remembered I used to record 3d applications with a program and it gave very nice video.  So I looked around for Ubuntu 3d recording software and found a program that records applications that use Opengl called [glc]("http://nullkey.ath.cx/projects/glc/").  Pretty easy to install, just made sure the dependencies were all there ```
sudo apt-get install build-essential cmake libx11-dev libxxf86vm-dev libgl1-mesa-dev libasound2-dev libpng12-dev

``` and then followed its instructions ```
wget http://nullkey.ath.cx/glc/scripts/glc-build.sh
chmod a+x glc-build.sh
./glc-build.sh

```

If you recall projectM is an audio visualizer that streams its output in Opengl so I fully installed projectM as per this thread [Howto: Install and use projectM music visualizer with pulseaudio support]("http://ubuntuforums.org/showthread.php?t=749793").

Once both those programs were installed I opened projectM with glc using this command ```
glc-capture projectM-pulseaudio
``` Then I opened up my audacious media player and set its sound output to pulse audio.  From there when I was ready to record I'd hit Shift + F8 and start playing the song in audacious, whenever you want to stop recording just hit Shift + F8 again.

I exited the projectM window and went into the directory I installed glc (In this case it was my home directory) and found a .glc file in this case it was called "projectM-pulseaudio-18485-0.glc".  From here the glc website tells you how to encode this file using mencoder, I'm not a fan of mencoder and have a fully functional avisynth + avidemux encoder combo so I used this code ```
glc-play projectM-pulseaudio-18485-0.glc -y 1 -o video.y4m
``` to create a raw video file called video.y4m and used avisynth to open it using rawsource which I piped to avidemux giving me the option to encode the video to a huge selection of formats.

---

### Post by intel design on 2011-06-28
[SIZE=2]I have enjoyed reading your thread! I have read a lot of posted complaints about ProjectM-Libvisual compiling! I want to record audio visualization for Internet screen-cast! I have had a little success without doing the hard part see my video: 
[COLOR=Red] [http://www.youtube.com/watch?v=B](http://www.youtube.com/watch?v=B)[/COLOR]

The hard part for me is building "ProjectM-Libvisual" in ~/projectm/trunk/src$  check out this frustrating occurrence:

[COLOR=Red] [http://pastebin.com/rf7Mud8C](http://pastebin.com/rf7Mud8C)[/COLOR][/SIZE]

[COLOR=Black]Once again I like your ideas and may implement them someday [/COLOR]but first I'd like to solves my own crazy build with ccmake issues!

---

### Post by intel design on 2011-06-28
[SIZE=2]I have enjoyed reading your thread! I have read a lot of  posted complaints about ProjectM-Libvisual compiling! I want to record  audio visualization for Internet screen-cast! I have had a little  success without doing the hard part see my video: 
[COLOR=Red] [http://www.youtube.com/watch?v=B](http://www.youtube.com/watch?v=B)[/COLOR]

The hard part for me is building "ProjectM-Libvisual" in ~/projectm/trunk/src$  check out this frustrating occurrence:

[COLOR=Red] [http://pastebin.com/rf7Mud8C](http://pastebin.com/rf7Mud8C)[/COLOR][/SIZE]

[COLOR=Black]Once again I like your ideas and may implement them someday [/COLOR]but first I'd like to solves my own crazy build with ccmake issues!

Check out my attachments!

---

