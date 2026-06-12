---
title: "Trying to Unclutter my audio"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by KevinCole on 2007-12-14
Hi,

I used to have sound... Now, on rare, random occasions, my speakers will give a "puff" of air, even when there doesn't appear to be any activity which would cause a sound.  It could be hardware, but I want to eliminate software as a cause if I can.  (I don't want to crawl around behind all my clutter and disconnect stuff, if I can avoid it.) Over the years I've put all sorts of crazy packages into the box.  The "ps" command shows the following running at the moment:

[list]
[*][COLOR="DarkRed"]**pulseaudio --log-target=syslog -Lmodule-esound-compat-spawnfd**[/COLOR]
[*][COLOR="DarkRed"]**artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f**[/COLOR]
[*][COLOR="DarkRed"]**esd -terminate -nobeeps -as 2 -spawnfd 17**
[/COLOR]
[/list]

(Those were the only ones that were obvious to me as sound related.)

I tried creating a new user, just in case some bogus edit to a ***[COLOR="Teal"]~/.something[/COLOR]*** file was getting in the way, but no joy.

So, does anything leap to mind? Should I be uninstalling and/or reconfiguring any of the following packages (esd, alsa, pulsaudio, arts):

[LIST]
[*]alsa-base
[*]alsa-utils
[*]gstreamer0.10-alsa
[*]libasound2
[*]libasound2-dev
[*]libasound2-doc
[*]libasound2-plugins
[*]libesd-alsa0
[*]libpt-plugins-alsa
[*]libsdl1.2debian-alsa
[*]linux-sound-base
[*]libgstreamer-plugins-pulse0.10-0
[*]libpulse-browse0
[*]libpulse-dev
[*]libpulse-mainloop-glib0
[*]libpulse0
[*]pulseaudio
[*]pulseaudio-esound-compat
[*]esound-common
[*]mpg123-esd
[*]arts
[*]artsbuilder
[*]libakode2
[*]libarts1-akode
[*]libarts1-audiofile
[*]libarts1-mpeglib
[*]libarts1-xine
[*]libarts1c2a
[*]libartsc0
[*]vlc-plugin-esd
[*]vlc-plugin-arts
[/LIST]

(Also lots of gstreamer0.10 stuff).

Thanks.

---

