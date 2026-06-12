---
title: "problem with apt-get"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by hoco on 2012-06-15
hi
 i wanted to install kmplayer 
```
sudo apt-get install kmplayer
```

but after, installing was failed, because of :
```
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
what should I do?

also, when i want to download form ubuntu software center, it says:
```
The action would require the installation of packages from not authenticated sources.
```
 
help me , plz

---

### Post by lykwydchykyn on 2012-06-15
- Did you try running "apt-get update" as suggested?

 - If that didn't work, can you post the ENTIRE output of "apt-get install kmplayer"?

---

### Post by hoco on 2012-06-16
i tried it, but it didn't work.

the output:
```
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkdnssd4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkemoticons4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkfile4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkjsapi4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkhtml5 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkidletime4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkmediaplayer4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libknewstuff3-4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libknotifyconfig4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libnepomukdatamanagement4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libnepomuksync4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main ntrack-module-libnl-0 amd64 016-1ubuntu1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libntrack0 amd64 016-1ubuntu1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libntrack-qt4-1 amd64 016-1ubuntu1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libilmbase6 amd64 1.0.1-3build2
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libopenexr6 amd64 1.6.1-4.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libqca2 amd64 2.0.3-2
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libthreadweaver4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libplasma3 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main phonon amd64 4:4.7.0really4.6.0-0ubuntu1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main kde-runtime-data all 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkde3support4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkjsembed4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkntlm4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libkrosscore4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libpolkit-qt-1-1 amd64 0.103.0-1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main kdelibs5-data all 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main kdoctools amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main kdelibs-bin amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main kdelibs5-plugins amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main oxygen-icon-theme all 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main shared-desktop-ontologies all 0.8.1-1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main plasma-scriptengine-javascript amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main kde-runtime amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/universe kmplayer amd64 1:0.11.3a-1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libqapt1 amd64 1.3.1-0ubuntu2
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libqapt-runtime amd64 1.3.1-0ubuntu2
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main qapt-batch amd64 1.3.1-0ubuntu2
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main kubuntu-debug-installer amd64 11.10ubuntu1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libfont-afm-perl all 1.20-1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libhtml-form-perl all 6.00-1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libhtml-format-perl all 2.10-1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libhttp-daemon-perl all 6.00-1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libsocket6-perl amd64 0.23-1build2
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libio-socket-inet6-perl all 2.69-2
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main libmailtools-perl all 2.08-1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main virtuoso-opensource-6.1-bin amd64 6.1.4+dfsg1-0ubuntu1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ir.archive.ubuntu.com/ubuntu/ precise/main virtuoso-minimal all 6.1.4+dfsg1-0ubuntu1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/s/sgml-data/sgml-data_2.0.6_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/d/docbook-xml/docbook-xml_4.5-7ubuntu1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/g/giflib/libgif4_4.1.6-9ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/p/phonon/libphonon4_4.7.0really4.6.0-0ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.8.1-0ubuntu4.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.8.1-0ubuntu4.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/q/qtwebkit-source/libqtwebkit4_2.2.1-1ubuntu4_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst_2.2.14p2-5ubuntu3_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian2_2.2.14p2-5ubuntu3_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/p/phonon-backend-gstreamer/phonon-backend-gstreamer_4.7.0really4.6.0-0ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/d/docbook-xsl/docbook-xsl_1.76.1+dfsg-1ubuntu1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libe/libencode-locale-perl/libencode-locale-perl_1.02-2_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libt/libtimedate-perl/libtimedate-perl_1.2000-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhttp-date-perl/libhttp-date-perl_6.00-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libf/libfile-listing-perl/libfile-listing-perl_6.03-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libu/liburi-perl/liburi-perl_1.59-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhtml-tagset-perl/libhtml-tagset-perl_3.20-2_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhtml-parser-perl/libhtml-parser-perl_3.69-1build1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhtml-tree-perl/libhtml-tree-perl_4.2-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libl/liblwp-mediatypes-perl/liblwp-mediatypes-perl_6.01-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhttp-message-perl/libhttp-message-perl_6.01-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhttp-cookies-perl/libhttp-cookies-perl_6.00-2_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhttp-negotiate-perl/libhttp-negotiate-perl_6.00-2_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libn/libnet-http-perl/libnet-http-perl_6.02-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libn/libnet-ssleay-perl/libnet-ssleay-perl_1.42-1build1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libi/libio-socket-ssl-perl/libio-socket-ssl-perl_1.53-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libl/liblwp-protocol-https-perl/liblwp-protocol-https-perl_6.02-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libw/libwww-robotrules-perl/libwww-robotrules-perl_6.01-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libw/libwww-perl/libwww-perl_6.03-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/i/icoutils/icoutils_0.29.1-2_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kate/kate-data_4.8.3-0ubuntu0.1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/p/pkg-kde-tools/libdlrestrictions1_0.14.2ubuntu5_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdecore5_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/a/attica/libattica0.3_0.3.0-0ubuntu2_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdeui5_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkcmutils4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/c/clucene-core/libclucene0ldbl_0.9.21b-2_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/v/virtuoso-opensource/virtuoso-opensource-6.1-common_6.1.4+dfsg1-0ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/v/virtuoso-opensource/libvirtodbc0_6.1.4+dfsg1-0ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/s/soprano/soprano-daemon_2.7.5+dfsg.1-0ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/s/soprano/libsoprano4_2.7.5+dfsg.1-0ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libnepomuk4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libsolid4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.7.7-1.1ubuntu3_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.7.7-1.1ubuntu3_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkio5_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libnepomukquery4a_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libnepomukutils4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkparts4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libktexteditor4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kate/libkatepartinterfaces4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kate/katepart_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdeclarative5_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkpty4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdesu5_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdewebkit5_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdnssd4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkemoticons4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkfile4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkjsapi4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkhtml5_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkidletime4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkmediaplayer4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libknewstuff3-4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libknotifyconfig4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde-runtime/libnepomukdatamanagement4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde-runtime/libnepomuksync4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/n/ntrack/ntrack-module-libnl-0_016-1ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/n/ntrack/libntrack0_016-1ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/n/ntrack/libntrack-qt4-1_016-1ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/i/ilmbase/libilmbase6_1.0.1-3build2_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/o/openexr/libopenexr6_1.6.1-4.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/q/qca2/libqca2_2.0.3-2_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libthreadweaver4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libplasma3_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon_4.7.0really4.6.0-0ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde-runtime/kde-runtime-data_4.8.3-0ubuntu0.1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkde3support4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkjsembed4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkntlm4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkrosscore4_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/p/polkit-qt-1/libpolkit-qt-1-1_0.103.0-1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.8.3-0ubuntu0.1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdoctools_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-plugins_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/o/oxygen-icons/oxygen-icon-theme_4.8.3-0ubuntu0.1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/s/shared-desktop-ontologies/shared-desktop-ontologies_0.8.1-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde-runtime/plasma-scriptengine-javascript_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kde-runtime/kde-runtime_4.8.3-0ubuntu0.1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/universe/k/kmplayer/kmplayer_0.11.3a-1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/q/qapt/libqapt1_1.3.1-0ubuntu2_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/q/qapt/libqapt-runtime_1.3.1-0ubuntu2_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/q/qapt/qapt-batch_1.3.1-0ubuntu2_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-debug-installer/kubuntu-debug-installer_11.10ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libf/libfont-afm-perl/libfont-afm-perl_1.20-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhtml-form-perl/libhtml-form-perl_6.00-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhtml-format-perl/libhtml-format-perl_2.10-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libh/libhttp-daemon-perl/libhttp-daemon-perl_6.00-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libs/libsocket6-perl/libsocket6-perl_0.23-1build2_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libi/libio-socket-inet6-perl/libio-socket-inet6-perl_2.69-2_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/libm/libmailtools-perl/libmailtools-perl_2.08-1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/v/virtuoso-opensource/virtuoso-opensource-6.1-bin_6.1.4+dfsg1-0ubuntu1_amd64.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/v/virtuoso-opensource/virtuoso-minimal_6.1.4+dfsg1-0ubuntu1_all.deb  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by cybercity@localhost on 2012-06-17
try this...
```
 sudo apt-get install kmplayer --forces-yes
```

