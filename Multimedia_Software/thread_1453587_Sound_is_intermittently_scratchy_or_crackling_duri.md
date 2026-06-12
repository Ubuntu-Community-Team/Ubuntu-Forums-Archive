---
title: "Sound is intermittently scratchy or crackling during games"
date: 2010-04-13
forum: Multimedia Software
---

### Post by travlemon on 2010-04-13
Hey everybody!

I'm slowly addressing some of my issues with my Ubuntu 9.10 installation.  One that I can't seem to find a solution for is my audio problem.

It seems like it's mostly an issue with playing games.  When I play certain 3D games, the audio may work for a little while, but will start getting scratching or full of static.  Some times it's a lot, and other times it's just a little bit.  Most times, the sound in the game will stop working after a short moment of static/scratchy sound.  Then I am left with complete silence.

I've seen on other posts that PCM volume may be turned up all the way.  I wasn't sure what PCM was, but in the volume controls, I saw that you could adjust each individual application's volume. I assumed that this was PCM, as the game's volume was all the way up.  I turned it down some, and I still got some static in the sound, and the sound still disappeared completely after a short time.

Has anyone else had this problem? This one is probably the most noticeable problem I've had with Ubuntu. 

Any help is MUCH appreciated!

---

### Post by hawthornso23 on 2010-04-14
I have just fixed a similar problem. Edit (as sudo) 

/etc/openal/alsoft.conf

scan down to find where it is talking about drivers. Uncomment and change the order  of listed drivers so that oss is listed first. Mine now says

drivers = oss,alsa,pulse,solaris,dsound,winmm,port,wave

What this fixes is a problem with the openal multiplatform sound system used in many games. Supposedly openal can plug into a wide variety of sound drivers on many platforms (including windows), however the developers seem to be concentrating most of their attention on windows these days and the linux drivers are bugridden and cause problems.

The default is alsa, which is why it is listed first. But this seems buggy and results in terrible sound distortion on Karmic. You get horrible farting sounds which get worse and worse untul the game hangs. 

The pulse interface doesn't seem to work at all. Listing pulse first results in a blank screen and immediate lockup whenever you try to play a game.

The solaris, dsound, winnm, port, and wave drivers are for other platforms. 

The oss driver is the only one that works properly.

Try it. It made a HUGE difference to my sound.

---

### Post by lidex on 2010-04-14
Try installing this package:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```
There is a known bug with alsa-plugins

---

### Post by travlemon on 2010-04-14
> **lidex said:**
> Try installing this package:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```There is a known bug with alsa-plugins


Hi!

To both of your responses, BIG THANKS!  I tried both, and it seems to have done the trick.  I'm not sure which one did it, but I thought it was good to do both. I'll be marking this as solved and saving for future reference!  Thanks again!

---

