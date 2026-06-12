---
title: "Trouble updating alsa"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by Anarchy965 on 2007-08-31
I tried updating alsa using the following steps:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
sudo ./configure
sudo make
sudo make install
```

I did it one step at a time and when I did "sudo ./configure" It said:
```
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

What should I do now?

---

### Post by ddrichardson on 2007-08-31
Do```

sudo apt-get install build-essential
```. Then Try again.

---

