---
title: "amarok won't play music"
date: 2009-08-18
forum: Multimedia Software
---

### Post by LifeEnemy on 2009-08-18
Hi all,
I've just switched to Ubuntu while upgrading my hard drive (set up a dual-boot with vista) after seeing a friend who switched. So far, I really like what Ubuntu has to offer. The one problem I'm having is finding a good music player. I've tried out many, but most don't fit my needs. I'd like to see if Amarok can do what I need it to do, I've heard that it can do crossfade, or some kind of gapless playback. However, I can't get Amarok to work at all. It detected all of my music at start up fine, and everything seems to work except the actual playing of the music. Whenever I try to start, Amarok says that it's playing the song but no sound is produced (other players and sound sources work, it's not my system). The progress bar of the song also doesn't move. I've tried a number of potential solutions I found here and other places:

1. Installed xine-ui and changed audio driver to Alsa and Pulseaudio ("audio driver to use" option under the 'audio' tab, right?)

2. I've heard mention of changing the engine in Amarok, but I can't find any option for that within Amarok.

3. I went through a setup guide for pulse audio that I found on these forums. This did fix some other problems that I had, but Amarok still doesn't work.

4. I heard of installing different packages (amarok-xine, amarok-engines, amarok-arts) but I couldn't find any of those in synaptic.


I'm not sure what to do anymore, and that's why I'm here. Any help would be greatly appreciated.

Also, this isn't related to my specific problem, but can any Amarok users tell me if it has an EQ? And is crossfading/gapless an actual feature? Those are the two most important things for me in an audio player.


EDIT: Forgot to mention, I also get an error message from the tray icon most of the time when I start Amarok: "The audio playback device **HDA Intel (STAC92xx Analog)** does not work, falling back to **default**"

---

### Post by stetzwebs on 2009-08-27
I am having the same problem. Also, whenever I try to scan my collection, the collection scan hangs at 97%. I have found absolutely no help on either of these subjects anywhere, and am very hopeful that someone has found a solution to these problems.

---

### Post by PFN on 2009-08-29
Having same problem (No sound in Amarok, Same Error message on Amarok start-up).
All other media players (Rhythmbox, Totem, VLC and Exaile) working well.
Somebody please help.

---

### Post by senor_smile on 2009-08-29
I am having a similar problem.  No mp3's will play in either amarok or exaile.  rhythmbox works just fine though.  

EDIT: In amarok I get the exact same message: "The audio playback device HDA Nvidia (ALC1200 Analog) does not work, falling back to default

---

### Post by ad_267 on 2009-08-29
Try installing the kubuntu-restricted-extras package. Xine requires different packages to gstreamer for mp3 playback.

---

### Post by senor_smile on 2009-08-29
I installed the kubuntu-restricted-extras 
which installed: 

  kdelibs-data kdelibs4c2a kubuntu-restricted-extras libavahi-qt3-1
  libdbus-qt-1-1c2 libk3b3 libk3b3-extracodecs liblua50 liblualib50
  libtunepimp5 libtunepimp5-mp3

Amarok still has the exact same error and won't play any mp3's however.

---

### Post by ad_267 on 2009-08-29
Some of the comments here might be helpful: [http://ubuntuforums.org/showthread.php?t=1253150](http://ubuntuforums.org/showthread.php?t=1253150)

---

### Post by PFN on 2009-08-30
I just removed Amarok-2 and installed 1.4 version. It is working great from the first start-up without any configuration changed.And sure, it is a great player worth a try.
You have to add the sources, just see this page: [http://www.ubuntugeek.com/howto-install-amarok-1-4-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-install-amarok-1-4-in-ubuntu-jaunty.html). Don't forget to give a look on the comments on the page.
Have fun guys.

---

### Post by Sephoroth on 2009-08-30
You may also wish to try installing phonon-backend-xine and libxine1-ffmpeg.

@LifeEnemy:  If you still can't get it to work or dislike Amarok 2.0, I suggest taking a look at Exaile, Banshee, and Songbird (the last of which I have become quite fond of).

Amarok 2.0 still seems like it needs a bit more time to mature.  It's release has been worse than that of Windows Vista o.O.

---

### Post by LifeEnemy on 2009-08-30
> **Sephoroth said:**
> You may also wish to try installing phonon-backend-xine and libxine1-ffmpeg.

@LifeEnemy:  If you still can't get it to work or dislike Amarok 2.0, I suggest taking a look at Exaile, Banshee, and Songbird (the last of which I have become quite fond of).

Amarok 2.0 still seems like it needs a bit more time to mature.  It's release has been worse than that of Windows Vista o.O.


I thank everyone for the suggestions. Hopefully they help solve the problem that many people seem to be having. Personally, I have given up on Amarok and am now using Banshee. Hopefully this problem can be solved for others, though.

---

### Post by senor_smile on 2009-08-30
I have installed all recommended components and still have the same problem with amarok.  I tried reinstalling exaile and tried banshee too.  All three of these programs won't play anything. 

As of now, only mplayer, vlc and rhythmbox work fine for playing mp3's(the ones that came preloaded with ubuntu!)

---

### Post by amx109 on 2009-12-12
> **Sephoroth said:**
> You may also wish to try installing phonon-backend-xine and libxine1-ffmpeg.

@LifeEnemy:  If you still can't get it to work or dislike Amarok 2.0, I suggest taking a look at Exaile, Banshee, and Songbird (the last of which I have become quite fond of).

Amarok 2.0 still seems like it needs a bit more time to mature.  It's release has been worse than that of Windows Vista o.O.

had the 'amarok wont play mp3s' problem. installed libxine1-ffmpeg

worked a treat. mp3-playback-ahoy!

thanks.

---

