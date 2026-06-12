---
title: "Issues with Pulseaudio and /home on SMB-Share"
date: 2010-02-17
forum: Multimedia Software
---

### Post by blackkite on 2010-02-17
Hi,

is there any way to tell pulseaudio, where to put all this stuff when it starts up? We have a restricted environment, no symlinks are allowed out of Samba-Share. Since /home is shared via Samba, pulse is not allowed to create its symlink to tmp. Running "pulseaudio" in a console throws this error:

```
E: core-util.c: Failed to symlink /home/.../.pulse/cea01c4b404b46d20c6cf3424aa7b635-runtime to /tmp/pulse-Qt6iKhn9Brs1: Permission denied
```Can I tell pulseaudio to create this stuff directly in /home, so that no symlinks will be needed?


Regards,
blackkite

---

### Post by blackkite on 2010-02-17
I joined the german Ubuntu-channel on freenode. The result was, that using Samba is not well suited for mounting /home on Ubuntu. NFSv4 was suggested, but that will involve some testing, since I am trying to mount shares from a live-system, which cannot be modified on a daily (and testing) basis. If anyone would have a quick work-around, that would be really really useful. NFSv3 is not an option, since user-authentication is a must.

---

