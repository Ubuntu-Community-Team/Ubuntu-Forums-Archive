---
title: "Cant Play mp3 files"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by marenkar on 2007-08-05
I tried to do what the HOWTO said and this came out

admin@admin-desktop:~$ sudo mkdir mplyr
mkdir: cannot create directory `mplyr': File exists
admin@admin-desktop:~$ cd mplyr
admin@admin-desktop:~/mplyr$ # get & install Ubuntu packages
admin@admin-desktop:~/mplyr$ apt-get install manpages-dev automake autoconf libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev -y
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
admin@admin-desktop:~/mplyr$ #
admin@admin-desktop:~/mplyr$ # get mplayer program
admin@admin-desktop:~/mplyr$ wget [http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5try2.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5try2.tar.bz2)
--16:05:28--  [http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5try2.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5try2.tar.bz2)
           => `MPlayer-1.0pre5try2.tar.bz2'
Resolving www1.mplayerhq.hu... 213.144.138.186
Connecting to www1.mplayerhq.hu|213.144.138.186|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,073,725 (4.8M) [text/plain]
MPlayer-1.0pre5try2.tar.bz2: Permission denied

Cannot write to `MPlayer-1.0pre5try2.tar.bz2' (Permission denied).
admin@admin-desktop:~/mplyr$ #
admin@admin-desktop:~/mplyr$ # get codecs
admin@admin-desktop:~/mplyr$ wget [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2)
--16:05:38--  [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2)
           => `essential-20041107.tar.bz2'
