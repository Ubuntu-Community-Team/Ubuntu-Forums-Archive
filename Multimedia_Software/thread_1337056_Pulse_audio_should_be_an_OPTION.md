---
title: "Pulse audio should be an OPTION"
date: 2009-11-25
forum: Multimedia Software
---

### Post by ggreco on 2009-11-25
Hello, after a month trying to survive with pulseaudio and having constant problems with every sound app around (from games to flash passing through video players...) I've chosen to REMOVE pulse audio and use ALSA directly where possibile.

Removing "pulseaudio" cause ubuntu to remove the meta package ubuntu-desktop, some people says it's not a problem (and I can tell so far it isn't, but it has the side effect to cause apt to think all the debug packages and some goffice libraries can be autoremoved ) .

Also I found that removing pulseaudio doesn't stop the pulseaudio deamon :)
and that alsa is configured to use pulse (you'll need to remove /etc/asound.conf and all your .asoundrc* files).

You'll need also to replace libsdl with the one with the -all suffix and remove the pulse vlc/gstreamer plugins.

The worst thing is anyway that system -> preferences -> sound stops to work if pulseaudio is not installed....

Reading an older post I found the 9.04 to be compatible, so I extracted from the 9.04 deb "gnome-volume-control" and replaced it with the 9.04 one...

I think that ubuntu developers should think about their policy about pulse audio, I can understand they want to make it the default on linux, but since it barely works with most of the apps around I think they should give the users a SIMPLE path to opt for not use it, like there is a simple path to disable "desktop effects".

---

### Post by gradinaruvasile on 2009-11-25
> **ggreco said:**
> Hello, after a month trying to survive with pulseaudio and having constant problems with every sound app around (from games to flash passing through video players...) I've chosen to REMOVE pulse audio and use ALSA directly where possibile.

Removing "pulseaudio" cause ubuntu to remove the meta package ubuntu-desktop, some people says it's not a problem (and I can tell so far it isn't, but it has the side effect to cause apt to think all the debug packages and some goffice libraries can be autoremoved ) .

Also I found that removing pulseaudio doesn't stop the pulseaudio deamon :)
and that alsa is configured to use pulse (you'll need to remove /etc/asound.conf and all your .asoundrc* files).

You'll need also to replace libsdl with the one with the -all suffix and remove the pulse vlc/gstreamer plugins.

The worst thing is anyway that system -> preferences -> sound stops to work if pulseaudio is not installed....

Reading an older post I found the 9.04 to be compatible, so I extracted from the 9.04 deb "gnome-volume-control" and replaced it with the 9.04 one...

I think that ubuntu developers should think about their policy about pulse audio, I can understand they want to make it the default on linux, but since it barely works with most of the apps around I think they should give the users a SIMPLE path to opt for not use it, like there is a simple path to disable "desktop effects".

Watch out for the asound.conf (the .asoundrc can be removed safely in most cases) file. You dont need to remove it. Edit the file with root rights (sudo), and comment out (just put # at the beginning of the line) the line that has the pulse.conf it it. Thats all you need. Of course remove every pulseaudio package. 
The other stuff mentioned here like messing with libsdl is not required and i would advise against it. Every media player (except totem) has a possibility to change the sound output to alsa.

The ubuntu-desktop package can be reinstalled afterwards. But this *may* cause some updates to reinstall pulseaudio (just a speculation though).

---

