---
title: "Error installing TCL in Ubuntu 10.10"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Lewke on 2010-09-24
Hi, I&#7743; trying to install TCL 8.0.5 onto my machine, if i type ¨wish¨ it tells me there are already these programs: 
```
 The program 'wish' can be found in the following packages:
 * tk
 * tk8.4
 * tk8.5
 * tk8.3
Try: sudo apt-get install <selected package> 
```The error trace is here: 
```

luke@luke-laptop:~/Downloads/tcl8.0.5/unix$ ./configure
loading cache ./config.cache
checking for ranlib... ranlib
checking whether cross-compiling... no
checking for getcwd... yes
checking for opendir... yes
checking for strstr... yes
checking for strtol... yes
checking for tmpnam... yes
checking for waitpid... yes
checking for strerror... yes
checking for getwd... yes
checking for wait3... yes
checking for uname... yes
checking for sin... no
checking for -lieee... no
checking dirent.h... yes
checking how to run the C preprocessor... cc -E
checking for errno.h... yes
checking for float.h... yes
checking for values.h... yes
checking for limits.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for sys/wait.h... yes
checking for dlfcn.h... yes
checking for unistd.h... yes
checking termios vs. termio vs. sgtty... termios
checking fd_set and sys/select... yes
checking for sys/time.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for tm_zone in struct tm... yes
checking tm_tzadj in struct tm... no
checking tm_gmtoff in struct tm... yes
checking long timezone variable... yes
checking for st_blksize in struct stat... yes
checking proper strstr implementation... yes
checking for strtoul... yes
checking for strtod... yes
checking for strtod... (cached) yes
checking for Solaris strtod bug... ok
checking for ANSI C header files... yes
checking for mode_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for uid_t in sys/types.h... yes
checking for opendir... (cached) yes
checking union wait... yes
checking matherr support... yes
checking return type of signal handlers... void
checking for vfork... yes
checking vfork/signal bug... ok
checking for strncasecmp... yes
checking for BSDgettimeofday... no
checking for gettimeofday... yes
checking for gettimeofday declaration... present
checking for -linet... no
checking for net/errno.h... no
checking whether char is unsigned... no
checking signed char declarations... yes
checking for connect... yes
checking for gethostbyname... yes
checking system version (for dynamic loading)... ./configure: 1: Syntax error: Unterminated quoted string


```Really not sure whats wrong, I´m horrible with linux if I´m  honest, tried a couple of google searches but didn´t make very much  progress. It´s for my final year project so any help would be greatly  appreciated.

Thanks :smile:

---

### Post by cariboo on 2010-09-24
Are you trying to install an older version on purpose? Various versions of tcl are available in the repositories. Just open up System->Administration->Synaptic Package Manager, or The Software Center, and do a search for tcl.

---

### Post by Lewke on 2010-09-24
> **cariboo907 said:**
> Are you trying to install an older version on purpose? Various versions of tcl are available in the repositories. Just open up System->Administration->Synaptic Package Manager, or The Software Center, and do a search for tcl.

Yes, the SOAR software I´m using for my project requires TCL 8.0 so It´s quite specific

---

### Post by VMC on 2010-09-24
> **Lewke said:**
> Yes, the SOAR software I´m using for my project requires TCL 8.0 so It´s quite specific

Here's the [pool]("http://archive.ubuntu.com/ubuntu/pool/main/t/tcl8.0/") for 8.0.5 to work from. Maybe you can install using one of these.

---

### Post by Lewke on 2010-09-25
> **VMC said:**
> Here's the [pool]("http://archive.ubuntu.com/ubuntu/pool/main/t/tcl8.0/") for 8.0.5 to work from. Maybe you can install using one of these.

Not sure how to install those, there´s no readme or anything in them with instructions... I´m bad at using linux.

---

### Post by Compyx on 2010-09-25
Pick the appropriate .deb file for your architecture and download it (in my case, I run 64-bit Ubuntu 10.04, so I downloaded tcl8.0_8.0.5-8.1_amd64.deb).

