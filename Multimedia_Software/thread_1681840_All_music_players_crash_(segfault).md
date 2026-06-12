---
title: "All music players crash (segfault?)"
date: 2011-02-04
forum: Multimedia Software
---

### Post by zweiundzwei on 2011-02-04
Rhythmbox crashes on startup, Clementine crashes once I try to play any file, Banshee crashes after the first second of any file.
Totem actually still works, but it's not a very satisfying media player. :P
This occurred suddenly after working fine for, well, months. I read that I should check whether I have the standard up-to-date gstreamer/pulseaudio/liborc versions installed, this seems to be the case.
Otherwise I'm kind of helpless and desperate.

Here the terminal output for all crashes:

> doro@matja:~$ clementine
virtual bool QxtGlobalShortcutBackend::DoRegister() 
Device added: "DeviceKit/NA057YSV/Seagate/FreeAgent GoFlex/1000202241024" 
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
HTTP GET  QUrl( "http://post.audioscrobbler.com:80/?hs=true&p=1.2.1&c=tng&v=0.6&u=zweiundzwei&t=1296870850&a=e6d7d1b96c9eabdad3b3036fb69437a9&api_key=75d20fb472be99275392aefa2760ea09&sk=f05c565777e77191b2db7fe1d7612b39" )  
Segmentation fault

> doro@matja:~$ banshee
[Info  02:54:39.092] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[Info  02:54:44.745] Updating web proxy from GConf
[Info  02:54:45.106] All services are started 5.063183
[Info  02:54:49.451] nereid Client Started
[Info  02:54:50.719] AppleDeviceSource is ignoring unmounted volume 21 GB Filesystem
[Warn  02:54:50.742] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[Warn  02:54:50.860] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
Stacktrace:

  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at System.Net.Dns.GetHostByName (string) <0x00038>
  at System.Net.ServicePoint.get_HostEntry () <0x00137>
  at System.Net.WebConnection.Connect (System.Net.HttpWebRequest) <0x0010b>
  at System.Net.WebConnection.InitConnection (object) <0x00129>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <0x00046>

Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x810ffeb]
	[0xd2640c]
	/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x3f) [0xaa16761f]
	/lib/libc.so.6(gethostbyname2_r+0x1c5) [0x6901a5]
	/lib/libc.so.6(+0xa782c) [0x64f82c]
	/lib/libc.so.6(getaddrinfo+0x165) [0x6513b5]
	banshee-1() [0x8158c93]
	[0x6c8208b]
	[0x6c81fa9]
	[0x6c81dc8]
	[0x6c81804]
	[0x6c814aa]
	[0x1620bf]
	banshee-1() [0x8061328]
	banshee-1(mono_runtime_invoke+0x40) [0x813c890]
	banshee-1(mono_runtime_invoke_array+0x2a4) [0x81421a4]
	banshee-1() [0x814266e]
	banshee-1() [0x81d2341]
	banshee-1() [0x81d2858]
	banshee-1() [0x81b11db]
	banshee-1() [0x81e8e4e]
	banshee-1() [0x8214f85]
	/lib/libpthread.so.0(+0x5cc9) [0xc1ecc9]
	/lib/libc.so.6(clone+0x5e) [0x67869e]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

> doro@matja:~$ rhythmbox

(rhythmbox:9290): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:9290): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (rhythmbox:9290): DEBUG: Loading the real store page

** (rhythmbox:9290): WARNING **: Got less number of items in credentials hash table than expected!
** (rhythmbox:9290): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
Segmentation fault

---

### Post by BrightEyesDavid on 2011-03-08
I seem to have the same problem in 10.10. I submitted a bug report to Pidgin as it was crashing on every message sent/received, and it turned out that was gstreamer. Clementine also crashes when playing audio:

