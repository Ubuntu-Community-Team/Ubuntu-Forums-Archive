---
title: "Is there a GOOD video player on Linux???"
date: 2008-05-13
forum: Multimedia Software
---

### Post by Kiri on 2008-05-13
Every video player I have used on linux so far is either buggy or doesn't really work properly, or is overly complex.

Is there any video player which just WORKS, and will let me view various video files? The only features I really care about is to be able to easily switch to full screen, support subtitles, and multiple audio streams. 

So far I have used SMPlayer, which would be good except that it seems really buggy on my machine and will not play many of my videos at all. 
VLC player which does well at playing a lot, but for some reason when I try to run it full screen it throws the video to my 2nd monitor. I know there are options to change this in the preferences, but they didnt seem to work when I changed full screen to be on a different X screen. 
In fact any of the options take a deal of effort to get to and change. 

I just want something simple that works. 

On windows, my favorite video player was kmplayer. And media player classic was also good. 



I have been using ubuntu for a few months now and love it. But unfortunately the only thing that makes me still use windows sometimes is the lack of stable, feature rich, easy to use software on linux :(

---

### Post by 3rdalbum on 2008-05-13
Try Gxine?

VLC is great; I have no idea why it's trying to use your second monitor though.

---

### Post by Archmage on 2008-05-13
> **Kiri said:**
> On windows, my favorite video player was kmplayer.

Did you try KMPlayer on Ubuntu? Maybe Mplayer would also be good.

---

### Post by rune0077 on 2008-05-13
Your VLC behaviour sounds odd. It's still the best player out there, so it may be worth the effort trying to get it fixed.

Otherwise, give plain ol' regular Totem-xine a go: it's really good, and way better (as in less buggy) than the Gstreamer Totem that ships with Ubuntu.

---

### Post by Lucky LIX on 2008-05-13
> **Archmage said:**
> Did you try KMPlayer on Ubuntu? Maybe Mplayer would also be good.

I'd also recommend Mplayer (without gui). Smplayer sometimes is a bit buggy here as well, but never had any trouble with basic Mplayer :)

---

### Post by Nameless_one on 2008-05-13
Check here for mplayer frontends, one of them is definitely going to suit you. 

[http://www.mplayerhq.hu/design7/projects.html](http://www.mplayerhq.hu/design7/projects.html)

---

### Post by cafeinoz on 2008-05-13
VLC is simple but still a great player.

---

### Post by rvm4000 on 2008-05-13
> **Lucky LIX said:**
> Smplayer sometimes is a bit buggy here as well

What problems are all of you having with smplayer?
I can't fix it if nobody reports them.

---

### Post by Lucky LIX on 2008-05-14
> **rvm4000 said:**
> What problems are all of you having with smplayer?
I can't fix it if nobody reports them.

You've got a point ;)

This is one annoying bug I found: when a film is closed in the middle of playback, it's meant to restart from that same point if you open it, say 5 minutes later, right? Most of the times I had some trouble on reopening the file, just checked what happened to one file I just tested: first just playing, I close and reopen, now the sound works but the screen is frozen (on the correct frame though), now when I double click it to get to fullscreen mode the film starts rolling again but the sound is out of sync...
Second bug I've just noticed: (sometimes, this does not happen every time, if you like I can look for a pattern*) when opening a video the audio works but the screen stays black (first frame?) until I choose to go fullscreen, fe forwarding does not help
* so far this is what I found: this only happens when the option to restart from the same time where you stopped last time is disabled, when opening a file for a first time, there is no problem, when reopening the same file after closing, the problem arises, it does not occur when you first open an other file (which just works) and then reopen the first file

I'd guess both problems are actually the same bug.

If you want more details or help testing, I'd be more than happy to help improve the project!

PS: I do like Smplayer, the interface is clean and quite simple, great for when you forgot some mplayer commands or for the rest of the family ;)

and just a thought: when trying to load subtitles from a file, it might be more convenient to open the folder in which the video file is located in stead of /usr/bin,
and some other idea, now I'm at it anyway, when choosing compact mode, it would be nice if the window itself actually got smaller and wouldn't just switch the 2 option bars to black, 'cause that makes the "compact" mode kind of useless as it isn't more compact imho

---

### Post by rvm4000 on 2008-05-14
> **Lucky LIX said:**
> You've got a point ;)

This is one annoying bug I found: when a film is closed in the middle of playback, it's meant to restart from that same point if you open it, say 5 minutes later, right? Most of the times I had some trouble on reopening the file, just checked what happened to one file I just tested: first just playing, I close and reopen, now the sound works but the screen is frozen (on the correct frame though), now when I double click it to get to fullscreen mode the film starts rolling again but the sound is out of sync...
Second bug I've just noticed: (sometimes, this does not happen every time, if you like I can look for a pattern*) when opening a video the audio works but the screen stays black (first frame?) until I choose to go fullscreen, fe forwarding does not help
* so far this is what I found: this only happens when the option to restart from the same time where you stopped last time is disabled, when opening a file for a first time, there is no problem, when reopening the same file after closing, the problem arises, it does not occur when you first open an other file (which just works) and then reopen the first file

I'd guess both problems are actually the same bug.

I have never experienced those problems. What version of mplayer are you using? What video and audio drivers do you have selected? Are you using Compiz by any chance?

> **Lucky LIX said:**
> If you want more details or help testing, I'd be more than happy to help improve the project!

PS: I do like Smplayer, the interface is clean and quite simple, great for when you forgot some mplayer commands or for the rest of the family ;)

