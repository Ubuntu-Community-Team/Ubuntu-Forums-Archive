---
title: "Flash update?"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by groeswenphil on 2007-12-14
Hi,
Anybody remind me?
I've downloaded the flash update to my desktop. I've managed to extract the file and it now lise within a folder on my desktop.
I've got to run a terminal command to get the file to run?
How do I map to that file in terminal?
Thanks,
Phil

---

### Post by disturbedite on 2007-12-14
why would download it from adobe's website when you can just install it from the repos via your package manager?

---

### Post by mdpalow on 2007-12-15
> **disturbedite said:**
> why would download it from adobe's website when you can just install it from the repos via your package manager?

Because the flash update from the repos is broke right now. Where you been? :)

---

### Post by groeswenphil on 2007-12-15
I downloaded a tar.gz file from their website. Will that work?
Phil

---

### Post by disturbedite on 2007-12-15
actually, i have seen ppl reporting that, but it must only affect *some* ppl cuz i have had no problems whatsoever with it...

---

### Post by daradib on 2007-12-15
You can install this way: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by mdpalow on 2007-12-15
> **daradib said:**
> You can install this way: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

If you'd rather have it done for you... see my link below.

---

### Post by daradib on 2007-12-16
Actually, I think the instructions at [thread]("http://ubuntuforums.org/showthread.php?t=636397") are very easy.

> **daradib said:**
> **Official Fix**

The fix for this bug has been uploaded to all proposed Ubuntu repositories. Please see [this]("https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree/"). This is for all Ubuntu releases from 6.06 though 7.10. This means the fix should be available very soon through the repositories (the binary packages have been built) if the proposed repository is enabled. Of course, this is still susceptible to the same problems as this fix (including no flash plugin support in Konqueror).

To enable the proposed repository, go to System -> Administration -> Software Sources. Under the Updates tab, check pre-released updates. When you close the window, it will then say package information is out of date, so click Reload. You may need to uninstall the package obtained through the immediate fix to download the package through the repositories.

If you do not wish to enable the proposed repository, you may download the binary package alone.

**32-bit packages:** The 32-bit package has been built, and the Ubuntu 7.10 package is available [here]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb") (on gutsy-proposed repository). Binary packages for other releases: [32-bit 7.04]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_i386.deb"), [32-bit 6.10]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.10_i386.deb"), and [32-bit 6.06]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.06_i386.deb"). Just download the package for your release, double-click the file, and install the package.

**64-bit packages:** The 64-bit package has been built, and the Ubuntu 7.10 package is available [here]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb") (on gutsy-proposed repository). Binary packages for other releases: [64-bit 7.04]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb"), [64-bit 6.10]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.10_amd64.deb"), and [64-bit 6.06]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.06_amd64.deb"). Just download the package for your release, double-click the file, and install the package. However, I do not believe you will be able to use the 64-bit flashplugin-nonfree package without modifications on Ubuntu releases before 7.10.

So basically either enable the proposed repository, or install the provided packages. Really simple.

---

