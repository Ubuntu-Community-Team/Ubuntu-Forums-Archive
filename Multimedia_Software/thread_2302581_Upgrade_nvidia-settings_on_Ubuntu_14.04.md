---
title: "Upgrade nvidia-settings on Ubuntu 14.04"
date: 2015-11-11
forum: Multimedia Software
---

### Post by errolflynn on 2015-11-11
Hey lads, I'm installing cuda. Among the dependencies, I have to upgrade my version of nvidia-settings 346.72 to be >= 352.39:

```
The following packages have unmet dependencies:
 cuda-drivers : Depends: nvidia-settings (>= 352.39) but 346.72-0ubuntu1 is to be installed



```

How would I do this? I've already changed my nvidia drivers to be v352.55.

Cheers

---

### Post by blm-ubunet on 2015-11-13
The nvidia-settings in trusty seems to have been out-of-sync with the driver for months.
At one point I compiled this from source (nvidia-settings is FOSS).
The settings package seems to cope with version mismatches but could be lacking some new features.

Could just force the installation with override options..
or 
These guys seems to have latest..
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=trusty)
**Will this break your CUDA install?** Need to study the driver readme file.
You could use their ppa or just pinch the "settings" package & manually install the deb.

---

