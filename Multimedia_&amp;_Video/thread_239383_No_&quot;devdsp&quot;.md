---
title: "No &quot;/dev/dsp&quot;"
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by Rashid584 on 2006-08-19
When I first installed Skype, it worked fine. But I tried to use audacity and it gave me an "error initializing i/o layer" so I did some stuff, and I really can't remember what it was (back in June) and it broke Skype.

I read [this](http://audacityteam.org/wiki/index.php?title=Linux_Issues) wiki and followed this step:

```
$ rm /dev/dsp;ln -s /dev/dsp0 /dev/dsp
```

But it gave me this error:

```
rashid@rashid-desktop:~$ sudo rm /dev/dsp;ln -s /dev/dsp0 /dev/dsp
rm: cannot remove `/dev/dsp': No such file or directory
ln: creating symbolic link `/dev/dsp' to `/dev/dsp0': Permission denied

```

I looked in /dev using konqueror, and there is actually no file there called dsp :S Only thing close is "adsp".

XMMS plays sound fine, and I get sound in firefox with flash and I can get sound in ET/TCE using the fix (echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss) but Skype can't even make calls, and I don't hear anything on teamspeak and I assume no one can hear me.

I've searched on Google and the forums, but can't find anything thats the same as me. Its not a problem with other programs using the device, because it worked perfectly before.

Any help would be appreciated :)

-Rashid

---

