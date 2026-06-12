---
title: "Setup a Media Server with transcoding to 360"
date: 2008-12-26
forum: Multimedia Software
---

### Post by neomaximus2k on 2008-12-26
This walk through will teach you how to setup and install a media server on your linux box.  It is designed for Ubuntu 8.10 and has been tested on the server edition.
I have also attached configuration files for the XBOX 360 to overcome 90% of the problems people get.
So let’s start!!!
```
Sudo apt-get update
```
Now we have updated libraries we can install the dependencies we will need (if people find more let me know)

```
sudo apt-get install ffmpeg build-essential libavutil-dev libavformat-dev libavcodec-dev subversion libtool automake autoconf libsqlite3-dev libpcre3-dev libxml2-dev pkg-config libsqlite3-dev twolame toolame lame libmp3lame0 svn
```

Ok so we have everything we need, except the software, the software we will be using to act as the server is called Fuppes.  We won’t be using apt-get to install this package (as it isn’t in the list) instead we will use svn to download and extract

```
svn co http://fuppes-svn.ulrich-voelkel.de/trunk fuppes
```
if this failes try
```
svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes
```

Once it has completed we can compile and install it
```
autoreconf -vfi
./configure --enable-video-transcoding
make
sudo make install
```

This will make the installation and then run it.  Once this is completed (hopefully no errors) you should then have fuppes installed, now we create the directories for it
First we run fuppes
```
Sudo fuppes
```
This will create the directories we need, now type q and press enter to quit.
Don’t worry; we will setup fuppes to run as a service later on so you won’t have to keep running the software
Ok the configuration files have been created for us, let’s change them to work with our setup.
```
Sudo Cd ~/.fuppes
```
This will take you to the fuppes folder; we will be changing this later.
I won’t go into too much detail in regards to the configuration but what I do suggest is you use the attached configuration files and change them to your network settings; this will save a lot of time and hassle.
To download the config files we will use wget, the code is shown below
```
wget --output-document=fuppes.cfg http://www.paramiliar.com/files/fuppes.cfg.txt
```

I prefer to use nano to edit files, I think it is easier than VI to use, so
```
Nano fuppes.cfg
```
To add directories we need to add a few lines to the shared_objects area, the configuration files are all XML based, maybe someday i’ll get round to making a Perl script to help edit these files, but for now we just need to get it working, the rest can be done via our web browser!
```
<shared_objects>
    <dir>/home/user/myMedia</dir>
    <dir>/home/user/moreMedia</dir>
  </shared_objects>
```

As you can see for each directory you wish to share you just add it within a <dir> tag
Next we setup fuppes to listen on port 8080 (you can change this port if you wish) and to accept requests from all ip’s.  We also need to tell it which interface we will be using (if you are unsure you can run ifconfig to get a list of network devices activated.)
```
<network>
    <interface>eth1</interface>
    <http_port>8080</http_port>
	<allowed_ips>
		<!-- <ip>192.168.1.1</ip> -->
	</allowed_ips>
  </network>
```

If you wanted to tell fuppes to ONLY accept requests from your Xbox, then your Xbox would need to have a static IP address and you would change the configuration to something like this
```
<network>
    <interface>eth1</interface>
    <http_port>8080</http_port>
	<allowed_ips>
		<ip>192.168.1.150</ip>
	</allowed_ips>
  </network>
```

Once you have done that we need to use a folder configuration that will allow you to view the files on your 360 / ps3, now if this is setup incorrectly you won’t see any files listed, therefore it is probably best to use the attached file.
So now we have everything done, make sure you have at least one video file and one music files shared in fuppes.  We can now load fuppes and see if our files are there
```
Sudo fuppes
```
 Now go to your 360, you need to go to your video library (quickest way is press the 360 x button, press right and select video library) you should then see your media server including the folders you have shared.  If you don’t your vfolder configuration isn’t correct.
To download the vfolder configuration we will use wget
```
wget --output-document=vfolder.cfg http://www.paramiliar.com/files/vfolder.cfg.txt
```

Ok so we have files listed great, but we have to run fuppes every time we want to use it, to me that’s a bad idea as it would mean being logged on to the Linux box.  So we are going to convert fuppes into a service!
```
sudo mkdir /etc/fuppes
sudo mkdir /var/lib/fuppes
sudo cp ~/.fuppes/fuppes.cfg /etc/fuppes
sudo cp ~/.fuppes/vfolder.cfg /etc/fuppes
sudo cp ~/.fuppes/fuppes.db /var/lib/fuppes
```

