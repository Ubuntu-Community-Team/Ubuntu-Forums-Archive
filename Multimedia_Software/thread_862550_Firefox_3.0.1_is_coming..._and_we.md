---
title: "Firefox 3.0.1 is coming... and we??"
date: 2008-07-17
forum: Multimedia Software
---

### Post by Alex Dinamo on 2008-07-17
Firefox 3.0.1 is coming presuming of even better stability. And we here in Ubuntu... when??

When will we be able of listening to an MP3 on Firefox, or using YouTube, or whatever any other flash/audio content around, without constant crashing? This is absurd.

And blame it on PulseAudio or whatever. It just keeps crashing and it is embarrasing.

Alex

PS: I've already tried a lot of recipes found here and in other places to presumably make it more stable. It has become more stable, yes. And it keeps crashing. Imagine how it was before.

---

### Post by scragar on 2008-07-17
can I point out that this is flash's fault not firefox or Ubuntu's fault.

Can I also point out that with any luck HTML5 specs will be finalised by 2009, so we can start expiencing video and audio playback acording to the browser without having to worry about the grossly closed source world of flash(although only 2 browsers comply with video so far, opera and safari, both of which do ogg though :P -- unless other browsers support it soon though it may get completely missed like about 50% of the CSS IE6 should have supported that still doesn't work in IE7)

---

### Post by Alex Dinamo on 2008-07-17
But it is not only about flash.

Right now I am *very* pissed off because I am publishing training material (videos) for our product on our wiki page and then, when I want to check the links for the videos, Firefox keeps crashing. It is not flash, those are .mov files.

I configured Firefox to use VLC for showing videos because I read somewhere that this would do some good to fix all this situation. Seems like it didn't.

Alex Escalante

---

### Post by dgonza9 on 2008-07-17
I don 't get it.  My system has never crashed and I watch videos all the time.  That's why I love Ubuntu.  No crashes or freezes.  Why is this person having so many problems with the crashes?

---

### Post by Alex Dinamo on 2008-07-17
I am not the only one, so it is not just "this person" as you put it. Look around google. 

My brother, for instance, has the same problems. He just made a clean install of Hardy.

---

### Post by Stason on 2008-07-18
Looks like Firefox 3 is not there yet. I am still on 2.16 because of the numerous stability issues.

---

### Post by ibutho on 2008-07-18
> **Stason said:**
> Looks like Firefox 3 is not there yet. I am still on 2.16 because of the numerous stability issues.
Firefox 3 works well for me on various distros and I have no problems with flash. Saying that, I am not using pulseaudio because I don't really need its features at the moment.

---

### Post by NilsE on 2008-07-18
FF 3.0.1 is in the Hardy Proposed repository now.

---

### Post by Lilszamora on 2008-07-18
I have not to many problems now with firefox, I used to get a few during flash, but it never crashed...just paused and I'd have to fresh restart firefox, but I don't even have to do that now that I've updated to flash 10

---

### Post by ahmad_1sa on 2008-07-18
I just try firefox 3 , till now not yet got problem.

---

### Post by Alex Dinamo on 2008-07-18
Maybe I need to reverse the VLC thing I did to firefox, just to be in common grounds. That way maybe I would just be with the flash problem.

Alex Escalante

---

### Post by Mhurst1 on 2008-07-18
Open firefox in a terminal and when i crashes post the error.

---

### Post by Alex Dinamo on 2008-07-18
Yeah, maybe I need to get into that, debugging the whole thing...

Thanks,
Alex

---

### Post by BigSilly on 2008-07-18
> **Mhurst1 said:**
> Open firefox in a terminal and when i crashes post the error.

It says:

```
Segmentation fault
```

---

### Post by silkstone on 2008-07-18
I had a problem with FF3 and Flash 9 from the repos - FF would close down unexpectedly after every two or three flash movies. I installed the Flash 10 beta plugin by following a tutorial on these forums, and there have been no problems since. However, there is now an updated Flash 10 beta 2 which some people find does not work as well as beta 1.

All other media files play perfectly using alsa.

I recommend this tutorial to anyone having problems with multimedia and streaming...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by scragar on 2008-07-18
> **BigSilly said:**
> It says:

```
Segmentation fault
```

segment fault is attempting to read to or write from inaccessible memory, it's unlikely to be firefox's fault.

---

### Post by Alex Dinamo on 2008-07-18
I just removed vlc-mozilla-plugin. Let's see how things go...

Alex

---

