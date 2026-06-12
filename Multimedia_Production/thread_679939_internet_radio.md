---
title: "internet radio"
date: 2008-01-27
forum: Multimedia Production
---

### Post by cleenux on 2008-01-27
[http://www.fcbarcelona.com/web/castellano/locucio/locucio.html](http://www.fcbarcelona.com/web/castellano/locucio/locucio.html)
when i first installed Ubuntu i went to this address to listen to a soccer game via firefox i listened to it with no problems.
after reinstalling ubuntu but this time the 7.10 version turns out that now i cant listen to it any more.

any ideas? ive tryed the flash plugins and what not.
by the way, audio should be only available when the team is playing, so in order to test this issue they have to be playing

---

### Post by Dennis on 2008-01-27
I get the english commentary if I paste the following url into VLC

[http://live1.interoutemediaservices.com/?id=db10b36c-a202-41b4-8c55-c247f7522d6a](http://live1.interoutemediaservices.com/?id=db10b36c-a202-41b4-8c55-c247f7522d6a)

Try this one for Catalan (I think it is)
[http://live1.interoutemediaservices.com/?id=bd2e8eca-7ad2-4f31-94d0-a392f6761f2a](http://live1.interoutemediaservices.com/?id=bd2e8eca-7ad2-4f31-94d0-a392f6761f2a)

---

### Post by cleenux on 2008-01-27
Thanks Dennis.
i had no luck on any of  those links.
what version of ubuntu do you have?
what firefox version?

---

### Post by Dennis on 2008-01-27
Kubuntu 7.10 and Firefox 3.0a8 (Gran Paradiso)

---

### Post by cleenux on 2008-02-03
it works, this is what i did. i followed instructions for DVD Playback in the following page: [http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback](http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback)

1. Open a terminal window.

2. Execute the following terminal command to install the necessary packages (make sure to approve any prompts):
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3


3. Execute the following terminal command:
sudo /usr/share/doc/libdvdread3/install-css.sh

this will uninstall the tottem gstreamer but your internet radio will work (i only tested it on theese address [http://www.fcbarcelona.com/web/caste...o/locucio.html](http://www.fcbarcelona.com/web/caste...o/locucio.html))

---