This will move your configuration files into the correct places an d move the database of shares into your var lib folder.
So now we have to setup a user just for fuppes, we could use the root account but that would pose so many security risks that it isn’t worth it.  Plus you should disable the root account on any box to make it more secure.
```
sudo adduser --system --home /var/lib/fuppes --shell /bin/sh --group --no-create-home fuppes
```

Now we assign the configuration to this user (don’t worry you can still edit the file with a sudo command)
```
sudo chown fuppes:fuppes /etc/fuppes/*
sudo chown -R fuppes:fuppes /var/lib/fuppes
```

Ok so we have the files in the right place, let’s do some shell programming!  For simplicity I have attached this initializing file below so if you don’t want to do a lot of typing you can just download it
To download the service file we will use wget
```
wget --output-document=fuppesd http://www.paramiliar.com/files/fuppesd.txt
```

```
Sudo nano /etc/init.d/fuppesd
```

The file content is listed below
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          fuppesd
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: UPnP Media Server
# Description:       Fuppes UPnP media server.
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DESC="UPnP Media Server"
NAME=fuppesd
DAEMON=`which $NAME`
DAEMON_ARGS="--config-dir /etc/fuppes/ --database-file /var/lib/fuppes/fuppes.db --log-level 0"
SCRIPTNAME=/etc/init.d/$NAME
FUPPES_USER=fuppes
FUPPES_GROUP=fuppes

# Exit if the package is not installed
if [ ! -x "$DAEMON" ]; then
{
        echo "Couldn't find $DAEMON"
        exit 99
}
fi

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	start-stop-daemon --start --quiet --chuid $FUPPES_USER:$FUPPES_GROUP --exec $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --chuid $FUPPES_USER:$FUPPES_GROUP --exec $DAEMON -- $DAEMON_ARGS \
		|| return 2
}

#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --signal 2 --retry 5 --quiet --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	return "$RETVAL"
}

case "$1" in
  start)
	log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) log_end_msg 0 ;;
		2) log_end_msg 1 ;;
	esac
	;;
  stop)
	log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) log_end_msg 0 ;;
		2) log_end_msg 1 ;;
	esac
	;;
  restart|force-reload)
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2

	exit 3
	;;
esac

:

