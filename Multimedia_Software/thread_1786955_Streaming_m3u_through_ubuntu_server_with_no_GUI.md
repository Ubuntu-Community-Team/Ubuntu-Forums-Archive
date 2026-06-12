---
title: "Streaming m3u through ubuntu server with no GUI"
date: 2011-06-20
forum: Multimedia Software
---

### Post by Euan1000 on 2011-06-20
Hi

This is my first ever post for help so be easy on me if I'm in the wrong place or dont provide enough details :?

About a year ago I installed Ubuntu Server 9.10 Karmic on a machine at my work to act as a file/print server and ftp host.  I managed this with a lot of googling and reading of forums and it's still all working exactly as it did on day 1!

Now I would like to use the server to stream a local radio station through speakers into the workshop.  I have again googled but have not managed to come up with a solution for a server sytem with no GUI...

The radio station streams in a m3u format.

Thanks in advance for any help you can give,
Euan

---

### Post by nothingspecial on 2011-06-20
You want to use the server to stream the radio station to another device in the workshop, or you simply want to plug the speakers into the server and play the radio stream?

---

### Post by Euan1000 on 2011-06-20
Thank you for your reply.
 
I simply want to plug speakers into the server and play the music through them.

---

### Post by tgalati4 on 2011-06-20
sudo apt-get install mplayer-nogui
man mplayer
mplayer [www.radiostation.com:8888://playlist.m3u](www.radiostation.com:8888://playlist.m3u)

One of my favorites:  Groove Salad

mplayer [http://somafm.com/groovesalad.pls](http://somafm.com/groovesalad.pls)

Once you get that working, then you will want to checkout music player daemon:

apt-cache search mpd
sudo apt-get install mpd

mpd has many clients to control it remotely, so it's convenient to put mpd on the server and use any other machine on the network to control it (start/stop/volume, change playlist, etc).  It will play any music stored locally on the server or music stream URL's.

[http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki)

---

### Post by Euan1000 on 2011-06-20
Thank you. I will try that tomorrow morning.

---

### Post by nothingspecial on 2011-06-21
Then you will need to install some sound related stuff.


```
sudo apt-get install alsa alsa-tools mplayer
```

Then add your user to the audio group

```
sudo adduser $USER audio
```

You might need a reboot here.

Then just

```
mplayer <address_of_stream>
```

If that doesn't work you may simply need some codecs, post back.

---

### Post by Euan1000 on 2011-06-21
Well I installed mplayer and tried to play the radio, it all seems to be working on the screen but no sound is coming out the speakers!

I have never played any music on this server and the only noise that has ever come out the speaker before was 'beep' like when you press the left cursor before input text on the command line.

Now I'm thinking there must be soming wrong with the audio modules or drivers??

I've followed the troubleshooting guide here 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) 

and found that I can't play the front_center sound although again on screen it looks like it's doing it right.

I've got as far as uploading my sound information to an alsa project webpage here,

[http://www.alsa-project.org/db/?f=2f406d2777149c25e7056b2745db137e99e2d632](http://www.alsa-project.org/db/?f=2f406d2777149c25e7056b2745db137e99e2d632)

I dont know if you're able to see whats wrong by looking at the web page.

Euan

---

### Post by tgalati4 on 2011-06-21
aplay -l

Try all the sound jacks.  Sometimes they are miswired.

alsamixer

Turn up the volume.

---

### Post by Euan1000 on 2011-06-21
Thanks. Got some time before I came home tonight. Tried all the jacks and I had previously turned all the volumes up on Alsamixer, still no sound.

Don't know why but I decided to reboot the machine and now it works! Wish I'd tried that an hour earlier. Anyway I can now play the radio station through the server.

Only had time for a quick look at mpd. I think I'll have to try and find walkthrough for installing... Could you recommend one or give me a few pointers? I only want to use it for this 1 radio station.

---

### Post by nothingspecial on 2011-06-21
> **Euan1000 said:**
> 

Only had time for a quick look at mpd. I think I'll have to try and find walkthrough for installing... Could you recommend one or give me a few pointers? I only want to use it for this 1 radio station.

If you only want to listen to the radio, stick with mplayer. No need for mpd.

---

### Post by tgalati4 on 2011-06-21
sudo apt-get install mpd mpc

mpd allows remote control from several machines.  You can control mplayer remotely by logging in and killing the process:

sudo killall mplayer

You can also adjust the volume with alsamixer.  mpd allows web-based, cli-based, and widget-based control from any machine on your network.

---

### Post by Euan1000 on 2011-06-22
Thank you for your help. All working now. 

Cheers

---

