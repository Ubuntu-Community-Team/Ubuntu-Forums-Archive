---
title: "best way to test jack for low latency??"
date: 2006-01-05
forum: Multimedia &amp; Video
---

### Post by stratotak on 2006-01-05
Got jack set up and have the ademudi  2.6.14 multimedia kernel and real time module built...whats the best way to test latency other then watching for Xruns on qjackctl....right now ive got jack runing and have 2 instances of Hydrogen the drum machinf running looping a drum pattern..and it hasnt had one Xrun yet...but not sure if thats a good stress test or not....i will get a Xrun or 2 if i launcg a Vst plugin via WINe..but vst plugin will play fine..no drop outs in sound..even though qjackctl show like maybe a 1/2 Xrun reading...im thinking that launching the VST plugin through wine causes the Xrun but once its made the jack connection its fine..but just basically want a real world test of jacks latecy other then the Xrun readout and qjackctl setup showing 42 as latency..which seems a bit high..i could get like around 12 with this same set up under windows 2000 running the asio4all driver....using this laptops built in intel sound chip,,,sigmatel c-major..

---

