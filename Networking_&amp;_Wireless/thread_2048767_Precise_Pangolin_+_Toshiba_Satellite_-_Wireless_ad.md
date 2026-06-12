---
title: "Precise Pangolin + Toshiba Satellite - Wireless adapter stopped working during update"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by KomodoDave on 2012-08-27
I've got a Toshiba Satellite A660-18N, it has a Realtek wireless adapter.

I recently installed Ubuntu 12.04 x64 and successfully used the wireless adapter out-of-the-box for a week or so with no issues.

Last night an automatic update was requested with two wireless security package installs/updates. I accepted the update, and during installation my wireless adapter disappeared from the network dropdown on the taskbar.

There are 2 keyboard shortcuts on the laptop to enable wireless hardware - which could be the problem - but neither functions in Ubuntu (one is Fn + F8, the other a wireless specific media key). The bios offers no options to enable the wireless adapter.

The media key shortcut for wireless was working until the update, as were the other media keys (volume etc). Potentially reinstalling/reconfiguring package(s) related to these would allow me to reenable the adapter, if that's the problem. I'm currently trying to find out how to reenable these.

Below is relevant output:

```
ndb@ndb-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
``````
ndb@ndb-ubuntu:~$ sudo lshw -class Network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:51:3d:29
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-1.fw ip=192.168.0.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:6000(size=256) memory:d3104000-d3104fff memory:d3100000-d3103fff memory:d3120000-d313ffff
```Packages installed during the update last night:

