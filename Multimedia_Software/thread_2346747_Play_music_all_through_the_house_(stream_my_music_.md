---
title: "Play music all through the house (stream my music to multiple receivers)"
date: 2016-12-18
forum: Multimedia Software
---

### Post by Keith_Beef on 2016-12-18
My question is a mix of audio (therefore multimedia) and network streaming (therefore networking).

Here's the project: play my music collection (a mix of formats: ogg, flac, MP3, maybe even WAV and aiff) on a NAS to a number of "receivers" around the house.
 
I had at first thought that this would be relatively simple, and that somebody would have already done something similar. Maybe on the fly transcoding where necessary to make the source file into ogg, send that over the network in broadcast or multicast UDP packets, and on each "receiver" (another computer attached to a DAC, small amp and pair of speakers) run a listener that catches the packets and sends the data into the DAC.

Icecast looked like it might be what I was looking for, until I read this:

> Can I use Icecast to stream like Spotify/Rdio/Pandora?

No. This kind of &#8220;streaming&#8221; is very different from what Icecast does. In Icecast you usually have a &#8220;station&#8221; (mountpoint) sourced by a source client like IceS and streamed by Icecast to a large amount of listeners. This implies that all listeners of that mountpoint get the same stream, so an individual listener can&#8217;t pause the stream or add different tracks without affecting all other users.

As already mentioned, Spotify and co. do not really &#8220;stream&#8221; in the classic meaning of the term. Actually what they in most cases do is provide the client with the individual songs and the client takes care of all the other things, like play/pause and playing the tracks in the desired order. It&#8217;s basically just simple file serving, which webservers like nginx or Apache do.

And then I found this very informative answer to another thread on a similar topic:

[https://ubuntuforums.org/showthread.php?t=2094447&highlight=multicast+audio+stream](https://ubuntuforums.org/showthread.php?t=2094447&highlight=multicast+audio+stream)
> 
Put cable boxes in each room and tune to the same music channel.

There is no zero-latency, IP/TCP protocol. The nature of ethernet communication is latency (although small) and graceful degradation through packet retransmission and rerouting (which adds larger latency).

There are dedicated music protocols that run over gigabit switches such as QSC's QSys network or CobraNet that can share traffic over high quality Cat6 networks, but they require expensive servers and endpoints. For a home user, there is no simple way to drive a house party in multiple rooms and synchronize the acoustic delays so that you don't get weird phasing effects.

Each computer that is decoding the music stream has a slightly different quartz clock (to maintain the 44,100 kHz sampling frequency). After a few minutes of several computers playing the same music, the clocks will drift apart and you will hear the latencies--this assumes zero network latency. Add in network latency and you have an impossible situation. You need a protocol that transmits a master clock and then synchronizes all playback based on that clock.

A better way acoustically to handle the situation is to have one primary sound system and use a 4-way line-out splitter and put some boom boxes around the house with cabling. That way you have only one sound source and you are using analog amplification after that. Keep the cable runs under 20' or you will get some acoustic delays (due to distance).

The most simple arrangement is to mix to mono and put 4 high-powered speakers in the center of the house pointed in 4 directions. That will allow the sound to travel throughout the house without acoustic delays.

A more complicated arrangement is to use a 5.1 receiver and program your receiver to put 0 seconds delay on the front of house and a few milliseconds of delay on the back speakers and put those in a distant room. You can tweak the delay such that the sound is coherent. There are delay calculators on the web.

Linux has some wonderful tools and protocols to share music libraries and stream music and play to remote machines, but it can't play multiple locations with controlled delay. What we need is a networked jackd protocol where xruns become network latency--yet another framework!

Or drop $50K and put in a real networked sound system:

[http://qscaudio.com/products/network/QSys/](http://qscaudio.com/products/network/QSys/)

(It actually runs a form of linux!) 

That was from back in 2012, and maybe things have changed since then&#8230;

A few ideas I'm investigating are:
firefly streaming server, already installed on my NAS, and clementine on the receivers
Squeezebox/softsqueeze (I have a Logitech squeezebox in one room, already, and have  Squeezebox server running on the NAS)
Shairplay
Chromecast (I have one chromecast audio plugged into an amp, and my son sometimes plays music from his Google Play Music collection)

---

### Post by cariboo on 2016-12-19
I saw an article about whole home audio systems using a [Squeezebox]("http://www.mysqueezebox.com/download") server, [clients]("http://softsqueeze.sourceforge.net/"), Raspberry Pi and inexpensive 2.1 speaker systems. Unfortunately I forgot yo bookmark it :(.

This is a DYI solution, you'll need a usb audio adaptors and wireless dongles, unless you are willing to run network cables to all the different locations.

**Edit:** I found the article [here]("http://www.instructables.com/id/Sonos-like-Wireless-Multiroom-Sound-System/")

---

