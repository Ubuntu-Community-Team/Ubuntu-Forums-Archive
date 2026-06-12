---
title: "[SOLVED] How Can I To Convert .iso file to .mkv format?"
date: 2016-03-22
forum: Multimedia Software
---

### Post by jooge on 2016-03-22
Hi folks, I'm in search of an easy way to convert some .iso files I have to .mkv format. I tried tutorials using handbrake that I found online but for some odd reason they did not work correctly. I would highly prefer a program if there is one out there with a GUI as I am still not too confident in using command line apps. I'm still a bit of a noob ;)

Thank you

---

### Post by T.J. on 2016-03-22
> **jooge said:**
> Hi folks, I'm in search of an easy way to convert some .iso files I have to .mkv format. I tried tutorials using handbrake that I found online but for some odd reason they did not work correctly. I would highly prefer a program if there is one out there with a GUI as I am still not too confident in using command line apps. I'm still a bit of a noob ;)

Thank you

As much as I truly want to help you, your question is too general to answer specifically without more information, such as what kind of data is in the ISO.  If you include more details, it is far more likely that myself or someone can provide the answer you need.  I'm happy to try if you can explain a bit more please. =)

If the ISO images are of commercial DVDs or Blu-Rays, then I am sorry, but no one on the forums is allowed to help you. That would probably be violating copyright law in some way.  We aren't permitted to discuss such things here in the forums under the Terms of Service.

---

### Post by jooge on 2016-03-24
Oh ok. Well the iso came from a dvd that I bought a few yrs ago legit, but if it cant be done, plz disregard this thread then.

---

### Post by howefield on 2016-03-24
Try this thread..

[http://ubuntuforums.org/showthread.php?t=2102902](http://ubuntuforums.org/showthread.php?t=2102902)

---

### Post by jooge on 2016-03-26
> **howefield said:**
> Try this thread..

[http://ubuntuforums.org/showthread.php?t=2102902](http://ubuntuforums.org/showthread.php?t=2102902)

Just want I needed. Thank you kindly howefield :D

---

### Post by jooge on 2016-03-26
> **howefield said:**
> Try this thread..

[http://ubuntuforums.org/showthread.php?t=2102902](http://ubuntuforums.org/showthread.php?t=2102902)


In comment #8 on this link ^^^ They have a link where you can install MakeMKV. Here is what they say and where I get stuck:

Download [COLOR=#FF0000]**both**[/COLOR] binary and source packages:
[http://www.makemkv.com/download/makemkv-bin-1.9.9.tar.gz](http://www.makemkv.com/download/makemkv-bin-1.9.9.tar.gz)
[http://www.makemkv.com/download/makemkv-oss-1.9.9.tar.gz](http://www.makemkv.com/download/makemkv-oss-1.9.9.tar.gz)

Make  sure you have all required tools and libraries installed. You'll need  GNU compiler and linker and header and library files for following  libraries: glibc, openssl-0.9.8, zlib, expat, libavcodec, qt4 or qt5.  You may use the following command to install all prerequisites on  debian-based system like ubuntu:


```
sudo apt-get install build-essential pkg-config libc6-dev libssl-dev libexpat1-dev libavcodec-dev libgl1-mesa-dev libqt4-dev


```
Unpack both packages and starting from source package do the following steps:
For makemkv-oss package:

```
./configure
make
sudo make install
```


For makemkv-bin package:

```
make
sudo make install


```

The application will be installed as "/usr/bin/makemkv". 
-----------------------------------------------------------------------------------------------------

Now, I installed the essential packages via terminal & also downloaded the 2 source pakages (.tar.gz) and extracted them. Being on the lower end of Linux know-how myself, I am stuck on:

For makemkv-oss package:

```
./configure
make
sudo make install
```


For makemkv-bin package:

```
make
sudo make install


```

Little help pretty please :)

---

### Post by jooge on 2016-03-27
Figured it out \\:D/

---

