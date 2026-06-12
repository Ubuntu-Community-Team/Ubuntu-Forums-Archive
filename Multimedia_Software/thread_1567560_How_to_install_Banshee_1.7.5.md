---
title: "How to install Banshee 1.7.5"
date: 2010-09-03
forum: Multimedia Software
---

### Post by arrimapirate on 2010-09-03
Banshee 1.7.5 supports the ipod touch and iphone but i can not figure out how to get it on Ubuntu. Its not in synaptic yet and i can not compile from source because it always says 
>  configure: error: Package requirements (gstreamer-0.10 >= 0.10.12
        gstreamer-base-0.10 >= 0.10.12
        gstreamer-plugins-base-0.10 >= 0.10.12
        gstreamer-controller-0.10 >= 0.10.12
        gstreamer-dataprotocol-0.10 >= 0.10.12
        gstreamer-fft-0.10 >= 0.10.12) were not met:

No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found
No package 'gstreamer-fft-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GST_CFLAGS
and GST_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


So is there anyway to install it now?

---

### Post by bowens44 on 2010-09-04
you have to install all the missing packages 

I have successfully built and installed it but it was very time consuming.

---

### Post by hriqe on 2010-09-04
You can use **_[Banshee Active Development PPA]("https://launchpad.net/~banshee-team/+archive/banshee-unstable")_** or the **_[Banshee Daily Build PPA]("https://launchpad.net/~banshee-team/+archive/banshee-daily")_**.
Works just fine.

---

### Post by howefield on 2010-09-04
> **hriqe said:**
> You can use...

This will give you 1.7.4 at the moment.

---

### Post by arrimapirate on 2010-09-05
> **bowens44 said:**
> you have to install all the missing packages 

I have successfully built and installed it but it was very time consuming.

Do you mean compile from source? Ill give that a try. 

[QUOTE=_hriqe]_You can use **_[Banshee Active Development PPA]("https://launchpad.net/%7Ebanshee-team/+archive/banshee-unstable")_** or the **_[Banshee Daily Build PPA]("https://launchpad.net/%7Ebanshee-team/+archive/banshee-daily")_**.
Works just fine.[/QUOTE]

I can never get those ppas to work right. It might be because i run 10.10

---

### Post by arrimapirate on 2010-09-05
Okay im working on compiling from source but i keep getting an error about BOO not being installed. I installed the recent version from synaptic but it still said it wasnt installed. Any one else had that problem?

---

### Post by oroberos on 2011-01-08
Install libboo-cil-dev from synaptic.

---

