---
title: "&quot;N: Ignoring file **********&quot; notices"
date: 2010-08-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by His on 2010-08-03
I just got a bunch of these when I ran 'sudo apt-get update':

> N: Ignoring file 'google-chrome.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'canonical-dx-team-une-lucid.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-wine-ppa-lucid.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'medibuntu.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'canonical-dx-team-une-lucid.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-mozilla-daily-ppa-lucid.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-wine-ppa-lucid.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'bisigi-ppa-lucid.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'medibuntu.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'bisigi-ppa-lucid.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'canonical-dx-team-une-lucid.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-wine-ppa-lucid.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'medibuntu.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'canonical-dx-team-une-lucid.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-mozilla-daily-ppa-lucid.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-wine-ppa-lucid.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'bisigi-ppa-lucid.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'medibuntu.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'bisigi-ppa-lucid.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

This was my first time getting this and I've been on Maverick for nearly a month now.

Thoughts?

---

### Post by ronacc on 2010-08-03
there are multiple threads on this .

---

### Post by His on 2010-08-03
yes, actually, I see that now.

---

### Post by 8jwong14 on 2010-08-09
> **His said:**
> yes, actually, I see that now.
Hey.  Can you please at least post a link or links to where I can get help for this problem?  I can't find it.

---

### Post by Anduu on 2010-08-09
> **8jwong14 said:**
> Hey.  Can you please at least post a link or links to where I can get help for this problem?  I can't find it.

Here is the related thread...I had trouble finding it as well...

[http://ubuntuforums.org/showthread.php?t=1542688&highlight=ignore](http://ubuntuforums.org/showthread.php?t=1542688&highlight=ignore)

---

### Post by Catharsis on 2010-08-09
[http://launchpad.net/bugs/611925](http://launchpad.net/bugs/611925)

---

### Post by dpacmittal on 2010-08-26
This fixed it for me:
[http://www.absolutelytech.com/?p=874](http://www.absolutelytech.com/?p=874)

---

