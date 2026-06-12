---
title: "Syncing audio output between two (or more) computers"
date: 2008-05-30
forum: Multimedia Software
---

### Post by SgtDude on 2008-05-30
Please read this post in it's entirety before replying.

I would like to be able to play an audio file on two (or more) different computers and have them synced together precisely, so that when I move from one computer to the other, I hear the same song continuously, like adding speakers to a single sound system.

Ideally, this would be used to make every computer in the house part of a single sound system, all playing the same song at the same time, all in sync with one another.

I apologize if I'm being a little long winded with the description of my goal, but I'd like to minimize the number of posts simply telling me how to set up a samba/nfs share.  Setting up a share is only a tiny portion of the problem.

I've got a pretty good idea of how a solution would work, I'm just looking for the community's thoughts, and maybe some pointers as to implementing it.

First, I'll need to use NTP to make sure the clocks on all the machines on my network are precisely in sync.  I think I can use the "at" command to tell all the machines to play a given audio file at exactly the same time.  

Now, if all of the machines take exactly the same amount of time to start the app and load the file, then I have a rudimentary solution.  However, given different hardware, different network speeds (wired/wireless) between the machines and the server hosting the file, and different loads on the machines, I think it's highly unlikely that they'll all start the audio file at exactly the same time.

I can think of two potential solutions to the problem:
a.  Tweak a current project to load the software, cache a portion of the audio file, and then wait until an agreed upon time to start playing the file.
b.  Make a ramdisk on each machine, and store the executable and the audio file on the ramdisk, then start the app and load the file from the ramdisk.  This should get all the machines to start playing the file within milliseconds of each other.

I'm not a programmer, but I know my way around bash scripting, so I think I'm going to go with option b.

Then again, I think I've read some stuff on pulse audio that says it might have some of the functionality I'm looking for.

So does anyone have any thoughts or suggestions on this?

---

### Post by forezt on 2008-05-30
One thing to look into is the music player daemon.

With MPD, you can stream music through the network. Many people use it to broadcast internet radio stations, but it works just as well (in fact better) on your local network. 

You can even re-encode the music on-the-fly so that it transmits faster through the network (at the cost of sound quality, of course). Since it uses a standard protocol, you can stream to windows, gnu/linux, os x, and almost any other OS, even some cell phones and handheld devices. 

I've only messed around with MPD, but there are some people that swear by it:

[http://www.musicpd.org/]("http://www.musicpd.org/")

[http://mpd.wikia.com/wiki/Configuration]("http://mpd.wikia.com/wiki/Configuration")

Happy streaming.

---

### Post by SgtDude on 2008-05-30
Upon further inspection it seems that PulseAudio should solve my problem.

[http://www.pulseaudio.org/wiki/FAQ#IsPulseAudiocapableofprovidingsynchronizedaudioplaybackoverthenetworkformovieplayerslikeMPlayer]("http://www.pulseaudio.org/wiki/FAQ#IsPulseAudiocapableofprovidingsynchronizedaudioplaybackoverthenetworkformovieplayerslikeMPlayer")

I'll let you guys know how it goes.

---

