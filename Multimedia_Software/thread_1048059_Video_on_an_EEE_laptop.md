---
title: "Video on an EEE laptop"
date: 2009-01-23
forum: Multimedia Software
---

### Post by schnerf on 2009-01-23
So I got a new EEE for Christmas, and decided to try this ubuntu thing again. it never worked on wireless on my other computers, but this one seemed promising.

So I get it set up, and I settle in to watch a video.

But I had some problems with Totem - subtitles didn't work well at all, though I managed to fix the abjectly horrible tearing with a switch to overlay video instead of textured - though the video looked worse, banding and whatnot.
So I tried VLC, which didn't do well with subtitles either, and had major tearing problems which I couldn't seem to fix at all.
SMplayer handles the subtitles quite nicely - almost perfectly.
But the video tearing is driving me up the wall.

So I changed the output to overlay (xv:port=90) and the tearing is gone.
At least, it sure seems to be gone. But then the video contrast/gamma/hue/etc is so bizarrely screwed up that I can't do anything about it. When I get it set for some codecs, it doesn't work for others, and there's only one "default". If I have to write it down each time what each video needs, that's not effective. 
And besides, the overlayed video has those banding problems and generally lower quality than textured. Except textured video TEARS ALL THE TIME. 

Is there a way to make the textured video output sync so that there's no tearing issues?
Is there any fix for this?
Or is this just another lesson learned - Windows, for all its problems, just works?

---

### Post by wolfen69 on 2009-01-23
which version of ubuntu did you use?

---

### Post by rvm4000 on 2009-01-23
> **schnerf said:**
> So I changed the output to overlay (xv:port=90) and the tearing is gone.
At least, it sure seems to be gone. But then the video contrast/gamma/hue/etc is so bizarrely screwed up that I can't do anything about it. 

What version of smplayer are you using? I think that problem is fixed in the latest versions.

---

### Post by Tomatz on 2009-01-23
The following should work. You need to switch to X11 video output. Videos will be slightly pixallated (on a large screen anyway) but the tearing or other problem's shouldn't occur again.

To do this for the 3 main media players (only do what is appropriate):

> GSTREAMER:
For Totem with the gstreamer backend (totem-gstreamer) open a terminal and type gstreamer-properties
Then click the Video tab and under Default Output select X Window System (No Xv) for the plugin. Then restart Totem. This will work for any video application that uses gstreamer as it's video backend.

MPLAYER:
If you use MPlayer (GMplayer) right-click on the screen and select Preferences then select the Video tab and under Available Drivers select X11 (XImage/Shm)
then restart MPlayer. The issue here is that it won't go fullscreen with the video. I suggest using VLC or totem-gstreamer.

XINE:
If you use Xine then go to File -> Configure -> Preferences.
(make sure under experience_level you select Master Of The Known Universe)
You will get a tab at the top for Video. Under driver select xshm. Then restart Xine. This also works if you are using the totem-xine backend. Just run gxine at the terminal and follow the steps.

VLC:
For VLC select Settings -> Preferences then in the bottom-right of the window check the Advanced Options box. Then expand the Video item on the left and select Output modules. Then in the list on the right for Video output module change it to X11 video output. Then restart VLC

This is due to a bug in the intel gpu drivers ;)

---

### Post by schnerf on 2009-01-23
> **wolfen69 said:**
> which version of ubuntu did you use?

It's EasyPeasy 1, which is basically 8.10 with EEE drivers and netbook remix (which I removed). I had this same question on their forum for four days and no replies, so I'm asking here.



