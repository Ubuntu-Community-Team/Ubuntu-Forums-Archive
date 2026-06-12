---
title: "streaming with gecko-mediaplayer plugin"
date: 2011-05-23
forum: Multimedia Software
---

### Post by beew on 2011-05-23
I have an issue and some questions that would like clarification.

First the issue is that when streaming long videos the playback would suddenly stop and I would need to restart playback manually and drag the progress bar to the correct position to resume playback. I think this is because buffering is not keeping up.

I would like to find a way to configure gnome-mplayer so that playback would just pause when buffer is running low and resumes as it grows, is that possible? 

In order to do this I have been playing with the cache setting in gnome-mplayer.

Here are a few questions and observations.

1) In gnome-mplayer there are two cache settings, one go under the Preference > Mplayer tab, the other under Preference > Plugins. What is the difference?

2) I notice that if I set the plugin cache to be minimum then playback will not start until the 20% mark is reached, iit will take longer  to start and the playback will last longer before buffer runs out.  On the other hand if plugin cache is set to some large value then playback will start almost instantly (~ 1%) but also stops very quickly.

The question is 20% of what? I thought it means 20% of cache size so it should take longer to fill if the cache is set bigger, this seems to be the other way around. 

3) With audio stream (say radio) it seems to be the opposite, if plugin cache is small then playback starts immediately, if it is big then it takes longer.

I would like to make sense of this and understand the logic behind it, thanks.

P.S. Gnome-mplayer  in Natty (as oppose to earlier versions) actually has too cache size options under Preference > Plugins but they don't seem to behave independently, for example, I set video cache to be large and audio cache to be small then according to 3) above  (and the small audio cache) audio playback should start instantly but instead it takes a while so the size of the video cache has an effect even without video streaming.

---

### Post by beew on 2011-05-24
Bump!

---

### Post by beew on 2011-05-25
Bump again!

---

### Post by beew on 2011-05-27
So is there a way to make gnome-mplayer to pause when the buffer is full and resume when more buffer space becomes available instead of just stops?

Thanks.

---

### Post by beew on 2011-05-28
Hello?? Anyone?

---

### Post by beew on 2011-05-29
Bump again!

---

### Post by beew on 2011-05-31
Hello? Anyone?

---

### Post by beew on 2011-06-01
Bump

---

### Post by beew on 2011-06-04
Ok, bump again. I am really asking what are the difference between mplayer's cache and the plugin cache in gnome-mplayer and how to optimize them for streaming so that 
1) Video would start in reasonable time

2) When buffer runs out the video would pause instead of stop so that I have to watch from the beginning or manually moving the progress bar to where it left off (in other words to configure gnome-mplayer so the gecko-mediaplayer plugin would stream video like e.g the Totem plugin)

I am sure these are common questions for users of the the gecko-mediaplayer, how come no one seems to know the answers?

Thanks in advance for any help.

---

### Post by beew on 2011-06-07
Bump!

---

### Post by beew on 2011-06-17
Ok, finally figured it out. The version of mplayer I installed is actually mplayer2
**[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")**

mplayer2 works a lot better than mplayer for hardware decoding and hd movies, vdpau etc (so if you are having problems with video playback with mplayer, should install from this ppa), but there is one catch, namely that gnome-mplayer's pausing function is broken and that is the reason for the problem that I am describing in this thread. Streaming works fine with the normal version of mplayer.  This will be fixed in the future according to mplayer2's website.

---