and just a thought: when trying to load subtitles from a file, it might be more convenient to open the folder in which the video file is located in stead of /usr/bin,

When you select to load a subtitle, it should open the latest folder you used to load file.

> **Lucky LIX said:**
> 
and some other idea, now I'm at it anyway, when choosing compact mode, it would be nice if the window itself actually got smaller and wouldn't just switch the 2 option bars to black, 'cause that makes the "compact" mode kind of useless as it isn't more compact imho

It seems something easy but I tried several times, unsuccessfully. The window just doesn't resize. Maybe a bug in Qt, I should try with a newer version.

---

### Post by Lucky LIX on 2008-05-14
> **rvm4000 said:**
> I have never experienced those problems. What version of mplayer are you using? What video and audio drivers do you have selected? Are you using Compiz by any chance?
Turning of Compiz appears to fix the problem, but Ubuntu has Compiz activated after a basic installation so this might be a problem for many? Not to mention the fact many people like a tiny bit of eye candy ;)
Used mplayer package: mplayer-nogui 2:1.0~rc2-0ubuntu13
Video driver: I'm not sure, these are installed (in synaptic): nvidia-glx and xserver-xorg-video-nv (which one is the video driver or am I missing something?)
Audio driver: I don't know, worked out of the box and don't have time right now to google how to find out


> **rvm4000 said:**
> When you select to load a subtitle, it should open the latest folder you used to load file.
When clicking "Subtitles" and "Load..." while playing a movie which was openened using Nautilus the opened folder unfortunately is /usr/bin 


> **rvm4000 said:**
> It seems something easy but I tried several times, unsuccessfully. The window just doesn't resize. Maybe a bug in Qt, I should try with a newer version.
Hope you get that fixed, appreciate all the work you put in it!

Cheers

---

### Post by rvm4000 on 2008-05-14
> **Lucky LIX said:**
> Turning of Compiz appears to fix the problem, but Ubuntu has Compiz activated after a basic installation so this might be a problem for many? Not to mention the fact many people like a tiny bit of eye candy ;)

Yes, but it seems to me that Compiz has a lot of bugs. If smplayer works ok with Compiz disabled, then it's not a bug in smplayer but in Compiz.

Maybe I could try to work around some of these bugs, but the best would be that those bugs were fixed in Compiz.

> **Lucky LIX said:**
> Used mplayer package: mplayer-nogui 2:1.0~rc2-0ubuntu13
Video driver: I'm not sure, these are installed (in synaptic): nvidia-glx and xserver-xorg-video-nv (which one is the video driver or am I missing something?)
Audio driver: I don't know, worked out of the box and don't have time right now to google how to find out


