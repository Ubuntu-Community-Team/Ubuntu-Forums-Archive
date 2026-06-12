---
title: "How to: &quot;Alsamixer&quot;?"
date: 2008-07-19
forum: Multimedia Software
---

### Post by illnin0 on 2008-07-19
I'm having trouble installing Alsamixer. I've tried "sudo apt-get install alsamixer" but I get a "couldn't find package" msg.

Can someone point me to a 101 on Alsamixer or tell me a different way to install it?

---

### Post by Lord DarkPat on 2008-07-19
I think it would be better if you used a GUI frontend like aumix or gnome-alsamixer or kmix

---

### Post by lswb on 2008-07-19
alsamixer is in the alsa-utils package. There is also alsamixergui for a general purpose gui interface and gnome-alsamixer for the gnome desktop.

Like LD, I also recommend synaptic for searching for packages when you don't know the exact name. It's easy to enter for instance "alsa" in the search box and then get a list of all packages that have "alsa" in the name or, if you specify, in the description as well. Then you can just mark the ones you want for installation at the same time.

---

### Post by markbuntu on 2008-07-19
The package you want to get alsa mixer is

alsa-utils (command line utilities)

It should have been there from the initial installation.

Other alsa packages you probably should have:

alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

---

