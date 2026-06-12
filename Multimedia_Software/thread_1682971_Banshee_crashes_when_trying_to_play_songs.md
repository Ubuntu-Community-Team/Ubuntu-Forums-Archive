---
title: "Banshee crashes when trying to play songs"
date: 2011-02-06
forum: Multimedia Software
---

### Post by moly82 on 2011-02-06
this is the output I get as soon as I double click any songs (disabled all extensions first just to be sure)


please help this does seem to be the only player that can sync music to my blackberry, including playlists :( (I'm sad as banshee is very slow here, while for example rhythmbox is much faster, but rhythmbox does not sync my playlists to the BB ;) :( )


thanks in advance bye


robinho@Beota:~$ banshee
[Info  01:06:26.701] Running Banshee 1.8.1: [Ubuntu 10.10 (linux-gnu, i686) @ 2011-01-29 19:31:12 UTC]
[Info  01:06:33.161] Updating web proxy from GConf
[Info  01:06:33.307] All services are started 5,514866
[Info  01:06:36.985] nereid Client Started

Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x805b81f]
	[0x29f40c]
	/usr/lib/liborc-0.4.so.0(orc_x86_emit_prologue+0xd8) [0x2c01cf8]
	/usr/lib/liborc-0.4.so.0(orc_compiler_sse_assemble+0x59) [0x2bfddf9]
	/usr/lib/liborc-0.4.so.0(orc_program_compile_full+0x51b) [0x2beb1fb]
	/usr/lib/liborc-0.4.so.0(orc_program_compile_for_target+0x36) [0x2beb2d6]
	/usr/lib/liborc-0.4.so.0(orc_program_compile+0x26) [0x2beb306]
	/usr/lib/gstreamer-0.10/libgstvolume.so(+0x3f3b) [0x62f1f3b]
	/usr/lib/gstreamer-0.10/libgstvolume.so(+0x2913) [0x62f0913]
	/usr/lib/gstreamer-0.10/libgstvolume.so(+0x2dbe) [0x62f0dbe]
	/usr/lib/libgstbase-0.10.so.0(+0x27bcf) [0x17bdbcf]
	/usr/lib/libgstbase-0.10.so.0(+0x28357) [0x17be357]
	/usr/lib/libgstreamer-0.10.so.0(+0x4fedd) [0x7190edd]
	/usr/lib/libgstreamer-0.10.so.0(+0x508f7) [0x71918f7]
	/usr/lib/libgstbase-0.10.so.0(+0x283ae) [0x17be3ae]
	/usr/lib/libgstreamer-0.10.so.0(+0x4fedd) [0x7190edd]
	/usr/lib/libgstreamer-0.10.so.0(+0x508f7) [0x71918f7]
	/usr/lib/libgstbase-0.10.so.0(+0x283ae) [0x17be3ae]
	/usr/lib/libgstreamer-0.10.so.0(+0x4fedd) [0x7190edd]
	/usr/lib/libgstreamer-0.10.so.0(+0x508f7) [0x71918f7]
	/usr/lib/libgstbase-0.10.so.0(+0x283ae) [0x17be3ae]
	/usr/lib/libgstreamer-0.10.so.0(+0x4fedd) [0x7190edd]
	/usr/lib/libgstreamer-0.10.so.0(+0x508f7) [0x71918f7]
	/usr/lib/libgstbase-0.10.so.0(+0x283ae) [0x17be3ae]
	/usr/lib/libgstreamer-0.10.so.0(+0x4fedd) [0x7190edd]
	/usr/lib/libgstreamer-0.10.so.0(+0x508f7) [0x71918f7]
	/usr/lib/gstreamer-0.10/libgstcoreelements.so(+0x17565) [0x2b21565]
	/usr/lib/libgstreamer-0.10.so.0(+0x7ccd9) [0x71bdcd9]
	/usr/lib/libgstreamer-0.10.so.0(+0x7e2b7) [0x71bf2b7]
	/lib/libglib-2.0.so.0(+0x6a3d4) [0xe113d4]
	/lib/libglib-2.0.so.0(+0x6848f) [0xe0f48f]
	/lib/libpthread.so.0(+0x5cc9) [0x11ecc9]
	/lib/libc.so.6(clone+0x5e) [0x20369e]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
===========================

---

### Post by moly82 on 2011-02-07
nobody? :(

---