```
Ok that’s our file, for my version I have told it not to log anything to the screen (otherwise what would happen is you would get visual alerts saying when new files are added, sounds great but when you’re in the middle of something it gets very confusing.  If you want to log output change DAEMON_ARGS and change –log-level to 1
Whether you downloaded the file or used the text above, we will need to make the script executable
```
sudo chmod +x /etc/init.d/fuppesd
```

now we just fixed some linking issues
```
sudo update-rc.d fuppesd defaults 60
```

There we have it, issue a reboot (reboot) and once your system has rebooted you can check if fuppes is online by visiting the webpage. **[http://IPADDRESS:8080](http://IPADDRESS:8080)**
if you want to manually start and stop fuppes the commands are shown below
```
sudo /etc/init.d/fuppesd stop
sudo /etc/init.d/fuppesd start
```

And there we have it, a fully working media server.  If you have any problems just post a response and I’ll try to help where I can

---

### Post by donwait on 2009-07-29
if you get a fail on the 

configure.ac:104: warning: AC_LIB_PREPARE_PREFIX is m4_require'd but not m4_defun'd
m4/iconv.m4:9: AM_ICONV_LINKFLAGS_BODY is expanded from...
m4/iconv.m4:20: AM_ICONV_LINK is expanded from...
m4/iconv.m4:154: AM_ICONV is expanded from...
configure.ac:104: the top level
configure.ac:104: warning: AC_LIB_RPATH is m4_require'd but not m4_defun'd
autoreconf: running: /usr/bin/autoconf --force
configure.ac:104: warning: AC_LIB_PREPARE_PREFIX is m4_require'd but not m4_defun'd
m4/iconv.m4:9: AM_ICONV_LINKFLAGS_BODY is expanded from...
m4/iconv.m4:20: AM_ICONV_LINK is expanded from...
m4/iconv.m4:154: AM_ICONV is expanded from...
configure.ac:104: the top level
configure.ac:104: warning: AC_LIB_RPATH is m4_require'd but not m4_defun'd
configure:21583: error: possibly undefined macro: AC_LIB_PREPARE_PREFIX
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:21584: error: possibly undefined macro: AC_LIB_RPATH
configure:21589: error: possibly undefined macro: AC_LIB_LINKFLAGS_BODY
configure:21597: error: possibly undefined macro: AC_LIB_APPENDTOVAR
autoreconf: /usr/bin/autoconf failed with exit status: 1


you need to install gettext

issue 

sudo apt-get install gettext 

probably add it to the original set

---

### Post by Elsven on 2009-12-22
Ok, I have tried this using several tutorials and I still can't enable transcoding.  I would love it if anyone could help me with this issue.

```
CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : no
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : no
      flac       : no
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : disabled

  image conversion/rescaling plugins
    ImageMagick        : disabled (Wand C-API)

  audio metadata extraction plugins
    taglib             : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : disabled
    ImageMagick        : disabled (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : disabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : disabled
    inotify            : enabled

Thanks for using fuppes
please report bugs

```

Here is the full output:

```
./configure --enable-video-transcoding
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for a BSD-compatible install... /usr/bin/install -c
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for off_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether we are building with mingw... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for unistd.h... (cached) yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for select... yes
checking for off_t... (cached) yes
checking size of off_t... 8
checking for long long int... yes
checking size of long long int... 8
checking for unsigned long long int... yes
checking size of unsigned long long int... 8
checking for long int... yes
checking size of long int... 4
checking for unsigned long int... yes
checking size of unsigned long int... 4
checking for int... yes
checking size of int... 4
checking for unsigned int... yes
checking size of unsigned int... 4
checking for short... yes
checking size of short... 2
checking for unsigned short... yes
checking size of unsigned short... 2

check minimum dependencies

checking for PCRE... yes
checking for LIBXML... yes
checking for SQLITE3... yes
checking for pthread_create in -lpthread... yes
checking for clock_gettime in -lrt... yes

check recommended dependencies

checking for UUID... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);

check optional stuff

checking for taglib-config... no
checking for FFMPEGTHUMBNAILER... no
checking for IMAGEMAGICK_WAND... no
checking for EXIV2... no
checking for LIBAVFORMAT... yes
checking libavformat/avformat.h usability... no
checking libavformat/avformat.h presence... no
checking for libavformat/avformat.h... no
checking for LIBSWSCALE... no
checking ffmpeg/avstring.h usability... yes
checking ffmpeg/avstring.h presence... yes
checking for ffmpeg/avstring.h... yes
checking for LIBAVCODEC... yes
checking for LIBAVUTIL... yes
checking for mpeg4ip-config... no
configure: *** mpeg4ip/libmp4v2 support disabled ***
checking for VORBISFILE... yes
checking mpcdec/config_types.h usability... no
checking mpcdec/config_types.h presence... no
checking for mpcdec/config_types.h... no
checking FLAC/file_decoder.h usability... no
checking FLAC/file_decoder.h presence... no
checking for FLAC/file_decoder.h... no
checking FLAC/stream_decoder.h usability... no
checking FLAC/stream_decoder.h presence... no
checking for FLAC/stream_decoder.h... no
checking for simage-config... no
checking for mysql_config... no
checking sys/inotify.h usability... yes
checking sys/inotify.h presence... yes
checking for sys/inotify.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating m4/Makefile
config.status: creating src/Makefile
config.status: creating src/plugins/Makefile
config.status: creating src/windows/Makefile
config.status: creating include/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : no
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : no
      flac       : no
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : disabled

  image conversion/rescaling plugins
    ImageMagick        : disabled (Wand C-API)

  audio metadata extraction plugins
    taglib             : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : disabled
    ImageMagick        : disabled (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : disabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : disabled
    inotify            : enabled

Thanks for using fuppes
please report bugs

sysadmin@Athina:~/fuppes$ shutdsudo shutdown 0
[sudo] password for sysadmin: 


Broadcast message from sysadmin@Athina

(/dev/pts/0) at 18:43 ...




The system is going down for maintenance NOW!

sysadmin@Athina:~/fuppes$ 
```

Regards,

Elsven

---

### Post by Elsven on 2009-12-23
Bump!

---

### Post by Elsven on 2009-12-31
Can anyone help me with this?

---

