---
title: "System freeze on Video Playback"
date: 2008-07-27
forum: Multimedia Software
---

### Post by ragflan on 2008-07-27
Hi, I'm on Ubuntu Hardy (using Gnome). I have a problem with video playback on Ubuntu. I have installed VLC, Gnome MPlayer and some other media players as well and I've tested this with different video formats and different videos as well. For some odd reason, just randomly regardless of the file (any file which otherwise works) and regardless of player, the system freezes for the first video file I play. 

For example, for this desktop session, I'm currently surfing the net and I want to play some videos on my hard disk. If the first video (any random file) I open works, then the session is fine. If not, the system freezes. 

I have to power off my laptop and reboot and then the same file with the same player works normally. It happens on random with the first video file I play for the desktop session. If the first video file (for a session) I play is fine, then the system doesn't hang with any other files I open. 

It's very random and I don't know what is causing it. Any ideas?

---

### Post by vfontanela on 2008-08-03
Oh, I have the same problem and this is getting me mad. I'm using Hardy Heron.

Randomly, when I play video the system deeply freezes. Ctrl+Alt+Backspace or Ctrl+Alt+F# doesn't work at all. I have to turn my laptop off.

First I thought it was some GStream problem, then I removed it and installed Xine, without any success, I tried several other players, lots of kinds of videos and, as it is ramdom, I tought a lot of times I have solved the problem, then it freezes again. Ah, it also happened once when I played mp3 with Totem (which is the default) Rhythmbox and Audacious works ok pretty well. And it is also strange, 'cause when I set the video players to work with ALSA, it freezes sometimes. But if I set it to work with PulseAudio, OSS then they will freezes always. And Audacious works ok with PulseAudio.

I googled for that and I discovered that there is a known problem with Intel Audio Sound, I have a ALC883 one. But it plays audio files, the system just freezes with video files (asf, wmv, avi, mpg, mpeg). I used other distros in this pc some time ago and it worked fine, so I think that there must be a solution.

Thanks for helping.

---

### Post by vfontanela on 2008-08-03
It seems this is not an audio issue, but a video one.

A way to partially solve it is configuring the player (like Gnome Mplayer) to use OpenGl (gl in Mplayer) as Video Output. Works like a charm.

---

### Post by ragflan on 2008-08-03
I hope that fixes it. I thought it was because I was using some of the Compiz effects without having a good 3D card or something. Then I removed all effects and the system still froze randomly on video playback. You're right, I can hear audio just fine but everything else is gone. I cannot do anything but move the mouse. But it can only move, it cannot click on anything. I hope this solution you provided solves it. 

This is very important because in my class I am the only one that uses a Linux box and I convince so many friends of mine to switch, and everyone thinks it's awesome and cool but I dare not play any videos and risk freezing the system and everyone's not gonna think it's cool anymore.

---

### Post by ragflan on 2008-08-03
Another thing is that I reinstalled Ubuntu and followed all instructions on video and audio (using the Multimedia thread in the forums) and I didn't change anything else but it still happens. System still freezes randomly.

I'm using a Compaq Presario v3000 notebook.

---

### Post by ragflan on 2008-08-03
Wow, this time I didn't even play anything and it froze on me. All I did was open up gxine and setup wizard came up with the following dialogs:


[CENTER][IMG]http://ramipage.googlepages.com/Screenshot-gxinesetupwizards.png[/IMG]

[IMG]http://ramipage.googlepages.com/Screenshot-gxinesetupwizards-1.png[/IMG]

[IMG]http://ramipage.googlepages.com/Screenshot-gxinesetupwizards-2.png[/IMG][/CENTER]

Once I press the 'CLOSE' button on the last dialog, system froze. Twice. Third time, gxine opens up but I get this error before the program closed:

**Fatal error Segmentation Fault. **

Isn't there any explanation to this? I tried what vfontanela suggested but the screen flickers uncontrollably during playback when using OpenGL.

---

### Post by vfontanela on 2008-08-04
Well, I forgot to tell you but the screen get a bit weird when playing with OpenGl, but after that no freezing, at least.

But now I definetelly solved it, installing and running KDE. I can run any video with Kaffeine ok, all the configs are as in default. I had already tried Kaffeine with Gnome but I had the same problem. Now it is damn ok, and the system is a lot faster.

sudo apt-get install kubuntu-desktop

Please try it, I would like to know if it would fix the problem there too.

---

