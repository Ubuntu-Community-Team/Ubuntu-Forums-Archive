---
title: "strange error when rebuilding"
date: 2010-08-11
forum: Mythbuntu
---

### Post by managementboy on 2010-08-11
my build stops with this error:
```
cd i18n/ && make check
make[2]: Entering directory `/home/elkin/src/mythtv/mythtv-0.24.0~trunk25612/i18n'
make[2]: Nothing to be done for `check'.
make[2]: Leaving directory `/home/elkin/src/mythtv/mythtv-0.24.0~trunk25612/i18n'
cd locales/ && make check
make[2]: Entering directory `/home/elkin/src/mythtv/mythtv-0.24.0~trunk25612/locales'
make[2]: Nothing to be done for `check'.
make[2]: Leaving directory `/home/elkin/src/mythtv/mythtv-0.24.0~trunk25612/locales'
cd config/ && make check
make[2]: Entering directory `/home/elkin/src/mythtv/mythtv-0.24.0~trunk25612/config'
make[2]: *** No rule to make target `check'.  Stop.
make[2]: Leaving directory `/home/elkin/src/mythtv/mythtv-0.24.0~trunk25612/config'
make[1]: *** [sub-config-check_ordered] Error 2
make[1]: Leaving directory `/home/elkin/src/mythtv/mythtv-0.24.0~trunk25612'
dh_auto_test: make -j1 check returned exit code 2
make: *** [build] Error 29
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```
when rebuilding the latest trunk 0.24 packages to add qt4.7 to it (part of kubuntu kde 4.5 packages). What could I be doing wrong?

---

