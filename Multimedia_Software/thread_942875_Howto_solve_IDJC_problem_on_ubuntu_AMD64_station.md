---
title: "Howto solve IDJC problem on ubuntu AMD64 station"
date: 2008-10-09
forum: Multimedia Software
---

### Post by zeld on 2008-10-09
Hi all!!! in this howto i explain my solution for working with idjc on ubuntu amd64 station!! Today i've try the binary version of idjc from official repository of ubuntu, and i've get some problem, segmentation fault or program crash. After this i felt to compile the latest vanilla source version of idjc, and i've met other problem. I was somewhat discouraged, but after a thorough search, i found this: 

```
1) [https://bugs.launchpad.net/ubuntu/+source/idjc/+bug/231963](https://bugs.launchpad.net/ubuntu/+source/idjc/+bug/231963)
2) [https://bugs.launchpad.net/ubuntu/+source/idjc/+bug/234916](https://bugs.launchpad.net/ubuntu/+source/idjc/+bug/234916)
```

If you, read all the post u can find "try to install idjc version from debian!" But is not specified the method!! hehehe if u try to install the binary package you met some dependecies problem!!! And now?????? i've try to solve this problem with this procedure, and now idjc with icecast2 work perfectly!! Follow this general procedure:
//
//
//
#Install this package:
```
apt-get install libavcodec1d libavformat1d libavutil1d libflac8, libjack0 libmad0 libogg0 libraw1394-8 libsamplerate0 libshout3 libsndfile1 libspeex1 libtheora0 libvorbis0a libvorbisenc2 libvorbisfile3 ffmpeg lame python-eyed3 make gcc gcc-multilib vorbis-tools checkinstall
```

#Build dependencies:
```
apt-get build-dep idjc

```
#Get the idjc source code and diff from unstable debian repository package:

```
mkdir idjc
cd idjc
wget [http://ftp.de.debian.org/debian/pool/main/i/idjc/idjc_0.7.7.orig.tar.gz](http://ftp.de.debian.org/debian/pool/main/i/idjc/idjc_0.7.7.orig.tar.gz)

wget [http://ftp.de.debian.org/debian/pool/main/i/idjc/idjc_0.7.7-1.diff.gz](http://ftp.de.debian.org/debian/pool/main/i/idjc/idjc_0.7.7-1.diff.gz)

```

#Unpack the package:
```
gunzip  idjc_0.7.7-1.diff.gz
tar -xvzf idjc_0.7.7.orig.tar.gz

```

#join on idjc source directory:
```
cd idjc-0.7.7/

```

#Apply the diff:
```
patch  -p1 < ../idjc_0.7.7-1.diff

```

#Now u can compile the source package!!! If u want optimize the code of idjc on configure phase u can add some cflags, cxxflags. Follow this link for get your appropriate cflags,cxxflags [http://gentoo-wiki.com/Safe_Cflags]("http://gentoo-wiki.com/Safe_Cflags")
In my case, i've and AMD Turion 64 ML-32, and i've use:
```

CFLAGS="-march=k8 -msse3 -O2 -pipe" CXXFLAGS="${CFLAGS}" ./configure
```

#Make the source code:

```
make 

```

#Create binary package with checkinstall

```
checkinstall >> Follow checkinstall instruction
```


End

Good stream with idjc and icecast2!!! :guitar:

zeld :KS

---

