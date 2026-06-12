---
title: "music-playing daemon with cross-platform GUI? webui?"
date: 2009-07-04
forum: Multimedia Software
---

### Post by ioxitial on 2009-07-04
I have a server with Ubuntu Server Edition 9.04 on it and two laptops, one with Ubuntu and one MacBook. What I would like to do is plug speakers into my server and be able to play music directly on the server, but control it using a GUI or Web UI from any other computer.

I've looked into programs like gnump3d, but I'm afraid its antiquated methods of cataloguing music may not be sufficient for my 100+ GB collection, beside the fact that I would like to stay away from a Web UI if possible; and if I had to use a Web UI, I would like it to be a bit more AJAX/Web2.0-ish. also I'm not interested in streaming and this looks like primarily a streaming program even though someone recommended it for the purposes I'm describing.

Ideally the setup would work similarly to how the Deluge bittorrent client does, with a daemon running on the server and cross-platform GUI client to control it. the GUI would have to be separate from say, iTunes, since I like iTunes to keep its own library. Even a shell program that uses a faux-GUI (like aptitude) may work for my purposes. anything that requires a GUI to be running on the server itself or that requires a remote X session is not acceptable.  Thanks for any suggestions...

---

### Post by RD1 on 2009-07-04
I'm not sure how it would be done but, if you have the pulseaudio server installed and running on your server, you should be able to use any player on a client machine and send the audio directly to the server.

I would do some Google searching for a how-to.

---

### Post by ioxitial on 2009-07-04
> **RD1 said:**
> I'm not sure how it would be done but, if you have the pulseaudio server installed and running on your server, you should be able to use any player on a client machine and send the audio directly to the server.

I would do some Google searching for a how-to.

This seems to be the clue that I needed, and may in fact be the preferable solution. I didn't know pulseaudio had that capability. However I'm having difficulty finding an iTunes-compatible solution (necessary for me if going with this method) but I'll keep searching. Also, would this take up double the network bandwidth - redundantly sending audio data to my laptop then back to the server? (since my iTunes library is based on an NFS share from the same server)

---

### Post by ioxitial on 2009-07-04
from one of the PulseAudio devs:

> Before you ask: it is unlikely that we will ever make PulseAudio be able to act as an ApEx compatible device that takes connections from iTunes (i.e. becoming a RAOP server instead of just an RAOP client). Apple has an unfriendly attitude of dongling their devices to their applications: normally iTunes has to cryptographically authenticate itself to the device and the device to iTunes. iTunes' key has been recovered by the infamous [Jon Lech Johansen]("http://nanocr.eu/2004/08/11/reversing-airtunes/"), but the device key is still unknown. Without that key it is not realistically possible to disguise PA as an ApEx.

so that's one route closed. i wonder if you can pass Core Audio over the network? i have no clue with this stuff.

---

### Post by RD1 on 2009-07-04
Have you looked at [Songbird]("http://www.getsongbird.com/") as a possible player?

---

### Post by tgalati4 on 2009-07-04
Why won't mpd work?  That is what it was designed for.  You can run mpc (music player client) on a lot of different machines to control mpd on the server.  There are various gui's to drive mpc.

With a bluetooth phone, you can get fancy and control the music with your phone including turning it on and off when the phone is within range.

---

### Post by ioxitial on 2009-07-04
> **RD1 said:**
> Have you looked at [Songbird]("http://www.getsongbird.com/") as a possible player?

no, but i will

> **tgalati4 said:**
> Why won't mpd work?  That is what it was designed for.  You can run mpc (music player client) on a lot of different machines to control mpd on the server.  There are various gui's to drive mpc.

With a bluetooth phone, you can get fancy and control the music with your phone including turning it on and off when the phone is within range.

this will likely work and is exactly what i was looking for. i didn't think it would be as easy as typing "music player daemon" into google so my searches were a lot more obtuse...

thanks

---

### Post by tgalati4 on 2009-07-05
It's as easy as:

sudo apt-get install mpd mpc
man mpd

apt-cache search mpc

---

### Post by raboofje on 2009-07-05
It's not quite clear to me on which machine your media files are located: if they're on the server (or if you don't care), by all means check out mpd.

---

### Post by RD1 on 2009-07-05
A GUI for mpc is in Synaptic ... GMPC (Gnome Music Player Client)

The problem is, this is not a cross platform solution. Songbird is available for Linux, Windows or Mac.

---

### Post by tgalati4 on 2009-07-05
I think there are mpc clients for Mac OS X.  I remember playing with them in the past.  There must be some simple Window's clients as well, since it is open source and it's a relatively simple communication protocol.

Heavy lifting is done by the server daemon which would be running on Linux.  The music files can be anyware on a local LAN with some simple filesharing set up if the music is not hung directly off of the server.

---

### Post by meatlover on 2009-07-05
I have the same setup as you: a macbook, a laptop running ubuntu 9.04 and a headless server running ubuntu 9.04.  

I want every sound that is played on my laptop to be routed to the server instead of my laptop, so that I can plug speakers into my server and essentially have wireless speakers.  I'm not sure if mpd could do this.  I believe Pulse Audio can based on this link:

[http://pulseaudio.org/wiki/FAQ#HowcanIusePulseAudiotostreammusicfrommymainPCtomyLANwithmultiplePCswithspeakers](http://pulseaudio.org/wiki/FAQ#HowcanIusePulseAudiotostreammusicfrommymainPCtomyLANwithmultiplePCswithspeakers)

Would I have to install audio drivers on my server in order to play the music, or is something like that already pre-installed?  At the moment the server only has an ssh server installed on it.

Is this similar to what you want to do?

Also, after installing pulseaudio via "apt-get pulseaudio" on my ubuntu server I get the following output for the following commands:

```
$ pulseaudio load-module module-rtp-recv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_24c5_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_8086_24c5_sound_card_0_alsa_capture_0 tsched=0"): initialization failed.
^CE: module-gconf.c: Unable to read or parse data from client.

```

---

### Post by meatlover on 2009-07-08
I hate to do this but "bump"

---

