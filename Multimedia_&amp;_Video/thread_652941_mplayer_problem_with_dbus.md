---
title: "mplayer problem with dbus"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by columbo on 2007-12-29
Hi,

Some specs to begin:
Fresh install of kubuntu gutsy (kde 3.5.8)
2 tuner cards PVR-150 (/dev/video0 and /dev/video1)

apt-get install mplayer mozilla-mplayer mplayer-doc mplayer-fonts

Here is the problem:

mplayer /dev/video0 (Works fine the first time)

I stop mplayer and if I try the same command, mplayer refuse to start:

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Seek failed

I do the following command:

myth@mythbox:/home/mythtv$ fuser /dev/video0
/dev/video0:          8347  8348myth@mythbox:/home/mythtv$ ps -ef | grep -e 834
myth      8347    /usr/bin/dbus-daemon --fork --print-pid 6 --print-address 8 --session
myth      8348    dbus-launch --autolaunch b334c5c34da5e7f1b95703004775c800 --binary-syntax --close-stderr

If I kill these 2 processes, mplayer will work because /dev/video0 will be released.

Is it a known bug? Has it a known fix?

Thanks

Daniel

---

### Post by Lasoul on 2008-02-06
Has anyone found a solution to this problem. I am also having this problem. I am using an DVB-C card in combination with mplayer. This first channel plays normally but then I have to kill the dbus processes to release the dvb-c card.

---

### Post by qwasar on 2008-03-24
Same problem. Any idea?. Thanks in advance.

---

### Post by qwasar on 2008-03-24
Seems to the dbus library holds the frontend of the device and this action not allows to other process to access to the device. I think mplayer must release the frontend device, but it seems the mplayer isn't doing this.

To try to get a workaround on this trouble, I have renamed the mplayer executable (on my distro: $> mv /usr/bin/mplayer /usr/bin/mplayer.orig) and I have created a script to ensure the frontend is released after its use. You can get the script below:

#! /bin/bash
mplayer.orig $@
fuser -k /dev/dvb/adapter0/frontend0


I hope get this trouble solved ASAP.

Regards.

---

### Post by niobos on 2008-04-14
I'm having the exact same problem... anything new on this since the previous post?

---

### Post by Markus Rechberger on 2008-05-15
It's a problem with the dbus library

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/230877](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/230877)

---

