---
title: "nvidia-current stuck in upgrade limbo"
date: 2011-01-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jmmL on 2011-01-15
Haven't seen this issue crop up here, which strikes me as odd and suggests that it might be a problem on my end rather than the repos.

nvidia-current is waiting for an upgrade to 260.19.29 (from 260.19.21). However, nvidia-current-modaliases doesn't have a 260.19.29 version to upgrade to, so it's being marked as remove whenever I try to upgrade nvidia-current.

Is nvidia-current-modaliases safe to remove? I've never been quite able to work out what it does. I'm running x86_64 with an Nvidia 8600M GS.

---

### Post by Harry33 on 2011-01-15
> **jmmL said:**
> Haven't seen this issue crop up here, which strikes me as odd and suggests that it might be a problem on my end rather than the repos.

nvidia-current is waiting for an upgrade to 260.19.29 (from 260.19.21). However, nvidia-current-modaliases doesn't have a 260.19.29 version to upgrade to, so it's being marked as remove whenever I try to upgrade nvidia-current.

Is nvidia-current-modaliases safe to remove? I've never been quite able to work out what it does. I'm running x86_64 with an Nvidia 8600M GS.

Yes all the -modaliases are safe to remove. In Natty official repo, there isn't anymore such a package. So it is depreciated.

---

### Post by terry_gardener on 2011-01-15
yes it is safe to remove. 

if you check the dependencies using synaptic it shows that it replaces the nvidia-current-modaliases package and also conflicts with it so it gets removed since it is no longer needed.  

i also have the nvidia-current and it works fine.

---

### Post by efflandt on 2011-01-15
I think some time ago that was removed and is handled some other way:

```
efflandt@natty-ssd:~$ **dpkg-query -l nvidia-current nvidia-settings nvidia-current-modaliases**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  nvidia-current              260.19.29-0ubuntu1          NVIDIA binary Xorg driver, kernel module and VDPAU library
un  nvidia-current-modaliases   <none>                      (no description available)
ii  nvidia-settings             260.19.21-0ubuntu3          Tool of configuring the NVIDIA graphics driver
```Note that NVIDIA X Server Settings does show proper version 260.19.29 and it all works for my GT 430 (which kernels do not even recognize) in 64-bit:

efflandt@natty-ssd:~$ **lspci | grep VGA**
01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1)

---

### Post by jmmL on 2011-01-15
Thanks for the helpful replies.

---

