---
title: "Dissapointing latency with jack &amp; ffado"
date: 2017-05-08
forum: Multimedia Software
---

### Post by Axxl Force on 2017-05-08
Hello everyone,

as there is a lot of progress with Reaper and LinVst atm I made another approach to move to Linux for good. I got everything working this time but unfortunately I get way too much XRuns for productive usage. I'm a little disappointed because to be honest i expected better latency with Linux than on Windows especially with the low latency kernel. However I can configure ASIO with 64 byte buffer at 48000Hz on Windows which is very good, but with jack I'm still getting XRuns when running with 256 byte buffer. More buffer introduces too much latency.

The interesting part is that it doesn't seem to make too much difference if I'm using 256, 128 or even 64 bytes which makes me hope that the problem lies somewhere else and can be fixed. CPU usage is really low too. Any ideas what i could try? I execute jack like this:

/usr/bin/jackd -R -dfirewire -p128 -n2
Ubuntu Gnome 17.04. x64

Realtime functionality seems to work as intended after I added myself to the audio group.

thanks & best regards
Alex

---

### Post by jejeman on 2017-05-10
For firewire period 3 is recommended.

---

### Post by Axxl Force on 2017-05-10
I see... but I still get XRuns with 3 periods and e.g. 128 samples i think even with 256. 

What I don't understand is, that I can reach much lower stable latencies on Windows whereas I would expect the Linux low-latency kernel to be superior.

---

### Post by jejeman on 2017-05-11
Turn off WiFi.
Turn off CPU scaling, or set to max.
Ditch the Unity.

---

