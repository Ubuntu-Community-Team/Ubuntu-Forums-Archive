---
title: "Twonky media server 7.3 and Ubuntu 14.04 LTS"
date: 2014-09-30
forum: Multimedia Software
---

### Post by cheechy on 2014-09-30
I've been using Twonky as a simple but effective DLNA server for quite a few years now but upon upgrading my server to 14.04 on a fresh build I've found that support for it has become fairly non existent, despite the company still offering to sell the product. It seems its becoming harder to run this on debian variants.

I'm trying to get it to work on 14.04 without success thus far. I get there are alternatives out there but i do like the simple interface of TMS along with the built in transcoding abilities so dont want to give up quite yet! I've configured everything up to specifying the appdata folder and running twonkystarter using the -appdata param. I get this :

libgcc_s.so.1 must be installed for pthread_cancel to work

Which goes round and round in a start/stop loop until Ubuntu OS kills it. 

Is this library avaialble in 14.04 and if so what is the package?

Anyone managed this successfully yet? 

Thanks.

---

### Post by Vladlenin5000 on 2014-10-02
The Linux How-to file included has this note:

```
Known issue:

The installer script (twonky*.sh) is not working for modern ubuntu linux
systems due to incompatibitlities with some system config tools (chkconfig 
vs. update-rc.d). The manual installation however is unaffected.


```

---

### Post by cheechy on 2014-10-02
Yes thanks am aware of this hence I was running "twonkystarter" direct with the -appdata parameter as mentioned above. Twonky.sh calls this command amongst others as part startup so I'm doing the startup manually as prescribed. This is where I'm getting the libgcc_s loop and eventual shutdown.

---

