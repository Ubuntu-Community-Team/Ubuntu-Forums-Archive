---
title: "How to set up forked-daapd (mt-daapd replacement) on 9.10"
date: 2009-12-13
forum: Multimedia Software
---

### Post by dontodd on 2009-12-13
Over the last several releases of Ubuntu, mt-daapd's transcoding has not worked for me out of the box. I had always been able to find a workaround (for example, for 9.04, see [this post]("http://ubuntuforums.org/showpost.php?p=7341087&postcount=3")); however, 9.10 has me totally stumped.

In searching for a replacement, I came across [forked-daapd]("http://blog.technologeek.org/2009/06/12/217") (see also [this firefly forum post]("http://forums.fireflymediaserver.org/viewtopic.php?f=2&t=29772")). It does what mt-daapd does minus the web interface. I never used mt-daapd's web interface, so no loss for me there.

Note: The author has made AMD 64-bit packages available: [forked-daapd]("http://debian.technologeek.org/forked-daapd/") and [antlr3]("http://debian.technologeek.org/antlr/"). If you're on i386 like me, keep reading.

Installing forked-daapd was a challenge. Thankfully, the author was kind and patient enough to help me get it up and running. Here's what it took.

**Grab the forked-daapd package:** ```
git clone git://git.debian.org/~jblache/forked-daapd.git
```
Read the README and INSTALL files so you know what's up. Panic when you read something about antlr3, discover that the stock Ubuntu version is too old, and discover that it has something to do with java. Now relax, I'll walk you through it.

Make sure you have the other required libraries installed (and -dev variants):

Libraries:
[LIST]
[*]glibc 2.9+ (for signalfd)
[*]Avahi client libraries, 0.6.24 minimum
[*]sqlite3
[*]ffmpeg
[*]confuse
[*]libevent 1.4+
[*]libavl
[*]MiniXML
[*]libflac (optional)
[*]taglibc (optional)
[*]libplist 0.15+ (optional - iTunes XML support)
[/LIST]

**Get antlr3 packages**

