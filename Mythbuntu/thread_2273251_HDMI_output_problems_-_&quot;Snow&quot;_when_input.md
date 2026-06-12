---
title: "HDMI output problems - &quot;Snow&quot; when input changes to HDMI"
date: 2015-04-11
forum: Mythbuntu
---

### Post by granicus on 2015-04-11
I recently purchased the ECS Liva hardware listed in the following post in order to set up a remote frontend:

[http://ubuntuforums.org/showthread.php?t=566529&page=38&p=13226401#post13226401](http://ubuntuforums.org/showthread.php?t=566529&page=38&p=13226401#post13226401)

I installed Mythbuntu 14.04.2 using the Pendrive Linux installer, and upon installation ran all the updates that I was prompted for after installation.  My TV has both VGA and HDMI inputs, and I currently have cables connecting both from the computer to the TV.  At this point, while connected to my TV via VGA, I can connect to my backend and play shows (no sound).  However, when I switch to the HDMI input, all I get is digital "snow".

I've found if I shut the computer down completely and reboot while on the HDMI input, it will boot fine outputting to HDMI (there is still no audio, but I believe that to be a separate issue). 

At this point just after booting on the HDMI input, xrandr shows "HDMI1 connected 1920x1080+0+0".  

However, if I change off of the HDMI input and back to HDMI, it goes back to the "snow".  Going back to the the VGA input, I can see xrandr now shows "HDMI1 disconnected 1920x1080+0+0".

I have also followed the instructions found here in order to enable the intel graphics driver repository (updating the commands for 14.04/trusty):

[http://www.webupd8.org/2013/04/how-to-use-intel-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/how-to-use-intel-linux-graphics-drivers.html)

The updated intel drivers do not seem to have any effect.

As a side note, I also have disabled screensaver and xfsettingsd from starting as xfsettingsd had caused a similar issue on my primary fronted/backend such that when switching off of HDMI input and back it would turn off the HDMI output and leave me with a blank screen.  To reiterate, that does not solve the "snow" issue.


Any ideas?

---

### Post by khPWXxF on 2015-04-12
I'm largely seeking clarification rather than proposing solutions.  You seem to allude to three issues:

1. Why do you want both HDMI and VGA connected?  Back in 2009 I thought I needed VGA for bios type operations, HDMI for viewing but I later learned that I could do everything with HDMI and life became much simpler.   What I did learn, after much head scratching, was that it was necessary to COLD boot after any display cable or configuration changes.  ie shut down, unplug power at power socket, press ‘start’ to discharge capacitors, then plug in again and boot up.
 
If you really want 2 devices then does this help (it is a rather old snippet)?
[http://www.nvnews.net/vbulletin/archive/index.php/t-129966.html](http://www.nvnews.net/vbulletin/archive/index.php/t-129966.html)
 
 
2.  HDMI sound – No doubt you have tried changing frontend > setup > Setup General > page 2 > Audio device?
 
3.  Your snow problem – is it related to the ‘no picture if TV turned on after frontend’ problem?
 
[http://www.gossamer-threads.com/lists/mythtv/users/570769](http://www.gossamer-threads.com/lists/mythtv/users/570769)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)
[http://ubuntuforums.org/showthread.php?t=2243778](http://ubuntuforums.org/showthread.php?t=2243778)
[http://ubuntuforums.org/showthread.php?t=2257014](http://ubuntuforums.org/showthread.php?t=2257014)
 
Sorry if I've missed your point!

Phil

---

### Post by novellahub on 2015-04-13
I have set up my Liva only using the HDMI port and do not have to use VGA. To get the audio to work in HDMI I had to unmute the audio in alsamixer.  I also installed pavucontrol to set the default sound output.

[https://apps.ubuntu.com/cat/applications/pavucontrol/](https://apps.ubuntu.com/cat/applications/pavucontrol/)

My Liva also has a quirk where I have to shut it down completely and not reboot.  If I do a reboot, it just sits on the BIOS boot up screen.

---

### Post by granicus on 2015-04-14
khPWXxF,

1) The only reason I connected the VGA port was because HDMI was giving me the snow, I don't have a need for both ports at all.  That one was only used because it allowed me to see what was going on with the box.

2) Yes, as I stated, separate problem.

3) Yes, it seems to be similar but not quite the same.  If I boot while on the HDMI port, I get picture. Actually, not 100% of the time, but about 80% of the time.  The other 20% of the time it boots straight to the "snow".  In the instances where HDMI does work on boot, if I change inputs on the tv or turn it off and on, I get "snow" (instead of the black screen everyone else gets).  On my main myth machine, I had the same problem as the other posters (black screen on input change/tv power off) and it was due to the xfsettingsd process seeing the port as being turned "off" and shutting it down but not powering it back in when input returned to that port.  The solution for my other machine was the solution I've seen elsewhere, disabling xfsettingsd completely.  That fixed my main machines problem, and was the first thing I tried here.  However, on this new Liva box I still get the snow and still get xrandr saying it has been disconnected even after disabling xfsettingsd.

---

