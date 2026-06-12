---
title: "Error when updating repositories"
date: 2010-08-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yumi on 2010-08-16
When I do "Sudo apt-get update" the following error is shown in the terminal (more of them, I copied only the first few).
> N: Ignoring file 'qbzr-dev-ppa-karmic.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-audio-dev-ppa-lucid.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'medibuntu.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'medibuntu.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

Can I delete sorces.list.d, the entries seem to be old ones.

Further since:
I deleted the files with the endings .save and .distUpgrade . No Errors any more, but still not upgrading. That happened before and I reported it yesterday. Update Manager and Terminal do not update despite showing 90 updates available.

> 
This is the end of the Terminals action after sudo apt-get update
Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) maverick-proposed/main i386 Packages
Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) maverick-proposed/multiverse i386 Packages
Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) maverick-proposed/universe i386 Packages
Reading package lists... Done



Michael

---

### Post by wojox on 2010-08-16
Sure go to System > Administration > Software Sources > Other Software and remove those ppa's.

---

### Post by Yumi on 2010-08-16
Followed your advice. Only ... ubuntu maverick partner is selected on this page. Not updating.

---

### Post by ktp on 2010-08-16
> **Yumi said:**
> When I do "Sudo apt-get update" the following error is shown in the terminal (more of them, I copied only the first few).

Can I delete sorces.list.d, the entries seem to be old ones.


"N: Ignoring file" thing was found while ago...here is a thread about it...hopefully it helps:

[http://ubuntuforums.org/showthread.php?t=1545006&highlight=list.save](http://ubuntuforums.org/showthread.php?t=1545006&highlight=list.save)

---

### Post by Yumi on 2010-08-16
Thanks ktp. Its a bug (611925) and I follow their development now. Should have searched for "Ignore file" instead of starting a new threat.

Michael

---

