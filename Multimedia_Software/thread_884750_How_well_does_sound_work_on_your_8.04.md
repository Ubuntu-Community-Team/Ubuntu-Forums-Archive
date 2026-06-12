---
title: "How well does sound work on your 8.04?"
date: 2008-08-09
forum: Multimedia Software
---

### Post by pikseli@work on 2008-08-09
After some heated discussions on audio issues elsewhere I realized this would be an useful poll.

Please, before answering test if your computer can play sound from multiple applications. 

For example, test if you can hear sound from a mp3 in a player app and Youtube video at the same time.

Please, also feel free to share a brief 3-4 line description of your experiences if you feel that would be useful to others.

Brief descriptions of the "options":

Perfectly normal, multi-app sound - All apps have always had sound working perfectly! 

Minor Tweaking, Solved problems, Multi-app sound - had to edit a file or two, but now it works!

Serious tweaking, Solved, Multi-app sound - after hours of heavy hacking the sounds work great!

Tweaking, some problems remain, but multi-app sound - despite problem-solving, some issues remain.

No sound, serious tweaking - despite problem solving, not an eep. Quiet as a mouse in a mitten.

Sound problems, didn't try to solve - sound but some problems too, but too busy, too lazy, can't be helped! 

Only single application has sound, didn't try to solve - monophonic, c'est la vie! Otherwise no problems.

No sound, didn't try to solve - haven't heard an eep, despite testing several audio apps. Other than sound, works.

Serious problems, crashing, bad fail - even trying to use sound resources causes crashing. Please specify why you feel crashing is related to sound sw/hw.

I do not understand, you fool! - what you mean sound is working? Audio? Ah, Dio? Amore mio!

---

### Post by pikseli@work on 2008-08-09
saturday night *bump*!

---

### Post by xc3RnbFO8P on 2008-08-09
Works fine here, never had a problem with this omputer (see signature).
I got a Zepto laptop, the only problem have is when I use
Skype, after conversion I have to change from front mic
to mic and back again front mic.

---

### Post by pikseli@work on 2008-08-10
bump'd!

---

### Post by markbuntu on 2008-08-10
It took a lot of work but I got everything working together all the time, even pulse audio through jack.

---

### Post by Java Geek on 2008-08-10
I have managed to get it working through Youtube and an ogg recording, but other than that not an eep!

---

### Post by Melcar on 2008-08-10
Works perfectly now.  I can use multiple apps. with no problems.  The only issue I used to have was Pulseaudio not outputting 5.1 sound, but that was easily fixed by editing /etc.pulse/daemon.conf.

---

### Post by cariboo on 2008-08-10
I've got two computers running hardy, laptop running Linux Mint , based on hardy. Command line 8.04 from mini iso install, its been playing tunes since Friday morning, its Sunday afternoon now, its still going strong. One computer running Intrepid alpha 3, it worked right out of the box, I should mention that this computer triple boots vista, hardy and intrepid.

JIm

---

### Post by estyles on 2008-08-10
I think the sound support in 8.04 is terrible.  I was able to get most things working with major tweaking and following a couple of different tutorials.  It shouldn't be that hard to get sound working - pulse should work correctly out of the box and should have a GUI setup for doing 5.1 audio, etc.  Not to mention that there are like 3 GUI setup apps for sound and none of them really do anything.  8.10 should have a combined settings app for sound and it should actually be able to *do* some of the things that we have to follow tutorials for now.

(I don't mean to sound *too* complainy - I don't mean it to be a "Ubuntu needs this to be perfect or I'm leaving" or a "Ubuntu isn't ready for the desktop because..."  post.  I'm perfectly happy with Ubuntu, *but* sound support is one of the things that could use a lot of improvement.)

---

### Post by gjoellee on 2008-08-10
*Perfectly normal, multi-app sound*

---

### Post by zenithdave on 2008-08-10
Good here, using a M audio delta44
Streaming without a glitch using VLC

When i can run fruity loops in wine with 11ms latency all will be perfect.

---

### Post by pony-tail on 2008-08-11
My sound issues do not fit into any of your categories !
I have 2 Asus mobo. based machines ( 1 is an M3N-VM the other an M3N-EMH HDMI ) they are both AMD AM2 machines with nVidia GF8200 chipsets one ( the M3N-EMH hdmi has an Athlon 64 5200+ ) the other has a Phenom 9850 . both have the same issue with sound - It works out of the box , but it stutters and is scratchy and totally unusable . It works in all apps but has the same absence of quality . I have tried quite a few things from various sources and I still can not get it right .I am using 8.04.1 as 8.04 does not recognize the hard drive controller and can not be installed .
Both of these machines are less than 6 months old .

---

### Post by eye208 on 2008-08-11
I use several apps known not to work with PulseAudio. Removing PulseAudio solved all the problems. :arrow: Perfect multi-app sound after minor tweaking.

---

### Post by jerome1232 on 2008-08-11
Works mostly perfect for me, A few programs will get scratchy sound, had to edit /etc/pulse/daemon.conf to get surround sound back. But I can have my music streaming to all ubuntu computers on the LAN, kinda cool :)

