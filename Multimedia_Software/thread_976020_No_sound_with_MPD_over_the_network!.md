---
title: "No sound with MPD over the network!"
date: 2008-11-08
forum: Multimedia Software
---

### Post by L14UX_1NS1D3 on 2008-11-08
Hello. Recently I have been trying to network my 60GB music library around the house.I tried get a upnp network setup with mediatomb and djmount. For me something always goes wrong, so was the case with getting djmount to work *sigh. Anyway I learned about the Music Playing Daemon and gave it a whirl. I edited the mpd.conf file with minimal effort and installed sonata, gmpc and areo to test the the music daemon. I setup MPD to serve up the music at 192.168.1.3:6333. I also uncommented the alsa section of the mpd.conf. I successfully played the music with on the local machine with gmpc but, here's the problem. When I tried playing the the music over my network there was no sound what so ever coming through even though I was able to connect and play the file! I had the same problem on the local machine I tested the setup on, but after uncommenting the alsa audio output section it worked just fine. I have no I clue as to what might be the problem. As always any ideas for a solution are welcome. Thanks

---

### Post by mcduck on 2008-11-10
your problem is that MPD doesn't stream music through network, it can only be *controlled* through network.

But I think MPD *can* work together with some streaming server like Icecast to get the result you want..

---

### Post by phetre on 2008-11-10
That's true, McDuck. But if the OP can get it working with PulseAudio (which supports streaming over networks), that might be an even better solution over a LAN.

That's why I'm here, actually; I've been trying to get MPD to play nice with Pulse on Intrepid, but only the ALSA driver seems to work, and it grabs the entire soundcard. I have tried all the suggestions on the [PulseAudio "Perfect Setup" page]("http://pulseaudio.org/wiki/PerfectSetup#MPD") and the [MPD wiki]("http://mpd.wikia.com/wiki/PulseAudio"). I don't see any related bugs in [Launchpad]("https://bugs.launchpad.net/mpd") -- does anyone else have this problem?

I hope this isn't a threadjack -- I want the same thing the OP does, and a fix for this should help both of us.

---

### Post by L14UX_1NS1D3 on 2008-11-14
I'll try setting up icecast stream. I would still prefer to have more control over the music. not just press play and listen to whatever is streaming. I'm very picky about what I listen to depending on the mood I'm in. I might be able to stream with icecast and control the song that is playing with an MPD client over the network possibly. I still wish there was a suitable UPnp client for linux. Anyway, enough rambling, Back to the drawing board... Again.

---

### Post by mplexus on 2009-01-05
just a thought, mpd can be controlled with ssh and command line mpc (stop/play/load playlists etc). And by controlling mpd you control icecast streaming.

---

