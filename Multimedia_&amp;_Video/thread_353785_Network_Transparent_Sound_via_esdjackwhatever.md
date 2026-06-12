---
title: "Network Transparent Sound via esd/jack/whatever?"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by braddock on 2007-02-05
I am attempting to stream all sound playing on my one Ubuntu computer to a computer with speakers in another room over the network.

I've been able to do this using esd/esound's network transparent sound protocol successfully.  Below are my notes on how to do this with esd.

But I would like to also stream non-ESD applications (for example, Real Player) to the esd server running in the other room (the second computer is an iPaq running Familiar, so I'm largely stuck with esd).

I believe this can be done with the Alsa loop capabilities and JACK or PulseAudio, but cannot find out how.  Does anyone know?

Here are my notes on a pure esd setup for the enlightenment of others:

Network Transparent Sound using ESD - 2/3/07

On "server" machine (with speakers):
killall esd
esd -tcp -public

On "client" machine (with app):
apt-get install esound-clients
esd # if not already running
esdmon | esdcat -s 192.168.1.106 # or whatever is your server IP

Now, start an ESD-capable app on client.  For example:
xmms music.mp3
Right click on xmms window, Options->Preferences->Output Plugin = eSound Output Plugin
apply and stop and restart song.

voila, should work. Volume control is independent on each machine.
about a 200ms or so delay on my wireless lan.

You can force mplayer to output to the ESD server as well:
mplayer -ao esd 04.mp3

gxine - works, but appears to have significant latency issues (20 sec?)
gxine can handle Real streams.
gxine -pq -g -H -A esd 04.mp3

------
PS - Of course i can use gxine to handle Real streams, but it doesn't always work properly, and Xine has latency issues when using esd.

---

### Post by braddock on 2007-02-06
I've figured this out now.  Hopefully these notes will be helpful to someone.

Using ALSA with ESD to transport ALL SOUND over the network to an esd server:
The above is limited to esd-output programs.

However, by using a monitor mode under ALSA, we can actually loop back ALL
audio output.

First, we need to turn on the "Capture" and "Mix" inputs.  You can do this
manually via GUI with gnome-alsamixer (or even the default Gnome mixer), or we
can do it via command line:
amixer set Capture cap
amixer set Mix cap

Now you can feed the alsa loopbacked input device to esdcat using sox:
rec -c 1 -r 44100 -s w -t raw - | esdcat -m -s 192.168.1.120

Voila.

---

### Post by .Mo on 2007-07-09
Works great!! Thanks so much! Tried to figure this out for quite a while.

Very helpful notes, just think it's important to let ppl know ;-)

=D>

---

### Post by pimlottc on 2007-07-15
Ah, very helpful.  I've been looking at doing this with my laptop, due to my dissatisfaction with its wimpy speakers.  Unfortunately, the audio can be chopping at times, even though I am quite close to the wireless router.

I'm also thinking about how to set up something to automatically fall back to the built-in speakers when the esd server is not available (i.e. when using the laptop elsewhere).  Not so much an issue for desktop computers but would be nice for the lappy.

Ideally the system would be set up to also use local sound when speakers or headphones are directly connected to the machine, although I'm not really sure it's possible to detect this.  Then again, MacBooks seem to do this (OS X maintains a different volume state for speakers and headphones.  Very handy so you don't deafen yourself accidently, or so you don't accidently wake your spouse when the headphones come unplugged).  But that might just be Mac Magic hardware.

---

### Post by dthiessen on 2007-07-22
I've also tried to figure out a way to do this for quite a while. Do you think there is any possibility of using gstreamer?

---

### Post by MrHippocampus on 2007-07-23
For network transparent sound you should really be looking into [pulseaudio]("http://www.pulseaudio.org/"), apparently its going to be the default sound server in the next fedora/ubuntu/other distros. The packages for it in the repo's for feisty so it should be pretty easy to get going (theres a bit of info on the set up at ubuntuguide.org)

One of the nice things about it is that you can run a program in the tray which you can just right click on and re-direct all of your audio to another computer (windows or a linux box). So its great for switching between laptop speakers/headphones whilst on the move and then your main PC when at home.

---

### Post by Genecks on 2007-08-15
The tutorial is not very good. For one, it lacks detail and explanation. It doesn't explain how the person is switching from a server to a client. Nor does the original thread creator explain why he or she puts those words in parentheses. I suppose it's enthymatic, but this audience member does not share nor understand the implied premise.

Ugh, to say the least. It looks like this is the only decent tutorial on this topic I've been able to find in five hours of searching on the web. And sadly, it isn't detailed enough. Whatever people are doing, this tutorial is not working for me. Upon the second post, the author did not even say what the IP address is for? Is it for the client or the server? I tried both, regardless, and I didn't turn up any good results. Then again, how is it that you type from the client to server when the client is on the freaking server. I'm using XDMCP. I suppose all of you are using VNC?

I want to transport sound to the client, not the server.

And where exactly do I put this line?
rec -c 1 -r 44100 -s w -t raw - | esdcat -m -s 192.168.1.120

I suppose I employ it on the server, right?

I've tried a variety of the possibilities, and none seem to have worked.

---

### Post by ^rooker on 2007-09-29
I'll try to improve the information details of this thread:

**1) Configure the ESD server:**
- Install esd (esound) and the client tools:
#apt-get install esound esound-clients