I meant the "output drivers" that appear in the preferences dialog of smplayer, in the general section (xv, x11, gl...)

> **Lucky LIX said:**
> When clicking "Subtitles" and "Load..." while playing a movie which was openened using Nautilus the opened folder unfortunately is /usr/bin 


I see. I'll try to fix it.

---

### Post by inportb on 2008-05-14
Dragon player seems to be the epitome of simplicity. And it works rather well.

---

### Post by Lucky LIX on 2008-05-14
> **rvm4000 said:**
> I meant the "output drivers" that appear in the preferences dialog of smplayer, in the general section (xv, x11, gl...)

My bad, xv and pulse. Might altering these help?

---

### Post by SunnyRabbiera on 2008-05-14
well I personally like xine, its quite versatile.

---

### Post by wotringmw on 2008-05-14
Hey Kiri - Have you tried changing the fullscreen options in VLC?  I had trouble getting fullscreen to go to my second monitor - the solution was in the settings.

Go to settings - video - output modules - X11 then enable the advanced options and there should be a setting for which screen to use for fullscreen.

I hope that helps

 -MW

---

### Post by disturbedite on 2008-05-14
i don't mean any offense to you or anyone else.  but all these programs work fine.  prolly 75% of the time in my experience, it is the user's fault.  either not installing required codecs, or just generally not very knowledgeable on how things work.

smplayer is the best video player for linux there is imo.  it plays absolutely anything you throw at it.  (of course mplayer does too, since smplayer is based on it).

the next best player imo is kaffeine.  it is based on xine & plays almost the same amount of audio/video formats/containers that mplayer does.

dragon player is also nice, but it still waaaaaaaaaaaay too immature (feature-wise) for me at the moment.

btw, it is recommend that ppl use xv (xvideo) for video ouput.  it is hardware accelerated.  if one uses x11, it isn't hardware supported & usually has worse performance.

---

### Post by Lucky LIX on 2008-05-14
> **disturbedite said:**
> i don't mean any offense to you or anyone else.  but all these programs work fine.  prolly 75% of the time in my experience, it is the user's fault.  either not installing required codecs, or just generally not very knowledgeable on how things work.
As long as this is the way it works, many folks won't like to switch from other operating systems and I thought Ubuntu was all about ease of use? Linux for the masses etc... So I believe we (the entire community) should try to make it as easy as possible if we want others to use it. (doesn't mean I'm part of the masses, I would like to learn how it all works, but more than 90% of human beings I know isn't interested in this kind of stuff or doesn't have time for it, with reason, there are better things to do in our free time :) I for one don't have enough time to learn proper programming etc but do try to help translate programs I like)

I personally like how the options are set in mplayer (textfile), and its simple and extremely clean looks ^^


> **disturbedite said:**
> btw, it is recommend that ppl use xv (xvideo) for video ouput.  it is hardware accelerated.  if one uses x11, it isn't hardware supported & usually has worse performance.
Just learned something, thanks for that!

---

### Post by rvm4000 on 2008-05-14
> **Lucky LIX said:**
> My bad, xv and pulse. Might altering these help?

Well, you can try to change them and see if there's any difference.

> **Lucky LIX said:**
> When clicking "Subtitles" and "Load..." while playing a movie which was openened using Nautilus the opened folder unfortunately is /usr/bin 

I think this problem should be fixed now in smplayer svn r1259.

> **Lucky LIX said:**
> and some other idea, now I'm at it anyway, when choosing compact mode, it would be nice if the window itself actually got smaller and wouldn't just switch the 2 option bars to black, 'cause that makes the "compact" mode kind of useless as it isn't more compact imho

