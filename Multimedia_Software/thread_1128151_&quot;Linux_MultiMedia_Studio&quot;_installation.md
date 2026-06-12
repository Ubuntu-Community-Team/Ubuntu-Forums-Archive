---
title: "&quot;Linux MultiMedia Studio&quot; installation"
date: 2009-04-17
forum: Multimedia Software
---

### Post by jl2035 on 2009-04-17
The archive 'lmms-0.4.3.tar.bz2' contains 'configure' file so I thought the installation would be normal(./configure, make, make install,...), but it doesn't work. When I type ./configure I get the folowing output:

```

Usage of configure & Co is deprecated! Please use 

    cmake . -DCMAKE_INSTALL_PREFIX=/usr  

or similiar instead.
```

The program was downloaded from [HERE]("http://linux.softpedia.com/progDownload/Linux-MultiMedia-Studio-Download-3149.html")

Any ideas?

---

### Post by mc4man on 2009-04-17
Probably

```
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
```

this ppa has current .debs (intrepid, hardy, if so then add the ppa to your sources
[https://launchpad.net/~tobydox/+archive/ppa](https://launchpad.net/~tobydox/+archive/ppa)

Thread about building on hardy
[http://ubuntuforums.org/showthread.php?t=1046909](http://ubuntuforums.org/showthread.php?t=1046909)

---

### Post by jl2035 on 2009-04-17
I solved the problem!

```
mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
```

now I needed to install libsndfile1 and removed the CMakeLists.txt file.

```
sudo apt-get install libsndfile1-dev
cd ..
rm CMakeLists.txt
cd build

```

and now cmake again

```
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
make
sudo make install 
```

Thanks for help!

---

