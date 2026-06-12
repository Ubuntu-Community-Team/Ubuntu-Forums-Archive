---
title: "Xine very slow starting up"
date: 2008-11-22
forum: Multimedia Software
---

### Post by AndrewWalker on 2008-11-22
I'm running MythTV on Kubuntu and want to use the xine player to play DVDs  and whilst it works perfectly, it takes ages to start up.
I've tried running it through a shell and I don't get any errors at all, the playback window appears immediately and then there's a good 15 second delay until something actually happens. I've run it in verbose mode and the main delay is due to the pulseaudio plugin. 
Here's the output

main: probing <pulseaudio> audio output plugin                                                                                                
load_plugins: failed to load audio output plugin <pulseaudio>

How do I get rid of the delay? Do I need pulseaudio? I assume it's a replacement for alsa but does it work with MythTV? I have the same problem with another Kubuntu machine and wondered if I need to install a package to fix the problem.

---

