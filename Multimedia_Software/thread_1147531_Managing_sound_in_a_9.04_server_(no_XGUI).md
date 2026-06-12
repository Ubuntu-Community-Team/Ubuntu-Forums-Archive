---
title: "Managing sound in a 9.04 server (no X/GUI)"
date: 2009-05-03
forum: Multimedia Software
---

### Post by wb0gaz on 2009-05-03
I am reconstructing a server (used for some audio processing) that was on Ubuntu 7.10. Audio output is silent.

I have not yet been able to use audio in Ubuntu 9.04 server; several command line scripts working under Alsa in Ubuntu 7.10 are now broken (no sound.)

I have installed pulse audio in the command line using:

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

There are two problems with this:

1. My server should not have a GUI at all (I had to install Xorg and stuff to run paman, but I don't want this in my server configurations as it is a "headless" server). Alsa is/was convenient as it could be manipulated at command line.

2. There is no test utility in the pulse audio tools above to send/receive a sample sound, so I am not sure how to proceed with troubleshooting.

I am stuck and would appreciate assistance,

---

