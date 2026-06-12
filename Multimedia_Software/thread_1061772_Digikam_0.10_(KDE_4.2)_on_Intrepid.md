---
title: "Digikam 0.10 (KDE 4.2) on Intrepid"
date: 2009-02-06
forum: Multimedia Software
---

### Post by putt1ck on 2009-02-06
If using KDE 4.2 with Digikam 0.10 (or just wanting to try the latest and greatest in photo management applications) here's some gotchas and the fixes.

First Digikam 0.10 and KDE 4.2 are interdependent i.e. you need both. Old Digikam won't work with key parts of KDE 4.2 and gets removed if you install those parts. New Digikam needs KDE 4.2 libraries to work. 

So you need two PPA respositories adding:

[https://launchpad.net/~kubuntu-experimental/+archive/ppa](https://launchpad.net/~kubuntu-experimental/+archive/ppa)

[https://launchpad.net/~digikam-experimental/+archive/ppa](https://launchpad.net/~digikam-experimental/+archive/ppa)

The first adds KDE 4.2 libraries and the second Digikam 4.2 and the Kipi-plugins it needs.

Note for smooth upgrading it is recommended you tick all the "upgrade" options types in your package manager (in Adept do Sources/Edit Software Sources/Updates and tick all the Kubuntu updates options).

Next note that the digikam3.db database file will be imported into the new digikam4.db file created when the new Digikam fires up the first time. This is a bad thing as the resultant database won't display any of your images... Rename the digikam3.db digikam3.old (or similar) before starting the new Digikam. If you've already been got with this invisible images trick, close Digikam, do the rename, delete the digikam4.db and restart.

But is worth it. Show me a better photo manager...

---

### Post by Nicram on 2009-02-25
Sorry, but it didn't work for me.
I have this message just after start.
Any ideas?
 
```
Program: digiKam (digikam), signal SIGSEGV
 [Current thread is 0 (LWP 24192)]
 
 Thread 2 (Thread 0xb3204b90 (LWP 24193)):
 [KCrash Handler]
 #5  0x00000000 in ?? ()
 #6  0xb527abe0 in Exiv2::ExifTags::tagList () from /usr/lib/libexiv2.so.4
 #7  0xb527ac12 in Exiv2::ExifTags::tagInfo () from /usr/lib/libexiv2.so.4
 #8  0xb5282cf5 in Exiv2::ExifTags::tagName () from /usr/lib/libexiv2.so.4
 #9  0xb5283347 in Exiv2::ExifKey::makeKey () from /usr/lib/libexiv2.so.4
 #10 0xb528391d in Exiv2::ExifKey::ExifKey () from /usr/lib/libexiv2.so.4
 #11 0xb5290b5c in Exiv2::TiffMetadataDecoder::decodeStdTiffEntry () from /usr/lib/libexiv2.so.4
 #12 0xb528d711 in Exiv2::TiffMetadataDecoder::decodeTiffEntry () from /usr/lib/libexiv2.so.4
 #13 0xb528d934 in Exiv2::TiffMetadataDecoder::visitEntry () from /usr/lib/libexiv2.so.4
 #14 0xb5287ec8 in Exiv2::TiffEntry::doAccept () from /usr/lib/libexiv2.so.4
 #15 0xb5287ea7 in Exiv2::TiffComponent::accept () from /usr/lib/libexiv2.so.4
 #16 0xb5287f5e in Exiv2::TiffDirectory::doAccept () from /usr/lib/libexiv2.so.4
 #17 0xb5287ea7 in Exiv2::TiffComponent::accept () from /usr/lib/libexiv2.so.4
 #18 0xb5288006 in Exiv2::TiffSubIfd::doAccept () from /usr/lib/libexiv2.so.4
 #19 0xb5287ea7 in Exiv2::TiffComponent::accept () from /usr/lib/libexiv2.so.4
 #20 0xb5287f5e in Exiv2::TiffDirectory::doAccept () from /usr/lib/libexiv2.so.4
 #21 0xb5287ea7 in Exiv2::TiffComponent::accept () from /usr/lib/libexiv2.so.4
 #22 0xb528bfa9 in Exiv2::TiffParser::decode () from /usr/lib/libexiv2.so.4
 #23 0xb528a7d6 in Exiv2::TiffImage::readMetadata () from /usr/lib/libexiv2.so.4
 #24 0xb784a67f in KExiv2Iface::KExiv2::load () from /usr/lib/libkexiv2.so.7
 #25 0xb71deb1c in Digikam::DMetadata::load (this=0xb3203e1c, filePath=@0xb3203da8) at /build/buildd/digikam-0.10.0~rc2/libs/dmetadata/dmetadata.cpp:75
 #26 0xb7054041 in Digikam::ImageScanner::loadFromDisk (this=0xb3203e14) at /build/buildd/digikam-0.10.0~rc2/libs/database/imagescanner.cpp:601
 #27 0xb705b232 in Digikam::ImageScanner::newFile (this=0xb3203e14, albumId=3) at /build/buildd/digikam-0.10.0~rc2/libs/database/imagescanner.cpp:89
 #28 0xb704d1da in Digikam::CollectionScanner::scanNewFile (this=0xb3204354, info=@0x90b4274, albumId=3) at /build/buildd/digikam-0.10.0~rc2/libs/database/collectionscanner.cpp:592
 #29 0xb704e76f in Digikam::CollectionScanner::scanAlbum (this=0xb3204354, location=@0x902f9b8, album=@0xb32040b4) at /build/buildd/digikam-0.10.0~rc2/libs/database/collectionscanner.cpp:545
 #30 0xb704e678 in Digikam::CollectionScanner::scanAlbum (this=0xb3204354, location=@0x902f9b8, album=@0xb3204204) at /build/buildd/digikam-0.10.0~rc2/libs/database/collectionscanner.cpp:556
 #31 0xb704e678 in Digikam::CollectionScanner::scanAlbum (this=0xb3204354, location=@0x902f9b8, album=@0xb3204284) at /build/buildd/digikam-0.10.0~rc2/libs/database/collectionscanner.cpp:556
 #32 0xb704f1d7 in Digikam::CollectionScanner::scanAlbumRoot (this=0xb3204354, location=@0x902f9b8) at /build/buildd/digikam-0.10.0~rc2/libs/database/collectionscanner.cpp:345
 #33 0xb704f47e in Digikam::CollectionScanner::completeScan (this=0xb3204354) at /build/buildd/digikam-0.10.0~rc2/libs/database/collectionscanner.cpp:192
 #34 0x0828f397 in Digikam::ScanController::run (this=0x8fa6450) at /build/buildd/digikam-0.10.0~rc2/digikam/scancontroller.cpp:432
 #35 0xb58896ae in ?? () from /usr/lib/libQtCore.so.4
 #36 0xb559e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
 #37 0xb5693a0e in clone () from /lib/tls/i686/cmov/libc.so.6
 
 Thread 1 (Thread 0xb48a16c0 (LWP 24192)):
 #0  0xb802d430 in __kernel_vsyscall ()
 #1  0xb55a2075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
 #2  0xb56a1bbd in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
 #3  0xb588a6f2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
 #4  0xb5889853 in QThread::wait () from /usr/lib/libQtCore.so.4
 #5  0x0828f65e in Digikam::ScanController::shutDown (this=0x8fa6450) at /build/buildd/digikam-0.10.0~rc2/digikam/scancontroller.cpp:264
 #6  0x08292511 in ~ScanController (this=0x8fa6450) at /build/buildd/digikam-0.10.0~rc2/digikam/scancontroller.cpp:247
 #7  0x082926ba in destroy () at /build/buildd/digikam-0.10.0~rc2/digikam/scancontroller.cpp:188
 #8  0xb55e0d89 in exit () from /lib/tls/i686/cmov/libc.so.6
 #9  0xb5e8cd2b in ?? () from /usr/lib/libQtGui.so.4
 #10 0xb694599a in KApplication::xioErrhandler (this=0xbfd2eda4, dpy=0x8e8e9b8) at /build/buildd/kde4libs-4.2.0/kdeui/kernel/kapplication.cpp:413
 #11 0xb69459d6 in kde_xio_errhandler (dpy=0x8e8e9b8) at /build/buildd/kde4libs-4.2.0/kdeui/kernel/kapplication.cpp:130
 #12 0xb542e062 in _XIOError () from /usr/lib/libX11.so.6
 #13 0xb5436135 in ?? () from /usr/lib/libX11.so.6
 #14 0xb5436985 in _XEventsQueued () from /usr/lib/libX11.so.6
 #15 0xb541e90f in XEventsQueued () from /usr/lib/libX11.so.6
 #16 0xb5ec706d in ?? () from /usr/lib/libQtGui.so.4
 #17 0xb4d34308 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
 #18 0xb4d34c8d in ?? () from /usr/lib/libglib-2.0.so.0
 #19 0xb4d34f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
 #20 0xb59a4497 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
 #21 0xb5ec6ea5 in ?? () from /usr/lib/libQtGui.so.4
 #22 0xb597852a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
 #23 0xb59786ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
 #24 0x0828f0e3 in Digikam::ScanController::completeCollectionScan (this=0x8fa6450, splash=0x0) at /build/buildd/digikam-0.10.0~rc2/digikam/scancontroller.cpp:326
 #25 0x082527aa in DigikamApp (this=0x9045900) at /build/buildd/digikam-0.10.0~rc2/digikam/digikamapp.cpp:164
 #26 0x082b4aa4 in main (argc=4, argv=0xbfd2f004) at /build/buildd/digikam-0.10.0~rc2/digikam/main.cpp:167
```

---

