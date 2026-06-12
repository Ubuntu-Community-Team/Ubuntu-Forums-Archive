---
title: "makemkv: a concern?"
date: 2013-02-03
forum: Multimedia Software
---

### Post by Euler2 on 2013-02-03
Storing the datestamp somewhere and not removing it with an uninstall is a bad sign indeed.

Sometime ago I made a backup with rsync before and after installing makemkv, and this is a list of files which were changed during those few minutes:

building file list
.d..t...... etc/
>f.st...... etc/ld.so.cache
.d..t...... root/
>f+++++++++ root/.xauthtbRS8d
.d..t...... run/systemd/sessions/
>f+++++++++ run/systemd/sessions/c20
cS+++++++++ run/systemd/sessions/c20.ref
.d..t...... run/systemd/users/
>f..t...... run/systemd/users/0
.d..t...... tmp/ksocket-user/
.d..t...... usr/bin/
>f+++++++++ usr/bin/makemkv
.d..t...... usr/lib/
>f+++++++++ usr/lib/libdriveio.so.0
>f+++++++++ usr/lib/libmakemkv.so.1
.d..t...... usr/share/applications/
>f+++++++++ usr/share/applications/makemkv.desktop
.d..t...... usr/share/icons/hicolor/128x128/apps/
>f+++++++++ usr/share/icons/hicolor/128x128/apps/makemkv.png
.d..t...... usr/share/icons/hicolor/16x16/apps/
>f+++++++++ usr/share/icons/hicolor/16x16/apps/makemkv.png
.d..t...... usr/share/icons/hicolor/22x22/apps/
>f+++++++++ usr/share/icons/hicolor/22x22/apps/makemkv.png
.d..t...... usr/share/icons/hicolor/32x32/apps/
>f+++++++++ usr/share/icons/hicolor/32x32/apps/makemkv.png
.d..t...... usr/share/icons/hicolor/64x64/apps/
>f+++++++++ usr/share/icons/hicolor/64x64/apps/makemkv.png
.d..t...... var/cache/ldconfig/
>f.st...... var/cache/ldconfig/aux-cache
>f.st...... var/log/messages
.d..t...... var/run/systemd/sessions/
>f+++++++++ var/run/systemd/sessions/c20
cS+++++++++ var/run/systemd/sessions/c20.ref
.d..t...... var/run/systemd/users/
>f..t...... var/run/systemd/users/0
>f..t...... var/tmp/kdecache-user/icon-cache.kcache
sent 17.28M bytes  received 15.42K bytes  11.53M bytes/sec
total size is 5.03G  speedup is 290.91
building file list
.d..t...... run/udev/
>f..t...... run/udev/queue.bin
.d..t...... usr/bin/
>f+++++++++ usr/bin/makemkvcon
.d..t...... usr/share/
cd+++++++++ usr/share/MakeMKV/
>f+++++++++ usr/share/MakeMKV/default.mmcp.xml
>f+++++++++ usr/share/MakeMKV/makemkv_deu.mo.gz
>f+++++++++ usr/share/MakeMKV/makemkv_dut.mo.gz
>f+++++++++ usr/share/MakeMKV/makemkv_jpn.mo.gz
>f+++++++++ usr/share/MakeMKV/makemkv_ptb.mo.gz
>f+++++++++ usr/share/MakeMKV/makemkv_spa.mo.gz
>f+++++++++ usr/share/MakeMKV/makemkv_swe.mo.gz
.d..t...... var/run/udev/
>f..t...... var/run/udev/queue.bin
.d..t...... var/tmp/kdecache-user/
>f.st...... var/tmp/kdecache-user/ksycoca4
>f..t...... var/tmp/kdecache-user/ksycoca4stamp
sent 10.43M bytes  received 15.26K bytes  6.96M bytes/sec
total size is 5.04G  speedup is 482.19

The datestamp must be hidden in some of those files, unless the installation of makemkv somehow is able to modify the rsync detection mechanism.

Note that the terms you have to agree when installing makemkv contain:

GUINPINSOFT INC DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO WARRANTIES RELATED TO: NON-INFRINGEMENT, **LACK OF VIRUSES**, ACCURACY OR COMPLETENESS OF RESPONSES OR RESULTS, IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE.

---

