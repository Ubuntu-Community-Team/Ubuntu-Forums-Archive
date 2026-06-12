---
title: "Totem and You Tube"
date: 2009-09-10
forum: Multimedia Software
---

### Post by ColinG on 2009-09-10
Running 9.04. Totem will not play You Tube vids (Firefox will). Totem ays it cannot open fie as I do not have permission. Terminal output is as follows. Any ideas on how to fix this please?

Thanks

** (totem:3967): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: Error: "http://www.youtube.com/get_video?video_id=M_bvT-DGcWw&t=vjVQa1PpcFMTtptwu6Fj3Pngxtc3gW5ibpPdBrk4a_U%253D&fmt=18": Not Found
gstsouphttpsrc.c(980): gst_soup_http_src_parse_status (): /GstPlayBin:play/GstSoupHTTPSrc:source:
404 Not Found

---

### Post by ngrieb on 2009-10-16
I am in the same boat as you but running 8.10. I recently had the same thing happen to me, when it was working before. Maybe we can narrow the causes down a bit. Did you recently install or uninstall anything? I have recently installed a few updates, I think a WINE update, VLC player (which I have a slight inkling is the culprit), and uninstalled OpenOffice 3.0 for a failed attempt to install 3.1. Anything here the same?

---

### Post by vinutux on 2009-10-16
some flvs not played in totem........vlc handled most of them.....

---

### Post by garvinrick4 on 2009-10-16
Turn your flv files into mpeg4 or wma something totem has codecs for. Totem with gstreamers in (ubuntu restricted extras package) will play about anything you throw at it. Or there are about 4 or 5 seperate gstreamer codecs packages available with all the different codecs. Anyway you want. Have a nice day.

---

### Post by ngrieb on 2009-10-16
I'm having a problem with playing (or streaming) them directly from the internet , not pre-downloaded flv files. If I wanted to download them, I could just use youtube-dl or something like it.

---

