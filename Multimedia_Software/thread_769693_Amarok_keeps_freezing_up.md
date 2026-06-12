---
title: "Amarok keeps freezing up"
date: 2008-04-26
forum: Multimedia Software
---

### Post by YAOMTC on 2008-04-26
Amarok has constantly been freezing up. I often watch YouTube videos, and every time I have my music playing and forget to pause the music before I watch the video, Firefox gets messed up (the video won't play for more than a couple seconds at a time, and when I close Firefox and try to start it up again, it says it's already running, so I have to kill its process), and when I have a YouTube video up and I try to play music, Amarok freezes up and I have to kill it. I have Amarok set to use PulseAudio, but that makes no difference. Anyone else have this problem?

I'm using Hardy, by the way. Just did a fresh install yesterday.

**EDIT:** Here's the solution: Install libflashsupport and vlc-plugin-pulse, and then set Amarok and VLC to use PulseAudio. According to some accounts, libflashsupport decreases the stability of Firefox when Flash is being used, but I think it's a fair tradeoff for the much more annoying problem it solves.

---

### Post by YAOMTC on 2008-04-26
Okay, now Amarok won't even start playing, period. I don't have YouTube up this time, or anything else that's flash or audio. What the heck... I want my Amarok back! :(

---

### Post by YAOMTC on 2008-04-26
Okay, it seems that PulseAudio is the cause here. I installed Audacious, and it works fine when I use ALSA output, but doesn't play when I choose PulseAudio.

---

### Post by Auslegung on 2008-04-29
I was having very similar problems with Youtube screwing up my audio and subsequently causing AmaroK to crash.  Found this fix [here]("http://ubuntuforums.org/showthread.php?t=771239&highlight=tube"):

Try going to "Synaptic Package Manager" and install "Ubuntu Restricted Extras". Then go to the Medibuntu website and follow the instructions on the "Repository How to" page to copy and paste the commands into Terminal. This should enable everything that you need for all multimedia, including allowing you to play/copy encrypted DVD's and ripping to MP3 with Sound Juicer. Hope this helps.
PS. I'm sure that I didn't have to do anything at all to play Youtube video's with a bog standard installation of Hardy. Perhaps you should try removing the Gnash plugin.

It worked for me.

---

### Post by YAOMTC on 2008-04-29
Well, after that, Amarok still doesn't seem to work through the pulseaudio plugin. Works just fine in ALSA, though, so that's not a problem.

---

### Post by Nero147 on 2008-05-17
thanks a bunch man. That completely fixed the issue I was having with amarok. The only significant problem I've been having with anything since I upgraded to Hardy. Now back to listening to music ;) Aphex Twin FTW!

---

### Post by Emily the strange on 2008-08-07
I have similar problem that YAOMTC has. If I open Youtube, Amarok won't work unless I restart the computer. 

I have already try with re-installation..

---

### Post by YAOMTC on 2008-08-07
Emily, I just edited the first post with the solution. Check it out. :)

In case you're new to Ubuntu, you'll need to install those through Synaptic Package Manger, under System -> Administration.

---

### Post by jarome on 2008-08-19
I just installed 8.04 on an HP mini-note. Amarok flashes up the logo and just disappears. Nothing is in the /var/log/messages file.

What do I do?

Also, do I have to do something special to get it to play mp3s?

Thanks,
Jim

---

