---
title: "Trouble Compiling Phasex 0.11.1 / ALSA related"
date: 2007-11-02
forum: Multimedia Production
---

### Post by NexusApollo on 2007-11-02
Hi,

I am trying to install Phasex-0.11.1 on Fiesty 7.4

When I try to compile it in terminal (with ./configure) I get the following error:

checking for GTK... yes
checking for ALSA... no
configure: error: need ALSA >= 0.9.x

When I look in Synaptic, I appear to have the latest alsa-core. When I run <sudo apt-get install alsa> I get:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base for regex ‘alsa’
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I downloaded the tar.gz from [http://www.sysex.net/phasex/](http://www.sysex.net/phasex/) 

If you can help i will be soooo happy!

---

### Post by morganpatrick on 2008-03-18
Same problem here, running gutsy on amd64.

---

