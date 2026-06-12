---
title: "Unable to play DVD's in Feisty"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by nedmas on 2007-04-21
I have just freshly installed feisty and tried to play a DVD, i have followed every HOWTO and thread i can find but i'm unable to solve the problem.

I have installed:
[INDENT]libdvdcss2[/INDENT]
[INDENT]libdvdread3[/INDENT]
[INDENT]libxine1[/INDENT]
[INDENT]libxine1-ffmpeg[/INDENT]
[INDENT]libxine-extracodecs[/INDENT]

Totem-xine says: "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

And Mplayer says: "Failed to open dvd://1"

If anyone can help me solve this problem i'd be most thankful.

---

### Post by phreeq on 2007-04-21
I'm running into the same problem

I have found that even though I can't play the DVD, vobcopy is ripping them. Nothing else would rip, but vobcopy will.

---

### Post by RomeReactor on 2007-04-21
Hi. According to [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_play_DVD.27s") it seems like you missed a couple of libraries:

```
sudo aptitude install libdvdnav4 libdvdplay0
```

---

### Post by phreeq on 2007-04-21
> **RomeReactor said:**
> Hi. According to [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_play_DVD.27s") it seems like you missed a couple of libraries:

```
sudo aptitude install libdvdnav4 libdvdplay0
```

I checked, and I do have both of those packages installed

---

### Post by RomeReactor on 2007-04-21
phreeq, does your Totem-Xine display the same error nedmas posted?

---

### Post by phreeq on 2007-04-21
Yes, it is the same message.

---

### Post by Antilavista on 2007-04-21
I getting exactly the same error in Mplayer but Totem gives this error:-

¨Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.¨

Í got round it by installing VLC (avaliable in Synaptic) which plays DVD ok but would still like to find a fix for this.

---

### Post by DoktorSeven on 2007-04-21
totem-gstreamer gave me that error with libdvdcss2 installed, but totem-xine (and plain xine-ui) played a DVD fine.

---

### Post by phreeq on 2007-04-21
> **Antilavista said:**
> I getting exactly the same error in Mplayer but Totem gives this error:-

¨Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.¨

Í got round it by installing VLC (avaliable in Synaptic) which plays DVD ok but would still like to find a fix for this.

I have VLC installed...but it won't play the DVD either. I don't get an error, it just quits.

---

### Post by omegamormegil on 2007-04-22
If VLC "just quits" you may have to tell it where your DVD-Rom device is.  Go to File > Open Disk, and look to see if the Device Name field is empty (or maybe incorrect).  It should say something like /media/cdrom.  To get this to be filled in automatically each time you start VLC go to Settings > Preferences> Input Codecs and scroll to the Default Devices section.  If the Audio CD device field is already filled in, you can probably copy whatever is there to the DVD Device field if you use the same drive for both (ie a CD/DVD combo drive).  Otherwise, your DVD Device should be listed in /media.

---

### Post by Pino_ptrs on 2007-04-25
Just go [here]("http://www.dtek.chalmers.se/groups/dvd/deb/") and download the right deb ("libdvdcss2_1.2.5-1_i..> 11-Feb-2003 23:08   25K" worked fine for my i386) install it and enjoy!

---

### Post by Temis on 2007-04-27
I have exactly the same problem: mplayer failed to open dvd://1. I have tried all the suggestion in this thread but no luck. I have upgraded to feisty and checked all repositories except  drake and edgy. Actually I was never able to make mplayer work.  Totem woks perfectly. ????????

---

### Post by kdub432 on 2007-04-28
for me, the only thing that will work is mplayer dvd://1
I really want totem and vlc to work though!!! I have all the packaged listed here installed. any help would be appreciated. :-)

---

### Post by Double-X on 2007-04-28
This worked for me, I had the same problem til 5 min's ago.

Mplayer:
- Right click the display-screen.
- Preferences
- Tab: Video
- Select other display driver (I selected: X11 OpenGL Multi Textures)
- Save Changes

VLC Player:
- Settings
- Preferences
- Fold open Output Modules
- Select Advanced (bottem of the window)
- Select Video output module (I select: OpenGL Video Output)
- Save Changes.

[geek mode]
I dunno totem, I'm a big n00b stil.
But eager to learn 
[/geek mode]

---

### Post by Temis on 2007-04-29
[QUOTE=Double-X;2554118]This worked for me, I had the same problem til 5 min's ago.

Mplayer:
- Right click the display-screen.
- Preferences
- Tab: Video
- Select other display driver (I selected: X11 OpenGL Multi Textures)
- Save Changes

I tied this. No go. Still: Mplayer failed to open dvd://1

---

### Post by OmegaInstigator on 2007-05-02
I had problems with those methods, too, but they put me on the right track. I wouldn't know about Mplayer and only used VLC -- but it wasn't OpenGL I wanted. When I selected X11 video it worked perfectly. Hope that's helpful.

---

### Post by gtemedtk1 on 2007-05-04
I am having this problem with mplayer....it is trying to open files such as my /home folder and cdroms which have no video or music on them such as AptOnCD. Has anyone got an idea how to fix this?


Gordon Eldridge

---

