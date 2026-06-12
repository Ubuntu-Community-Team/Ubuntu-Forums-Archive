---
title: "using encrypted loopback files from older releases"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VogonZarniwoop on 2011-04-02
I've been using encrypted loopback devices for a long time, maybe since 8.x.  They've always been working fine but I'm having troubles now in 11.04 in using the image files I made a long time ago.  I'm using the procedure described here: [https://h3g3m0n.wordpress.com/2007/04/16/quick-simple-encrypted-loopback-filesystem/](https://h3g3m0n.wordpress.com/2007/04/16/quick-simple-encrypted-loopback-filesystem/)

It seems like I can make a new image and it works fine, but the image files I have had for a long time can no longer be decrypted using encryption=aes,keybits=256. They were encrypted with aes256 a number of versions ago.

What's the trick for using old images now?  I've tried both cryptoloop and dm-crypt with no luck.

---

