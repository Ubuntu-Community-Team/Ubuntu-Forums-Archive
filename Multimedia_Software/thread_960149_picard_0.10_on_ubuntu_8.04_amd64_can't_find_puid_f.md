---
title: "picard 0.10 on ubuntu 8.04 amd64 can't find puid for m4a files?"
date: 2008-10-27
forum: Multimedia Software
---

### Post by seenxu on 2008-10-27
searched on forum, maillist, google, still can't find a proper solution. so I decide to ask it here.

I compiled picard 0.10 from source, while config the source, there seems no directshow available on my system

python setup.py config

running config
checking for pkg-cfg... yes
checking for libofa... (pkg-config) yes
checking for libavcodec/libavformat... (pkg-config) yes
checking for directshow... no
saving build.cf


if the directshow support is the key that I don't have m4a file support for picard?


as for finding PUID of m4a files using picard 0.10, there is no error message popup, only a warning inside the statusbar, which has the following sentence, "Couldn't find PUID for file xxx.m4a". and I had also tried launching picard in debug mode, it prints out the following message which processing the same file.

D: 140340588644064 22:11:25 Updating file <File #2 u'xxx.m4a'>
D: 1131583824 22:11:25 'Creating fingerprint for file xxx.m4a...'
D: 1131583824 22:11:25 Decoding using 'picard.musicdns.avcodec'...
D: 140340588644064 22:11:25 "Couldn't find PUID for file xxx.m4a"
D: 140340588644064 22:11:25 Updating file <File #2 xxx.m4a'>

and I do believe musicdns do have the PUID for the files, because those are not rare tracks, and the second reason is all my m4a files won't work, so this can be a solid prove that it is something related with the problem of mp4 support on my system. 

thx in advance.

system spec.
xubuntu 8.04 amd64

---