RMV4000:  I'm using .6.1 SVN r1304  with mplayer 1.0 rc2 (which I can't figure out how to update (did I mention I'm new at this?))   I tried installing the latest one from the smplayer website, which seemed nice.
Except it didn't display ANY video for .MKV files.
At all. No matter what settings I put it on - it's like the media splitter didn't recognize the video stream.

Tomatz: X11 tears worse than textured video. When I said I had switched the video to overlay, that's what I did with xv: port=90 in the mplayer options.

the eee 900a has two video ports apparently, textured and overlay. Textured is port 72, overlay is port 90.
When I put it on overlay, it freaks out, and the color/hue/saturation/gamma is bizarre - on some codecs. I can make it reasonable,until I watch a different file, when it suddenly looks like I'm watching through smoked glass. So I reset it. Then I go back to another video, and it's back to freaking out. That's not right. And through all of this, the overlay just looks worse than textured.
But textured video tears. A lot. Like if theres ANY movement on the screen.


So where do I go from here?

---

### Post by snowpine on 2009-01-23
Hi Schnerf, I don't own a 900a personally, so take my advice with a grain of salt. I think the issue is the SSD in your 900a, which is notoriously slow. It just can't keep up with the video. Lots of 900a owners are upgrading to a faster drive: [http://forum.eeeuser.com/viewtopic.php?id=54112](http://forum.eeeuser.com/viewtopic.php?id=54112)

Have you tested video with Windows on your eee? Until you do that, there's no way to know whether it's a Windows vs. Linux issue, or a slow SSD drive issue. :)

---

### Post by Tomatz on 2009-01-23
> **schnerf said:**
> It's EasyPeasy 1, which is basically 8.10 with EEE drivers and netbook remix (which I removed). I had this same question on their forum for four days and no replies, so I'm asking here.



RMV4000:  I'm using .6.1 SVN r1304  with mplayer 1.0 rc2 (which I can't figure out how to update (did I mention I'm new at this?))   I tried installing the latest one from the smplayer website, which seemed nice.
Except it didn't display ANY video for .MKV files.
At all. No matter what settings I put it on - it's like the media splitter didn't recognize the video stream.

Tomatz: X11 tears worse than textured video. When I said I had switched the video to overlay, that's what I did with xv: port=90 in the mplayer options.

the eee 900a has two video ports apparently, textured and overlay. Textured is port 72, overlay is port 90.
When I put it on overlay, it freaks out, and the color/hue/saturation/gamma is bizarre - on some codecs. I can make it reasonable,until I watch a different file, when it suddenly looks like I'm watching through smoked glass. So I reset it. Then I go back to another video, and it's back to freaking out. That's not right. And through all of this, the overlay just looks worse than textured.
But textured video tears. A lot. Like if theres ANY movement on the screen.


So where do I go from here?

As said, set the players how i showed you. Fixes the issue on my eee ;)

---

### Post by schnerf on 2009-01-23
It's not the SSD. If the thing couldn't read faster than about 5 megabytes a minute, you might have something there.
If switching it to overlay didn't fix it, you might have something there.
But it's not the SSD - it does it on the SSD, on a SD card, on a USB drive.
It stops when you switch to overlay.
But overlay video has its own set of (significant) problems.


And while x11 works on your eee, it's not the overlay port on a 900a, so it still tears. Yes, I tried it, yes I reset the player, yes, it still tears quite badly.

in mplayer, in smplayer, etc. Also, on x11, you get one size for that video. it doesn't change size no matter what I tell it to.

So where do we go now?

---

### Post by Tomatz on 2009-01-23
> **schnerf said:**
> It's not the SSD. If the thing couldn't read faster than about 5 megabytes a minute, you might have something there.
If switching it to overlay didn't fix it, you might have something there.
But it's not the SSD - it does it on the SSD, on a SD card, on a USB drive.
It stops when you switch to overlay.
But overlay video has its own set of (significant) problems.


And while x11 works on your eee, it's not the overlay port on a 900a, so it still tears. Yes, I tried it, yes I reset the player, yes, it still tears quite badly.

in mplayer, in smplayer, etc. Also, on x11, you get one size for that video. it doesn't change size no matter what I tell it to.

So where do we go now?

Hmmm thats strange? Are you running compiz?

---

### Post by Tomatz on 2009-01-23
Open a terminal and type:

```
metacity --replace
```

If you are running compiz, then try a video ;)


EDIT:

Obviously not as you run eeeubuntu (easypeasy).

---

### Post by schnerf on 2009-01-23
well, there was a video driver update this morning.
I'm busy for a few hours, though.
I'll see if it helped.

---

### Post by rvm4000 on 2009-01-23
> **schnerf said:**
> RMV4000:  I'm using .6.1 SVN r1304  with mplayer 1.0 rc2 (which I can't figure out how to update (did I mention I'm new at this?))   I tried installing the latest one from the smplayer website, which seemed nice.
Except it didn't display ANY video for .MKV files.
At all. No matter what settings I put it on - it's like the media splitter didn't recognize the video stream.

Try enable or disable the correct pts option in preferences -> advanced. If that doesn't fix it, take a look at the mplayer log (options -> view logs), probably mplayer is complaining about something.

---

### Post by schnerf on 2009-01-26
It seems that the video driver update fixed it fairly well.

Is there a way to know when those driver updates come out, or if another update will cause more problems, etc?
If I hadn't been looking, I don't know that I would have gotten that update.

---

### Post by Tomatz on 2009-01-26
> **schnerf said:**
> It seems that the video driver update fixed it fairly well.

Is there a way to know when those driver updates come out, or if another update will cause more problems, etc?
If I hadn't been looking, I don't know that I would have gotten that update.

I turn the update notifier off. You can update manually via a terminal or synaptic if you get a problem or need something updated for some reason.

An old man once told me *"if it ain't broke, don't fix it"*...

;)

