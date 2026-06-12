---
title: "GOpenVPN on 9.04 - Jaunty Jackelope"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by darryliswright on 2009-08-22
Hi Everybody,

I'm am trying to setup GopenVPN on Ubuntu release 9.04 and have used the following links to aid in the process:
[http://tranceparance.wordpress.com/2009/02/28/gopenvpn-installation-instructions-for-ubuntu-linux-810/](http://tranceparance.wordpress.com/2009/02/28/gopenvpn-installation-instructions-for-ubuntu-linux-810/)
[http://http://ubuntuforums.org/showthread.php?t=816512&page=2]("http://http//ubuntuforums.org/showthread.php?t=816512&page=2")
[http://gopenvpn.sourceforge.net/](http://gopenvpn.sourceforge.net/)

I have reached the stage where I enter the ./configure command in the terminal and this is the output that I get:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
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
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking return type of signal handlers... void
checking for socket... yes
checking for strrchr... yes
checking for openvpn... no
[COLOR=Blue]**configure: error: openvpn was not installed**[/COLOR]

I am a little confused as to why it is not being installed. I have all the prerequisite programs installed and had very little, if any, issues with that. 

The next command would be "make", but I am not comfortable with running it until I can sort the above error out.

Any suggestions on why I would be getting this error?

Thanks all,

---

### Post by mattias.jn on 2009-08-22
Sorry if this offends you, but have you actually installed openVPN (check synaptic)? I'm no expert but I think that GopenVpn and all that other stuff is just "front-end" thing to help in the use of the actual open vpn client.

I have tried to install the program my self but I get stuck at the autogen stage so I'm guessing you'll sort this out quicker than me ;) 

Be sure to post your progress cause from what I can see from google we are not alone in this quest ;)

---

### Post by sefs on 2009-08-22
```

sudo apt-get install openvpn 

```

Should do the trick.

---

