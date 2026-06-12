---
title: "Movie Player"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Howie Williams on 2009-05-01
Updated to Jaunty from Intrepid and ever since when I try to play audio or vids in either mplayer or Movie player the apps start then window closes on its own. Vlc does the job but not as well as it use to, it opens vids up in seperate minimized window.:confused:

---

### Post by zigga15 on 2009-05-01
I have noticed this too.

If you haven't already - sudo apt-get update && sudo apt-get upgrade

I think this helps for some files. Otherwise try re-installing the media part??

I guess we just have to wait for developers to keep improving them. Or we can revert to an older version manually. Maybe try this:

```

sudo apt-get remove totem
sudo apt-get install ubuntu-restricted-extras

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

sudo apt-get install totem

```

---

