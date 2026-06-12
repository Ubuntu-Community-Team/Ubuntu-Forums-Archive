---
title: "Trunk - 15283 :: MythVideo &amp; MythStream"
date: 2008-01-03
forum: Mythbuntu
---

### Post by modorf on 2008-01-03
Hi,

I upgraded my mythbuntu box from fixes to trunk last week.  It works better but there are some issues with the most recent build.

MythVideo Trunk 15283 amd64 won't upgrade.
Also the build for MythStream 0.18.1-0ubuntu1~gutsy1 amd64 is built against an older version of libmyth-20, so I can't modify the settings.

Error while running apt-get upgrade -V:
```

Preparing to replace mythvideo 0.20.99+trunk15221-0ubuntu0~mythbuntu1 (using .../mythvideo_0.20.99+trunk15283-0ubuntu0~mythbuntu1_amd64.deb) ...
Unpacking replacement mythvideo ...
dpkg: error processing /var/cache/apt/archives/mythvideo_0.20.99+trunk15283-0ubuntu0~mythbuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/mv-sel.png', which is also in package mythtv-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mythvideo_0.20.99+trunk15283-0ubuntu0~mythbuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thank you.

---

### Post by slighted on 2008-01-03
I stumbled across the same issues... as far as MythVideo goes, try this:
```
sudo dpkg -i --force overwrite /var/cache/apt/archives/mythvideo_0.20.99+trunk15283-0ubuntu0~mythbuntu1_amd64.deb
```
...assuming apt is configured as per default, and you are running 64bit. If you are running 32bit you will need to provide the correct deb.
```
sudo dpkg -i --force overwrite /var/cache/apt/archives/mythvideo_0.20.99+trunk14583-0ubuntu0~mythbuntu2_i386.deb
```
MythStream on the other hand had to be compiled from source, and is still kicking up some issues... segmentation faults on exit causing the frontend to crash.

Hope this helps,
Ted

---

### Post by laga on 2008-01-03
Thanks for your report,

we'll be kicking off fixed builds in a few hours.

---

### Post by modorf on 2008-01-06
laga,

Thank you for the fixed build of MythVideo.
Can you explain why MythStream isn't being included in the trunk builds.

---

