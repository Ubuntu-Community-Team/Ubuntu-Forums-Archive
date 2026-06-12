---
title: "Recommended Video Editing Software"
date: 2009-08-21
forum: Multimedia Software
---

### Post by JoshStrobl on 2009-08-21
I recently moved from Windows Vista, using Movie Maker and Sony Vegas 9 to edit my videos.

I have tried Open Movie Editor and Avidemux.

Well for one, I downloaded Cinelerra but can't find the file to open the program, so anyone know where that could be?

Two: I am looking for an open-source or costly Linux based video editing software that is close to Windows Movie Maker and Sony Vegas 8 AS POSSIBLE.

---

### Post by JoshStrobl on 2009-08-21
nevermind I found KdenLive...man I love Ubuntu with all the sick stuff that can go along with it.

To the creators of Ubuntu: You guys rock!

---

### Post by jukingeo on 2009-08-27
> **JoshStrobl said:**
> nevermind I found KdenLive...man I love Ubuntu with all the sick stuff that can go along with it.

To the creators of Ubuntu: You guys rock!

And how is your experience with Kdenlive thusfar?  Last I checked it was fairly buggy.

Seems like the 'new' kick now is OpenShot.  I haven't tried it yet, but it looks pretty good from the videos and screen shots I have seen.

---

### Post by AlexanderDGreat on 2009-09-12
kdenlive is buggy for me.

can't install cinelerra

Ubuntu JJ

---

### Post by jukingeo on 2009-09-12
> **AlexanderDGreat said:**
> kdenlive is buggy for me.

can't install cinelerra

Ubuntu JJ

Surprised you are having trouble with installing Cinelerra.  I don't recommend Synaptic (not that I am even sure it is there.  I believe when I installed it, it was a deb file.  It installed on my system fine.  Use the terminal:

wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update

And then execute:

sudo apt-get install cinelerracv

Right now I am using OpenShot.  Cinelerra is cool and powerful, but it is hard to learn. While it's capabilities are nothing short of spectacular, sometimes the simplest of edits are complicated.  Thus I was looking for a good program that is easy to use and fast.  I have to put a bunch of movie edits together and fast.   Almost everything I tried either wasn't capable enough or simply just didn't work.  This includes Kino, Kdenlive, Open Movie Editor, etc, you name it.  Thus far the only thing that didn't give me trouble was Cinelerra.

While there are high hopes for OpenShot, it is still in its infancy as we speak and there are a few problems, but for the most part it DOES run.  If you are putting pictures together to music or making simple videos it is already good to go, however there are problems when you get into precise editing and there are some issues with video/audio sync.  So there is still a ways to go, but I have high hopes for this one.

Geo

---

### Post by AlexanderDGreat on 2009-09-13
Yeah, I guess I found my way here too. It has become my practice to use the search function before starting a new thread.

Anyways, is that so? Oh well I'm going to use sudo apt-get install cinelerracv and see if it works.

I just need a simple video editor, can OpenShot do a simple, cut, paste, insert subtitle, transition, and pictures slide film? And export it to a small file like mp4, divx, etc...?

Does the sound work ok? If not, then I'll be forced to use cinelerra even if it's complicated. Thanks. =)

---

### Post by cotcot on 2009-09-13
See [[COLOR="Red"]this thread [/COLOR]]("http://ubuntuforums.org/showthread.php?t=1246176")for more discussions about video editors.

---

### Post by zipperback on 2009-09-13
My needs for video production are pretty low. In general I just need to import my videos, do some minor quick editing, and then export my work to various formats.

I use Kino for importing video from my Canon ZR9000 Mini DV camera and overall I've been pretty happy with it.

I've used a few others, but for my specific needs Kino does exactly what I need from it.

- zipperback
:popcorn:

---

### Post by jukingeo on 2009-09-13
> **AlexanderDGreat said:**
> Yeah, I guess I found my way here too. It has become my practice to use the search function before starting a new thread.

Yeah, I do that too.  Most of the time I don't have to start a new thread.

> Anyways, is that so? Oh well I'm going to use sudo apt-get install cinelerracv and see if it works.

Yes as in the other outlines, you just need those two lines to install cinelerra.  The wget line goes to Cinelerra and gets the program.  The apt-get install line installs it.  It should work from there, if it doesn't then there could be a problem on your system.

> I just need a simple video editor, can OpenShot do a simple, cut, paste, insert subtitle, transition, and pictures slide film? And export it to a small file like mp4, divx, etc...?

Yes, it can.  The program is the first one I have come across that works well in Gnome.  BUT it isn't without it's glitches.  It is in its infancy and it still has some problems to iron out.

