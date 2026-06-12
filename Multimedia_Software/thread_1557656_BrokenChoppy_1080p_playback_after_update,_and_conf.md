---
title: "Broken/Choppy 1080p playback after update, and confusion regarding VDPAU in 8800"
date: 2010-08-21
forum: Multimedia Software
---

### Post by Henriku on 2010-08-21
Hello my fellow linuxers, this is my first post here ever. I have been  using ubuntu for about 2 years now, and have always lurked these forums  for solutions to my problems, and have always had them resolved. This  time, however, I am at a loss. I have been googling and trying random  stuff for about 12 hours without any results. So after all this time I  may actually have an original problem for you to solve. Man, I bet  you're all excited!

I have 8800 ultra and quad core 2,4. 

[B]HERE BE THE PROBLEM:
[/B]I did a clean install of 10.04 about 2 weeks ago, and installed the  nvidia 256.44 driver. Everything basically worked perfectly, and 1080p  files ran cleaner than alcohol - even in the unmodified native mplayer.  In earlier distros I could only run 1080p flawless in xbmc with VDPAU  enabled, so I downloaded it this time too just for good measure even if I  didn't appear to need it. Everything was all flowering meadows and  bliss under the moonlight until I pressed that damned "update now"  button and everything went to crap. I am not sure what specific updates  messed up my system - I installed them blindly - but the update was very  recent. 2 days ago.

Now even xbmc can't play the heavier hd without getting a seizure. I  reinstalled the nvidia driver and the VDPAU packages, but nothing  changed. I followed countless tips (most found on this forum) on how to  get clean hd on ubuntu, figuring one of the guides might just fix  whatever's broken, but nothing helped. Xorg.conf has been modified more  times the last ten hours than the previous last year.

And then I come across [this]("http://art.ubuntuforums.org/showthread.php?t=1037625")  guide, and it basically tells me I CAN'T get VDPAU on my graphics card.  I googled this extensively, and found a bunch of other sources that  said the same thing - 8800 ultra is not VDPAU compatible. 

This begs the question; how and why is it that I have gotten 1080p to  run flawlessly before, and with VDPAU entered as the video output (at  least in xbmc and gnome mplayer, unsure if I had it in the standard  mplayer or vlc - but these also played 1080p well, vlc the least, but  are now completely useless), and if I have NEVER actually used VDPAU  before - this would have to imply that when VDPAU is selected as output,  the process doesn't fail but rather jumps over to a different output  without changing the apparent config files - then what has gone wrong on  my system? 

I downloaded mplayer-nogui and did some hocus pocus to it per some  trobleshooter's recommendation, and it did help the playback a little  tad, but heavier bitrates are still unwatchable. When VDPAU is selected  in (S)Mplayer, I now get only sound.

I understand there are a lot of different things that might have gone  wrong here, so please ask for further information missing in this post  that any of you might find key.
I now ask if any of you lot have any light to shed on this. If this is resolved in some way, I will be forever grateful.
Also, even though I am a 2 year long user of this usually wonderful OS, I  am a very casual user and most likely of lesser intellect, so spelling  things out to me in big and clear letters is probably the way to go.

---

### Post by cchhrriiss121212 on 2010-08-21
Given that your card does not support vdpau, I would say that you were never using it, did you ever check your cpu usage while playing 1080p video?

In any case, I would first try removing and reinstalling your nvidia driver. After that try using X11 video output, or look into multi-threaded mplayer [here]("http://ubuntuforums.org/showthread.php?t=1104967").  
If that is no good, maybe try trading your card in and buy a more recent one, you could probably get a gt220 (full vdpau on every video format) for the same price.

---

### Post by Henriku on 2010-08-21
Yes, it never spiked until now after that update. And yeah unless something groundbreakingly fantastical is going on inside my computer, it would seem I never actually have used VDPAU, only believed I had since it went smooth on that setting.

But I've never used the multi threaded mplayer, so it shouldn't really be neccessary. But I am installing that now anyway and will post results.

Do you know what kind of updates I did? Seeing VDPAU must be a non-issue, I'm guessing the updates that did the damage would have had to do something with the 256.44 nvidia driver or the x server or whatever. Even if the multi threaded thingy works, it would have been pretty interesting to know what went wrong.

And yeah a new card could be a solution. The one you recommended is only like 80 bucks

---

### Post by Henriku on 2010-08-21
Yeah that didn't help at all. Hm.

---

### Post by cchhrriiss121212 on 2010-08-21
I don't really have any way of guessing what updates you might have performed, synaptic has a history but I don't think it stores auto updates. Regarding the nvidia driver, did you install that yourself or did you use the system>hardware drivers jockey?
I avoid using the jockey for reasons like this, if you install drivers manually then there is less chance of updates knocking out functionality.

I'm surprised that multi-threading had no improved performance, as your cpu seems plenty powerful, did you remember to set the number of cores?

---

### Post by Henriku on 2010-08-21
I realized that something had gone wrong somewhere when i tried installing mplayer-mt, so I've been messing around with that since last I posted. I realized this when I couldn't actually select more than one core haha.

I've been looking for ppa's with mplayer-mt ready to go, but the only one that seems to be relevant is ppa:ripps818/coreavc and the terminal just comes back "key EEB23232: "Launchpad PPA for Taylor "Ripps" L-Wren" not changed" and when I apt get update nothing really happens. Must be down or something.

Concerning coreavc, which I guess is kinda relevant to my problem: I could never get it installed properly in wine. Never tried it in lucid though, may be worth a go.

I have been stuck in front of my computer without other breaks than to eat food since 9 pm last night (now it's 3 pm haha), I'm about to kick something in the teeth:mad:

Thanks for all your help and interest so far mate!

EDIT: oh and yeah I installed the 256.44 driver manually. The only one offered under hardware drives was 170 or some old crap like that. It worked perfectly up until, as mentioned, 2-3 days ago when that update came along. I did a manual reinstall after that with no errors, and nothing changed. I have noticed these last XX hours, though, that sometimes after a reboot windows are missing their... uhm... egdes or whatever you should call it without sounding like a retard. Where the minimize/close/etc buttons are. A x server restart fixes it, but it gives me the impression something's not quite right with the nvidia driver. Oh and I use compiz, but I have tried disabling it and even removing it completely, but that has no noticeable effect on video playback.

I can also play 1080p on vlc when post processing is on 0 without much lag at all, but that frankly makes the picture look like a raspy turd smeared across my monitor.

---

### Post by HDave on 2011-01-13
@Henriku - How did this end up?  I have the same problem...

---

### Post by Henriku on 2011-01-25
Hey, I haven't been on for a while and forgot this thread.
 
The ppa:ripps818/coreavc came up again some weeks later, and it miraculously fixed the whole hd playback problem.
 
But atm my computer is completely smashed. So I'll get back to this thread with a 10.10 solution, if I find one, when I get my computer back on track.

---

### Post by HDave on 2011-01-26
Good to know...thanks!

---

