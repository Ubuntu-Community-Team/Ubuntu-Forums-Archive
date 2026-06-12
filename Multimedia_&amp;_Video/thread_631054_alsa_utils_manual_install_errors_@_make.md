---
title: "alsa utils manual install errors @ make"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by Paradoxfox93 on 2007-12-04
Okay, so yeah, I'm a n00b.   Still, I'm intelligent, especially when it comes to computers in general.  I've been messing around with my new laptop for two weeks and have sound and wireless working now.  Still, when I try to install alsa (to get my sound working) I get errors on 'make'ing utils.  I've been talking to others on the forums with similar problems and they report the same errors.  I have sound.  It's not a major problem at the moment but I imagine it will be at some point.  FYI for those pulling up this thread because they read MT3244 gateway, the Alsa 1.0.15 driver update fixes with the patch already integrated (I.E. you don't need the patch, just 'sudo ./configure && sudo ./make && ./make install' the drivers and libraries, however I imagine you will likely have the following errors).  I get the following errors configuring & making the utils:

configure:


config.status: WARNING: alsaconf/po/Makefile.in seems to ignore the --datarootdir setting

Making:


Making all in include
make[1]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/include'
make all-am
make[2]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/include'
make[2]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/include'
make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/include'
Making all in alsactl
make[1]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf'
Making all in po
make[2]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf'
make: *** [all-recursive] Error 1

-----------

Can someone tell me how to easily fix this?  Perhaps someone can even tell me how to troubleshoot?  Describe this error as a bug worthy of reporting to Alsa?

---

