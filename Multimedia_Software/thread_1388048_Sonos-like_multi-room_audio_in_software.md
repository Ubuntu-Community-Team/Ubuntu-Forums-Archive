---
title: "Sonos-like multi-room audio in software?"
date: 2010-01-22
forum: Multimedia Software
---

### Post by myth01 on 2010-01-22
Hi all

I have just moved and I'm planning on using MythTV throughout the house for TV/recorded DVDs but was wondering about multi-room audio.

Does anyone know of a Linux (Ubuntu) based way to achieve what Sonos does?  As I will have MythTV frontends in most rooms, I don't really want to have to put a Sonos (or Squeezebox) piece of kit alongside it.  The thing I am most interested in is the sync-ed audio, ie the same track at the same time in multiple zones.

I am not too bothered if I have to go to each frontend to start the audio.

Please say if I need to elaborate.  Any help or pointers greatly appreciated.

---

### Post by matiasw on 2010-01-23
> **myth01 said:**
> 
Does anyone know of a Linux (Ubuntu) based way to achieve what Sonos does?  As I will have MythTV frontends in most rooms, I don't really want to have to put a Sonos (or Squeezebox) piece of kit alongside it.  The thing I am most interested in is the sync-ed audio, ie the same track at the same time in multiple zones.


I was looking for a way to do this as well, and found [SoftSqueeze]("http://sourceforge.net/projects/softsqueeze/"). I just installed it, but have not tried it yet.

---

### Post by myth01 on 2010-01-24
Hi matiasw

Just installed squeezeboxserver and softsqueeze.  

Softsqueeze seems to have been dropped in favour of squeezeplay (according to the server).  

I tried squeezeplay but the menu doesn't show whats highlighted (which is a pain) and it doesn't seem to find the server.  

Softsqueeze won't start at all, complaining that I have no Java installed.  I'm not completely surprised because I have had loads of problems with Java on this pc.

I did discover a Myth plugin called mythsqueezebox but it seems to be in its infancy.  Still, I'll give it a go once the frontends are running.

So far not much success!  Might have to shelve this one until the myth network is up and running.

---

### Post by matiasw on 2010-01-24
> **matiasw said:**
> I was looking for a way to do this as well, and found [SoftSqueeze]("http://sourceforge.net/projects/softsqueeze/"). I just installed it, but have not tried it yet.

Well, I installed [SqueezeBox Server](http://www.logitechsqueezebox.com/support/download-squeezebox-server.html) and [SqueezePlay using this guide](http://www.jfwhome.com/2009/11/22/compiling-squeezeplay-on-linux-ubuntu-amd64/). However, the most important feature, sync, seems desperately broken (see [this thread](http://forums.slimdevices.com/showthread.php?t=70337), for example). It does not seem to be possible to use synchronization between two 3rd party players (I tried to sync VLC and Winamp, but could not). [Seems rather hopeless](http://ask.slashdot.org/article.pl?sid=07/05/04/2036217).

If you get it to work, let me know!

---

### Post by tgalati4 on 2010-01-24
A bigger problem than just track sync is audio delay.  I'm working with some high-end, linux-based IP-audio boxes ([http://www.digigram.com/products/product_infos.php?prod_key=15350](http://www.digigram.com/products/product_infos.php?prod_key=15350)).  Even these boxes don't get true audio sync correct.  That is unless you run a separate, dedicated, cat5 network with nothing but audio-IP on it.

The issue becomes noticeable when you have two streams running in adjacent rooms and they are a few milliseconds out of sync.  You get some strange audio effects and overall a poor listening experience.

You are better off getting a RANE or ASHLY multiroom (4 or 8  ) room divider with programmable delays so that audio in the entire house sounds coherent.

The Pyko boxes that I mentioned earlier send out an RTP (real-time audio multicast) than any computer can pickup.  The RTP floods your network with audio IP packets at a specific address (say 239.255.100.100:50000).  You point your browser or vlc to that address and music plays.  Quality is OK, 128 kbps mp3 up to 320 kbps mps and up to 6 simultaneous stereo streams.

Of course, your network gets hammered and becomes slow for anyone else to use.  If you don't mind running duplicate wiring and ethernet switching, then this might work OK.

It's still cheaper to purchase one room divider amp with programmable delays and simply wire your house with speaker cable.

These new audio-IP products provide low-latency, near-real-time performance. When you have your whole house running with each computer pulling off the multicast RTP stream, you will quickly notice that they are out of sync and it will drive you insane.

Unlike wikipedia, this is an idea that looks good on paper, but is terrible in practice.

Now if you need to run high-quality audio 1000 feet, and have multiple streams to choose from (say internet radio in the horse barns), then this is a good solution.

---

### Post by markbuntu on 2010-01-24
Given the way Ethernet networks work it can be extemely difficult to stream audio across a network for synchronous playback. It is not impossible, just very  difficult. 

What you need to do is measure max possible latency of the network and then tell all the multicast recievers to start playback on a time clocked scheme that allows plenty of room for the delay. If your recievers are not running with rt priority for audio or with different buffer sizes this will not entirely fix the problem.

This is where dedicated boxes work best. They sync their clocks and play with a fixed/adjustable latency. You can do this without them but it requires some hacking.

---

### Post by tgalati4 on 2010-01-25
The pyko boxes even have clock correction factors in parts-per-million.  But even with corrected clocks, network latency varies widely.  This alone makes adjacent room sound fields incoherent.  Bass waves travel between rooms; treble waves are localized.  The mismatch will give you a headache.

---

### Post by myth01 on 2010-01-25
OK, cool, cheers guys.  Seems like this might be a no-go with the network approach.  Just out of curiosity, does gear like Sonos overcome (or as near as damn it) these problems of different delays/latency?  I assume they minimize it by using their Sonos-net wireless, and predictable hardware in each zone/location?

---

### Post by tgalati4 on 2010-01-26
Test it in a two room configuration.  The audio should be delayed by the centerpoint of the room to the subwoofer.  It's similar to surround-sound delay.  The center of the sound field starts at the subwoofer and each outer room should be delayed by 2 to 5 ms.  You should be able to walk between rooms and have a coherent sound field.

The cheapest solution is to get a 7.1 receiver and program the distances to the outer rooms.  Denons can go out to 85'.

I haven't worked with Sonos.

---

