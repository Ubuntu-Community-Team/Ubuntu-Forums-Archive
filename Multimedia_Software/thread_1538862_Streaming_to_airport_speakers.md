---
title: "Streaming to airport speakers"
date: 2010-07-25
forum: Multimedia Software
---

### Post by creepa1982 on 2010-07-25
Hey guys,

I am trying to stream music from an Ubuntu machine using pulseaudio to an apple running airfoil speakers. 
I followed the guide: [http://www.1ph0ne.com/2009/10/16/how-to-setup-ubuntu-to-works-with-airport-express](http://www.1ph0ne.com/2009/10/16/how-to-setup-ubuntu-to-works-with-airport-express) but I cannot see the apple computer as sink. On windows 7 with an airfoil client I have no trouble finding and streaming to the apple computer. 

Both computers are connected to a linksys router through cable. No problem getting ping from the apple computer. 

When I try to manually add the sink I get, connection refused. 

pactl load-module module-raop --server <IP>
Connection failure: Connection refused

Does anybody have an idea what I might be missing? 

Benjamin

---

### Post by creepa1982 on 2010-07-27
Nobody got an idea?

---

### Post by cchhrriiss121212 on 2010-07-28
Did you see this comment on the article you linked to?
> It didn&#8217;t work for me with the AEX in client mode until a post on the ubuntu forum suggested
~$ pactl load-module module-raop-discover
If you did, it may be a permissions issue.

---

### Post by creepa1982 on 2010-07-28
Thanks for your reply! 

I get the following error:

pactl load-module module-raop-discover 
Failure: Module initalization failed

Unfortunately I don't really know how to trace down the problem. What kind of permission issue are you thinking of?

---

### Post by cchhrriiss121212 on 2010-07-29
Perhaps you need to add yourself to the audio group, which you can do from system>users & groups.

---

### Post by creepa1982 on 2010-07-29
Indeed I was not part of the audio group(s). I added myself to every group that seemed related to audio but with no luck. 

Any other suggestions?

---

### Post by creepa1982 on 2010-07-31
Small update: 

When I enable "Enable access to local sound services", my sound devices popup as sink and source. 

So in general my pulseaudio seems to be set up fine. But there is something about the Mac server that seems to create trouble. 

I keep working on it, any input is appreciated.

---

### Post by creepa1982 on 2010-07-31
I further used avahi-discover to see the devices in the network and I can indeed find the airfoil speaker: 

Service Type: _airfoilspeaker._tcp
Service Name: 0023DF8D767C@minime
Domain Name: local
Interface: eth0 IPv4
Address: minime.local/192.168.0.197:5000
TXT ch = 2
TXT pw = false
TXT ss = 16
TXT sr = 44100
TXT tp = UDP
TXT rast = afs
TXT ramach = Macmini3,1
TXT txtvers = 1
TXT raAudioFormats = ALAC,L16
TXT rastx = iafs


Still no automatic discovery in pulseaudio. Any ideas how I can go from here?

---

