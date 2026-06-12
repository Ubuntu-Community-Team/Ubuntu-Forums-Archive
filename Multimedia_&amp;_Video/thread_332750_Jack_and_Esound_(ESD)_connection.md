---
title: "Jack and Esound (ESD) connection?"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by Mickeysofine1972 on 2007-01-06
Hi

Is it possible to link Jackctl to ESD for audio mixing? 

I want to use ESD as its the only sound server that works on my system when i'm playing SecondLife. I already have jack setup to use ALSA but this doesnt work when i run SL as well.

Any ideas or suggestions would me greatly appreciated!

Mike

---

### Post by carlosfocker on 2007-01-06
Is there any reason you are using Jack or ESD? If you want software audio mixing try using asym. 

[http://alsa.opensrc.org/Asym](http://alsa.opensrc.org/Asym)

---

### Post by Mickeysofine1972 on 2007-01-13
my problems is this:

I need to have a jack audio system to send sound to oddcast so that it can relay to my shoutcast server.

The only problem is that i want to run Secondlife as well and that will only let me play multiple sounds with esd but not oss or alsa!

any idea how i can pull this off?

Mike

---

### Post by Mickeysofine1972 on 2007-01-14
bump

---

### Post by carlosfocker on 2007-01-14
ESD is a soundserver for oss so you are using oss and I have gotten SL working with alsa using asym.  Correct me if I'm wrong but JACK is an session manager that use alsa.  So you should be able to set asym up , disable ESD and software mixing should work fine.

---

