---
title: "pulse audio upgrades broke MPD"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by Jewfro_Macabbi on 2008-02-16
Recent updates in Hardy (pulse audio) broke all of my audio - everything but MPD is fixed now. I can't seem to figure out what adujustments to make to mpd.conf 

I'm getting this error:

unable to bind port 6600: Cannot assign requested address
maybe MPD is still running?

I've tried all the suggested pulse configurations both here, and on the MPD page:

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

any ideas?

---

### Post by adam_kimber on 2008-05-30
TBH from the error I am not sure it is Pulse Audio that is the problem. It looks more like a permissions issue. What permissions and where the problem might lie could be any number of things. MPD transmits and it then recieved by a client, and it can be used across a network. Your problem looks like it could be network related. Firsly what address in your mpd.conf is quoted? Is it localhost or an acutal IP address? Secondly are you running a firewall? I had problems with MPD and firewall in my Gutsy upgrade. Look at IP tables and Firestarter for further information.

---

