---
title: "Cannot play certain videos after upgrading to 13.10"
date: 2013-11-07
forum: Multimedia Software
---

### Post by vaibhav on 2013-11-07
After upgrading to 13.10, I can no longer play certain video files through totem. I get the error
```
Required plugin could not be found

Videos requires to install plugins to play media files of the following type: H.264 decoder
```Kindly help me resolve the same.
Thanks.

---

### Post by Bucky Ball on 2013-11-07
Have you checked you still have ubuntu-restricted-extras installed?

---

### Post by vaibhav on 2013-11-07
Yes
```
~$ dpkg -l ubuntu-restricted-extras
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                    Version                  Architecture             Description
+++-=======================================-========================-========================-====================================================================================
ii  ubuntu-restricted-extras                59                       amd64                    Commonly used restricted packages for Ubuntu

```

---

