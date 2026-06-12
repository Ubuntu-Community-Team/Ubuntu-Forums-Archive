---
title: "Pulseaudio PCM output device in /dev ?"
date: 2011-02-10
forum: Multimedia Software
---

### Post by id. on 2011-02-10
Hello,

I've got an old embedded linux device (Ångstrom on an iPaq) and have managed to get audio streaming from a more powerful Ubuntu 10 computer over the network onto the device, basically by piping /dev/dsp over a network socket. It's a quick and dirty solution, and it works.

However, rather than just transmit the more powerful system's microphone, my goal is to broadcast all of the system sounds from the more powerful computer to the iPaq, thus creating a cheap and cheerful audio slingbox for my home.

My question therefore is how can I get a PCM device file similar to /dev/dsp, but which outputs from the PulseAudio system mixer. A number of posts I've read elsewhere say to use a "mixer monitor" device, but I don't seem to have such a thing configured on my system, and can't see any relevant files in /dev.

The iPaq is very limited so doesn't have PulseAudio, so I can't simply fling a PA stream over the network. Also, I don't really want to stream the output of individual applications to another application on the iPaq, for example using a VLC server and client; this is not the solution I'm after; I'd rather send the whole merged sound system over the network.

Cheers dudes.
Id

---

