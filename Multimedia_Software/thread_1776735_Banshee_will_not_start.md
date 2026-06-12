---
title: "Banshee will not start"
date: 2011-06-06
forum: Multimedia Software
---

### Post by bombchicken on 2011-06-06
Recently Banshee won't start up all the way. If I just start it from the Unity launcher I get a blank white screen which will eventually stop responding. If I run Banshee from a terminal I get this output:
```
[Info  14:08:56.332] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-04-18 16:18:52 UTC]
[Info  14:08:58.329] Updating web proxy from GConf
[Info  14:08:58.536] All services are started 1.852889
** (Banshee:4120): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:4120): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:4120): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/kieran/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:4120): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

(Banshee:4120): Cogl-glx-WARNING **: ./cogl-framebuffer.c:912: Failed to create an OpenGL framebuffer

```

Any help would be appreciated.

---

### Post by set321go on 2011-06-16
Any resolution? 

im seeing the same issue, window opens then closes, same behavior if i open from unity or from tray widget

---

### Post by Yellow Pasque on 2011-06-16
Try this before running banshee:
```
mdkir ~/Podcasts
```
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/774820](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/774820)

---

### Post by set321go on 2011-06-17
Well i gave it a go, but it didnt work. I also tried running banshee with sudo which failed in the same way but did give a more verbose startup. I have attached the output first as normal user and second sudo privileges.

I also tried upgrading banshee but looks like i have the latest version. 

```

aedwards@alexdesktop:~/Downloads$ sudo mkdir ~/Podcasts
aedwards@alexdesktop:~/Downloads$ banshee
[Info  08:54:14.495] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, i686) @ 2011-04-18 16:21:33 UTC]
[Info  08:54:15.358] Updating web proxy from GConf
[Info  08:54:15.394] All services are started 0.730085
** (Banshee:7243): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:7243): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:7243): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/aedwards/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:7243): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:7243): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:7243): DEBUG: Loading the real store page

** (Banshee:7243): WARNING **: Got less number of items in credentials hash table than expected!
[Info  08:54:15.929] nereid Client Started
[Info  08:54:15.988] GStreamer version 0.10.32.0, gapless: True, replaygain: False

Native stacktrace:

	banshee() [0x80dbc5b]
	banshee() [0x805e92f]
	[0x71f40c]
	/usr/lib/libproxy.so.0(px_proxy_factory_get_proxies+0x4fa) [0x35acbfa]
	/usr/lib/i386-linux-gnu/gio/modules/libgiolibproxy.so(+0x107f) [0x44e507f]
	/usr/lib/i386-linux-gnu/gio/modules/libgiolibproxy.so(+0x1218) [0x44e5218]
	/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0x5db79) [0x8a1bb79]
	/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0x4e53c) [0x8a0c53c]
	/lib/i386-linux-gnu/libglib-2.0.so.0(+0x6ca39) [0x515a39]
	/lib/i386-linux-gnu/libglib-2.0.so.0(+0x6a2df) [0x5132df]
	/lib/i386-linux-gnu/libpthread.so.0(+0x5e99) [0xcd7e99]
	/lib/i386-linux-gnu/libc.so.6(clone+0x5e) [0x2dc73e]

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


```

