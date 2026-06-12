---
title: "No OSS Sound in Intrepid"
date: 2008-11-08
forum: Multimedia Software
---

### Post by Poilar on 2008-11-08
Help!

I can't get any sound through OSS in Intrepid! I had it when I first updated, and then I tried to fix my whole pulseaudio/alsa problem (which seems to be common) and now I can't even get sound through OSS. No idea where to begin. Every sound problem post on here seems to refer to alsa or pulseaudio and not to OSS.

---

### Post by falkaholic on 2008-11-08
I been having similar problems after geting on Intrepid. Can't actully help you right now, since I'm still working on mine.

Looks like something could be wrong with the ALSA packages that come with intrepid.



EDIT: This worked for me: [http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

---

### Post by 73ckn797 on 2008-11-08
> **Poilar said:**
> Help!

I can't get any sound through OSS in Intrepid! I had it when I first updated, and then I tried to fix my whole pulseaudio/alsa problem (which seems to be common) and now I can't even get sound through OSS. No idea where to begin. Every sound problem post on here seems to refer to alsa or pulseaudio and not to OSS.

Double click on the sound icon in top bar. You can set levels there. Recommend select preferences and tick all settings options and run those levels up.

---

### Post by Poilar on 2008-11-09
The problem is not a volume problem. I've already turned the volume up all the wayy. Also, I've just uninstalled pulseaudio and reinstalled esound, and still no sound. It's something deeper.

Actually, now when I try to do play something on OSS I get a long error message about the device already being use (as opposed to just silence). When I try to play something on ALSA (now that puleaudio is uninstalled) I just get silence.

---

### Post by swalker23 on 2008-11-09
I use OSS by following this guide:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

I used it in Hardy and now intrepid but with intrepid I had a problem with system sound got help from Cessium in 4front forums and he told me to do this and it worked

install the gstreamer phonon backend and make it the preferred one in sound configuration panel go to "System Settings"->"Sound"->"Backend" and "prefer" the gstreamer backend.

---

