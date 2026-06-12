---
title: "Linksys WUSB300N USB Card - help plz!"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by dwalton00 on 2009-08-15
I just installed Linux yesterday (woohoo) and found that my Linksys card wouldn't work with Linux. So, I got ndiswrapper through terminal. I also put the .inf config file I extracted from Linksys' website on my desktop. I went to " **System** | **Administration** | **Windows wireless drivers"** I clicked on " install new driver" and selected the .inf file. It gave me the error "Unable to see if hardware is present," but at the same time my wireless card's lights started flashing. After clicking ok, I was back at the "Wireless Network Drivers" screen and it showed on the left side "netmw245" and said that the hardware is present (although when I reopen "Wireless Network Drivers" it tells me it is unable to see if hardware is present. 

I have been following this guide [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
I am stuck at this step.
 
**3.4.2.1. Check to make sure the driver was installed correctly**

 Run the following command from a Terminal:   ndiswrapper -lIf the driver is installed correctly, you should see the following output:   Installed ndis drivers:
  {name of driver} driver present, hardware presentor   {name of driver} : driver installed
       device ({Chipset ID}) presentIf you don't see this message: 
[LIST=1]
[*]Try a different driver such as the drivers for Windows 2000, or another driver matching the PCI ID on the [ndiswrapper list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List").
[*]This document has a [troubleshooting]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#trouble") section which may provide an answer.
[*]Look for additional help. Read [HowToGetHelp]("https://help.ubuntu.com/community/HowToGetHelp") for more information.
[/LIST]



**When I type "ndiswrapper -l" into terminal, it puts this out **

"install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card"


I decided to try going ahead (even though this might still be an issue.)




**On this step:**
**3.5. Load the new driver module**

 If ndiswrapper correctly associates the driver to the wireless adapter, you are now ready to load the driver into memory, and try to establish a network connection. Open a Terminal and run the following commands:   sudo depmod -a
  sudo modprobe ndiswrapperThen, also in a Terminal, check for error messages:   tail /var/log/messages[B]I get this output:
[/B]
"WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release."





Again, I tried going to the next step just to see what would happen. 



**3.6. Configuring Wireless Network Settings**

  
**3.6.1. Configuring Wireless Network Settings using nm-applet (GNOME front end for Network Manager)**

 If this applet is installed, it makes wireless network connection to multiple networks (roaming) easier - this is useful if you use your laptop to connect to wireless networks at more than one location. 
[LIST=1]
[*]Open the Networking Admin tool (**System** | **Administration** | **Networking**), select the Wireless connection and click **Properties**, ensure the **Enable roaming mode** checkbox is ticked.
[*]Click the Network Manager icon (computers icon in the top right corner of system tray), your network ESSID should be shown in the drop-down list. Select your network by clicking on it.
[*]If the Network requires any further configuration (eg WEP key), a dialog should appear, select the correct settings and paste in your key.
[*]The Network Manager applet uses Keyring Manager to store your passwords - so a second dialog will open after this, asking to create a master password for the keyring manager. Note that you will be requested to enter the Master Keyring password each time you logon - there is a solution to avoid entering a password each time [here]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1").
[*]Your Wireless Network should now be configured - skip to [Automatically loading at Startup]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart")
[/LIST]



I was unable to find **System** | **Administration** | **Networking** so I decided to download the nmapp package. It is on my desktop. I opened the included Install document, and found that I need to compile the package. 

"The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.
     Running `configure' might take a while.  While running, it prints
     some messages telling which features it is checking for.
  2. Type `make' to compile the package.
  3. Optionally, type `make check' to run any self-tests that come with
     the package.
  4. Type `make install' to install the programs and any data files and
     documentation."

When I type ./configure (I'm in the right directory, I get:

"david@david-desktop:~/Desktop/nmapp$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for mode_t... yes
checking for pid_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking for select... yes
checking for socket... yes
checking for uname... yes
checking for intltool >= 0.35.0... 0.37.1 found
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GOBJECT... yes
checking for NMA... configure: error: Package requirements (dbus-glib-1 >= 0.72
         glib-2.0 >= 2.10
         NetworkManager >= 0.7.0
         libnm_glib >= 0.7.0
         libnm-util >= 0.7.0
         libnm_glib_vpn >= 0.7.0
         gtk+-2.0 >= 2.10
         libglade-2.0
         gmodule-export-2.0
         gconf-2.0
         gnome-keyring-1
         libnotify >= 0.4.3) were not met:

No package 'NetworkManager' found
No package 'libnm_glib' found
No package 'libnm-util' found
No package 'libnm_glib_vpn' found
No package 'libglade-2.0' found
No package 'libnotify' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NMA_CFLAGS
and NMA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details"


Thanks in advance for your help!

---

### Post by bkratz on 2009-08-15
> **dwalton00 said:**
> I just installed Linux yesterday (woohoo) and found that my Linksys card wouldn't work with Linux. 
I was unable to find **System** | **Administration** | **Networking** so I decided to download the nmapp package. It is on my desktop. I opened the included Install document, and found that I need to compile the package. 


Sure sounds like you have been through alot! try this link

[http://ubuntuforums.org/showthread.php?t=1226858&highlight=WUSB300N](http://ubuntuforums.org/showthread.php?t=1226858&highlight=WUSB300N)

it explains loading in ndiskgtk which will get you the system-administration- networking you were looking for.

Good Luck

do a search for WUSB300N above and it will show you 26 links.

---

### Post by dwalton00 on 2009-08-15
Haha. What a joke. It had been working all along (at least since I installed the driver...despite the error message). Firefox needed to be restarted. rofl. Thanks for your help!

---

### Post by bkratz on 2009-08-15
Glad to hear it!

---

