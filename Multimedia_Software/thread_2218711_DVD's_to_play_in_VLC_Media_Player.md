---
title: "DVD's to play in VLC Media Player"
date: 2014-04-21
forum: Multimedia Software
---

### Post by edward_anthony on 2014-04-21
I am using Ubuntu 10.04 on an Acer desktop and need help getting DVD's to play in VLC. Please help if you can. Thank you kindly.

---

### Post by jacob21 on 2014-04-21
You need to install libdvdcss.

```
sudo apt-get install libdvdcss
```

---

### Post by monkeybrain20122 on 2014-04-21
Ubuntu 10.04 has been dead for over a year. You should make a clean install of a supported release.

---

### Post by monkeybrain20122 on 2014-04-21
> **jacob21 said:**
> You need to install libdvdcss.

```
sudo apt-get install libdvdcss
```

I gather that you never watch dvd on Ubuntu? That command does not work. First the package is called libdvdcss2, secondly it is not in the repository.

---

### Post by ibjsb4 on 2014-04-21
Don't forget to setup libdvdread on that fresh install :)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss)

---

### Post by Yellow Pasque on 2014-04-22
> **monkeybrain20122 said:**
> Ubuntu 10.04 has been dead for over a year. You should make a clean install of a supported release.

Lucid still receives security updates and it is still supported. Some users prefer waiting as long as possible to upgrade, especially when newer versions of Ubuntu use a very different interface by default...

---

### Post by edward_anthony on 2014-04-22
Thank you for the help so far. It does play but there distortions. The picture is pixilated and the sound is choppy with random static here and there. Is there a fix for this?

---

