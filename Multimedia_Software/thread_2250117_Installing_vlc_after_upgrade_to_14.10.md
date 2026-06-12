---
title: "Installing vlc after upgrade to 14.10"
date: 2014-10-26
forum: Multimedia Software
---

### Post by ansus on 2014-10-26
I have experienced the same problem after upgrade from 14.04 to 14.10. I note that it has been reported as a 'bug'.

unmet dependencies.....

---

### Post by ansus on 2014-10-26
The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.2.0~pre2+git20141011+r57575+24+12~ubuntu14.10.1) but 3.0.0~~git20140930+r58027+30~ubuntu14.10.1 is to be installed
       Depends: libgles1-mesa (>= 7.8.1) but it is not going to be installed or
                libgles1
       Recommends: vlc-plugin-notify (= 2.2.0~pre2+git20141011+r57575+24+12~ubuntu14.10.1) but 3.0.0~~git20140930+r58027+30~ubuntu14.10.1 is to be installed
       Recommends: vlc-plugin-samba (= 2.2.0~pre2+git20141011+r57575+24+12~ubuntu14.10.1) but 3.0.0~~git20140930+r58027+30~ubuntu14.10.1 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by mc4man on 2014-10-26
> **ansus said:**
> The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.2.0~pre2+git20141011+r57575+24+12~ubuntu14.10.1) but 3.0.0~~git20140930+r58027+30~ubuntu14.10.1 is to be installed
       Depends: libgles1-mesa (>= 7.8.1) but it is not going to be installed or
                libgles1
       Recommends: vlc-plugin-notify (= 2.2.0~pre2+git20141011+r57575+24+12~ubuntu14.10.1) but 3.0.0~~git20140930+r58027+30~ubuntu14.10.1 is to be installed
       Recommends: vlc-plugin-samba (= 2.2.0~pre2+git20141011+r57575+24+12~ubuntu14.10.1) but 3.0.0~~git20140930+r58027+30~ubuntu14.10.1 is to be installed
E: Unable to correct problems, you have held broken packages.
You do not have the same issue. It appears you have mixed the videolan stable & master ppa's.
Maybe try this - 
```
sudo apt-get purge vlc-data
```
Then ck. your sources about which ppa if any you'd like to use
(the videolan master ppa is a bit of a mess as the current vlc git needs sources not in 14.10 so builds always fail

---

### Post by howefield on 2014-10-26
Hello ansus, I have moved your posts to their own thread.

---

