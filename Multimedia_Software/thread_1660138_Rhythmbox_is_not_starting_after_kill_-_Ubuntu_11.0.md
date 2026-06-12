---
title: "Rhythmbox is not starting after kill - Ubuntu 11.04"
date: 2011-01-05
forum: Multimedia Software
---

### Post by shayzu on 2011-01-05
Hi

As Rhythmbox got stuck while it played a "radio station", I had to kill it using "kill" applet from the panel
Since then, any attempt to start it fails.

Looking at the "Volume" applet on the panel, we can see that Rhythmbox is still playing.
On the other hand, on "Applications" tab of sound preferences, it does not exist.

Any other sound program, like VLC works just fine.

When executing it from command line under strace, its execution ends with:
13724 uname({sys="Linux", node="shay", ...}) = 0
13724 open("/home/shay/.Xdefaults-shay", O_RDONLY) = -1 ENOENT (No such file or directory)
13724 access("MARK:     [main.c main 160] END parsing command line options", F_OK) = -1 ENOENT (No such file or directory)
13724 time(NULL)                        = 1294206503
13724 gettimeofday({1294206503, 570329}, NULL) = 0
13724 clock_getres(CLOCK_MONOTONIC, {0, 1}) = 0
13724 socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC, 0) = 7
13724 connect(7, {sa_family=AF_FILE, path=@"/tmp/dbus-sDBjJROwTv"}, 23) = 0
13724 fcntl64(7, F_GETFL)               = 0x2 (flags O_RDWR)
13724 fcntl64(7, F_SETFL, O_RDWR|O_NONBLOCK) = 0
13724 geteuid32()                       = 500
13724 getsockname(7, {sa_family=AF_FILE, NULL}, [2]) = 0
13724 poll([{fd=7, events=POLLOUT}], 1, 0) = 1 ([{fd=7, revents=POLLOUT}])
13724 write(7, "\0", 1)                 = 1
13724 send(7, "AUTH EXTERNAL 353030\r\n", 22, MSG_NOSIGNAL) = 22
13724 poll([{fd=7, events=POLLIN}], 1, -1) = 1 ([{fd=7, revents=POLLIN}])
13724 read(7, "OK d5bae1f009a75e9c954f0ec20000002f\r\n", 2048) = 37
13724 poll([{fd=7, events=POLLOUT}], 1, -1) = 1 ([{fd=7, revents=POLLOUT}])
13724 send(7, "NEGOTIATE_UNIX_FD\r\n", 19, MSG_NOSIGNAL) = 19
13724 poll([{fd=7, events=POLLIN}], 1, -1) = 1 ([{fd=7, revents=POLLIN}])
13724 read(7, "AGREE_UNIX_FD\r\n", 2048) = 15
13724 poll([{fd=7, events=POLLOUT}], 1, -1) = 1 ([{fd=7, revents=POLLOUT}])
13724 send(7, "BEGIN\r\n", 7, MSG_NOSIGNAL) = 7
13724 poll([{fd=7, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=7, revents=POLLOUT}])
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\0\0\0\0\1\0\0\0n\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 128}, {"", 0}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 128
13724 clock_gettime(CLOCK_MONOTONIC, {516017, 786409769}) = 0
13724 poll([{fd=7, events=POLLIN}], 1, 25000) = 1 ([{fd=7, revents=POLLIN}])
13724 recvmsg(7, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1\f\0\0\0\1\0\0\0=\0\0\0\6\1s\0\7\0\0\0:1.1297\0\5\1u\0\1\0\0\0\10\1g\0\1s\0\0\7\1"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 264
13724 recvmsg(7, 0xbfa6dc98, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
13724 fstat64(7, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
13724 fcntl64(7, F_GETFL)               = 0x802 (flags O_RDWR|O_NONBLOCK)
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1n\0\0\0\2\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"i\0\0\0type='signal',sender='org.freedesktop.DBus',pa"..., 110}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 254
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1\244\0\0\0\3\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"\237\0\0\0type='signal',sender='org.freedesktop.DBus',pa"..., 164}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 308
13724 gettimeofday({1294206503, 577897}, NULL) = 0
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\31\0\0\0\4\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"\24\0\0\0org.freedesktop.DBus\0", 25}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 169
13724 gettimeofday({1294206503, 578110}, NULL) = 0
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\34\0\0\0\5\0\0\0\200\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"\23\0\0\0org.gnome.Rhythmbox\0\4\0\0\0", 28}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 172
13724 clock_gettime(CLOCK_MONOTONIC, {516017, 787735806}) = 0
13724 poll([{fd=7, events=POLLIN}], 1, 25000) = 1 ([{fd=7, revents=POLLIN}])
13724 recvmsg(7, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1\31\0\0\0\3\0\0\0=\0\0\0\6\1s\0\7\0\0\0:1.1297\0\5\1u\0\4\0\0\0\10\1g\0\1s\0\0\7\1"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 189
13724 recvmsg(7, 0xbfa6dc78, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1n\0\0\0\6\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"i\0\0\0type='signal',sender='org.freedesktop.DBus',pa"..., 110}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 254
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1\244\0\0\0\7\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"\237\0\0\0type='signal',sender='org.freedesktop.DBus',pa"..., 164}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 308
13724 gettimeofday({1294206503, 578920}, NULL) = 0
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\30\0\0\0\10\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"\23\0\0\0org.gnome.Rhythmbox\0", 24}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 168
13724 clock_gettime(CLOCK_MONOTONIC, {516017, 788542380}) = 0
13724 poll([{fd=7, events=POLLIN}], 1, 2000) = 1 ([{fd=7, revents=POLLIN}])
13724 recvmsg(7, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1\f\0\0\0\5\0\0\0=\0\0\0\6\1s\0\7\0\0\0:1.1297\0\5\1u\0\10\0\0\0\10\1g\0\1s\0\0\7\1"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 92
13724 recvmsg(7, 0xbfa6dd58, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1k\0\0\0\t\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"f\0\0\0type='signal',sender=':1.1057',path='/org/gnom"..., 107}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 251
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1\227\0\0\0\n\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"\222\0\0\0type='signal',sender='org.freedesktop.DBus',pa"..., 151}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 295
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1\4\0\0\0\v\0\0\0w\0\0\0\1\1o\0\32\0\0\0/org/gnome/Rhythmbox/Shell"..., 136}, {"\0\0\0\0", 4}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 140
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1k\0\0\0\f\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"f\0\0\0type='signal',sender=':1.1057',path='/org/gnom"..., 107}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 251
13724 sendmsg(7, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1\227\0\0\0\r\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/freedesktop/DBus\0\0\0\6\1"..., 144}, {"\222\0\0\0type='signal',sender='org.freedesktop.DBus',pa"..., 151}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 295
13724 socketpair(PF_FILE, SOCK_STREAM, 0, [8, 9]) = 0
13724 fcntl64(8, F_SETFL, O_RDONLY|O_NONBLOCK) = 0
13724 fcntl64(9, F_SETFL, O_RDONLY|O_NONBLOCK) = 0
13724 write(9, "W", 1)                  = 1
13724 close(9)                          = 0
13724 close(8)                          = 0
13724 gettimeofday({1294206503, 580570}, NULL) = 0
13724 gettimeofday({1294206503, 580756}, NULL) = 0
13724 gettimeofday({1294206503, 580909}, NULL) = 0
13724 gettimeofday({1294206503, 581043}, NULL) = 0
13724 gettimeofday({1294206503, 581161}, NULL) = 0
13724 gettimeofday({1294206503, 581284}, NULL) = 0
13724 gettimeofday({1294206503, 581396}, NULL) = 0
13724 gettimeofday({1294206503, 581506}, NULL) = 0
13724 gettimeofday({1294206503, 581634}, NULL) = 0
13724 gettimeofday({1294206503, 581741}, NULL) = 0
13724 gettimeofday({1294206503, 581854}, NULL) = 0
13724 gettimeofday({1294206503, 581968}, NULL) = 0
13724 gettimeofday({1294206503, 582081}, NULL) = 0
13724 gettimeofday({1294206503, 582194}, NULL) = 0
13724 gettimeofday({1294206503, 582306}, NULL) = 0
13724 gettimeofday({1294206503, 582422}, NULL) = 0
13724 gettimeofday({1294206503, 582543}, NULL) = 0
13724 gettimeofday({1294206503, 582663}, NULL) = 0
13724 gettimeofday({1294206503, 582773}, NULL) = 0
13724 gettimeofday({1294206503, 582891}, NULL) = 0
13724 gettimeofday({1294206503, 583004}, NULL) = 0
13724 gettimeofday({1294206503, 583113}, NULL) = 0
13724 gettimeofday({1294206503, 583259}, NULL) = 0
13724 gettimeofday({1294206503, 583375}, NULL) = 0
13724 gettimeofday({1294206503, 583487}, NULL) = 0
13724 gettimeofday({1294206503, 583610}, NULL) = 0
13724 gettimeofday({1294206503, 583727}, NULL) = 0
13724 gettimeofday({1294206503, 583834}, NULL) = 0
13724 gettimeofday({1294206503, 584111}, NULL) = 0
13724 gettimeofday({1294206503, 584256}, NULL) = 0
13724 gettimeofday({1294206503, 584395}, NULL) = 0
13724 gettimeofday({1294206503, 584454}, NULL) = 0
13724 gettimeofday({1294206503, 584493}, NULL) = 0
13724 access("MARK: [main.c main 356] END starting rhythmbox", F_OK) = -1 ENOENT (No such file or directory)
13724 exit_group(0)                     = ?


Any ideas, what should be done before rebooting the box?

Thanks!

Shay

---

