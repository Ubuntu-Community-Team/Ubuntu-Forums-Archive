---
title: "how install FFMPEG, FLVTOOL2, MENCODER, GD, FREETYPE,"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by etusha on 2008-03-09
hello all
i have vps (with plesk) i need to install FFMPEG, FLVTOOL2, MENCODER, GD, FREETYPE,

---

### Post by stooshbunutu on 2008-03-11
in terminal

```
sudo apt-get install ffmpeg flvtool2 mencoder gd freetype
```

Assuming they are all ubuntu software

---

### Post by etusha on 2008-03-11
sudo apt-get install gd
E: Couldn't find package gd
======================
sudo apt-get install flvtool2
E: Couldn't find package flvtool2
no problem for flvtools2 i can install it manually

---

### Post by stooshbunutu on 2008-03-11
had a little search:

did you mean *libgd* or did *php5-gd* or is it an actual program called gd

---

### Post by etusha on 2008-03-11
libgd
i think the right command is 
apt-get install libgd-dev

???

---

### Post by stooshbunutu on 2008-03-11
yup that'l do it

---

### Post by etusha on 2008-03-13
it tells me that i need more soruce.list
i have

Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper

---

### Post by stooshbunutu on 2008-03-13
> **etusha said:**
> it tells me that i need more soruce.list
i have

Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper

can u copy/paste the out put from terminal when you try it please

---

### Post by etusha on 2008-03-14
it show me
>  apt-get build-dep ffmpeg
Reading package lists... Done
Building dependency tree... Done
E: You must put some 'source' URIs in your sources.list


im trying to instaling ffmpeg in this way 
[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

---

### Post by etusha on 2008-03-15
i have add some line in soruce.list
but ut show me 
> sudo apt-get build-dep ffmpeg
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for ffmpegcvs


---

### Post by stooshbunutu on 2008-03-18
Try doing it from [here]("http://packages.ubuntu.com/gutsy/ffmpeg") with seperate dependencies, length but works

---

