---
title: "Control Patio Tunes from Laptop"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by flyboy917 on 2009-09-04
Ok, I have a Jaunty machine hooked to my stereo receiver and my receiver has a second speaker zone that is on the patio. I'm running Amarok to play my music. I'd like to use my laptop, on the patio, to run the thing. i.e. not have to go in the house to play a requested song. Is there a way to do this?

---

### Post by Whiffle on 2009-09-04
I don't know about Amarok, but this is what MPD is designed to do.  You run the mpd daemon on the one hooked up the the stereo, and then you run a client such as Ario or Sonata on your laptop.  It talks to the daemon over the network, and controls the playback.  I have this setup here and it works very well.

---

### Post by flyboy917 on 2009-09-05
> **Whiffle said:**
> I don't know about Amarok, but this is what MPD is designed to do.  You run the mpd daemon on the one hooked up the the stereo, and then you run a client such as Ario or Sonata on your laptop.  It talks to the daemon over the network, and controls the playback.  I have this setup here and it works very well.

K, so I install Ario or Sonata on both systems, make one the server and one the client, and badda boom? 

It is Labor Day weekend. Need tunes outside!

Cheers 
Thanks....

---

### Post by Whiffle on 2009-09-05
Not quite, you install mpd on the one hooked to the stereo (the server), and then Ario or Sonata on the one you want to control it from (the client).  Here's the wiki for mpd:

[http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki)

---

### Post by bear24rw on 2009-09-05
You can also try Exaile with the web frontend plugin

---

### Post by flyboy917 on 2009-09-05
Ok, I've got mpd configured and running. Now Ario sees the computer with the mpd daemon on it but wont let me connect. "impossible to connect to server. check conections settings"

---

### Post by Whiffle on 2009-09-05
I think you need to go into the mpd config and allow it to accept connections from other computers.  Go into /etc/mpd.conf, and change the "bind to address" line to whatever ip address that computer is using.  Then restart mpd and try connect again.

---

### Post by issih on 2009-09-05
For something like this, there a lots of options, heres a couple of the ones I consider simple

"ssh -X" into the box with the tunes and then run whatever music app you like from that terminal....the remote app will display on your local X server and there you go...not ideal for games, but should work for choosing playlists.

vlc, it comes with a built in web interface that you just have to turn on from the menus, and is perfectly capable of playing music as well as videos.

Hope that helps

---

### Post by flyboy917 on 2009-09-05
> **Whiffle said:**
> I think you need to go into the mpd config and allow it to accept connections from other computers.  Go into /etc/mpd.conf, and change the "bind to address" line to whatever ip address that computer is using.  Then restart mpd and try connect again.

Ok, had to set the "bind to address" to the IP address of the machine running mpd. We're up and running with no music client just Ario. 
Outstanding guys! Thanks!::KS

---

