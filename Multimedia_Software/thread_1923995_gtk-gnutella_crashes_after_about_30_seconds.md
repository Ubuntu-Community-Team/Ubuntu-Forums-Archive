---
title: "gtk-gnutella crashes after about 30 seconds"
date: 2012-02-11
forum: Multimedia Software
---

### Post by cforput on 2012-02-11
I installed the version of gtk-gnutella (97-2) both our of synaptic and off the gtk website. Both instances act the same. At first they wouldn't connect. Then after it bootstrapped it now shuts down after running about 30 seconds. 

Here is one of the crash reports:

***************************************
Executable-Path: /usr/bin/gtk-gnutella
Version: gtk-gnutella/0.97-19337 (2011-07-18; GTK2; Linux x86_64)
Run-Elapsed: 10s
Run-Seconds: 10
Crash-Signal: SIGTRAP
Crash-Time: 2012-02-11 16:47:15
Core-Dump: disabled
Working-Directory: /home/xxxxxxxx
Crash-Directory: /home/xxxxxxxxx/.gtk-gnutella/crashes
Crash-File: gtk-gnutella-r19337-crash.10928.log
Stacktrace:
	0x7fcd98973060
	0x7fcd98e10313
	0x7fcd98e106a2
	~prop_get_storage+224
	~dmesh_alternate_location+3744
	~download_send_request+2883
	~download_continue+705
	~download_rx_done+401
	~thex_download_data_ind+336
	~is_readable+256
	~inputevt_timer+469
	~dispatch_poll+12
	0x7fcd98e07a5d
	0x7fcd98e08258
	0x7fcd98e08792
	0x7fcd99fffdb7
	~main_gui_run+276
	~main+1716
	0x7fcd9833d30d
	~_start+41
	0x0
	0x0
	0x1f2d840
	0x1f2d9d0
	0xb
	0xfbad8004
	0x23dc078
	0x0
	0x0
	0x7fff9181a210
	0x7fff9181a25a
	0x7fff9181c210
	0x1f2d8b8
	0x2397580
	0x7fcd94de0a74
	0x0
	0x21
	0x23dc078
	0x1fb87c0
	0x401f3ba88
	0x1fb8b30
	0x0
	0x0
	0x1f3bb38
	0x1f3ba30
	0x1f3bb38
	0x1
	0x1f2d840
	0x7fcd94de36b3
	0xffffffff
	~signal_trampoline
	0x14000000
	0x7fcd98973060
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x1f36a38
	0x0
	0x14000000
	0x7fcd98973060
	0x0
	0x249d5b8
	0xa
	0x1f36a08
	0xa
	0x100000001
	0x118
	0x1f36970
	0x5555555555555556
	0x3
	0x1f36a38
	0x1
	0x0
	0x7fcd94dea01e
	0x2
	0x140
	0xa
	~signal_set+184
	~signal_trampoline
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x0
	0x10000000
	0x0
	0x7fcd98963f00
	0x0
	0x0
	0x249d5b8
	0xa
	0x1f36a08
	0xa
	0x100000001
	0x118
	0x1f36970
	0x5555555555555556
	0x3
	0x1f36a38
	0x1
	0x0
	0x7fcd94dea01e
	0x2
	0x140
	0x7fff14000000
	0x7fcd98973060
	0x7fff9181dc60
	0x7fff9181ca70
	0x5

Reading symbols from /usr/bin/gtk-gnutella...(no debugging symbols found)...done.
Attaching to program: /usr/bin/gtk-gnutella, process 10928
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
(gdb) No stack.
(gdb) No stack.
(gdb) 
******************************************************

Anyone have any ideas?

---

### Post by ram4 on 2012-02-12
> **cforput said:**
> I installed the version of gtk-gnutella (97-2) both our of synaptic and off the gtk website. Both instances act the same. At first they wouldn't connect. Then after it bootstrapped it now shuts down after running about 30 seconds. 

Here is one of the crash reports:

Version: gtk-gnutella/0.97-19337 (2011-07-18; GTK2; Linux x86_64)
Crash-Signal: SIGTRAP

Anyone have any ideas?

Woa, a SIGTRAP is a very weird signal to receive.  Is this a pre-compiled binary or did you compile it yourself?

The stack trace was prefixed with "~" symbols, meaning that gtk-gnutella did not fully match the symbols with the function addresses.  This is a sign that something is not in sync.

I have two things to suggest at this point:

Either look for version 0.98.2 (the latest) pre-compiled for Ubuntu and see whether you have better luck.  The problem you're having is not really related to gtk-gnutella, but rather seems to be a mismatch between the binary and your system.

Or, if you can follow complation instructions, grab the source package from sourceforge, untar it and look at README.Debian.  Since Ubuntu is based on Debian, the provided instructions will work just fine.  If after installing the .deb resulting from a recompilation on your system you are having the same problems, we'll have to become more elaborate in our investigation.

Let me know how well it goes.

---

### Post by cforput on 2012-02-12
Well a couple of things. First, I tried just intalling out of Synaptic and also off of the gtk-gnutella site so precompiled. I got the same result. Then I wanted to check a couple of things so I started it back up and it didn't crash. Very odd. The only thing that I did differently is I didn't filter my search results by audio files. I just left them all unchecked. 

At this point, I think I'm OK but I really don't know what I did (or didn't do).

I'm going to close this as solved even though I have no solution to document or offer.

Thanks for the response.

---

