---
title: "Mythvodka error"
date: 2009-03-31
forum: Mythbuntu
---

### Post by davidstoll on 2009-03-31
I see that this question was asked in another post, but the direction of the thread has forked a bit.  Plus, there have been some changes since then.

Basically, I'm trying to install mythvodka.

```
$ sudo make
cd mythvodka && make -f Makefile
make[1]: Entering directory `/usr/lib/mythtv/plugins/mythvodka/mythvodka'
make[1]: *** No rule to make target `/usr/qt/3/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.
make[1]: Leaving directory `/usr/lib/mythtv/plugins/mythvodka/mythvodka'
make: *** [sub-mythvodka] Error 2
```

I can't get past this step.  I'm using 8.10
I'm using this page as a guide...
[http://www.mythtv.org/wiki/MythStreams](http://www.mythtv.org/wiki/MythStreams)

---

### Post by azmyth on 2009-03-31
$cd mythvodka
$qmake mythvodka.pro
$make
$sudo make install

---

### Post by davidstoll on 2009-03-31
> **azmyth said:**
> $cd mythvodka
$qmake mythvodka.pro
$make
$sudo make install

```
$ cd mythvodka/
david@MythBuntu:~/temp/mythvodka/mythvodka$ qmake mythvodka.pro 
david@MythBuntu:~/temp/mythvodka/mythvodka$ make
cd mythvodka && make -f Makefile
make[1]: Entering directory `/home/david/temp/mythvodka/mythvodka/mythvodka'
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT -fPIC  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o main.o main.cpp
main.cpp:1:32: error: mythtv/mythcontext.h: No such file or directory
main.cpp:2:30: error: mythtv/mythdbcon.h: No such file or directory
main.cpp:3:34: error: mythtv/mythpluginapi.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:4:32: error: mythtv/mythdialogs.h: No such file or directory
In file included from main.cpp:6:
streamssettings.h:4:29: error: mythtv/settings.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:13: error: expected class-name before \u2018{\u2019 token
streamsui.h:14: error: ISO C++ forbids declaration of \u2018Q_OBJECT\u2019 with no type
streamsui.h:15: error: expected \u2018;\u2019 before \u2018public\u2019
streamsui.h:18: error: expected `)' before \u2018*\u2019 token
streamsui.h:23: error: \u2018QKeyEvent\u2019 has not been declared
streamsui.h:32: error: ISO C++ forbids declaration of \u2018GenericTree\u2019 with no type
streamsui.h:32: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:33: error: ISO C++ forbids declaration of \u2018GenericTree\u2019 with no type
streamsui.h:33: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:35: error: \u2018QDomNode\u2019 has not been declared
streamsui.h:36: error: \u2018QDomNode\u2019 has not been declared
streamsui.h:43: error: ISO C++ forbids declaration of \u2018GenericTree\u2019 with no type
streamsui.h:43: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:44: error: ISO C++ forbids declaration of \u2018UIManagedTreeListType\u2019 with no type
streamsui.h:44: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:45: error: ISO C++ forbids declaration of \u2018GenericTree\u2019 with no type
streamsui.h:45: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:50: error: ISO C++ forbids declaration of \u2018MSqlQuery\u2019 with no type
streamsui.h:50: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:51: error: ISO C++ forbids declaration of \u2018MSqlQuery\u2019 with no type
streamsui.h:51: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:52: error: ISO C++ forbids declaration of \u2018MSqlQuery\u2019 with no type
streamsui.h:52: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:56: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:56: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:57: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:57: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:58: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:58: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:59: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:59: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:60: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:60: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:61: error: ISO C++ forbids declaration of \u2018UIImageType\u2019 with no type
streamsui.h:61: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:62: error: ISO C++ forbids declaration of \u2018MythPopupBox\u2019 with no type
streamsui.h:62: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:63: error: ISO C++ forbids declaration of \u2018MythPopupBox\u2019 with no type
streamsui.h:63: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:64: error: ISO C++ forbids declaration of \u2018MythPopupBox\u2019 with no type
streamsui.h:64: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:65: error: ISO C++ forbids declaration of \u2018QButton\u2019 with no type
streamsui.h:65: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:66: error: ISO C++ forbids declaration of \u2018QButton\u2019 with no type
streamsui.h:66: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:71: error: expected `:' before \u2018slots\u2019
streamsui.h:72: error: expected primary-expression before \u2018void\u2019
streamsui.h:72: error: ISO C++ forbids declaration of \u2018slots\u2019 with no type
streamsui.h:72: error: expected \u2018;\u2019 before \u2018void\u2019
streamsui.h:73: error: \u2018IntVector\u2019 has not been declared
streamsui.h:75: error: expected `:' before \u2018slots\u2019
streamsui.h:76: error: expected primary-expression before \u2018void\u2019
streamsui.h:76: error: ISO C++ forbids declaration of \u2018slots\u2019 with no type
streamsui.h:76: error: expected \u2018;\u2019 before \u2018void\u2019
In file included from main.cpp:6:
streamssettings.h:7: error: expected class-name before \u2018{\u2019 token
main.cpp:10: error: expected constructor, destructor, or type conversion before \u2018*\u2019 token
main.cpp: In function \u2018int mythplugin_init(const char*)\u2019:
main.cpp:20: error: \u2018gContext\u2019 was not declared in this scope
main.cpp:21: error: \u2018MYTH_BINARY_VERSION\u2019 was not declared in this scope
main.cpp:23: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
main.cpp:24: error: \u2018VERBOSE\u2019 was not declared in this scope
main.cpp:30: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
main.cpp:31: error: \u2018VERBOSE\u2019 was not declared in this scope
main.cpp: In function \u2018void runStreams()\u2019:
main.cpp:40: error: \u2018gContext\u2019 was not declared in this scope
streamsui.h:20: error: \u2018StreamsUI::~StreamsUI()\u2019 is private
main.cpp:41: error: within this context
main.cpp:42: error: \u2018class StreamsUI\u2019 has no member named \u2018exec\u2019
main.cpp: In function \u2018void runConfig()\u2019:
main.cpp:49: error: \u2018class StreamsSettings\u2019 has no member named \u2018exec\u2019
main.cpp: In function \u2018int mythplugin_run()\u2019:
main.cpp:54: error: \u2018gContext\u2019 was not declared in this scope
main.cpp:61: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
main.cpp:62: error: \u2018VERBOSE\u2019 was not declared in this scope
main.cpp: In function \u2018int setupDatabase()\u2019:
main.cpp:81: error: \u2018gContext\u2019 was not declared in this scope
main.cpp:84: error: \u2018gContext\u2019 was not declared in this scope
main.cpp:86: error: \u2018VB_GENERAL\u2019 was not declared in this scope
main.cpp:86: error: \u2018VERBOSE\u2019 was not declared in this scope
main.cpp:88: error: \u2018MSqlQuery\u2019 was not declared in this scope
main.cpp:88: error: expected `;' before \u2018query\u2019
main.cpp:89: error: \u2018query\u2019 was not declared in this scope
main.cpp:122: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
main.cpp:134: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/david/temp/mythvodka/mythvodka/mythvodka'
make: *** [sub-mythvodka] Error 2
david@MythBuntu:~/temp/mythvodka/mythvodka$ sudo make install
( [ -d mythvodka ] && cd mythvodka ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d mythvodka ] && cd mythvodka ; make -f Makefile install; ) || true
make[1]: Entering directory `/home/david/temp/mythvodka/mythvodka/mythvodka'
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT -fPIC  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o main.o main.cpp
main.cpp:1:32: error: mythtv/mythcontext.h: No such file or directory
main.cpp:2:30: error: mythtv/mythdbcon.h: No such file or directory
main.cpp:3:34: error: mythtv/mythpluginapi.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:4:32: error: mythtv/mythdialogs.h: No such file or directory
In file included from main.cpp:6:
streamssettings.h:4:29: error: mythtv/settings.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:13: error: expected class-name before \u2018{\u2019 token
streamsui.h:14: error: ISO C++ forbids declaration of \u2018Q_OBJECT\u2019 with no type
streamsui.h:15: error: expected \u2018;\u2019 before \u2018public\u2019
streamsui.h:18: error: expected `)' before \u2018*\u2019 token
streamsui.h:23: error: \u2018QKeyEvent\u2019 has not been declared
streamsui.h:32: error: ISO C++ forbids declaration of \u2018GenericTree\u2019 with no type
streamsui.h:32: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:33: error: ISO C++ forbids declaration of \u2018GenericTree\u2019 with no type
streamsui.h:33: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:35: error: \u2018QDomNode\u2019 has not been declared
streamsui.h:36: error: \u2018QDomNode\u2019 has not been declared
streamsui.h:43: error: ISO C++ forbids declaration of \u2018GenericTree\u2019 with no type
streamsui.h:43: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:44: error: ISO C++ forbids declaration of \u2018UIManagedTreeListType\u2019 with no type
streamsui.h:44: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:45: error: ISO C++ forbids declaration of \u2018GenericTree\u2019 with no type
streamsui.h:45: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:50: error: ISO C++ forbids declaration of \u2018MSqlQuery\u2019 with no type
streamsui.h:50: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:51: error: ISO C++ forbids declaration of \u2018MSqlQuery\u2019 with no type
streamsui.h:51: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:52: error: ISO C++ forbids declaration of \u2018MSqlQuery\u2019 with no type
streamsui.h:52: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:56: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:56: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:57: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:57: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:58: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:58: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:59: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:59: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:60: error: ISO C++ forbids declaration of \u2018UITextType\u2019 with no type
streamsui.h:60: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:61: error: ISO C++ forbids declaration of \u2018UIImageType\u2019 with no type
streamsui.h:61: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:62: error: ISO C++ forbids declaration of \u2018MythPopupBox\u2019 with no type
streamsui.h:62: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:63: error: ISO C++ forbids declaration of \u2018MythPopupBox\u2019 with no type
streamsui.h:63: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:64: error: ISO C++ forbids declaration of \u2018MythPopupBox\u2019 with no type
streamsui.h:64: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:65: error: ISO C++ forbids declaration of \u2018QButton\u2019 with no type
streamsui.h:65: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:66: error: ISO C++ forbids declaration of \u2018QButton\u2019 with no type
streamsui.h:66: error: expected \u2018;\u2019 before \u2018*\u2019 token
streamsui.h:71: error: expected `:' before \u2018slots\u2019
streamsui.h:72: error: expected primary-expression before \u2018void\u2019
streamsui.h:72: error: ISO C++ forbids declaration of \u2018slots\u2019 with no type
streamsui.h:72: error: expected \u2018;\u2019 before \u2018void\u2019
streamsui.h:73: error: \u2018IntVector\u2019 has not been declared
streamsui.h:75: error: expected `:' before \u2018slots\u2019
streamsui.h:76: error: expected primary-expression before \u2018void\u2019
streamsui.h:76: error: ISO C++ forbids declaration of \u2018slots\u2019 with no type
streamsui.h:76: error: expected \u2018;\u2019 before \u2018void\u2019
In file included from main.cpp:6:
streamssettings.h:7: error: expected class-name before \u2018{\u2019 token
main.cpp:10: error: expected constructor, destructor, or type conversion before \u2018*\u2019 token
main.cpp: In function \u2018int mythplugin_init(const char*)\u2019:
main.cpp:20: error: \u2018gContext\u2019 was not declared in this scope
main.cpp:21: error: \u2018MYTH_BINARY_VERSION\u2019 was not declared in this scope
main.cpp:23: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
main.cpp:24: error: \u2018VERBOSE\u2019 was not declared in this scope
main.cpp:30: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
main.cpp:31: error: \u2018VERBOSE\u2019 was not declared in this scope
main.cpp: In function \u2018void runStreams()\u2019:
main.cpp:40: error: \u2018gContext\u2019 was not declared in this scope
streamsui.h:20: error: \u2018StreamsUI::~StreamsUI()\u2019 is private
main.cpp:41: error: within this context
main.cpp:42: error: \u2018class StreamsUI\u2019 has no member named \u2018exec\u2019
main.cpp: In function \u2018void runConfig()\u2019:
main.cpp:49: error: \u2018class StreamsSettings\u2019 has no member named \u2018exec\u2019
main.cpp: In function \u2018int mythplugin_run()\u2019:
main.cpp:54: error: \u2018gContext\u2019 was not declared in this scope
main.cpp:61: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
main.cpp:62: error: \u2018VERBOSE\u2019 was not declared in this scope
main.cpp: In function \u2018int setupDatabase()\u2019:
main.cpp:81: error: \u2018gContext\u2019 was not declared in this scope
main.cpp:84: error: \u2018gContext\u2019 was not declared in this scope
main.cpp:86: error: \u2018VB_GENERAL\u2019 was not declared in this scope
main.cpp:86: error: \u2018VERBOSE\u2019 was not declared in this scope
main.cpp:88: error: \u2018MSqlQuery\u2019 was not declared in this scope
main.cpp:88: error: expected `;' before \u2018query\u2019
main.cpp:89: error: \u2018query\u2019 was not declared in this scope
main.cpp:122: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
main.cpp:134: error: \u2018VB_IMPORTANT\u2019 was not declared in this scope
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/david/temp/mythvodka/mythvodka/mythvodka'
david@MythBuntu:~/temp/mythvodka/mythvodka$ 


```

---

### Post by azmyth on 2009-03-31
$cd mythvodka
$sudo apt-get install libmyth-dev
$make clean
$qmake mythvodka.pro
$make
$sudo make install

---

### Post by davidstoll on 2009-03-31
> **azmyth said:**
> $cd mythvodka
$sudo apt-get install libmyth-dev
$make clean
$qmake mythvodka.pro
$make
$sudo make install

according to the wiki, I am supposed to do all this inside the plugins directory...

```
david@MythBuntu:/usr/lib/mythtv/plugins/mythvodka/mythvodka$ make clean
make: *** No rule to make target `/usr/qt/3/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.
david@MythBuntu:/usr/lib/mythtv/plugins/mythvodka/mythvodka$ qmake mythvodka.pro 
Failure to open file: /usr/lib/mythtv/plugins/mythvodka/mythvodka/Makefile
david@MythBuntu:/usr/lib/mythtv/plugins/mythvodka/mythvodka$ make
make: *** No rule to make target `/usr/qt/3/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.
david@MythBuntu:/usr/lib/mythtv/plugins/mythvodka/mythvodka$ sudo make install
make: *** No rule to make target `/usr/qt/3/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.
david@MythBuntu:/usr/lib/mythtv/plugins/mythvodka/mythvodka$
```

---

### Post by azmyth on 2009-03-31
It's looking for qmake.conf in the wrong place.

Open the mythvodka/makefile and search for

```
Makefile: mythvodka.pro  /usr/qt/3/mkspecs/linux-g++/qmake.conf /usr/local/include/mythtv/mythconfig.mak \
```

Replace with

```
Makefile: mythvodka.pro  /usr/share/qt3/mkspecs/default/qmake.conf /usr/local/include/mythtv/mythconfig.mak \

```

Try again

---

### Post by davidstoll on 2009-03-31
> **azmyth said:**
> It's looking for qmake.conf in the wrong place.

Open the mythvodka/makefile and search for

```
Makefile: mythvodka.pro  /usr/qt/3/mkspecs/linux-g++/qmake.conf /usr/local/include/mythtv/mythconfig.mak \
```

Replace with

```
Makefile: mythvodka.pro  /usr/share/qt3/mkspecs/default/qmake.conf /usr/local/include/mythtv/mythconfig.mak \

```

Try again

That seemed to help, but on each line I had to sudo..

$sudo qmake mythvodka.pro
$sudo make
$sudo make install

Also, for some reason the script dumped the plugin "libmythvodka.so" into a newly created folder /mythtv/plugins/

I moved "/mythtv/plugins/libmythvodka.so" to /usr/lib/mythtv/plugins/

```
mv /mythtv/plugins/libmythvodka.so /usr/lib/mythtv/plugins/
```

When I tried to run mythvodka, I got a some errors about certain pl scripts not being executable, so I did this...

```
chmod 755 /usr/local/bin/gethulu.pl
chmod 755 /usr/local/bin/get_iplayer.pl
```


Next up, rtmpdump:

According to...
[http://www.mythtv.org/wiki/MythStreams](http://www.mythtv.org/wiki/MythStreams)
I am supposed to do the following...
```
wget http://garr.dl.sourceforge.net/sourceforge/rtmpdump/rtmpdump-v1.2a.tar.gz
tar xzf rtmpdump-v1.2a.tar.gz
cd rtmpdump
make
cp rtmpdump /usr/local/bin/
chmod 777 /var/tmp

```

however, when I make (or I even tried sudo make), I get this error...

```
david@MythBuntu:/usr/lib/mythtv/plugins/mythvodka/mythvodka/rtmpdump$ make
g++ -Wall rtmp.cpp log.cpp AMFObject.cpp rtmppacket.cpp rtmpdump.cpp -o rtmpdump -lboost_regex
rtmp.cpp:30:27: error: boost/regex.hpp: No such file or directory
rtmp.cpp: In member function ‘bool RTMP_LIB::CRTMP::Connect(char*, char*, char*, char*, char*, char*, char*, double)’:
rtmp.cpp:80: error: ‘boost’ has not been declared
rtmp.cpp:80: error: expected `;' before ‘re’
rtmp.cpp:82: error: ‘boost’ has not been declared
rtmp.cpp:82: error: ‘re’ was not declared in this scope
rtmp.cpp:97: error: ‘boost’ has not been declared
rtmp.cpp:97: error: expected `;' before ‘matches’
rtmp.cpp:99: error: ‘boost’ has not been declared
rtmp.cpp:99: error: expected `;' before ‘re1’
rtmp.cpp:100: error: ‘boost’ has not been declared
rtmp.cpp:100: error: ‘matches’ was not declared in this scope
rtmp.cpp:100: error: ‘re1’ was not declared in this scope
rtmp.cpp:109: error: ‘matches’ was not declared in this scope
rtmp.cpp:113: error: ‘matches’ was not declared in this scope
make: *** [rtmpdump] Error 1
david@MythBuntu:/usr/lib/mythtv/plugins/mythvodka/mythvodka/rtmpdump$
```


By the way, I really appreciate all this help!
:D

---

### Post by azmyth on 2009-04-01
You need boost-dev to compile mythvodka.

There's a mythvodka package. You'll have to enable the ppa repo that you can find in the original mythvodka thread but you're almost there with compiling. You'll still have to make the changes to a few files to get it working to fix hulu's attempt to stop us.

"That seemed to help, but on each line I had to sudo..

$sudo qmake mythvodka.pro
$sudo make
$sudo make install"

Yeah, I forgot you're building in a directory owned by root. I originally compiled in my home directory. I ended up switching to the package though.

---

### Post by davidstoll on 2009-04-01
> **azmyth said:**
> You need boost-dev to compile mythvodka.

There's a mythvodka package. You'll have to enable the ppa repo that you can find in the original mythvodka thread but you're almost there with compiling. You'll still have to make the changes to a few files to get it working to fix hulu's attempt to stop us.

"That seemed to help, but on each line I had to sudo..

$sudo qmake mythvodka.pro
$sudo make
$sudo make install"

Yeah, I forgot you're building in a directory owned by root. I originally compiled in my home directory. I ended up switching to the package though.

I hate to be a newbee, but can you tell me what the link to the repository is?  I google searched it, but I guess I'm not looking for the right thing....or maybe this repository is built into mythbuntu...?  But if you could show me how to do it, I would appreciate it.  I would much rather apt-get something and let it auto install and setup everything correctly.

Thanks!

---

### Post by azmyth on 2009-04-01
Try

[https://code.launchpad.net/~tgm4883/+junk/mythvodka](https://code.launchpad.net/~tgm4883/+junk/mythvodka)

---

### Post by davidstoll on 2009-04-01
> **azmyth said:**
> Try

[https://code.launchpad.net/~tgm4883/+junk/mythvodka](https://code.launchpad.net/~tgm4883/+junk/mythvodka)

I have seen that page before, but I didn't see much in the way of instruction, so I never pursued it.

After your suggestion, I did try it.  It didn't like the https, so I changed it to http

```
deb https://code.launchpad.net/~tgm4883/+junk/mythvodka intrepid main
```

However, apt-get install mythvodka didn't work.  His page doesn't really say either.  Any ideas?

---

### Post by tgm4883 on 2009-04-01
> **davidstoll said:**
> I have seen that page before, but I didn't see much in the way of instruction, so I never pursued it.

After your suggestion, I did try it.  It didn't like the https, so I changed it to http

```
deb https://code.launchpad.net/~tgm4883/+junk/mythvodka intrepid main
```

However, apt-get install mythvodka didn't work.  His page doesn't really say either.  Any ideas?

Thats because that isn't a PPA, it's a bzr branch.  I took the package off of my PPA because I needed to start working with packages that would probably break some users systems.  I gave good notice of this in that thread and requested someone to take it over.

What you can do with that bzr branch is download it, patch the necessary problems due to hulu changing their site, and upload it to your own PPA (where it will build).  There is also a branch for rtmpdump, although i'm not sure that is needed anymore depending on how mythvodka gets hulu working.

---

### Post by wheniwork on 2009-04-01
> **davidstoll said:**
> I hate to be a newbee, but can you tell me what the link to the repository is?  I google searched it, but I guess I'm not looking for the right thing....or maybe this repository is built into mythbuntu...?  But if you could show me how to do it, I would appreciate it.  I would much rather apt-get something and let it auto install and setup everything correctly.

Thanks!

I am getting the same error when trying to "make" rtmpdump. I get this output.

```
g++ -Wall rtmp.cpp log.cpp AMFObject.cpp rtmppacket.cpp rtmpdump.cpp -o rtmpdump -lboost_regex
rtmp.cpp:30:27: error: boost/regex.hpp: No such file or directory
rtmp.cpp: In member function &#8216;bool RTMP_LIB::CRTMP::Connect(char*, char*, char*, char*, char*, char*, char*, double)&#8217;:
rtmp.cpp:80: error: &#8216;boost&#8217; has not been declared
rtmp.cpp:80: error: expected `;' before &#8216;re&#8217;
rtmp.cpp:82: error: &#8216;boost&#8217; has not been declared
rtmp.cpp:82: error: &#8216;re&#8217; was not declared in this scope
rtmp.cpp:97: error: &#8216;boost&#8217; has not been declared
rtmp.cpp:97: error: expected `;' before &#8216;matches&#8217;
rtmp.cpp:99: error: &#8216;boost&#8217; has not been declared
rtmp.cpp:99: error: expected `;' before &#8216;re1&#8217;
rtmp.cpp:100: error: &#8216;boost&#8217; has not been declared
rtmp.cpp:100: error: &#8216;matches&#8217; was not declared in this scope
rtmp.cpp:100: error: &#8216;re1&#8217; was not declared in this scope
rtmp.cpp:109: error: &#8216;matches&#8217; was not declared in this scope
rtmp.cpp:113: error: &#8216;matches&#8217; was not declared in this scope
make: *** [rtmpdump] Error 1

```

You say i need boost-dev in order to make rtmpdump... is that correct? If so how do i get boost-dev... no repositiories have it. I didn't see it in yours either. I tried boost-build but that did not allow me to make rtmpdump.

Thanks for the help..

BTW: Mythbvodka installed fine... Im just getting a script error on the hulu perl file... probably because rtmpdump isnt installing right....

---

### Post by wheniwork on 2009-04-01
Ok. Got rtmpdump installed with apt by using libboost-dev.


BUT.. I still get an error when accessing through myth. See below... any ideas? 

[IMG]http://www.thisclicks.net/assets/mytherror.png[/IMG]

---

### Post by azmyth on 2009-04-01
What are your mythvodka settings?

---

### Post by wheniwork on 2009-04-01
MythVodka settings are here....

[IMG]http://www.thisclicks.net/assets/mythvodkasettings.png[/IMG]

Thanks for any help...

---

### Post by azmyth on 2009-04-01
change hulu grabber to

/bin/cat /var/tmp/hulu.xml

Then through a terminal run

cd to the gethulu.pl file and then

./gethulu.pl /var/tmp/hulu.xml

You may have to do this as root.

It'll take hours to complete the first time after it's done go back to the frontend and enter mythvodka it'll take awhile to enter to the db and it'll crash a few times but then you should be good to go.

---

### Post by wheniwork on 2009-04-01
Ok. I don't think the XML is getting generated.

when I run from this from the terminal it happens pretty fast.

```
/usr/local/bin/gethulu.pl /var/tmp/hulu.xml
```

Then when i view the hulu.xml all that is in that file is:

```
<MediaStreams>
</MediaStreams>

```

Did Hulu change something that breaks mythvodka? Does it work for you?

---

### Post by azmyth on 2009-04-02
Mines busted too and I never noticed. Maybe someone can point us to a new gethulu.pl.

There's one here but I haven't tried it since it needs a bunch more perl modules.

[http://lazorsoftware.com/mythtv/index.php](http://lazorsoftware.com/mythtv/index.php)

---

### Post by azmyth on 2009-04-02
I gave the gethulu.pl a try in the above link and it works. Actually it just needed one perl module, JSON. Haven't tried to see how the xml imports in though since I'm still generating the xml.

---

### Post by davidstoll on 2009-04-02
> **azmyth said:**
> I gave the gethulu.pl a try in the above link and it works. Actually it just needed one perl module, JSON. Haven't tried to see how the xml imports in though since I'm still generating the xml.

Mine is also currently pulling down the hulu.xml.

The perl module was "libconfig-json-perl" along with some other dependencies that will be added automatically.

Much thanks to you guys for the help!

):P

---

### Post by davidstoll on 2009-04-03
Uh oh, it didn't run for that long...and I tried two more times.  I got this error (just the end of what showed up on the command line).

```
<Stream>
<Name>June 11, 2007</Name>
<Url>http://www.hulu.com/watch/28158</Url>
<Subtitle>S35E13034</Subtitle>
<AirDate>06/11/2007</AirDate>
<Synopsis>Cleo moves ahead with her designs on Will. Alison's life is in danger until Dusty arrives to help. Faith is involved in a dangerous accident.</Synopsis>
<RunningTime>2273</RunningTime>
<Type>Full Episode</Type>
<StreamImage>http://thumbnails.hulu.com/9/783/29739_145x80_generated__YWsWmrqLOkeJP49HDuOjfQ.jpg</StreamImage>
</Stream>
malformed text data., at character offset 0 ["(end of string)"] at ./gethulu.pl line 249
```

---

### Post by azmyth on 2009-04-03
you need to add a -o to the command so gethulu.pl -o /var/rmp/hulu.xml or you won't get a file. It'll crash a few time so you just need to keep running until it exits without an error. Doesn't matter anyways as the plugin is busted again due to hulu changes.

---

### Post by davidstoll on 2009-04-03
> **azmyth said:**
> you need to add a -o to the command so gethulu.pl -o /var/rmp/hulu.xml or you won't get a file. It'll crash a few time so you just need to keep running until it exits without an error. Doesn't matter anyways as the plugin is busted again due to hulu changes.

gethulu.pl -o /var/tmp/hulu.xml

Doesn't work at all (first because rmp should be "tmp") but even so the -o gives this error...

```
$ sudo ./gethulu.pl -o /var/tmp/hulu.xml
malformed text data., at character offset 0 ["(end of string)"] at ./gethulu.pl line 249

```

How many times do I have to run it?  I've run it 5-10 times.

---

### Post by azmyth on 2009-04-03
Typo on the rmp. I had to run it a bunch too. It'll finally create the file without crapping out. You just have to fight with it the one time and that'll be it. If you don't have the -o, then everything just goes to the screen.

---

### Post by davidstoll on 2009-04-04
> **azmyth said:**
> Typo on the rmp. I had to run it a bunch too. It'll finally create the file without crapping out. You just have to fight with it the one time and that'll be it. If you don't have the -o, then everything just goes to the screen.

Any chance you could just post the xml in the meantime?

---

### Post by azmyth on 2009-04-04
The file size is 4.5MB. I'll be happy to email it to you. The plugin is broken since hulu changed something on their side.

---

### Post by davidstoll on 2009-04-05
> **azmyth said:**
> The file size is 4.5MB. I'll be happy to email it to you. The plugin is broken since hulu changed something on their side.

Could you post it here and then post the url?

[http://megaupload.com/](http://megaupload.com/)

I know it's probably stupid because hulu isn't working currently, but I would just like to see what it looks like.

Thanks!

---

### Post by azmyth on 2009-04-05
Megaupload didn't work. Try this link

[http://rapidshare.com/files/217828091/hulu.xml.html](http://rapidshare.com/files/217828091/hulu.xml.html)

---

### Post by Dr Bones on 2009-12-11
Hello all,

I have made the changes to the Makefile by changing the following lines...

```
Makefile: mythvodka.pro  /usr/qt/3/mkspecs/linux-g++/qmake.conf /usr/local/include/mythtv/mythconfig.mak \
```

such that it reads as follows...

```
Makefile: mythvodka.pro  /usr/share/qt3/mkspecs/default/qmake.conf /usr/local/include/mythtv/mythconfig.mak \
```

I then retried using make and got the following response...

```
cd mythvodka && make -f Makefile
make[1]: Entering directory `/usr/lib/mythtv/plugins/mythvodka/mythvodka'
Makefile:106: *** target pattern contains no `%'.  Stop.
make[1]: Leaving directory `/usr/lib/mythtv/plugins/mythvodka/mythvodka'
make: *** [sub-mythvodka] Error 2

```

I have tried this a bunch of different ways and seem to be making a little bit of progress slowly as I make changes.  I figure from the text there is an error on line 106 of the Makefile file but I am not well versed in doing this sort of thing so I have absolutely no idea as to what I need to do in order to remedy the situation.  I would like to thank whomever responds in advance, as I have spent a few hours searching how to get Mythvodka running and look forward to having it up and running.

---

