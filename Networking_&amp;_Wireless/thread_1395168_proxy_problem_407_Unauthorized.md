---
title: "proxy problem: 407 Unauthorized"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by palash_me06 on 2010-01-31
i use proxy settings for http in my network which has username &password authentication.
i set up system > preference > network proxy .like below........
[http://img718.imageshack.us/img718/9917/proxy.jpg](http://img718.imageshack.us/img718/9917/proxy.jpg)
When i use "add/remove" or  :synaptic" i get net conncetion .
but in command line ,when i try to use  "sudo apt-get install ..." i get the following error..
_____________________________-
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
  407 Unauthorized
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
  407 Unauthorized
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
  407 Unauthorized
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
  407 Unauthorized
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
  407 Unauthorized
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
  407 Unauthorized
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
  407 Unauthorized
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
  407 Unauthorized
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages)  407 Unauthorized

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources)  407 Unauthorized

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  407 Unauthorized

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  407 Unauthorized

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  407 Unauthorized

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  407 Unauthorized

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  407 Unauthorized

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  407 Unauthorized

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  407 Unauthorized

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  407 Unauthorized
__________________________________________________________________

server pc : windows xp sp2.
server software :CCPROXY
[http://www.youngzsoft.net/ccproxy/]("http://www.youngzsoft.net/ccproxy/")
what's the problem ?

---

