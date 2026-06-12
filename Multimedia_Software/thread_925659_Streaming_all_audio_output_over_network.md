---
title: "Streaming all audio output over network"
date: 2008-09-20
forum: Multimedia Software
---

### Post by Mars Thrax on 2008-09-20
Sorry if this has been covered before...I've done some searching, but I'm not entirely sure on the terminology I should be looking into...

In any case, I have a tablet that, needless to say, has crappy speakers. I also have a desktop that has some pretty good ones. I would like to be able to stream all of my audio output from my laptop to my desktop (Desktop runs Hardy, laptop dual-boots Vista 64 and Hardy) over the network. So, for instance, I could control Pandora from my tablet, but have the sound come out of my Desktop's speakers.

I know I could use VNC or something to just handle it all that way, but that is a lot more overhead than I really need (or want) for just controlling audio. 

Since my tablet dual boots, I'd like to have a client solution that is compatible between the two, however and Ubuntu specific implementation is acceptable (I spend more time in there anyways).

Any information would be greatly appreciated.

---

### Post by cariboo on 2008-09-21
Install samba on your desktop computer and then mount your music directory on your desktop as a samba share and play the tunes from it. Here is a link to a samba howto:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Jim

---

### Post by eye208 on 2008-09-21
You can make the ALSA loopback driver your default sound device, then use Jack and NetJack to transport all audio to the other computer.

---

### Post by markbuntu on 2008-09-21
You can also use pulseaudio to stream to a network:

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

---

### Post by FakeOutdoorsman on 2008-09-21
Another option is [MPD (Music Player Daemon)]("http://www.musicpd.org/").  From the MPD site:
> Music Player Daemon (MPD) allows remote access for playing music (MP3, Ogg Vorbis, FLAC, AAC, Mod, and wave files) and managing playlists. MPD is designed for integrating a computer into a stereo system that provides control for music playback over a local network. It also makes a great desktop music player, especially if you are a console junkie, like frontend options, or restart X often.

Good non-console GUIs for MPD are Sonata and GMPC.  There are all in the repository.

---

### Post by Pro-reason on 2008-09-26
> **markbuntu said:**
> You can also use pulseaudio to stream to a network:

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

That FAQ is less than clear.  Do you know how to enable streaming?

---

### Post by markbuntu on 2008-09-26
I have not tried the pulseaudio rtp sender/client yet but I am thinking about trying it this weekend since I have a Acer Aspire One that has XP on it. I will try to stream from my Ubuntu box to it. I also plan to replace XP on it with Intrepid when that is released and will try that also.

I will write up a how to if I get it figured out and put a link to it here for you.

---

### Post by markbuntu on 2008-09-27
This is what I found so far:


[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

[http://www.pulseaudio.org/wiki/HowToListenToTheRtpStream](http://www.pulseaudio.org/wiki/HowToListenToTheRtpStream)

[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio)

All of these are for streaming linux to linux. The last one seem the most complete but you should look at them all. You will see that you can skip a lot of the basics.

The windows pulseaudio rtp is big pain in the ... no gui, very sketchy docs. I just don't have the patience for that one.

---

### Post by Pro-reason on 2008-09-28
> **markbuntu said:**
> This is what I found so far:


[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

[http://www.pulseaudio.org/wiki/HowToListenToTheRtpStream](http://www.pulseaudio.org/wiki/HowToListenToTheRtpStream)

[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio)



The third of those was helpful.  I can now watch (and listen to) TV on my computer, using the TV tuner which is plugged into my girlfriend's computer.

---

### Post by Jose Catre-Vandis on 2008-09-28
Easiest way is to use vlc for both server and client - cross platform too :)

---

### Post by Pro-reason on 2008-09-28
> **Jose Catre-Vandis said:**
> Easiest way is to use vlc for both server and client - cross platform too :)

Well, obviously not, because I've failed to make VLC work, and the PulseAudio method worked straightaway.

---

