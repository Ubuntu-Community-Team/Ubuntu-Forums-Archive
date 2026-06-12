---
title: "cant install vlc"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by laro on 2007-10-23
Hi

I just install ububtu 7.10

I want to play movies (divx) via vlc

when I try to install vlc via synaptic 

I get the following msg:

"could not mark all packages for installation or upgrade

the following packages have unresolvable dependencies.
make sure that all required repositories are add and enabled in the prefernces"

"vlc:
depends: vlc nox but it not going to be installed
depends: libsdl-image 1.2 (>=1.2.5) but it is not installable
depends ttf-dejavu but it is not installable"


what can i do ?

---

### Post by 1/0 on 2007-10-23
Well... You could for instance make sure the needed repositories are enabled and check that you have all [media codecs]("http://www.5thwind.com/?p=48") etc installed.

---

### Post by mtbrDot on 2007-11-01
I had the same error.

download and install it manually from here:

[https://launchpad.net/ubuntu/gutsy/i386/libsdl-image1.2/1.2.5-3](https://launchpad.net/ubuntu/gutsy/i386/libsdl-image1.2/1.2.5-3)

then add medibuntu to your repositories and run the command

sudo apt-get install vlc

it worked for me.

---

### Post by Alan Percy on 2007-11-27
I too followed mtbrDot's advice and it worked like a charm. Thanks to the Ubuntu Community for helping us noobies! :popcorn:

---