I first installed the antlr3 packages from the repositories. Then I got the antlr-3.1.3.jar ([http://www.antlr.org/download/antlr-3.1.3.jar](http://www.antlr.org/download/antlr-3.1.3.jar)). Edit /usr/bin/antlr3 and in the CLASSPATH variable replace the path to the antlr-3.1.3.jar you downloaded. Don't worry about the stringtemplate.jar.

Grab the C libraries for antlr3 at [http://antlr.org/download/C](http://antlr.org/download/C) (3.1.3). Build and install with the typical ./configure --prefix=/usr ; make ; sudo make install.

**Configure and build forked-daapd**
Assuming you got the required libraries and antlr3 packages installed, you're ready to configure and build forked-daapd. Enter its directory and run ```
autoreconf -i
``` to build the configure script. I ran the configure script as recommended in the INSTALL: ```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --enable-flac --enable-musepack
```. Your configure options might be different depending on your needs. Run `make` and `sudo make install`.

**Add user daapd**
Forked-daapd will run with user daapd. I had to create the user on my system: ```
sudo useradd -r daapd
```
I also had to make sure user daapd could read my music library. I added daapd to the group music, which has read access to my library:
```
sudo usermod -G music daapd
groups daapd
```
(That last line just to verify.)
 
**Point to your library in the conf file**
The conf file is /etc/forked-daapd.conf. There's not much to configure, just point to your music library under "Directories to index."

**Create directory for database**
The database will live in /var/cache/forked-daapd so create that directory and make daapd the owner:
```
sudo mkdir /var/cache/forked-daapd
sudo chown daapd /var/cache/forked-daapd
```

Fire up forked-daapd with: ```
sudo /usr/sbin/forked-daapd
```

If you run into issues with your Soundbridge or other device not being able to see the server, check out [this post]("http://ubuntuforums.org/showpost.php?p=7335637&postcount=7") to learn how to add the daap service to avahi. Mine was a holdover from struggling with mt-daapd.

Cheers!

---

### Post by pikop on 2009-12-28
I was wondering if you had a download link to a .deb install?  Installing it through the .git with the avahi client libraries is creating conflicts

---

### Post by geoff123 on 2010-01-08
Thanks for the info. I just started using mt-daapd and ran across this.  What are the benefits of forked-daapd? and what is the stability compared with mt-daapd?  

I've really had no problems with mt-daapd so far other than a little confusion getting it set up the first time.  

Thanks, Geoff

---

### Post by Ace Jones on 2010-02-11
The main benefit to forked-daapd is that it is actively developed.  If mt-daapd works great for what you need, there is no reason to switch.  If you run into bugs or wish it had more capabilities, you're out of luck unless you want to get the code and fix/improve it yourself.

Forked-daapd is especially better suited to handling videos.  In particular, it:

[LIST]
[*]Supports Front Row (for audio and video)
[*]Interprets iTunes TV metadata correctly
[*]Supports files > 2GB
[/LIST]
In addition, I expect that it will be more stable and performant, because it was re-written from the ground up.  However, that's only based on anecdotal information from people who run mt-daapd.

Here's my download/build/installation process for Ubuntu 9.10 Server 64-bit.  This uses antlr-3.1.2, and configures it for 64-bit.  I don't mess around with CLASSPATH only because this is the only java I ever use on my system.  This also includes no optional features.
```
sudo apt-get install build-essential wget git-core git-doc autoconf automake libtool sun-java6-bin libavahi-client-dev libconfuse-dev libsqlite3-dev libavcodec-dev libavformat-dev libmxml-dev libavl-dev libevent-dev 

cd /usr/share/java
sudo wget http://www.antlr.org/download/antlr-3.1.2.jar

cd ~/Source
wget http://www.antlr.org/download/C/libantlr3c-3.1.2.tar.gz -O - | tar xvz

cd libantlr3c-3.1.2
./configure --enable-64bit
make && sudo make install
sudo ldconfig

cd ~/Source
git clone git://git.debian.org/users/jblache/forked-daapd.git

cd forked-daapd
autoreconf -i
./configure --prefix=/ --exec-prefix=/usr --datarootdir=/usr/share ac_cv_prog_JAVA="java -cp /usr/share/java/antlr-3.1.2.jar"
make && sudo make install

sudo mkdir -pv /var/cache/forked-daapd
sudo chown <me> /var/cache/forked-daapd

sudo /usr/sbin/forked-daapd
```That's good advice above to create user daapd, but I just configure it to run as me.

---

### Post by regles on 2010-03-20
*

---

### Post by cnperels on 2010-03-23
I followed the steps by Ace Jones, and when I get to the point where I make on forked-daapd, I get the following:
```

gcc -DHAVE_CONFIG_H -I. -I..  -D_GNU_SOURCE -D_REENTRANT          -D_THREAD_SAFE -D_REENTRANT -DDATADIR="\"/usr/share/forked-daapd\"" -DCONFDIR="\"//etc\"" -DSTATEDIR="\"//var\""   -g -O2 -Wall -D_LARGEFILE_SOURCE -MT forked_daapd-artwork.o -MD -MP -MF .deps/forked_daapd-artwork.Tpo -c -o forked_daapd-artwork.o `test -f 'artwork.c' || echo './'`artwork.c
mv -f .deps/forked_daapd-artwork.Tpo .deps/forked_daapd-artwork.Po
gcc -DHAVE_CONFIG_H -I. -I..  -D_GNU_SOURCE -D_REENTRANT          -D_THREAD_SAFE -D_REENTRANT -DDATADIR="\"/usr/share/forked-daapd\"" -DCONFDIR="\"//etc\"" -DSTATEDIR="\"//var\""   -g -O2 -Wall -D_LARGEFILE_SOURCE -MT forked_daapd-misc.o -MD -MP -MF .deps/forked_daapd-misc.Tpo -c -o forked_daapd-misc.o `test -f 'misc.c' || echo './'`misc.c
mv -f .deps/forked_daapd-misc.Tpo .deps/forked_daapd-misc.Po
java -cp /usr/share/java/antlr-3.1.2.jar org.antlr.Tool  RSP.g
make[2]: Leaving directory `/home/bonnye/source/forked-daapd/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bonnye/source/forked-daapd'
make: *** [all] Error 2

```
Anybody know what I'm doing wrong?

---

### Post by cnperels on 2010-03-23
Hmmm, somehow I got it to work.  Couldn't tell you how, but I know I accidentally ran make after removing antlr, which obviously failed.  I then reinstalled antlr and reran ./configure, then make without doing a make clean.  Bizarre.

---

### Post by regles on 2010-03-25
How can I crosscompile this on ubuntu on a system lacking glibc 2.9? I already found out I could use the headers instead of totally replacing and installing glibc (2.3.4). 
I ask this because I'd like it to run this on my synology with ppc proc and jamvm as java surrogate (allthough it doesn't really need java to run). Other then that I'm at a loss how to go about this.

So, where my interest is focussed is on how to crosscompile this on a ubuntu box.

I already noticed how "your mileage may vary" with the provided installation guide.

EDIT: sorry not the headers but copying the include files from glibc-2.9 to /usr/include.

---

### Post by bozo_the_grey on 2010-03-27
Hi,

regarding the java problems, I ran
java -cp /usr/share/java/antlr-3.2.jar org.antlr.Tool src/*.g
and then make.

After that, another problem:

gcc: @PHTREAD_LIBS@: No such file or directory

Does it sound like a variable in the Makefile that is not exported correctly ? seems also that there is a mispelling, shouldn't be PTHREAD_LIBS ?

Infact, 'make' runs the command:

libtool: link: gcc -g -O2 -Wall -D_LARGEFILE_SOURCE -o forked-daapd forked_daapd-main.o forked_daapd-db.o forked_daapd-logger.o forked_daapd-conffile.o forked_daapd-filescanner.o forked_daapd-filescanner_ffmpeg.o forked_daapd-filescanner_urlfile.o forked_daapd-filescanner_m3u.o forked_daapd-mdns_avahi.o forked_daapd-remote_pairing.o forked_daapd-http.o forked_daapd-ffmpeg_url_evbuffer.o forked_daapd-httpd.o forked_daapd-httpd_rsp.o forked_daapd-httpd_daap.o forked_daapd-httpd_dacp.o forked_daapd-dmap_helpers.o forked_daapd-transcode.o forked_daapd-artwork.o forked_daapd-misc.o forked_daapd-rsp_query.o forked_daapd-daap_query.o forked_daapd-scan-wma.o forked_daapd-scan-flac.o forked_daapd-scan-mpc.o forked_daapd-RSPLexer.o forked_daapd-RSPParser.o forked_daapd-RSP2SQL.o forked_daapd-DAAPLexer.o forked_daapd-DAAPParser.o forked_daapd-DAAP2SQL.o @PHTREAD_LIBS@  /usr/lib/libavahi-client.so -ldbus-1 -lpthread -lrt /usr/lib/libavahi-common.so -ldl -lsqlite3 -lavcodec -lavformat -lswscale -lavutil /usr/lib/libconfuse.so -lFLAC -lm -ltag_c -ltag -levent_core -lavl -lmxml -lantlr3c -lgcrypt -lgpg-error -pthread

Actually, in my config.log file I read 

pkg_cv_MINIXML_LIBS='@PHTREAD_LIBS@ -lmxml  '


Thanks,

Stefano

---

### Post by regles on 2010-03-27
My linux environment is different in that everything can be found in opt/.. instead of usr/..
Furthermore java could be a problem unless I use jamvm. Some other packages have to be compiled by hand as well.

I think I need some real help here...or some patience. Info on both would be really appreciated.

---

### Post by bozo_the_grey on 2010-03-27
Hi, I have removed  @PHTREAD_LIBS@ from Makefile and /src/Makefile.
Everything now compiles.
This variabel is associated always with the tag -lmxml so it seems that it has something to do with Mini-XML (mxml).

---

### Post by regles on 2010-03-28
> **bozo_the_grey said:**
> Hi, I have removed  @PHTREAD_LIBS@ from Makefile and /src/Makefile.
Everything now compiles.
This variabel is associated always with the tag -lmxml so it seems that it has something to do with Mini-XML (mxml).

The issue is with Mini-XML

mini-xml / mxml.pc.in

prefix=@prefix@
exec_prefix=@exec_prefix@
libdir=@libdir@
includedir=@includedir@ 
Name: Mini-XML
Description: Lightweight XML support library
Version: @VERSION@
[COLOR="Red"]Libs: @PC_LIBS@ @PHTREAD_LIBS@[/COLOR]
Cflags: @PC_CFLAGS@ @PTHREAD_FLAGS@


BTW I found this [http://code.google.com/p/raopd/](http://code.google.com/p/raopd/)

---

### Post by codebutler on 2010-04-01
Hi everyone,

I modified the debian packages from forked-dapp's author ([http://blog.technologeek.org/2010/02/14/282](http://blog.technologeek.org/2010/02/14/282)) to work on Ubuntu Karmic, and put them in my PPA here:

[https://launchpad.net/~codebutler/+archive/ppa](https://launchpad.net/~codebutler/+archive/ppa)

Let me know if you have any questions or just find this useful!

- Eric

---

### Post by Stupkid on 2010-04-03
Eric that was a huge help.  Got forked-daapd up and serving music to a Mac in about five minutes with your packages.  Made me look like a ninja after I told my wife I would have to compile my own packages.   ;)

Thanks a bunch!

---

### Post by cupoange on 2010-04-20
> **codebutler said:**
> Hi everyone,

I modified the debian packages from forked-dapp's author ([http://blog.technologeek.org/2010/02/14/282](http://blog.technologeek.org/2010/02/14/282)) to work on Ubuntu Karmic, and put them in my PPA here:

[https://launchpad.net/~codebutler/+archive/ppa]("https://launchpad.net/%7Ecodebutler/+archive/ppa")

Let me know if you have any questions or just find this useful!

- Eric

Found this very useful!  I've been having trouble with Rhythmbox/mt-daapd, and figured I'd give forked-daapd a try to see if it fixes my issues.  Extremely easy to set up, thanks!

One thing I was used to with mt-daapd, was through the web interface I could force a rescan of my library (and subsequently get the status of the scan).  Any plans on having some interface to support this functionality?  Is there any way I can see the status of the server scanning?  How would I initiate a rescan if I add more music to the library?

thanks again!

edit:  now when I try to connect to my library from rhythmbox, i see this error in the logs:
[2010-04-21 10:28:32]     daap: No User-Agent header, rejecting login request

it worked fine connecting from itunes on windows.

---

### Post by regles on 2010-05-07
Anybody tried installling the new and improved sourcecode?

[last forked-daapd code]("http://github.com/jasonmc/forked-daapd/blob/master")

---

### Post by ad_267 on 2010-06-20
I've also added an init script to get forked-daapd to run at startup.

```
gksu gedit /etc/init.d/forked-daapd
sudo chmod +x /etc/init.d/forked-daapd
sudo update-rc.d forked-daapd defaults
```

In /etc/init.d/forked-daapd I copied and modified /etc/init.d/skeleton so it looks like:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          forked-daapd
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start forked-daapd
# Description:       Start forked-daapd, a media server using
#                    the DAAPD protocol
### END INIT INFO

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="DAAP server for media sharing"
NAME=forked-daapd
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS=""
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

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
	start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
		$DAEMON_ARGS \
		|| return 2
	# Add code here, if necessary, that waits for the process to be ready
	# to handle requests from services started subsequently which depend
	# on this one.  As a last resort, sleep for some time.

    # Not really necessary, nothing else should depend on this
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
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Wait for children to finish too if this is a daemon that forks
	# and if the daemon is only ever run from this initscript.
	# If the above conditions are not satisfied then add some other code
	# that waits for the process to drop all resources that could be
	# needed by services started subsequently.  A last resort is to
	# sleep for some time.
	start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
	[ "$?" = 2 ] && return 2
	# Many daemons don't delete their pidfiles when they exit.
	rm -f $PIDFILE
	return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
	#
	# If the daemon can reload its configuration without
	# restarting (for example, when it is sent a SIGHUP),
	# then implement that here.
	#
	start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
	return 0
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  status)
       status_of_proc "$DAEMON" "$NAME" && exit 0 || exit $?
       ;;
  #reload|force-reload)
	#
	# If do_reload() is not implemented then leave this commented out
	# and leave 'force-reload' as an alias for 'restart'.
	#
	#log_daemon_msg "Reloading $DESC" "$NAME"
	#do_reload
	#log_end_msg $?
	#;;
  restart|force-reload)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
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
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop|status|restart|force-reload}" >&2
	exit 3
	;;
esac

:

```

---

### Post by geistio on 2010-06-30
Did anyone succeed in trying to compile the latest code from the git-repo with Ubuntu-10.04?
Are there any actively maintained PPA's?
Thanks in advance! ):P

---

### Post by ad_267 on 2010-07-01
> **geistio said:**
> Did anyone succeed in trying to compile the latest code from the git-repo with Ubuntu-10.04?
Are there any actively maintained PPA's?
Thanks in advance! ):P

After recent changes I've had to run this before ./configure, otherwise the configure script can't find zlib for some reason:
```
export ZLIB_CFLAGS=-I/usr/include
export ZLIB_LIBS=-lz
```

I also had to install libsqlite3-0 and libsqlite3-dev from debian testing which have the unlock notify API enabled.

I had to install libunistring-dev and libunistring0 but the build is failing at:
```
gcc -DHAVE_CONFIG_H -I. -I..  -D_GNU_SOURCE -I/usr/include -D_REENTRANT         -I/usr/include/taglib   -D_THREAD_SAFE -D_REENTRANT     -I/usr/include/alsa -DDATADIR="\"/usr/share/forked-daapd\"" -DCONFDIR="\"/etc\"" -DSTATEDIR="\"/var\"" -DFLAC -DMUSEPACK  -g -O2 -Wall -D_LARGEFILE_SOURCE -MT forked_daapd-misc.o -MD -MP -MF .deps/forked_daapd-misc.Tpo -c -o forked_daapd-misc.o `test -f 'misc.c' || echo './'`misc.c
In file included from misc.c:36:
/usr/include/unistr.h:189: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;_UNUSED_PARAMETER_&#8217;
/usr/include/unistr.h:259: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;_UNUSED_PARAMETER_&#8217;
make[2]: *** [forked_daapd-misc.o] Error 1
make[2]: Leaving directory `/home/adam/downloads/forked-daapd/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/adam/downloads/forked-daapd'
make: *** [all] Error 2
```

---

### Post by ninjaaOPI on 2010-07-17
Hi,

I have simply removed the #include <unistr.h> in misc.c,
which still seems to compile without flaws and seems to work without errors at the moment ... but didn't test too much, so can't decide on whether this makes sense at all as it must have been added by somewhat ... let's say ... intention !?

party on.

---

### Post by johnt0000 on 2010-07-18
Hi, 
I got around this error by removing libunistring and compiling this package from source.

The problems I have been having so far are that for some of my mp3 files, the tags aren't read.
Watching the program running using forked-daapd -fd 3, the songs that don't have tags show this:

ffmpeg: ID3v2.4 tag skipped, cannot handle unsynchronization

I am using the ffmpeg compiled from source on ubuntu 10.04 server amd64.
when I was running mt-daapd, it processed all of the tags correctly

Another issue I had was when I used the prebuild forked-daapd for debain on ubuntu, I could detect my AirPort Express and connect to it after I rebooted it through remote on iPhone (otherwise it would not connect)
On the version I built, the APE was not discovered.

Any hints would be appreciated,
I'll try rebuilding today.

Thanks,
John

---

### Post by ad_267 on 2010-07-19
Hi John, you might want to contact the author of forked-daapd about this as it sounds like a bug that should be fixed. His email address can be found in the AUTHORS file with the source code.

---

### Post by IndieRockSteve on 2010-07-26
Anyone try this on Lucid (10.04)? I'm trying and get this when I run *autoreconf -i*

```
$ autoreconf -i
configure.in:100: warning: AM_ICONV is m4_require'd but not m4_defun'd
m4/libunistring.m4:14: gl_LIBUNISTRING is expanded from...
configure.in:100: the top level
configure.in:100: warning: AM_ICONV is m4_require'd but not m4_defun'd
m4/libunistring.m4:14: gl_LIBUNISTRING is expanded from...
configure.in:100: the top level
configure.in:100: warning: AM_ICONV is m4_require'd but not m4_defun'd
m4/libunistring.m4:14: gl_LIBUNISTRING is expanded from...
configure.in:100: the top level
configure.in:100: warning: AM_ICONV is m4_require'd but not m4_defun'd
m4/libunistring.m4:14: gl_LIBUNISTRING is expanded from...
configure.in:100: the top level
configure:12007: error: possibly undefined macro: AM_ICONV
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:12009: error: possibly undefined macro: AC_LIB_HAVE_LINKFLAGS
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

anyone know what I need to get past this?

thanks!

---

### Post by Remix_88 on 2010-08-12
Hi,

Thanks to the previous posters I've been able to create a script which builds and installs forked-daapd (and its requirements) on Ubuntu Lucid and Maverick. The script also creates logrotate.d and init.d scripts.

Currently I've only tested forked-daap on 64-bit Lucid and listened to music with Banshee, but the script should also work on 32-bit as well. 

**NOTE!** forked-daapd requires SQLite3 with update notify API enabled which is _not_ available in the Lucid repos. Therefore my script grabs SQLite 3.6.23.1-4 from the Maverick builds in order to satisfy this requirement. I've no idea what the knock on effect might be so don't blame me if my script eats all your chocolates ;-) I've built forked-daapd in a virtual guest to ensure I don't break anything important on my production machines. Naturally, when running this script on Maverick it doesn't do the funky SQLite3 stuff.

You can get my scripts from my bzr repository. There are other scripts in there, most are incomplete or experimental.

```
bzr branch lp:~flexiondotorg/+junk/ServerScripts
```

The script needs to be executed via 'sudo'.

```
sudo ./daap-server.sh
```

The output from the script looks like this.

```
Installing daapd server
 [x] Downloading SQLite3 with notify unlock API enabled success
 [x] Installing SQLite3 with notify unlock API enabled success
 [x] Installing build requirements success
 [x] Updating ANTLR success
 [x] Downloading ANTLR C runtime success
 [x] Unpacking ANTLR C runtime success
 [x] Configuring ANTLR C runtime success
 [x] Building ANTLR C runtime success
 [x] Installing ANTLR C runtime success
 [x] Updating libraries success
 [x] Downloading forked-daapd success
 [x] Configuring forked-daapd success
 [x] Building forked-daapd success
 [x] Installing forked-daapd success
 [x] Adding 'daapd' user success
 [x] Setting 'daapd' permissions success
 [x] Configuring logrotate success
 [x] Configuring init.d success
```

If you want to see what the script is doing while it is running just execute the following in another shell.

```
tail -f daap-server.sh.log
```

Hopefully this will help some of you who, like me, were struggling to get forked-daapd working.

---

### Post by mikeb123 on 2010-08-13
Martin, thanks for that script - it saved me a lot of faffing with sqlite etc. However had to change line 116 to

DISTRIB_ARCH=`uname -m`

to get it running.

Cheers... Mike

---

### Post by Remix_88 on 2010-08-13
Hi Mike,

Thanks for the feedback, I've modified 'common.sh' as per your suggestion. I've also updated 'daap-server.sh' so that it supports Lucid and Maverick, but on Maverick it doesn't have to do the funky SQLite3 stuff :-)

---

### Post by swests on 2010-08-26
Martin

Thanks for posting your script.  Running on a clean 10.04 32-bit server install hits a problem when it runs autoreconf, installing 'gettext' fixes the issue.

Thought you'd want to know so you can patch the script.

Simon

---

### Post by swests on 2010-08-30
> **IndieRockSteve said:**
> Anyone try this on Lucid (10.04)? I'm trying and get this when I run *autoreconf -i*

```
$ autoreconf -i
configure.in:100: warning: AM_ICONV is m4_require'd but not m4_defun'd
m4/libunistring.m4:14: gl_LIBUNISTRING is expanded from...
configure.in:100: the top level
configure.in:100: warning: AM_ICONV is m4_require'd but not m4_defun'd
m4/libunistring.m4:14: gl_LIBUNISTRING is expanded from...
configure.in:100: the top level
configure.in:100: warning: AM_ICONV is m4_require'd but not m4_defun'd
m4/libunistring.m4:14: gl_LIBUNISTRING is expanded from...
configure.in:100: the top level
configure.in:100: warning: AM_ICONV is m4_require'd but not m4_defun'd
m4/libunistring.m4:14: gl_LIBUNISTRING is expanded from...
configure.in:100: the top level
configure:12007: error: possibly undefined macro: AM_ICONV
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:12009: error: possibly undefined macro: AC_LIB_HAVE_LINKFLAGS
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

anyone know what I need to get past this?

thanks!

To get past this I had to install gettext 
```
 sudo apt-get install gettext 
```

---

### Post by swests on 2010-08-30
Hi All

Has anyone been able to get the latest source to build?  There are more references to unistr.h, but it would appear that, on Lucid, that unistr.h is still work in progress...

See /usr/include/unistr.h lines 189 and 259.

Simon

---

### Post by Remix_88 on 2010-09-02
Hi,

I've updated the script to also install 'gettext'.

---

### Post by ergosteur on 2010-09-02
> **johnt0000 said:**
> 
Another issue I had was when I used the prebuild forked-daapd for debain on ubuntu, I could detect my AirPort Express and connect to it after I rebooted it through remote on iPhone (otherwise it would not connect)
On the version I built, the APE was not discovered.


Hi, feeling like a complete idiot here, but how do you connect the Remote app on iOS and AirPort Express to forked-daapd? I must be missing something obvious but can't for the life of me figure it out.

Running forked-daapd from the prebuilt packages for squeeze.

EDIT:
I should RTFM.

README
> Pairing with Remote on iPod/iPhone
----------------------------------

forked-daapd can be paired with Apple's Remote application for iPod/iPhone;
this is how the pairing process works:
 - start forked-daapd
 - start Remote, go to Choose Library, Add Library
 - prepare a text file with a filename ending with .remote; the filename
   doesn't matter, only the .remote ending does. This file must contain
   two lines: the first line is the name of your iPod/iPhone, the second
   is the 4-digit pairing code displayed by Remote.

   If your iPod/iPhone is named "Foobar" and Remote gives you the pairing
   code 5387, the file content will be:

      Foobar
      5387 

 - move this file somewhere in your library

At this point, you should be done with the pairing process and Remote should
display the name of your forked-daapd library. You can delete the .remote file
once the pairing process is done.

If Remote doesn't display the name of your forked-daapd library at this point,
the pairing process failed.

This will usually be because the .remote file did not contain the correct name
or pairing code. Start over the pairing process and try again.

If in doubt, enable a more verbose level of logging and check that forked-daapd
receives the mDNS announcement from your iPod/iPhone when the pairing code is
displayed by Remote (you can also use avahi-browse for this purpose, see below).
If not, you have a network issue and mDNS doesn't work properly on your network.

If you are unsure about your iPod/iPhone's name, here's how you can check for
the correct value:
 - in a terminal, run avahi-browse -r -k _touch-remote._tcp
 - start Remote, goto Choose Library, Add Library
 - after a couple seconds at most, you should get something similar to this:

+ ath0 IPv4 59eff13ea2f98dbbef6c162f9df71b784a3ef9a3      _touch-remote._tcp   local
= ath0 IPv4 59eff13ea2f98dbbef6c162f9df71b784a3ef9a3      _touch-remote._tcp   local
   hostname = [Foobar.local]
   address = [192.168.1.1]
   port = [49160]
   txt = ["DvTy=iPod touch" "RemN=Remote" "txtvers=1" "RemV=10000" "Pair=FAEA410630AEC05E" "DvNm=Foobar"]

The name of your iPod/iPhone is the value of the DvNm field above. In this
example, the correct value is Foobar.

Hit Ctrl-C to terminate avahi-browse.


---

### Post by DewDrop on 2010-09-02
Been trying different methods to compile it without any success... Keeps getting this:

```
make[2]: Entering directory `/home/andrei/forked-daapd/forked-daapd/src'
gcc -DHAVE_CONFIG_H -I. -I..  -D_GNU_SOURCE -I/usr/include -D_REENTRANT     -I/usr/local/include     -I/usr/include/taglib   -D_THREAD_SAFE -D_REENTRANT   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I/usr/include/alsa -DDATADIR="\"/usr/share/forked-daapd\"" -DCONFDIR="\"/etc\"" -DSTATEDIR="\"/var\"" -DFLAC -DMUSEPACK -DITUNES  -g -O2 -Wall -D_LARGEFILE_SOURCE -MT forked_daapd-db.o -MD -MP -MF .deps/forked_daapd-db.Tpo -c -o forked_daapd-db.o `test -f 'db.c' || echo './'`db.c
make[2]: *** [forked_daapd-db.o] Error 1
make[2]: Leaving directory `/home/andrei/forked-daapd/forked-daapd/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andrei/forked-daapd/forked-daapd'
make: *** [all] Error 2

```

Anyone, help please?

---

### Post by quakenul on 2010-09-03
Remix_88: Thanks a lot for your script. Unfortunately I've run into a problem on my 64-Bit Lucid when trying to excute the dappd-server.sh:

```

quakenul@shambler:~/ServerScripts$ sudo ./daap-server.sh 
Installing daapd server
ERROR! ./daap-server.sh is not supported on this platform

```

Any ideas to what the cause might be? uname -a says

```

Linux shambler 2.6.32-24-server #41-Ubuntu SMP Thu Aug 19 02:47:08 UTC 2010 x86_64 GNU/Linux

```

---

### Post by philipholland on 2010-09-04
If you're having problem compiling due to a unistr.h error on Ubuntu 10.04:

[FONT="Courier New"]/usr/include/unistr.h:189: error: expected ‘;’, ‘,’ or ‘)’ before ‘_UNUSED_PARAMETER_’
[/FONT]
Then try the following addition to the configure step:

[FONT="Courier New"]CFLAGS=-fno-inline ./configure[/FONT] 

This will cause an alternate form of the function to be used without the _UNUSED_PARAMETER_ which then makes it through the compiler.

---

### Post by johnt2010 on 2010-09-04
> **ergosteur said:**
> Hi, feeling like a complete idiot here, but how do you connect the Remote app on iOS and AirPort Express to forked-daapd? I must be missing something obvious but can't for the life of me figure it out.

Running forked-daapd from the prebuilt packages for squeeze.

EDIT:
I should RTFM.

README

Hey there, no problems.

If you are having are having problems connecting to an airport device, make sure ipv6 is enabled in the avahi conf (it is not by default in ubuntu 10.04).

On another note forked-daapd reached version .12, yay.

I'm so glad people have put so much time and effort making this great piece of software.


Just wondering if anyone has looked at or thought about the AirPlay ([http://www.engadget.com/2010/09/01/apples-airplay-music-streaming-coming-to-third-party-speaker-do/](http://www.engadget.com/2010/09/01/apples-airplay-music-streaming-coming-to-third-party-speaker-do/)) standard. Hopefully AirPlay won't be too different to AirTunes v2. Has anyone looked at it yet, or is it time to do some sniffing?



John

---

### Post by jpdanylik on 2010-09-07
I was having a lot of trouble getting this to compile on a stock Ubuntu Lucid server, and getting the same errors as quakenul and swests with the installation script.  After a spending too much time chasing down compilation errors and some of the weird dependancies, I found a tip that Debian's testing repositories have a working build, and installing from that worked flawlessly for me (after a little fiddling with gcrypt.)

Instructions are [here]("http://jamesdanylik.com/articles/undoing-the-damage-replacing-mt-daapd-firefly-with-forked-daapd/").  I know this isn't quite with the topic of the thread, but I thought I'd add this here since it's the leading forked-daapd thread in search right now and I'm sure with [iTunes 10 breaking Firefly support]("http://discussions.apple.com/thread.jspa?threadID=2564925&tstart=15") lots of people will be looking for it.

---

### Post by basicmonkey on 2010-09-08
> **philipholland said:**
> If you're having problem compiling due to a unistr.h error on Ubuntu 10.04:

[FONT="Courier New"]/usr/include/unistr.h:189: error: expected ‘;’, ‘,’ or ‘)’ before ‘_UNUSED_PARAMETER_’
[/FONT]
Then try the following addition to the configure step:

[FONT="Courier New"]CFLAGS=-fno-inline ./configure[/FONT] 

This will cause an alternate form of the function to be used without the _UNUSED_PARAMETER_ which then makes it through the compiler.
Thanks for that!

---

### Post by imsonica on 2010-09-13
hi all guys,
i've just installed my forked-daapd server, now i can view the shared library but i CAN'T access to webinterface the user name is invalid...i didn't undertand how to set up a new account... please help me to find the right solution!
thank you so much

---

### Post by Ferglitz on 2010-09-13
On a vanilla Lucid install, I'm finding this breaks as follows:

[x] Autoreconf forked-daapd success
 [x] Configure forked-daapd failed
 [i] Showing the last 5 lines from the logfile (/home/fergus/Projects/linux/Firefly/ServerScripts/./daap-server.sh.log)...
checking whether to build static libraries... no
checking for antlr3... no
configure: error: antlr3 wrapper not found and pre-generated files not available
20935's retcode: 1
failed

---

### Post by maubp on 2010-09-13
> **imsonica said:**
> hi all guys,
i've just installed my forked-daapd server, now i can view the shared library but i CAN'T access to webinterface the user name is invalid...i didn't undertand how to set up a new account... please help me to find the right solution!
thank you so much
That's easy - there is no web interface, as per the first post of the thread:
> **dontodd said:**
> It does what mt-daapd does minus the web interface. I never used mt-daapd's web interface, so no loss for me there.

---

### Post by ronsonk on 2010-09-15
I've been able to get it installed, but have 2 issues (+ 1 question):

1) The daemon won't stay running.  I'll be listening to a stream and the process (on the server) will die.  The last log entry is usually 'scan: Badly formatted .url file; expected format is bitrate, descr, url' I've checked the library I'm scanning - there are no .url files.

2) It won't scan my entire library.  It's only getting about 50%.  I've checked permissions, users and groups and everything seems ok.  Is there anyway to reset the scan or force a rescan, say by deleting the database?

3) How do I enable verbose logging?

Thanks,

Ken

---

### Post by mo-hog on 2010-09-19
This all seems like a bit of a drama. Will the packages automatically be pulled from Debian into the next Ubuntu, or does someone need to file a "needs-packaging" request?

It isn't in the current packages:
[http://packages.ubuntu.com/search?keywords=daapd&searchon=names&suite=all&section=all]("http://packages.ubuntu.com/search?keywords=daapd&searchon=names&suite=all&section=all")
but apparently the Debian packages work:
[http://jamesdanylik.com/articles/undoing-the-damage-replacing-mt-daapd-firefly-with-forked-daapd/]("http://jamesdanylik.com/articles/undoing-the-damage-replacing-mt-daapd-firefly-with-forked-daapd/")

The homepage says that it is in Debian Squeeze:
[http://www.jblache.org/projects/daapd/index.html]("http://www.jblache.org/projects/daapd/index.html")

---

### Post by nocliq on 2010-09-19
> **Ferglitz said:**
> On a vanilla Lucid install, I'm finding this breaks as follows:

[x] Autoreconf forked-daapd success
 [x] Configure forked-daapd failed
 [i] Showing the last 5 lines from the logfile (/home/fergus/Projects/linux/Firefly/ServerScripts/./daap-server.sh.log)...
checking whether to build static libraries... no
checking for antlr3... no
configure: error: antlr3 wrapper not found and pre-generated files not available
20935's retcode: 1
failed

I appear to be having this same issue. 

```
[x] Autoreconf forked-daapd success
[x] Configure forked-daapd failed
[i] Showing the last 5 lines from the logfile (/home/nocliq/ServerScripts/./daap-server.sh.log)...
checking whether to build static libraries... no
checking for antlr3... no
configure: error: antlr3 wrapper not found and pre-generated files not available
12989's retcode: 1
failed
```I tried manually reinstalling antlr3, but get the same "failed" message after running daap-server.sh again.
Any suggestions on getting around this?

```
Linux 2.6.32-24-generic-pae #42-Ubuntu SMP Fri Aug 20 15:37:22 UTC 2010 i686 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
```

Edit: Found the answer! Thanks mo-hog!
[http://jamesdanylik.com/articles/undoing-the-damage-replacing-mt-daapd-firefly-with-forked-daapd/](http://jamesdanylik.com/articles/undoing-the-damage-replacing-mt-daapd-firefly-with-forked-daapd/)

---

### Post by hpras on 2010-09-20
Well, I did the jamesdanylik recipe, and it seemed to work.... briefly. I'm on 10.04 though, not 9.10. 64bit. forked-daapd fires up, starts indexing my file, I can see the server in iTunes 10, and play a song, but then it crashes with........
 
Sep 19 20:53:14 odin kernel: [20113.170493] forked-daapd[6693]: segfault at 8020a3438 ip 00007f62d5bdb9ae sp 00007f62ce824580 error 4 in libavformat.so.52.31.0[7f62d5b8a000+9d000]

---

### Post by maubp on 2010-09-27
> **ad_267 said:**
> After recent changes I've had to run this before ./configure, otherwise the configure script can't find zlib for some reason:
```
export ZLIB_CFLAGS=-I/usr/include
export ZLIB_LIBS=-lz
```

I also had to install libsqlite3-0 and libsqlite3-dev from debian testing which have the unlock notify API enabled.

I had to install libunistring-dev and libunistring0 but the build is failing at:
```
gcc -DHAVE_CONFIG_H -I. -I..  -D_GNU_SOURCE -I/usr/include -D_REENTRANT         -I/usr/include/taglib   -D_THREAD_SAFE -D_REENTRANT     -I/usr/include/alsa -DDATADIR="\"/usr/share/forked-daapd\"" -DCONFDIR="\"/etc\"" -DSTATEDIR="\"/var\"" -DFLAC -DMUSEPACK  -g -O2 -Wall -D_LARGEFILE_SOURCE -MT forked_daapd-misc.o -MD -MP -MF .deps/forked_daapd-misc.Tpo -c -o forked_daapd-misc.o `test -f 'misc.c' || echo './'`misc.c
In file included from misc.c:36:
/usr/include/unistr.h:189: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;_UNUSED_PARAMETER_&#8217;
/usr/include/unistr.h:259: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;_UNUSED_PARAMETER_&#8217;
make[2]: *** [forked_daapd-misc.o] Error 1
make[2]: Leaving directory `/home/adam/downloads/forked-daapd/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/adam/downloads/forked-daapd'
make: *** [all] Error 2
```
I had the same problem with unistr.h using the libunistring version 0.9.1-1 libraries with Ubuntu Lucid - I installed libunistring0 and libunistring-dev 0.9.3-3 as deb files from Debian sid and that solved this:

[http://packages.debian.org/sid/libunistring0](http://packages.debian.org/sid/libunistring0)
[http://packages.debian.org/sid/libunistring-dev](http://packages.debian.org/sid/libunistring-dev)

Well, I've compiled forked-daapd-0.12 now - testing it is next...

P.S. This was also an easy way to install libantlr3c,

[http://packages.debian.org/sid/libantlr3c-3.2-0](http://packages.debian.org/sid/libantlr3c-3.2-0)
[http://packages.debian.org/sid/libantlr3c-dev](http://packages.debian.org/sid/libantlr3c-dev)

For a sufficiently up to date sqlite3 I used:

[http://packages.debian.org/sid/sqlite3](http://packages.debian.org/sid/sqlite3)
[http://packages.debian.org/squeeze/libsqlite3-0](http://packages.debian.org/squeeze/libsqlite3-0)
[http://packages.debian.org/sid/libsqlite3-dev](http://packages.debian.org/sid/libsqlite3-dev)

---

### Post by pcace on 2010-09-30
Hey im Running into the same issues like others:

>  [i] Showing the last 5 lines from the logfile (/home/hannes/source/ServerScripts/./daap-server.sh.log)...
checking whether to build static libraries... no
checking for antlr3... no
configure: error: antlr3 wrapper not found and pre-generated files not available
11523's retcode: 1
failed


> 2.6.32-24-generic-pae #43-Ubuntu SMP Thu Sep 16 15:30:27 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS


Is there a way to get this compiled? I just tried a manual install of antlr3 wrapper... - i dont want to use the debian repository!

Any Idea?


Thanks!

Pcace

EDIT: I did this Problem! But sorry for all who has this Poblem: i realy do not know what i did to fix it...

Anyway: The Next Problem:
SQLITE3
> checking for SQLITE3... configure: error: Package requirements ( sqlite3 >= 3.5.0 ) were not met:

No package 'sqlite3' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SQLITE3_CFLAGS
and SQLITE3_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

user@server:~/source/forked-daapd$ sqlite3
SQLite version 3.7.2
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite> 


What can i do there?? I realy dont know whats wrong there! Has anyone an idea how to fix that sqlite Problem? I installed the version from the Debian repository...


Thanks!

Pcace!

EDIT2:

GOT IT!!!! I used that version: [http://packages.debian.org/sid/i386/libsqlite3-dev/download](http://packages.debian.org/sid/i386/libsqlite3-dev/download)

---

### Post by maubp on 2010-10-01
When running configure and it tells you it is missing a dependency it isn't always clear what the Ubuntu/Debian package name is. The dependency list here is a great help:

[http://packages.debian.org/sid/forked-daapd](http://packages.debian.org/sid/forked-daapd)

Don't forget for package foo you will also want to install package foo-dev to get the header files to compile against.

---

### Post by rickwookie on 2010-10-20
> **Remix_88 said:**
> Hi,

Thanks to the previous posters I've been able to create a script which builds and installs forked-daapd (and its requirements) on Ubuntu Lucid and Maverick. The script also creates logrotate.d and init.d scripts.

Currently I've only tested forked-daap on 64-bit Lucid and listened to music with Banshee, but the script should also work on 32-bit as well. 

**NOTE!** forked-daapd requires SQLite3 with update notify API enabled which is _not_ available in the Lucid repos. Therefore my script grabs SQLite 3.6.23.1-4 from the Maverick builds in order to satisfy this requirement. I've no idea what the knock on effect might be so don't blame me if my script eats all your chocolates ;-) I've built forked-daapd in a virtual guest to ensure I don't break anything important on my production machines. Naturally, when running this script on Maverick it doesn't do the funky SQLite3 stuff.

You can get my scripts from my bzr repository. There are other scripts in there, most are incomplete or experimental.

```
bzr branch lp:~flexiondotorg/+junk/ServerScripts
```

The script needs to be executed via 'sudo'.

```
sudo ./daap-server.sh
```

The output from the script looks like this.

```
Installing daapd server
 [x] Downloading SQLite3 with notify unlock API enabled success
 [x] Installing SQLite3 with notify unlock API enabled success
 [x] Installing build requirements success
 [x] Updating ANTLR success
 [x] Downloading ANTLR C runtime success
 [x] Unpacking ANTLR C runtime success
 [x] Configuring ANTLR C runtime success
 [x] Building ANTLR C runtime success
 [x] Installing ANTLR C runtime success
 [x] Updating libraries success
 [x] Downloading forked-daapd success
 [x] Configuring forked-daapd success
 [x] Building forked-daapd success
 [x] Installing forked-daapd success
 [x] Adding 'daapd' user success
 [x] Setting 'daapd' permissions success
 [x] Configuring logrotate success
 [x] Configuring init.d success
```

If you want to see what the script is doing while it is running just execute the following in another shell.

```
tail -f daap-server.sh.log
```

Hopefully this will help some of you who, like me, were struggling to get forked-daapd working.

I get this on 10.10 server (32-bit):```
Installing daapd server
 [x] Installing forked-daapd requirements success
 [x] Downloading antlr-3.2.jar success
 [x] Downloading http://www.antlr.org/download/C/libantlr3c-3.2.tar.gz success
 [x] Unpacking libantlr3c-3.2.tar.gz success
 [x] Configure libantlr3c-3.2 success
 [x] Compile libantlr3c-3.2 success
 [x] Install libantlr3c-3.2 success
 [x] Updating libraries success
 [x] Downloading forked-daapd success
 [x] Autoreconf forked-daapd success
 [x] Configure forked-daapd failed
 [i] Showing the last 5 lines from the logfile (/home/richard/ServerScripts/daap-server.sh.log)...
checking whether to build static libraries... no
checking for antlr3... no
configure: error: antlr3 wrapper not found and pre-generated files not availab31939's retcode: 1
failed
```

Any ideas?

---

### Post by Squizzle on 2010-10-24
> **rickwookie said:**
> I get this on 10.10 server (32-bit):```
Installing daapd server
 [x] Installing forked-daapd requirements success
 [x] Downloading antlr-3.2.jar success
 [x] Downloading http://www.antlr.org/download/C/libantlr3c-3.2.tar.gz success
 [x] Unpacking libantlr3c-3.2.tar.gz success
 [x] Configure libantlr3c-3.2 success
 [x] Compile libantlr3c-3.2 success
 [x] Install libantlr3c-3.2 success
 [x] Updating libraries success
 [x] Downloading forked-daapd success
 [x] Autoreconf forked-daapd success
 [x] Configure forked-daapd failed
 [i] Showing the last 5 lines from the logfile (/home/richard/ServerScripts/daap-server.sh.log)...
checking whether to build static libraries... no
checking for antlr3... no
configure: error: antlr3 wrapper not found and pre-generated files not availab31939's retcode: 1
failed
```

Any ideas?

Exact same. Anyone?

---

### Post by ctothej on 2010-11-03
> **Squizzle said:**
> Exact same. Anyone?

> **rickwookie said:**
> I get this on 10.10 server (32-bit):```
Installing daapd server
 [x] Installing forked-daapd requirements success
 [x] Downloading antlr-3.2.jar success
 [x] Downloading http://www.antlr.org/download/C/libantlr3c-3.2.tar.gz success
 [x] Unpacking libantlr3c-3.2.tar.gz success
 [x] Configure libantlr3c-3.2 success
 [x] Compile libantlr3c-3.2 success
 [x] Install libantlr3c-3.2 success
 [x] Updating libraries success
 [x] Downloading forked-daapd success
 [x] Autoreconf forked-daapd success
 [x] Configure forked-daapd failed
 [i] Showing the last 5 lines from the logfile (/home/richard/ServerScripts/daap-server.sh.log)...
checking whether to build static libraries... no
checking for antlr3... no
configure: error: antlr3 wrapper not found and pre-generated files not availab31939's retcode: 1
failed
```

Any ideas?

I finally got around this problem...
I made a file ~/bin/antlr3 containing
```
#!/bin/sh
CLASSPATH=/usr/share/java/antlr-3.2.jar
java -cp $CLASSPATH org.antlr.Tool "$@"

```

Make sure it is executable:
> chmod +x ~/bin/antlr3

~/bin is on my PATH, so configure finds it alright. 

There was _some_ instruction for this in the read me here: [https://github.com/jasonmc/forked-daapd](https://github.com/jasonmc/forked-daapd).

---

### Post by Remix_88 on 2010-11-19
Hi,

A PPA for forked-daapd has been created including backported versions of the required packages. 

[https://launchpad.net/~codebutler/+archive/ppa](https://launchpad.net/~codebutler/+archive/ppa)

My script has been updated to use that PPA which makes this whole thing much simpler :-)

---

### Post by iDiogenes on 2010-12-31
Just installed forked-daaped using Remix_88 script and it worked great.  Thanks for the script Remix_88, saved me lots of time.

However, I am having two issues post install:

1. None of my movies (.mp4, .m4v) are showing up, only my music. From my mac I can play the same movies just fine in iTunes. According to the forked-daapd README it implies these video formats should not be a problem.

2. My Apple TV 2 cannot see the forked-daapd library, I have a feeling this has to do with "Home Sharing".  Can anyone confirm that the Apple TV 2 can work with forked-daaped and if so point me in the right direction about what needs to be configured to do so.

Thanks!

---

### Post by vinnybad on 2011-01-04
> **Remix_88 said:**
> Hi,

I've updated the script to also install 'gettext'.

Hey man, 

When I tried running the script on a fresh ubuntu 10.10 install, I ran into an error:

Downloading common.sh
Installing DAAP server
 [x] Adding ppa:codebutler/ppa success
 [x] Update package list failed
 [i] Showing the last 5 lines from the logfile (/home/vinnybad/forked-mtdaapd/ServerScripts/daap-server.sh.log)...
9396's retcode: 0
success
 [x] Update package list   /usr/local/lib/common.sh: line 422: aptitude: command not found
9424's retcode: 127
failed

  I ran "sudo apt-get install aptitude" to fix it...

---

### Post by tji on 2011-01-08
I tried the new script, which adds the repository and installs forked-daapd package.  It looks successful, but fails:
```
sudo ./daap-server.sh
Installing DAAP server
 [x] Adding ppa:codebutler/ppa success
 [x] Update package list success
 [x] Installing forked-daapd success
```

But, the log file says it didn't:

```
[x] Installing forked-daapd   Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Couldn't find any package whose name or description matched "forked-daapd"
Couldn't find any package whose name or description matched "forked-daapd"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 211 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

This is on an AMD64 10.10 system.  Any tips for getting it to install?

---

### Post by tji on 2011-01-09
I was able to get mine built manually after struggling with it for a while.  That antlr stuff is a pain in the *** to get right..  In 10.10 they call their antlr package 3.2, but upon closer inspection I found that they actually reverted to 3.0.1, which is older than the recommended version.   So, I scrapped theirs, and used 3.1.3.

---

### Post by alanpuccinelli on 2011-03-26
Trying to compile the latest 0.14 on 10.04 64 bit with much pain finally got configure to run and now this when I make... any ideas?


RSPLexer.c:3600: error: &#8216;struct ANTLR3_BASE_RECOGNIZER_struct&#8217; has no member named &#8216;exception&#8217;
make[2]: *** [forked_daapd-RSPLexer.o] Error 1
make[2]: Leaving directory `/root/forked-daapd-0.14/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/forked-daapd-0.14'
make: *** [all] Error 2


EDIT: Got it!! 0.14 running on 10.04 lucid
Ended up building from git and it worked smoothly. YMMV but the Tarballs were killing me. The initial post is spot on once you get all the library dependencies met, I build antlr3 library 3.2 from source and downloaded the 3.2 jar to accompany it. configured as is noted in INSTALL and then just MAKE and MAKE INSTALL. Copied this post to make a service to execute at startup. [http://ubuntuforums.org/showthread.php?t=1354196](http://ubuntuforums.org/showthread.php?t=1354196)

UPDATE: To get local audio output working properly (at least for ALSA) make sure you add your daapd user to the audio group (eg usermod -a -G audio daapd) Took me forever to figure out why the heck forked-daapd wasn't able to find my audio card, and that was it... no thanks to the error reporting from ALSA!

---

### Post by jbrew on 2011-04-06
I have forked-daapd setup up and it shows on my desktop (library is on my laptop) but it is only showing selective songs. It is setup to show /home/user/Music/ in prefs. Any advice to access the rest?

---

### Post by rsjaffe on 2011-05-01
I compiled from the latest tarball. Using 11.04 Natty, here are the dependencies I had to load.

[FONT="Fixedsys"]sudo apt-get build-essential libtagc0-dev gperf libunistring-dev pkg-config zlib1g-dev  libconfuse-dev libavahi-client-dev libsqlite3-dev libavcodec-dev libavformat-dev libswscale-dev libmxml-dev libevent-dev libavl-dev libantlr3c-dev libgcrypt11-dev libflac-dev libogg-dev libtagc0-dev libasound2-dev[/FONT]

Those will load lots of other files as well. Hopefully those will take care of most of the errors from the configure command:

[FONT="Fixedsys"]./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --enable-flac --enable-musepack[/FONT]

---

### Post by Twizzle on 2011-05-14
I have finally got this up and running thanks to this thread, however I am a bit stcuk when it comes to using Local Audio Output which the readme seems to suggest it can do.

I have my Ubuntu box, with soundcard, plugged into my Stereo and when I use Remote on my iPhone, I can't see the option to choose it as the speakers.

The way the Readme file reads is that it should appear as a 'speaker' option.

Has anyone managed to get this working?

---

### Post by keithspg on 2011-06-09
So, there are a couple things that can be done. 

The trick of adding debian repositories, installing and removing those repositories. Squeeze is using a fairly out of date version. You can try wheezy and sid. Sid is the most up to date. 

[http://tmoore.org/technology/mp3-library-serving-to-itunes-10-with-ubuntu/](http://tmoore.org/technology/mp3-library-serving-to-itunes-10-with-ubuntu/)

If you want to use git and keep current, you can install these packages under 11.04 Natty and it will compile. I have not checked to see if it will run, but it does compile.

```
sudo apt-get install pkg-config antlr3 gperf libunistring-dev zlib1g-dev libconfuse-dev libavahi-common-dev libavahi-client-dev libsqlite3-dev libavutil-dev libavcodec-dev
libavformat-dev libswscale-dev libmxml-dev libevent-dev libavl-dev libantlr3c-dev libgcrypt-dev libasound2-dev
```

Enjoy

---

### Post by demck85 on 2011-06-14
I got it running on 11.04 64-bit using this package:

[http://ftp.us.debian.org/debian/pool/main/f/forked-daapd/forked-daapd_0.16-2_amd64.deb]("http://ftp.us.debian.org/debian/pool/main/f/forked-daapd/forked-daapd_0.16-2_amd64.deb")

```

wget http://ftp.us.debian.org/debian/pool/main/f/forked-daapd/forked-daapd_0.16-2_amd64.deb

dpkg -i forked-daapd_0.16-2_amd64.deb

```

I got it paired with my iPhone 4 w/ Remote App 2.1.1

Stuff plays fine through my Windows 7 64bit w/ iTunes 10.3.1.

Though, it won't play through my iPhone though. No audio. Sees everything fine, just no audio.

---

### Post by demck85 on 2011-06-14
Has anyone tried this fix yet?

[http://www.c-note.dk/2011/04/14/airtunes-forked-daapd-and-airport-express/]("http://www.c-note.dk/2011/04/14/airtunes-forked-daapd-and-airport-express/")

---

### Post by Neonightmare on 2011-06-20
Hi, does anyone has a compiled i386.deb of forked-daapd?

[http://ftp.us.debian.org/debian/pool/main/f/forked-daapd/forked-daapd_0.16-2_i386.deb]("http://ftp.us.debian.org/debian/pool/main/f/forked-daapd/forked-daapd_0.16-2_i386.deb")

This one will not install because of dependencies.

THX Neo

---

### Post by demck85 on 2011-06-21
If you check earlier posts and install the dependencies that are mention, you shouldn't have any issue.

---

### Post by demck85 on 2011-06-29
check this site for .deb of forked-dappd:

[http://ftp.us.debian.org/debian/pool/main/f/forked-daapd/]("http://ftp.us.debian.org/debian/pool/main/f/forked-daapd/")

---

### Post by powerpleb on 2011-07-09
Is anyone else having problems using forked-daapd 0.17 with Banshee and Exaile?

It works fine in Rhythmbox, but both Banshee and Exaile are unable to connect.

---

### Post by oldfart101 on 2011-08-23
Would anyone who has compiled for Ubuntu care to upload here? 
The process of compiling on a running system is a bit daunting for me!

Also a question
Should the .remote file be with the mp3 s?. (same directory as specified in the .conf file)

---

### Post by sashxp on 2011-09-17
i can't compile forked v0.19 with natty - i think that i stuck with the antl3r things.
Is it possible to get a working v19 .deb from someone who hast compiled it?

Here is my errorlog:

```
gcc -DHAVE_CONFIG_H -I. -I..  -D_GNU_SOURCE -DDATADIR="\"/usr/share/forked-daapd\"" -DCONFDIR="\"/etc\"" -DSTATEDIR="\"/var\"" -DPKGLIBDIR="\"/usr/lib/forked-daapd\""  -DFLAC -DMUSEPACK -D_REENTRANT -I/usr/include/taglib   -D_THREAD_SAFE -D_REENTRANT -I/usr/include/alsa   -g -O2 -Wall -D_LARGEFILE_SOURCE -MT forked_daapd-RSPLexer.o -MD -MP -MF .deps/forked_daapd-RSPLexer.Tpo -c -o forked_daapd-RSPLexer.o `test -f 'RSPLexer.c' || echo './'`RSPLexer.c
RSPLexer.c: In function ‘RSPLexerNew’:
RSPLexer.c:318:5: error: too few arguments to function ‘antlr3LexerNewStream’
/usr/include/antlr3defs.h:544:28: note: declared here
RSPLexer.c: In function ‘mQUOTE’:
RSPLexer.c:414:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mLPAR’:
RSPLexer.c:453:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mRPAR’:
RSPLexer.c:492:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mAND’:
RSPLexer.c:532:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mOR’:
RSPLexer.c:572:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mNOT’:
RSPLexer.c:611:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mEQUAL’:
RSPLexer.c:650:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mINCLUDES’:
RSPLexer.c:690:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mSTARTSW’:
RSPLexer.c:730:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mENDSW’:
RSPLexer.c:770:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mGREATER’:
RSPLexer.c:809:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mLESS’:
RSPLexer.c:848:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mGTE’:
RSPLexer.c:888:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mLTE’:
RSPLexer.c:928:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mBEFORE’:
RSPLexer.c:968:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mAFTER’:
RSPLexer.c:1008:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mDAY’:
RSPLexer.c:1077:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1078:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1079:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1080:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1091:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1092:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1093:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1094:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1105:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1106:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1107:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1108:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1137:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mWEEK’:
RSPLexer.c:1211:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1212:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1213:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1214:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1225:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1226:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1227:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1228:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1239:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1240:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1241:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1242:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1253:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1254:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1255:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1256:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1285:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mMONTH’:
RSPLexer.c:1364:49: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1365:49: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1366:49: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1367:49: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1378:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1379:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1380:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1381:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1392:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1393:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1394:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1395:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1406:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1407:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1408:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1409:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1420:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1421:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1422:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1423:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1452:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mYEAR’:
RSPLexer.c:1526:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1527:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1528:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1529:41: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1540:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1541:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1542:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1543:33: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1554:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1555:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1556:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1557:25: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1568:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1569:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1570:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1571:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1600:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mTODAY’:
RSPLexer.c:1640:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mNEWLINE’:
RSPLexer.c:1703:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mWS’:
RSPLexer.c:1745:13: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1746:13: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1752:19: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘channel’
RSPLexer.c:1757:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mFIELD’:
RSPLexer.c:1835:22: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1836:22: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:1857:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mINT’:
RSPLexer.c:1932:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mDATE’:
RSPLexer.c:1999:21: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2000:21: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2001:21: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2002:21: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2061:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2062:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2063:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2064:17: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2110:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mSTR’:
RSPLexer.c:2188:26: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2189:26: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2207:37: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘tokFactory’
RSPLexer.c:2207:65: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘tokFactory’
RSPLexer.c:2229:11: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2230:11: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2243:14: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘text’
RSPLexer.c:2248:7: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘type’
RSPLexer.c: In function ‘mESCAPED’:
RSPLexer.c:2302:21: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2303:21: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2304:21: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2305:21: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2319:23: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘text’
RSPLexer.c:2330:23: error: ‘struct ANTLR3_LEXER_struct’ has no member named ‘text’
RSPLexer.c:2275:16: warning: unused variable ‘_type’
RSPLexer.c: In function ‘mDIGIT09’:
RSPLexer.c:2366:16: warning: unused variable ‘_type’
RSPLexer.c: In function ‘mDIGIT19’:
RSPLexer.c:2402:16: warning: unused variable ‘_type’
RSPLexer.c: In function ‘mTokens’:
RSPLexer.c:2569:15: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2570:15: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2571:15: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2572:15: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2607:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2608:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2609:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2610:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2715:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2716:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2717:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2718:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2833:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2834:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2835:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2836:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2931:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2932:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2933:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:2934:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3039:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3040:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3041:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3042:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3127:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3128:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3129:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3130:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3225:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3226:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3227:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3228:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3333:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3334:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3335:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3336:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3431:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3432:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3433:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3434:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3499:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3500:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3501:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3502:19: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3597:13: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3598:13: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3599:13: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
RSPLexer.c:3600:13: error: ‘struct ANTLR3_BASE_RECOGNIZER_struct’ has no member named ‘exception’
make[2]: *** [forked_daapd-RSPLexer.o] Error 1
make[2]: Leaving directory `/home/sascha/forked-daapd-0.19/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/sascha/forked-daapd-0.19/src'
make: *** [install-recursive] Error 1
```

thanks!

sash

---

### Post by demck85 on 2011-10-13
This site has it complied already:
[http://ftp.us.debian.org/debian/pool/main/f/forked-daapd/](http://ftp.us.debian.org/debian/pool/main/f/forked-daapd/)

Though, I'm on 11.04 64bit and having a lot of dependencies issues now getting it installed.

---

### Post by Rezista on 2011-10-23
I was able to get this installed easily on my 11.10 server.

However I wanted to add AlbumArtSmall as a file to look for in artwork.c so i downloaded the source from launchpad + github.

Regardless of which one I use, the final executable is 1.5mb in size (the executable in the .deb is 500k), and it won't work with my iPhone (the .deb one does).

Has anyone been able to successfully compile either version and have it working?

---

### Post by matog on 2011-10-28
I've installed forked-daapd in 11.10.
I type:
```
mato@mato-Unity:~$ sudo /usr/sbin/forked-daapd
[sudo] password for mato: 
    main: Forked Media Server Version 0.19 taking off
mato@mato-Unity:~$ 

```

but when it try to connect to the server throug my ipod touch (It worked fine with mt-daapd) iPod says "Cannont Connect"

How can I see if forked-daapd is running? No program running in the system monitor....

Regards,
Mato.-

---

### Post by mashedbear on 2011-10-29
One way to see what forked-daapd is doing is to look at the log file. 

Try ```
tail -f /var/log/forked-daapd.log
```

I have installed forked-daapd using ubuntu software center in 11.10, and am having problems getting it running. (I did have mt-daapd running nicely but 11.10 upgrade broke that - [http://ubuntuforums.org/showthread.php?p=11384566#post11384566](http://ubuntuforums.org/showthread.php?p=11384566#post11384566))

I have edited my config file /etc/forked-daapd.conf to point to where my music files are. I haven't changed anything else.

When I fire up forked-daapd with sudo /usr/sbin/forked-daapd I am getting the following problem - any ideas?
 
> tail -f /var/log/forked-daapd.log 
[2011-10-29 09:24:07]     main: Forked Media Server Version 0.19 taking off
[2011-10-29 09:24:07]     main: mDNS init
[2011-10-29 09:24:07]     mdns: Avahi state change: Client running
[2011-10-29 09:24:07]    httpd: Could not bind INADDR_ANY:3689
[2011-10-29 09:24:07]     main: HTTPd thread failed to start
[2011-10-29 09:24:07]     main: Player deinit
[2011-10-29 09:24:07]     main: File scanner deinit
[2011-10-29 09:24:07]     main: Database deinit
[2011-10-29 09:24:07]     main: mDNS deinit
[2011-10-29 09:24:07]     main: Exiting.

---

### Post by mashedbear on 2011-10-29
Works now. Restarted system!

---

### Post by matog on 2011-10-29
> **mashedbear said:**
> One way to see what forked-daapd is doing is to look at the log file. 

Try ```
tail -f /var/log/forked-daapd.log
```

I have installed forked-daapd using ubuntu software center in 11.10, and am having problems getting it running. (I did have mt-daapd running nicely but 11.10 upgrade broke that - [http://ubuntuforums.org/showthread.php?p=11384566#post11384566](http://ubuntuforums.org/showthread.php?p=11384566#post11384566))

I have edited my config file /etc/forked-daapd.conf to point to where my music files are. I haven't changed anything else.

When I fire up forked-daapd with sudo /usr/sbin/forked-daapd I am getting the following problem - any ideas?

Same problem here. But restarting system didn't solve anything...

Regards,
Mato.-

---

### Post by mashedbear on 2011-10-29
Is the process running? You can tell by 

> ps -A | grep daap

Should return something like

>  1142 ?        00:01:10 forked-daapd

---

### Post by matog on 2011-10-31
The process is not running, and the log shows:

```
[2011-10-31 20:47:52]     main: Forked Media Server Version 0.19 taking off
[2011-10-31 20:47:52]     main: mDNS init
[2011-10-31 20:47:52]     mdns: Avahi state change: Client connecting
[2011-10-31 20:47:52]     mdns: Failed to create service browser: Estado incorrecto
[2011-10-31 20:47:52]   player: Could not add mDNS browser for AirTunes devices
[2011-10-31 20:47:52]     main: Player thread failed to start
[2011-10-31 20:47:52]     main: File scanner deinit
[2011-10-31 20:47:53]     main: Database deinit
[2011-10-31 20:47:53]     main: mDNS deinit
[2011-10-31 20:47:53]     main: Exiting.
```

---

### Post by mashedbear on 2011-11-02
Hey matog - whats your config file look like?

---

### Post by matog on 2011-11-02
> **mashedbear said:**
> Hey matog - whats your config file look like?

```

general {
	# Username
	uid = "daapd"
	logfile = "/var/log/forked-daapd.log"
	# Database location
#	db_path = "/var/cache/forked-daapd/songs3.db"
	# Available levels: fatal, log, warning, info, debug, spam
	loglevel = log
	# Admin password for the non-existent web interface
	admin_password = "mato"
	# Enable/disable IPv6
	ipv6 = no
}

# Library configuration
library {
	# Name of the library as displayed by the clients
	# %h: hostname, %v: version
	name = "My Music on %h"
	# TCP port to listen on. Default port is 3689 (daap)
	port = 3689
	# Password for the library. Optional.
#	password = ""

	# Directories to index
	directories = { "/home/mato/Escritorio/a" }
	# Directories containing compilations
	# Matches anywhere in the path (not a regexp, though)
#	compilations = { "/compilations/" }

	# Should iTunes metadata override ours?
#	itunes_overrides = true

	# Formats: mp4a, mp4v, mpeg, alac, flac, mpc, ogg, wma, wmal, wmav, aif, wav
	# Formats that should never be transcoded
#	no_transcode = { "alac", "mp4a" }
	# Formats that should always be transcoded
#	force_transcode = { "ogg", "flac" }
}

# Local audio output
audio {
	# AirTunes name - used in the speaker list in Remote
	nickname = "Computer"
	# Audio device name for local audio output
#	card = "default"
	# Mixer channel to use for volume control - ALSA/Linux only
	# If not set, PCM will be used if available, otherwise Master.
#	mixer = ""
}

# Airport Express device
#apex "ApEx" {
	# AirTunes password
#	password = "s1kr3t"
#}
```

---

### Post by mashedbear on 2011-11-04
Hey matog
the only difference in mine is admin password - in mine I have

> admin_password = "unused"

Hope this helps!

---

### Post by matog on 2011-11-05
> **mashedbear said:**
> Hey matog
the only difference in mine is admin password - in mine I have



Hope this helps!

Still not working...

---

### Post by zim2dive on 2011-11-13
It appears the version (0.19) from the 11.10 repositories is NOT compiled with --enable-itunes? (it sees my files, but not the playlists I had from iTunes)

(is there a way to tell which flags were set with the repo version?)

---

### Post by mb36 on 2012-02-12
@matog: I had the same message on my dreamplug with debian squeeze. I needed to start avahi-daemon, and then things started working. But on my ubuntu installations I keep getting these messages that there is a problem with avahi and the .local domain of my network, so you might also run into something like that. But that would be another problem. First, try to start the avahi-daemon. Command in terminal: sudo avahi-daemon &

Best regards, Mårten

---

### Post by c-m on 2012-03-03
i've got forked-daap installed on my server. My laptop running banshee shows the name of the share i.e Music at home on..." but it states that it is unable to connect to the music share.

I've changed the port on forked-daap to 1066, and forwarded this through my router. I have set the port in banshee to 1066 too.

My music directory is set correctly.

What should i be adding as the username in the forked-daap conf file? and why doesn't banshee ask for credentials?

What else is there to do?

---

### Post by c-m on 2012-03-09
Works on my Desire S through DAAP in the market.

Yet it won't work on the Galaxy s2 it keeps asking for the password, even though the correct password has already been entered.

Rhythmbox is same. Constantly asks for the password, despite being give the correct one.

---

### Post by c-m on 2012-07-01
Forked-daapd is really rubbish for me compared to mt-daapt.

On initial setup it worked just fine. Now when I connect sometimes my music doesn't show up.

Today connecting, only about 7 of my albums are showing.

---

### Post by chet9119 on 2012-11-28
Anyone else having trouble reaching the web interface in 11.10?

I'm using the user name and pass from the config file, but cannot access.  I'm using the local host so I am assuming there is no router issue.

---

### Post by chet9119 on 2012-11-29
Well - found my own answer - apparently there is no web interface in the forked version.

That said I have it working it 11.10.  Surprisingly easy (and my skills are minimal).  I'm moving files over now to see if it is stable.


used these instructions...only addition is to make sure the ubuntu "Music" file is shared.


[http://macvalley.blogspot.com/2011/02/successful-installation-of-forked-daapd.html](http://macvalley.blogspot.com/2011/02/successful-installation-of-forked-daapd.html)

hope it helps....

---

