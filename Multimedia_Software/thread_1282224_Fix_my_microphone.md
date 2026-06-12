---
title: "Fix my microphone"
date: 2009-10-04
forum: Multimedia Software
---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-04
Hello! I tried raising all sorts of levels, but my micophone just doesn't work. If I raise the mic boost I get only noise and without it I get nothing.

Here is my sound card

[B]00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
[/B]
Let me know what info you need

---

### Post by lupa18 on 2009-10-14
Here the same problem.. I'm using this alsa version (see attachment)

---

### Post by alfred.garcia on 2010-02-13
Same frustration here.. I found this bug had been reported here as well: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/441247](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/441247)

Have you been any successful in solving the problem?

---

### Post by thundre on 2010-02-13
I've got one system (Intel DG31GL motherboard) where I have to change the input source before it works.  In alsamixer it seemed to default correctly to 'Mic', but changing it to something else and then changing it back fixed everything.  

I got tired of repeating the process after every reboot so I made a script:

```
#/bin/bash

amixer -c 0 set 'Input Source' 'Line'
amixer -c 0 set 'Input Source' 'Mic'

# amixer -c 0 cset name='Input Source',index=1 'Line'
# amixer -c 0 cset name='Input Source',index=1 'Mic'

```

---

### Post by cotcot on 2010-02-13
Do not know if this will help you :
I got mine working after having installed [COLOR="Blue"]linux-backports-modules-alsa-karmic-generic[/COLOR]
It is in the repos and can be installed through synaptic

---

### Post by alfred.garcia on 2010-02-13
> **cotcot said:**
> Do not know if this will help you :
I got mine working after having installed [COLOR=Blue]linux-backports-modules-alsa-karmic-generic[/COLOR]
It is in the repos and can be installed through synaptic
This works for me! Thanks a lot!

---

### Post by Julita on 2010-02-16
> **cotcot said:**
> Do not know if this will help you :
I got mine working after having installed [COLOR="Blue"]linux-backports-modules-alsa-karmic-generic[/COLOR]
It is in the repos and can be installed through synaptic

That worked for me too! Thanks a lot! Too bad the button "thanks" has been removed... That was a real frustration when after 9.04 I couldn't get my micro working in 9.10!

---

