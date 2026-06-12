---
title: "Totem/movie player only plays frame by frame"
date: 2009-12-19
forum: Multimedia Software
---

### Post by Zeedok on 2009-12-19
I upgraded to 9.10 (from 9.04) yesterday and I have had problems playing .mov and .avi files in totem ever since. I have restricted extras installed and totem is able to open the file, but it just sits on the first frame.  You can advance frames one by one (so I don't think it is a codec problem, which I have reinstalled in any case) but the video will not play normally.

Any ideas how I could fix this?

EDIT: I installed VLC and the files play OK, do it seems to be a totem issue

EDIT 2: Reinstalling VLC obviously added a dependency - now it's working fine.

EDIT 3: Spoke too soon.  VLC still plays the files perfectly, but totem is stuck on the first frame again.

---

### Post by Zeedok on 2009-12-19
So the problem seems to extend to some other programs as well, for example pitivi and kdenlive.

---

### Post by Zeedok on 2009-12-19
This is curious.  I think the problem is to do with Gstreamer.  My videos play perfectly in xine (the standalone player) and vlc, but will not play in totem.  BUT . . . I have tried removing totem-gstreamer and replacing it with totem-xine, but this doesn't fix the problem.

It wouldn't matter that much (VLC works fine) but I believe Pitivi (and some other programs) use a Gstreamer backend, so I really need to sort this one out.

Can anyone please help?

---

### Post by Zeedok on 2009-12-20
Bump

---

### Post by Zeedok on 2009-12-20
Bumo x 2

---

### Post by Zeedok on 2009-12-20
Bump

---

### Post by houseworkshy on 2009-12-20
Not quite a bump but very similar.  After I put 9.10 in I found that videos were stalling visually whilst the audio continued,  After a few seconds the video would resume, in sync so some frames had been skipped.  Then due to other issues I formated then reinstalled the 8.04lts and the problem remained.  So I conclude that there is a general problem with totem and xine which started around the time 9.10 was releaced, the timeing may be coincidential rather than related.

---

### Post by Zeedok on 2009-12-20
> **houseworkshy said:**
> Not quite a bump but very similar.  After I put 9.10 in I found that videos were stalling visually whilst the audio continued,  After a few seconds the video would resume, in sync so some frames had been skipped.  Then due to other issues I formated then reinstalled the 8.04lts and the problem remained.  So I conclude that there is a general problem with totem and xine which started around the time 9.10 was releaced, the timeing may be coincidential rather than related.

Thanks for your input - I was getting lonely!!  Unfortunately, I think you problem is different to mine.  Totem will not play any videos (with either the Gstreamer or Xine backend) but with the standalone xine player, everything in fine.  Alternatively, Pitivi (which uses Gstreamer) doesn't work.

So I have deduced that the problem is with Gstreamer (I think) . . . I just don't know how to fix it!!

---

### Post by houseworkshy on 2009-12-22
I haven't been able to fix the problem but have found that VLC, another open source video player which is available in the repositories, seems to behave much better.  You could try that one out as an alternative.

---

### Post by Zeedok on 2009-12-22
> **Zeedok said:**
> I upgraded to 9.10 (from 9.04) yesterday and I have had problems playing .mov and .avi files in totem ever since. I have restricted extras installed and totem is able to open the file, but it just sits on the first frame.  You can advance frames one by one (so I don't think it is a codec problem, which I have reinstalled in any case) but the video will not play normally.

Any ideas how I could fix this?

EDIT: I installed VLC and the files play OK, do it seems to be a totem issue

EDIT 2: Reinstalling VLC obviously added a dependency - now it's working fine.

EDIT 3: Spoke too soon.  VLC still plays the files perfectly, but totem is stuck on the first frame again.

Thanks for the suggestion - VLC was one of the first alternatives I tried.

---

### Post by houseworkshy on 2009-12-22
Ah yes so you did, sorry tired eyes.  There isn't much I can think of.  If you haven't already it may be worth adding the mediabuntu repositories first and then adding the restricted extras next.  That might do it.  Could be drivers, nvidia's was a mess a few days ago ( The ubuntugeek website had a fix for them which got me out of my own pickle ).  I had a lot of issues after putting in 9.10 so went back to the 8.04lts where everything works.  You could also utterly remove totem using the terminal ( for details on how use the built in manual:- open a terminal and type "man" without the quotes in front of the command you want to know about, in this case it would be "apt-get" the option you'd need would be purge, the manual will tell you better than I could how to use it )  After that's done you should be able to do a clean reinstall, if that doesn't work then sorry I wouldn't know what to try next.

---

### Post by Zeedok on 2009-12-22
> **houseworkshy said:**
> it may be worth adding the mediabuntu repositories first and then adding the restricted extras next.  That might do it.

I'll give it a go.

EDIT: No luck.

> **houseworkshy said:**
> Could be drivers, nvidia's was a mess a few days ago ( The ubuntugeek website had a fix for them which got me out of my own pickle ).

Maybe - but every other video player works well.

> **houseworkshy said:**
> I had a lot of issues after putting in 9.10 so went back to the 8.04lts where everything works.

I might wait until 10.04LTS and do a clean install.

> **houseworkshy said:**
> You could also utterly remove totem using the terminal . . . After that's done you should be able to do a clean reinstall, if that doesn't work then sorry I wouldn't know what to try next.

Already tried it, no luck.

Probably should have mentioned it if I haven't already, but this machine is my HTPC and I am running a Mythbuntu install, with an Ubuntu desktop.  Maybe that has introduced slightly different packages or repos (even though Mythbuntu uses it's own internam player rather than gstreamer/totem.

Thanks for your efforts - I appreciate the suggestions (just wish they had worked!)

---

### Post by mc4man on 2009-12-22
have no experience with mythubuntu, but anyway... all the players you're having success with don't use the gstreamer plugins so you might as well try this

```
sudo apt-get clean && sudo apt-get update
```

```
sudo apt-get --purge remove gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by davidryderuk on 2009-12-23
Have you tried changing the different options available in "gstreamer-properties"? It should allow you to set which video output is used by default. 

I would suggest choosing "X Window System (X11/XShm/Xv)" as your default plugin, then testing each of the available devices separately (if you have more than one).

---

### Post by Zeedok on 2009-12-23
> **mc4man said:**
> have no experience with mythubuntu, but anyway... all the players you're having success with don't use the gstreamer plugins so you might as well try this.

Didn't work I'm afraid.  

Thanks for the suggestion though.

---

### Post by Zeedok on 2009-12-23
> **davidryderuk said:**
> Have you tried changing the different options available in "gstreamer-properties"? It should allow you to set which video output is used by default. 

I would suggest choosing "X Window System (X11/XShm/Xv)" as your default plugin, then testing each of the available devices separately (if you have more than one).

No luck - I really can't work this one out . . .

---

### Post by Zeedok on 2009-12-23
When I started gstreamer-proerties I got this output from the terminal:

```
zeedok@zeedok-desktop:~$ gstreamer-properties

(gstreamer-properties:1101): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpython_d.so': /usr/lib/gstreamer-0.10/libgstpython_d.so: undefined symbol: _Py_RefTotal
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
zeedok@zeedok-desktop:~$ 
```

Could that be relevant??

---

### Post by mc4man on 2009-12-23
> Could that be relevant?? 

I haven't spent much time with gstreamer/gstreamer apps but probably not. You'd see that "GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer..." if you have python-gst0.10-dbg installed. 

The "unavailables' are expected.

Maybe install totem-dbg and see what you can uncover ( have almost no experience here debugging gst.

may give you some ideas

totem --help-gst 

I guess you could try this and see what shows up 

totem --gst-debug-level=1 /path/to/file

---

### Post by davidryderuk on 2009-12-24
```
No luck - I really can't work this one out . . .
```

Sorry, the point is that both totem and vlc player will probably use your graphics card to help in processing the video. However the exact method by which they process and display the video may vary. The gstreamer-properties application can tell you what methods of video acceleration are available on your computer and will allow you to test each one to see which one works best.

1. Open "gstreamer-properties" and go to the video tab.

2. Go to the "Video Output" section and click on the test button.

3. You should have a test video come up which is supposed to have moving static in the bottom right hand corner. 

4. If you can only see one frame in the test video (like the issue you mentioned in totem) then it suggests your problem may be to do with gstreamer applications in general.

5. The application allows you to test specific methods of video acceleration.To do this go to "Plugin:" and select "X Window System (X11/XShm/Xv)" from the drop down menu.

6. Then go to "Device:" and see if their is more than one option in the drop down menu. If there is, then test each option one by one. 

I'm afraid I can't help with debugging your warning message, but mc4man's advice seems pretty good anyway.

---

### Post by Zeedok on 2009-12-24
> **davidryderuk said:**
> ```
No luck - I really can't work this one out . . .
```

Sorry, the point is that both totem and vlc player will probably use your graphics card to help in processing the video. However the exact method by which they process and display the video may vary. The gstreamer-properties application can tell you what methods of video acceleration are available on your computer and will allow you to test each one to see which one works best.

Actually, I understood and tried your suggestion (the test video worked fine).  I mean I can't understand what the problem is.

---

### Post by davidryderuk on 2009-12-24
```
Actually, I understood and tried your suggestion (the test video worked fine). I mean I can't understand what the problem is.
```

Oh okay. 

Since you upgraded to ubuntu 9.10, have you tried getting rid of the old totem configuration files yet? 

I think they're at:

~/.gconf/apps/totem/

~/.config/totem/

and 

~/.cache/totem/

There are also the gstreamer configuration files that you might want to delete which I think are at:

~/.gstreamer-0.10

```
So the problem seems to extend to some other programs as well, for example pitivi and kdenlive.
```

Also have you seen the following thread about kdenlive?

[http://ubuntuforums.org/showthread.php?p=8377817#post8377817](http://ubuntuforums.org/showthread.php?p=8377817#post8377817)

and the bug report

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/459940](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/459940)

They both suggest that the package "frei0r-plugins" might conflict with gstreamer.

---

### Post by Zeedok on 2009-12-24
> **davidryderuk said:**
> Since you upgraded to ubuntu 9.10, have you tried getting rid of the old totem configuration files yet? 

I think they're at:

~/.gconf/apps/totem/

~/.config/totem/

and 

~/.cache/totem/

Didn't work unfortunately.

> **davidryderuk said:**
> There are also the gstreamer configuration files that you might want to delete which I think are at:

~/.gstreamer-0.10

Nor did this.

> **davidryderuk said:**
> Also have you seen the following thread about kdenlive?

Although I previously had "frei0r-plugins" installed -- it is a dependency for OpenShot, which I was trying to get working -- it is not currently installed.

Thanks.

---

### Post by mc4man on 2009-12-24
Because you mentioned 'openshot', might as well ck. something. (using the openshot dev.. ppa and letting it upgrade your ffmpeg libs will break totem.
The problem is it usually breaks vlc also.

So maybe search ffmpeg in synaptic and ck. the version number of libavcodec, libavformat, ect. (should be 4:0.5+svn[COLOR="Blue"]20090706[/COLOR]-.....

---

### Post by Zeedok on 2009-12-25
> **mc4man said:**
> Because you mentioned 'openshot', might as well ck. something. (using the openshot dev.. ppa and letting it upgrade your ffmpeg libs will break totem.
The problem is it usually breaks vlc also.

So maybe search ffmpeg in synaptic and ck. the version number of libavcodec, libavformat, ect. (should be 4:0.5+svn[COLOR="Blue"]20090706[/COLOR]-.....

They're all correct.

---

### Post by LMB on 2009-12-25
> **Zeedok said:**
> 

EDIT: No luck.




My problem was related to video drivers. I had the newest nVidia driver installed from console; this was replaced with version  183 from repositories, and now everything is back to normal. 

But perhaps my problem was slightly different: I had skippy video in all players, including Flash plugin (i.e. youtube)

---

### Post by mc4man on 2009-12-26
If you get a chance and inclination, try cli playback with mplayer of one of your .avi's. Not to see if it plays, more to ck. out the .avi itself. (mplayer will show some info on the files that may be informative.

mplayer /path/to/filename or mplayer -v /path/to/filename

While it's quite possible to continue to have a real working totem-xine, (instead of the current dummy in karmic and lucid), I don't think that will help you with your other apps as mentioned.

(unless they were using totem itself, then you could have 'totem' call totem-xine instead of totem-gstreamer, though I prefer to leave totem as is and have totem-xine standalone so to speak

---

### Post by Zeedok on 2009-12-28
Some progress at last - I think I have narrowed down where the problem is.

Mplayer (either from CL or from GUI) cannot play video files either.  There is a bunch of output from the CLI when using -v and a link to [this bug report]("http://www.pulseaudio.org/ticket/440").

I'm not sure if this is the same problem, but it is certainly similar.

This lead me to fiddle with my audio settings, with some configurations the video files play perfectly.  The issues I was having with flash ([see my other thread here]("http://ubuntuforums.org/showthread.php?t=1360390")) were also resolved.  So obviously, the problem is with the ALSA configuration (rather than Gstreamer).  The problem I now have is finding which hardware profiles (and switches) to use that maintain my "movie player" and "flash" playback, but don't break my Mythbuntu audio.

My system is connected to my AV amplifier via an optical output, and needs to send digital signals (I use the machine as a primary media PC).  I am currently using the "Digital Stereo Duplex (IEC958 )" hardware profile, which gives me audio in Mythbuntu and reproduces the error with video/flash playback. If I select another profile (I can't remember which one exactly) I can enjoy normal video playback and flash performance, but the Mythbuntu sound is broken.  

In the Myth setup dialogues, I have selected the sound output device as "ALSA:default".

Can anyone suggest a remedy, now that we have identified the problem??

---

### Post by Zeedok on 2009-12-28
I worked out that if I leave the audio device profile as "Digital Stereo Duplex (IEC958 )", but exit MythTV frontend, then my video and flash play fine, but if MythTV frontend is running, my problem persists.  I'm going to post this in Mythbuntu forum to see if anyone there has any suggestions.

---

