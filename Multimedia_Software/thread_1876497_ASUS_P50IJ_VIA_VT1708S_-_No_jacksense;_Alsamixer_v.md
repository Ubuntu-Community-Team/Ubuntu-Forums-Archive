---
title: "ASUS P50IJ: VIA VT1708S - No jacksense; Alsamixer v1.0.24.2"
date: 2011-11-06
forum: Multimedia Software
---

### Post by nordak21 on 2011-11-06
Hello, 

I recently installed Ubuntu 11.10 on my ASUS P50IJ, but the problem with the sound is that when I plug my headphones in, there is no jack sense and sound comes through both the internal speakers and the headphones. 

My chip is VIA VT1708S, which is a HDA Intel card.

I searched many threads, which prompted me to do multiple things:
Update alsamixer - I did this through apt-get and it appears I have the latest version
Append a line with the model to /etc/modprobe.d/alsa-base.conf - I added "options snd-hda-intel model=auto" since this was the only one in one of the lists of models I found. This doesn't do anything for the problem.

From the changelog from Alsa v1.0.21 to v1.0.22 ([http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22)]("http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22") , it appears that alsa does in fact support my chip. (Under HDA codec there are multiple lines about added support for VT1708S).

But I still can't figure out how to configure alsa so that the jack sense will work properly! Any help will be greatly appreciated.

Thanks!

---

