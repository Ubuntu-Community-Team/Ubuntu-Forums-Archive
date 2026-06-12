---
title: "libdvdcss Troubles..."
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by joshtruction on 2006-11-13
I have been using Ubuntu 6.06 for the past few months and have been greatly enjoying it. It's been a little tough sometimes getting things to work, but so far everything's going well. That is, except for DVD playback. I have been trying desperatly to get purchased DVDs to play in any media player. I have downloaded them all in hopes that one may magically work for no real reason. I have installed libdvdread from the package manager. I am just having trouble installing libdvdcss. I have downloaded a ".deb" file for this package, but when I attempt to run it, I get the error message in Package Installer "Error: Dependency is not satisfiable: libdvdcss2". I have also attempted to install it in the terminal, but I receive the following

```
 sudo  /usr/share/doc/libdvdread3/examples/install-css.sh
Password:
Error parsing proxy URL http://:8080/: Invalid host name.

```

Please Ubuntu Community! I beg of you! Help me out with this. It's the last thing I need before my computer is essentailly perfect for me. Thank you. 

Also, it would help if any explainations were explained as if I knew very little or nothing at all about Ubuntu as to make it as clear as possible. 

Tha

-Joshtruction

---

### Post by ape on 2006-11-13
Try adding the following into your /etc/apt/sources.list file:

```
## PLF
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
```

Then issue a 'sudo aptitude update'.  You should now be able to install libdvdcss2.

Good luck,

--ape--

---

### Post by joshtruction on 2006-11-13
Wow! Awesome. This fixed it. Also, I had some problems with the pacages I was downloading. Thanks a bunch. You won't be forgotten good sir/ma'am.

-Joshtruction

---

### Post by dorcssa on 2006-12-11
> **ape said:**
> Try adding the following into your /etc/apt/sources.list file:

```
## PLF
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
```

Then issue a 'sudo aptitude update'.  You should now be able to install libdvdcss2.

Good luck,

--ape--

I've added this repo to my sources.list, updated synaptic, ang get this:

```
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.bz2: bzip2 alfolyamat hibakóddal tért vissza (2)
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.bz2: bzip2 alfolyamat hibakóddal tért vissza (2)
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.bz2: bzip2 alfolyamat hibakóddal tért vissza (2)
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.bz2: bzip2 alfolyamat hibakóddal tért vissza (2)
http://hu.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: gzip alfolyamat hibakóddal tért vissza (1)
```
Means in english( closely): bzip2/gzip subprocess returns with an error code. 

And than when I close it: 

```
W: GPG error: http://packages.freecontrib.org dapper Release: Ismeretlen hiba a gpgv végrehajtása közben.
W: GPG error: http://kubuntu.org dapper Release: A következ&#337; aláírásaok nem ellen&#337;rizhet&#337;ek, mivel a nyilvános kulcs nem érhet&#337; el: NO_PUBKEY A506E6D4DD4D5088

``` Unknown error during gpgv for the first one, and the second one complaining about the signature and the public key. I hope you can at least understand my problem. :D

---

### Post by dorcssa on 2006-12-11
Nobody can help me? Well, I have a normal dvd player, so it's not a big problem, but it'd be good to see my dvd's on my pc too.

---

### Post by eeried on 2006-12-29
Try adding this line to your source list-- this is the updated PLF repository

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

then  the PUBkey hitch:

 ```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Now ```
sudo apt-get update
```
then ```
sudo apt-get install libdvdcss libdvdcss2
```

NB: I'm not sure which you need libdvdcss or libdvdcss2? can someone tell us the difference (region?).

If you read the official help you'll see that there's a script that does it all for you.

---

### Post by dorcssa on 2006-12-29
I've already solved my problem and managed to install libdvdcss2. Somehow the repos started to work. But thanks for an other tip though, I appreciate it very much. :)

---

### Post by j0e_x on 2007-01-17
thanks everyone--this was so helpful to me! works a charm. joe
Toshiba Satellite 1000
Xubuntu 6.10
256 meg ram!
runs great.

---

