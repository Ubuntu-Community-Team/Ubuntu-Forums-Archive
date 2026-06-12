---
title: "Intel WiMax 5150/5350 Ubuntu 9.10 64bit (x86_64) &quot;Karmic&quot; works!"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by prokher on 2009-12-16
1. Make your ubuntu up-to-date and install necessary packages.
```

      # update & upgrade ubuntu
      sudo aptitude update
      sudo aptitude full-upgrade

      # dependencies
      sudo aptitude install build-essential ia32-libs linux-headers libnl-dev

      # library libnl 32bit version manual installation
      wget [http://mirrors.kernel.org/ubuntu/pool/main/libn/libnl/libnl1_1.1-5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libn/libnl/libnl1_1.1-5_i386.deb)
      ar vx libnl1_1.1-5_i386.deb
      tar -xzvf data.tar.gz
      sudo cp ./usr/lib/libnl.so.1.1 /usr/lib32/
      sudo ln -s libnl.so.1.1 /usr/lib32/libnl.so.1
      sudo ln -s libnl.so.1.1 /usr/lib32/libnl.so
      ldconfig

```
   2. Download WiMAX Network Service 1.4.0 from  [http://linuxwimax.org/Download](http://linuxwimax.org/Download) 

   3. Extract files from archive
```

      tar xjf WiMAX-Network-Service-1.4.0.tar.bz2
      cd WiMAX-Network-Service-1.4.0/

```
   4. Build & Install
```

      # configure
      CFLAGS=-m32 ./configure --sysconfdir=/etc --localstatedir=/var --mandir=/usr/share/man prefix=/usr/local --with-i2400m=/usr/src/linux-headers-`uname -r` --build=i386
      # do kung fu :)
      for i in `rgrep CFLAGS\ = . | grep -i makefile | grep O2 | sed -r "s/([^:]*):.*/\1/g"`; do sed -i "s/CFLAGS = -O2/CFLAGS = -O2 -m32/g" $i; done
      # build
      make all
      # install
      sudo make install

```
   5. Yota (russian wimax provider) specifig configs.
```

      wget [http://icelord.net/images/wimax/NDnSAgentConfig_forDriver.xml](http://icelord.net/images/wimax/NDnSAgentConfig_forDriver.xml)
      wget [http://icelord.net/images/wimax/NDnSAgentDefaultConfig.xml](http://icelord.net/images/wimax/NDnSAgentDefaultConfig.xml)
      sudo cp NDnSAgent* /usr/local/share/wimax/

```

   6. Start it!
```

      sudo service wimax start
      # check service
      sudo wimaxcu status
      # turn radio on
      sudo wimaxcu ron
      # scan networks just to make sure that Yota is here
      sudo wimaxcu scan
      # connect to yota network
      sudo wimaxcu connect network 15

```
Links:
    * [http://blog.brainbean.org/blog/prokher_2009.12.12_08.32.08](http://blog.brainbean.org/blog/prokher_2009.12.12_08.32.08)
    *  [http://icelord.net/wordpress/archives/1151](http://icelord.net/wordpress/archives/1151)
    *  [http://lists.linuxwimax.org/pipermail/wimax/2009-December/000671.html](http://lists.linuxwimax.org/pipermail/wimax/2009-December/000671.html)
    *  [http://linuxwimax.org/](http://linuxwimax.org/)

---

### Post by Le[Men] on 2009-12-16
Ok, It looks like it works for me.

---

### Post by jclb111181 on 2010-10-03
I am trying to configure my laptop to work with Clear wimax.  When I try to compile with the commands that you supplied, I get the following error message.  Any ideas how to fix?  Thanks for any help you can provide.

john@ubuntu:~/WiMAX-Network-Service-1.4.0$ CFLAGS=-m32 ./configure --sysconfdir=/etc --localstatedir=/var --mandir=/usr/share/man prefix=/usr/local --with-i2400m=/usr/src/linux-headers-`uname -r` --build=i386
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

