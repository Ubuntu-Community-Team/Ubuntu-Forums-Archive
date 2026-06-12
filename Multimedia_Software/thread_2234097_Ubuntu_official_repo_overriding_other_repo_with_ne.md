---
title: "Ubuntu official repo overriding other repo with newer version"
date: 2014-07-12
forum: Multimedia Software
---

### Post by derekcentrico on 2014-07-12
I'm trying to get the latest TVHeadend installed on my home server.

I followed the instructions at [https://tvheadend.org/projects/tvheadend/wiki/AptRepository](https://tvheadend.org/projects/tvheadend/wiki/AptRepository) and installed the proper repository in sources.list.  

However, after doing apt-get update the system does not see newer builds.  I did apt-get tvheadend purge and started over.  Ubuntu repositories installed the older version of tvheadend and ignored the new one.

I'd like to get away from 3.4.xx and get to the 3.9.xx for some serious bug fixes are needed on my end.

I have had no luck with apt-get install -t.  But, I'm somewhat ignorant there.

deb [http://apt.tvheadend.org/stable](http://apt.tvheadend.org/stable) precise maindeb [http://apt.tvheadend.org/stable](http://apt.tvheadend.org/stable) precise maindeb [http://apt.tvheadend.org/stable](http://apt.tvheadend.org/stable) precise mainAny help would be great.
deb [http://apt.tvheadend.org/stable](http://apt.tvheadend.org/stable) precise maindeb [http://apt.tvheadend.org/stable](http://apt.tvheadend.org/stable) precise main

---

### Post by slooksterpsv on 2014-07-12
[https://tvheadend.org/boards/5/topics/11696](https://tvheadend.org/boards/5/topics/11696)

The stable version on trustytahr only supports 3.4.28 - here's the package output:
```

Package: tvheadend
Version: **3.4.28~geb79aee~trusty**
Architecture: i386
Maintainer: Andreas Ã&#8211;man <andreas@tvheadend.org>
Installed-Size: 6995
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libc6 (>= 2.7), libcurl3-gnutls (>= 7.16.2), libssl1.0.0 (>= 1.0.0), zlib1g (>= 1:1.1.4)
Recommends: xmltv-util
Enhances: showtime
Replaces: hts-tvheadend
Homepage: https://tvheadend.org
Priority: extra
Section: video
Filename: pool/main/t/tvheadend/tvheadend_3.4.28~geb79aee~trusty_i386.deb
Size: 1624420
SHA256: ab69bd807384b5ea77a26d3ef0240fc25afeaf2c569da638024418e311282a11
SHA1: 3ecccf5c2d0c3479b407e8a4a2ea1f99a50425b7
MD5sum: 9ce4e9d96e224fcb0a8991b6232d73fa
Description: Tvheadend
 Tvheadend is a TV streaming server for Linux supporting DVB, ATSC, IPTV, and Analog video (V4L) as input sources.
 Can be used as a backend to Showtime, XBMC and various other clients.

Package: tvheadend-dbg
Source: tvheadend
Version: 3.4.28~geb79aee~trusty
Architecture: i386
Maintainer: Andreas Ã&#8211;man <andreas@tvheadend.org>
Installed-Size: 2216
Depends: tvheadend (= 3.4.28~geb79aee~trusty)
Priority: extra
Section: debug
Filename: pool/main/t/tvheadend/tvheadend-dbg_3.4.28~geb79aee~trusty_i386.deb
Size: 687884
SHA256: 7ccadaff50dc872448921b97eea8106b5a49181d4830aae3b6023e44d3cdcf39
SHA1: bef49f1090829a88b29ffd7ec25dcde8885b4579
MD5sum: b4bffa05968ce6d99f953343d7c81adb
Description: Debug symbols for Tvheadend
 This package contains the debugging symbols for Tvheadend.

```

You'll need to add the unstable branch.

---

### Post by derekcentrico on 2014-07-12
Argh I found a craptastic blog and assumed it was accurate on the latest stable.  I didn't pay attention the the builds list was nightly on the developer site, either.

Thanks for pointing this out.  Cheers.

---

### Post by Bucky Ball on 2014-07-12
*Thread moved to **Multimedia & Video**.*

This thread could come in handy for others. Could you please mark as solved? (It won't close the thread.) ;)

---

### Post by derekcentrico on 2014-07-13
Roger that.  Marked as solved.

---

