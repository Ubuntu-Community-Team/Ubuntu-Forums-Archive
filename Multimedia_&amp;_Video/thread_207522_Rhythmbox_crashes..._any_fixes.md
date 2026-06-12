---
title: "Rhythmbox crashes... any fixes?"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by ts2000 on 2006-07-02
Rhythmbox crashes with th following.... any ideas on how to fix?


dave@MainPC:~$ rhythmbox

(rhythmbox:18026): Rhythmbox-WARNING **: Unable to start mDNS browsing

(rhythmbox:18026): Rhythmbox-WARNING **: error: Failed to register the shell: (n ull)
This probably means that you installed Rhythmbox in a different prefix than bono bo-activation; this warning is harmless, but IPC will not work.

---

### Post by Ptero-4 on 2006-07-02
you need to install the mdnsresponder package.

---

### Post by ts2000 on 2006-07-02
What repo is msdresponder package located in?

Its not showing up in Synaptic.

---

### Post by tseliot on 2006-07-02
Try installing this:
[ftp://cipherfunk.org/pub/random_cruft/rhythmbox-with-ipod-support-for-dapper/rhythmbox_0.9.5-0unofficialubuntu1_i386.deb]("ftp://cipherfunk.org/pub/random_cruft/rhythmbox-with-ipod-support-for-dapper/rhythmbox_0.9.5-0unofficialubuntu1_i386.deb")

---

### Post by ts2000 on 2006-07-03
Thanks.   Installed... but it still crashed.  I have to xkill to close the program.

---

