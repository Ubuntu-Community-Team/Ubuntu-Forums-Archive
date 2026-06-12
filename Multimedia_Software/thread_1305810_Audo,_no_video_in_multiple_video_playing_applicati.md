---
title: "Audo, no video in multiple video playing applications"
date: 2009-10-30
forum: Multimedia Software
---

### Post by CFBauer on 2009-10-30
Hello,

After upgrading to Karmic RC, I cannot play videos. I have universe and medibuntu as repositories, tried installing restricted-extras, tried reinstalling mplayer, and gstreamer, still no luck. I've also updated and upgraded.

VLC and Totem play audio but there is no video.

In **SMPlayer**, I get this error:

"MPlayer has finished unexpectedly. Exit code 127"

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 69206031 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/chris/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 /home/chris/Videos/King of the Hill - S05E15 - Luanne 2.0.avi -loop 0

/usr/bin/mplayer: error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory
```

I did check, libx264.so.67 is installed, but there is no file in usr/bin called "mplayer".

**VLC** does this:

```
No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.
```

**Totem** searches for plugins, but does this:

```
No packages with the requested plugins found

The requested plugins are:

XVID MPEG-4 decoder
```

Ive tried all types of video types. The "requested plugin" from Totem changes, but it is never found.

Any tips would be appreciated. Thanks.

-Chris

---

### Post by mushr00m on 2009-10-30
try installing libAVcodec52... it got the videos working for me.

---

### Post by CFBauer on 2009-10-30
> **mushr00m said:**
> try installing libAVcodec52... it got the videos working for me.
I have libAVcodec52-extra installed, not sure what the difference is.

Did Totem's "search for plugins" not work for you either?

---

### Post by CFBauer on 2009-11-01
Bump :). I miss watching videos.

Also, reinstalling from scratch is another option, but I have what I think is a Nvidia driver issue that will make re-installation a whole other can of worms.Basically my computer goes into what looks like standby mode after a few minutes of installation using the default Nvidia driver.

---

### Post by CFBauer on 2009-11-07
I've tried Ubuntu and Kubuntu live CDs, still no luck. This is awful.

$20 via Paypal to anyone who successfully helps me get this working, prefereably without a workaround.

---

### Post by CFBauer on 2009-11-08
Anyone have suggestions as to where I can look into this? I tried Googling obviously, not much look. Looks like Canonical offers support, which I don't mind paying for, but it's $50. Seems like a lot to have one question answered.

---

### Post by ypsilon1988 on 2009-11-08
I had the same problem and I was googling to no avail. I accidently found a solution by trial and error: in Synaptic, look for libx264. Select libx264-67. Then go to package > force version, and install the older version. I can use Mplayer, Totem (Xine) and VLC again now.

---

### Post by CFBauer on 2009-11-08
That did it, much appreciated. Unfortunately, all my videos are blue now, although I watched a DVD yesterday (before I changed the version of libx264) and it was also blue Weird.

Post or PM me your Paypal address.

---

### Post by CFBauer on 2009-11-08
Blue video sort of fix:

> **threetwoone said:**
> I am having a similar problem but I'm not sure.  Do the video's all look blueish?

I have an nvidia 9500m GS (using the 185 driver) and that is whats happening to me.  If you open up the "nvidia xserver settings" utility while the movie is playing it fixes it for me, you can close it after.  It isn't a fix but its an easy work around.  I was using the 185 with 9.04 and this wasn't a problem.  Maybe the one from the nvidia site won't have this problem?

It would seem that the setting for Hue (in the "X server XVideo Settings" tab) gets messed up when you play a video (mine was at -1000).  If you put it back to zero (or hit it reset hardware defaults button) then you can just open it to fix the movies like i mentioned before.

Unfortunately I don't even know how to start looking for a fix but I hope this helps.

[http://ubuntuforums.org/showthread.php?t=1308346](http://ubuntuforums.org/showthread.php?t=1308346)

---

### Post by ypsilon1988 on 2009-11-08
You're welcome. Don't know about the blue video thingy. I think I saw something about that floating around on the Google.
< Edit: Ah, there it is. >

I don't have a Paypal adress ;)

---

### Post by CFBauer on 2009-11-08
> **ypsilon1988 said:**
> You're welcome. Don't know about the blue video thingy. I think I saw something about that floating around on the Google.
< Edit: Ah, there it is. >

I don't have a Paypal adress ;)
Well you fixed a big issue for me, and I promised $20 do whoever did so. I can mail you a check?

---

### Post by ypsilon1988 on 2009-11-08
You really don't owe me anything. It was a big issue for you, but it took me less then five minutes typing in what I'd done. So no biggie. Plus you'd have to have that check shipped to Belgium. Go sponsor some charity or something ;)

---

### Post by CFBauer on 2009-11-08
> **ypsilon1988 said:**
> You really don't owe me anything. It was a big issue for you, but it took me less then five minutes typing in what I'd done. So no biggie. Plus you'd have to have that check shipped to Belgium. Go sponsor some charity or something ;)
The number of Euros $20 gets you wouldn't be pretty either. Thanks again.

---

### Post by chronos00 on 2009-11-14
> **ypsilon1988 said:**
> in Synaptic, look for libx264. Select libx264-67. Then go to package > force version, and install the older version.

Thanks!
This worked for me too. Not only for h264 videos, but for any video in general.
My problem began after upgrading to Karmic. Seems the repos got all mixed up.

Thanks again for the solution!

---

### Post by ronaldpianist on 2009-11-23
Hi,

I am completey unexperienced user, but never had any problems with video playback in Jaunty, yet I keep having problems playing the XVID video files in Karmic. I tried some solutions found on this forums, but still cannot get the playback - could you provide some simple guide what to do - I try to uninstall all the gstreamer and related packages now so I could start from scratch.

Thanks to the all Ubuntu community for those pages, without them I would already have to switch back to Windows...

R.

---

### Post by Sagoober on 2009-12-09
> **ypsilon1988 said:**
> I had the same problem and I was googling to no avail. I accidently found a solution by trial and error: in Synaptic, look for libx264. Select libx264-67. Then go to package > force version, and install the older version. I can use Mplayer, Totem (Xine) and VLC again now.

This just fixed my problem as well, thank you.

---

### Post by waltermuniz on 2009-12-09
> **mushr00m said:**
> try installing libAVcodec52... it got the videos working for me.
That's the real answer !!!!! Works for me two !!!! Thanks a lot !!!

---

### Post by doron387 on 2010-01-27
also for me. 
easy and simple.
i wish i knew why it is not installed as a default in karmic and why we have to waste time to look for these answers.
it just doesn't make good public relations to ubuntu.

if the issue is that it is restricted package or whatever - so add a document in the first time openning the distro with all the things that should be fixed.

hooray to to mushr00m

doron387

---