Open a terminal and go to the location you saved the file, and enter:
```

sudo dpkg -i tcl8.0_8.0.5-8.1_amd64.deb

```
That should output something similar to this:
```

compyx@compyx-laptop:~/Downloads$ sudo dpkg -i tcl8.0_8.0.5-8.1_amd64.deb
[sudo] password for compyx: 
Selecting previously deselected package tcl8.0.
(Reading database ... 142831 files and directories currently installed.)
Unpacking tcl8.0 (from tcl8.0_8.0.5-8.1_amd64.deb) ...
Setting up tcl8.0 (8.0.5-8.1) ...

Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Alternatively, you could go to the file with Nautilus ("Places" => "Downloads" or "Places" => "Home") and double-click on it: that should open the GDebi installer, which will allow you to install the package using a GUI, if you prefer.

On my system, when I clicked the file in Firefox, Firefox offered to open the file with GDebi, which makes installing the package even easier.


One more thing: you should probably 'pin' the package, so the next time you update your system, the package isn't replaced with a more up-to-date version:

Open Synaptic and search for 'tcl', select 'tcl8.0' and select "Package" => "Lock Version" from the menu. That will keep the package installed even if there's a newer version available (which there is).


Hope this helps.

---

### Post by mc4man on 2010-09-25
I would suggest running this first before trying to install the 8.0 package, tcl uses a dependency package (tcl) that will prevent the 8.0 from being installed if you have the current version installed (8.4

```
sudo apt-get remove tcl
```

If it reports tcl not being installed you'll be fine, go ahead and install the 8.0 package.

If it removes tcl then again go ahead and install the 8.0 package but do this before using. (switch to 8.0
```
sudo update-alternatives  --config tclsh
```

Pick the number for the 8.0 and press enter

Ex.
> doug@doug-laptop:~$ sudo update-alternatives  --config tclsh
There are 3 choices for the alternative tclsh (providing /usr/bin/tclsh).

  Selection    Path               Priority   Status
------------------------------------------------------------
* 0            /usr/bin/tclsh8.4   841       auto mode
 [COLOR="Blue"] 1 [/COLOR]           /usr/bin/tclsh8.0   800       manual mode
  2            /usr/bin/tclsh8.4   841       manual mode
  3            /usr/bin/tclsh8.5   840       manual mode

Press enter to keep the current choice[*], or type selection number:[COLOR="Blue"]1[/COLOR]


---

### Post by Lewke on 2010-09-25
It seemed to have worked (I got all the expected outputs) but now I´m installing SOAR and it asked me to find these files (did a system search, only found one):

tcl.h
libtcl8.0.so (Found this one probably, was called libtcl8.0.so.1)
libtk8.0.so
wish8.0

They´re necessary for the installation and i just can find them... did a file system search from the root directory which returned nothing for most of them.

---

### Post by mc4man on 2010-09-25
you need to return to the 'pool' site and download and install the tcl8.0-dev package **that matches the one you just installed** (the -dev package contains the headers.

---

### Post by Lewke on 2010-09-25
Thanks very much guys, i can find all the files in /usr/lib and /usr/include, now to proceed with installing SOAR :) Never would have been able to do this without you.

---

### Post by Lewke on 2010-09-25
Ran into what seems to be a small error with SOAR, this is the make file:

```

#!/bin/csh
pushd kernel
./configure --with-tcl-lib-dir=/usr/lib --with-tk-lib-dir=/usr/lib
make
popd
pushd interface
./configure --prefix=../.. --with-tcl-lib-dir=/usr/lib --with-tcl-doc-dir=/usr/tcl --with-tk-lib-dir=/usr/lib  --disable-static-soar --disable-static-soartk --enable-dynamic-soar --with-kernel=../kernel
make
cp  libsoar7.3* ../library
popd

```

but the first line keeps giving error as the directory doesn´t exist on the system, not really sure what it should be changed to either. I edited the rest of the things in the file to what they need to be.

---

### Post by VMC on 2010-09-25
> **Lewke said:**
> Thanks very much guys, i can find all the files in /usr/lib and /usr/include, now to proceed with installing SOAR :) Never would have been able to do this without you.

Glad you got it working for your school project.

Will you please mark the topic as solved, thanks.

---

### Post by Lewke on 2010-09-25
> **VMC said:**
> Glad you got it working for your school project.

Will you please mark the topic as solved, thanks.

Still one small problem, even though it´s not quite the same software. Should i make a new topic for it?

---

### Post by ranch hand on 2010-09-25
Yes, there actually a few people that use the forum search to check to see if their problem is already dealt with.  One topic per thread makes that possible.

---