this is because the package is from unauthenticated source we have to force apt to just install the package without authentication.

if it still doesn't work try

apt-get install -f

or apt-get install --fix-missing

---

### Post by Cheesehead on 2012-06-17
> **hoco said:**
> Err [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) precise-updates/main libkdnssd4 amd64 4:4.8.3-0ubuntu0.1
  Something wicked happened resolving 'ir.archive.ubuntu.com:http' (-5 - No address associated with hostname)

Looks like you were trying at a time when that mirror was down.

Make sure the mirror [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) is working.
Or go into Software Sources (in Synaptic's or Software Center's settings) and select a different mirror.

---

### Post by firekage on 2012-06-17
> **cybercity@localhost said:**
> try this...
```
 sudo apt-get install kmplayer **--**forces-yes
```this is because the package is from unauthenticated source we have to force apt to just install the package without authentication.

if it still doesn't work try

apt-get install **-**f

or apt-get install --fix-missing

Sorry for stupid question but why sometimes in commands there is:

- 

and sometimes it is:

--

Can You explain this?

---

### Post by lykwydchykyn on 2012-06-17
> **firekage said:**
> Sorry for stupid question but why sometimes in commands there is:

- 

and sometimes it is:

--

Can You explain this?


Generally one dash is for single-letter (a.k.a. shorthand) switches, and two dashes are for the more verbose long-form switches.  I believe this is a GNU convention, and many other projects follow the same.

Not every program follows that convention though, mostly because programs are all written by different people and nothing forces them to follow the same rules.

---

### Post by cybercity@localhost on 2012-06-18
> Looks like you were trying at a time when that mirror was down.

Make sure the mirror [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) is working.
Or go into Software Sources (in Synaptic's or Software Center's settings) and select a different mirror.

agree with that.

---

### Post by firekage on 2012-06-18
> **lykwydchykyn said:**
> Generally one dash is for single-letter (a.k.a. shorthand) switches, and two dashes are for the more verbose long-form switches.  I believe this is a GNU convention, and many other projects follow the same.

Not every program follows that convention though, mostly because programs are all written by different people and nothing forces them to follow the same rules.

Thank You very much. I didn't know this. Nice to know. :)

---

