---
title: "Problems installing jahshaka"
date: 2015-11-23
forum: Multimedia Software
---

### Post by Daniel_Sierra on 2015-11-23
Hi everybody,

I'm trying ti install jahshaka software. The unic instructions are to type 
[INDENT][COLOR=#000080][I]cd /jahshakaDirectory
./configure
make
make install
[/I][/COLOR]
[/INDENT]
But that's what happend when I try
[INDENT][COLOR=#000080]daniel@daniel-Bonobo-WS:~$ cd /home/daniel/Downloads/jahshaka
daniel@daniel-Bonobo-WS:~/Downloads/jahshaka$ ./configure
>>Configuring build type for jahshaka

Project MESSAGE: Jahshaka 2.0 build system
Project MESSAGE: -----------------------------
Project MESSAGE: 
Project MESSAGE: Checking operating system and paths
Project MESSAGE: 
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch /home/daniel/Downloads/jahshaka/Settings.pro:425
Project LOAD(): Feature Settings.pro cannot be found.
---------------------------------------
Jahshaka Configure Script User Commands
---------------------------------------

SYNOPSIS

     ./configure [ switches ]
     ./configure [ switches ] jahshaka
     ./configure [ switches ] jahplayer

DESCRIPTION

     Configures the jahshaka build process to build either jahshaka
     or jahplayer

     By default running configure with no arguments will activate the
     build for jahshaka

     You need to follow the configure command with the make command
     in order to actually build the software!

SWITCHES

     --prefix=path
          sets the path for the installation (default: /usr/local)

     --disable-debug
          sets debug mode off

     --disable-plugins
          disables the plugin build and install

     --enable-static
          disables the dynamic loading of various open libraries

daniel@daniel-Bonobo-WS:~/Downloads/jahshaka$ make
make: *** No targets specified and no makefile found.  Stop.
daniel@daniel-Bonobo-WS:~/Downloads/jahshaka$ 
[/COLOR]
[/INDENT]
I'm pretty newbie with ubuntu and I'm not sure what to do. Any help will be wellcomed. Thanks for your atention

---

### Post by lisati on 2015-11-23
Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

Duplicate of [http://ubuntuforums.org/showthread.php?t=2304004](http://ubuntuforums.org/showthread.php?t=2304004) closed.

---

