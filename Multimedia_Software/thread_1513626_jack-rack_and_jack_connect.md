---
title: "jack-rack and jack_connect"
date: 2010-06-19
forum: Multimedia Software
---

### Post by grackleman on 2010-06-19
Hi
I have an audio application that will be run from a script. I'd like to use jack-rack in jack_connect but the problem is jack-rack comes up with a PID number. In jack_lsp the ports are jack_rack2380 for instance. I can't use a connect script because I have to use the port name shown in jack_lsp. Next time it runs, jack-rack will have a different PID and my port name will be invalid.
Has anyone worked with jack-rack in jack_connect?
Thanks
Peter

---

### Post by grackleman on 2010-06-19
Sorry about posting a stupid question. Somehow I missed the 'jack-rack -n' option to only use the name.
Dummy Peter

---

