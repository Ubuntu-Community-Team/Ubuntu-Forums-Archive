---
title: "MythNetvision missing bbciplayer.py?"
date: 2010-10-10
forum: Multimedia Software
---

### Post by allywilson on 2010-10-10
Hi all,
       After just building my first HTPC, I wanted to watch BBC iPlayer on it. 

I apt-get installed mythnetvision - but the bbciplayer.py script was missing. Not a problem thinks I, I'll just download it. So, I got the script from [http://cuymedia.net/mythtv-trunk/bbciplayer_8py-source.html](http://cuymedia.net/mythtv-trunk/bbciplayer_8py-source.html) I put it in the correct directory (/usr/share/mythtv/mythnetvision/scripts). If I run it in the shell I get: > The subdirectory "nv_python_libs/common" containing the modules common_api.py and
common_exceptions.py (v0.1.3 or greater),
They should have been included with the distribution of MythNetvision
Error(No module named common.common_api)

I can't find a copy of common_api.py or common_exceptions.py anywhere online (my google-fu isn't strong enough it seems).

I checked the ubuntu package contents and it shows that bbciplayer and those 2 python scripts aren't in it 

[IMG]http://imgur.com/i91Rb.png[/IMG]

seen here: [http://packages.ubuntu.com/en/lucid/i386/mythnetvision/filelist](http://packages.ubuntu.com/en/lucid/i386/mythnetvision/filelist)

Can anyone help?

---

