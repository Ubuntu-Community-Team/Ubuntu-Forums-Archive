---
title: "gtkpod not wanting to play nice with mpeg4ip support?"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by AzraelUK on 2007-06-30
I've recently been trying to compile gtkpod CVS version with MP4 support, so I can get DVDs that I've ripped to play on my iPod. I've had to jump through hoops just to get mpeg4ip to compile, and now gtkpod refuses to compile with mp4 support now.

I downloaded the latest version of mpeg4ip ([http://prdownloads.sourceforge.net/mpeg4ip/mpeg4ip-1.5.0.1.tar.gz](http://prdownloads.sourceforge.net/mpeg4ip/mpeg4ip-1.5.0.1.tar.gz)). I get an error about a missing function doing ./bootstrap normally, so I have to do ./bootstrap --disable-server --disable-player. After a while, it finishes compiling, then I do the checkinstall magic, and change the package name to mpeg4ip (as [this guide]("https://help.ubuntu.com/community/iPodVideoTransferring") suggests). So, that's that seemingly sorted.

libgpod also compiles fine, no worries about that.

But, when I get onto gtkpod, here's where the fun starts. `bash ./configure` tells me that no, I can't have my cake (or my mp4 support, for that matter) and eat it too. Because this is Linux, where win-win situations are a lot rarer than normal. Looking through the output, it says 'checking for library containing MP4GetMetadataGrouping... no', which I think may be the cause of the problem.

Any help?

AMD Sempron 3400+ / nVidia 6100 / 2GB DDRII RAM / too much free time

---

### Post by AzraelUK on 2007-07-01
Bump.

This is seriously getting on my nerves now. Please help :/

---

### Post by AzraelUK on 2007-07-09
Bump, again.

---

### Post by vikrant82 on 2007-07-24
Same here budz!!!
](*,)

---

### Post by scorpion-kde on 2007-09-16
[https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/135178](https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/135178)

This is not cool.  It worked in Feisty.

---

