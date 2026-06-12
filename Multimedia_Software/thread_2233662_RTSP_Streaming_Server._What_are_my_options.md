---
title: "RTSP Streaming Server. What are my options?"
date: 2014-07-10
forum: Multimedia Software
---

### Post by Roasted on 2014-07-10
Hello friends. I have a few IP network surveillance cameras on my LAN. They are simply doing a 24/7 record right to my file server. I do not have a DVR/NVR for a few reasons (costly, no need for any other features, just need 24/7 recording which the cameras provide right to my file server, which I quite like). The catch is, with a setup like this, I do not have any live streaming capabilities. I mean, I can pull up each individual stream via VLC, but it's been a series of dead ends when it comes to trying to pull in multiple streams on one interface. VLC has a mosaic option, but it seems quite broken and VLC developers even blatantly told me the documentation is lackluster and wildly outdated. It seems as if HTML does not support direct RTSP streams or else I would just whip up a quick surveillance.html file and call it a day.

I started to think about it more and I thought about changing things a bit. Mind you, this is just a home LAN, but let's consider the bigger picture. Let's say I, for whatever reason, had 10 clients. If 10 clients connect right now, they're pulling 10 streams from the cameras. Instead of making that a responsibility of the cameras, I want to make that a responsibility of the server. That way one stream gets pulled into the server and the server kicks it back out to whoever wants to see what's going on.

I looked into crtmpserver, which on the man page sounds great, but in actuality, the documentation seems quite poor and under heavy development. I figured I'd at least check here to see what you folks thought. Essentially I want to pull in multiple RTSP streams from my cameras and then pull those same streams, but in one window (like a 2x2 grid format, similar to what you see on regular CCTV appliances) for more of a live watch.

Is there anything else other than crtmpserver? Maybe something I'm missing? Or perhaps someone has wildly awesome crtmpserver documentation?

FYI - Server is Ubuntu Server 12.04.4.

Thanks for any/all assistance!

---

