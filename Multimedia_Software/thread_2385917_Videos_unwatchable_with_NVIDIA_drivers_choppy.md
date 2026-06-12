---
title: "Videos unwatchable with NVIDIA drivers choppy"
date: 2018-02-26
forum: Multimedia Software
---

### Post by justin76 on 2018-02-26
Good afternoon everyone! I hope this is the right place for this. Basically I have a Sony Vaio that was bought several years back as a movie playing laptop. When I had Windows on it, it would run HAD movies flawlessly without any issue. 

I moved over to Linux because I wanted to try something new and although I don't primarily watch movies on this laptop, sometimes I want to hook it up to my TV through HDMI and watch videos. Regardless though, if it's HDMI or the laptop screen, any movie file I try to watch is completely unwatchable. The sound usually plays without issue but the video skips, freezes, breaks up, and generally distorts in some fashion for 80% of the file. 



I'm running Ubuntu 17.10 because I was having this issue with 16.04. the graphics card is an NVIDIA GeForce G21M using the NVIDIA binary driver 340.106. There's also an option for 'legacy binary driver 304.137' and 'X.Org.X Server'. It's also showing a second device called 'Unknown: unknown' saying it is using an alternate driver. It's default selected to one that says 'Using processor microcode firmware for Intel COUs from Intel microcode.' The second option for this unknown device is 'Do not use this device'. I'm not sure what the best selection for these drivers should be. 

I've tried a few different things to fix the video, but nothing so far has worked. Here's the list of things I've gotten from online...

I'm using VLC 2.2.6-6

1. Apt-get update and upgrade.
2. Tried Mplayer
3. Changed file buffer length in VLC to 1500 ms
4. Turned off hardware acceleration
5. Turned off loop filter.
6. Changed output to opengl.


Does anyone have an idea of how to resolve these issues? I mean I know this hardware is capable of watching video files without issue

********************************************************************************************************************************************************************************************************************
 
Update! Problem solved. Not much help from the forums, but it's all good! Here's the solution if you happen to share this problem. I have been successfully watching several different videos that are all HD and very large (up to 5 gigs). Before I fixed it they were completely unwatchable, but now they are running perfectly like it's a theater. Literally every single issue I was having is now gone. It's running video files no problem. 

Here are the steps in case anyone else is having the same problems. This seems like a solid solution. 

1. Sudo apt-get update; sudo apt-get upgrade

2. Switched from NVIDIA Binary Driver 340.106 and went to the NVIDIA Legacy Binary Driver 304.137. I think this part is what really fixed it, but I'm not sure what it changes. 

3. VLC reset preferences

4. Simple Preferences - Input Codecs : 

(A) hardware accelerated decoding set to "Automatic". 

(B) Skip H.264 in-loop deblocking filter set to "None"

5. Simple Preferences - Video

(A) Output set to "Automatic"

(B) Deinterlacing set to "Off"

6. Advanced Preferences - Input Codecs

(A) Go to Advanced section at bottom and find the File caching, Live Capture caching, Disc caching, and Network caching. They should each be set to 2000 milliseconds.

---

### Post by SeijiSensei on 2018-02-27
You need to use the built-in decoding software built into the NVIDIA chip, called "VDPAU".  In mplayer you can add "-vo vdpau" to the command line, or use a GUI front-end like SMPlayer where you can specify it in the Preferences.  These days, though, I'd recommend mpv over mplayer.  SMPlayer supports both engines.

---

### Post by justin76 on 2018-02-27
Is there no way to enable this while using VLC?

---

### Post by justin76 on 2018-02-28
So I just wanted to give an update that I think I have resolved this finally. I have been successfully watching several different videos that are all HD and very large (up to 5 gigs). Before I fixed it they were completely unwatchable, but now they are running perfectly like it's a theater. Literally every single issue I was having is now gone. It's running video files no problem. 

Here are the steps in case anyone else is having the same problems. This seems like a solid solution. 

1. Sudo apt-get update; sudo apt-get upgrade

2. Switched from NVIDIA Binary Driver 340.106 and went to the NVIDIA Legacy Binary Driver 304.137. I think this part is what really fixed it, but I'm not sure what it changes. 

3. VLC reset preferences

4. Simple Preferences - Input Codecs : 

(A) hardware accelerated decoding set to "Automatic". 

(B) Skip H.264 in-loop deblocking filter set to "None"

5. Simple Preferences - Video

(A) Output set to "Automatic"

(B) Deinterlacing set to "Off"

6. Advanced Preferences - Input Codecs

(A) Go to Advanced section at bottom and find the File caching, Live Capture caching, Disc caching, and Network caching. They should each be set to 2000 milliseconds.

---

### Post by monkeybrain20122 on 2018-02-28
> **justin76 said:**
> Is there no way to enable this while using VLC?
Yes, choose VDPAU in Video>output and  Input/codecs hardware acceleration. But vdpau works better in Smplayer+mpv than vlc. Here vlc vdpau doesn't work on some .mkv files but mpv works for all of them, and when vlc works with vdpau, cpu usage of vlc+vdpau is about 2x that of mpv+vdpau (though both are low, a difference between something like 12% and 6% of cpu with vdpau)

---

