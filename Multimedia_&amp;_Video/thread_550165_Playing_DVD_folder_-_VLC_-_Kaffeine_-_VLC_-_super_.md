---
title: "Playing DVD folder - VLC - Kaffeine - VLC - super user - problems"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by tedrogers on 2007-09-13
Hi,

Using an IBM T22 and Feisty and trying to play a DVD folder on HD.

Sure I can get VLC to open the folder fine, but VLC has a bug on my system and the sound drops out every couple of minutes (very annoying).

Totem won't open the whole DVD (from HD), but I can view individual files.

Kaffeine (Kubuntu app) seems the ideal solution as it can handle whole folders like VLC, but it won't run unless I give it super user privelages, i.e. I have to sudo in the terminal to get it to run and it spews out loads of errors like this:

```
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
0
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
me@t22-feisty:~$ kaffeine: WARNING: KXineWidget: No config file found, will create one...

```

Kaffeine actually works fine, but I'd rather not run under super user mode.

Anybody know how to solve this or will Kaffeine just not work under Ubuntu?

Thanks in advance.

---

