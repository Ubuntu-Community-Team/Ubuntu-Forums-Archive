---
title: "Banshee alarm clock - Mono not found"
date: 2008-11-09
forum: Multimedia Software
---

### Post by emf on 2008-11-09
I recently installed Banshee 1.2.1 and would like to use the alarm clock extension found on the [[COLOR="Blue"]banshee extensions page[/COLOR]]("http://banshee-project.org/download/extensions/").

When I attempt ./configure I receive the output:

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking dependency style of gcc... none
checking for intltool >= 0.35.0... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO_MODULE... configure: error: Package requirements (mono >= 1.2.2) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_MODULE_CFLAGS
and MONO_MODULE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I have installed the following mono packages with synaptic: mono-common, mono-gac, mono-gmcs, mono-jit, mono-mcs, mono-runtime, mono-utils.

1. Is there a mono package I am missing?
2. If I have all necessary files, could someone help me with setting the environmental variables to make ./configure work?

Thank you.

---

### Post by directhex on 2008-11-09
libmono-dev

But I can't for the life of me imagine why your app has that in its config script

---

### Post by emf on 2008-11-09
Thank you.  libmono-dev allowed me to run configure without a hitch:

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking dependency style of gcc... none
checking for intltool >= 0.35.0... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO_MODULE... yes
checking for gmcs... /usr/bin/gmcs
checking for mono... /usr/bin/mono
checking for BANSHEE... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
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
checking for msgfmt... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: creating build/Makefile
config.status: creating src/Makefile
config.status: creating src/AssemblyInfo.cs
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

Extension will be installed in /usr/local/lib/banshee-1/Extensions
```

However, now I've received the following error when running make:

```
Making all in build
make[1]: Entering directory `/home/name/Desktop/banshee-alarm-extension-0.4.1/build'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/name/Desktop/banshee-alarm-extension-0.4.1/build'
Making all in po
make[1]: Entering directory `/home/name/Desktop/banshee-alarm-extension-0.4.1/po'
file=`echo fr | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file fr.po
/bin/sh: -o: not found
make[1]: *** [fr.gmo] Error 127
make[1]: Leaving directory `/home/name/Desktop/banshee-alarm-extension-0.4.1/po'
make: *** [all-recursive] Error 1
```

Any suggestions?

---

### Post by directhex on 2008-11-09
A copy of po/Makefile would be helpful

---

### Post by emf on 2008-11-09
I've attached the Makefile as a text file.  Thank you for continuing to help with this.

---

### Post by directhex on 2008-11-10
Try installing gettext, and re-running configure

Unable to reproduce problems here, builds fine - but I'm on a rather different system to you

---

### Post by emf on 2008-11-12
I installed gettext and re-ran configure with no luck.

I've given up on banshee and I've decided to use jajuk instead.

---

### Post by nkobel003 on 2009-01-07
I'm having the same problem with both 8.04 and 8.10, as well as alarm clock versions .4.1 and .4.2. I don't see anything obviously wrong. Any suggestions?

---

### Post by directhex on 2009-01-07
> **nkobel003 said:**
> I'm having the same problem with both 8.04 and 8.10, as well as alarm clock versions .4.1 and .4.2. I don't see anything obviously wrong. Any suggestions?

The problem is here in the makefile:
```
	file=`echo $* | sed 's,.*/,,'`.gmo \
	  && rm -f $$file && $(GMSGFMT) -o $$file $<
```

See the "$(GMSGFMT)"? It's undefined:
```
GMSGFMT = 
```

Hence empty string, hence blank, hence it just tries to call "-o"

The "msgfmt" command is in the gettext package - re-running configure after installing it is vital.

---

### Post by sojusnik on 2009-03-01
Hi,

I'm stuck in the same place installing the alarm clock 0.4.2 extension on Ubuntu 8.10 64-bit for Banshee 1.4.2.

When typing make, the following comes:
> sojusnik@cassiopeia:~/.config/banshee-1/addin-db-001/banshee-alarm-extension-0.4.2$ make
Making all in build
make[1]: Betrete Verzeichnis '/home/sojusnik/.config/banshee-1/addin-db-001/banshee-alarm-extension-0.4.2/build'
make[1]: Für das Ziel »all« ist nichts zu tun.
make[1]: Verlasse Verzeichnis '/home/sojusnik/.config/banshee-1/addin-db-001/banshee-alarm-extension-0.4.2/build'
Making all in po
make[1]: Betrete Verzeichnis '/home/sojusnik/.config/banshee-1/addin-db-001/banshee-alarm-extension-0.4.2/po'
file=`echo fr | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file fr.po
make[1]: Verlasse Verzeichnis '/home/sojusnik/.config/banshee-1/addin-db-001/banshee-alarm-extension-0.4.2/po'
Making all in src
make[1]: Betrete Verzeichnis '/home/sojusnik/.config/banshee-1/addin-db-001/banshee-alarm-extension-0.4.2/src'
no -debug -out:Banshee.AlarmClock.dll -target:library -r:/usr/lib/banshee-1/Banshee.Widgets.dll -r:/usr/lib/banshee-1/Banshee.ThickClient.dll -r:/usr/lib/banshee-1/Banshee.Services.dll -r:Mono.Cairo -r:/usr/lib/banshee-1/Hyena.Gui.dll -r:/usr/lib/banshee-1/Banshee.Core.dll -r:System -r:/usr/lib/banshee-1/Mono.Media.dll -r:/usr/lib/cli/taglib-sharp-2.0/taglib-sharp.dll -r:/usr/lib/cli/ndesk-dbus-1.0/NDesk.DBus.dll -r:/usr/lib/cli/ndesk-dbus-glib-1.0/NDesk.DBus.GLib.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll -r:/usr/lib/cli/mono-addins-0.2/Mono.Addins.dll -r:System.Data -r:Mono.Data.SqliteClient -r:Mono.Posix -r:/usr/lib/banshee-1/Hyena.dll -r:/usr/lib/banshee-1/MusicBrainz.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll    -resource:./Banshee.AlarmClock.addin.xml,Banshee.AlarmClock.addin.xml  -resource:./AlarmMenu.xml,AlarmMenu.xml ./Alarm.cs ./AlarmClockService.cs ./AlarmConfigDialog.cs ./ConfigurationDialog.cs ./ConfigurationSchema.cs ./SleepTimerConfigDialog.cs ./VolumeFade.cs ./AssemblyInfo.cs
/bin/bash: no: command not found
make[1]: *** [Banshee.AlarmClock.dll] Fehler 127
make[1]: Verlasse Verzeichnis '/home/sojusnik/.config/banshee-1/addin-db-001/banshee-alarm-extension-0.4.2/src'
make: *** [all-recursive] Fehler 1

> **directhex said:**
> The problem is here in the makefile:
```
	file=`echo $* | sed 's,.*/,,'`.gmo \
	  && rm -f $$file && $(GMSGFMT) -o $$file $<
```

See the "$(GMSGFMT)"? It's undefined:
```
GMSGFMT = 
```

Hence empty string, hence blank, hence it just tries to call "-o"

The "msgfmt" command is in the gettext package - re-running configure after installing it is vital.
I can't really understand how to solve this due to the above mentioned words.
Is there a newbie friendly solution to this?

---

### Post by directhex on 2009-03-01
> **sojusnik said:**
> Hi,

I'm stuck in the same place installing the alarm clock 0.4.2 extension on Ubuntu 8.10 64-bit for Banshee 1.4.2.

When typing make, the following comes:



I can't really understand how to solve this due to the above mentioned words.
Is there a newbie friendly solution to this?

mono-devel package.

---

