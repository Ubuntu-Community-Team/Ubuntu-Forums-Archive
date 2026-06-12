---
title: "VLC - When playing a simple AVI becomes a frustrating mess."
date: 2012-06-10
forum: Multimedia Software
---

### Post by Roasted on 2012-06-10
Ubuntu 12.04 64 bit, VLC 2.0.1.

I run Motion (Linux motion detection software) and I have the target directory for where Motion saves its feeds shared out via Samba. That way I can hit the share from any system on the LAN and view the feeds back. They save in AVI format.

After some frustration with the same issue on my laptop, I managed to get it working with some help from the VLC IRC channel. It seemed as if multithreading was causing an issue, along with subtitles. Yeah, subtitles. I have no idea why subtitles would cause an AVI file to hang up and the program to not respond, but it did. Once done, VLC plays the feeds fine on my laptop, which is also Ubuntu 12.04 and VLC 2.0.1.

So then we come down to my desktop. Since I already went through the headache infatuated steps from before with VLC on the laptop, I was quick to fire up preferences, disable subtitles, and adjust the threads to 1 as per my laptop settings.

To my surprise, VLC failed to work here. To remove the network out of the picture, I copied one of the AVI's locally to my desktop and played it. It failed, showing only a solid image. A few Google searches revealed I had to bump up the file caching spec, so I made the jump from 300 to 1500. The file now plays, but playing over LAN is still an issue as it won't play whatsoever.

So basically, I have VLC 100% working on my laptop (12.04 + 2.0.1) yet it fails to play over the LAN on my desktop (12.04 + 2.0.1) however it works when the files play locally after more fine tuning adjustments. The settings between my laptop and desktop are identical.

This experience has proven to me why it's a good idea to keep Totem as the default player. It's simple, reliable, and does the basics without an issue, including playing videos over the LAN. VLC, I love you, but holy wow this is beyond frustrating.

Anybody have anything to add? I'd REALLY like to get VLC working beautifully again, despite my rage comments above.

EDIT - Thanks to further IRC help, it seems to be (semi) resolved. Buried in the logs revealed a permission denied issue in regard to the samba share itself. Mounting the share via terminal with my username and password as part of the command revealed that VLC could play the videos just fine. As a result, VLC itself wasn't necessarily at fault, however there's clearly something different in the way Totem interprets the connection through .gvfs, as it's able to play the files just fine.

While I'm not entirely enthusiastic about the answer, at least things make more sense now. I still have no idea why my laptop works using the. same. exact. method. whereas my desktop does not, but eh...

EDIT II - Seems as if my laptop is successfully putting mounted Samba shares in .gvfs, whereas my desktop isn't putting anything in .gvfs. That's likely where the issue is... This might be continued by a part 2 of troubleshooting to follow...

EDIT III - Fixed via [this thread here.]("http://ubuntuforums.org/showthread.php?t=1327560&highlight=empty+gvfs")

```
umount ~/.gvfs
```
```
chmod 755 ~/.gvfs
```
```
/usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs
```

---