- Edit the esd config file "**/etc/esound/esd.conf**" to look like this:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-tcp -public
```
In my example, I've added the default options "**-tcp -public**" in order to make esd listen to a tcp connection from non-localhost computers.
(you can add "-port" to specify the port explicitely)

Furthermore, it's possible to tell esd exactly which soundcard to use, in case you have more than 1 audio devices in that computer. Just add another flag at the end of "spawn_options" - like "**-d hw:1" for the second alsa device**, or "-d default" to use the default audio device set by "asoundconf set-default-card".

**2) Configure the client(s)**
Most of the ways previously mentioned in the above threads are more complicated than necessary. According to Esound-docs, all esd-clients make use of the environment variable "ESPEAKER=host:port" to determine which server to use.

- To configure this setting system-wide, add the following line to "**/etc/bash.bashrc**":
```
export ESPEAKER="your_esd_server"
```

- You must logout/login in order for your system to realize that new environment variable.

- **Tip: **If you have your own in-house DNS, you can add a new subdomain pointing to the server running esd. In my case, I have "export ESPEAKER=sound.localdomain.home".


**3) Configure the client applications:**
- Choose ESD as output method. Since they will read the value of $ESPEAKER, you don't have to tell it which server:port to use.


**4) Test it with *one* client only at the beginning.** [ESD has some authentification mechanism to prevent audio-eavesdropping]("http://developer.gnome.org/doc/whitepapers/esd/"), so without proper configuration of access rights, esd will not allow more than 1 clients to connect by default. 

- If one client works, stop the esd on the server:
```
#killall esd
```

- Then make sure that all users/clients have the same "**~/.esd_auth"** file.
This file seems to be automatically generated by esd on the first startup of a client application, so what I did was simply use it from one user's home directory and overwrite the others' .esd_auth files.


----------- useful ressources ------------
[http://www.linuxfan.dk/download/readme-ESD.txt](http://www.linuxfan.dk/download/readme-ESD.txt)
[http://mail.gnome.org/archives/gnome-list/1999-January/msg00084.html](http://mail.gnome.org/archives/gnome-list/1999-January/msg00084.html)

---

### Post by moon2js on 2007-11-08
You guys are going to laugh at me, but what I do is I plug in an audio cable from my speaker-less computer's audio-out jack and then plug that into my speaker-equipped computer's audio-in jack. It works, but I think my cable is really cheap/flakey and often there is interference (buzz) or one of the channels is gone until I tweak the cable a bit. This is really annoying, so I'm looking into sending the audio over ethernet.

Trying to decide whether to try this or PulseAudio.

---

