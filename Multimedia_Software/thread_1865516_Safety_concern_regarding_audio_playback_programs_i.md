---
title: "Safety concern regarding audio playback programs in ubuntu."
date: 2011-10-20
forum: Multimedia Software
---

### Post by newhere_m on 2011-10-20
I have recently switched over to ubuntu 10.04LTS and I always try to keep my system as safe as possible. Regarding audio playback programs, I have tested so far totem and rhythmbox and both of them seem to be able to connect to internet without my notice. I know this can be controlled using apparmor but it will take some time for me to be able to write profiles for them. Can anybody please inform if there is any reasonably good audio play back program which can not connect to internet (or at least without my approval). Otherwise if apparmor profiles for such programs are available, please inform me about the source of such profiles. Thanks.

---

### Post by Shazaam on 2011-10-20
Most of them have plugins for fetching cover art, idtags, lyrics and such. Try looking in the menu settings and disable any plugins you dont need.
Another way (more complicated) is to set up port blocking in ufw (ubuntu firewall/iptables) or block the ports in your broadband modem/router.

---

