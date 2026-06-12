---
title: "Ktorrent Signal:11  Ubuntu ver 9.04"
date: 2009-12-12
forum: Minnesota Team - US
---

### Post by n97ua on 2009-12-12
I loaded Ktorrent on the new version of Ubuntu 9.04 and I keep getting this error when running Ktorrent.

Has anyuone seen this, or know where to start debugging it.

Executable: ktorrent PID: 7806 Signal: 11 (Segmentation fault)

Got plenty of RAM som I know its not that...  So far everything works except Ktorrent and its a bit anoying...  My guess is someone out there has seen this and knows what it is.

Here is a dump of KTorrent :

Application: KTorrent (ktorrent), signal: Segmentation fault
[Current thread is 1 (Thread 0xb77a3700 (LWP 7806))]

Thread 3 (Thread 0xb4dfeb70 (LWP 7815)):
#0  0x0032e422 in __kernel_vsyscall ()
#1  0x068b9e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x050dc78d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0x00de44d2 in ?? () from /usr/lib/libQtCore.so.4
#4  0x00ddfba2 in QMutex::lock() () from /usr/lib/libQtCore.so.4
#5  0x0064a356 in ?? () from /usr/lib/libbtcore.so.11
#6  0x00636047 in mse::StreamSocket::onDataReady(unsigned char*, unsigned int) () from /usr/lib/libbtcore.so.11
#7  0x0062cbc8 in ?? () from /usr/lib/libbtcore.so.11
#8  0x00632e97 in ?? () from /usr/lib/libbtcore.so.11
#9  0x006330e3 in ?? () from /usr/lib/libbtcore.so.11
#10 0x006332be in ?? () from /usr/lib/libbtcore.so.11
#11 0x00630e22 in ?? () from /usr/lib/libbtcore.so.11
#12 0x00631ab5 in ?? () from /usr/lib/libbtcore.so.11
#13 0x00631531 in ?? () from /usr/lib/libbtcore.so.11
#14 0x00631d38 in ?? () from /usr/lib/libbtcore.so.11
#15 0x00de4e32 in ?? () from /usr/lib/libQtCore.so.4
#16 0x068b580e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#17 0x050cf7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb45fdb70 (LWP 7816)):
#0  0x0032e422 in __kernel_vsyscall ()
#1  0x068b9e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x050dc78d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0x00de44d2 in ?? () from /usr/lib/libQtCore.so.4
#4  0x00ddfb82 in QMutex::lock() () from /usr/lib/libQtCore.so.4
#5  0x0062f6c0 in net::SocketMonitor::lock() () from /usr/lib/libbtcore.so.11
#6  0x00630922 in ?? () from /usr/lib/libbtcore.so.11
#7  0x00631d38 in ?? () from /usr/lib/libbtcore.so.11
#8  0x00de4e32 in ?? () from /usr/lib/libQtCore.so.4
#9  0x068b580e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0x050cf7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb77a3700 (LWP 7806)):
[KCrash Handler]
#6  0x05078006 in memcpy () from /lib/tls/i686/cmov/libc.so.6
#7  0xbfdf125c in ?? ()
#8  0x0757a7bb in QCA::Hash::update(char const*, int) () from /usr/lib/libqca.so.2
#9  0x0061c594 in bt::SHA1HashGen::update(unsigned char const*, unsigned int) () from /usr/lib/libbtcore.so.11
#10 0x00651eb8 in ?? () from /usr/lib/libbtcore.so.11
#11 0x00652d30 in ?? () from /usr/lib/libbtcore.so.11
#12 0x006598ff in bt::Downloader::pieceReceived(bt::Piece const&) () from /usr/lib/libbtcore.so.11
#13 0x00641b0f in bt::PeerManager::pieceReceived(bt::Piece const&) () from /usr/lib/libbtcore.so.11
#14 0x0064049f in ?? () from /usr/lib/libbtcore.so.11
#15 0x00649f16 in ?? () from /usr/lib/libbtcore.so.11
#16 0x006401d9 in ?? () from /usr/lib/libbtcore.so.11
#17 0x00643f0e in bt::PeerManager::update() () from /usr/lib/libbtcore.so.11
#18 0x006793be in bt::TorrentControl::update() () from /usr/lib/libbtcore.so.11
#19 0x0806d1e7 in _start ()

Not sure what can be causing this.

---

### Post by katakaio on 2009-12-22
Have you tried posting this in the General Help section? This section of the forum is usually frequented only by members of the Minnesota LoCo.

I can't decrypt that dump, but I am curious why you're using KTorrent (which depends on a lot of KDE code found in Kubuntu) on Ubuntu (where something like Transmission or Deluge plays nicer).

---