Resolving ftp5.mplayerhq.hu... 143.248.234.110
Connecting to ftp5.mplayerhq.hu|143.248.234.110|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.kaist.ac.kr/mplayer/releases/codecs/essential-20041107.tar.bz2](http://ftp.kaist.ac.kr/mplayer/releases/codecs/essential-20041107.tar.bz2) [following]
--16:05:43--  [http://ftp.kaist.ac.kr/mplayer/releases/codecs/essential-20041107.tar.bz2](http://ftp.kaist.ac.kr/mplayer/releases/codecs/essential-20041107.tar.bz2)
           => `essential-20041107.tar.bz2'
Resolving ftp.kaist.ac.kr... 143.248.234.110
Reusing existing connection to ftp5.mplayerhq.hu:80.
HTTP request sent, awaiting response... 404 Not Found
16:05:48 ERROR 404: Not Found.

admin@admin-desktop:~/mplyr$ #
admin@admin-desktop:~/mplyr$ # get fonts
admin@admin-desktop:~/mplyr$ wget [http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2)
--16:05:48--  [http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2)
           => `font-arial-iso-8859-1.tar.bz2'
Resolving ftp5.mplayerhq.hu... 143.248.234.110
Connecting to ftp5.mplayerhq.hu|143.248.234.110|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.kaist.ac.kr/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2](http://ftp.kaist.ac.kr/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2) [following]
--16:06:00--  [http://ftp.kaist.ac.kr/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2](http://ftp.kaist.ac.kr/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2)
           => `font-arial-iso-8859-1.tar.bz2'
Resolving ftp.kaist.ac.kr... 143.248.234.110
Reusing existing connection to ftp5.mplayerhq.hu:80.
HTTP request sent, awaiting response... 404 Not Found
16:06:09 ERROR 404: Not Found.

admin@admin-desktop:~/mplyr$ #
admin@admin-desktop:~/mplyr$ # get skin (my default skin is "phony")
admin@admin-desktop:~/mplyr$ # ***********************************
admin@admin-desktop:~/mplyr$ # go to [http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html) to choose a
admin@admin-desktop:~/mplyr$ # different skin. Right Click your favourite *** [HTTP] *** skin, Copy Link Location,
admin@admin-desktop:~/mplyr$ # paste it over the following line after wget)
admin@admin-desktop:~/mplyr$ # ***********************************
admin@admin-desktop:~/mplyr$ wget [http://ftp5.mplayerhq.hu/mplayer/Skin/phony-1.1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/Skin/phony-1.1.tar.bz2)
--16:06:09--  [http://ftp5.mplayerhq.hu/mplayer/Skin/phony-1.1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/Skin/phony-1.1.tar.bz2)
           => `phony-1.1.tar.bz2'
Resolving ftp5.mplayerhq.hu... 143.248.234.110
Connecting to ftp5.mplayerhq.hu|143.248.234.110|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.kaist.ac.kr/mplayer/Skin/phony-1.1.tar.bz2](http://ftp.kaist.ac.kr/mplayer/Skin/phony-1.1.tar.bz2) [following]
--16:06:14--  [http://ftp.kaist.ac.kr/mplayer/Skin/phony-1.1.tar.bz2](http://ftp.kaist.ac.kr/mplayer/Skin/phony-1.1.tar.bz2)
           => `phony-1.1.tar.bz2'
Resolving ftp.kaist.ac.kr... 143.248.234.110
Reusing existing connection to ftp5.mplayerhq.hu:80.
HTTP request sent, awaiting response... 404 Not Found
16:06:27 ERROR 404: Not Found.

admin@admin-desktop:~/mplyr$ #
admin@admin-desktop:~/mplyr$ tar -xjf MPlayer-1.0pre5try2.tar.bz2
tar: MPlayer-1.0pre5try2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
admin@admin-desktop:~/mplyr$ cd MPlayer-1.0pre5try2
bash: cd: MPlayer-1.0pre5try2: No such file or directory
admin@admin-desktop:~/mplyr$ ./configure --enable-gui
bash: ./configure: No such file or directory
admin@admin-desktop:~/mplyr$ make
bash: make: command not found
admin@admin-desktop:~/mplyr$ make install
bash: make: command not found
admin@admin-desktop:~/mplyr$ #
admin@admin-desktop:~/mplyr$ cd ..
admin@admin-desktop:~$ tar -xjf essential-20041107.tar.bz2
tar: essential-20041107.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
admin@admin-desktop:~$ mkdir -p /usr/local/lib/codecs
mkdir: cannot create directory `/usr/local/lib/codecs': Permission denied
admin@admin-desktop:~$ cp essential-20041107/* /usr/local/lib/codecs/
cp: target `/usr/local/lib/codecs/' is not a directory: No such file or directory
admin@admin-desktop:~$ #
admin@admin-desktop:~$ tar -xjf font-arial-iso-8859-1.tar.bz2
tar: font-arial-iso-8859-1.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
admin@admin-desktop:~$ cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
cp: target `/usr/local/share/mplayer/font/' is not a directory: No such file or directory
admin@admin-desktop:~$ #
admin@admin-desktop:~$ # ***********************************
admin@admin-desktop:~$ # If you decide on a different skin, you'll have to change the name "phony"
admin@admin-desktop:~$ # (after tar -xfj) to your skin file name
admin@admin-desktop:~$ # ***********************************
admin@admin-desktop:~$ tar -xjf phony-1.1.tar.bz2
tar: phony-1.1.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
admin@admin-desktop:~$ mkdir -p /usr/local/share/mplayer/Skin/default
mkdir: cannot create directory `/usr/local/share/mplayer': Permission denied
admin@admin-desktop:~$ # ***********************************
admin@admin-desktop:~$ # change the word "phony" with the name of your preferred skin
admin@admin-desktop:~$ # ***********************************
admin@admin-desktop:~$ cp -r phony/* /usr/local/share/mplayer/Skin/default/
cp: target `/usr/local/share/mplayer/Skin/default/' is not a directory: No such file or directory
admin@admin-desktop:~$ #
admin@admin-desktop:~$ cp MPlayer-1.0pre5try2/etc/* /usr/local/etc/mplayer/
cp: target `/usr/local/etc/mplayer/' is not a directory: No such file or directory
admin@admin-desktop:~$ #
admin@admin-desktop:~$ # get dvd codecs
admin@admin-desktop:~$ wget [http://www.las.ic.unicamp.br/pub/debian.d/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb](http://www.las.ic.unicamp.br/pub/debian.d/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb)
--16:06:27--  [http://www.las.ic.unicamp.br/pub/debian.d/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb](http://www.las.ic.unicamp.br/pub/debian.d/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb)
           => `libdvdcss2_1.2.8-0.0_i386.deb'
Resolving [www.las.ic.unicamp.br](www.las.ic.unicamp.br)... 143.106.60.116
Connecting to www.las.ic.unicamp.br|143.106.60.116|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:06:36 ERROR 404: Not Found.

admin@admin-desktop:~$ #
admin@admin-desktop:~$ # install dvd codecs
admin@admin-desktop:~$ dpkg -i libdvdcss2_1.2.8-0.0_i386.deb
dpkg: requested operation requires superuser privilege
admin@admin-desktop:~$ #
admin@admin-desktop:~$ cd ..
admin@admin-desktop:/home$ # start gmplayer program
admin@admin-desktop:/home$ gmplayer
bash: gmplayer: command not found
admin@admin-desktop:/home$ #
admin@admin-desktop:/home$ exit


What should i do?

---

### Post by Gremlinzzz on 2007-08-06
Get the deb package if your using ubuntu get smplayer package (Qt3; without KDE support)
if your using kubuntu get smplayer package (Qt3; with KDE support)
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
right click on downloaded package and choose the deb installer
next get codecs
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
paste command in terminal
after go into synaptic package manager and unistall totem mozilla plugin then in same package manager install mplayermozilla plugin

---

### Post by marenkar on 2007-08-06
tnx but where can I find synaptic package manager? Sorry I'm a noob so far in ubuntu

Btw i got an error when I tried to choose the deb installer this came out, Error: Dependency is not satisfiable:mplayer|mplayer-nogui

---

### Post by ubuntu27 on 2007-08-06
Check the links on my signature.

[Can't play mp3, wmv and other files? You need to install Codecs.]("https://help.ubuntu.com/community/RestrictedFormats"). 

 ["Tutorial on How to install anything in Ubuntu"]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Gremlinzzz on 2007-08-06
Being a noob you would have a easier time with a out of the box system like mint
[http://distrowatch.com/?newsid=04261](http://distrowatch.com/?newsid=04261)
:guitar:
[http://www.linuxmint.com/cassandra.html](http://www.linuxmint.com/cassandra.html)

---

