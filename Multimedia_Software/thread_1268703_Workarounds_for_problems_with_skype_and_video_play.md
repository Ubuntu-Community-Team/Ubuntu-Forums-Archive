---
title: "Workarounds for problems with skype and video playback"
date: 2009-09-17
forum: Multimedia Software
---

### Post by dmkaplan2000 on 2009-09-17
Since making the jump from Intrepid to Jaunty, I have had many problems with sound and video.  Lots of things that have worked out of the box for a long time are now broken.  I am not sure what has caused this regression, but I have lost quite a bit of time trying to find workarounds to the various problems.  In the hope of saving the next person to come along some time and perhaps get some insight as to what is causing all these problems, I am posting here.  

The main two problems that I have been having are that sound has been hopelessly broken in Skype on both my laptop and desktop, and video playback has been broken on my laptop (I haven't really tried it on the desktop).  First sound:

For info, my laptop (a Lenovo 3000 v100) sound system is:

```

$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In skype, trying to make a call would respond with "problem with audio playback".  When run from the command line, skype would spit out:

```
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

```

There are a large number of bug and forum reports relating to this error output from skype and other sound applications, but I am fairly convinced this bug has almost nothing to do with the problems I am having.  I started along the road to finding the solution with the following Launchpad comment: 

[https://bugs.launchpad.net/medibuntu/+bug/285412/comments/9](https://bugs.launchpad.net/medibuntu/+bug/285412/comments/9)

in Launchpad [bug #285412]("https://bugs.launchpad.net/medibuntu/+bug/285412").  Basically, the problem was pulseaudio and the solution was to kill pulseaudio each time I log in with:

```
sudo killall -9 pulseaudio
```

or permanently from System->Preferences->Startup Applications->Pulseaudio.

This got sound output going, but I now found that sound input was not working.  Getting this going took some random fiddling around and testing.  A large part of the problem is that Skype gives me no less than 9 sound-in options (one being "Default"), System-Preferences->Sound also gives me 9 sound capture options, but no default and the rest are at the very least labeled differently (including two options that are both labeled identically "HDA Intel ALC883 Analog (ALSA)", but produce different results).  Furthermore, in the "Volume Control" mixer, I have three capture devices on the Recording tab (labeled simply as capture, capture 1 and digital), and two options on the options tab, both of which are labeled "Input source".   Needless to say, none of this makes much sense to me and Default didn't get it working on Skype.  

Finally, after much testing, I have found that gnome recording applications work if I set the capture device in System->Preferences->Sound to the SECOND "HDA Intel ALC883 Analog (ALSA)" option.  The first one doesn't work at all.  Lord knows why this is.  

In Skype, the Sound In option needed to be set to the fourth option, which is conveniently labeled "HDA Intel (hw:Intel,4)".  Curiously, the Sound Out option needed to be the "Default device" (in addition to killing pulseaudio), all other options failed.  

If anyone can make some sense out of all this, I would greatly appreciate some insight.

Next video:

For playing video files, just about any video application (for example, vlc) would end on my laptop with the following error:

```
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

```

Again, lots of bug reports on this one from a whole list of video applications.  I found out why in some random ubuntu bug report that I can't find anymore.  The Xv extension, which apparently allows GPU hardware acceleration of rescaling of video playback, was turned off for a class of video controllers, including mine (Intel Corporation Mobile 945GM/GMS, 943/940GM) in order to avoid some other (presumably worse) bug.  This essentially breaks all video out of the box on Jaunty (oddly, thinkings like YouTube still work).  

In the bug report, I remember some people fixing this by reverting to an old version of the video driver, but this appeared hard and dangerous.  An easier workaround for this problem is to use some other video output renderer (on applications that let you choose).  For example, on VLC I changed to Video Output setting from "Default" to "X11 video output".  This works for many, but not all videos, but unfortunately reduces quality and speed of the output.

Well, thats enough ranting.  Hopefully someone will find some truth in all this.

---