And I think this is finally done in [svn r1260](ftp://ftp.berlios.de/pub/smplayer/source/smplayer-svn-r1260.tar.bz2).

---

### Post by disturbedite on 2008-05-15
> **Lucky LIX said:**
> As long as this is the way it works, many folks won't like to switch from other operating systems and I thought Ubuntu was all about ease of use? Linux for the masses etc... So I believe we (the entire community) should try to make it as easy as possible if we want others to use it. (doesn't mean I'm part of the masses, I would like to learn how it all works, but more than 90% of human beings I know isn't interested in this kind of stuff or doesn't have time for it, with reason, there are better things to do in our free time :) 
we are in total agreement.  it should be as easy as possible.  but then again, as you said, most ppl aren't interested in learning a thing and that really, really rubs me the wrong way.  i know that's the way ppl are, i'm a computer technician, so i experience this all the time.  (particularly with older ppl, no offense to anyone).  so in conclusion, i guess i kind of hold conflicting views on this subject.  i think it should be as easy as possible to use for the sake of gaining more converts to linux, but then again, i despise ppl's unwillingness to learn anything new.  (you will never grow if you are never willing to learn anything new)!

> **Lucky LIX said:**
> Just learned something, thanks for that!
no prob.  you're welcome.

---

### Post by goggins on 2008-05-17
> **disturbedite said:**
> 

btw, it is recommend that ppl use xv (xvideo) for video ouput.  it is hardware accelerated.  if one uses x11, it isn't hardware supported & usually has worse performance.

And how is this done?  Where does one even find out which one is enabled?

---

### Post by Lucky LIX on 2008-05-18
In mplayer you could write a config file with the following code:
vo=xv

In SMplayer you can just choose xv in the options menu. (preferences, video output driver)

---

### Post by goggins on 2008-05-18
Ah, thanx.  It appears to be application specific, so one must write a config file or set up the preferences for each video app I take it.

---

### Post by Kiri on 2008-05-19
Thanks to everyone who replied to this thread.

I have managed to get VLC player fullscreen working by changing the screen setting in the advanced options to be for screen 0 instead of screen 1. 

I do prefer SMPlayer over VLC, but I am still having problems getting it to work. 
When I try to play some videos, SMPlayer just loads with a blank screen and does not play the video at all, or plays 1 second and then freezes. It may actually not be the fault of SMPlayer though, because I also cant play those video files in mplayer either.
Either way, I'm not sure how I can fix it..





> **disturbedite said:**
> i don't mean any offense to you or anyone else.  but all these programs work fine.  prolly 75% of the time in my experience, it is the user's fault.  either not installing required codecs, or just generally not very knowledgeable on how things work.


> we are in total agreement. it should be as easy as possible. but then again, as you said, most ppl aren't interested in learning a thing and that really, really rubs me the wrong way. i know that's the way ppl are, i'm a computer technician, so i experience this all the time. (particularly with older ppl, no offense to anyone). so in conclusion, i guess i kind of hold conflicting views on this subject. i think it should be as easy as possible to use for the sake of gaining more converts to linux, but then again, i despise ppl's unwillingness to learn anything new. (you will never grow if you are never willing to learn anything new)!


I'm more than happy to learn new things (otherwise I would not be using Ubuntu and would just stick to windows). 
But it seems like a lot of programs in linux take quite a bit of tweaking and research to even get working correctly. Should just playing a video file really require users to learn the ins and outs of every individual program and troubleshoot them just to get it to work?

I think learning new things should be something we do voluntarily when we want to be able to do something we couldn't do before, or to become more proficient in something. Isn't productivity what computers should be useful for anyway?
If I have to research or learn how to do every simple little thing on my computer, then pretty soon I am spending all my time just getting my computer to work, instead of using it to do work. 

Thats my opinion anyway. But thank you also for your input and advice :)

---

### Post by rvm4000 on 2008-05-19
> **Kiri said:**
> I do prefer SMPlayer over VLC, but I am still having problems getting it to work. 
When I try to play some videos, SMPlayer just loads with a blank screen and does not play the video at all, or plays 1 second and then freezes. It may actually not be the fault of SMPlayer though, because I also cant play those video files in mplayer either.
Either way, I'm not sure how I can fix it..

Do you have Compiz enabled?

---

### Post by Kiri on 2008-05-19
Yes, but I just tried turning it off and the videos still do not play.

---

### Post by ibharathy on 2008-05-19
VLC is the best player... Try it.

---

### Post by rvm4000 on 2008-05-19
> **Kiri said:**
> Yes, but I just tried turning it off and the videos still do not play.

What does the mplayer log say after trying to play a file? (Options->View logs)

---

