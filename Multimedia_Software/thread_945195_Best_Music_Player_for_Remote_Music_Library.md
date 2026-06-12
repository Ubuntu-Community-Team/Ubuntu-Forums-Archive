---
title: "Best Music Player for Remote Music Library"
date: 2008-10-12
forum: Multimedia Software
---

### Post by crazybilly on 2008-10-12
I've been poking around, looking for a music player I can really latch on to (I was crazy for Foobar2000 in my windows days).  But right now, my music library is primarily on my home server, but most often, I want to play music on my laptop.

The files are shared via samba, and I often (but not always) mount the share via sshfs when I need to get to it.

Amarok, Banshee and Rhythymbox all do ok when the music directory is mounted, but get real angry when it's not.

Is there a music client that handles remote music libraries well?

---

### Post by itix on 2008-10-13
I'd reccomend Exaile. It doesn't shout at you, it just ignores those not there. You have to update collection though before it realizes that your music is no longer available...

Quite nice actually when you have most your music on a 16 gb sdhc card.

---

### Post by aeiah on 2008-10-13
you could install a daap server on the server and get your music player to connect that way. it should behave even if the server is down. i think all the main music clients for linux support daap

---

### Post by Archmage on 2008-10-13
> **crazybilly said:**
> Amarok, Banshee and Rhythymbox all do ok when the music directory is mounted, but get real angry when it's not.

How does an angry Amarok does look like? Last time I did check it was simply skipping the files that are not there, but play them, when they are there.

---

### Post by vanadium on 2008-10-13
Rythmbox *is* angry: it starts to remove all files that it won't find. This is indeed not an ideal behaviour. There seems no way to disable automatic updating of the library. It keeps deleting files even if the checkbox "watch my library for new files" is not checked.

In fact, I do not use Rythmbox myself (mostly for lack of gapless mp3 support). I use mpd ("music player daemon) with Sonata, which only updates the library "on command". It can therefore be started even when the mount is not ready without issues, but obviously will just silently skip the files if you attempt to play them while they are not there.

---

### Post by crazybilly on 2008-10-13
I'll give Exhaile a go, see if it does any better. 

I like the daap idea, though--that might be the most likely solution. Sound like it's designed for what I want to do.

---

### Post by happyisland on 2008-11-14
I'm curious to know how exaile worked for you. I just installed a readynas duo in my house to use as a streaming media server. I normally use amarok, but it doesn't seem that easy to get it working right with a network library.

---

### Post by quazi on 2008-11-14
> **crazybilly said:**
> I've been poking around, looking for a music player I can really latch on to (I was crazy for Foobar2000 in my windows days).  But right now, my music library is primarily on my home server, but most often, I want to play music on my laptop.

The files are shared via samba, and I often (but not always) mount the share via sshfs when I need to get to it.

Amarok, Banshee and Rhythymbox all do ok when the music directory is mounted, but get real angry when it's not.

Is there a music client that handles remote music libraries well?

I recommend foobar2000.  It works great in wine and, despite my attempts to use a native linux player, none of them fully matched the capabilities of foobar2000.  While it's admittedly not quite the same, I have all my music located on an external HD, but foobar has no problems when the drive is mounted (other than its obvious inability to play files that it cannot access).

Tips to get foobar2000 working can be found [here]("http://www.hydrogenaudio.org/forums/index.php?showtopic=54933") and [here]("http://ubuntuforums.org/showthread.php?t=690301").

---

### Post by itix on 2008-11-16
> **happyisland said:**
> I'm curious to know how exaile worked for you. I just installed a readynas duo in my house to use as a streaming media server. I normally use amarok, but it doesn't seem that easy to get it working right with a network library.

Unfortunately, Exaile isn't done with their UPnP stream playing support. They are for the moment trying to get version 0.3.0 to a sharp version and not an Alpha, but it is nowhere near finished. The developers have at least in their [Forum]("http://www.exaile.org/forum/index.php") promised UPnP support for 0.3.0. Current stable version is 0.2.14.

You can mount your streaming device with djmount, allowing you to use ANY player, but I wouldn't recommend it since it isn't exactly bug free.

I have a guide for djmount at the howto section if you, despite my warning, would be interested.

---

### Post by crazybilly on 2008-11-16
To be honest, with Intrepid rolling out and with the craziness at work, I haven't given this problem a lot of thought in the last little while.  

I still like the DAAP idea. but do love my foobar2000....

---

### Post by Rob Loach on 2010-10-20
Totem does UPnP through the Coherence plugin:
[http://coherence.beebits.net/wiki/Totem](http://coherence.beebits.net/wiki/Totem)

All other attempts get get DAAP/UpNP working in any other media player on Linux have failed miserably. You'd think this is something that should work out of the box, but no :( .

---

### Post by bobwyajnr on 2010-10-20
> **crazybilly said:**
> 
Amarok, Banshee and Rhythymbox all do ok when the music directory is mounted, but get real angry when it's not.

Is there a music client that handles remote music libraries well?

XBMC has a good array of networking tools (including SMB) builtin. Obviously it's a meant to be used on a frontend, media-streaming HTPC! But the tools actually work (extremely well)!

I was impressed with the general UI as well. Even does BluRay playback with a bit of hacking... :popcorn:

Bob

---

