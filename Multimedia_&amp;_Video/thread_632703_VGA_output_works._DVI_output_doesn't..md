---
title: "VGA output works. DVI output doesn't."
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by ntt2007 on 2007-12-05
Sorry for the duplicate post. I just want to clean up my previous thread.

I have a desktop with Asus M2A-VM motherboard and ATI X1200 (according to lspci) integrated. I installed fglrx driver but I got no signal on my DVI output (blank screen). I try VGA output and it works. Does anybody know how to fix this?

Thanks.

BTW, my monitor is Gateway FPD2275W, Gutsy Kubuntu. The vesa driver works with the DVI connector but it only outputs 1280x1024 resolution. My monitor native resolution is 1680x1050.

---

### Post by vickiho on 2008-01-12
I was having the same problem, and for some reason, switching to the open source ATI driver wasn't the answer to my problems, because it couldn't render my resolution properly.

I was using the restricted driver fglrx activated automatically, but my problem was fixed when I went to [www.ati.com](www.ati.com) and got the driver for my exact card model off the site.

I'm not sure why, but my TV output works now! :)

Download the autorun installer package from ATI, navigate to the directory where the file is located and enter

```
sudo sh _filename_
```

---