Two problems I discovered is that when exporting the program uses too much of system resources and sometimes the resultant video comes out pixelated.  I am working on this to see if it is a setting on my end or if it is a true bug.

The next problem is an audio/video sync problem.  Most of the time the video/audio is in sync without any trouble, but I have noticed that sometimes the sync 'jumps' and the video will play slightly ahead or behind the audio.  There is no pop or alteration in the sound though...sound plays fine.  It is a hiccup in the video end.   I was wondering if it was a buffer problem but the developers came back to me and explained that this problem IS a true bug and they are working on it.

What I am going to do the next couple evenings is to create a trivia slide based pre-show for a movie with OpenShot.  A slide show that just plays along with an audio track probably will not need the accurate audio/video sync and I should be able to get away with it for now.

> 
Does the sound work ok? If not, then I'll be forced to use cinelerra even if it's complicated. Thanks. =)

The sound is fine.  No stuttering or distortion or anything.  The only nit pick I would have with the sound is that if you use the cutting tool and divide a track, but play it back as a whole with the divide point in place, you will hear a faint 'pop' in the output which was not there prior to editing.  

If you have been using Windows Movie Maker, you will find many improvements over that program and most of those improvements are in the sound capabilities.  For one you can independently mute video and audio in a track.  So in my case if I am going to edit video, but not the audio of a given track, I can create a second track just for audio alone and edit the video track.  Thus in that case, I get around that 'pop' I mentioned above.

Another thing is you can MIX audio levels in OpenShot...which you can't do with Windows Movie Maker.  Each clip you can alter it's sound level.  You can auto-fade too thus creating the illusion you have a mixing console.

Given the fact that it just about accepts ANY video format and exports to ANY format does increase the program's versatility.  With Cinelerra, you have to provide your own codecs for quite a few file types.

I would say as it stands now, Cinelerra is the more stable of the two programs, but it does have disadvantages.   Simple editing is actually a long laborious process in Cinelerra.  If I were to make a music video (or my own movie) and have very sophisticated synchronized hits or frame changes, then I would say stick with Cinelerra.   But like most people what I want to do is put photos together with music, edit home videos down to music and make movie pre-show presentations.  A simple editor should do all these things much faster than Cinelerra.   However up to now, all simple editors I have tried have fallen flat on their source code (face).  Most programs wouldn't even LOAD properly.  Others like Kdenlive I was able to get running, but it is designed to run under KDE, so under Gnome it is loaded with bugs.  So OpenShot DOES run well in Gnome, but it does have minor issues that need to be fixed.  Luckily the program is new and they have a development team right on it.  So I am hoping the problems will be fixed pretty quickly. 

Geo

---

### Post by AlexanderDGreat on 2009-09-14
Hey, thanks for that long reply.

I think I'll give OpenShot a shot since you say it's very basic, that's all I need.

I'll post my findings soon. =)

---

### Post by jukingeo on 2009-09-14
> **AlexanderDGreat said:**
> Hey, thanks for that long reply.

I think I'll give OpenShot a shot since you say it's very basic, that's all I need.

I'll post my findings soon. =)

Heh, Heh, yeah that was a big one...but not the first time I have made a long reply.  I have been known from time to time to publish a 'book' here every now and then.

OpenShot does have quite the promise running behind it.  Like I said above, it isn't ready yet (consider it in alpha stages) so don't be disappointed if things don't work right or it doesn't have all the features you would like.  However, what is there IS usable and you can edit a full video.  Just the sync is a bit off, so for sync critical work, you will have to wait until they fix the bug.

Geo

---

### Post by AlexanderDGreat on 2009-09-14
Hi, I've tried OpenShot but it doesn't work for me. As a trial, I recorded some clips using recordmydesktop - it produced, .ogv files.

Then I imported them to OpenShot, but at the beginning of every clip in the timeline, there's a white wash, that completely doesn't show the good 1st 3 seconds of the clip.

I've tried different formats it's the same.

Is this a bug?

---

### Post by AlexanderDGreat on 2009-09-15
Hey, I've finally installed cinelerra and quite the contrary, it's so EASY to use!

Plus, it only crashed 1x on my Ubuntu 9.04 while rendering 2x 1-minute span videos with transitions and effects.

Compared to others kdenlive and OpenShot which crashed 149x just doing cutting and transitions.

To only take away watch these tutorial videos:

Basic Editing in Cinelerra Pt. 1 - [http://www.youtube.com/watch?v=-Q-NTYLiyKc&](http://www.youtube.com/watch?v=-Q-NTYLiyKc&)

Trust me it would only take 30-45 minutes of your time. If a newbie like me can do it, you can do it too...

Thanks. =)

---

