---
title: "buiding mythbuntu package with ng patches"
date: 2008-04-27
forum: Mythbuntu
---

### Post by valois22 on 2008-04-27
hello everybody. I'am using mythbuntu 7.10 . I'm trying to recompile mythbuntu with NA dvb patches. someone in other forum sugested that in /usr/scr/  download the mythtv source code using   apt-get source mythtv      and in the mythtv directory patch the source and then do  dpkg-buildpackage -rfakeroot -b -d  . but after doing so it giveme the following error:

```
dh_installdocs -pmythtv-doc docs/mythtv-HOWTO*
dh_installexamples -pmythtv-doc configfiles/*
dh_installcron -i
dh_installchangelogs  -i
dh_link -i
dh_perl -i
dh_compress -i
dh_fixperms -i
dh_installdeb -i
dh_gencontrol -i
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dpkg-gencontrol: warning: unknown substitution variable ${perl:Depends}
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dh_md5sums -i
dh_builddeb -i
warning, `debian/mythtv/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `mythtv' in `../mythtv_0.20.2-0ubuntu10_all.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
warning, `debian/mythtv-common/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `mythtv-common' in `../mythtv-common_0.20.2-0ubuntu10_all.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
warning, `debian/mythtv-doc/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `mythtv-doc' in `../mythtv-doc_0.20.2-0ubuntu10_all.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
warning, `debian/mythtv-database/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `mythtv-database' in `../mythtv-database_0.20.2-0ubuntu10_all.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
warning, `debian/mythtv-backend-master/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `mythtv-backend-master' in `../mythtv-backend-master_0.20.2-0ubuntu10_all.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
warning, `debian/ubuntu-mythtv-frontend/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `ubuntu-mythtv-frontend' in `../ubuntu-mythtv-frontend_0.20.2-0ubuntu10_all.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
dh_testdir -a
dh_testroot -a
dh_installdocs -a -A README debian/README.Debian AUTHORS keys.txt FAQ UPGRADING
dh_installdebconf -a
dh_installexamples -a
dh_installmenu -a
dh_installlogrotate -a
dh_installinit -a -u'defaults 24 16'
dh_installcron -a
dh_installinfo -a
dh_installchangelogs  -a
dh_strip -a
dh_link -a
dh_compress -a
dh_fixperms -a
dh_makeshlibs -a -V -Xusr/lib/mythtv/filters
dh_installdeb -a
dh_shlibdeps -a
dh_gencontrol -a
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
dh_md5sums -a
dh_builddeb -a
warning, `debian/mythtv-backend/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `mythtv-backend' in `../mythtv-backend_0.20.2-0ubuntu10_i386.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
warning, `debian/mythtv-transcode-utils/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `mythtv-transcode-utils' in `../mythtv-transcode-utils_0.20.2-0ubuntu10_i386.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
warning, `debian/mythtv-frontend/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `mythtv-frontend' in `../mythtv-frontend_0.20.2-0ubuntu10_i386.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
warning, `debian/libmyth-0.20/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `libmyth-0.20' in `../libmyth-0.20_0.20.2-0ubuntu10_i386.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
warning, `debian/libmyth-dev/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `libmyth-dev' in `../libmyth-dev_0.20.2-0ubuntu10_i386.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
 signfile mythtv_0.20.2-0ubuntu10_i386.changes
gpg: skipped "Mario Limonciello <superm1@ubuntu.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

dpkg-buildpackage: binary only upload (no source included)
(WARNING: Failed to sign .changes file)
```

any idea how fo fix this?. Thank you in advance

---

### Post by superm1 on 2008-04-27
You are welcome to do whatever you want with patches and recompiling, but no discussions of sasc-ng in this forum.  Keep it elsewhere..

---

