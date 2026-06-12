---
title: "Sound crackle after update?"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by Flooghans on 2006-09-18
My Ubuntu installation has been working great, and I never noticed any audio crackle.  But today I started noticing an audio crackle.

Ok, first what I mean by 'crackle'.  The sound is somehow being mixed way too loud by rhythmbox, mplayer, etc. so that it crackles, especially with songs that have tons of bass.  I know this is the case because turning down the volume a lot eliminates the crackle and still plays the song audibly.

So basically, I can fix this problem by playing all of my music at 10-20% volume, but something is clearly wrong.

Note:  Setting the master volume lower DOESN'T fix the problem; the sound has to be lowered in the actual application.

Maybe this has been happening for a while and I never noticed, but I'm pretty sure this started today.

My setup is a AMD dual core with nVidia motherboard, that also has the sound on it.  I'm using the k7 kernel.  Don't know what other information is useful.  

Let me know if theres any easy fix for this.  

-- Flooghans

---

### Post by Flooghans on 2006-09-18
Subscribing....

---

### Post by nianhbg on 2006-09-21
I got same issue on my machine. And i got it after I reinstalled/upgraded my ubuntu from 5.04 to 6.06. The sound is great but very low for couple off seconds maybe 10-20. Then it start to sound very uggly. And I have tried to change sound process to OSS but that did not make any diffrent.

---

### Post by weird_c00kie on 2006-10-30
sounds similar to the problem i have.
did you manage to fix it eventually?


for me it only really does it for music files. at least that's what i noticed. and it started out of the blue for me as well

i'm also running a dual-core amd64 on an nvidia board

---

### Post by Flooghans on 2006-11-01
That's interesting...I have an nVidia board as well.

Well, I finally did fix it.  Turns out the problem was really dumb, so it might be what you have but there's a good chance it isn't.  Apparently some applications have access to the global sound settings and can make it so the sound volume gets too loud and causes a crackle.  In my case, the application that caused this was MPlayer.  The solution was just to open up MPlayer and set the volume lower in MPlayer until the crackle was gone on my loudest music files and movies.

The weird thing about all of this, so far as I'm concerned, is that I couldn't use the GNOME system volume to reset the volume.  I had to use MPlayer.  I guess it bypasses GNOME, and GNOME can't fix it?  Seems strange.

Well, I hope this helps.

---

### Post by weird_c00kie on 2006-11-03
weird. that's definitely one to keep in mind. unfortunately, for some reason my sound has completely gone now, so i can't try it :p

---

### Post by tich on 2007-01-19
i have a similar problem, my sound crackles too, usually not right when the bass (--or volume,  like in a movie when it goes from whispering to bombs dropping) is loud but a few (milli-) seconds after, as if the bass or volume itself isn't the problem but rather that it sets the problem off.
sometimes it just crackles for what i would deem to be no reason at all, without any warning (such as a bass or volume increase)

i have also noticed that my playback sounds slow sometimes (the pitch gets lower, much like a dying cassette player) and that there can be little pops as if the playback is doing some sort of catch up (like when video jumps but with sound)

this glitch affects everything (mplayer, totem, rhythembox, vlc, exaile... although some rare times i can get through a whole movie or show using totem (with maybe only a few pops) so i don't think it is a gstreamer problem.

i believe that it occurred after an upgrade about a week ago (jan 10, 11 or 12), but that could just be a coincidence or me seeing connections where they don't exist.

and i also run a nvidia card but i am using the -generic kernel.


**i just tried the mplayer fix and it had no effect on the playback. it still has the same glitches.

---

### Post by pcjunkie on 2007-02-20
Same here.

Video is ok but bass is bad....
MP3 in M player is great but bass issues....
embedded media.. is awful. Flash etc is way overloading the system even at low volumes sound clipping is occurring...

---

### Post by sunset blvd. on 2007-03-02
Subscribing here too. That's about the only problem I haven't been able to fix yet. And it is kind of disturbing.

So, no ideas yet?

---

### Post by crash369 on 2008-03-06
This post is old as hell, but in case anyone is still subscribed...

I have been able to control the "bass crackle" by turning down the PCM volume in the full volume-control panel.

The reason some of you had to turn the volume down in Mplayer is because it controls the PCM volume, instead of the master volume.

Hope this helps

---

### Post by Thingymebob on 2008-05-09
Old Thread I know but this has just reared its head on my machine after upgrade to hardy (ATI SB450 HDA) Adjusting PCM makes no difference. 

Appears there's a couple of bug reports here
[https://bugs.launchpad.net/ubuntu/+bug/139188]("https://bugs.launchpad.net/ubuntu/+bug/139188")
and xine-lib
[https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/84774]("https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/84774")

---

### Post by Thingymebob on 2008-05-09
Bye Bye Exaile, You're the only one That is persisting with this

---

