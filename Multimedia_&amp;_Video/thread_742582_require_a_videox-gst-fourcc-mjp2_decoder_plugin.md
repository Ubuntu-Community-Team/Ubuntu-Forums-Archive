---
title: "require a video/x-gst-fourcc-mjp2 decoder plugin"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by vraetorian on 2008-04-01
Hi there,
Has anyone else found this decoder? It's needed to play a .mov, quicktime file.

" this movie requires a video/x-gst-fourcc-mjp2 decoder plugin which is not installed."

I searched google for it, added every kind of codec i could find relating even remotely to it in the synaptic package manager.

VLC, Movieplayer both don't work.

Hope someone is able to help!

---

### Post by warp99 on 2008-04-02
Have you installed the w32 codec packages from Medibuntu.org?

[https://help.ubuntu.com/community/Medibuntu#head-b7483038fe4d8989bff6ac4ce3bf34060659b4ac](https://help.ubuntu.com/community/Medibuntu#head-b7483038fe4d8989bff6ac4ce3bf34060659b4ac)

If you have already completed this step then you can find a Windows codec for that particular format and place the file into the /usr/lib/codecs directory. Then mplayer should decode the file.

---

### Post by warp99 on 2008-04-02
The windows codec you're looking for is mj2desc.dll:

[http://www.softwaretipsandtricks.com/dll/15438-Mj2descdll.html](http://www.softwaretipsandtricks.com/dll/15438-Mj2descdll.html)

---

### Post by nitrofurano on 2008-07-21
Well, this url has no .dll downloads available, and from google i can't find anywhere.

the main fact is i'm very curious to see this last Michel Gondry work, which i can only find encoded with this codec: [http://www.wired.com/images/article/full/2008/04/wanderlust3d_wired.mov](http://www.wired.com/images/article/full/2008/04/wanderlust3d_wired.mov)

---