---

### Post by NovaAesa on 2008-08-11
I only could have sound comming from one app at a time. I just changed something (I can't remember what lol) to ALSA (or something like that) and it worked fine.

---

### Post by !ndy on 2008-08-11
i am stuck with the nvidia chipset and maybe some guys know, what it means...

i have just reinstalled system, because sound worked only with programs using some codecs (movie and mp3 players)

maybe an issue was removing mod ohcd or something like that (i read on one forum that it is a cool idea)
or meybe nad issue was reinstalling nvidia drivers a lot of times and something got wrong there.

howerver, now it's working fine, but i did not load restricted graphic drivers yet... omg.

---

### Post by pikseli@work on 2008-08-11
So, judging from the current votes in this very limited poll, it looks like:

- [B]One third of 8.04 users do not have proper sound.
[/B]
- **Only 46% of Ubuntu 8.04 users get to enjoy the role of "human" in regard to having working sound system**, the rest will have to possess some qualities of an engineer (or at least a troubleshooter) to enjoy sound on 8.04.

**pony-tail** - Ah, I forgot the serious tweaking, some sound -option.

Funny, but some people I am talking to seem to think that sound problems are the Dirty Little Secret of Ubuntuforums -community, and it seems you're not supposed to talk about it or you will 1) get flamed, 2) admins will remove your thread. 

Funny. Thats exactly what happened to me before I got the idea to start this thread. So, I am thinking theres some truth to that. 

Now, lets stop playing ostrich and start realizing the "linux for humans" dream in an open, honest and grown-up manner? Well I hope so anyway.

---

### Post by pikseli@work on 2008-08-12
*bump for votes*

---

### Post by markbuntu on 2008-08-12
> **pikseli@work said:**
> So, judging from the current votes in this very limited poll, it looks like:

- [B]One third of 8.04 users do not have proper sound.
[/B]
- **Only 46% of Ubuntu 8.04 users get to enjoy the role of "human" in regard to having working sound system**, the rest will have to possess some qualities of an engineer (or at least a troubleshooter) to enjoy sound on 8.04.

**pony-tail** - Ah, I forgot the serious tweaking, some sound -option.

Funny, but some people I am talking to seem to think that sound problems are the Dirty Little Secret of Ubuntuforums -community, and it seems you're not supposed to talk about it or you will 1) get flamed, 2) admins will remove your thread. 

Funny. Thats exactly what happened to me before I got the idea to start this thread. So, I am thinking theres some truth to that. 

Now, lets stop playing ostrich and start realizing the "linux for humans" dream in an open, honest and grown-up manner? Well I hope so anyway.


It took me forever to get my sound working the way I wanted on my 4 different Ubuntu Hrdy installations but I did (i386, amd64, ubuntusSudioi386, UbuntuStudioamd64). I originally just kept a bunch of tomboy notes for myself so I could remember how to get things working again after trying some of the how-tos and stuff that failed me miserably at times. 

Along the way I realized how fragmented the information has become which makes it very difficult to track down answers so I organized my notes and posted them in this thread as a sort of one stop shopping place for general sound issues:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I am also working on a one stop shopping thread for people with sound hardware problems. It will hopefully make its debut sometime soon.

I agree wioth you though about the "dirty little secret issues" but it is not just in Ubuntu, it is in linux. I have seen sniping between the pulse and oss devs. Really stupid juvenile behavior that helps no one. Meanwhile we are all left in the woods dealing with this huge amalgam of semi-compatible systems working at cross purposes.

---

### Post by pikseli@work on 2008-08-14
Well put, and thanks for the troubleshooter thread.

---

### Post by pikseli@work on 2008-08-16
Do you think the results of this poll are biased one way or the other due to the fact it is in this subforum (Multimedia & Video) ?

---

### Post by momalle1 on 2008-08-16
Audigy 4, Stereo speakers, ALSA, the only sound problem I have is DVD playback, when I play 5.1, it sounds fine, when I try stereo I get fuzz. Haven't really spent any time trying to fix it since I usually watch movies on my television.

---

### Post by leepesjee on 2008-08-16
*Minor Tweaking, Solved problems, Multi-app sound*
In my opinion, the trouble is the implementation of pulseaudio. Have a look at at the pulseaudio-diagram:  [http://en.wikipedia.org/wiki/Image:Pulseaudio-diagram.png](http://en.wikipedia.org/wiki/Image:Pulseaudio-diagram.png)
I dont say pulseaudio is bad. It's an attempt to cope with the linux-sound mess. The point is that it places itself in the center of all sound-activities. So you either adopt it fully or you better leave it. The implementation is surely not yet at the 'just works' level.

---

### Post by pikseli@work on 2008-08-17
leepesjee - Thanks for the pulseaudio diagram. Hadn't seen that before. I think you have some wise words.

Personally, for me the problem*was that I was misled by the "marketing" for Ubuntu 8.04 - it promised much better audio layer (finally), and everything audio-related went bad instead, taking me back to year 1996 or so.

---

### Post by jammin2222 on 2008-08-17
No sound from youtube, no system sounds, 

Can hear mp3's and play video files stored on my computer no problem.

---

### Post by pikseli@work on 2008-08-17
FYI, I plan to make another poll for the 8.10, and so forth.

This would give very very rough estimates on how well the attempt at making things work has succeeded.

---

### Post by markbuntu on 2008-08-17
I am not sure if the poll would be very accurate since lots of people have no problems and so do not come to the forums.

---

### Post by eye208 on 2008-08-17
> **leepesjee said:**
> In my opinion, the trouble is the implementation of pulseaudio. Have a look at at the pulseaudio-diagram:  [http://en.wikipedia.org/wiki/Image:Pulseaudio-diagram.png](http://en.wikipedia.org/wiki/Image:Pulseaudio-diagram.png)
I dont say pulseaudio is bad. It's an attempt to cope with the linux-sound mess.
In my opinion there was no mess until PulseAudio arrived.
[list][*]OSS, ESD, and aRts were on their way out. Very few applications still required one of these.
[*]Flash 9 adopted ALSA.
[*]Skype adopted ALSA.
[*]Gnome adopted ALSA (except for system sounds).
[*]Software mixing was added to ALSA's default device.
[*]Advanced features such as network sound transport were provided by JACK if required.
[*]ALSA provided a JACK sink (similar to the new Pulse sink, but not included in Ubuntu).[/list]
Everything was about to fall into place.

Now we are all the way back to the start. PulseAudio adds yet another API but still requires ALSA and/or JACK, i.e. we have several competing systems again. OSS has been resurrected from its grave too. Gnome will continue using the ESD compatibility layer for its system sounds instead of completing the switch to ALSA.

Sound on Linux has just become more complicated than ever before. Why couldn't we just stick with ALSA/JACK and phase out everything else?

---

### Post by pikseli@work on 2008-08-18
> **markbuntu said:**
> I am not sure if the poll would be very accurate since lots of people have no problems and so do not come to the forums.

Ok, I suppose thats one angle on that. But I can instantly come up with the opposite: people who don't get sound working when trying Ubuntu, leave it and try something else.

---

### Post by unoodles on 2008-08-18
My sound was completely broken after my upgrade from gutsy to hardy. There were alot of other issues too, so a clean install and everything work perfect.

---

### Post by eye208 on 2008-08-19
> **unoodles said:**
> so a clean install and everything work perfect.
It all depends on how you define "everything".

---

### Post by Garratt on 2008-08-24
mine worked, sorta, dvd playback was quiet but apart from that it worked up untill i saw this post then tried to play 2 things at once... now my sound is broken and i can't hear mp3's

---

### Post by dorite on 2008-08-24
Stumbled on this thread while looking for help:  Sound worked perfectly well for me in 7.10.  Upgraded to 8.04.1 -- no sound at all, at all.  Oh, well -- price of progress, eh?

---

### Post by ileksip4truth on 2008-08-26
bump for freedom!

---

### Post by co0lingFir3 on 2008-08-26
multi-app-sound works even in firefox/flash after installing libflashsupport. mic is not working although...

---

### Post by Garratt on 2008-08-27
some of the answers are kinda off, like i can only hear sound in 1 app at a time, and yes i have tried to fix, and no i have not yet fixed, so for me answering "sound in 1 app,did not try to fix" is the complete opposite to what i wanted to say :P

also things like, "some minor tweaking, some problems still exist, multi app."

so ive done minor tweaking, problems still remain, and no multi app, searching for solution to no avail.

---

### Post by jocheem67 on 2008-08-27
I didn't do the poll, as I don't care about multi-app sound.
I got rid of pulse and work through alsa and jack.
No probs there....

---

### Post by TenPlus1 on 2008-08-27
Mine works perfectly, multi-app... but... I removed Pulse audio :)  I just use ALSA :)

---

