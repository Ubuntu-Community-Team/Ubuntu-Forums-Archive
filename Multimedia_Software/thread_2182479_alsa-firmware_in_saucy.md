---
title: "alsa-firmware in saucy"
date: 2013-10-21
forum: Multimedia Software
---

### Post by jaddle on 2013-10-21
I have a tascam us-122 USB sound module which requires some non-free firmware. I used to use the alsa-firmware package from medibuntu, but now that has been shut down. Is this firmware available in another repository somewhere? I could just install the files manually from alsa, but I'd rather have it handled in a proper .deb, for obvious reasons.

Thanks!

---

### Post by jaddle on 2013-10-21
To clarify - there's an alsa-firmware-loader package, but this only has the binaries used to upload the firmwares to the devices. The actual firmware is in the alsa-firmware package, which used to be provided by medibuntu. Now, it seems that the only way to get it is by downloading the .tar.bz2 from alsa-project.org,and unzipping it. I'd rather have a maintained .deb if one is available though.

---

### Post by Yellow Pasque on 2013-10-21
There's always checkinstall utility to easily make your own .deb package..

```
sudo apt-get install checkinstall
./configure
make
sudo checkinstall make install
```

---

### Post by jaddle on 2013-10-26
Keep in mind that 'make install' will put the files into /usr/local. I expect 'sudo checkinstall make install --prefix=/usr' would make a package with more normal paths, though I ended up just installing to /usr/local/ and then making a symlink.

Note that there are other bugs with the alsa-firmware-loaders package it seems - [https://bugs.launchpad.net/ubuntu/+source/alsa-tools/+bug/1245096](https://bugs.launchpad.net/ubuntu/+source/alsa-tools/+bug/1245096) explains it, including a workaround.

---

