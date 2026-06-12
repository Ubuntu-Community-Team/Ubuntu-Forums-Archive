---
title: "Trying to build Jahshaka"
date: 2011-08-07
forum: Multimedia Software
---

### Post by medsouz on 2011-08-07
I've been trying to build Jahshaka ([http://sourceforge.net/projects/jahshakafx/](http://sourceforge.net/projects/jahshakafx/)) but I'm stuck on this make error:
> medsouz@ubuntu:~/Jahshaka/jahshaka$ make
cd source/AuxiliaryLibraries && make -f Makefile
make[1]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries'
cd blur && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/blur'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/blur'
cd FTGL && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/FTGL'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/FTGL'
cd particle && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/particle'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/particle'
cd apollon && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/apollon'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/apollon'
cd gift && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/gift'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/gift'
cd spaceball && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/spaceball'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/spaceball'
cd glew && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/glew'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries/glew'
make[1]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/AuxiliaryLibraries'
cd source/OpenLibraries && make -f Makefile
make[1]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/OpenLibraries'
cd opencore && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/OpenLibraries/opencore'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/OpenLibraries/opencore'
cd openassetlib/v2_openassetlib/sqlite3 && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/OpenLibraries/openassetlib/v2_openassetlib/sqlite3'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/OpenLibraries/openassetlib/v2_openassetlib/sqlite3'
cd openassetlib/v2_openassetlib && make -f Makefile
make[2]: Entering directory `/home/medsouz/Jahshaka/jahshaka/source/OpenLibraries/openassetlib/v2_openassetlib'
g++ -c -pipe -g -Wall -W -O2 -fexceptions -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -Icommon/include -I/usr/include/qt3 -o Release/Database.o src/Database.cpp
src/Database.cpp: In member function ‘virtual std::list<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > olib::openassetlib::Database::collectionNames() const’:
src/Database.cpp:217: warning: deprecated conversion from string constant to ‘char*’
src/Database.cpp: In member function ‘void olib::openassetlib::Database::testDatabase()’:
src/Database.cpp:677: warning: deprecated conversion from string constant to ‘char*’
src/Database.cpp:706: error: ‘strcpy’ was not declared in this scope
src/Database.cpp:737: warning: deprecated conversion from string constant to ‘char*’
src/Database.cpp:745: warning: deprecated conversion from string constant to ‘char*’
src/Database.cpp:753: warning: deprecated conversion from string constant to ‘char*’
make[2]: *** [Release/Database.o] Error 1
make[2]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/OpenLibraries/openassetlib/v2_openassetlib'
make[1]: *** [sub-openassetlib-v2_openassetlib] Error 2
make[1]: Leaving directory `/home/medsouz/Jahshaka/jahshaka/source/OpenLibraries'
make: *** [sub-source-OpenLibraries] Error 2
medsouz@ubuntu:~/Jahshaka/jahshaka$ 


Anybody know of a way I can solve this error?

---

### Post by .... on 2011-08-07
>  error: &#8216;strcpy&#8217; was not declared in this scope
[http://ubuntuforums.org/archive/index.php/t-1079695.html](http://ubuntuforums.org/archive/index.php/t-1079695.html)

---

