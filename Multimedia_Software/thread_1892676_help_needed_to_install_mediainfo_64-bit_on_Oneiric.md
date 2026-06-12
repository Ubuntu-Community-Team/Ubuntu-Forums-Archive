---
title: "help needed to install mediainfo 64-bit on Oneiric"
date: 2011-12-08
forum: Multimedia Software
---

### Post by shantiq on 2011-12-08
just went through a brand new install of Oneiric and struggling to install mediainfo



last time i used 

> wget [http://ovh.dl.sourceforge.net/sourceforge/mediainfo/MediaInfo_CLI_0.7.8_GNU_FromSource.tar.bz2](http://ovh.dl.sourceforge.net/sourceforge/mediainfo/MediaInfo_CLI_0.7.8_GNU_FromSource.tar.bz2)



bzip2 -d  MediaInfo_CLI_0.7.8_GNU_FromSource.tar.bz2

tar xvf MediaInfo_CLI_0.7.8_GNU_FromSource.tar

cd  MediaInfo_CLI_GNU_FromSource

sh CLI_Compile.sh

cd MediaInfo/Project/GNU/CLI


sudo make install

which worked well but this time it collapses around the Compile  

** issue about Zenlib**

```
sh CLI_Compile.sh
checking build system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating libzen-config
config.status: creating libzen.pc
config.status: creating Makefile
config.status: executing depfiles commands

Configured ZenLib for 'x86_64-unknown-linux-gnu'

  Unicode?                                                yes
  wstring missing support?                                no
  Large files support?                                    yes
  Using WxWidgets?                                        no

  Create static lib?                                      yes
  Create shared lib?                                      no

  CXXFLAGS:  -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2
  LIBS: 
test -z "libzen.la" || rm -f libzen.la
rm -f "./so_locations"
rm -rf .libs _libs
rm -f *.o
rm -f *.lo
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT Conf.lo -MD -MP -MF .deps/Conf.Tpo -c ../../../Source/ZenLib/Conf.cpp -o Conf.o
 gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -fPIC -O2 -MT ConvertUTF.lo -MD -MP -MF .deps/ConvertUTF.Tpo -c ../../../Source/ZenLib/ConvertUTF.c -o ConvertUTF.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT CriticalSection.lo -MD -MP -MF .deps/CriticalSection.Tpo -c ../../../Source/ZenLib/CriticalSection.cpp -o CriticalSection.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT Dir.lo -MD -MP -MF .deps/Dir.Tpo -c ../../../Source/ZenLib/Dir.cpp -o Dir.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT File.lo -MD -MP -MF .deps/File.Tpo -c ../../../Source/ZenLib/File.cpp -o File.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT FileName.lo -MD -MP -MF .deps/FileName.Tpo -c ../../../Source/ZenLib/FileName.cpp -o FileName.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT InfoMap.lo -MD -MP -MF .deps/InfoMap.Tpo -c ../../../Source/ZenLib/InfoMap.cpp -o InfoMap.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT int128s.lo -MD -MP -MF .deps/int128s.Tpo -c ../../../Source/ZenLib/int128s.cpp -o int128s.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT int128u.lo -MD -MP -MF .deps/int128u.Tpo -c ../../../Source/ZenLib/int128u.cpp -o int128u.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT MemoryDebug.lo -MD -MP -MF .deps/MemoryDebug.Tpo -c ../../../Source/ZenLib/MemoryDebug.cpp -o MemoryDebug.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT OS_Utils.lo -MD -MP -MF .deps/OS_Utils.Tpo -c ../../../Source/ZenLib/OS_Utils.cpp -o OS_Utils.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT Translation.lo -MD -MP -MF .deps/Translation.Tpo -c ../../../Source/ZenLib/Translation.cpp -o Translation.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ZenLib\" -DVERSION=\"0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I../../../Source -DUNICODE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -fPIC -O2 -MT Thread.lo -MD -MP -MF .deps/Thread.Tpo -c ../../../Source/ZenLib/Thread.cpp -o Thread.o
In file included from ../../../Source/ZenLib/Thread.cpp:30:0:
../../../Source/ZenLib/Thread.h:66:19: error: 'size_t' has not been declared
../../../Source/ZenLib/Thread.cpp:322:20: error: variable or field 'Sleep' declared void
../../../Source/ZenLib/Thread.cpp:322:20: error: 'size_t' was not declared in this scope
../../../Source/ZenLib/Thread.cpp:322:20: note: suggested alternative:
/usr/include/c++/4.6/x86_64-linux-gnu/./bits/c++config.h:155:26: note:   'std::size_t'
[COLOR="Red"]make: *** [Thread.lo] Error 1
Problem while compiling ZenLib[/COLOR]
shantiq@shantiq-00000000000000000000000:~/MediaInfo_CLI_GNU_FromSource$ 

```


anyone knows how to fix that?




OR are there other routes?



thanx    shan

---

### Post by shantiq on 2011-12-08
**ok** thank God found a quick alternative route might be of use to some of you


go [**here**]("http://mediainfo.sourceforge.net/en/Download/Ubuntu")


and install [after downloading them in that order]

```
sudo dpkg -i libzen0_0.4.23-1_amd64.Ubuntu_11.10.deb

```

```
sudo dpkg -i libmediainfo0_0.7.51-1_amd64.Ubuntu_11.10.deb

```

```
sudo dpkg -i mediainfo_0.7.51-1_amd64.Debian_5.deb

```


much quicker than aforementioned route...


and for all other **[distros]("http://mediainfo.sourceforge.net/en/Download")**

---

