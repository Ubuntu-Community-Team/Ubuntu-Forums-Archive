---
title: "Dead.letter  Samba"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by mick222 on 2010-04-22
I just noticed this today should i report the bug I have messed about so much with samba recently;trying to get windows7 to connect and setting up a printer ,that i don't know if it's just me that messed things up. I don't remember it asking me about this or samba crashing yesterday. I only noticed because i opened nautilus for another reason.

> The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for PID 2393 (/usr/sbin/smbd).

This means there was a problem with the program, such as a segfault.
Below is a backtrace for this process generated with gdb, which shows
the state of the program at the time the error occurred.  The Samba log
files may contain additional information about the problem.

If the problem persists, you are encouraged to first install the
samba-dbg package, which contains the debugging symbols for the Samba
binaries.  Then submit the provided information as a bug report to
Ubuntu by visiting this link:
[https://launchpad.net/ubuntu/+source/samba/+filebug](https://launchpad.net/ubuntu/+source/samba/+filebug)

[Thread debugging using libthread_db enabled]
0x00110422 in __kernel_vsyscall ()
#0  0x00110422 in __kernel_vsyscall ()
#1  0x004977d3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0x00438de3 in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0x0033427d in system () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x00b396bd in smb_panic ()
#5  0x00b26bee in ?? ()
#6  <signal handler called>
#7  0x004737a0 in ?? () from /lib/tls/i686/cmov/libc.so.6
#8  0x00b0ec28 in rep_strlcpy ()
#9  0x00b47e27 in connections_fetch_entry ()
#10 0x008a991f in yield_connection ()
#11 0x0091dffe in close_cnum ()
#12 0x008b1ca7 in conn_close_all ()
#13 0x00e1f25c in ?? ()
#14 0x00e1f480 in exit_server_cleanly ()
#15 0x0091da12 in ?? ()
#16 0x00b4ac74 in run_events ()
#17 0x0091c402 in smbd_process ()
#18 0x00e1f978 in ?? ()
#19 0x00b4ac74 in run_events ()
#20 0x00b4af1f in ?? ()
#21 0x00b4b568 in _tevent_loop_once ()
#22 0x00e206ba in main ()
A debugging session is active.

	Inferior 1 [process 2393] will be detached.

Quit anyway? (y or n) [answered Y; input not from terminal]

---

