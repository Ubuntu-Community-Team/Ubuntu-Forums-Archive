---
title: "Audio freezes applications [Gutsy]"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by monstercloset on 2007-11-26
I'm using Ubuntu Gutsy Gibbon, and any application with sound (mplayer, VLC, flash videos in firefox) will freeze the application upon loading, and I end up having to force quit the application.

I don't know what the problem is, since it was working fine the other day.

Any idea what's going on?

---

### Post by monstercloset on 2007-11-27
*bump*

---

### Post by Janus%TheDoorman on 2007-11-27
I'm haivng this same issue, and would like to add that it's been consistent across Banshee, Audacious, Totem, and Amarok in addition to the things already mentioned.

---

### Post by monstercloset on 2007-11-27
*bump*

---

### Post by monstercloset on 2007-11-28
I think I've got it solved.

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
```

---

### Post by Brian031168 on 2007-11-28
Hi

I tried this "fix" and while it did make the freezing stop, it seems to have messed up other things. I was running GDM but now KDM runs. Also if I log-out all I get is a black screen and no way to do anything so I have to switch of my computer. 
Maybe I did something wrong, but I followed your fix as it is shown. During the process it shut down GDM and crashed my comp.
I am now searching for the answers to fix the new problems.

---

### Post by rad79 on 2007-11-29
Having the same issue here. I've discovered that if I watch a video on youtube that doesn't contain sound, the video keeps playing. If I watch a video on youtube with sound, play a cd, test the sound card, play audio in vlc etc. I'll get about 2 seconds worth of video or playback without sound then it will freeze and I'll usually have to force quite the application. I've also noticed, if I play a dvd, the movie will play but at about 4 frames a second without sound.

I haven't tried the fix posted earlier for fear of screwing up a great operating system setup. If anyone gets this working let me know.

Just thought I'd mention. whether I install the restricted ati drivers or use the default ati drivers it still doesn't fix the problem. Actually when i use the restricted drives compiz-fusion fails to work.


Rad79

---

### Post by Janus%TheDoorman on 2007-11-29
I tried the posted fix and nothing appears to have changed. Though, as someone mentioned on occasion there are a few seconds of playback before a freeze.

---

### Post by princess9987 on 2007-12-20
Same thing happens with me. The applications freeze and no sound is heard.. Has anyone found the solution?

---

### Post by bmcatt on 2007-12-22
*bump* for also experiencing this problem.

After doing a little playing around, it appears almost like the sound subsystem isn't allowing multiple users in certain conditions. So, when the next application tries to use something sound-related, it deadlocks until the resource is freed.

I've confirmed this by playing (mplayer) an mp3... I stop it playing and then open up sound properties (System->Preferences->Sound) The devices for Sound Events, Music and Movies and Audio Conferencing playback are all set to "Autodetect". I can "Test" any one of them. However, trying to test a second one causes an immediate freeze of the preferences.

While preferences is frozen, I try to play the mp3 again. It freezes.

*HOWEVER*, when I kill gnome-sound-properties, the mp3 *immediately* starts playing.

Is there a launchpad bug open on this? Given how repeatable this is, I find it hard to believe that this can't be further diagnosed / localized.

Note - I did *not* try to uninstall/reinstall sound. I'm concerned, as it is, about how seemingly fragile my system has become with the upgrade to gutsy and I'm disinclined to do something which might be that dramatic until it can be determined exactly what the failure is.

---

### Post by ptelder on 2007-12-24
While I have no idea what the problem is, I can confirm that this has been happening to me in both Feisty **and** Gutsy.

---

### Post by bmcatt on 2007-12-26
I've opened Bug #178520 ([https://bugs.launchpad.net/ubuntu/+bug/178520](https://bugs.launchpad.net/ubuntu/+bug/178520)) on this. Hopefully, someone will take it and run with it.

---

### Post by wavesound on 2008-01-14
Hi All
I to get this all the time, I can play stuff for days and then it all stops.
When I test the sound app it freezes and I have to log out to get back.
I'm using the default sound card although I have a rme digi card as well, but that take a alot of work to get going.

Cheers
Bob

---

### Post by joe57005 on 2008-02-08
I'm having the same problem. At first i thought it was a problem with the mp3 plugins, until i realized every noise-making program (not just banshee) freezes in the same circumstances. I think it's the soundsystem (or driver or whatever you guys call it, i'm a linux n00b) as the problem stopped when i switched from alsa to oss.

---

### Post by joe57005 on 2008-02-09
i've also been having problems with firefox freezing when playing flash. i think, i think very strongly, that this is related to the sound problems, but i can not test this.
Is there any way to FORCE flash to use oss rather than alsa for sound? i am able to do that for all other programs on my system, and it fixed all of my other problems. if i can do it, i may be able to confirm a link to the sound problems. also, is it possible (or even safe) to reinstall alsa, or downgrade it? i had no problems in feisty, so i'm hoping that downgrading will do the trick. (i want to keep gutsy, though)

---

### Post by bmcatt on 2008-02-09
Note - it appears that one of the recent updates (within the past couple of weeks or so?) has corrected the problem, at least for me. You may want to try fully upgrading your system and see if that takes care of the problem.

---

### Post by joe57005 on 2008-02-09
as far as i can tell, my system's completely up to date. the update manager shows no updates, i'll check through synaptic next.

---

### Post by wavesound on 2008-02-10
HI 
Mine is alway updated,  Gutsy still refuses to use my RME card.

Back to the realtek for me!

Cheers
Bob

---

### Post by joe57005 on 2008-02-12
is there any way to check if alsa is broken, and if so, how can i fix it? all my problems seem to stop when i stop using alsa. it didn't always freeze, i think my problems started about when i installed azureus and java jre. i may (quite likely) be mistaken, i am rather new to all this.

---

