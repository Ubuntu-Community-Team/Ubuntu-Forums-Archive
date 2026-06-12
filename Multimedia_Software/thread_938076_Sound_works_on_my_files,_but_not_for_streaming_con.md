---
title: "Sound works on my files, but not for streaming content"
date: 2008-10-04
forum: Multimedia Software
---

### Post by tinker123 on 2008-10-04
Hi;

I'm using Ubuntu 8.04 & Firefox 3.0.3

I was getting sound just fine with flash 9 until a thunderstorm hit a few days ago.  My ethernet card got toasted.  I replaced it.  Audio works fine for everything else, but not Flash.

Any ideas for things I could try?

Thanks in advance for any info

---

### Post by tinker123 on 2008-10-06
I got it working

I did these

> 
sudo bash

apt-get install libflashsupport 

apt-get install alsa-oss

gedit /etc/firefox/firefoxrc



Then I altered the file above to read:

> 
FIREFOX_DSP="aoss"


Then I used synaptic to reinstall flashplugin-nonfree

---

