---
title: "Amarok install issue"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by sbennettgso on 2007-03-01
I'm having an issue installing amaroK.  When I install the package (either through Synaptic or using sudo apt-get),  I get the following error message:

```
dpkg: error processing /var/cache/apt/archives/python-sip4_4.4.5-2ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/sipconfig.py', which is also in package python2.4-sip-qt3
Errors were encountered while processing:
 /var/cache/apt/archives/python-sip4_4.4.5-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I then have a broken dependency show up in Synaptic, python-qt3.

Any ideas as to what's going on and what I might need to do to fix it?

Any information would be appreciated.

EDITED
I fixed this problem by removing python2.4-sip-qt3.  I was then able to install amaroK and all its dependencies.

Thanks,
Scott

---

