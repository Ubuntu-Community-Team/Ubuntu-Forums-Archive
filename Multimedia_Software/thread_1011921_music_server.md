---
title: "music server?"
date: 2008-12-15
forum: Multimedia Software
---

### Post by Snappo on 2008-12-15
I have an ubuntu box (8.04) which I use for a fileserver, how would I go around setting it up as a music server, so I can stream the music to other Ubuntu computers on the network.

---

### Post by FakeOutdoorsman on 2008-12-15
You have several options.  You could try [MPD (Music Player Daemon)]("http://www.musicpd.org/").  From the MPD site:
> Music Player Daemon (MPD) allows remote access for playing music (MP3, Ogg Vorbis, FLAC, AAC, Mod, and wave files) and managing playlists. MPD is designed for integrating a computer into a stereo system that provides control for music playback over a local network. It also makes a great desktop music player, especially if you are a console junkie, like frontend options, or restart X often.
Good non-console GUIs for MPD are Sonata and GMPC.  There are all in the repository.

Another option is [Streaming on Ubuntu 8.04 with PulseAudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio).  Some people recommend just using Samba to create a shared folder and accessing it from the remote machine.  You could also use sshfs to locally mount a remote directory and play from there using any client.

---

### Post by Snappo on 2008-12-15
I'm messing about with cplay via ssh, it seems to just be playing on the host not the client is there anyway to fix this.

---

### Post by FakeOutdoorsman on 2008-12-15
Ooops.  I wasn't really thinking there.  I meant sshfs.  Of course once that is working you wouldn't need to use a console based client:
```
sshfs snappo@192.168.1.155:/path/to/audio/directory ~/music
```
This will mount the remote machine's directory as ~/music on the local machine.  You could add this to your .bashrc as an alias.

---

### Post by RFGunslinger on 2008-12-15
I run mt-daapd on my 8.04 server.  I pulled it down from the repository and ran through a quick web-based setup.  Rhythmbox detects the share automatically on all of my 8.10 clients.  Its awesome.

---

### Post by Snappo on 2008-12-16
> **RFGunslinger said:**
> I run mt-daapd on my 8.04 server.  I pulled it down from the repository and ran through a quick web-based setup.  Rhythmbox detects the share automatically on all of my 8.10 clients.  Its awesome.

Maybe you could write a quick setup guide? :KS

---

### Post by doobiest on 2008-12-16
If you're just doing this on a local network why dont you just play the files over a samba or nfs mount?

Aren't music streaming servers a little restrictive as far as what you're listening to (predetemined playlists, etc)  and is the audio quality downsampled to be better for streaming across the net?

I don't know just a thought, I'd rather have normal file access to my mp3s.  I stream to all my computers and to my XBMC boxes fine over samba

---

