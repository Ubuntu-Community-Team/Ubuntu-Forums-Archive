---
title: "Trying to undo an oss4 install"
date: 2008-07-05
forum: Multimedia Software
---

### Post by hyunkell on 2008-07-05
I installed oss4 some days ago, worked fine, except for my headset, which I couldn't get the mic to work at all.

I liked it but I can't live without my headset, so back to alsa and oss3.
And exactly here is my problem, I can't find any package that would install oss3 for me again, and the installer fails:

[http://oss.pastebin.com/mfd1011](http://oss.pastebin.com/mfd1011)

Now please correct me if I understand it all wrong, but without oss3 I won't be able to use any soundcard at all right?

> aplay -l
aplay: device_list:205: no soundcards found...

I also tried reinstalling alsa from packages and from source, but that didn't help at all.

Edit: solved the problem
had to modprobe my sound drivers and alsa started working again.
I also misunderstood how oss and alsa work, I always was under the impression that alsa is some kind of layer over oss, which is why I wanted to install oss3.

During boot I get alot of errors about all possible sound drivers, and then it tells me it can't load oss3.

sudo dpkg-reconfigure alsa-source is set to use alsa.

So... yeah, I'm totally lost, and I don't exactly understand the sound systems of linux either.
If I understand correctly, without oss, I won't have any soundcards in /dev/dsp, and without a soundcard alsa won't work.

Any ideas how to get my sound back to default on ubuntu 8.04?

Thanks,
hyu

---

