---
title: "No sound in Ubuntu 10.04"
date: 2010-07-29
forum: Multimedia Software
---

### Post by wand_maker on 2010-07-29
I have just installed Ubuntu 10.04 on a dell inspiron 9400 (the sound card is Intel Corporation N10/ICH 7 Family High Definition Audio Controller), but there is no sound through speakers, although there is with headphones. Here is what I have tried after reading some posts:

[http://docs.google.com/gview?a=v&pid=explorer&chrome=true&api=true&srcid=0B9-qm2qpYZI1YWU4YTUwY2YtZTA1NS00OGI3LTg5ZjgtN2ZkZWUwODAyZjc2&hl=es](http://docs.google.com/gview?a=v&pid=explorer&chrome=true&api=true&srcid=0B9-qm2qpYZI1YWU4YTUwY2YtZTA1NS00OGI3LTg5ZjgtN2ZkZWUwODAyZjc2&hl=es)

any ideas why is still not working?

---

### Post by ricardo.gloe on 2010-07-29
I have Ubuntu 10.04 on a Sony Vaio VPCF111FB, and had the same issue. No sound through speakers, headphones working. The only way I could fix the sound was downloading and replacing the kernel with the latest lucid version from [HTML]http://kernel.ubuntu.com/~kernel-ppa/mainline/[/HTML]

Fortunately, that worked, although boot time was just a little bit longer, nothing unbearable.

---

### Post by lidex on 2010-08-01
How about these outputs:
```
uname -a
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
sudo dmidecode -t bios
sudo dmidecode -t baseboard
```

---

### Post by ooganblat on 2010-11-17
I have sound on mine, but the media controls for the volume only control (what sounds like) the treble. Pretty weird...

---