```
                                    
aedwards@alexdesktop:~/Downloads$ sudo banshee
[Info  08:56:27.358] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, i686) @ 2011-04-18 16:21:33 UTC]
[Warn  08:56:28.624] DBus support could not be started. Disabling for this session.
[Info  08:56:28.854] Migrating album-art cache directory
[Warn  08:56:28.857] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 1: no such table: CoverArtDownloads (SQL: DELETE FROM CoverArtDownloads) (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
[Info  08:56:28.860] Migrated 0 files in 0.004536s
[Warn  08:56:31.685] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  08:56:31.685] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Warn  08:56:31.704] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `NDesk.DBus')
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
[Warn  08:56:31.704] Extension `Banshee.SoundMenu.SoundMenuService' not started: Unable to open the session message bus.
[Info  08:56:31.706] Updating web proxy from GConf
[Warn  08:56:31.805] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  08:56:31.805] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.

(Banshee:7310): Gtk-WARNING **: Refusing to add non-unique action 'CloseAction' to action group 'Global'
[Warn  08:56:31.805] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `NDesk.DBus')
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
[Warn  08:56:31.805] Extension `Banshee.SoundMenu.SoundMenuService' not started: Unable to open the session message bus.
[Info  08:56:31.806] All services are started 3.181493
** (Banshee:7310): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged

(Banshee:7310): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:7310): WARNING **: Error calling get_info: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1

** (Banshee:7310): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed
[Warn  08:56:32.443] Migrating Internet Radio Stations - System.IO.DirectoryNotFoundException: Directory '/root/.config/banshee/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFiles (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00000] in <filename unknown>:0 

** (Banshee:7310): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:7310): DEBUG: Loading the real store page

** (Banshee:7310): WARNING **: Got less number of items in credentials hash table than expected!
[Info  08:56:32.835] nereid Client Started
[Info  08:56:32.890] GStreamer version 0.10.32.0, gapless: True, replaygain: False

Native stacktrace:

	banshee() [0x80dbc5b]
	banshee() [0x805e92f]
	[0x40f40c]
	/usr/lib/libproxy.so.0(px_proxy_factory_get_proxies+0x4fa) [0x65d3bfa]
	/usr/lib/i386-linux-gnu/gio/modules/libgiolibproxy.so(+0x107f) [0x2dac07f]
	/usr/lib/i386-linux-gnu/gio/modules/libgiolibproxy.so(+0x1218) [0x2dac218]
	/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0x5db79) [0x3d1fb79]
	/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0x4e53c) [0x3d1053c]
	/lib/i386-linux-gnu/libglib-2.0.so.0(+0x6ca39) [0x4a6a39]
	/lib/i386-linux-gnu/libglib-2.0.so.0(+0x6a2df) [0x4a42df]
	/lib/i386-linux-gnu/libpthread.so.0(+0x5e99) [0x179e99]
	/lib/i386-linux-gnu/libc.so.6(clone+0x5e) [0x9f073e]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0xb12ffb70 (LWP 7362)]
[New Thread 0x58f2b70 (LWP 7361)]
[New Thread 0x5b07b70 (LWP 7359)]
[New Thread 0x3a16b70 (LWP 7356)]
[New Thread 0x5185b70 (LWP 7353)]
[New Thread 0x5021b70 (LWP 7352)]
[New Thread 0x3fc8b70 (LWP 7351)]
[New Thread 0x3880b70 (LWP 7350)]
[New Thread 0xb20ffb70 (LWP 7333)]
[New Thread 0xb2a7cb70 (LWP 7327)]
[New Thread 0xb327db70 (LWP 7326)]
[New Thread 0x39abb70 (LWP 7325)]
[New Thread 0x29c4b70 (LWP 7322)]
[New Thread 0x8edb70 (LWP 7313)]
[New Thread 0x17ffb70 (LWP 7312)]
0x0040f416 in __kernel_vsyscall ()
  16 Thread 0x17ffb70 (LWP 7312)  0x0040f416 in __kernel_vsyscall ()
  15 Thread 0x8edb70 (LWP 7313)  0x0040f416 in __kernel_vsyscall ()
  14 Thread 0x29c4b70 (LWP 7322)  0x0040f416 in __kernel_vsyscall ()
  13 Thread 0x39abb70 (LWP 7325)  0x0040f416 in __kernel_vsyscall ()
  12 Thread 0xb327db70 (LWP 7326)  0x0040f416 in __kernel_vsyscall ()
  11 Thread 0xb2a7cb70 (LWP 7327)  0x0040f416 in __kernel_vsyscall ()
  10 Thread 0xb20ffb70 (LWP 7333)  0x0040f416 in __kernel_vsyscall ()
  9 Thread 0x3880b70 (LWP 7350)  0x0040f416 in __kernel_vsyscall ()
  8 Thread 0x3fc8b70 (LWP 7351)  0x0040f416 in __kernel_vsyscall ()
  7 Thread 0x5021b70 (LWP 7352)  0x0040f416 in __kernel_vsyscall ()
  6 Thread 0x5185b70 (LWP 7353)  0x0040f416 in __kernel_vsyscall ()
  5 Thread 0x3a16b70 (LWP 7356)  0x0040f416 in __kernel_vsyscall ()
  4 Thread 0x5b07b70 (LWP 7359)  0x0040f416 in __kernel_vsyscall ()
  3 Thread 0x58f2b70 (LWP 7361)  0x0040f416 in __kernel_vsyscall ()
  2 Thread 0xb12ffb70 (LWP 7362)  0x0040f416 in __kernel_vsyscall ()
* 1 Thread 0x111900 (LWP 7310)  0x0040f416 in __kernel_vsyscall ()

Thread 16 (Thread 0x17ffb70 (LWP 7312)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0017e48c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x0821258a in ?? ()
#3  0x0820b1a9 in ?? ()
#4  0x08210db2 in ?? ()
#5  0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#6  0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 15 (Thread 0x8edb70 (LWP 7313)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x001807d5 in sem_wait@@GLIBC_2.1 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x08200488 in mono_sem_wait ()
#3  0x081412d8 in ?? ()
#4  0x081c3da4 in ?? ()
#5  0x081f669a in ?? ()
#6  0x08211c12 in ?? ()
#7  0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 14 (Thread 0x29c4b70 (LWP 7322)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x009e1f76 in poll () from /lib/i386-linux-gnu/libc.so.6
#2  0x0048b84b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x0047b1af in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x0047b92b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x03d79304 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#6  0x004a42df in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 13 (Thread 0x39abb70 (LWP 7325)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0017e48c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x081dfa74 in ?? ()
#3  0x081dfae4 in ?? ()
#4  0x081f316f in ?? ()
#5  0x081c3683 in ?? ()
#6  0x039c963a in ?? ()
#7  0x039c94ec in ?? ()
#8  0x039c881a in ?? ()
#9  0x001509d1 in ?? ()
#10 0x08062bc8 in ?? ()
#11 0x08192eee in mono_runtime_invoke ()
#12 0x081931f4 in mono_runtime_delegate_invoke ()
#13 0x081c3ebb in ?? ()
#14 0x081f669a in ?? ()
#15 0x08211c12 in ?? ()
#16 0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#17 0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 12 (Thread 0xb327db70 (LWP 7326)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0017e48c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0xb5152f57 in ?? () from /usr/lib/libwebkitgtk-1.0.so.0
#3  0xb5152f9d in ?? () from /usr/lib/libwebkitgtk-1.0.so.0
#4  0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#5  0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 11 (Thread 0xb2a7cb70 (LWP 7327)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0017e48c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0xb5166ab4 in ?? () from /usr/lib/libwebkitgtk-1.0.so.0
#3  0xb47afc12 in ?? () from /usr/lib/libwebkitgtk-1.0.so.0
#4  0xb47b141f in ?? () from /usr/lib/libwebkitgtk-1.0.so.0
#5  0xb47b156d in ?? () from /usr/lib/libwebkitgtk-1.0.so.0
#6  0xb516678f in ?? () from /usr/lib/libwebkitgtk-1.0.so.0
#7  0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 10 (Thread 0xb20ffb70 (LWP 7333)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0018152b in read () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x080dbe3d in ?? ()
#3  0x0805e92f in ?? ()
#4  <signal handler called>
#5  0x00a3ccbb in ?? () from /lib/i386-linux-gnu/libc.so.6
#6  0x0305ef82 in ?? () from /usr/lib/libproxy/0.3.1/modules/pacrunner_webkit.so
#7  0x065d3bfa in px_proxy_factory_get_proxies () from /usr/lib/libproxy.so.0
#8  0x02dac07f in ?? () from /usr/lib/i386-linux-gnu/gio/modules/libgiolibproxy.so
#9  0x02dac218 in ?? () from /usr/lib/i386-linux-gnu/gio/modules/libgiolibproxy.so
#10 0x03d1fb79 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#11 0x03d1053c in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#12 0x004a6a39 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#13 0x004a42df in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#14 0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#15 0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 9 (Thread 0x3880b70 (LWP 7350)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x00181d46 in nanosleep () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x081f5898 in ?? ()
#3  0x081c4f90 in ?? ()
#4  0x081c3da4 in ?? ()
#5  0x081f669a in ?? ()
#6  0x08211c12 in ?? ()
#7  0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 8 (Thread 0x3fc8b70 (LWP 7351)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0017e48c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x081dfa74 in ?? ()
#3  0x081dfb67 in ?? ()
#4  0x081f3b23 in ?? ()
#5  0x081c374f in ?? ()
#6  0x0370776d in ?? ()
#7  0x0370750f in ?? ()
#8  0x03707095 in ?? ()
#9  0x001460bf in ?? ()
#10 0x08062bc8 in ?? ()
#11 0x08192eee in mono_runtime_invoke ()
#12 0x081967a0 in mono_runtime_invoke_array ()
#13 0x08198d1e in ?? ()
#14 0x081c3ff3 in ?? ()
#15 0x081c4b67 in ?? ()
#16 0x081c3da4 in ?? ()
#17 0x081f669a in ?? ()
#18 0x08211c12 in ?? ()
#19 0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#20 0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 7 (Thread 0x5021b70 (LWP 7352)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0017e48c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x081dfa74 in ?? ()
#3  0x081dfb67 in ?? ()
#4  0x081f3b23 in ?? ()
#5  0x081c374f in ?? ()
#6  0x0370776d in ?? ()
#7  0x0370750f in ?? ()
#8  0x03707095 in ?? ()
#9  0x001460bf in ?? ()
#10 0x08062bc8 in ?? ()
#11 0x08192eee in mono_runtime_invoke ()
#12 0x081967a0 in mono_runtime_invoke_array ()
#13 0x08198d1e in ?? ()
#14 0x081c3ff3 in ?? ()
#15 0x081c4b67 in ?? ()
#16 0x081c3da4 in ?? ()
#17 0x081f669a in ?? ()
#18 0x08211c12 in ?? ()
#19 0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#20 0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 6 (Thread 0x5185b70 (LWP 7353)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0017e48c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x081dfa74 in ?? ()
#3  0x081dfb67 in ?? ()
#4  0x081f3b23 in ?? ()
#5  0x081c374f in ?? ()
#6  0x0370776d in ?? ()
#7  0x0370750f in ?? ()
#8  0x03707095 in ?? ()
#9  0x001460bf in ?? ()
#10 0x08062bc8 in ?? ()
#11 0x08192eee in mono_runtime_invoke ()
#12 0x081967a0 in mono_runtime_invoke_array ()
#13 0x08198d1e in ?? ()
#14 0x081c3ff3 in ?? ()
#15 0x081c4b67 in ?? ()
#16 0x081c3da4 in ?? ()
#17 0x081f669a in ?? ()
#18 0x08211c12 in ?? ()
#19 0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#20 0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 5 (Thread 0x3a16b70 (LWP 7356)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x009e1f76 in poll () from /lib/i386-linux-gnu/libc.so.6
#2  0x0048b84b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x0047b1af in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x0047b92b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x019a9e10 in ?? () from /usr/lib/libORBit-2.so.0
#6  0x004a42df in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 4 (Thread 0x5b07b70 (LWP 7359)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0018152b in read () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x03ec08e2 in Mono_Posix_Syscall_read () from /usr/lib/libMonoPosixHelper.so
#3  0x0193b79a in ?? ()
#4  0x0193ce6a in ?? ()
#5  0x0193cd1a in ?? ()
#6  0x03753bdf in ?? ()
#7  0x03756e4d in ?? ()
#8  0x03713fa7 in ?? ()
#9  0x001460bf in ?? ()
#10 0x08062bc8 in ?? ()
#11 0x08192eee in mono_runtime_invoke ()
#12 0x081967a0 in mono_runtime_invoke_array ()
#13 0x08198d1e in ?? ()
#14 0x081c3ff3 in ?? ()
#15 0x081c4b67 in ?? ()
#16 0x081c3da4 in ?? ()
#17 0x081f669a in ?? ()
#18 0x08211c12 in ?? ()
#19 0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#20 0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 3 (Thread 0x58f2b70 (LWP 7361)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x00181758 in accept () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x081edcf6 in ?? ()
#3  0x0819b9fb in ?? ()
#4  0x03716ec5 in ?? ()
#5  0x03234e58 in ?? ()
#6  0x0375b083 in ?? ()
#7  0x001509d1 in ?? ()
#8  0x08062bc8 in ?? ()
#9  0x08192eee in mono_runtime_invoke ()
#10 0x081931f4 in mono_runtime_delegate_invoke ()
#11 0x081c3ebb in ?? ()
#12 0x081f669a in ?? ()
#13 0x08211c12 in ?? ()
#14 0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#15 0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 2 (Thread 0xb12ffb70 (LWP 7362)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x0017e834 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x0057af0e in ?? () from /usr/lib/i386-linux-gnu/libgthread-2.0.so.0
#3  0x0044e42c in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x004a6a83 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x004a42df in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#6  0x00179e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#7  0x009f073e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 1 (Thread 0x111900 (LWP 7310)):
#0  0x0040f416 in __kernel_vsyscall ()
#1  0x009e1f76 in poll () from /lib/i386-linux-gnu/libc.so.6
#2  0x0048b84b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x0047b1af in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x0047b92b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x01f1dc39 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#6  0x031f40c6 in ?? ()
#7  0x031f408b in ?? ()
#8  0x07076e3d in ?? ()
#9  0x006681f8 in ?? ()
#10 0x0066809a in ?? ()
#11 0x00667fbd in ?? ()
#12 0x0065af19 in ?? ()
#13 0x0065ad96 in ?? ()
#14 0x0065adec in ?? ()
#15 0x08062bc8 in ?? ()
#16 0x08192eee in mono_runtime_invoke ()
#17 0x081959e0 in mono_runtime_exec_main ()
#18 0x0065ad27 in ?? ()
#19 0x0065abe7 in ?? ()
#20 0x0065aab6 in ?? ()
#21 0x0065aa60 in ?? ()
#22 0x0065a9e2 in ?? ()
#23 0x0065a998 in ?? ()
#24 0x00155102 in ?? ()
#25 0x00146351 in ?? ()
#26 0x0014644b in ?? ()
#27 0x08062bc8 in ?? ()
#28 0x08192eee in mono_runtime_invoke ()
#29 0x081959e0 in mono_runtime_exec_main ()
#30 0x08195ced in mono_runtime_run_main ()
#31 0x080b7706 in mono_main ()
#32 0x08059355 in ?? ()
#33 0x00936e37 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
#34 0x08059291 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
==========================

```

---

### Post by set321go on 2011-07-25
have there been any updates on this issue?

---

### Post by stevenmc on 2013-02-19
> **Temüjin said:**
> Try this before running banshee:
```
mdkir ~/Podcasts
```
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/774820](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/774820)


Yes, **mkdir /~Podcasts** worked (note the typo in the quote though).

---

### Post by wildmanne39 on 2013-02-19
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

