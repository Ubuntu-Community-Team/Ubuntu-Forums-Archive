---
title: "Wireless Trouble Broadcom BCM4311"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by epwolfram on 2010-03-03
Hey, this is my first post on this forum. I recently installed Ubuntu Studio on my laptop and thought it would be better than Vista. Well, so far I'm really frustrated. I can't get the wireless network to work, despite several nights and countless hours going in circles. I'm about ready to reinstall vista.
 
Let me tell you what I know. Please help if you can, or at least point me in the right direction.
 
Laptop: Dell Inspiron 1721
Ubuntu Studio 9.10 amd64
Network Controller: Broadcom BCM4311 802.11b/g WLAN
 
eth0 connects to internet just fine
wlan0 produces no ping, no dig, but shows up in lspci
 
I believe that I have correctly installed b43-fwcutter and that it has automatically updated my firmware.
 
Does anyone know how to do the following?
Verify driver installation (I believe it's the b43, which is automatic?)
Verify firmware installation
 
Another wierd thing:
Under the System/administration/network tools hitting "configure" for wlan0 produces the error: "The interface does not exist"
 
networking restart yields: No DHCPOffers Received
 
Thanks for your help.

---

### Post by cchhrriiss121212 on 2010-03-04
This annoyed me a lot when I first tried studio, lucky it's a simple fix. 
See my post on this similar thread:
[http://ubuntuforums.org/showthread.php?t=1418519](http://ubuntuforums.org/showthread.php?t=1418519)

---

### Post by epwolfram on 2010-03-04
Ok, cool, thanks.  I will try this tonight when I get home.  If it turns out to be that easy, I think I might just shoot someone.

You don't want to know what I've [been through]("http://sfbay.craigslist.org/forums/?ID=152604483") on this..  I'll post back to let you know how it goes.

---

### Post by epwolfram on 2010-03-04
Of course it wasn't that easy, what was I thinking!?

Well, I went to this site to get the file:
 [http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)

downloaded: NetworkManager-0.8.tar.gz

of course, it can't be a simple executable.

so, I follow the install functions

> eric@ubuntuLaptop:~$ cd /home/eric/Desktop/network-manager-applet-0.8
eric@ubuntuLaptop:~/Desktop/network-manager-applet-0.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for objdump... objdump
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
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
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
checking whether NLS is requested... yes
checking for intltool >= 0.35.0... ./configure: line 12427: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.

WTFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF??????????????????

can anyone PLEASE help me?!

---

### Post by epwolfram on 2010-03-05
Ok, so now I have the tarball for intltool.  How do I install that?

I downloaded it from: [https://edge.launchpad.net/intltool](https://edge.launchpad.net/intltool)

The readme in the file does not give instructions, and there is no install doc.

Can anyone help?

---

### Post by cchhrriiss121212 on 2010-03-05
Sorry I should have mentioned how to get it. Just go to synaptic package manager under system and search for network manager. Click on the box to install then press apply.
If you ever want software with Ubuntu you should check synaptic before searching the web, the releases in there will always be stable and compatible.

---

### Post by epwolfram on 2010-03-05
Ok, I will try that.  Thanks for your help.

---

### Post by epwolfram on 2010-03-08
Ok, I believe I have it installed, but am not 100% sure. I have a new app called Network Connections (Different name?) and an icon in the upper right with two monitor screens and a red x.
 
Clicking on this icon yields:
Wired Network: Device not managed
Wireless network Device not managed
 
In the Network Connections program, under the wireless tab is 
Name: ifupdown (wlan0) Last Used: Never
 
The edit button is grayed out.
 
Any ideas on the next step?
 
Note: I still don't have wireless, obviously.

---

### Post by cchhrriiss121212 on 2010-03-08
Broadcom devices aren't always working out of the box. Here is a thread that should help with the rest:
[http://ubuntuforums.org/showthread.php?t=1417733&highlight=Broadcom+BCM4311](http://ubuntuforums.org/showthread.php?t=1417733&highlight=Broadcom+BCM4311)

---

### Post by epwolfram on 2010-03-08
This worked!  I'm surfing wireless!
 
Thank you SOOOOO much for your help!
 
+10 karma points :D

---