---

### Post by schnerf on 2009-02-02
Ok, I'm bumping something that's a little old, but I have a new problem that's related.
I've been watching videos, it's all been awesome, the video is nice and clear and it looks great.

And then I decided that one video was too loud, so I reached up to push 9on the keyboard to change the volume.
I missed.
8 apparently adjusts those iamge equalizer things, and the instant I touched it, it's back to all the previous problems - EXTREMELY bright, oversaturated, etc.

and it does that on all the videos now, again.
Also, now, when I watch anything, it starts, pauses, chokes, and then I unpause, it flashes, and pauses, I pause again and it goes.

What the heck happened, and how do I bring it back to working well?

---

### Post by Tomatz on 2009-02-03
> **schnerf said:**
> Ok, I'm bumping something that's a little old, but I have a new problem that's related.
I've been watching videos, it's all been awesome, the video is nice and clear and it looks great.

And then I decided that one video was too loud, so I reached up to push 9on the keyboard to change the volume.
I missed.
8 apparently adjusts those iamge equalizer things, and the instant I touched it, it's back to all the previous problems - EXTREMELY bright, oversaturated, etc.

and it does that on all the videos now, again.
Also, now, when I watch anything, it starts, pauses, chokes, and then I unpause, it flashes, and pauses, I pause again and it goes.

What the heck happened, and how do I bring it back to working well?

Does it do this in ALL media players?

---

### Post by schnerf on 2009-02-03
It doesn't seem to.

I reinstalled smplayer (removed with all configuration) and reinstalled, and that fixed the colors.

But when I double click on a media file, it starts blue (overlay), and plays the music.
I pause it, and it disappears, and then comes back blue, but stopped.
ThenI unpause it, it disappears, and comes back, and I see a static shot of the opening scene, with music. Then I pause it again, (disappears, reappeears) and then unpause, and after a flash, it plays like normal.

So it works. I just have to pause and unpause a few times to get to see anything.

I have no idea what precipitated this.
It started when I hit the saturation hot-keys.
I dont know what's going on at all.

---

### Post by Tomatz on 2009-02-04
Really, you should install easy peasy (ubuntu eee). It will save you all these problems.

[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

---

### Post by schnerf on 2009-02-04
I'm already running it - I said so in post 5. 

So it didn't really fix it.
Really, the visual settings are off, but they're in a place as default that works.
I assume that's what that's for.

but the never starting properly, having to pause, unpause, pause, unpause, with a second break in between because the whole window disappears for a moment before I can do anything - that's annoying.
it didn't do that before.

---

### Post by Tomatz on 2009-02-04
> **schnerf said:**
> I'm already running it - I said so in post 5. 

So it didn't really fix it.
Really, the visual settings are off, but they're in a place as default that works.
I assume that's what that's for.

but the never starting properly, having to pause, unpause, pause, unpause, with a second break in between because the whole window disappears for a moment before I can do anything - that's annoying.
it didn't do that before.

Its such an "off the wall" problem TBH. I've never came across this before and to my knowledge there are no settings that determine video output config "across the board" (as in video not X). Have you tried **MPlayer** and do flsah (youtube) videos do this? 

Must be really frustrating! :(

---

### Post by schnerf on 2009-02-05
ok.
soit doesn't have any of the problems in mplayer.
only smplayer.
I've "completely removed" and reinstalled smplayer, and it still has the problems.
Is there a more complete removal so that I can get a REALLY clean install of smplayer?

---

### Post by rvm4000 on 2009-02-05
What problems do you have with smplayer? If mplayer plays the files without problems, smplayer should do it as well.

Anyway to uninstall smplayer:
sudo apt-get --purge remove smplayer

To remove the smplayer config files, delete the directory $HOME/.smplayer (or $HOME/.config/smplayer in newer versions)

---

### Post by schnerf on 2009-02-05
Awesome.

Deleting the config files in ~/.config/smplayer/ made it perfectly back to normal ( after I reset it to overlay video).
I had tried deleting ~/.smplayer/ files, and that didn't work - those must be from a previous version, then?

It works again.
I still have no clue what happened - but it works again.
I suppose I did save that bad .ini file, so maybe I could check the difference between it and the new one that works. 

If I figure out how to compare them, I'll post the differences.





- I can post pretty much any part of the diff. This seems to be an important part.
177c177
< temp\autoport=52596
---
> temp\autoport=47154

but I don't know.

---

### Post by ottogiugno on 2009-04-28
Hi.
I have just installed Ubuntu 9.04 on my eeepc 900A and the XviD playback isn't as good as it was with Windows Xp (and Ubuntu eee before).

Could you please tell me what I shold adjust and how?
Thanks.

---

