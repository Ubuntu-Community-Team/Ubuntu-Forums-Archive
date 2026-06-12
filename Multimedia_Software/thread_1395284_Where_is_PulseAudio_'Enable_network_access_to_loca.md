---
title: "Where is PulseAudio 'Enable network access to local sound devices' on Ubuntu Server?"
date: 2010-01-31
forum: Multimedia Software
---

### Post by nimrodwebdesign on 2010-01-31
I have hunted high and low for information on how to enable my server's sound-card as a network accessible device through PulseAudio (which is running Ubuntu Server 9.04), but with no success.

Doing this on a Desktop (running Ubuntu 9.10) is a breeze, I just check the box 'Enable network access to local sound devices' in the PulseAudio Preferences, and it magically works. I just can't work out how to accomplish the same thing in the server config files.


I have tried the only thing I can find that seems relevant, which is to uncomment the following lines in [FONT="Courier New"]/etc/pulse/default.pa[/FONT], but it hasn't helped.

```

load-module module-esound-protocol-tcp auth-ip-acl=127.0.0.1;192.168.1.0/24
load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1;192.168.1.0/24
load-module module-zeroconf-publish
```


If anyone can shed any light on this, I'd be very grateful.


Cheers in advance,
Colin :KS

---

