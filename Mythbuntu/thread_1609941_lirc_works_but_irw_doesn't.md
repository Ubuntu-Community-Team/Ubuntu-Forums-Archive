---
title: "lirc works but irw doesn't"
date: 2010-10-31
forum: Mythbuntu
---

### Post by Gizmonty on 2010-10-31
I've just installed a fresh installation of Mythbuntu 10.04 on a new frontend I've built and am having some problems with lirc.

After setup the remote seems to work out of the box (Windows MCE compatible remote) and controls most functions OK in MythTV but I was hoping to do some tweaking. Unfortunately I get no output from irw to see what commands are being sent. This is the exact opposite problem to what I have had in the past (irw worked but struggled to get the commands passed to MythTV).

I'm wondering if I need to point irw to a different device but the only lirc device listed in /dev is /dev/lircd.

Any ideas?

-Edit-

FYI, the output from 'ps ax | grep lirc' is

 1330 ?        Ss     0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --device=/dev/lirc0

There is no /dev/lirc0 listed when I 'ls /dev/lirc*'. I'm confused.

---

