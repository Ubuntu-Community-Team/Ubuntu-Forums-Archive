---
title: "Problem Installing minidlna"
date: 2020-03-17
forum: Multimedia Software
---

### Post by MickSulley on 2020-03-17
I have rebuilt my server with 19.10 and I'm trying to install minidlna.  This is what I have done so far - 
```
mkdir ~/.minidlna
cd .minidlna/
git clone git://git.code.sf.net/p/minidlna/git minidlna-git
cd minidlna-git/
sudo apt install autoconf
sudo apt install automake
sudo apt install gettext
sudo apt install autopoint
sudo apt install libavutil-dev
sudo apt install libavcodec-dev
sudo apt install libavformat-dev
sudo apt install libjpeg-dev
sudo apt install libsqlite3-dev
sudo apt install libexif-dev
```
but when I try ./configure it fails with configure: error: libid3tag headers not found or not usable
```
share@zen:~/.minidlna/minidlna-git$ ./configure 
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking target system type... x86_64-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /usr/bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether make supports nested variables... (cached) yes
checking whether make supports the include directive... yes (GNU style)
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for gawk... (cached) gawk
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking whether gcc understands -c and -o together... (cached) yes
checking dependency style of gcc... (cached) gcc3
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for inline... inline
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for uint8_t... yes
checking for int32_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for ssize_t... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for struct dirent.d_type... yes
checking for struct stat.st_blocks... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking whether byte ordering is bigendian... no
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking whether lstat correctly handles trailing slash... yes
checking for gethostname... yes
checking for getifaddrs... yes
checking for gettimeofday... yes
checking for inet_ntoa... yes
checking for memmove... yes
checking for memset... yes
checking for mkdir... yes
checking for realpath... yes
checking for select... yes
checking for sendfile... yes
checking for setlocale... yes
checking for socket... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strpbrk... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for strtoul... yes
checking whether SEEK_HOLE is declared... yes
checking for struct ip_mreqn... yes
checking syscall.h usability... yes
checking syscall.h presence... yes
checking for syscall.h... yes
checking sys/syscall.h usability... yes
checking sys/syscall.h presence... yes
checking for sys/syscall.h... yes
checking mach/mach_time.h usability... no
checking mach/mach_time.h presence... no
checking for mach/mach_time.h... no
checking for __NR_clock_gettime syscall... yes
checking for linux/netlink.h... yes
checking libavutil/avutil.h usability... yes
checking libavutil/avutil.h presence... yes
checking for libavutil/avutil.h... yes
checking ffmpeg/libavutil/avutil.h usability... no
checking ffmpeg/libavutil/avutil.h presence... no
checking for ffmpeg/libavutil/avutil.h... no
checking libav/libavutil/avutil.h usability... no
checking libav/libavutil/avutil.h presence... no
checking for libav/libavutil/avutil.h... no
checking avutil.h usability... no
checking avutil.h presence... no
checking for avutil.h... no
checking ffmpeg/avutil.h usability... no
checking ffmpeg/avutil.h presence... no
checking for ffmpeg/avutil.h... no
checking libav/avutil.h usability... no
checking libav/avutil.h presence... no
checking for libav/avutil.h... no
checking libavcodec/avcodec.h usability... yes
checking libavcodec/avcodec.h presence... yes
checking for libavcodec/avcodec.h... yes
checking ffmpeg/libavcodec/avcodec.h usability... no
checking ffmpeg/libavcodec/avcodec.h presence... no
checking for ffmpeg/libavcodec/avcodec.h... no
checking libav/libavcodec/avcodec.h usability... no
checking libav/libavcodec/avcodec.h presence... no
checking for libav/libavcodec/avcodec.h... no
checking avcodec.h usability... no
checking avcodec.h presence... no
checking for avcodec.h... no
checking ffmpeg/avcodec.h usability... no
checking ffmpeg/avcodec.h presence... no
checking for ffmpeg/avcodec.h... no
checking libav/avcodec.h usability... no
checking libav/avcodec.h presence... no
checking for libav/avcodec.h... no
checking libavformat/avformat.h usability... yes
checking libavformat/avformat.h presence... yes
checking for libavformat/avformat.h... yes
checking ffmpeg/libavformat/avformat.h usability... no
checking ffmpeg/libavformat/avformat.h presence... no
checking for ffmpeg/libavformat/avformat.h... no
checking libav/libavformat/avformat.h usability... no
checking libav/libavformat/avformat.h presence... no
checking for libav/libavformat/avformat.h... no
checking avformat.h usability... no
checking avformat.h presence... no
checking for avformat.h... no
checking ffmpeg/avformat.h usability... no
checking ffmpeg/avformat.h presence... no
checking for ffmpeg/avformat.h... no
checking libav/avformat.h usability... no
checking libav/avformat.h presence... no
checking for libav/avformat.h... no
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking sqlite3.h usability... yes
checking sqlite3.h presence... yes
checking for sqlite3.h... yes
checking libexif/exif-loader.h usability... yes
checking libexif/exif-loader.h presence... yes
checking for libexif/exif-loader.h... yes
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
checking for jpeglib.h... (cached) yes
checking for sqlite3.h... (cached) yes
checking for libexif/exif-loader.h... (cached) yes
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
configure: error: libid3tag headers not found or not usable
```
I tried to install  libid3tag headers but that fails
```

mick@zen:~$ sudo apt install libid3tag
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libid3tag
```

Any suggestions how to fix this?
Thanks
Mick

---

### Post by speedwell68 on 2020-03-17
Can't you just install it directly?

---

### Post by deadflowr on 2020-03-17
Try libid3tag0-dev

---

### Post by SeijiSensei on 2020-03-18
> **speedwell68 said:**
> Can't you just install it directly?

I just checked on my 19.10 machine and can still install minidlna from the repositories with "sudo apt install minidlna".  Much easier than compiling from scratch.

By the way, the easiest method to compiling a package that exists in the repositories is to use the wonderful "build-dep" tool in apt-get.

```

sudo apt update
sudo apt install build-essential
sudo apt-get build-dep minidlna

```

"Build-essential" contains everything needed to compile software.  The build-dep line tells apt to get any source dependencies the minidlna package requires.  You'll need to have uncommented the "deb-src" lines in /etc/apt/sources.list for this to work.

---

### Post by MickSulley on 2020-03-19
Many thanks for the replies, yes you are right it does install directly.  I was using notes from a previous install which sent me on that route.

I then edited the .conf file to point to the media and also set the location of the log and the sqlite database, and it works!!!

Thanks for you help
Mick

---

