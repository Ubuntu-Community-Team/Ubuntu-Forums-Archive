---
title: "Mythtv package install problem with dependencies"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by kn33bz on 2007-07-13
When using synaptic on feisty the following is the output when checking the backend for installation.  Any pointers as to what I am doing or have wrong.

Thanks



mythtv-backend:
  Depends: libasound2 (>1.0.14) but 1.0.13-1ubuntu5 is to be installed
  Depends: libc6 (>=2.5-5) but 2.5-0ubuntu14 is to be installed
  Depends: libgcc1 (>=1:4.2-20070516) but 1:4.1.2-0ubuntu4 is to be installed
 Depends: libjack0 (>=0.103.0) but it is not installable
 Depends: libmyth-0.20 but it is not going to be installed
  Depends: libstdc++6 (>=4.2-20070516) but 4.1.2-0ubuntu4 is to be installed
 Depends: transcode but it is not going to be installed

---

### Post by tgm4883 on 2007-07-13
Did you add the multiverse to your sources.list then apt-get update?

---

### Post by kn33bz on 2007-07-13
Hi, thanks for the reply.
here are all the uncommented lines from my apt  sources.list. I added a few things during my attempts to resolve this. I am not a newby to linux although relatively new to Ubuntu. I have used an FC2 workstation for over 12 months then to FC6 then I discovered Ubuntu ( finally took a look at it after hearing of it for a while. ---sold on it.)
I use a centos 4.5 server and the command line is no enemy to me. 
I thought I would ask here to see if I had missed something obvious before I go back to square 1 and start over.
Synaptic , apt-get and aptitude all indicate the same issues.





deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe #Added by software-properties
deb-src [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main

---

### Post by tgm4883 on 2007-07-13
Do 
sudo apt-get update
then try installing it again and see if you get the same error.

---

### Post by kn33bz on 2007-07-14
I have done this also sudo aptitude update and reload via synaptic.

 This is the problem, the updates have been done and still the package management is reporting these version mismatches. This is why I thought it was something simple I was missing as I have not had this issue with any other packages. It looks to me like the generic named versions are being expected but the Ubuntu named versions are being supplied. Without knowledge of how these dependencies are specified I am at a disadvantage and hence am posting here.
 I will build it from the tarball packages if I have to but I did want a straight forward method as I likely will be doing this more than once.

---

### Post by tgm4883 on 2007-07-14
> **kn33bz said:**
> Hi, thanks for the reply.
here are all the uncommented lines from my apt  sources.list. I added a few things during my attempts to resolve this. I am not a newby to linux although relatively new to Ubuntu. I have used an FC2 workstation for over 12 months then to FC6 then I discovered Ubuntu ( finally took a look at it after hearing of it for a while. ---sold on it.)
I use a centos 4.5 server and the command line is no enemy to me. 
I thought I would ask here to see if I had missed something obvious before I go back to square 1 and start over.
Synaptic , apt-get and aptitude all indicate the same issues.





deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe #Added by software-properties
deb-src [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main

Why do you have debian-multimedia in repos in there?

---

### Post by kn33bz on 2007-07-14
I spent quite some time trying to get MythTV installed running before ending up here. This was mentioned on one of the sites with a supposed howto on Ubuntu. If you think this is causing confusion for the system, well that's the type of thing I thought might be going on and the advice I am seeking here. 

I have just removed it via synaptic and it appears OK and is installing as we "speak"

makes sense though with hind sight considering my statement on generic named versions.

Thanks for the replies.

---

### Post by tgm4883 on 2007-07-14
Glad its working.
In case you need a good guide, this one is the best I know of.
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

