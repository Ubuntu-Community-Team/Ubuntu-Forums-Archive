---
title: "No Video or Audio :("
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by latin_l3oi on 2008-02-29
hello,

I'm new to ubuntu and I can't play audio or video files... :(

I can't view youtube videos or any as such. I got a message saying:

"Install Multimedia Codecs", when I click on "Install", I get the following message:

==================================================
Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
==================================================

What could I do to resolve this issue?

Regards,

latin_l3oi

---

### Post by kpkeerthi on 2008-02-29
Open a terminal and type
```
sudo aptitude install ubuntu-restricted-extras
```

You'll be all set.

---

### Post by jan quark on 2008-02-29
and make sure your software sources are enabled

go to

system > administration > software sources

and enable everything except source code and cd

then run 

```
sudo apt-get update
``` in terminal
you should not have any problems with downloading the codecs

---

### Post by latin_l3oi on 2008-02-29
Thank you kpkeerthi and jan quark :)

I've got Audio and Video now! :D

Cheers, ;)

latin_l3oi

---

