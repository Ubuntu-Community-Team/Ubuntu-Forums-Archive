---
title: "Totem Firefox plugin doesnt stream"
date: 2010-05-06
forum: Multimedia Software
---

### Post by robosteven on 2010-05-06
I installed the greasemonkey script "youtube without flash auto" to replace the youtube player with the default totem plug-in in firefox. The script is awesome because now I don't get bogged down with flash when watching youtube.

Everything works as expected, but the problem is that the plugin doesn't stream, I have to wait until the video finishes loading before I can play it. Ironically, if i don't use the plugin and directly open the video cache in /tmp with totem, it was able to play even when the video wasn't finished loading.

I am not sure if this is normal, but I find it a huge annoyance. Does anyone else running this script have the same problem? I don't know if it is the script, the plugin, or my configs in general. A push in the right direction would be greatly appreciated.

im running Xubuntu 10.04 btw

---

### Post by lovinglinux on 2010-05-06
First, I would recommend gecko-mediaplayer plugin instead of totem. See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

You need to let the minimal setup cache to download before playing. Which means when it reaches about 20% you can click play and it will play.

If you want to change the minimal cache size, open ~/.mplayer/config file and add something like this:

```
cache=8192
cache-min=10.0
cache-seek-min=30
```

The first value is in bytes while the others are percentage.

---