```

ndb@ndb-ubuntu:~$ cat /var/log/dpkg.log | grep "\ install\ "
2012-08-24 01:10:11 install libgcj-common <none> 1:4.6.3-1ubuntu5
2012-08-24 01:10:12 install gcj-4.6-base <none> 4.6.3-1ubuntu2
2012-08-24 01:10:12 install libgcj12 <none> 4.6.3-1ubuntu2
2012-08-24 01:10:14 install libgcj-bc <none> 4.6.3-1ubuntu5
2012-08-24 01:10:14 install openjdk-6-jre-lib <none> 6b24-1.11.3-1ubuntu0.12.04.1
2012-08-24 01:10:15 install openjdk-6-jre-headless <none> 6b24-1.11.3-1ubuntu0.12.04.1
2012-08-24 01:10:17 install libxml-commons-resolver1.1-java <none> 1.2-7
2012-08-24 01:10:18 install libxml-commons-external-java <none> 1.4.01-2
2012-08-24 01:10:18 install libxerces2-java <none> 2.11.0-4
2012-08-24 01:10:19 install ant <none> 1.8.2-4build1
2012-08-24 01:10:19 install ant-optional <none> 1.8.2-4build1
2012-08-24 01:10:20 install libaspectj-java <none> 1.6.12+dfsg-3
2012-08-24 01:10:21 install aspectj <none> 1.6.12+dfsg-3
2012-08-24 01:10:21 install libjline-java <none> 1.0-1
2012-08-24 01:10:22 install bsh <none> 2.0b4-12build1
2012-08-24 01:10:22 install bsh-gcj <none> 2.0b4-12build1
2012-08-24 01:10:23 install libjaxp1.3-java <none> 1.3.05-2ubuntu2
2012-08-24 01:10:23 install libxalan2-java <none> 2.7.1-7
2012-08-24 01:10:24 install libapache-pom-java <none> 10-2
2012-08-24 01:10:24 install libbsf-java <none> 1:2.4.0-5
2012-08-24 01:10:25 install libavalon-framework-java <none> 4.2.0-8
2012-08-24 01:10:25 install libcommons-io-java <none> 1.4-4
2012-08-24 01:10:26 install libcommons-parent-java <none> 22-2
2012-08-24 01:10:26 install libcommons-logging-java <none> 1.1.1-9
2012-08-24 01:10:27 install java-wrappers <none> 0.1.24
2012-08-24 01:10:27 install libbatik-java <none> 1.7.ubuntu-8ubuntu1
2012-08-24 01:10:28 install libxmlgraphics-commons-java <none> 1.4.dfsg-4ubuntu1
2012-08-24 01:10:29 install libfop-java <none> 1:1.0.dfsg2-6
2012-08-24 01:10:29 install fop <none> 1:1.0.dfsg2-6
2012-08-24 01:10:30 install gcj-4.6-jre-lib <none> 4.6.3-1ubuntu2
2012-08-24 01:10:31 install glassfish-javaee <none> 1:2.1.1-b31g-1
2012-08-24 01:10:31 install junit <none> 3.8.2-8
2012-08-24 01:10:32 install libhamcrest-java <none> 1.1-8
2012-08-24 01:10:32 install junit4 <none> 4.8.2-2
2012-08-24 01:10:33 install libnetty-java <none> 1:3.2.6.Final-2
2012-08-24 01:10:33 install libslf4j-java <none> 1.6.4-1
2012-08-24 01:10:34 install libasync-http-client-java <none> 1.6.5-1
2012-08-24 01:10:34 install libplexus-classworlds2-java <none> 2.4-1
2012-08-24 01:10:34 install libasm3-java <none> 3.3.2-1
2012-08-24 01:10:35 install libcommons-lang-java <none> 2.6-3ubuntu1
2012-08-24 01:10:35 install libcommons-cli-java <none> 1.2-3
2012-08-24 01:10:36 install libjsr305-java <none> 0.1~+svn49-4
2012-08-24 01:10:36 install libgoogle-collections-java <none> 1.0-2
2012-08-24 01:10:37 install libjaxen-java <none> 1.1.3-1
2012-08-24 01:10:37 install libjdom1-java <none> 1.1.2+dfsg-2
2012-08-24 01:10:37 install libcommons-beanutils-java <none> 1.8.3-2
2012-08-24 01:10:38 install libcommons-collections-java <none> 2.1.1-10
2012-08-24 01:10:38 install libcommons-digester-java <none> 1.8.1-3
2012-08-24 01:10:39 install libcommons-validator-java <none> 1:1.3.1-8
2012-08-24 01:10:39 install libcommons-collections3-java <none> 3.2.1-5
2012-08-24 01:10:40 install libservlet2.5-java <none> 6.0.35-1ubuntu3
2012-08-24 01:10:40 install libcommons-configuration-java <none> 1.7-1
2012-08-24 01:10:41 install libcommons-codec-java <none> 1.5-1
2012-08-24 01:10:41 install libhttpcore-java <none> 4.1.4-1
2012-08-24 01:10:42 install libhttpclient-java <none> 4.1.1-1
2012-08-24 01:10:42 install libitext1-java <none> 1.4-5
2012-08-24 01:10:43 install liblog4j1.2-java <none> 1.2.16-3ubuntu1
2012-08-24 01:10:43 install libplexus-interpolation-java <none> 1.11-3
2012-08-24 01:10:45 install libplexus-utils-java <none> 1:1.5.15-4
2012-08-24 01:10:45 install libclassworlds-java <none> 1.1-final-5
2012-08-24 01:10:46 install libplexus-container-default-java <none> 1.0-alpha-9-stable-1-6
2012-08-24 01:10:46 install libplexus-classworlds-java <none> 1.5.0-3
2012-08-24 01:10:47 install libxbean-java <none> 3.7-4
2012-08-24 01:10:47 install libplexus-containers-java <none> 1.0~beta3.0.7-5
2012-08-24 01:10:48 install libplexus-i18n-java <none> 1.0-beta-10-3
2012-08-24 01:10:48 install libdoxia-java <none> 1.1.4-1ubuntu3
2012-08-24 01:10:48 install libexcalibur-logkit-java <none> 2.0-9
2012-08-24 01:10:49 install libantlr-java <none> 2.7.7+dfsg-3
2012-08-24 01:10:49 install libwerken.xpath-java <none> 0.9.4-14
2012-08-24 01:10:50 install velocity <none> 1.7-4
2012-08-24 01:10:50 install libplexus-velocity-java <none> 1.1.7-5
2012-08-24 01:10:51 install libdoxia-sitetools-java <none> 1.1.4-1ubuntu1
2012-08-24 01:10:51 install libplexus-build-api-java <none> 0.0.4-4
2012-08-24 01:10:52 install libmodello-java <none> 1.1-2
2012-08-24 01:10:52 install libplexus-io-java <none> 1.0~alpha5-2
2012-08-24 01:10:52 install libplexus-archiver-java <none> 1.0~alpha12-3
2012-08-24 01:10:53 install libplexus-cipher-java <none> 1.5-2
2012-08-24 01:10:53 install libplexus-sec-dispatcher-java <none> 1.3.1-5
2012-08-24 01:10:54 install libplexus-ant-factory-java <none> 1.0~alpha2.1-3
2012-08-24 01:10:54 install libplexus-bsh-factory-java <none> 1.0~alpha7-3
2012-08-24 01:10:55 install libplexus-interactivity-api-java <none> 1.0-alpha-6-6
2012-08-24 01:10:55 install libcommons-httpclient-java <none> 3.1-10
2012-08-24 01:10:56 install libcommons-net2-java <none> 2.2-1ubuntu1
2012-08-24 01:10:56 install libeasymock-java <none> 2.4+ds1-6
2012-08-24 01:10:57 install libjetty-java <none> 6.1.24-6ubuntu0.12.04.1
2012-08-24 01:10:57 install libjsch-java <none> 0.1.42-2fakesync1
2012-08-24 01:10:57 install libjsoup-java <none> 1.6.1-2
2012-08-24 01:10:58 install libganymed-ssh2-java <none> 250-2
2012-08-24 01:10:58 install libnetbeans-cvsclient-java <none> 6.5-2
2012-08-24 01:10:59 install libregexp-java <none> 1.5-3
2012-08-24 01:10:59 install libmaven-scm-java <none> 1.3-4
2012-08-24 01:11:00 install libwagon-java <none> 1.0.0-2ubuntu2
2012-08-24 01:11:00 install libbackport-util-concurrent-java <none> 3.1-3
2012-08-24 01:11:01 install libmaven2-core-java <none> 2.2.1-8
2012-08-24 01:11:01 install libmaven-reporting-impl-java <none> 2.1-1
2012-08-24 01:11:02 install libqdox-java <none> 1.12-1
2012-08-24 01:11:02 install libjtidy-java <none> 7+svn20110807-3
2012-08-24 01:11:03 install libmaven-plugin-tools-java <none> 2.8-2
2012-08-24 01:11:03 install libplexus-cli-java <none> 1.2-3
2012-08-24 01:11:03 install libplexus-utils2-java <none> 2.0.5-1
2012-08-24 01:11:04 install libplexus-containers1.5-java <none> 1.5.5-2
2012-08-24 01:11:04 install libaopalliance-java <none> 20070526-5
2012-08-24 01:11:05 install libatinject-jsr330-api-java <none> 1.0-2
2012-08-24 01:11:05 install libgeronimo-interceptor-3.0-spec-java <none> 1.0.1-1fakesync1
2012-08-24 01:11:06 install libcdi-api-java <none> 1.0-1
2012-08-24 01:11:06 install libguava-java <none> 09-2
2012-08-24 01:11:06 install libservlet2.4-java <none> 5.5.33-1
2012-08-24 01:11:07 install libsisu-guice-java <none> 3.1.0-1
2012-08-24 01:11:07 install libsisu-ioc-java <none> 2.3.0-3
2012-08-24 01:11:08 install libaether-java <none> 1.13.1-2
2012-08-24 01:11:08 install libcglib-java <none> 2.2.2+dfsg-1
2012-08-24 01:11:09 install libcommons-jexl-java <none> 1.1-3
2012-08-24 01:11:09 install libcommons-jxpath-java <none> 1.3-5
2012-08-24 01:11:10 install libcommons-vfs-java <none> 2.0-1ubuntu1
2012-08-24 01:11:10 install libjaxme-java <none> 0.5.2+dfsg-6
2012-08-24 01:11:11 install libxpp2-java <none> 2.1.10-7
2012-08-24 01:11:11 install libxpp3-java <none> 1.1.4c-2
2012-08-24 01:11:12 install libdom4j-java <none> 1.6.1+dfsg.2-5
2012-08-24 01:11:13 install libosgi-core-java <none> 4.3.0-1
2012-08-24 01:11:13 install libosgi-foundation-ee-java <none> 4.2.0-1
2012-08-24 01:11:14 install libosgi-compendium-java <none> 4.3.0-1
2012-08-24 01:11:15 install libgeronimo-osgi-support-java <none> 1.0-2
2012-08-24 01:11:15 install libgeronimo-jpa-2.0-spec-java <none> 1.1-2
2012-08-24 01:11:16 install liboro-java <none> 2.0.8a-8
2012-08-24 01:11:16 install librhino-java <none> 1.7R3-5
2012-08-24 01:11:16 install libsaxon-java <none> 1:6.5.5-8
2012-08-24 01:11:17 install libxom-java <none> 1.2.1-3
2012-08-24 01:11:17 install openjdk-6-jre <none> 6b24-1.11.3-1ubuntu0.12.04.1
2012-08-24 01:11:19 install maven <none> 3.0.4-2
2012-08-24 01:11:19 install rhino <none> 1.7R3-5
2012-08-24 01:11:20 install icedtea-6-jre-cacao <none> 6b24-1.11.3-1ubuntu0.12.04.1
2012-08-24 01:11:20 install icedtea-6-jre-jamvm <none> 6b24-1.11.3-1ubuntu0.12.04.1
2012-08-24 01:11:21 install icedtea-netx-common <none> 1.2-2ubuntu1.1
2012-08-24 01:11:22 install icedtea-netx <none> 1.2-2ubuntu1.1
2012-08-24 12:02:03 install jdownloader <none> 0.3-0jd2~precise
2012-08-24 16:14:07 install libjmol-java-doc <none> 12.2.2+dfsg-1
2012-08-25 10:12:25 install gsfonts-x11 <none> 0.22
2012-08-25 11:55:08 install libunistring0 <none> 0.9.3-5
2012-08-25 11:55:09 install libgettextpo0 <none> 0.18.1.1-5ubuntu3
2012-08-25 11:55:09 install libtimedate-perl <none> 1.2000-1
2012-08-25 11:55:10 install libdpkg-perl <none> 1.16.1.2ubuntu7
2012-08-25 11:55:11 install dpkg-dev <none> 1.16.1.2ubuntu7
2012-08-25 11:55:11 install html2text <none> 1.3.2a-15
2012-08-25 11:55:12 install gettext <none> 0.18.1.1-5ubuntu3
2012-08-25 11:55:13 install intltool-debian <none> 0.35.0+20060710.1
2012-08-25 11:55:13 install po-debconf <none> 1.0.16+nmu2ubuntu1
2012-08-25 11:55:14 install dh-apparmor <none> 2.7.102-0ubuntu3.1
2012-08-25 11:55:15 install debhelper <none> 9.20120115ubuntu3
2012-08-25 11:55:16 install librpmio2 <none> 4.9.1.1-1build1
2012-08-25 11:55:16 install rpm-common <none> 4.9.1.1-1build1
2012-08-25 11:55:17 install librpm2 <none> 4.9.1.1-1build1
2012-08-25 11:55:18 install librpmbuild2 <none> 4.9.1.1-1build1
2012-08-25 11:55:18 install librpmsign0 <none> 4.9.1.1-1build1
2012-08-25 11:55:19 install rpm2cpio <none> 4.9.1.1-1build1
2012-08-25 11:55:19 install rpm <none> 4.9.1.1-1build1
2012-08-25 11:55:20 install alien <none> 8.86
2012-08-25 11:55:20 install libstdc++6-4.6-dev <none> 4.6.3-1ubuntu5
2012-08-25 11:55:21 install g++-4.6 <none> 4.6.3-1ubuntu5
2012-08-25 11:55:22 install g++ <none> 4:4.6.3-1ubuntu5
2012-08-25 11:55:23 install build-essential <none> 11.5ubuntu2
2012-08-25 11:55:23 install libalgorithm-diff-perl <none> 1.19.02-2
2012-08-25 11:55:24 install libalgorithm-diff-xs-perl <none> 0.04-2build2
2012-08-25 11:55:24 install libalgorithm-merge-perl <none> 0.08-2
2012-08-25 11:55:25 install libsys-hostname-long-perl <none> 1.4-2
2012-08-25 11:55:25 install libmail-sendmail-perl <none> 0.79.16-1
2012-08-25 12:04:57 install jdk <none> 1.7.006-1
2012-08-25 12:07:56 install jre <none> 1.7.0-1
2012-08-25 13:47:35 install jre <none> 1.7.0-1
2012-08-25 13:50:50 install jre <none> 1.7.0-1
2012-08-25 13:51:06 install jdk 1.7.006-1 1.7.006-1
2012-08-25 13:52:34 install jdk 1.7.006-1 1.7.006-1
2012-08-25 13:56:05 install jdk 1.7.006-1 1.7.006-1
2012-08-25 13:57:55 install jdk 1.7.006-1 1.7.006-1
2012-08-25 14:02:12 install oracle-java7-installer <none> 7u6-0~webupd8~0
2012-08-26 14:41:14 install libgtkmm-2.4-1c2a <none> 1:2.24.2-1ubuntu1
2012-08-26 14:41:15 install gparted <none> 0.11.0-2
2012-08-26 17:03:38 install python3.2-minimal <none> 3.2.3-0ubuntu3
2012-08-26 17:03:39 install python3.2 <none> 3.2.3-0ubuntu3
2012-08-26 17:03:40 install python3-minimal <none> 3.2.3-0ubuntu1
2012-08-26 17:03:41 install python3 <none> 3.2.3-0ubuntu1
2012-08-26 18:12:59 install liblqr-1-0 <none> 0.4.1-1.1
2012-08-26 18:13:00 install imagemagick-common <none> 8:6.6.9.7-5ubuntu3.2
2012-08-26 18:13:01 install libmagickcore4 <none> 8:6.6.9.7-5ubuntu3.2
2012-08-26 18:13:01 install libmagickwand4 <none> 8:6.6.9.7-5ubuntu3.2
2012-08-26 18:13:02 install imagemagick <none> 8:6.6.9.7-5ubuntu3.2
2012-08-26 18:13:03 install libcdt4 <none> 2.26.3-10ubuntu1
2012-08-26 18:13:03 install libcommon-sense-perl <none> 3.4-1
2012-08-26 18:13:04 install libencode-locale-perl <none> 1.02-2
2012-08-26 18:13:05 install libextutils-depends-perl <none> 0.304-1
2012-08-26 18:13:06 install libextutils-pkgconfig-perl <none> 1.12-1
2012-08-26 18:13:06 install libhttp-date-perl <none> 6.00-1
2012-08-26 18:13:07 install libfile-listing-perl <none> 6.03-1
2012-08-26 18:13:07 install libfile-which-perl <none> 1.08-1
2012-08-26 18:13:08 install libfont-afm-perl <none> 1.20-1
2012-08-26 18:13:08 install libgnome2-canvas-perl <none> 1.002-2build3
2012-08-26 18:13:09 install libgnome2-gconf-perl <none> 1.044-4
2012-08-26 18:13:09 install libgnome2-vfs-perl <none> 1.081-3build1
2012-08-26 18:13:10 install libgnome2-perl <none> 1.042-2build3
2012-08-26 18:13:11 install libgnome2-wnck-perl <none> 0.16-2build2
2012-08-26 18:13:11 install libgnomevfs2-extra <none> 1:2.24.4-1ubuntu2
2012-08-26 18:13:12 install libgoocanvas-common <none> 0.15-1
2012-08-26 18:13:12 install libgoocanvas3 <none> 0.15-1
2012-08-26 18:13:13 install libgoo-canvas-perl <none> 0.06-1build2
2012-08-26 18:13:13 install libgraph4 <none> 2.26.3-10ubuntu1
2012-08-26 18:13:14 install libgtkimageview0 <none> 1.6.4-1
2012-08-26 18:13:14 install libgtk2-imageview-perl <none> 0.05-1build2
2012-08-26 18:13:15 install libunique-1.0-0 <none> 1.1.6-4
2012-08-26 18:13:16 install libgtk2-unique-perl <none> 0.05-1build2
2012-08-26 18:13:16 install libpathplan4 <none> 2.26.3-10ubuntu1
2012-08-26 18:13:17 install libgvc5 <none> 2.26.3-10ubuntu1
2012-08-26 18:13:17 install liburi-perl <none> 1.59-1
2012-08-26 18:13:18 install libhtml-tagset-perl <none> 3.20-2
2012-08-26 18:13:18 install libhtml-parser-perl <none> 3.69-1build1
2012-08-26 18:13:19 install liblwp-mediatypes-perl <none> 6.01-1
2012-08-26 18:13:19 install libhttp-message-perl <none> 6.01-1
2012-08-26 18:13:20 install libhtml-form-perl <none> 6.00-1
2012-08-26 18:13:20 install libhtml-tree-perl <none> 4.2-1
2012-08-26 18:13:21 install libhtml-format-perl <none> 2.10-1
2012-08-26 18:13:22 install libhttp-cookies-perl <none> 6.00-2
2012-08-26 18:13:22 install libhttp-daemon-perl <none> 6.00-1
2012-08-26 18:13:22 install libhttp-negotiate-perl <none> 6.00-2
2012-08-26 18:13:23 install libhttp-server-simple-perl <none> 0.44-1
2012-08-26 18:13:24 install libilmbase6 <none> 1.0.1-3build2
2012-08-26 18:13:24 install libsocket6-perl <none> 0.23-1build2
2012-08-26 18:13:25 install libio-socket-inet6-perl <none> 2.69-2
2012-08-26 18:13:25 install libnet-ssleay-perl <none> 1.42-1build1
2012-08-26 18:13:26 install libio-socket-ssl-perl <none> 1.53-1
2012-08-26 18:13:26 install libjson-perl <none> 2.53-1
2012-08-26 18:13:27 install libjson-xs-perl <none> 2.320-1build1
2012-08-26 18:13:27 install libnet-http-perl <none> 6.02-1
2012-08-26 18:13:28 install libwww-robotrules-perl <none> 6.01-1
2012-08-26 18:13:28 install libwww-perl <none> 6.03-1
2012-08-26 18:13:29 install liblwp-protocol-https-perl <none> 6.02-1
2012-08-26 18:13:29 install libopenexr6 <none> 1.6.1-4.1
2012-08-26 18:13:30 install libmagickcore4-extra <none> 8:6.6.9.7-5ubuntu3.2
2012-08-26 18:13:30 install libmailtools-perl <none> 2.08-1
2012-08-26 18:13:31 install libxml-parser-perl <none> 2.41-1build1
2012-08-26 18:13:32 install libxml-twig-perl <none> 1:3.39-1ubuntu1
2012-08-26 18:13:32 install libnet-dbus-perl <none> 1.0.0-1build1
2012-08-26 18:13:33 install libnetpbm10 <none> 2:10.0-15
2012-08-26 18:13:34 install libpath-class-perl <none> 0.24-1
2012-08-26 18:13:34 install libproc-processtable-perl <none> 0.45-3
2012-08-26 18:13:35 install libproc-simple-perl <none> 1.30-1
2012-08-26 18:13:35 install libsort-naturally-perl <none> 1.02-1
2012-08-26 18:13:36 install libtie-ixhash-perl <none> 1.21-2
2012-08-26 18:13:36 install libwww-mechanize-perl <none> 1.71-1
2012-08-26 18:13:37 install libx11-protocol-perl <none> 0.56-2
2012-08-26 18:13:38 install libxml-namespacesupport-perl <none> 1.09-3
2012-08-26 18:13:38 install libxml-sax-base-perl <none> 1.07-1
2012-08-26 18:13:39 install libxml-sax-perl <none> 0.99+dfsg-1ubuntu0.1
2012-08-26 18:13:40 install libxml-sax-expat-perl <none> 0.40-2
2012-08-26 18:13:41 install libxml-simple-perl <none> 2.18-3
2012-08-26 18:13:41 install libxml-xpath-perl <none> 1.13-7
2012-08-26 18:13:42 install netpbm <none> 2:10.0-15
2012-08-26 18:13:43 install perlmagick <none> 8:6.6.9.7-5ubuntu3.2
2012-08-26 18:13:43 install shutter <none> 0.88.1-1
```lspci lists the device as:

**02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)**

See full output below.

```
ndb@ndb-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
16:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
16:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
16:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
16:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```[B]

UPDATE[/B]

After a reboot the multimedia keys are working again, but pressing the wireless adapter enable/disable key combos I described earlier does nothing sadly.

Any suggestions would be much appreciated at this point!

---

### Post by KomodoDave on 2012-08-27
Resolved, see my post here:

[http://ubuntuforums.org/showthread.php?p=12199567#post12199567](http://ubuntuforums.org/showthread.php?p=12199567#post12199567)

---

