---
title: "Amarok and Wine Audio Conflict"
date: 2009-04-28
forum: Multimedia Software
---

### Post by yedidyah on 2009-04-28
When I am running Amarok Wine programs have no sound. When I run Wine Amarok has no sound.

I have wine audio configured to run oss.

---

### Post by markbuntu on 2009-04-28
OSS is not capable of sharing sound hardware so if you have wine set up to use OSS it will grab the hardware exclusively for itself and if it cannot, it will not play. With kubuntu on jaunty Amarok is using phonon as the sound server and phonon knows nothing about OSS. There is a way around this that may get them both to work together. You can read this which explains the problem in KDE4 and tells you how to get pulseaudio workng with phonon/KDE4.

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

I am not entrely sure that wine will work in jaunty with this but you should set wine to use OSS and edit the launcher to 

padsp wine

I don't use wine myself but this has worked in Hardy and Intrepid depending on which version of wine was used. The latest seems to work better.

---

### Post by yedidyah on 2009-04-29
Okay when I am ready I will post the results of my tests here. Thank you for your guidance.

---

