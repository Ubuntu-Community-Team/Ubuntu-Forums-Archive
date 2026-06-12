---
title: "Installing Totem"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by tufcamman on 2008-02-07
Hi, I am still fairly new at linux.  I am trying to install the latest version of totem.  I downloaded and extracted the file and in the terminal when I try to install it this comes up.

ben@mobile:~/Desktop/totem-2.21.92$ sudo ./configure; make; makeinstall
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
bash: make: command not found
bash: makeinstall: command not found
ben@mobile:~/Desktop/totem-2.21.92$

I have tried to find and install a valid C compiler but I'm afraid I'm just not experienced enough to know what to do.  If someone could help point me in the right direction that would be great.  Thanks!

---

### Post by gandaran on 2008-02-07
install the build-essential package, look it up on synaptic and apply for install

---

### Post by tufcamman on 2008-02-07
Thanks, this helps.  I was able to install those packages and it got further this time.  Now it replies with

ben@mobile:~/Desktop/totem-2.21.92$ ./configure; make; makeinstall
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
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for intltool >= 0.35.0... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
make: *** No targets specified and no makefile found.  Stop.
bash: makeinstall: command not found

Here is the contents of the folder I am installing from

ben@mobile:~/Desktop/totem-2.21.92$ ls
aclocal.m4      configure             intltool-merge.in   po
AUTHORS         configure.in          intltool-update.in  py-compile
autogen.sh      COPYING               lib                 README
bindings        COPYING.LIB           license_change      src
browser-plugin  data                  ltmain.sh           TODO
ChangeLog       depcomp               Makefile.am         totem.spec
compile         gnome-doc-utils.make  Makefile.in         totem.spec.in
config.guess    help                  missing             xmldocs.make
config.h.in     INSTALL               mkinstalldirs
config.log      install-sh            NEWS
config.sub      intltool-extract.in   omf.make

Thanks again for your help.  What do you think I should try next?

---

### Post by danillo on 2008-02-07
Some missing package, perhaps libxml-parser-perl. And try putting a space between "make" and "install".

---

