---
title: "Autobuild doesn't seem to include backend packages"
date: 2010-08-30
forum: Mythbuntu
---

### Post by wsuetholz on 2010-08-30
Hello, the ppa [https://edge.launchpad.net/~mythbuntu/+archive/0.23.1/+packages](https://edge.launchpad.net/~mythbuntu/+archive/0.23.1/+packages) doesn't seem to have the mythtv-backend packages available for installation..

I enabled the ppa by doing the dpkg-reconfigure, I have the latest version of the autobuilds package,

I did the apt-get update && apt-get upgrade, and I got the frontend stuff all updated to 0.23.1, but not the backend.  After that I was getting the network protocol mismatch frontend 23056 backend 56.

I eventually found the packages and manually downloaded and installed, but I shouldn't have had to.

Bill

---

### Post by LowSky on 2010-08-30
you should use this: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

to keep mythbuntu upgraded to .23.1 and later for .24

---

### Post by tgm4883 on 2010-08-30
You never stated which repo you are using. The backend packages are available, so if they aren't available on whichever repo you selected then that is an issue.

:EDIT:

Just to confirm, this screenshot is for Lucid

---

