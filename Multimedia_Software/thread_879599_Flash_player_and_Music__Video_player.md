---
title: "Flash player and Music / Video player"
date: 2008-08-04
forum: Multimedia Software
---

### Post by kevintth on 2008-08-04
Something wrong to flash player with other music / video player on Ubuntu. After i finish watch the Youtube video, I cant play any video or music with Rhythmbox music player or Movie player. Then, I must close down the Firefox then only can play song with Rhythmbox. Same problem, if i play the music with Rhythmbox first, then i cant listen any sound from youtube's video while video still playing. What is wrong? Is it a bug?

---

### Post by kevintth on 2008-08-05
why there is no one reply ?  This forum is really bad.:( Every single question i asked was no one reply.

---

### Post by Stochastic on 2008-08-05
Can you give a few more details such as what version of Ubuntu you're running, or what version of flash you have installed, or if the problem exists in any other browser (or if it just happens with firefox), etc...

---

### Post by rossmoore on 2008-08-07
To help this thread along, I can contibute my problems in this area. I run Hardy on a Dell XPS1530 laptop, Nvidia 8600GTM graphics card with fancy effects turned on. I'm using an HDMI connection to feed my audio and video to a flat screen TV.

Here's two failure scenarios:
1. I listen to some music in Rhythmbox, then stop playing that (but leave Rhythmbox running); now I watch a VOB video file using VLC. Then I close that. When I start playing music in Rhythmbox I can't hear anything. I now have to restart Rhythmbox to get audio out.

2. I navigate to a YouTube or BBC video with FF and play that. Most times FF crashes. I restart FF, it says "continue session" (or something similar) and takes me back to the page with the video (thank you!). The video now plays.

I don't know if kevintth shares all of my problems, or I all of his, but they sound similar problems. I believe I followed most of the sticky thread elsewhere on this forum to set up flash in FF and set up the rest of the video and audio - if you have some specific questions for more set-up details I can have a look for you (but only while I'm at the laptop).

---

### Post by NESFreak on 2008-08-07
[http://project.revolutionlinux.com/PulseAudio](http://project.revolutionlinux.com/PulseAudio)

install some dependencies, download the source code, compile and install
```
sudo apt-get install build-essential libtool libesd0-dev libpulse-dev libssl-dev subversion
svn co https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/src/
cd src
make
sudo make install
```be sure to restart firefox. This way flash can use not only alsa but also pulseaudio or esd whichever is available (see link)

--edit--
for some reason it at first didn't appear in synaptic for me, but there is a package for libflashsupport don't know in which repository, but if available installing it this way would be easier. srry i didn't notice it before

---

### Post by tuxxy on 2008-08-07
How did you install flash>?

---

### Post by rossmoore on 2008-08-07
Hmm, I presumed it was an audio server thing, but I don't understand that part of Linux yet. Actually, it seems noone does terribly well, sound does seem a bit of a mess in Linux.

So what's this going to do? Hardy has Pulse as the default sound engine, but I presume that current versions of Flash without this software you link to only use ALSA, is that right? I guess that should solve the FF crashing thing described above.

How about the Rhythmbox and playing a vob in VLC thing? I presume this is also related to ALSA and Pulse, but I guess is because one or both of these don't use the same sound server - right? So I just wait for support to be added to them, and then the problem will go away?

---

### Post by rossmoore on 2008-08-07
This excellent sticky how-to thread describes how to install flash and a number of multimedia related things:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by rossmoore on 2008-08-08
I installed flash according to that how-to.

I've downloaded and installed that PulseAudio support as you suggested, but FF still crashes when I view videos sometimes.

Thanks for the help - any other ideas?

---

### Post by mocha on 2008-08-08
For the Firefox and Flash crash issue you need to search this forum for "firefox flash crash problem" or something like that and you should see a thread with lots of views and responses.  The fix is basically to purge flashplugin-nonfree, install nspluginwrapper (link to deb in thread), reinstall flashplugin-nonfree.  This will "wrap" flash videos when you view them in Firefox, so if the flash acts up it just kills the wrapper, so all you have to do is reload the webpage and it doesn't take Firefox down with it.

For the sound issue, I believe you need to install libflashsupport (look in Synaptic).  You should also search this forums for "how to setup pulseaudio", there is another long thread with a great how-to at the beginning of how to properly get pulseaudio working in Hardy and it addresses this issue you are talking about.

---

### Post by rossmoore on 2008-08-11
Thanks I'll try and have a look at that over the next day or so.

The nspluginwrapper solution doesn't sound like a solution so much as a quick semi-fix. Do we know if someone is working on properly solving the bug?

---

