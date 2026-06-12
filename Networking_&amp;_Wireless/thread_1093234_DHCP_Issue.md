---
title: "DHCP Issue"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by Keymaster on 2009-03-11
I have 3 IBM eServers that randomly restart the networking interface as DHCP despite the fact that they have static IPs in /etc/network/interfaces

Here is a sample of one of the /etc/network/interfaces files (they are all the same except +1 to the last octet):
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
 address 172.25.0.173
 netmask 255.255.255.0
 gateway 172.25.0.1
```

Here is a list of installed packages:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                  Version                               Description
+++-=====================================-=====================================-============================================
ii  adduser                               3.105ubuntu1                          add and remove users and groups
ii  apparmor                              2.1+1075-0ubuntu9.1                   User-space parser utility for AppArmor
ii  apparmor-utils                        2.1+1075-0ubuntu9.1                   Utilities for controlling AppArmor
ii  apt                                   0.7.9ubuntu17.1                       Advanced front-end for dpkg
ii  apt-utils                             0.7.9ubuntu17.1                       APT utility programs
ii  aptitude                              0.4.9-2ubuntu5                        terminal-based package manager
ii  at                                    3.1.10ubuntu4                         Delayed job execution and batch processing
ii  base-files                            4.0.1ubuntu5.8.04.4                   Debian base system miscellaneous files
ii  base-passwd                           3.5.16                                Debian base system master password and group
ii  bash                                  3.2-0ubuntu18                         The GNU Bourne Again SHell
ii  bash-completion                       20060301-3ubuntu3                     programmable completion for the bash shell
ii  belocs-locales-bin                    2.4-2.2ubuntu7                        tools for compiling locale data files
ii  bind9-host                            1:9.4.2.dfsg.P2-2ubuntu0.1            Version of 'host' bundled with BIND 9.X
ii  bsdmainutils                          6.1.10ubuntu2                         collection of more utilities from FreeBSD
ii  bsdutils                              1:2.13.1-5ubuntu3                     Basic utilities from 4.4BSD-Lite
ii  busybox-initramfs                     1:1.1.3-5ubuntu12                     Standalone shell setup for initramfs
ii  bzip2                                 1.0.4-2ubuntu4                        high-quality block-sorting file compressor -
ii  command-not-found                     0.2.17ubuntu1                         Suggest installation of packages in interact
ii  command-not-found-data                0.2.17ubuntu1                         Set of data files for command-not-found.
ii  console-setup                         1.21ubuntu9                           Set up the font and the keyboard on the cons
ii  console-terminus                      4.20-6                                Fixed-width fonts for fast reading on the Li
ii  console-tools                         1:0.2.3dbs-65ubuntu7                  Linux console and font utilities
ii  coreutils                             6.10-3ubuntu2                         The GNU core utilities
ii  cpio                                  2.9-6ubuntu1                          GNU cpio -- a program to manage archives of 
ii  cpp                                   4:4.2.3-1ubuntu6                      The GNU C preprocessor (cpp)
ii  cpp-4.2                               4.2.4-1ubuntu3                        The GNU C preprocessor
ii  cron                                  3.0pl1-100ubuntu2                     management of regular background processing
ii  dash                                  0.5.4-8ubuntu1                        POSIX-compliant shell
ii  debconf                               1.5.20                                Debian configuration management system
ii  debconf-i18n                          1.5.20                                full internationalization support for debcon
ii  debianutils                           2.28.2-0ubuntu1                       Miscellaneous utilities specific to Debian
ii  dhcp3-client                          3.0.6.dfsg-1ubuntu9                   DHCP client
ii  dhcp3-common                          3.0.6.dfsg-1ubuntu9                   common files used by all the dhcp3* packages
ii  diff                                  2.8.1-12ubuntu1                       File comparison utilities
ii  dmidecode                             2.9-1ubuntu1                          Dump Desktop Management Interface data
ii  dnsutils                              1:9.4.2.dfsg.P2-2ubuntu0.1            Clients provided with BIND
ii  dosfstools                            2.11-2.3ubuntu1                       Utilities to create and check MS-DOS FAT fil
ii  dpkg                                  1.14.16.6ubuntu4                      package maintenance system for Debian
ii  e2fslibs                              1.40.8-2ubuntu2                       ext2 filesystem libraries
ii  e2fsprogs                             1.40.8-2ubuntu2                       ext2 file system utilities and libraries
ii  ed                                    0.7-1ubuntu1                          The classic unix line editor
ii  eject                                 2.1.5-6ubuntu1                        ejects CDs and operates CD-Changers under Li
ii  ethtool                               6-0                                   display or change ethernet card settings
ii  fdutils                               5.5-20060227-1.1                      Linux floppy utilities
ii  file                                  4.21-3ubuntu1                         Determines file type using "magic" numbers
ii  findutils                             4.2.32-1ubuntu2                       utilities for finding files--find, xargs
ii  friendly-recovery                     0.1.2                                 Make recovery more user-friendly
ii  ftp                                   0.17-16build1                         The FTP client
ii  fuse-utils                            2.7.2-1ubuntu2                        Filesystem in USErspace (utilities)
ii  gcc-4.2-base                          4.2.4-1ubuntu3                        The GNU Compiler Collection (base package)
ii  gettext-base                          0.17-2ubuntu1                         GNU Internationalization utilities for the b
ii  gnupg                                 1.4.6-2ubuntu5                        GNU privacy guard - a free PGP replacement
ii  gpgv                                  1.4.6-2ubuntu5                        GNU privacy guard - signature verification t
ii  grep                                  2.5.3~dfsg-3                          GNU grep, egrep and fgrep
ii  groff-base                            1.18.1.1-16                           GNU troff text-formatting system (base syste
ii  grub                                  0.97-29ubuntu21.1                     GRand Unified Bootloader
ii  gzip                                  1.3.12-3.2                            The GNU compression utility
ii  hdparm                                8.6-1ubuntu1                          tune hard disk parameters for high performan
ii  hostname                              2.94                                  utility to set/show the host name or domain 
ii  ifupdown                              0.6.8ubuntu8                          high level tools to configure network interf
ii  info                                  4.11.dfsg.1-4                         Standalone GNU Info documentation browser
ii  initramfs-tools                       0.85eubuntu39.3                       tools for generating an initramfs
ii  initscripts                           2.86.ds1-14.1ubuntu45                 Scripts for initializing and shutting down t
ii  inputattach                           1.23-0ubuntu2                         utility to attach serial devices to the inpu
ii  installation-report                   2.31ubuntu1                           system installation report
ii  iproute                               20071016-2ubuntu2                     Professional tools to control the networking
ii  iptables                              1.3.8.0debian1-1ubuntu2               administration tools for packet filtering an
ii  iputils-arping                        3:20071127-1                          Tool to send ICMP echo requests to an ARP ad
ii  iputils-ping                          3:20071127-1                          Tools to test the reachability of network ho
ii  iputils-tracepath                     3:20071127-1                          Tools to trace the network path to a remote 
ii  iscsitarget                           0.4.15-5ubuntu2                       iSCSI Enterprise Target userland tools
ii  klibc-utils                           1.5.7-4ubuntu4                        small statically-linked utilities built with
ii  klogd                                 1.5-1ubuntu1                          Kernel Logging Daemon
ii  laptop-detect                         0.13.2ubuntu1                         attempt to detect a laptop
ii  less                                  418-1                                 Pager program similar to more
ii  libacl1                               2.2.45-1                              Access control list shared library
ii  libatm1                               2.4.1-17.1build1                      shared library for ATM (Asynchronous Transfe
ii  libattr1                              1:2.4.39-1                            Extended attribute shared library
ii  libauthen-pam-perl                    0.16-1                                Perl interface to PAM library
ii  libbind9-30                           1:9.4.2.dfsg.P2-2ubuntu0.1            BIND9 Shared Library used by BIND
ii  libblkid1                             1.40.8-2ubuntu2                       block device id library
ii  libbz2-1.0                            1.0.4-2ubuntu4                        high-quality block-sorting file compressor l
ii  libc6                                 2.7-10ubuntu4                         GNU C Library: Shared libraries
ii  libc6-i686                            2.7-10ubuntu4                         GNU C Library: Shared libraries [i686 optimi
ii  libcap1                               1:1.10-14build1                       support for getting/setting POSIX.1e capabil
ii  libck-connector0                      0.2.3-3ubuntu5                        ConsoleKit libraries
ii  libcomerr2                            1.40.8-2ubuntu2                       common error description library
ii  libconsole                            1:0.2.3dbs-65ubuntu7                  Shared libraries for Linux console and font 
ii  libcurl3-gnutls                       7.18.0-1ubuntu2                       Multi-protocol file transfer library (GnuTLS
ii  libcwidget3                           0.5.8-1ubuntu1                        high-level terminal interface library for C+
ii  libdb4.6                              4.6.21-6ubuntu1                       Berkeley v4.6 Database Libraries [runtime]
ii  libdbus-1-3                           1.1.20-1ubuntu3.2                     simple interprocess messaging system
ii  libdevmapper1.02.1                    2:1.02.20-2ubuntu2                    The Linux Kernel Device Mapper userspace lib
ii  libdns35                              1:9.4.2.dfsg.P2-2ubuntu0.1            DNS Shared Library used by BIND
ii  libedit2                              2.9.cvs.20050518-4                    BSD editline and history libraries
ii  libelfg0                              0.8.6-4                               an ELF object file access library
ii  libexpat1                             2.0.1-0ubuntu1                        XML parsing C library - runtime library
ii  libfribidi0                           0.10.9-1                              Free Implementation of the Unicode BiDi algo
ii  libfuse2                              2.7.2-1ubuntu2                        Filesystem in USErspace library
ii  libgc1c2                              1:6.8-1.1                             conservative garbage collector for C and C++
ii  libgcc1                               1:4.2.4-1ubuntu3                      GCC support library
ii  libgcrypt11                           1.2.4-2ubuntu7                        LGPL Crypto library - runtime library
ii  libgdbm3                              1.8.3-3                               GNU dbm database routines (runtime version)
ii  libglib2.0-0                          2.16.6-0ubuntu1                       The GLib library of C routines
ii  libgnutls13                           2.0.4-1ubuntu2.3                      the GNU TLS library - runtime library
ii  libgpg-error0                         1.4-2ubuntu7                          library for common error values and messages
ii  libgpmg1                              1.19.6-25ubuntu1                      General Purpose Mouse - shared library
ii  libhtml-parser-perl                   3.56-1                                A collection of modules that parse HTML text
ii  libhtml-tagset-perl                   3.10-2                                Data tables pertaining to HTML
ii  libhtml-tree-perl                     3.23-1                                represent and create HTML syntax trees
ii  libidn11                              1.1-1                                 GNU libidn library, implementation of IETF I
ii  libio-pty-perl                        1:1.07-1                              Perl module for pseudo tty IO
ii  libisc35                              1:9.4.2.dfsg.P2-2ubuntu0.1            ISC Shared Library used by BIND
ii  libisccc30                            1:9.4.2.dfsg.P2-2ubuntu0.1            Command Channel Library used by BIND
ii  libisccfg30                           1:9.4.2.dfsg.P2-2ubuntu0.1            Config File Handling Library used by BIND
ii  libiw29                               29-1ubuntu2                           Wireless tools - library
ii  libkeyutils1                          1.2-4                                 Linux Key Management Utilities (library)
ii  libklibc                              1.5.7-4ubuntu4                        minimal libc subset for use with initramfs
ii  libkrb53                              1.6.dfsg.3~beta1-2ubuntu1             MIT Kerberos runtime libraries
ii  libldap-2.4-2                         2.4.9-0ubuntu0.8.04.2                 OpenLDAP libraries
ii  liblocale-gettext-perl                1.05-2ubuntu1                         Using libc functions for internationalizatio
ii  liblwres30                            1:9.4.2.dfsg.P2-2ubuntu0.1            Lightweight Resolver Library used by BIND
ii  liblzo2-2                             2.02-3                                data compression library
ii  libmagic1                             4.21-3ubuntu1                         File type determination library using "magic
ii  libmd5-perl                           2.03-1                                backwards-compatible wrapper for Digest::MD5
ii  libncurses5                           5.6+20071124-1ubuntu2                 Shared libraries for terminal handling
ii  libncursesw5                          5.6+20071124-1ubuntu2                 Shared libraries for terminal handling (wide
ii  libnet-ssleay-perl                    1.30-1                                Perl module for Secure Sockets Layer (SSL)
ii  libnewt0.52                           0.52.2-11.2ubuntu1                    Not Erik's Windowing Toolkit - text mode win
ii  libntfs-3g23                          1:1.2216-1ubuntu3                     ntfs-3g filesystem in userspace (FUSE) libra
ii  libopencdk10                          0.6.6-1ubuntu1                        Open Crypto Development Kit (OpenCDK) (runti
ii  libpam-modules                        0.99.7.1-5ubuntu6.1                   Pluggable Authentication Modules for PAM
ii  libpam-runtime                        0.99.7.1-5ubuntu6.1                   Runtime support for the PAM library
ii  libpam0g                              0.99.7.1-5ubuntu6.1                   Pluggable Authentication Modules library
ii  libparted1.7-1                        1.7.1-5.1ubuntu9.1                    The GNU Parted disk partitioning shared libr
ii  libpcap0.8                            0.9.8-2                               System interface for user-level packet captu
ii  libpcre3                              7.4-1ubuntu2.1                        Perl 5 Compatible Regular Expression Library
ii  libpopt0                              1.10-3build1                          lib for parsing cmdline parameters
ii  libreadline5                          5.2-3build1                           GNU readline and history libraries, run-time
ii  librpc-xml-perl                       0.59-2                                Perl module implementation of XML-RPC
ii  libsasl2-2                            2.1.22.dfsg1-18ubuntu2                Cyrus SASL - authentication abstraction libr
ii  libsasl2-modules                      2.1.22.dfsg1-18ubuntu2                Cyrus SASL - pluggable authentication module
ii  libselinux1                           2.0.55-0ubuntu4                       SELinux policy enforcement, run-time librari
ii  libsepol1                             2.0.20-0ubuntu3                       SELinux binary policy, run-time library
ii  libsigc++-2.0-0c2a                    2.0.17-2ubuntu3                       type-safe Signal Framework for C++ - runtime
ii  libslang2                             2.1.3-2                               The S-Lang programming library - runtime ver
ii  libsqlite3-0                          3.4.2-2                               SQLite 3 shared library
ii  libss2                                1.40.8-2ubuntu2                       command-line interface parsing library
ii  libssl0.9.8                           0.9.8g-4ubuntu3.4                     SSL shared libraries
ii  libstdc++6                            4.2.4-1ubuntu3                        The GNU Standard C++ Library v3
ii  libsysfs2                             2.1.0-4                               interface library to sysfs
ii  libtasn1-3                            1.1-1                                 Manage ASN.1 structures (runtime)
ii  libterm-readkey-perl                  2.30-3ubuntu1                         A perl module for simple terminal control
ii  libtext-charwidth-perl                0.04-4build1                          get display widths of characters on the term
ii  libtext-iconv-perl                    1.4-3                                 converts between character sets in Perl
ii  libtext-wrapi18n-perl                 0.06-5                                internationalized substitute of Text::Wrap
ii  liburi-perl                           1.35.dfsg.1-1                         Manipulates and accesses URI strings
ii  libusb-0.1-4                          2:0.1.12-8                            userspace USB programming library
ii  libuuid1                              1.40.8-2ubuntu2                       universally unique id library
ii  libvolume-id0                         117-8                                 volume identification library
ii  libwrap0                              7.6.dbs-14                            Wietse Venema's TCP wrappers library
ii  libwww-perl                           5.808-1                               WWW client/server library for Perl (aka LWP)
ii  libxml-parser-perl                    2.34-4.3                              Perl module for parsing XML files
ii  linux-image-2.6.24-23-server          2.6.24-23.46                          Linux kernel image for version 2.6.24 on x86
ii  linux-image-server                    2.6.24.23.25                          Linux kernel image on Server Equipment.
ii  linux-server                          2.6.24.23.25                          Complete Linux kernel on Server Equipment.
ii  linux-ubuntu-modules-2.6.24-23-server 2.6.24-23.36                          Ubuntu supplied Linux modules for version 2.
ii  locales                               2.7.9-4                               common files for locale support
ii  login                                 1:4.0.18.2-1ubuntu2.2                 system login tools
ii  logrotate                             3.7.1-3ubuntu0.8.04                   Log rotation utility
ii  lsb-base                              3.2-4ubuntu1                          Linux Standard Base 3.2 init script function
ii  lsb-release                           3.2-4ubuntu1                          Linux Standard Base version reporting utilit
ii  lshw                                  02.12.01-2ubuntu1.1                   information about hardware configuration
ii  lsof                                  4.78.dfsg.1-3                         List open files
ii  ltrace                                0.5-3ubuntu1                          Tracks runtime library calls in dynamically 
ii  lzma                                  4.43-12ubuntu1                        Compression method of 7z format in 7-Zip pro
ii  makedev                               2.3.1-84ubuntu1                       creates device files in /dev
ii  man-db                                2.5.1-3                               on-line manual pager
ii  manpages                              2.77-1                                Manual pages about using a GNU/Linux system
ii  mawk                                  1.3.3-11ubuntu2                       a pattern scanning and text processing langu
ii  mc                                    1:4.6.1-8ubuntu1                      midnight commander - a powerful file manager
ii  mdadm                                 2.6.3+200709292116+4450e59-3ubuntu3.1 tool to administer Linux MD arrays (software
ii  memtest86+                            1.70-3ubuntu1                         thorough real-mode memory tester
ii  mii-diag                              2.11-2                                A little tool to manipulate network cards
ii  mime-support                          3.39-1ubuntu1                         MIME files 'mime.types' & 'mailcap', and sup
ii  mktemp                                1.5-5ubuntu2                          Makes unique filenames for temporary files
ii  mlocate                               0.18-2ubuntu1                         quickly find files on the filesystem based o
ii  module-init-tools                     3.3-pre11-4ubuntu5.8.04.1             tools for managing Linux kernel modules
ii  mount                                 2.13.1-5ubuntu3                       Tools for mounting and manipulating filesyst
ii  mtr-tiny                              0.72-2ubuntu1                         Full screen ncurses traceroute tool
ii  nano                                  2.0.7-1ubuntu1                        free Pico clone with some new features
ii  ncurses-base                          5.6+20071124-1ubuntu2                 Descriptions of common terminal types
ii  ncurses-bin                           5.6+20071124-1ubuntu2                 Terminal-related programs and man pages
ii  net-tools                             1.60-19ubuntu1                        The NET-3 networking toolkit
ii  netbase                               4.30ubuntu1                           Basic TCP/IP networking system
ii  netcat                                1.10-36                               TCP/IP swiss army knife -- transitional pack
ii  netcat-traditional                    1.10-36                               TCP/IP swiss army knife
ii  ntfs-3g                               1:1.2216-1ubuntu3                     read-write NTFS driver for FUSE
ii  ntpdate                               1:4.2.4p4+dfsg-3ubuntu2.1             client for setting system time from NTP serv
ii  openssh-blacklist                     0.1-1ubuntu0.8.04.1                   list of blacklisted OpenSSH RSA and DSA keys
ii  openssh-client                        1:4.7p1-8ubuntu1.2                    secure shell client, an rlogin/rsh/rcp repla
ii  openssh-server                        1:4.7p1-8ubuntu1.2                    secure shell server, an rshd replacement
ii  openssl                               0.9.8g-4ubuntu3.4                     Secure Socket Layer (SSL) binary and related
ii  parted                                1.7.1-5.1ubuntu9.1                    The GNU Parted disk partition resizing progr
ii  passwd                                1:4.0.18.2-1ubuntu2.2                 change and administer password and group dat
ii  pciutils                              1:2.2.4-1.1ubuntu6                    Linux PCI Utilities
ii  pcmciautils                           014-4ubuntu1                          PCMCIA utilities for Linux 2.6
ii  perl                                  5.8.8-12ubuntu0.4                     Larry Wall's Practical Extraction and Report
ii  perl-base                             5.8.8-12ubuntu0.4                     The Pathologically Eclectic Rubbish Lister
ii  perl-modules                          5.8.8-12ubuntu0.4                     Core Perl modules
ii  popularity-contest                    1.43ubuntu1                           Vote for your favourite packages automatical
ii  ppp                                   2.4.4rel-9ubuntu2                     Point-to-Point Protocol (PPP) daemon
ii  pppconfig                             2.3.17ubuntu1                         A text menu based utility for configuring pp
ii  pppoeconf                             1.17ubuntu1                           configures PPPoE/ADSL connections
ii  procps                                1:3.2.7-5ubuntu3                      /proc file system utilities
ii  psmisc                                22.6-1                                Utilities that use the proc filesystem
ii  python                                2.5.2-0ubuntu1                        An interactive high-level object-oriented la
ii  python-apt                            0.7.4ubuntu7.4                        Python interface to libapt-pkg
ii  python-central                        0.6.7ubuntu0.1                        register and build utility for Python packag
ii  python-gdbm                           2.5.2-0ubuntu2                        GNU dbm database support for Python
ii  python-gnupginterface                 0.3.2-9ubuntu1                        Python interface to GnuPG (GPG)
ii  python-minimal                        2.5.2-0ubuntu1                        A minimal subset of the Python language (def
ii  python-support                        0.7.5ubuntu1                          automated rebuilding support for python modu
ii  python2.5                             2.5.2-2ubuntu4.1                      An interactive high-level object-oriented la
ii  python2.5-minimal                     2.5.2-2ubuntu4.1                      A minimal subset of the Python language (ver
ii  readline-common                       5.2-3build1                           GNU readline and history libraries, common f
ii  reiserfsprogs                         1:3.6.19-6                            User-level tools for ReiserFS filesystems
ii  rsync                                 2.6.9-6ubuntu2                        fast remote file copy program (like rcp)
ii  sed                                   4.1.5-5                               The GNU sed stream editor
ii  startup-tasks                         0.3.9-2                               definitions of essential tasks to run on sta
ii  strace                                4.5.15-1.1ubuntu1                     A system call tracer
ii  sudo                                  1.6.9p10-1ubuntu3.3                   Provide limited super user privileges to spe
ii  sysklogd                              1.5-1ubuntu1                          System Logging Daemon
ii  system-services                       0.3.9-2                               definitions of essential system services
ii  sysv-rc                               2.86.ds1-14.1ubuntu45                 System-V-like runlevel change mechanism
ii  sysvutils                             2.86.ds1-14.1ubuntu45                 System-V-like utilities
ii  tar                                   1.19-3                                GNU version of the tar archiving utility
ii  tasksel                               2.70ubuntu5                           Tool for selecting tasks for installation on
ii  tasksel-data                          2.70ubuntu5                           Official tasks used for installation of Debi
ii  tcpd                                  7.6.dbs-14                            Wietse Venema's TCP wrapper utilities
ii  tcpdump                               3.9.8-2                               A powerful tool for network monitoring and d
ii  telnet                                0.17-35ubuntu1                        The telnet client
ii  time                                  1.7-21build1                          The GNU time program for measuring cpu resou
ii  tzdata                                2008h-0ubuntu0.8.04.1                 time zone and daylight-saving time data
ii  ubuntu-keyring                        2008.03.04                            GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                        1.102                                 Minimal core of Ubuntu
ii  ubuntu-standard                       1.102                                 The Ubuntu standard system
ii  ucf                                   3.005                                 Update Configuration File: preserve user cha
ii  udev                                  117-8                                 rule-based device node and kernel event mana
ii  ufw                                   0.16.2.4                              program for managing a netfilter firewall
ii  update-inetd                          4.27-0.6                              inetd.conf updater
ii  update-manager-core                   1:0.87.30                             manage release upgrades
ii  upstart                               0.3.9-2                               event-based init daemon
ii  upstart-compat-sysv                   0.3.9-2                               compatibility for System-V-like init
ii  upstart-logd                          0.3.9-2                               boot logging daemon
ii  usbutils                              0.73-5ubuntu2                         Linux USB utilities
ii  util-linux                            2.13.1-5ubuntu3                       Miscellaneous system utilities
ii  util-linux-locales                    2.13.1-5ubuntu3                       Locales files for util-linux
ii  uuid-runtime                          1.40.8-2ubuntu2                       universally unique id library
ii  vim-common                            1:7.1-138+1ubuntu3.1                  Vi IMproved - Common files
ii  vim-tiny                              1:7.1-138+1ubuntu3.1                  Vi IMproved - enhanced vi editor - compact v
ii  w3m                                   0.5.1-5.1ubuntu1                      WWW browsable pager with excellent tables/fr
ii  webmin                                1.450                                 A web-based administration interface for Uni
ii  wget                                  1.10.2-3ubuntu1                       retrieves files from the web
ii  whiptail                              0.52.2-11.2ubuntu1                    Displays user-friendly dialog boxes from she
ii  wireless-tools                        29-1ubuntu2                           Tools for manipulating Linux Wireless Extens
ii  wpasupplicant                         0.6.0+0.5.8-0ubuntu2                  Client support for WPA and WPA2 (IEEE 802.11
ii  xkb-data                              1.1~cvs.20080104.1-1ubuntu8           X Keyboard Extension (XKB) configuration dat
ii  zlib1g                                1:1.2.3.3.dfsg-7ubuntu1               compression library - runtime
```

