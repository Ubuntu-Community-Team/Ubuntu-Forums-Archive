---
title: "audacious not working"
date: 2008-11-05
forum: Multimedia Software
---

### Post by JvdS45 on 2008-11-05
g(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
id3_file_vfsopen: file failed
id3_file_vfsopen: file failed
id3_file_vfsopen: file failed

when starting internetradio I get these outcome
and wehn starting a normal file this

g(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded but stil the file is not working very strange :|

---

### Post by quonsar on 2008-11-05
there is a proposed upgrade in the intrepid-proposed repository which solved my problems with audacious. go to system | administration | software sources | updates and check the box marked intrepid-proposed to get it. or just wait a few days! :-)

---

