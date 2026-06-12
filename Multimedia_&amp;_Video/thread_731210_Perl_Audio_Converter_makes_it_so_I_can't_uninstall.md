---
title: "Perl Audio Converter makes it so I can't uninstall/install"
date: 2008-03-21
forum: Multimedia &amp; Video
---

### Post by pemur1 on 2008-03-21
I tried to install Perl Audio Converter using the Terminal, but something happened (I don't know what) and it didn't install correctly. Now I'm unable to update anything. I can't uninstall Perl Audio Converter and I'm getting very frustrated. Here's what's said when I try to update:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried to run sudo dpkg --configure -a, but nothing happens.

Any help is greatly appreciated.

---

### Post by cozmicharlie on 2008-03-21
Just in time comes the Ubuntu community to the rescue.  Check out my tutorial on PACPL.  If you are still having problems post there and I will help.

[http://ubuntuforums.org/showthread.php?t=712064](http://ubuntuforums.org/showthread.php?t=712064)

Don't give up yet

---

### Post by Lord Illidan on 2008-03-21
Exactly what happens when you enter this command?

```
sudo dpkg --configure -a
```

---

### Post by pemur1 on 2008-03-21
> **Lord Illidan said:**
> Exactly what happens when you enter this command?

```
sudo dpkg --configure -a
```

I haven't forgotten, I'm still waiting for it to complete.

---

### Post by gandaran on 2008-03-21
try this:
sudo dpkg --remove --force-remove-reinstreq 'package'
change 'package' for the file name you wan't to remove

---

### Post by pemur1 on 2008-03-21
> **gandaran said:**
> try this:
sudo dpkg --remove --force-remove-reinstreq 'package'
change 'package' for the file name you wan't to remove

I appreciate that, but I've been running the configuration for about 45 minutes now. I might as well stick it out and see if it'll complete sometime soon.

---

### Post by pemur1 on 2008-03-21
```
Setting up pacpl (4.0.0beta3-1) ...
CPAN: Storable loaded ok
Going to read /root/.cpan/sources/authors/01mailrc.txt.gz
CPAN: Compress::Zlib loaded ok
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/02packages.details.txt.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/02packages.details.txt.gz)
``` The nothing for a long time.

Then: ```
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/02packages.details.txt.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/02packages.details.txt.gz)
```

Then: ```
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/modules/02packages.details.txt.gz](ftp://carroll.cac.psu.edu/pub/CPAN/modules/02packages.details.txt.gz)
Going to read /root/.cpan/sources/modules/02packages.details.txt.gz
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT

  There's a new CPAN.pm version (v1.9205) available!
  [Current version is v1.7602]
  You might want to try
    install Bundle::CPAN
    reload cpan
  without quitting the current session. It should be a seamless upgrade
  while we are running...

Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/03modlist.data.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/03modlist.data.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/03modlist.data.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/03modlist.data.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/modules/03modlist.data.gz](ftp://carroll.cac.psu.edu/pub/CPAN/modules/03modlist.data.gz)
Going to read /root/.cpan/sources/modules/03modlist.data.gz
Going to write /root/.cpan/Metadata
Parse::RecDescent is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Inline is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Inline::C is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module Devel::Symdump
Running make for A/AN/ANDK/Devel-Symdump-2.08.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz)
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/A/AN/ANDK/CHECKSUMS](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/A/AN/ANDK/CHECKSUMS)
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz ok
Scanning cache /root/.cpan/build for sizes
Devel-Symdump-2.08/
Devel-Symdump-2.08/t/
Devel-Symdump-2.08/t/recur.t
Devel-Symdump-2.08/t/export.t
Devel-Symdump-2.08/t/tree.t
Devel-Symdump-2.08/t/symdump.t
Devel-Symdump-2.08/t/pod.t
Devel-Symdump-2.08/t/autogen.t
Devel-Symdump-2.08/t/diff.t
Devel-Symdump-2.08/t/podcover.t
Devel-Symdump-2.08/ChangeLog.svn
Devel-Symdump-2.08/MANIFEST
Devel-Symdump-2.08/ChangeLog
Devel-Symdump-2.08/lib/
Devel-Symdump-2.08/lib/Devel/
Devel-Symdump-2.08/lib/Devel/Symdump.pm
Devel-Symdump-2.08/lib/Devel/Symdump/
Devel-Symdump-2.08/lib/Devel/Symdump/Export.pm
Devel-Symdump-2.08/Makefile.PL
Devel-Symdump-2.08/README
Devel-Symdump-2.08/META.yml
Devel-Symdump-2.08/SIGNATURE

  CPAN.pm: Going to build A/AN/ANDK/Devel-Symdump-2.08.tar.gz

WARNING: LICENSE is not a known parameter.
Checking if your kit is complete...
Looks good
'LICENSE' is not a known MakeMaker parameter name.
Writing Makefile for Devel::Symdump
cp lib/Devel/Symdump.pm blib/lib/Devel/Symdump.pm
cp lib/Devel/Symdump/Export.pm blib/lib/Devel/Symdump/Export.pm
Manifying blib/man3/Devel::Symdump.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/autogen.....ok                                                             
t/diff........ok                                                             
t/export......ok                                                             
t/pod.........skipped
        all skipped: Test::Pod 1.00 required for testing POD
t/podcover....skipped
        all skipped: Test::Pod::Coverage required for testing pod coverage
t/recur.......ok                                                             
t/symdump.....ok                                                             
t/tree........ok                                                             
All tests successful, 2 tests skipped.
Files=8, Tests=29,  1 wallclock secs ( 0.31 cusr +  0.07 csys =  0.38 CPU)
  /usr/bin/make test -- OK
Running make install
Installing /usr/local/share/perl/5.8.8/Devel/Symdump.pm
Installing /usr/local/share/perl/5.8.8/Devel/Symdump/Export.pm
Installing /usr/local/man/man3/Devel::Symdump.3pm
Writing /usr/local/lib/perl/5.8.8/auto/Devel/Symdump/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module Switch
Running make for R/RG/RGARCIA/Switch-2.13.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz)
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/R/RG/RGARCIA/CHECKSUMS](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/R/RG/RGARCIA/CHECKSUMS)
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz ok
Scanning cache /root/.cpan/build for sizes
Switch-2.13/
Switch-2.13/t/
Switch-2.13/t/given.t
Switch-2.13/t/switch.t
Switch-2.13/t/nested.t
Switch-2.13/MANIFEST
Switch-2.13/META.yml
Switch-2.13/Changes
Switch-2.13/Switch.pm
Switch-2.13/README
Switch-2.13/Makefile.PL

  CPAN.pm: Going to build R/RG/RGARCIA/Switch-2.13.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Switch
cp Switch.pm blib/lib/Switch.pm
Manifying blib/man3/Switch.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/given.....ok                                                               
t/nested....ok                                                               
t/switch....ok                                                               
All tests successful.
Files=3, Tests=590,  2 wallclock secs ( 0.84 cusr +  0.03 csys =  0.87 CPU)
  /usr/bin/make test -- OK
Running make install
Installing /usr/local/share/perl/5.8.8/Switch.pm
Installing /usr/local/man/man3/Switch.3pm
Writing /usr/local/lib/perl/5.8.8/auto/Switch/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module Pod::Coverage
Running make for R/RC/RCLAMP/Pod-Coverage-0.19.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RC/RCLAMP/Pod-Coverage-0.19.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RC/RCLAMP/Pod-Coverage-0.19.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RC/RCLAMP/Pod-Coverage-0.19.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RC/RCLAMP/Pod-Coverage-0.19.tar.gz)
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/R/RC/RCLAMP/CHECKSUMS](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/R/RC/RCLAMP/CHECKSUMS)
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/R/RC/RCLAMP/Pod-Coverage-0.19.tar.gz ok
Scanning cache /root/.cpan/build for sizes
Pod-Coverage-0.19/
Pod-Coverage-0.19/bin/
Pod-Coverage-0.19/bin/pod_cover
Pod-Coverage-0.19/Build.PL
Pod-Coverage-0.19/Changes
Pod-Coverage-0.19/examples/
Pod-Coverage-0.19/examples/check_installed
Pod-Coverage-0.19/examples/script-covered
Pod-Coverage-0.19/lib/
Pod-Coverage-0.19/lib/Pod/
Pod-Coverage-0.19/lib/Pod/Coverage/
Pod-Coverage-0.19/lib/Pod/Coverage/CountParents.pm
Pod-Coverage-0.19/lib/Pod/Coverage/ExportOnly.pm
Pod-Coverage-0.19/lib/Pod/Coverage/Overloader.pm
Pod-Coverage-0.19/lib/Pod/Coverage.pm
Pod-Coverage-0.19/Makefile.PL
Pod-Coverage-0.19/MANIFEST
Pod-Coverage-0.19/META.yml
Pod-Coverage-0.19/README
Pod-Coverage-0.19/t/
Pod-Coverage-0.19/t/01compile.t
Pod-Coverage-0.19/t/02simple.t
Pod-Coverage-0.19/t/03import.t
Pod-Coverage-0.19/t/04cvgv.t
Pod-Coverage-0.19/t/05parentage.t
Pod-Coverage-0.19/t/06trustme.t
Pod-Coverage-0.19/t/07pod.t
Pod-Coverage-0.19/t/08tie.t
Pod-Coverage-0.19/t/lib/
Pod-Coverage-0.19/t/lib/Args.pm
Pod-Coverage-0.19/t/lib/Child.pm
Pod-Coverage-0.19/t/lib/Earle.pm
Pod-Coverage-0.19/t/lib/Fully/
Pod-Coverage-0.19/t/lib/Fully/Qualified.pm
Pod-Coverage-0.19/t/lib/GrandParent.pm
Pod-Coverage-0.19/t/lib/Parent.pm
Pod-Coverage-0.19/t/lib/Sibling.pm
Pod-Coverage-0.19/t/lib/Simple1.pm
Pod-Coverage-0.19/t/lib/Simple2.pm
Pod-Coverage-0.19/t/lib/Simple3.pm
Pod-Coverage-0.19/t/lib/Simple4.pm
Pod-Coverage-0.19/t/lib/Simple4.pod
Pod-Coverage-0.19/t/lib/Simple5.pm
Pod-Coverage-0.19/t/lib/Simple6.pm
Pod-Coverage-0.19/t/lib/Simple7.pm
Pod-Coverage-0.19/t/lib/Simple8.pm
Pod-Coverage-0.19/t/lib/Tie.pm
Pod-Coverage-0.19/t/lib/Trustme.pm
Pod-Coverage-0.19/t/lib/XS4ALL.pm

  CPAN.pm: Going to build R/RC/RCLAMP/Pod-Coverage-0.19.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Pod::Coverage
cp lib/Pod/Coverage.pm blib/lib/Pod/Coverage.pm
cp lib/Pod/Coverage/CountParents.pm blib/lib/Pod/Coverage/CountParents.pm
cp lib/Pod/Coverage/ExportOnly.pm blib/lib/Pod/Coverage/ExportOnly.pm
cp lib/Pod/Coverage/Overloader.pm blib/lib/Pod/Coverage/Overloader.pm
cp bin/pod_cover blib/script/pod_cover
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/pod_cover
Manifying blib/man3/Pod::Coverage::CountParents.3pm
Manifying blib/man3/Pod::Coverage.3pm
Manifying blib/man3/Pod::Coverage::ExportOnly.3pm
Manifying blib/man3/Pod::Coverage::Overloader.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/01compile......ok                                                          
t/02simple.......ok                                                          
t/03import.......ok                                                          
t/04cvgv.........ok                                                          
t/05parentage....ok                                                          
t/06trustme......ok                                                          
t/07pod..........skipped
        all skipped: Test::Pod 1.00 required for testing POD
t/08tie..........ok                                                          
All tests successful, 1 test skipped.
Files=8, Tests=63,  2 wallclock secs ( 0.70 cusr +  0.10 csys =  0.80 CPU)
  /usr/bin/make test -- OK
Running make install
Installing /usr/local/share/perl/5.8.8/Pod/Coverage.pm
Installing /usr/local/share/perl/5.8.8/Pod/Coverage/CountParents.pm
Installing /usr/local/share/perl/5.8.8/Pod/Coverage/ExportOnly.pm
Installing /usr/local/share/perl/5.8.8/Pod/Coverage/Overloader.pm
Installing /usr/local/man/man3/Pod::Coverage::CountParents.3pm
Installing /usr/local/man/man3/Pod::Coverage::ExportOnly.3pm
Installing /usr/local/man/man3/Pod::Coverage::Overloader.3pm
Installing /usr/local/man/man3/Pod::Coverage.3pm
Installing /usr/local/bin/pod_cover
Writing /usr/local/lib/perl/5.8.8/auto/Pod/Coverage/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module Test::Pod::Coverage
Running make for P/PE/PETDANCE/Test-Pod-Coverage-1.08.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/P/PE/PETDANCE/Test-Pod-Coverage-1.08.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/P/PE/PETDANCE/Test-Pod-Coverage-1.08.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/P/PE/PETDANCE/Test-Pod-Coverage-1.08.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/P/PE/PETDANCE/Test-Pod-Coverage-1.08.tar.gz)
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/P/PE/PETDANCE/CHECKSUMS](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/P/PE/PETDANCE/CHECKSUMS)
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/P/PE/PETDANCE/Test-Pod-Coverage-1.08.tar.gz ok
Scanning cache /root/.cpan/build for sizes
Test-Pod-Coverage-1.08/
Test-Pod-Coverage-1.08/t/
Test-Pod-Coverage-1.08/t/privates.t
Test-Pod-Coverage-1.08/t/parms.t
Test-Pod-Coverage-1.08/t/nopod.t
Test-Pod-Coverage-1.08/t/all_modules.t
Test-Pod-Coverage-1.08/t/Simple.pm
Test-Pod-Coverage-1.08/t/simple.t
Test-Pod-Coverage-1.08/t/self.t
Test-Pod-Coverage-1.08/t/PC_Inherits.pm
Test-Pod-Coverage-1.08/t/00.load.t
Test-Pod-Coverage-1.08/t/nosymbols.t
Test-Pod-Coverage-1.08/t/Privates.pm
Test-Pod-Coverage-1.08/t/PC_Inherited.pm
Test-Pod-Coverage-1.08/t/Nosymbols.pm
Test-Pod-Coverage-1.08/t/pod.t
Test-Pod-Coverage-1.08/t/all_pod_coverage_ok.t
Test-Pod-Coverage-1.08/t/Nopod.pm
Test-Pod-Coverage-1.08/t/alt_class.t
Test-Pod-Coverage-1.08/Changes
Test-Pod-Coverage-1.08/MANIFEST
Test-Pod-Coverage-1.08/Coverage.pm
Test-Pod-Coverage-1.08/META.yml
Test-Pod-Coverage-1.08/Makefile.PL

  CPAN.pm: Going to build P/PE/PETDANCE/Test-Pod-Coverage-1.08.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Test::Pod::Coverage
cp Coverage.pm blib/lib/Test/Pod/Coverage.pm
Manifying blib/man3/Test::Pod::Coverage.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00.load................# Testing Test::Pod::Coverage 1.08
t/00.load................ok                                                  
t/all_modules............ok                                                  
t/all_pod_coverage_ok....ok                                                  
t/alt_class..............ok                                                  
t/nopod..................ok                                                  
t/nosymbols..............ok                                                  
t/parms..................ok                                                  
t/pod....................skipped
        all skipped: Test::Pod 1.14 required for testing POD
t/privates...............ok                                                  
t/self...................ok                                                  
t/simple.................ok                                                  
All tests successful, 1 test skipped.
Files=11, Tests=22,  2 wallclock secs ( 0.94 cusr +  0.19 csys =  1.13 CPU)
  /usr/bin/make test -- OK
Running make install
Manifying blib/man3/Test::Pod::Coverage.3pm
Installing /usr/local/share/perl/5.8.8/Test/Pod/Coverage.pm
Installing /usr/local/man/man3/Test::Pod::Coverage.3pm
Writing /usr/local/lib/perl/5.8.8/auto/Test/Pod/Coverage/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module MP3::Info
Running make for D/DA/DANIEL/MP3-Info-1.23.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/MP3-Info-1.23.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/MP3-Info-1.23.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/MP3-Info-1.23.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/MP3-Info-1.23.tar.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/D/DA/DANIEL/MP3-Info-1.23.tar.gz](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/D/DA/DANIEL/MP3-Info-1.23.tar.gz)
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/D/DA/DANIEL/CHECKSUMS](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/D/DA/DANIEL/CHECKSUMS)
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/D/DA/DANIEL/MP3-Info-1.23.tar.gz ok
Scanning cache /root/.cpan/build for sizes
MP3-Info-1.23/
MP3-Info-1.23/inc/
MP3-Info-1.23/inc/Module/
MP3-Info-1.23/inc/Module/Install.pm
MP3-Info-1.23/inc/Module/Install/
MP3-Info-1.23/inc/Module/Install/AutoInstall.pm
MP3-Info-1.23/inc/Module/Install/Fetch.pm
MP3-Info-1.23/inc/Module/Install/Makefile.pm
MP3-Info-1.23/inc/Module/Install/Include.pm
MP3-Info-1.23/inc/Module/Install/Base.pm
MP3-Info-1.23/inc/Module/Install/Metadata.pm
MP3-Info-1.23/inc/Module/Install/Can.pm
MP3-Info-1.23/inc/Module/Install/WriteAll.pm
MP3-Info-1.23/inc/Module/Install/Win32.pm
MP3-Info-1.23/inc/Module/AutoInstall.pm
MP3-Info-1.23/Changes
MP3-Info-1.23/t/
MP3-Info-1.23/t/test1.mp3
MP3-Info-1.23/t/id3.t
MP3-Info-1.23/t/testv1.mp3
MP3-Info-1.23/t/testv2.2.0.mp3
MP3-Info-1.23/t/getset.t
MP3-Info-1.23/t/testv2.3.0.mp3
MP3-Info-1.23/t/testv1.1.mp3
MP3-Info-1.23/t/test2.mp3
MP3-Info-1.23/t/testv2.4.0.mp3
MP3-Info-1.23/t/test.aiff
MP3-Info-1.23/t/lame-info.t
MP3-Info-1.23/t/remove.t
MP3-Info-1.23/MANIFEST
MP3-Info-1.23/TODO
MP3-Info-1.23/eg/
MP3-Info-1.23/eg/mp3tag.PL
MP3-Info-1.23/eg/mp3tocddb.PL
MP3-Info-1.23/Info.pm
MP3-Info-1.23/README
MP3-Info-1.23/Makefile.PL

  CPAN.pm: Going to build D/DA/DANIEL/MP3-Info-1.23.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for MP3::Info
cp Info.pm blib/lib/MP3/Info.pm
Manifying blib/man3/MP3::Info.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'inc', 'blib/lib', 'blib/arch')" t/getset.t t/id3.t t/lame-info.t t/remove.t
t/getset.......ok                                                            
t/id3..........ok                                                            
t/lame-info....ok                                                            
t/remove.......ok                                                            
All tests successful.
Files=4, Tests=246,  1 wallclock secs ( 0.38 cusr +  0.08 csys =  0.46 CPU)
  /usr/bin/make test -- OK
Running make install
Manifying blib/man3/MP3::Info.3pm
Installing /usr/local/share/perl/5.8.8/MP3/Info.pm
Installing /usr/local/man/man3/MP3::Info.3pm
Writing /usr/local/lib/perl/5.8.8/auto/MP3/Info/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module Audio::Musepack
Running make for D/DA/DANIEL/Audio-Musepack-0.7.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/Audio-Musepack-0.7.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/Audio-Musepack-0.7.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authorFetching](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authorFetching) with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/D/DA/DANIEL/Audio-Musepack-0.7.tar.gz](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/D/DA/DANIEL/Audio-Musepack-0.7.tar.gz)
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/D/DA/DANIEL/Audio-Musepack-0.7.tar.gz ok
Scanning cache /root/.cpan/build for sizes
Audio-Musepack-0.7/
Audio-Musepack-0.7/data/
Audio-Musepack-0.7/data/test.mpc
Audio-Musepack-0.7/data/test.ape
Audio-Musepack-0.7/inc/
Audio-Musepack-0.7/inc/Module/
Audio-Musepack-0.7/inc/Module/Install.pm
Audio-Musepack-0.7/inc/Module/Install/
Audio-Musepack-0.7/inc/Module/Install/AutoInstall.pm
Audio-Musepack-0.7/inc/Module/Install/Fetch.pm
Audio-Musepack-0.7/inc/Module/Install/Makefile.pm
Audio-Musepack-0.7/inc/Module/Install/Include.pm
Audio-Musepack-0.7/inc/Module/Install/Base.pm
Audio-Musepack-0.7/inc/Module/Install/Metadata.pm
Audio-Musepack-0.7/inc/Module/Install/Can.pm
Audio-Musepack-0.7/inc/Module/Install/WriteAll.pm
Audio-Musepack-0.7/inc/Module/Install/Win32.pm
Audio-Musepack-0.7/inc/Module/AutoInstall.pm
Audio-Musepack-0.7/lib/
Audio-Musepack-0.7/lib/Audio/
Audio-Musepack-0.7/lib/Audio/APETags.pm
Audio-Musepack-0.7/lib/Audio/Musepack.pm
Audio-Musepack-0.7/lib/Audio/APE.pm
Audio-Musepack-0.7/Changes
Audio-Musepack-0.7/MANIFEST
Audio-Musepack-0.7/t/
Audio-Musepack-0.7/t/basic.t
Audio-Musepack-0.7/t/pod-coverage.t
Audio-Musepack-0.7/t/pod.t
Audio-Musepack-0.7/META.yml
Audio-Musepack-0.7/README
Audio-Musepack-0.7/Makefile.PL

  CPAN.pm: Going to build D/DA/DANIEL/Audio-Musepack-0.7.tar.gz

*** Module::AutoInstall version 1.03
*** Checking for Perl dependencies...
[Core Features]
- MP3::Info ...loaded. (1.23 >= 1.20)
*** Module::AutoInstall configuration finished.
Checking if your kit is complete...
Looks good
Writing Makefile for Audio::Musepack
cp lib/Audio/APETags.pm blib/lib/Audio/APETags.pm
cp lib/Audio/Musepack.pm blib/lib/Audio/Musepack.pm
cp lib/Audio/APE.pm blib/lib/Audio/APE.pm
Manifying blib/man3/Audio::APETags.3pm
Manifying blib/man3/Audio::Musepack.3pm
Manifying blib/man3/Audio::APE.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'inc', 'blib/lib', 'blib/arch')" t/basic.t t/pod-coverage.t t/pod.t
t/basic...........ok                                                         
t/pod-coverage....ok                                                         
t/pod.............skipped
        all skipped: Test::Pod 1.00 required for testing POD
All tests successful, 1 test skipped.
Files=3, Tests=10,  0 wallclock secs ( 0.25 cusr +  0.04 csys =  0.29 CPU)
  /usr/bin/make test -- OK
Running make install
Installing /usr/local/share/perl/5.8.8/Audio/APETags.pm
Installing /usr/local/share/perl/5.8.8/Audio/Musepack.pm
Installing /usr/local/share/perl/5.8.8/Audio/APE.pm
Installing /usr/local/man/man3/Audio::APE.3pm
Installing /usr/local/man/man3/Audio::Musepack.3pm
Installing /usr/local/man/man3/Audio::APETags.3pm
Writing /usr/local/lib/perl/5.8.8/auto/Audio/Musepack/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module Audio::WMA
Running make for D/DA/DANIEL/Audio-WMA-1.1.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/Audio-WMA-1.1.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/Audio-WMA-1.1.tar.gz)
s/id/D/DA/DANIEL/Audio-Musepack-0.7.tar.gz
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/Audio-WMA-1.1.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/D/DA/DANIEL/Audio-WMA-1.1.tar.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/D/DA/DANIEL/Audio-WMA-1.1.tar.gz](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/D/DA/DANIEL/Audio-WMA-1.1.tar.gz)
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/D/DA/DANIEL/Audio-WMA-1.1.tar.gz ok
Scanning cache /root/.cpan/build for sizes
Audio-WMA-1.1/
Audio-WMA-1.1/inc/
Audio-WMA-1.1/inc/Module/
Audio-WMA-1.1/inc/Module/Install.pm
Audio-WMA-1.1/inc/Module/Install/
Audio-WMA-1.1/inc/Module/Install/AutoInstall.pm
Audio-WMA-1.1/inc/Module/Install/Fetch.pm
Audio-WMA-1.1/inc/Module/Install/Makefile.pm
Audio-WMA-1.1/inc/Module/Install/Include.pm
Audio-WMA-1.1/inc/Module/Install/Base.pm
Audio-WMA-1.1/inc/Module/Install/Metadata.pm
Audio-WMA-1.1/inc/Module/Install/Can.pm
Audio-WMA-1.1/inc/Module/Install/WriteAll.pm
Audio-WMA-1.1/inc/Module/Install/Win32.pm
Audio-WMA-1.1/inc/Module/AutoInstall.pm
Audio-WMA-1.1/data/
Audio-WMA-1.1/data/test-drm.wma
Audio-WMA-1.1/data/test1.wma
Audio-WMA-1.1/data/test2.wma
Audio-WMA-1.1/Changes
Audio-WMA-1.1/t/
Audio-WMA-1.1/t/drm.t
Audio-WMA-1.1/t/pod-coverage.t
Audio-WMA-1.1/t/2.t
Audio-WMA-1.1/t/1.t
Audio-WMA-1.1/t/pod.t
Audio-WMA-1.1/MANIFEST
Audio-WMA-1.1/META.yml
Audio-WMA-1.1/WMA.pm
Audio-WMA-1.1/README
Audio-WMA-1.1/Makefile.PL

  CPAN.pm: Going to build D/DA/DANIEL/Audio-WMA-1.1.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Audio::WMA
cp WMA.pm blib/lib/Audio/WMA.pm
Manifying blib/man3/Audio::WMA.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'inc', 'blib/lib', 'blib/arch')" t/1.t t/2.t t/drm.t t/pod-coverage.t t/pod.t
t/1...............ok                                                         
t/2...............ok                                                         
t/drm.............ok                                                         
t/pod-coverage....ok                                                         
t/pod.............skipped
        all skipped: Test::Pod 1.00 required for testing POD
All tests successful, 1 test skipped.
Files=5, Tests=20,  0 wallclock secs ( 0.30 cusr +  0.06 csys =  0.36 CPU)
  /usr/bin/make test -- OK
Running make install
Manifying blib/man3/Audio::WMA.3pm
Installing /usr/local/share/perl/5.8.8/Audio/WMA.pm
Installing /usr/local/man/man3/Audio::WMA.3pm
Writing /usr/local/lib/perl/5.8.8/auto/Audio/WMA/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module MP3::Tag
Running make for I/IL/ILYAZ/modules/MP3-Tag-0.9710.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/I/IL/ILYAZ/modules/MP3-Tag-0.9710.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/I/IL/ILYAZ/modules/MP3-Tag-0.9710.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/I/IL/ILYAZ/modules/MP3-Tag-0.9710.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/I/IL/ILYAZ/modules/MP3-Tag-0.9710.tar.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/I/IL/ILYAZ/modules/MP3-Tag-0.9710.tar.gz](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/I/IL/ILYAZ/modules/MP3-Tag-0.9710.tar.gz)
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/I/IL/ILYAZ/modules/CHECKSUMS](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/I/IL/ILYAZ/modules/CHECKSUMS)
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/I/IL/ILYAZ/modules/MP3-Tag-0.9710.tar.gz ok
Scanning cache /root/.cpan/build for sizes
MP3-Tag-0.9710/
MP3-Tag-0.9710/cddb.tm
MP3-Tag-0.9710/cddb.tmp
MP3-Tag-0.9710/Changes
MP3-Tag-0.9710/data_pod.PL
MP3-Tag-0.9710/examples/
MP3-Tag-0.9710/examples/audio_rename
MP3-Tag-0.9710/examples/cddb2cddb.pl
MP3-Tag-0.9710/examples/dir_mp3_2fake_cddb.pl
MP3-Tag-0.9710/examples/eat_wav_mp3_header.pl
MP3-Tag-0.9710/examples/empty.mp3
MP3-Tag-0.9710/examples/empty_10sec.mp3
MP3-Tag-0.9710/examples/extract-y.pl
MP3-Tag-0.9710/examples/extractID3v2.pl
MP3-Tag-0.9710/examples/fetch_composer_codm.pl
MP3-Tag-0.9710/examples/fetch_composer_wiki.pl
MP3-Tag-0.9710/examples/fulltoc_2fake_cddb.pl
MP3-Tag-0.9710/examples/inf_2fake_cddb.pl
MP3-Tag-0.9710/examples/mod/
MP3-Tag-0.9710/examples/mod/manage_M_N_F.pm
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields/
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields/A_Dvor_k.comp
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields/A_Schnittke.comp
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields/D_Shostakovich.comp
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields/G_Gershwin.comp
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields/J_Brahms.comp
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields/L_van_Beethoven.comp
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields/Music_Normalize_Fields-rus.lst
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields/Music_Normalize_Fields.lst
MP3-Tag-0.9710/examples/mod/Music_Normalize_Fields.pm
MP3-Tag-0.9710/examples/mod/Music_Translate_Fields.pm
MP3-Tag-0.9710/examples/mod/transliterate_win1251.pm
MP3-Tag-0.9710/examples/mp3info.pl
MP3-Tag-0.9710/examples/mp3info2
MP3-Tag-0.9710/examples/mp3_total_time.pl
MP3-Tag-0.9710/examples/Music_Normalize_Fields-normalize.pl
MP3-Tag-0.9710/examples/README.txt
MP3-Tag-0.9710/examples/src/
MP3-Tag-0.9710/examples/src/Beethoven.all_y
MP3-Tag-0.9710/examples/src/HOWTO
MP3-Tag-0.9710/examples/tagged.pl
MP3-Tag-0.9710/examples/tagit.pl
MP3-Tag-0.9710/examples/typeset_audio_dir
MP3-Tag-0.9710/ID3v2-Data.pod
MP3-Tag-0.9710/Makefile.PL
MP3-Tag-0.9710/MANIFEST
MP3-Tag-0.9710/META.yml
MP3-Tag-0.9710/README.shrink
MP3-Tag-0.9710/README.txt
MP3-Tag-0.9710/t/
MP3-Tag-0.9710/t/interpolate.t
MP3-Tag-0.9710/t/mp3tag.t
MP3-Tag-0.9710/t/parser.t
MP3-Tag-0.9710/t/set_v2.t
MP3-Tag-0.9710/t/update_tags.t
MP3-Tag-0.9710/t/v2_comments.t
MP3-Tag-0.9710/Tag/
MP3-Tag-0.9710/Tag/CDDB_File.pm
MP3-Tag-0.9710/Tag/File.pm
MP3-Tag-0.9710/Tag/ID3v1.pm
MP3-Tag-0.9710/Tag/ID3v2.pm
MP3-Tag-0.9710/Tag/Inf.pm
MP3-Tag-0.9710/Tag/LastResort.pm
MP3-Tag-0.9710/Tag/ParseData.pm
MP3-Tag-0.9710/Tag.pm
MP3-Tag-0.9710/test.mp3
MP3-Tag-0.9710/tk-tag/
MP3-Tag-0.9710/tk-tag/README
MP3-Tag-0.9710/tk-tag/tk-tag.pl
MP3-Tag-0.9710/TODO

  CPAN.pm: Going to build I/IL/ILYAZ/modules/MP3-Tag-0.9710.tar.gz


This program comes with several scripts which I would try to install in
directory /usr/bin.

To skip, rerun with option -n given to Makefile.PL.

Checking if your kit is complete...
Looks good
Writing Makefile for MP3::Tag
cp Tag.pm blib/lib/MP3/Tag.pm
cp Tag/ID3v1.pm blib/lib/MP3/Tag/ID3v1.pm
cp Tag/File.pm blib/lib/MP3/Tag/File.pm
cp Tag/CDDB_File.pm blib/lib/MP3/Tag/CDDB_File.pm
cp Tag/ParseData.pm blib/lib/MP3/Tag/ParseData.pm
cp Tag/Inf.pm blib/lib/MP3/Tag/Inf.pm
cp Tag/ID3v2.pm blib/lib/MP3/Tag/ID3v2.pm
cp ID3v2-Data.pod blib/lib/MP3/ID3v2-Data.pod
cp Tag/LastResort.pm blib/lib/MP3/Tag/LastResort.pm
cp examples/typeset_audio_dir blib/script/typeset_audio_dir
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/typeset_audio_dir
cp examples/mp3info2 blib/script/mp3info2
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/mp3info2
cp examples/audio_rename blib/script/audio_rename
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/audio_rename
Manifying blib/man1/typeset_audio_dir.1p
Manifying blib/man1/mp3info2.1p
Manifying blib/man1/audio_rename.1p
Manifying blib/man3/MP3::Tag.3pm
Manifying blib/man3/MP3::Tag::ID3v1.3pm
Manifying blib/man3/MP3::Tag::File.3pm
Manifying blib/man3/MP3::Tag::CDDB_File.3pm
Manifying blib/man3/MP3::Tag::ParseData.3pm
Manifying blib/man3/MP3::Tag::Inf.3pm
Manifying blib/man3/MP3::Tag::ID3v2.3pm
Manifying blib/man3/MP3::Tag::ID3v2-Data.3pm
Manifying blib/man3/MP3::Tag::LastResort.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/interpolate....ok                                                          
t/mp3tag.........ok                                                          
t/parser.........ok                                                          
t/set_v2.........ok                                                          
t/update_tags....ok                                                          
t/v2_comments....ok                                                          
All tests successful.
Files=6, Tests=377,  1 wallclock secs ( 0.85 cusr +  0.20 csys =  1.05 CPU)
  /usr/bin/make test -- OK
Running make install
Installing /usr/local/share/perl/5.8.8/MP3/ID3v2-Data.pod
Installing /usr/local/share/perl/5.8.8/MP3/Tag.pm
Installing /usr/local/share/perl/5.8.8/MP3/Tag/LastResort.pm
Installing /usr/local/share/perl/5.8.8/MP3/Tag/CDDB_File.pm
Installing /usr/local/share/perl/5.8.8/MP3/Tag/ID3v1.pm
Installing /usr/local/share/perl/5.8.8/MP3/Tag/File.pm
Installing /usr/local/share/perl/5.8.8/MP3/Tag/ParseData.pm
Installing /usr/local/share/perl/5.8.8/MP3/Tag/ID3v2.pm
Installing /usr/local/share/perl/5.8.8/MP3/Tag/Inf.pm
Installing /usr/local/man/man1/typeset_audio_dir.1p
Installing /usr/local/man/man1/audio_rename.1p
Installing /usr/local/man/man1/mp3info2.1p
Installing /usr/local/man/man3/MP3::Tag.3pm
Installing /usr/local/man/man3/MP3::Tag::File.3pm
Installing /usr/local/man/man3/MP3::Tag::ParseData.3pm
Installing /usr/local/man/man3/MP3::Tag::ID3v1.3pm
Installing /usr/local/man/man3/MP3::Tag::CDDB_File.3pm
Installing /usr/local/man/man3/MP3::Tag::LastResort.3pm
Installing /usr/local/man/man3/MP3::Tag::Inf.3pm
Installing /usr/local/man/man3/MP3::Tag::ID3v2.3pm
Installing /usr/local/man/man3/MP3::Tag::ID3v2-Data.3pm
Installing /usr/local/bin/audio_rename
Installing /usr/local/bin/typeset_audio_dir
Installing /usr/local/bin/mp3info2
Writing /usr/local/lib/perl/5.8.8/auto/MP3/Tag/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Ogg::Vorbis::Header is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
IO::String is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
MP4::Info is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Audio::APETags is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module CDDB_get
Running make for F/FO/FONKIE/CDDB_get-2.27.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/F/FO/FONKIE/CDDB_get-2.27.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/F/FO/FONKIE/CDDB_get-2.27.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/F/FO/FONKIE/CDDB_get-2.27.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/F/FO/FONKIE/CDDB_get-2.27.tar.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/F/FO/FONKIE/CDDB_get-2.27.tar.gz](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/F/FO/FONKIE/CDDB_get-2.27.tar.gz)
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/F/FO/FONKIE/CHECKSUMS](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/F/FO/FONKIE/CHECKSUMS)
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/F/FO/FONKIE/CDDB_get-2.27.tar.gz ok
Scanning cache /root/.cpan/build for sizes
CDDB_get-2.27/
CDDB_get-2.27/t/
CDDB_get-2.27/t/use.t
CDDB_get-2.27/README
CDDB_get-2.27/CDDB_get.pm
CDDB_get-2.27/Changes
CDDB_get-2.27/Copying
CDDB_get-2.27/Artistic
CDDB_get-2.27/Makefile.PL
CDDB_get-2.27/META.yml
CDDB_get-2.27/DATABASE
CDDB_get-2.27/perl-CDDB_get-2.27.spec
CDDB_get-2.27/CDDB_cache.pm
CDDB_get-2.27/cddb.pl
CDDB_get-2.27/MANIFEST

  CPAN.pm: Going to build F/FO/FONKIE/CDDB_get-2.27.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for CDDB_get
cp CDDB_get.pm blib/lib/CDDB_get.pm
AutoSplitting blib/lib/CDDB_get.pm (blib/lib/auto/CDDB_get)
cp cddb.pl blib/lib/cddb.pl
cp CDDB_cache.pm blib/lib/CDDB_cache.pm
AutoSplitting blib/lib/CDDB_cache.pm (blib/lib/auto/CDDB_cache)
cp cddb.pl blib/script/cddb.pl
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/cddb.pl
Manifying blib/man3/CDDB_get.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/use....ok                                                                  
All tests successful.
Files=1, Tests=1,  0 wallclock secs ( 0.07 cusr +  0.00 csys =  0.07 CPU)
  /usr/bin/make test -- OK
Running make install
Installing /usr/local/share/perl/5.8.8/cddb.pl
Installing /usr/local/share/perl/5.8.8/CDDB_get.pm
Installing /usr/local/share/perl/5.8.8/CDDB_cache.pm
Installing /usr/local/share/perl/5.8.8/auto/CDDB_get/autosplit.ix
Installing /usr/local/share/perl/5.8.8/auto/CDDB_cache/autosplit.ix
Installing /usr/local/man/man3/CDDB_get.3pm
Installing /usr/local/bin/cddb.pl
Writing /usr/local/lib/perl/5.8.8/auto/CDDB_get/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK

Finished! 
```I hope someone can make sense of this.

---

### Post by cozmicharlie on 2008-03-21
Did you try and run PACPL to see if it works?

---

### Post by pemur1 on 2008-03-21
> **cozmicharlie said:**
> Did you try and run PACPL to see if it works?

Not yet. I have to figure out how it works. I'm not particularly adept at using the Terminal.

---

### Post by cozmicharlie on 2008-03-21
simple - open a terminal and type the following at the prompt

pacpl --longhelp

---

### Post by pemur1 on 2008-03-21
> **cozmicharlie said:**
> simple - open a terminal and type the following at the prompt

pacpl --longhelp

Thank you!

Let me ask you this. If I wanted to say convert a wv file (or batch convert) what would the syntax be? Sorry if I sound noobieish. :)

---

### Post by pemur1 on 2008-03-21
BTW, I can now install the updates. Thanks for your assistance.

Also, what about updating the program? I noticed that I may have installed an old version. Is there a way to update it?

---

### Post by cozmicharlie on 2008-03-21
Another command you will want to run 
```
pacpl -f
```
This gives you a list of all the codecs you have installed that PACPl is using.  If you find you are missing some that you need (mp3 for example) then go to synaptic and install them.  Feel free to post back to the tutorial if you have more questions.  Also, their is a help forum at the PACPL sourceforge sight and Philip (the developer) is very helpful if you need to email him.

There is no automatic update.  Basically, you just install a new version over the top of the old one or uninstall the old version and install the new one.  Now that you have all the dependencies all you should need to do is:

download pacpl.tar.bz (I just download to my desktop)
extract (right click - extract here)
cd to the untarred folder
```
./configure
```
```
make
```
```
sudo make install
```

and that should do it.



Enjoy

---

### Post by pemur1 on 2008-03-21
Thanks so much for your help with this. I'm so glad I got rid of Windows. It's people like you who make the transition so easy. Again, thanks for all of your assistance.

---