---

### Post by netztier on 2009-03-11
> **Keymaster said:**
> 
```

ii  dhcp3-client                          3.0.6.dfsg 1ubuntu9                   DHCP client


My server also has dhcp3-client installed, but it's not active.

Is it running on your machine?

[CODE]user@server~$: **ps -eaf | grep dhcp**
```

As a next step, we should then investigate *why* it's running, but let's leave that for later.

regards

Marc

---

### Post by khelben1979 on 2009-03-11
Take a look at what services you have running in your startup script directory:

```
cd /etc/init.d/
```

Then if you see something which shouldn't be there you can always uninstall this from the system.

```
man [name of the program]
```
to read about what the scripts does.

---

### Post by Keymaster on 2009-03-11
ps aux | grep "dhcp" yields the following results:

```
ahrem@iscsi1:~$ ps aux | grep "dhcp"
dhcp      4151  0.0  0.0   2436   832 ?        S<s  Mar09   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
ahrem    23407  0.0  0.0   3008   776 pts/2    S+   11:45   0:00 grep dhcp
ahrem@iscsi1:~$ 


```

Could this be the issue?  These particular IBM servers are quite glitchy with every OS I've tried on them.

---

### Post by puppywhacker on 2009-03-11
the dhcpclient shouldn't be running if you only want static addresses. you can kill it with
```
kill 4151
```


