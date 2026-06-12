---
title: "Shrew Soft VPN 2.1.7 Release"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by lindleyrl13 on 2011-01-12
Could someone please tell me how to compile Shrew Soft VPN 2.1.7 from source here - [http://www.shrew.net/download/ike](http://www.shrew.net/download/ike) ??

There Ubuntu repo has 2.1.5, but it does not work for the Cisco device I am trying to connect to.  With Windows 7 Ultimate, I can connect using 2.1.7 but not 2.1.5.  

I have not compiled anything from source before so please be a bit detailed - I am confident I can get it compiled with right set of instructions and guidance.

Thank you very much - very new to Ubuntu from MS realm.  Would like to use Ubuntu much more for work and home.

---

### Post by hokiejp on 2011-01-12
First you'll need to make sure you have the appropriate packages installed.  The command below took care of everything I needed.  You may need more depending on what you've built/installed in the past.

> sudo apt-get install cmake libqt3-dev flex bison

Now build and install the program with the following commands.  These will put it in /usr/local.  Change the CMAKE_INSTALL_PREFIX if you don't want it there.

> cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DQTGUI=YES -DETCDIR=/etc -DNATT=YES
make
make install

Additional steps to get it running:

> sudo ldconfig
sudo cp /etc/iked.conf.sample /etc/iked.conf

After that you run it by:

> sudo /usr/local/sbin/iked
/usr/local/bin/ikea

---

### Post by lindleyrl13 on 2011-01-13
Thank you hokiejp, but I received the following error.  Any suggestion?  


vostro@vostro15k:~/Downloads/ike$ cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DQTGUI=YES -DETCDIR=/etc -DNATT=YES
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Using install prefix /usr/local ...
-- Using etc path /etc ...
-- Using lib path /usr/local/lib ...
-- Using man path /usr/local/man ...
CMake Error at CMakeLists.txt:196 (message):
  Unable to locate openssl crypto include files

FIXED first error by:  sudo apt-get install libcurl3-openssl-dev

Next error:  Unable to locate required package : QT

---

### Post by hokiejp on 2011-01-15
try:

> sudo apt-get install libqt3-mt libqt3-mt-dev

that should do it.

---

### Post by lars25700 on 2011-04-21
For me it spits out following error: 

```
-- Install configuration: ""
-- Up-to-date: /usr/local/sbin/iked
CMake Error at source/iked/cmake_install.cmake:45 (FILE):
  file RPATH_REMOVE given FILE "/usr/local/sbin/iked" that does not exist.
Call Stack (most recent call first):
  cmake_install.cmake:37 (INCLUDE)


make: *** [install] Error 1

```

Any ideas for a quick and dirty work around? 

Thanks.

---

### Post by lars25700 on 2011-04-22
Nudge

---

### Post by MadJeff on 2011-05-05
Hitting the same error here, any ideas?

---

### Post by Shikaka on 2011-05-16
> **lars25700 said:**
> For me it spits out following error: 

```
-- Install configuration: ""
-- Up-to-date: /usr/local/sbin/iked
CMake Error at source/iked/cmake_install.cmake:45 (FILE):
  file RPATH_REMOVE given FILE "/usr/local/sbin/iked" that does not exist.
Call Stack (most recent call first):
  cmake_install.cmake:37 (INCLUDE)


make: *** [install] Error 1

```Any ideas for a quick and dirty work around? 

Thanks.



Here is the workaround I used.
```
sudo make install
```

---

### Post by Webnet on 2013-02-19
This thread contains outdated information about libqt3.  I'm needing to set this up as well.  I found resources telling me to setup 

```
sudo apt-get install libqt4-dev
```

but that package wasn't found. Here's my command log:

```
user@ubuntu:~/Programs/ShrewSoft VPN$ cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DQTGUI=YES -DETCDIR=/etc -DNATT=YES
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Using install prefix /usr/local ...
-- Using etc path /etc ...
-- Using lib path /usr/local/lib ...
-- Using man path /usr/local/man ...
-- Using binary /usr/bin/flex ...
-- Using binary /usr/bin/bison ...
-- Enabled NAT Traversal support ...
-- Could NOT find Qt3 (missing:  QT_QT_LIBRARY QT_INCLUDE_DIR QT_MOC_EXECUTABLE) 
CMake Error at CMakeLists.txt:423 (message):
  Unable to locate required package : QT
```

What package do I need in order to compile Shrewsoft VPN?  One person said I could use
```
sudo apt-get install ike
```
Of course that didn't work either :-\

---

### Post by wildmanne39 on 2013-02-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

