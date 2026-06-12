---
title: "libasound headers version &gt;= 1.0.16... not present."
date: 2009-07-18
forum: Multimedia Software
---

### Post by wetinwales on 2009-07-18
Hi All
Following essay on installing drivers for emu1212 sound card as per
[http://ubuntuforums.org/showthread.php?t=715755](http://ubuntuforums.org/showthread.php?t=715755)
Solved all problems so far.
Getting on with config make make install for packages. Learning lots!

Got to ./configure --w... alsa-utils-1.0.20 and I get:-
...etc
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.:(

According to Synaptic, libasound2-1.0.18-1ubuntu9 is installed
tried installing both the [https://launchpad.net/~voria/+archive/ppa/+files/lib64asound2_1.0.20-1ubuntu2~ppa1~nc10~jaunty_i386.deb](https://launchpad.net/~voria/+archive/ppa/+files/lib64asound2_1.0.20-1ubuntu2~ppa1~nc10~jaunty_i386.deb)
and the 
libasound2_1.0.18-1ubuntu9_amd64.deb  I am an amd64bit processor.

So stuck for clues. alsa-utils-1.0.20 won't play without libasound 'something'

Anyone have any ideas?

Thanks
Daf:confused:

---

### Post by mc4man on 2009-07-18
is libasound2-dev installed?

---

### Post by wetinwales on 2009-07-19
Hi
No, libasound2-dev was not installed.
Installed it from Synaptic ( 1.0.18-1ubuntu9 )
Couldn't spot error messages in ./configure
make wasn't happy:-

user@puter:/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: Entering directory `/alsa-utils-1.0.20/include'
make  all-am
make[2]: Entering directory `/alsa-utils-1.0.20/include'
make[2]: Leaving directory `/alsa-utils-1.0.20/include'
make[1]: Leaving directory `/alsa-utils-1.0.20/include'
Making all in alsactl
make[1]: Entering directory `/alsa-utils-1.0.20/alsactl'
Making all in init
make[2]: Entering directory `/alsa-utils-1.0.20/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/alsa-utils-1.0.20/alsactl/init'
make[2]: Entering directory `/alsa-utils-1.0.20/alsactl'
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/alsa-utils-1.0.20/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/alsa-utils-1.0.20/alsactl'
make: *** [all-recursive] Error 1
user@puter:/alsa-utils-1.0.20$

make install didn't work either:-

daf@daftop:/alsa-utils-1.0.20$ sudo make install
[sudo] password for daf: 
Making install in include
make[1]: Entering directory `/alsa-utils-1.0.20/include'
make[2]: Entering directory `/alsa-utils-1.0.20/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/alsa-utils-1.0.20/include'
make[1]: Leaving directory `/alsa-utils-1.0.20/include'
Making install in alsactl
make[1]: Entering directory `/alsa-utils-1.0.20/alsactl'
Making install in init
make[2]: Entering directory `/alsa-utils-1.0.20/alsactl/init'
make[3]: Entering directory `/alsa-utils-1.0.20/alsactl/init'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: Leaving directory `/alsa-utils-1.0.20/alsactl/init'
make[2]: Leaving directory `/alsa-utils-1.0.20/alsactl/init'
make[2]: Entering directory `/alsa-utils-1.0.20/alsactl'
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/alsa-utils-1.0.20/alsactl'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/alsa-utils-1.0.20/alsactl'
make: *** [install-recursive] Error 1


I think I am stuck...! 
any ideas?

---

### Post by wetinwales on 2009-07-19
Ah..wait.. found a glich in ./configure:-

configure: creating ./config.status
config.status: creating Makefile
config.status: creating alsactl/Makefile
config.status: creating alsactl/init/Makefile
config.status: creating alsamixer/Makefile
config.status: creating amidi/Makefile
config.status: creating amixer/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating alsaconf/alsaconf
config.status: creating alsaconf/Makefile
config.status: creating alsaconf/po/Makefile
**config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting**
config.status: creating aplay/Makefile
config.status: creating include/Makefile
config.status: creating iecset/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-utils.spec
config.status: creating seq/Makefile
config.status: creating seq/aconnect/Makefile
config.status: creating seq/aplaymidi/Makefile
config.status: creating seq/aseqdump/Makefile
config.status: creating seq/aseqnet/Makefile
config.status: creating speaker-test/Makefile
config.status: creating speaker-test/samples/Makefile
config.status: creating include/aconfig.h
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands

how can I fix it?
Daf

---

### Post by mc4man on 2009-07-19
> bin/bash: xmlto: command not found

Either install xmlto or configure it out

suggest installing it, then run a ```
make distclean
``` on source, then configure as you were doing and make.

You may wish to install checkinstall also, then after the make succeeds use this to install
```
sudo checkinstall --fstrans=no
```

---

### Post by wetinwales on 2009-07-19
Problem solved.

The block in alsa-utils-1.0.20 cleared with installing 'xmlto' and re configure make make install.
One remaining error message was in place on make and make install but nevertheless emu is now working fine

Look at the caveat in this forum which warns against the emu cards not being well served with drivers for linux.
I wanted the full 192KHz but can not have it. Only 48000 sample rate available

---

