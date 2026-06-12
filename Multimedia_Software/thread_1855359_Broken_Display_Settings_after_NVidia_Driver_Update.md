---
title: "Broken Display Settings after NVidia Driver Update Attempt"
date: 2011-10-06
forum: Multimedia Software
---

### Post by HellesAngel on 2011-10-06
Perhaps someone can help me - I followed the destructions [here]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html") to attempt to get my Asus X53S laptop with NVidia GT540M to use the latest drivers.  The results were not good - the boot stopped halfway, no error messages.  I now would like to revert to the original factory settings.

In summary the steps were:
> 
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings


By removing /etc/X11/xorg.conf I have the destop back, but Unity is gone (some may say that's a good thing ;)) and I would like to revert to the original default Ubuntu settings.  I followed the PPA Purge instructions on that page which didn't set everything back as it was.

Can anyone provide more instructions? Thanks in advance.

---

### Post by mikewhatever on 2011-10-06
You have to installed the proprietary Nvidia driver to use Unity. Use the Additional Driver utility to install the recommended one from the repositories.

---

### Post by HellesAngel on 2011-10-06
Many thanks for the hint - I found this already, it shows NVIDIA accelerated graphics driver (current version) [Recommended] is installed but not currently in use.  I could try to remove it and re-install, or perhaps there's a better option?

---

### Post by lcman on 2011-10-06
> **HellesAngel said:**
> Perhaps someone can help me - I followed the destructions [here]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html") to attempt to get my Asus X53S laptop with NVidia GT540M to use the latest drivers.  The results were not good - the boot stopped halfway, no error messages.  I now would like to revert to the original factory settings.

In summary the steps were:


By removing /etc/X11/xorg.conf I have the destop back, but Unity is gone (some may say that's a good thing ;)) and I would like to revert to the original default Ubuntu settings.  I followed the PPA Purge instructions on that page which didn't set everything back as it was.

Can anyone provide more instructions? Thanks in advance.

You need to uninstall the drivers you've just installed first. You need to do sudo apt-get remove nvidia-current nvidia-current-modaliases nvidia-settings

Maybe you'll need to boot into single user mode for that idk. You should always install drivers from the additional drivers program because the other drivers might be latest but might not work properly with your kernel

---

### Post by HellesAngel on 2011-10-06
Many thanks - the drivers were already uninstalled (perhaps because of the purge above) and the additional drivers program reinstalled something but they're still listed as not currently in use.  

This laptop is one of those with switchable Intel on board and NVidia graphics, I've read that can cause trouble, or did in the past - is this still an issue?

---

### Post by HellesAngel on 2011-10-06
This thread does perhaps better belong in the ASUS forum as it's ASUS specific.  The answer for me was Bumblebee with the named configuration the  K53 configuration from Thomas Kratz as recommended elsewhere and it  works fine.

---

