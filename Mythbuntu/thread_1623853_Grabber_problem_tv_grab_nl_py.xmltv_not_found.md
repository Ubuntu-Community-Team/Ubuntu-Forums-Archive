---
title: "Grabber problem: tv_grab_nl_py.xmltv not found"
date: 2010-11-17
forum: Mythbuntu
---

### Post by qrazi on 2010-11-17
I recently made a fresh install of Ubuntu 10.10 and installed mythtv and mythbuntu control centre. I use tv_grab_nl_py for EPG ([http://code.google.com/p/tvgrabnlpy/](http://code.google.com/p/tvgrabnlpy/)), and I normally have no trouble installing it using the installation instructions on the website. However, I cannot get it running now. I keep on getting an error: Config file .xmltv/tv_grabnl_py.xmltv not found. Which is correct since tv_grab_nl_py creates .xmltv/tv_grab_nl_py.conf. Renaming doesn't solve the problem, pressing configure in the mythtv-setup doesn't help either.

Are there any pointers? Changes I have missed since the last release I used (ubuntu 9.04 and mythtv 0.22)?

---

### Post by qrazi on 2010-11-18
I reinstalled Ubuntu, and step by step started to install MythTV again. After using Mythbuntu Control Centre to change the role to primary backend and desktop frontend. After that I went to setup the grabber again, and this time I chose only the configure option in mythtv-setup, and not for the grabber directly on the commandline. This resulted in a tv_grab_nl_py.xmltv in /home/[user]/.mythtv/ which I edited to fit my channel preferences.

Mythfilldatabase worked without problems after this...

---

