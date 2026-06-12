---
title: "snd_ice1724 needs to be re-inserted to work."
date: 2008-07-29
forum: Multimedia Software
---

### Post by redbeardmcg on 2008-07-29
I recently did a clean install, hardy 32 bit, and after the installation audio worked properly. Starting yesterday the audio stopped working. While troubleshooting I found these steps resolved the issue (they are more than likely not the only steps and not the most efficient steps):

1 - switch to a console
2 - /etc/init.d/gdm stop
3 - /etc/init.d/alsa-utils stop
4 - rmmod -fw snd_ice1724
5 - modprobe -f snd_ice1724 (audible click through speakers)
6 - /etc/init.d/alsa-utils start
7 - /etc/init.d/gdm start

Then, drums and all, I get audio output. I DID have to kill gdm to remove and successfully re-insert the module to clarify the reason I took those steps.

Is there some sort of startup script with gdm/X that is causing this issue?

Thanks all,

-Ryan

---

