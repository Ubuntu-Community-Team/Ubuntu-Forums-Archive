---
title: "XVID &amp; MP4 Not Working"
date: 2009-10-28
forum: Multimedia Software
---

### Post by jmadgin on 2009-10-28
Hi There!

I upgraded to Karmic yesterday! Everything so far has been working as expected though for some reason all of my videos mostly .AVI as XVid or MP4 will not play in any media application?? I usually use VLC though this gives me the message:

> No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.


In Movie Player I get this:

> Internal data stream error.

They appear to play the audio but not the video, this leads me to some problem with the restricted drivers? I've set up the medibuntu reps and installed all relevant restricted extras including w32codecs!!

I'm tearing my hair out! Anyone got any fixes?

---

### Post by vinutux on 2009-10-28
sounds like prob related to codec conflict

you have installed/upgraded some  codecs from third party repos like mediubuntu conflict with official codecs....

This is happens because of the codes from mediubuntu have higher version number than official version > Naturally when you are updated your system [after adding mediubuntu repo] your system upgraded to mediubuntu codecs.... 

Solution :

1. Disable mediaubuntu repo from synaptic > Settings > Third paty software/other software tab | Then reload synaptic

2. uninsatall vlc and mplayer 

3. reinstall all gstreamer-plugins [use search to find it]

4. uninstall softwares from **installed autoremoovable** [side bar of synaptic]
   or type this in terminal ```
apt-get autoremove
``` (close synaptic before doing this)

5. install vlc and mplayer again....

hopes it fix your prob..........:D

---

### Post by jmadgin on 2009-10-28
I'm afraid this didn't fix it. I did exactly as you instructed an I still have the same error message?

---

### Post by vinutux on 2009-10-28
Are you upgrading after adding mediubuntu repos ?

anyway try once again....

uninstall mplayer and vlc


```
sudo apt-get remove vlc 
```

```
sudo apt-get remove mplayer 
```

also uninstall all media related softwares too [in sound and video section only need pre-installed apps like rhythmbox,brasero,movie player and sound recoder  all other must be uninstalled]

disable mediubuntu repo from System > administration > software sources > third party tab | close


```
sudo apt-get update
```

```
apt-get autoremove
```


open synaptic search for gstreamer

right click and reinstall all gstreamer plugins and related apps there..............


did this once again

```
sudo apt-get update
```

```
apt-get autoremove
```

---

### Post by mc4man on 2009-10-28
vlc and mplayer don't use gstreamer plugins ( though they may benefit from libs installed as deps of some of the plugins. - see bottom list

Search ffmpeg in synaptic and mark the 'extra' versions of the ffmpeg libs for install and apply. (don't mark the current ones for removal

There are up to 7 available, the key ones would be libavcodec-extra-52 ; libavformat-extra-52 ; libswscale-extra-0 ; libpostproc-extra-51

(if you wish a fairly full gstreamer plugins then search gstreamer and install these gstreamer  plugins

bad  (1st listed
bad multiverse  (4th listed
ugly (1st
ugly multiverse ( 4th
gstreamer0.10-ffmpeg
pitfdll (allows limited use of w32codecs in gstreamer - somewhat broken in karmic atm

---

### Post by jmadgin on 2009-10-28
Once again,I've followed both of your instructions. I have checked and have all the relevant packages and have followed procedures of removing and reinstalling  relevant programs. This makes no difference?!!?

---

### Post by jmadgin on 2009-11-07
I ended up doing a fresh install of Koala, everything works fine now. I'm glad I partitioned my drive up into '/' and '/home' partitions! Makes re-installing the system a lot easier!

---

### Post by adampope on 2009-11-09
I still get the same error after following all your instructions. Since I've now removed all the software I use as per your 'remove all sound/video' apps step above I might as just reinstall Karmic. I guess that's the 'solution'.

---

