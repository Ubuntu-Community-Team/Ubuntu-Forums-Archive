---
title: "k3b problem with install"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by swoskow on 2007-08-16
I have tried to install k3b on feisty (gnome) but I get a message that I am missing the following.

k3b:
  Depends: kdelibs4c2a (>=4:3.5.7-1) but 4:3.5.6-0ubuntu14 is to be installed
  Depends: libart-2.0-2 (>=2.3.18) but 2.3.17-1 is to be installed
  Depends: libc6 (>=2.6-1) but 2.5-0ubuntu14 is to be installed
  Depends: libdbus-1-3 (>=1.1.1) but 1.0.2-1ubuntu4 is to be installed
  Depends: libfreetype6 (>=2.3.5) but 2.2.1-5ubuntu1.1 is to be installed
  Depends: libgcc1 (>=1:4.2-20070516) but 1:4.1.2-0ubuntu4 is to be installed
 Depends: libk3b3 but it is not going to be installed
  Depends: libmusicbrainz4c2a (>=2.1.5) but 2.1.4-1ubuntu2 is to be installed
  Depends: libstdc++6 (>=4.2-20070516) but 4.1.2-0ubuntu4 is to be installed
  Depends: zlib1g (>=1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed

These are newer versions of the programs I have so I am thinking I must be missing a repository in my list but I do not know which one I need.  Also, the libc6 is a constant problem and I cannot find any good solution searching the forums.

Any suggestions?

---

### Post by wolfen69 on 2007-08-16
i dont know if this will solve your problem, but try the medibuntu repositories. [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) also, did you go to software sources to see if all your repos are all checked off?

---

### Post by swoskow on 2007-08-16
Thank you for helping.

I have medibuntu in my repository and I did check and they are all checked off.

---

### Post by swoskow on 2007-08-16
> **wolfen69 said:**
> i dont know if this will solve your problem, but try the medibuntu repositories. [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) also, did you go to software sources to see if all your repos are all checked off?

Your post did help - the problem was that I had rarewares also in my repository and the k3b in synaptic was from rarewares not medibuntu.  I unchecked rarewares and installed k3b from medibuntu and it worked fine.  Your post led me to the answer - thank you very much.

---

