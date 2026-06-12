---
title: "rt vs lowlatency kernel"
date: 2011-05-18
forum: Multimedia Software
---

### Post by deadalus.globalnode on 2011-05-18
Greetings,
I am using Xubuntu 11.04. I spend a majority of my time using Blender 2.57, gimp, and other similar programs (actually blender and gimp are all I can think of in graphics at the moment ;) ). I am roughly following the slacker-media guide at [http://www.slackermedia.info/](http://www.slackermedia.info/) to setup a Xubuntu work station. 

I came across a part about a real time kernel, which peaked my interest quite a bit. I have compiled my own kernel many times (Gentoo rocks) so I am not afraid to do that. While doing some research I noticed that the RT Kernels are no longer supported, and that a newer thing called low latency kernels are being implemented. 

So my question is, should I get a low latency kernel over a rt-kern? If so, how do I set certain applications to have "real time" or the lowest latency possible? With the rt-kernel it seemed you used an additional program to give the program of your choice (for example Blender) "real time" priority. Does it work the same way with a low latency kernel?[URL="http://www.slackermedia.info/"]
[/URL]

---

### Post by gsmanners on 2011-05-18
The realtime kernels are deprecated, so you should go with low latency.

see: [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)

EDIT: Or maybe not.

> -rt kernel - is based on the Ubuntu kernel source tree with Ingo Molnar maintained PREEMPT_RT patch applied to it. Also know as a hard real-time kernel.

-lowlatency kernel - very similar to the -preempt kernel and based on the -generic kernel source tree, but uses a more aggressive configuration to further reduce latency. Also know as a soft real-time kernel.

-realtime kernel - is based on the vanilla kernel source tree with Ingo Molnar maintained PREEMPT_RT patch applied to it. Also know as a hard real-time kernel.

from [https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)
see: [http://en.wikipedia.org/wiki/Real-time_computing](http://en.wikipedia.org/wiki/Real-time_computing)

---

