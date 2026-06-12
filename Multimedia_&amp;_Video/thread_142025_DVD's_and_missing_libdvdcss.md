---
title: "DVD's and missing libdvdcss"
date: 2006-03-09
forum: Multimedia &amp; Video
---

### Post by sdb2028 on 2006-03-09
I get this error message when trying to play a DVD, I try'd to find the file to install. Can't find it in Synaptic and here is what I get from apt-get:> Reading package lists... Done
Building dependency tree... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate
Any suggestions?

---

### Post by John.Michael.Kane on 2006-03-09
```
## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free


```

should have the codecs you need.. please make sure it is legal to use in your country...

---

### Post by sdb2028 on 2006-03-09
I get the same message.
I downloaded libdvdcss2_1.2.9-1_i386.deb from [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)
and extracted it to tmp.
How do I proceed from there? I have been using apt-get and Synaptic so long I don't remember how to tar!
Thanks.

---

### Post by slacker990 on 2006-03-09
I found this in another post, and it worked for me.

[begin snip]

1. sudo apt-get install libdvdread3
2. sudo /usr/share/doc/libdvdread3/examples/install-css.sh
3. sudo apt-get install wget
4. cd /tmp; wget [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
5. sudo dpkg -i w32codecs_20050412-0.0_i386.deb
6. sudo apt-get install vlc
7. vlc /media/cdrom

Explanation:

1. You need to install the libdvdread3 library if it isn't already installed and that contains a script to install the libdvdcss, which is used for DVD decryption.
2. This command installs libdvdcss
3. This installs wget, which is a good command-line utility for grabbing stuff off the web
4. This downloads the win32 codecs that are used to help play DVDs and other non-free formats.
5. This installs the downloaded win32 codecs
6. This installs the vlc application that will be used to play the DVDs. This is important because totem DOESN'T WORK with a Dell 700m for whatever reason and crashes everytime no matter what you try. I think this is because it cannot handle some types of DVD audio streams (the more common type) and bails. It probably can play older DVDs but not newer ones.

[end snip]

---

### Post by John.Michael.Kane on 2006-03-09
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by sdb2028 on 2006-03-09
I ran the tar files, unfortunately it set everything up in temp---not suposed to be there right. also, now I can't log in as user. I get an error mesage that say's the session lasted less than 10 seconds(then some more gibberish) i click ok and it goes back to the log in screen.
How might I fix this?

---

### Post by sdb2028 on 2006-03-09
Here is the exact read from the .xsession-errors file
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "steve"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied

This happened right after I ran:
> sudo tar xvzf control.tar.gz and
sudo tar xvzf data.tar.gz
which are the 2 files extracted from the
> libdvdcss2_1.2.9-1_i386.deb file

---

### Post by sdb2028 on 2006-03-09
By the way slacker990, Thanks, I will try that approach when I can log back in as user. Right now I'm logged in as root (I know) and don't like to do to much installation from here unless absolutely necessary since all the safe guards are  turned off.

---

### Post by sdb2028 on 2006-03-09
Made a change to the info you sent-- #4 had the wrong ftp address:
Can you tell me where you found that info, I will post there too to give the right address.
> 1. sudo apt-get install libdvdread3
2. sudo /usr/share/doc/libdvdread3/examples/install-css.sh
3. sudo apt-get install wget
4. cd /tmp; wget [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
5. sudo dpkg -i w32codecs_20050412-0.0_i386.deb
6. sudo apt-get install vlc
7. vlc /media/cdrom

Never mind... Just truncated it. I found the error there.

---

### Post by t3h_mounty on 2006-03-14
I'm having some issues installing libdvdcss

after much fun and heartache, I've managed to get this far
```
rawrusk8u@Lenore:/home$ sudo /usr/share/doc/libdvdread3/examples/install-css.sh
No binary deb available.  Will try to build and install it.
You need to have debhelper, dpkg-dev and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

--03:50:12--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz
           => `libdvdcss_1.2.5.orig.tar.gz.9'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 267,699 (261K) [application/x-tar]

100%[====================================>] 267,699       66.15K/s    ETA 00:00

03:50:18 (49.97 KB/s) - `libdvdcss_1.2.5.orig.tar.gz.9' saved [267699/267699]

--03:50:18--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.diff.gz
           => `libdvdcss_1.2.5-1.diff.gz.9'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20 [text/plain]

100%[====================================>] 20            --.--K/s

03:50:18 (2.72 MB/s) - `libdvdcss_1.2.5-1.diff.gz.9' saved [20/20]

--03:50:18--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.dsc
           => `libdvdcss_1.2.5-1.dsc.9'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 341 [text/plain]

100%[====================================>] 341           --.--K/s

03:50:19 (36.13 MB/s) - `libdvdcss_1.2.5-1.dsc.9' saved [341/341]

dpkg-source: extracting libdvdcss in libdvdcss-1.2.5
dpkg-source: unpacking libdvdcss_1.2.5.orig.tar.gz
dpkg-source: applying ./libdvdcss_1.2.5-1.diff.gz
dh_testdir
./configure --prefix=/usr --mandir=${prefix}/share/man \
        --infodir=${prefix}/share/info
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77

```

I'd show the contents of "config.log" as well, but I don't know where it is. Any help at all would be very much appreciated.

---

### Post by sdb2028 on 2006-03-14
Did you try this exactly as written?
The url in step 4 has been truncated; right click   and "copy link location" to terminal along with "cd /tmp: wget"
1. sudo apt-get install libdvdread3
2. sudo /usr/share/doc/libdvdread3/examples/install-css.sh
3. sudo apt-get install wget
4. cd /tmp; wget [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
5. sudo dpkg -i w32codecs_20050412-0.0_i386.deb
6. sudo apt-get install vlc
7. vlc /media/cdrom

---

