---
title: "installing dvdrip on lubuntu i386 laptop"
date: 2019-06-24
forum: Multimedia Software
---

### Post by erictheviking on 2019-06-24
I am trying out Lubuntu on this pretty old i386 Panasonic toughbook with 2gb ram. I wish to install dvdrip. In Xubuntu it is in the package manager but not here on Lubuntu. I have given up trying to install it manually. Is there an easy way I can do this please.
ps. Yes I know handbrake is available but I prefer dvdrip. 
Thanks.

---

### Post by erictheviking on 2019-06-28
Just a bump on this. No replies at all! 
Thanks

---

### Post by Holger_Gehrke on 2019-06-30
Searching on packages.ubuntu.com shows that dvdrip is available for 16.04 and 18.04. Might be one of those packages that are only available in LTS-releases. Also a look at the programs homepage at [http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/) shows that it's been a long time since any updates were made to it )2010 or so), so it might be better to look for an alternative.

Holger

---

### Post by #&amp;thj^% on 2019-06-30
I'd just try the .deb already packaged for Ubuntu: [https://ubuntu.pkgs.org/18.04/ubuntu-multiverse-i386/dvdrip_0.98.11-0ubuntu8_all.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-multiverse-i386/dvdrip_0.98.11-0ubuntu8_all.deb.html)
And I would use Gdebi to install it.
This will be installed:
```
Requires
Name 	Value
dvdrip-utils 	-
eject 	-
ffmpeg 	-
fping 	-
imagemagick 	-
libevent-execflow-perl 	>= 0.64
libevent-perl 	-
libevent-rpc-perl 	>= 1.01
libgtk2-ex-formfactory-perl 	>= 0.66
libintl-perl 	>= 1.16
liblocale-gettext-perl 	-
lsdvd 	-
ogmtools 	-
perl 	-
transcode 	>= 3:1.1.7-1
Conflicts
Name 	Value
video-dvdrip 	<= 0.50.18-0.0

```
The version numbers may change though.
I use it from time to time, but not on Ubuntu and not as a i386 install.
Mostly I use MakeMKV and HandBrake.
Good Luck

---