to reset / reconfigure the network interface you can than restart the network
**DONT DO THIS IF YOU ARE CONNECTED OVER THE NETWORK**
```
/etc/init.d/networking restart
```

The dhclient is started during startup at the INIT. you can find the script here
```
grep dhclient /etc/init.d/*
```

---

### Post by Keymaster on 2009-03-11
I killed the dhcp process and set the bootup to no longer start dhcdbd.  Is this all I had to do?  The static IPs are assigned, but the problem was that they reset to dhcp around 7pm for no reason.

The description to dhcdbd was :
"dhcdbd provides a D-DBus interface to dhclient,"

Is that the correct process to stop from starting?

---

### Post by netztier on 2009-03-11
> **Keymaster said:**
> 
The description to dhcdbd was :
"dhcdbd provides a D-DBus interface to dhclient,"


Hmm. From the extended description:

```
Description: D-Bus interface to the ISC DHCP client
 dhcdbd provides a D-Bus interface to dhclient, the DHCP client from ISC,
 so applications such as NetworkManager can query and control dhclient.
 This allows an application-neutral interface for such operations

```

D-Bus? NetworkManager?

Er... You wouldn't happen to have a GUI installed on that server at some point of time (you know, "sudo aptitude install ubuntu-desktop" and the likes),  so that NetworkManager got installed as well?

regards

Marc

---

### Post by Keymaster on 2009-03-11
No I don't have a GUI on it.

---

### Post by netztier on 2009-03-11
> **Keymaster said:**
> No I don't have a GUI on it.

okay. Is there any other tool you might've installed that promised to make network configuration easier by some scripting magic? 

If you reboot now, is dhclient3 still running? 

The fact that it resets at some seemling random point in time has to do with lease duration: After half of the lease time is expired, the dhcp client will try to renew it's IP address - and if it gets one, your interface will be reconfigured. The fact that you manually configure it for static adressing will not necessarily stop the dhcp client from trying to renew the lease a few hours later. Stopping/deactivating the dhcp client certainly will.

regards

Marc

---

### Post by Keymaster on 2009-03-11
well I killed the client and set it so that dhcdbd won't start up automatically with reboot.

---

