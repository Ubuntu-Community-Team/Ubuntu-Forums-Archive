---
title: "Live Shout Streaming"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by drhiii on 2008-02-17
Before posting the question...I've been searching for solutions for several hours and am not nailing one down, so came here...

I have set up an icecast2 server.  No problems.  Ran outta the box, configuration is familiar, everything looks good.

I have a Ubuntu client machine that I was to capture the audio from (darkice??) and stream it to the icecast2 server (separate box).  I've like to be able to use an existing plugin that can perform the audio capture, and push the stream fo the icecast2 server.  I mucked around with xmms but recent information says that this is unstable, not recommended, and indeed I did not get it to sync up a stream with the icecast2 server.

Lots of mention of WInamp Plugins that will do this, but that is Winamp (windows, yuk)

So, can anyone point me to a HOWTO on getting an Ubuntu client machine to capture and transmit audio to an icecast2 server?

---

### Post by drhiii on 2008-02-18
Hm, this is getting a bit messier than I thought...

Having poured over scads of tutorials, HOWTOs, etc, I have been able to successfully (I think) install an Icecast2 server.  It runs as a daemon, accepts a stream, am able to view the admin screen, it shows a mount point when a stream is pointed at it, shows when I attempt to connect to it with a browser that a client has connected.... and....   I installed Darkice, am able to play an audio file, it connects to the Icecast2 server, and all appears hunky dory.  

Except, there is no sound.  The client app (have tried several incl XMMS, VLC, and so on) all keep trying to reconnect to the stream.  I think what is happening is that Darkice is not capturing the audio source properly, so when everything else appears to be connecting or syncing, if there is no audio in the stream, the behavior is as if everything is working, but no audio.  I am not studied enough in this yet to know if this is indeed what is happening... but am continuing to try and learn what part of my configuration is not working.  I do think it is DarkIce.

So... anyone able to point me to a Tutorial or Howto that they followed, and it worked?

Also, the server side is on a live server connected to a public IP.  The port is whitelisted of course, otherwise I would not be able to send a stream to it, or I would not be able to view the admin screens for Icecast2.

The client machines has been both a laptop and a desktop running v7.10 with everything current as can be.  

Darkice is configured having followed several examples and Icecast2 does report the mountpoint, and this all appears correct.  Just... no sound.  I have been trying to discover what the alternatives are for the   'device = /dev/dsp' 

I have also started to try MPD as this has come up as a working alternative.

Anyone have any suggestions here?  I've worked through a ton of cool apps in Ubuntu, but this is the first one that has brought me almost to my knees.  Or at least to drink a few beers, tho I would do that anyway.  

Help?

---

### Post by JvdS45 on 2008-02-24
Hi 
I also tried to connect as a client with several programs and indeed i was connected but no sound, The best connection i had was liveice using in xmms but no sound even i saw i was connected.

I am thinking something has todo with porting to the streamer ( maybe a port is closed) I am trying to find out why.

I hope somehow there is a solution. BTW when searching over the internet it seems the problem is already a long time and nobody gives a good solution. 


are we the only ones :-)

Johan

---

### Post by drhiii on 2008-02-24
I did finally have success with IDJC or Internet DJ Console.  You can pull it down through synaptic as IDJC.  Note that as is, it does not work and I had to find some further tweak in the Ubuntu Forums to upgrade a component or two, can't recall off top of head (gee, and it was just last week too).  But I was able to get IDJC to connect to an Icecast2 server and push a .ogg stream.  .mp3 is broken in this version.  But it did work and I found IDJC to be quite handy once it became familiar.  

As noted, it will take some additional fixes that can be references here I believe, and it does work.  Nice, fully featured application.  I never could get any other combination of darkice, or client side app working with an icecast or icecast2 server.

---

### Post by FrankVdb on 2008-02-24
Nice to read you found a solution.

I was going to mention gnome-peercast. Available from the repos. It's basically a Gnome interface for peercast but maybe it fits your bill.

---

