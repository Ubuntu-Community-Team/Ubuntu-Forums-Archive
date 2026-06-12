---
title: "Codecs..."
date: 2008-06-12
forum: Multimedia Software
---

### Post by ultimate_aektzis on 2008-06-12
Hi guys.I just want to make a simple question.How can I download all the existing codecs so that I can play every media file type on my pc??
Thanks in advance:)

---

### Post by kdcoetzee on 2008-06-12
If you go to Add/Remove... and install "Ubuntu restricted extras"
And for dvd support you need to install libdvdcss2

sudo apt-get install libdvdcss2

you will need Medibuntu repository for that package.

you can get it on the Ubuntu site[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by ultimate_aektzis on 2008-06-13
Just to verify.Firts of all
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

then

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

```
sudo apt-get install libdvdcss2
```

I have had already installed Ubuntu restricted areas...
Thanks for your help Juggernaut_KDC

---

### Post by kdcoetzee on 2008-06-13
Yes the first one added the repository to your sources.list

the second one ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

first updates your index of all the available packages. then you install medibuntu-keyring which is the GPG key. which is security.

libdvdcss2 is support for dvd's

then you need to run this command as well, it added the non-free codec.

```
sudo apt-get install w32codecs
```

But i think it is already install tru the Ubuntu restricted extras.

---

### Post by Joeb454 on 2008-06-13
I think you're correct - w32codecs does get installed with ubuntu-restricted-extras :)

At least I've never specifically installed w32codecs, but have never had any issues playing .wmv files if I ever get them :)

---

