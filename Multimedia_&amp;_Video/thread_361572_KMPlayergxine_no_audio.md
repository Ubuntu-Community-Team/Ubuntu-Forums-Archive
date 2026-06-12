---
title: "KMPlayer/gxine no audio"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by ktm5124 on 2007-02-14
I'm not getting any audio through KMPlayer or gxine but I am getting video. The audio driver for KMPlayer (which plays on xine) is set to back-end defaults. I tried some other drivers and they didn't work. Anyone know why I'm not getting any sound?

I get this when I play something:
```

andrew@roflbirds:~/Desktop$ kmplayer test.wmv
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kmplayer: View 54526195
kmplayer: PartBase::openURL file:///home/andrew/Desktop/test.wmvtrue
kxineplayer -wid 54526195 -f '/home/andrew/.kde/share/apps/kmplayer/xine_config' -vo xv -cb kmplayer-14309/KMPlayerCallback-0 -c
kxineplayer -wid 54526195 -f '/home/andrew/.kde/share/apps/kmplayer/xine_config' -vo xv -cb kmplayer-14309/KMPlayerCallback-0 -c
kmplayer: up and running kxineplayer-14322
kmplayer: processState Not Running -> Ready
kmplayer: Source::currentMrl document src:file:///home/andrew/Desktop/test.wmv
kmplayer: resolveURL file:///home/andrew/Desktop/test.wmv
kmplayer: document Mrl::activate
kmplayer: Source::currentMrl document src:file:///home/andrew/Desktop/test.wmv
kmplayer: CallbackProcess::play file:///home/andrew/Desktop/test.wmv
kmplayer: processState Ready -> Buffering
kmplayer: setMovieParams 154 320,240 1.33333
kmplayer: processState Buffering -> Playing
kmplayer: setMovieParams 154 320,240 1.33333
kmplayer: CallbackProcess::quit ()
kmplayer: PartBase::~PartBase
kmplayer: ~ConfigDocument
kmplayer: ~Document
kmplayer: ~Document
kmplayer: ~Document
kmplayer: ~Document
kmplayer: ~Document
kmplayer: ~Document
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x340018a
andrew@roflbirds:~/Desktop$

```

---

### Post by bobofett on 2007-02-19
I just wanted to chime in with my two cents.  I'm having exactly the same problem (except the input device is 169, and major opcode 147...but I suspect it's the same thing).  

Ktm could you try and run a video straight through xine from the command line?  

When I just run xine from the command line with no paramaters.  The video plays fine audio and all.  But it seems that anything else that uses xine in "plugin fashion" like KMplayer, gxine, and the Mozilla xineplugin all seem to play the video fine just no audio.

Ktm if you stumble on a solution for this, I would love to hear it, or if anyone else here has any ideas or maybe a nudge in the right direction, it would be much appreciated.

Thank you all.

---

### Post by panch0 on 2007-03-02
Have you tried an MPlayer based player like KPlayer? If it doesn't work right away, there are a few options to configure the sound output...

---

### Post by Mark76 on 2007-06-16
I had exactly the same problem when I tried to play a clip from the BBC website in Konqueror using the KMplayer.  With the xine option I get video (and it's pretty decent video, btw... even in FS mode) but no sound and with the Mplayer option I get sound and video, but lots of stalling.  I did think of installing KPlayer, but a quick trip to the repos (for Fiesty Fawn) revealed it to be conspicuously absent. 

 I should look elsewhere?

---

### Post by grauss on 2008-05-20
I have managed to solve this in my PC (Dell 755) Just go to configure at the KMPlayer, then go to General Options, then Output tab, then inside Audio list, I choose "Use back-end defaults".

Hope this works! Regards!

---

