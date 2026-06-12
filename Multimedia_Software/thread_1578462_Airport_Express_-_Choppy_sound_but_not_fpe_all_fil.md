---
title: "Airport Express - Choppy sound but not fpe all files"
date: 2010-09-20
forum: Multimedia Software
---

### Post by Antenax on 2010-09-20
Hi Everyone,

Please find below my problem:

I would like to use my Airport Express to listen on my HiFi system the music I have on Rhythmbox . The problem is the sound is choppy and almost unlisteable for certain radios (my prefered ones) but there is no problem for other radios (sound is OK without any interruptions)

Example of radio with choppy sound on Airport Express
[http://broadcast.infomaniak.net:80/radionova-high.mp3](http://broadcast.infomaniak.net:80/radionova-high.mp3)

Example of radio without problem:
[http://wknc.sma.ncsu.edu:8000/wknchq.ogg.m3u](http://wknc.sma.ncsu.edu:8000/wknchq.ogg.m3u)

If anyone can help, I would be so happy !

Thanks !

Ant.

PS: Of course, when I listen the music on my computer (not through Airport Express) there is no problem at all

---

### Post by Antenax on 2010-09-20
Hi,

Just another thing to consider. 

I tried quite a few radios, and I get choppy sound for all radios >128kps, but for radios <128kbps like the second example (112 kbps in this case) that works perfectly.....

Any idea ?

Ant.

---

### Post by perspectoff on 2010-09-20
This is a tough one.

I think the problem is in the Avahi server, to be honest. 

In the past, I have tried shaping my network traffic (which my Linksys router allows) to give Avahi traffic high priority, in order to make sure that it wasn't merely a network traffic problem (since double streaming is required -- once from the Internet to the computer and once from the computer to the Airport Express).

I only can get the Airport Express to work properly with the newest version of Pulse Audio (Karmic or later), but sometimes (not always) something happens after about 30-60 minutes of play and mine, too, becomes choppy. It is as if some buffer somewhere becomes full or the network traffic suddenly becomes more bombarded.

But this is happening on my Windows-based AEX streamers, too (I use Airfoil for that), so I suspect the problem isn't intrinsic to the Linux OS.

Of course, the problem is worse when other streaming occurs (I stream Netflix and Hulu in addition to Internet Radio).

I tried using lighter, more efficient radio players (like Audacious) instead of Rhythmbox or Amarok, and they help, but not much.

Now, to be honest, the ports (such as 5353 and 6000) used by Avahi are shared by several Windows background processes on the LAN, and my real suspicion is that Windows blasts traffic over those ports (for device recognition on the LAN, mDNS, or something), and that is the root of the problem. The port-specific Avahi traffic is routinely interrupted by meddlesome Windows LAN "background" traffic.

This is the same problem I have if I ever use my IP address for a network gaming server or for torrents, where my IP address gets bombarded by traffic (that is residual from a prior use).

Of course, I only allow ports 5353 and 6000 to be open on my LAN, not to be open to the Internet, and that is why I don't suspect Internet traffic as the culprit, but suspect LAN traffic (from Windows computers). This seems borne out by graphical real-time network scans by Etherape.

A way to test this hypothesis would be to change the ports the Avahi server communicates with so that they are not the same ports used by the windows background network processes, but I haven't delved into how to do this both on the Airport Express as well as the Avahi server.

I have tried shutting off a lot of the Windows background services, and this indeed seems to clear up the problem, but since my kids use Windows computers to run LAN-based games, they squawk every time I do this.

---

### Post by Antenax on 2010-09-20
Thanks for your swift reply.

Strange things happen sometime.. Now it works .. In fact I just added some songs to Rythmbox, and after trying to stream those to Airport Express, that it works properly on this player, but still not on other players like realpayer (choppy sound)..

I still don't understand why...

Ant.

---

### Post by Antenax on 2010-09-20
And still don't work properly with youtube or any website broadcasting music...

---

### Post by Takkat on 2010-09-20
> **perspectoff said:**
> This is a tough one.

I think the problem is in the Avahi server, to be honest. 
...

I tried using lighter, more efficient radio players (like Audacious) instead of Rhythmbox or Amarok, and they help, but not much.


That's exactly my observation too. Avahi seems to bring in some unstablety when streaming to an AEX. This may be overcome by some players and not by others. At the moment I'm quite happy with Guayadeque but this may not be so in your setting. You'll need some testing.

One solution to overcome Avahi issues is to stream directly to the IP of your AEX. You're welcome to test my python program  [stream2ip]("https://launchpad.net/stream2ip") that does this for you.

Tak

---

### Post by Antenax on 2010-09-21
Hi Tak,
 
I already use your program stream2ip which is really brilliant ! I can only recommend people to try it.
 
The only thing is that although Rhythmbox now works like a charm when streaming to AEX, streaming from firefox (like youtube or radios) procudes only choppy sound. I tried as well several other players and I have same choppy sound.
 
Any thought that can help ?
 
Ant.

---

### Post by Takkat on 2010-09-21
> **Antenax said:**
> 

streaming from firefox (like youtube or radios) procudes only choppy sound.

I don't use firefox any more so I'm not of much help on this matter, I'm afraid. To give you ideas: maybe it's got something to do with buffer setting from your firefox player plugin? In addition, your observation that streams above 128k are affected only indicates some bandwith issue with your inet connection.

Tak

---

### Post by hoogland on 2010-11-26
No solutions from me yet. I can only add to the number of people experiencing this problem. Default radiostations in Rhythmbox play fine, but as soon as I play from a flash-based internet station in a browser (chrome in my case) there is a few seconds with sound that gets quickly cut off by a few second pause.

---