### Post by zkma on 2008-08-08
vfontanela, I've tried your solution by installing kubuntu, and it works.
But actually, I didn't like KDE and prefer Gnome so I've looked for another solution, and I found one, proposed by Gremlinzzz on that thread : [http://ubuntuforums.org/showthread.php?t=480357](http://ubuntuforums.org/showthread.php?t=480357)

* GStreamer (The default video player in Ubuntu, totem-gstreamer, and any video player that is based on the gstreamer backend)
o Open a terminal and type "gstreamer-properties". Press Enter.
o Click the Video tab.
o Under Default Video Plugin select "X Window System (No Xv)".
o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
o Click Close

* VLC (VLC is not installed by default; you need to search in the package manager, then install)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

* MPlayer (Mplayer is not installed by default)
o Start Mplayer
o Right-click on the screen and select Preferences
o Select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
o Click Save and restart the program for the setting to take effect.
+ Some users reported that MPlayer may not be able to show videos in full screen.

* Xine
o Start xine
o Click File, then Configure and then Preferences
o In experience_level select "Master Of The Known Universe" so that all available settings are visible.
o Select the tab for video.
o Under Driver select "xshm".
o Restart xine.
+ The same process enables Totem that has the totem-xine backend configured.


Hope this will help

---

### Post by dstorrez on 2008-08-17
:) Hurray!!
the previous post fixed it for me. I was like others and had loaded different players and could not fix the problem the vids would just freeze.
I ended up clearing them all out and just running totem the default player and followed the directions on the previous post and so far I have tried three different formats. I'll keep ya posted and see if it freezes again. But, so far so good. thanks.

---

### Post by ragflan on 2008-08-18
Yeah but the X11 thing makes the video look bad. Like grainy or something. I wish there was a way to have the normal video (Default video output) settings without having the use the X11 output thing.

---

### Post by Louigi Verona on 2010-02-13
I have the same problem. Using Movie Player just freezes the system instantly on video playback. Using X11 solves the problem, but the video quality is worse and, most importantly, a lot of files stop playing correctly and start "shaking", as if some frames are repeated several times, which makes it impossible to watch. Weird, I've used that same distro before for a long time without having any such problems. What could've set it off?

---

### Post by Louigi Verona on 2010-02-16
I seem to have solved the issue by switching sound from PulseAudio to ALSA in the Preferences of Ubuntu as a default.

---

### Post by babboo65 on 2010-02-16
I'm running Karmic - have been running Ubuntu since Gutsy and have never experienced a problem like this before - until the Karmic update.  I can only play about 10 or 15 minutes worth of any video until the system freezes.  I can't even change from Pulse to ALSA because that option doesn't exist.

I'm reading this and other threads describing the same problems.

---

### Post by Louigi Verona on 2010-02-16
This problem with Karmic had topped my line of problems with Karmic which I struggled with for three months and I went back to Jaunty, the decision which I consider to be a very good one for any Karmic user who experiences problems with 9.10

However, the freeze I describe occurs on Jaunty and seems to be fixed by setting ALSA as default, while PulseAudio by default freezes the system. However, it freezes it immediately, not after 10-15 minutes, which seems like a significant difference in our cases.

---

### Post by Louigi Verona on 2010-03-21
While in general the fix works, sometimes the video playback would still freeze the system, but randomly. I mean, when I am opening VLC first and open a video through it, it is ok. Freezing occurs usually if I click on a video file and it calls up VLC. So when I am clicking on a video file I never know if it will freeze it or not.

---

### Post by efrens on 2010-08-04
> **zkma said:**
> vfontanela, I've tried your solution by installing kubuntu, and it works.
But actually, I didn't like KDE and prefer Gnome so I've looked for another solution, and I found one, proposed by Gremlinzzz on that thread : [http://ubuntuforums.org/showthread.php?t=480357](http://ubuntuforums.org/showthread.php?t=480357)

* GStreamer (The default video player in Ubuntu, totem-gstreamer, and any video player that is based on the gstreamer backend)
o Open a terminal and type "gstreamer-properties". Press Enter.
o Click the Video tab.
o Under Default Video Plugin select "X Window System (No Xv)".
o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
o Click Close

* VLC (VLC is not installed by default; you need to search in the package manager, then install)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

* MPlayer (Mplayer is not installed by default)
o Start Mplayer
o Right-click on the screen and select Preferences
o Select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
o Click Save and restart the program for the setting to take effect.
+ Some users reported that MPlayer may not be able to show videos in full screen.

* Xine
o Start xine
o Click File, then Configure and then Preferences
o In experience_level select "Master Of The Known Universe" so that all available settings are visible.
o Select the tab for video.
o Under Driver select "xshm".
o Restart xine.
+ The same process enables Totem that has the totem-xine backend configured.


Hope this will help

Is there a way to do the same to Pitivi video editor? Playing video hangs on me and this solution worked so far as to playback. But when I try to playback from Pitivi it's crushing again. And I can't see an option to change the video output in the gui of the preferences of Pitivi. May there's text file to edit? Anyone?

---

### Post by hastinbe on 2010-09-18
zkma's solution worked for me in Lucid Lynx

---

### Post by glbala on 2010-10-31
The solution provided here did help me. Thanks a lot. :)

---

