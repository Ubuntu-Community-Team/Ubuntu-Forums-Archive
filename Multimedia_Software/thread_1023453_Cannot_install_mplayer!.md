---
title: "Cannot install mplayer!"
date: 2008-12-27
forum: Multimedia Software
---

### Post by PrateekParekh on 2008-12-27
I am trying to install mplayer because I have read that it contains the scaletempo plugin that can be used to listen to audio books at 1.5x speed without any change in the pitch. 

When I try to install it through terminal I get the following message:
> sudo apt-get install mplayerReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libfaac0 (>= 1.26) but it is not installable
           Depends: libmp3lame0 (>= 3.98) but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages

Using the synaptic manager gives the following:
> mplayer:
 Depends: libfaac0 (>=1.26) but it is not installable
 Depends: libmp3lame0 (>=3.98) but it is not installable
 Depends: libxvidcore4 (>=1:1.0.0-0.0) but it is not installable
 Depends: mplayer-skins  but it is not installable


Any pointers?

---

### Post by wolfen69 on 2008-12-28
just go to system>administration>software sources and make sure all your repos are checked off. check the third party tab too if you want. then close and it will ask you to reload. do so. you should be able to download it now.

---

### Post by PrateekParekh on 2008-12-28
Thanks. That worked.

---

