---
title: "MP3 and DVD playback without restricted extras?"
date: 2011-10-06
forum: Multimedia Software
---

### Post by garyjmellor on 2011-10-06
Hi,

Does anyone know if it is possible to get MP3 and DVD playback features individually? I don't want to run ubuntu restricted extras for the simple reason this will also install Flash, which I specifically want to avoid due to the supercookie issue. I'll be using Gnash instead. I guess what I'm after are the package(s) necessary for MP3 and DVD playback and nothing else that comes with restricted extras.

Thanks in advance.

---

### Post by dniMretsaM on 2011-10-06
You can easily do this. ubuntu-restricted-extras is simply a metapackage that points to all the necessary packages (Flash, unrar, GStreamer plug-ins, etc.). Thus, you can simply install all the packages that you want without installing Flash. Run the following in terminal to install everything except [FONT=Courier New]adobe-flashplugin[/FONT] and [FONT=Courier New]flashplugin-installer[/FONT]
```
sudo apt-get update
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse ttf-mscorefonts-installer unrar gstreamer0.10-plugins-bad-multiverse libavcodec-extra-52 libmp4v2-0 gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-pitfdll icedtea6-plugin gstreamer0.10-fluendo-mp3
```

---

### Post by wolfen69 on 2011-10-06
> **garyjmellor said:**
> I'll be using Gnash instead.

Good luck with that, as it's basically useless. And the "supercookie" issue you mentioned is old, and Adobe has taken care of it with the last few releases.

---

### Post by beew on 2011-10-06
You can install restricted-extra and then uninstall flash. Does gnash actually work??

---

### Post by garyjmellor on 2011-10-07
Thanks for all the replies. The supercookie issue still persists on my machine as at 11.04 using the latest ubuntu-restricted-extras. Anyways, I have the answer I require. Thanks all. Oh, Gnash does work but it's clunky ;o)

---

### Post by dniMretsaM on 2011-10-07
Mark as solved please.

---

