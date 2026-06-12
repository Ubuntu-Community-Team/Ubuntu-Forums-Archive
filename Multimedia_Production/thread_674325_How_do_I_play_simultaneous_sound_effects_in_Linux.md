---
title: "How do I play simultaneous sound effects in Linux?"
date: 2008-01-21
forum: Multimedia Production
---

### Post by CyrusComputers on 2008-01-21
I have spent almost 8 hours searching for a solution with no luck. I volunteer for a high school theatre group which uses linux to play all of their sound effects and videos, but I have been unable to find a way for one program to play more then one sound effect at the same time. I would use SFX by Stage Research for Windows or QLab for OSX, but both of those are not options because this school has very little money and no Macs. Does anyone know of an equivelant program for Linux, where I can configure it to play a large number of sound effects in a pre-specified order, play more than one at once, and have a GUI simple enough for a high school student to run it? Any help on this would be very much appriciated!!!

---

### Post by erginemr on 2008-01-21
I am not sure if this is what you are looking for, but with Audacity, you can play two (or more) sound tracks simultaneously.

When you install the application, use Tracks-> Add New...
and use File -> Import -> Audio...
to import a new track to the list.

Also refer to the following thread for more alternatives:
[http://ubuntuforums.org/showthread.php?t=671237](http://ubuntuforums.org/showthread.php?t=671237)

---

### Post by CyrusComputers on 2008-01-21
No, that's not what I'm talking about. I currently use Audacity to edit my audio files, but I need software for cue-based playback. Take a look at the SFX screenshot [here]("http://www.stageresearch.com/sales/cart/DBImageHandler.ashx?GeneralProductGuid=13ab915e-c300-43a7-9474-664c541b8535&ImageNumber=3&Width=900&Height=778") or the QLab screenshot [here]("http://figure53.com/qlab/images/screenshots/workspace.png").

---

### Post by erginemr on 2008-01-22
Then, please take a look at:
[http://www.linuxappfinder.com/alternatives](http://www.linuxappfinder.com/alternatives)
[http://www.linuxappfinder.com/multimedia](http://www.linuxappfinder.com/multimedia)

If there is a native Linux application that comes close to your needs, you should be able to find it here.

---

### Post by CyrusComputers on 2008-01-22
Unfortunately, I did not find anything there, and I look at every single one! I'm sure that there must be some other Linux user who is involved in theatre, and I'm hoping that they see this thread and reply!

---

### Post by prismatic7 on 2008-01-22
I'm also a theatre tech, so I've been interested in this problem for a while.

There is no current Linux equivalent for QLab or SFX. You may be able to run SFX under WINE, but I've never tried it so i can't help you there. Given the [frankly insane system requirements for SFX](http://www.stageresearch.com/products/SFX6/Requirements.aspx) I don't think it'll be much fun! 

Obviously, a program like QLab for Linux would be ideal - although Figure53 don't seem to have plans for such a beast.

Other ideas might be to use one of the DJ apps for Linux, like [Mixxx](http://mixxx.sourceforge.net/) or [DJPlay](http://djplay.sourceforge.net/). If you know anyone who's good with [Pure Data](http://puredata.info/) it might be possible to construct something.

---

### Post by CyrusComputers on 2008-01-22
> **prismatic7 said:**
> I'm also a theatre tech, so I've been interested in this problem for a while.

There is no current Linux equivalent for QLab or SFX. You may be able to run SFX under WINE, but I've never tried it so i can't help you there. Given the [frankly insane system requirements for SFX](http://www.stageresearch.com/products/SFX6/Requirements.aspx) I don't think it'll be much fun! 

Obviously, a program like QLab for Linux would be ideal - although Figure53 don't seem to have plans for such a beast.

Other ideas might be to use one of the DJ apps for Linux, like [Mixxx](http://mixxx.sourceforge.net/) or [DJPlay](http://djplay.sourceforge.net/). If you know anyone who's good with [Pure Data](http://puredata.info/) it might be possible to construct something.

I've tried SFX under Wine but it won't run because it tries to use a custom driver to access the our sound card and midi system. The requirements aren't an issue, we run Linux on a 2GHz dual-core machine with a state-of-the-art graphics card. I just tried Mixxx and DJPlay right now, and neither of them allow cue-based playback. As for Pure Data, it looks interesting but is realistically not viable because high school students need to run this equipment. I contacted Figure53 yesterday and they said that QLab has too many OSX-specific APIs to be portable to Linux. Oh well, thanks for the help anyway. I hope someone with more programming experience than I have will take a look at this thread and adapt an existing program, but I do not expect it. I guess it's back to Windows for this one.............

---

### Post by crush304 on 2008-01-22
have you tried hydrogen, it is a drum machine but I think the end result isn't too far off from what you are asking for

---

### Post by CyrusComputers on 2008-01-22
> **crush304 said:**
> have you tried hydrogen, it is a drum machine but I think the end result isn't too far off from what you are asking for

NO, that one actually one of the ones that I tried before I posted here. What I need does not need to create or edit files, but it should be able to play more than one pre-existing audio file at the same time, but only when I manually start each one.

---

### Post by prismatic7 on 2008-01-23
> **CyrusComputers said:**
> I've tried SFX under Wine but it won't run because it tries to use a custom driver to access the our sound card and midi system. The requirements aren't an issue, we run Linux on a 2GHz dual-core machine with a state-of-the-art graphics card. I just tried Mixxx and DJPlay right now, and neither of them allow cue-based playback. As for Pure Data, it looks interesting but is realistically not viable because high school students need to run this equipment. I contacted Figure53 yesterday and they said that QLab has too many OSX-specific APIs to be portable to Linux. Oh well, thanks for the help anyway. I hope someone with more programming experience than I have will take a look at this thread and adapt an existing program, but I do not expect it. I guess it's back to Windows for this one.............

I figured something like that might be a problem. There just doesn't seem to be any timeline/cue-based playback for Linux (yet)

You probably have already seen the helpful lists at [Blue Room](http://www.blue-room.org.uk/wiki/Sound_FAQ#Computer_Based_Playback_anyone.3F) and so forth, but I'll point that out for other theatre-lurkers!

And (OT) - check [this](http://qlc.sourceforge.net/index.php?doc=News) out! DMX lighting control for Linux! Just found it while searching for a solution...

---

### Post by CyrusComputers on 2008-01-23
Thanks for the link. Looking through the list of programs, Sound Cue System might have the needed features, and perhaps it does not try to install its own drivers. I will be very busy for the next few days, but I will install the demo version when I get a chance and post back with the results.

Also, nice find with the lighting software! We don't have a digital board, but we most cirtainly can use it to model our stage and lighting cues on the computer for a better lighting design.

---

### Post by prismatic7 on 2008-01-24
More searching has turned up [SoundPanel](http://www.salemradiolabs.com/soundpanel/) - more of a radio application than theatre, but definitely in the ballpark. It'd be nice to have something cue-list based, though...

---