```
david@skipper:~$ gdb clementine
GNU gdb (GDB) 7.2-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/clementine...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/bin/clementine 
[Thread debugging using libthread_db enabled]
[New Thread 0x7fffeaa22700 (LWP 5437)]
[New Thread 0x7fffdee24700 (LWP 5438)]
virtual bool QxtGlobalShortcutBackend::DoRegister() 
[New Thread 0x7fffde5d9700 (LWP 5439)]
[New Thread 0x7fffdddd8700 (LWP 5440)]
[New Thread 0x7fffdd5d7700 (LWP 5441)]
[Thread 0x7fffdd5d7700 (LWP 5441) exited]
[New Thread 0x7fffdd5d7700 (LWP 5442)]
[New Thread 0x7fffdcdd6700 (LWP 5443)]
[New Thread 0x7fffd7fff700 (LWP 5444)]
[New Thread 0x7fffd77fe700 (LWP 5445)]
[New Thread 0x7fffd6ffd700 (LWP 5446)]
[New Thread 0x7fffd67fc700 (LWP 5447)]
[New Thread 0x7fffd5ffb700 (LWP 5448)]
[New Thread 0x7fffd57fa700 (LWP 5449)]
[New Thread 0x7fffd4ff9700 (LWP 5450)]
[New Thread 0x7fffcffff700 (LWP 5451)]
[New Thread 0x7fffcccd6700 (LWP 5453)]
[New Thread 0x7fffc7e8e700 (LWP 5454)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7fffc7e8e700 (LWP 5454)]
0x00007fffced5be4c in orc_sse_set_mxcsr () from /usr/lib/liborc-0.4.so.0
(gdb) bt
#0  0x00007fffced5be4c in orc_sse_set_mxcsr () from /usr/lib/liborc-0.4.so.0
#1  0x00007fffced6209a in orc_compiler_sse_assemble () from /usr/lib/liborc-0.4.so.0
#2  0x00007fffced521f5 in orc_program_compile_full () from /usr/lib/liborc-0.4.so.0
#3  0x00007fffcf5fc177 in ?? () from /usr/lib/gstreamer-0.10/libgstvolume.so
#4  0x00007fffcf5fb27c in ?? () from /usr/lib/gstreamer-0.10/libgstvolume.so
#5  0x00007ffff403d161 in ?? () from /usr/lib/libgstbase-0.10.so.0
#6  0x00007ffff403d77d in ?? () from /usr/lib/libgstbase-0.10.so.0
#7  0x00007ffff47fc12d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#8  0x00007ffff47fc9ee in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x00007ffff403d7c9 in ?? () from /usr/lib/libgstbase-0.10.so.0
#10 0x00007ffff47fc12d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#11 0x00007ffff47fc9ee in ?? () from /usr/lib/libgstreamer-0.10.so.0
#12 0x00007ffff403d7c9 in ?? () from /usr/lib/libgstbase-0.10.so.0
#13 0x00007ffff47fc12d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0x00007ffff47fc9ee in ?? () from /usr/lib/libgstreamer-0.10.so.0
#15 0x00007ffff403d7c9 in ?? () from /usr/lib/libgstbase-0.10.so.0
#16 0x00007ffff47fc12d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#17 0x00007ffff47fc9ee in ?? () from /usr/lib/libgstreamer-0.10.so.0
#18 0x00007ffff403d7c9 in ?? () from /usr/lib/libgstbase-0.10.so.0
#19 0x00007ffff47fc12d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#20 0x00007ffff47fc9ee in ?? () from /usr/lib/libgstreamer-0.10.so.0
#21 0x00007ffff47fc12d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#22 0x00007ffff47fc9ee in ?? () from /usr/lib/libgstreamer-0.10.so.0
#23 0x00007ffff47fc12d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#24 0x00007ffff47fc9ee in ?? () from /usr/lib/libgstreamer-0.10.so.0
#25 0x00007ffff47fc12d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#26 0x00007ffff47fc9ee in ?? () from /usr/lib/libgstreamer-0.10.so.0
#27 0x00007fffc80b6675 in ?? () from /usr/lib/gstreamer-0.10/libgstflac.so
#28 0x00007fffcd1d758d in ?? () from /usr/lib/libFLAC.so.8
#29 0x00007fffcd1d7920 in FLAC__stream_decoder_process_single () from /usr/lib/libFLAC.so.8
#30 0x00007fffc80b4b80 in ?? () from /usr/lib/gstreamer-0.10/libgstflac.so
#31 0x00007ffff4825c93 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#32 0x00007ffff4ae973f in ?? () from /lib/libglib-2.0.so.0
#33 0x00007ffff4ae77e4 in ?? () from /lib/libglib-2.0.so.0
#34 0x00007ffff76ec971 in start_thread () from /lib/libpthread.so.0
#35 0x00007ffff0ec592d in clone () from /lib/libc.so.6
#36 0x0000000000000000 in ?? ()
```

I'm not sure what to try next. Maybe I can get an updated gstreamer from somewhere...

Rhythmbox is actually playing okay, however.

---

### Post by BrightEyesDavid on 2011-03-08
Success! [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

```
sudo add-apt-repository ppa:gstreamer-developers/ppa
sudo apt-get update
sudo apt-get upgrade
```

Try your music player again.

---

