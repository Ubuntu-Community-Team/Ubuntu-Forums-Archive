---
title: "ATT wan card not working"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by xkaliburx on 2009-09-20
I recently restaged my laptop (dell xps m1330) due to a defective hard drive.  One of the last things to get working (which did work fine in 9.04) is my ATT wan card using the Hsoconnect.  I did the install a long time ago, but here is what I have so far.  The following 2 packages installed;

hsoconnect-py2.5_1.1.128_all.deb  
hsolink_1.0.118-1_i386.deb

* Note this is a 64 bit install which I dont remember what I had last time, so needed a --force on the hsolink package *

Well, when I start the app (tried as local user and sudo) issuing;
sudo python2.5 -m hsoc
The app does start, I setup the ATT login, but in the debug window I continually get the following;

Init serPort /dev/ttyHS1Could not open port: [Errno 2] No such file or directory: '/dev/ttyHS1'

Any help or ideas is appreciated, looking around I really only see one or 2 non english posts so trying to get this resolved.

Thanks

---

