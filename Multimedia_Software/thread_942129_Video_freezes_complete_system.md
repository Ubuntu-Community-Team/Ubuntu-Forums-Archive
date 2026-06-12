---
title: "Video freezes complete system"
date: 2008-10-08
forum: Multimedia Software
---

### Post by hellmet on 2008-10-08
I'm using a Thinkpad R500 system with no graphics card (Integrated graphics). I installed Ubuntu-64 on my Core2Duo a few days back. I then fire up Totem and play an .avi file. It asks if I want to download codecs. I agree and let it download codecs. Then when it starts playing, it shows no video and within a matter of milliseconds, the entire system freezes. I then have to force shutdown the system. I tried playing several types of videos. Each time the same thing happens. Sometimes I can still move the mouse and Ctrl-Alt-Bksp doesn't work neither does Alt-Tab. 
Sometimes I can't even move the mouse.

I then think it might be some problem with 64Bit and so I install the 32bit version and still the same. 

Everything else works. Please help!

---

### Post by Everybody Loves Hypnotoad on 2008-10-28
I have the same problem I think. Sometimes a video avi or wmv wont begin playing in the default totem(?) based player, the video window is black but the audio works. Xorg freezes but the mouse cursor can still be moved around. Alt-sysrec+REISUB can often reboot the machine. This is with 8.04 on a HP laptop with the intel GMA950. VLC does the same, and more often than the default player.

edit; this is with all the evil codecs already installed.
edit2; went into synaptic and removed various junk related to video playback, only kept the ubuntu base install gstreamer set (like plugins good and gstreamer tools). Opened a wmv file that had given me troubles before, installed the ffmpeg and gstreamer plugins extra packages when totem asked me about that. Now it works. Too early to say if the freezing is cured though.

---

### Post by dustice on 2008-10-28
I'm having a similar problem with a Lenovo X200. I've tried removing/reinstalling various packages to no avail - Hypnotoad can you list for me exactly which packages you removed?

---

### Post by Everybody Loves Hypnotoad on 2008-10-28
What I do have installed that might be related to this issue is:

gstreamer-tools                                0.10.18-4ubuntu2
gstreamer0.10-alsa                             0.10.18-3   
gstreamer0.10-ffmpeg                           0.10.3-6  
gstreamer0.10-gnomevfs                         0.10.18-3 
gstreamer0.10-plugins-bad                      0.10.6-5ubuntu0.1      
gstreamer0.10-plugins-bad-multiverse           0.10.6-1  
gstreamer0.10-plugins-base                     0.10.18-3  
gstreamer0.10-plugins-base-apps                0.10.18-3   
gstreamer0.10-plugins-good                     0.10.7-3ubuntu0.1 
gstreamer0.10-plugins-ugly                     0.10.7-3ubuntu1   
gstreamer0.10-plugins-ugly-multiverse          0.10.7-1  
gstreamer0.10-pulseaudio                       0.9.7-2   
gstreamer0.10-tools                            0.10.18-4ubuntu2 
gstreamer0.10-x                                0.10.18-3   
libgstreamer-plugins-base0.10-0                0.10.18-3 
libgstreamer0.10-0                             0.10.18-4ubuntu2 
totem-gstreamer                                2.22.1-0ubuntu2
totem                                          2.22.1-0ubuntu2          
totem-common                                   2.22.1-0ubuntu2   
totem-gstreamer                                2.22.1-0ubuntu2 
totem-plugins                                  2.22.1-0ubuntu2   
libtotem-plparser10                            2.22.3-0ubuntu2   
totem-mozilla                                  2.22.1-0ubuntu2   

(dkgl -l | totem , and dpkg -l | gstreamer)
((edit: that's "dpkg -k" not anything else. ))

The stuff I removed was amongst other things (like the democracy player mplayer gxine...) the w32codecs pack.

---

### Post by hellmet on 2008-10-29
Same problem on Gutsy too. I moved on to Intrepid Ibex and I've no problems at all.

---

### Post by Everybody Loves Hypnotoad on 2008-10-30
Problem is back, or rather it didn't go away at all. And I don't want to dist-upgrade to get rid of bugs. :/

---

### Post by Fuzzy_Logic on 2008-11-25
I possibly have the same problem.
Yesterday, for the first time, and again today, my entire system freezes when watching (divx or possibly xvid) video with Totem. I did some googling, and the problem seems to be quite common. I also might have found a solution, but I haven't dared test it yet, as I am not sure what it does.

Check out this link: [http://blog.macuyiko.com/2008/06/is-w32codecs-freezing-your-ubuntu.html](http://blog.macuyiko.com/2008/06/is-w32codecs-freezing-your-ubuntu.html)

The problem sounds very similar to the one we are all experiencing, though the post refers to RealMedia files.

Or if you're to lazy, it basically gives these instructions:
> 1. Make sure you have gstreamer0.10-pitfdll installed.
2. Install (if you haven't already) w32codecs.
3. Execute the following three commands in the terminal:
   rm -rf ~/.gstreamer-0.10
   gst-inspect-0.10
   gst-inspect-0.10 pitfdll
4. Try Totem again. Should work now.

If you know what these commands do, or if you have the guts to try them, please answer, as I am very interested in a solution. :)

edit:
I tried installing MPlayer and using that instead, but the same problem occured; the image and sound froze, and the Caps Lock and Scroll Lock buttons were blinking. This means it's not a problem with Totem, so it might be codec-related?

edit 2:
Curses and damnations! I just had the same kind of freeze, and this time I wasn't watching anything, wasn't even running Totem or any other video-playing-app...

I fear this rules out this being a codec-issue, at least for me... There is a few apps I was running every time this happened, though: Pidgin, Transmission, possibly Skype. Skype might actually be the offender, I installed it either shortly before or shortly after this happened the first time. I'll try uninstalling it and see if the problem disappeares.

edit 3:
Did some searching in the forum, learned that hard freeze with flashing caps and num lock LEDs means a server panic has occured. 

Also found another thread discussing the same problem, but they seem convinced it's something to do with wlan-drivers. (I haven't read through all 19 pages yet, though...) [http://ubuntuforums.org/showthread.php?t=832383&highlight=freeze+caps+scroll+lock+blinking](http://ubuntuforums.org/showthread.php?t=832383&highlight=freeze+caps+scroll+lock+blinking)

---

