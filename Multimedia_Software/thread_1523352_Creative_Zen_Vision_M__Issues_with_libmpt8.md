---
title: "Creative Zen Vision: M  Issues with libmpt8"
date: 2010-07-03
forum: Multimedia Software
---

### Post by x56sImpulse on 2010-07-03
I've been having problems with my Zen for quite a while now.  I mostly use Banshee and I was previously able to easily sync my zen with it.  I stopped using my Zen for a while.  When I finally did try to sync with Banshee the program crashed.  
Individual files can be manually moved to the Zen with banshee and only every few songs cause banshee to crash.  When syncing, a few songs will sync, sometimes up to 25, but then banshee will crash again.
The same goes for Rhythmbox.  Some songs will cause an error, others will not.  Right now Rhythmbox will crash immediately after connecting to the zen.


I have heard of some problems involving libmpt8, but I haven't seen any solutions.

banshee --debug gives:

```

[1 Debug 11:29:16.780] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 11:29:16.787] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 11:29:16.832] Player state change: NotReady -> Ready
[1 Debug 11:29:16.840] Loaded equalizer presets: 6.3E-05
[1 Debug 11:29:16.844] Selected equalizer: Rock
[1 Debug 11:29:16.849] Player state change: Ready -> Idle
[1 Debug 11:29:16.853] (libbanshee:player) Disabled ReplayGain
[1 Debug 11:29:16.854] Delayed Initializating Banshee.LibraryWatcher.LibraryWatcherService
[1 Debug 11:29:16.907] Started LibraryWatcher for Music (/home/space-fish/Music/)
[1 Debug 11:29:16.909] Started LibraryWatcher for Videos (/home/space-fish/Videos/)
[1 Debug 11:29:16.928] Starting
[1 Debug 11:29:16.957] Delayed Initializating Banshee.Podcasting.PodcastService
[2 Debug 11:29:16.969] Finished
[1 Debug 11:29:16.996] Delayed Initializating Banshee.Dap.DapService
[1 Debug 11:29:16.999] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 11:29:17.000] Dap support extension loaded: Banshee.Dap.Karma
[1 Debug 11:29:17.000] Dap support extension loaded: Banshee.Dap.Ipod
[1 Debug 11:29:17.000] Dap support extension loaded: Banshee.Dap.Mtp
[3 Debug 11:29:17.005] Refreshing any podcasts that haven't been updated in over an hour
[1 Debug 11:29:17.309] Delayed Initializating Banshee.Daap.DaapService
[4 Debug 11:29:17.440] DAAP Proxy listening for connections on port 8089
[5 Debug 11:29:18.334] Found DAP support (Banshee.Dap.Mtp.MtpSource) for device My Zen
[1 Debug 11:29:25.202] Starting - Saving Metadata to File
[6 Debug 11:29:25.210] Finished - Saving Metadata to File
[7 Debug 11:29:28.527] Starting
[7 Debug 11:29:28.630] Initialized MediaProfileManager: 0.073417
[7 Debug 11:29:28.650] GStreamer pipeline does not run: audioconvert ! novellaacenc bitrate=128000 profile=2 outputformat=0 ! novellqtmux
[7 Debug 11:29:28.663] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[7 Debug 11:29:28.673] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[7 Info  11:29:30.285] Uncached artwork size 170 requested
[7 Info  11:29:31.971] Uncached artwork size 170 requested
Stacktrace:

  at (wrapper managed-to-native) Mtp.Album.LIBMTP_Create_New_Album (Mtp.MtpDeviceHandle,Mtp.AlbumStruct&) <0x00004>
  at (wrapper managed-to-native) Mtp.Album.LIBMTP_Create_New_Album (Mtp.MtpDeviceHandle,Mtp.AlbumStruct&) <0xffffffff>
  at Mtp.Album.Create () <0x0001b>
  at Mtp.AbstractTrackList.Save () <0x00159>
  at Mtp.Album.Save (byte[],uint,uint) <0x00029>
  at Banshee.Dap.Mtp.MtpSource.AddTrackToDevice (Banshee.Collection.Database.DatabaseTrackInfo,Banshee.Base.SafeUri) <0x002f2>
  at Banshee.Dap.DapSource.AttemptToAddTrackToDevice (Banshee.Collection.Database.DatabaseTrackInfo,Banshee.Base.SafeUri) <0x00156>
  at Banshee.Dap.DapSource.AddTrackAndIncrementCount (Banshee.Collection.Database.DatabaseTrackInfo) <0x0003c>
  at Banshee.Sources.PrimarySource.AddTrackList (object) <0x001ce>
  at Banshee.Sources.PrimarySource.AddAllTracks (Banshee.Sources.Source) <0x0017e>
  at Banshee.Dap.DapLibrarySync.Sync (bool) <0x000a1>
  at Banshee.Dap.DapLibrarySync.Sync () <0x00012>
  at Banshee.Dap.DapSync.RateLimitedSync () <0x00174>
  at Banshee.Base.RateLimiter.InnerExecute () <0x0004e>
  at Banshee.Base.RateLimiter.Execute () <0x00060>
  at Banshee.Dap.DapSync.Sync () <0x00058>
  at Banshee.Dap.DapSource.ThreadedLoadDeviceContents (object) <0x000da>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1() [0x80ca6e4]
	banshee-1() [0x80f6893]
	[0xb77f5410]
	/usr/lib/libmtp.so.8(LIBMTP_Create_New_Album+0x7f) [0xa99e18af]
	[0xa9973035]
	[0xa9972e2c]
	[0xa9972d1a]
	[0xa9972ad2]
	[0xa99712bb]
	[0xa9970bef]
	[0xa9989acd]
	[0xa9989397]
	[0xa99889e7]
	[0xa9988312]
	[0xa998826b]
	[0xa9987d85]
	[0xafb851ef]
	[0xafb85189]
	[0xa9987c09]
	[0xa9c3a61b]
	[0xb713c087]
	banshee-1(mono_runtime_invoke_array+0x34f) [0x8115d2f]
	banshee-1() [0x8115f7e]
	banshee-1() [0x8155043]
	banshee-1() [0x8155517]
	banshee-1() [0x81527ea]
	banshee-1() [0x81c3062]
	banshee-1() [0x81e1925]
	/lib/tls/i686/cmov/libpthread.so.0(+0x596e) [0xb76ef96e]
	/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7637a4e]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0xa9e86b70 (LWP 7801)]
[New Thread 0xaa2fcb70 (LWP 7799)]
[New Thread 0xaf9ffb70 (LWP 7798)]
[New Thread 0xa9affb70 (LWP 7797)]
[New Thread 0xa9d6db70 (LWP 7796)]
[New Thread 0xa9fb8b70 (LWP 7791)]
[New Thread 0xa9ff9b70 (LWP 7790)]
[New Thread 0xaa0fab70 (LWP 7789)]
[New Thread 0xaa1fbb70 (LWP 7788)]
[New Thread 0xaa3fdb70 (LWP 7786)]
[New Thread 0xaa4feb70 (LWP 7785)]
[New Thread 0xaa5ffb70 (LWP 7784)]
[New Thread 0xab101b70 (LWP 7783)]
[New Thread 0xaf8feb70 (LWP 7781)]
[New Thread 0xb0dd9b70 (LWP 7778)]
[New Thread 0xb4ffeb70 (LWP 7777)]
[New Thread 0xb50ffb70 (LWP 7775)]
[New Thread 0xb6d47b70 (LWP 7771)]
[New Thread 0xb6d6bb70 (LWP 7770)]
0xb77f5430 in __kernel_vsyscall ()
  20 Thread 0xb6d6bb70 (LWP 7770)  0xb77f5430 in __kernel_vsyscall ()
  19 Thread 0xb6d47b70 (LWP 7771)  0xb77f5430 in __kernel_vsyscall ()
  18 Thread 0xb50ffb70 (LWP 7775)  0xb77f5430 in __kernel_vsyscall ()
  17 Thread 0xb4ffeb70 (LWP 7777)  0xb77f5430 in __kernel_vsyscall ()
  16 Thread 0xb0dd9b70 (LWP 7778)  0xb77f5430 in __kernel_vsyscall ()
  15 Thread 0xaf8feb70 (LWP 7781)  0xb77f5430 in __kernel_vsyscall ()
  14 Thread 0xab101b70 (LWP 7783)  0xb77f5430 in __kernel_vsyscall ()
  13 Thread 0xaa5ffb70 (LWP 7784)  0xb77f5430 in __kernel_vsyscall ()
  12 Thread 0xaa4feb70 (LWP 7785)  0xb77f5430 in __kernel_vsyscall ()
  11 Thread 0xaa3fdb70 (LWP 7786)  0xb77f5430 in __kernel_vsyscall ()
  10 Thread 0xaa1fbb70 (LWP 7788)  0xb77f5430 in __kernel_vsyscall ()
  9 Thread 0xaa0fab70 (LWP 7789)  0xb77f5430 in __kernel_vsyscall ()
  8 Thread 0xa9ff9b70 (LWP 7790)  0xb77f5430 in __kernel_vsyscall ()
  7 Thread 0xa9fb8b70 (LWP 7791)  0xb77f5430 in __kernel_vsyscall ()
  6 Thread 0xa9d6db70 (LWP 7796)  0xb77f5430 in __kernel_vsyscall ()
  5 Thread 0xa9affb70 (LWP 7797)  0xb77f5430 in __kernel_vsyscall ()
  4 Thread 0xaf9ffb70 (LWP 7798)  0xb77f5430 in __kernel_vsyscall ()
  3 Thread 0xaa2fcb70 (LWP 7799)  0xb77f5430 in __kernel_vsyscall ()
  2 Thread 0xa9e86b70 (LWP 7801)  0xb77f5430 in __kernel_vsyscall ()
* 1 Thread 0xb75376f0 (LWP 7768)  0xb77f5430 in __kernel_vsyscall ()

Thread 20 (Thread 0xb6d6bb70 (LWP 7770)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f7736 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a6af8 in ?? ()
#3  0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 19 (Thread 0xb6d47b70 (LWP 7771)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f6245 in sem_wait@@GLIBC_2.1 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0812e199 in ?? ()
#3  0x081527ea in ?? ()
#4  0x081c3062 in ?? ()
#5  0x081e1925 in ?? ()
#6  0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 18 (Thread 0xb50ffb70 (LWP 7775)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac8b4 in ?? ()
#4  0x081c742f in ?? ()
#5  0x0814f763 in ?? ()
#6  0xb5911e45 in ?? ()
#7  0xb5911b94 in ?? ()
#8  0xb59117d2 in ?? ()
#9  0xb71426f9 in ?? ()
#10 0x08110ef4 in mono_runtime_delegate_invoke ()
#11 0x0815285b in ?? ()
#12 0x081c3062 in ?? ()
#13 0x081e1925 in ?? ()
#14 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 17 (Thread 0xb4ffeb70 (LWP 7777)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb2e57ec7 in ?? () from /usr/lib/libwebkit-1.0.so.2
#3  0xb2e57f01 in ?? () from /usr/lib/libwebkit-1.0.so.2
#4  0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 16 (Thread 0xb0dd9b70 (LWP 7778)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb2d93ad4 in ?? () from /usr/lib/libwebkit-1.0.so.2
#3  0xb2b269af in ?? () from /usr/lib/libwebkit-1.0.so.2
#4  0xb2b26a84 in ?? () from /usr/lib/libwebkit-1.0.so.2
#5  0xb2d93a3f in ?? () from /usr/lib/libwebkit-1.0.so.2
#6  0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 15 (Thread 0xaf8feb70 (LWP 7781)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac937 in ?? ()
#4  0x081c7a63 in ?? ()
#5  0x081512f9 in ?? ()
#6  0xafe4da75 in ?? ()
#7  0xafe4d829 in ?? ()
#8  0xafe4d4fd in ?? ()
#9  0xb713c087 in ?? ()
#10 0x08115d2f in mono_runtime_invoke_array ()
#11 0x08115f7e in ?? ()
#12 0x08155043 in ?? ()
#13 0x08155517 in ?? ()
#14 0x081527ea in ?? ()
#15 0x081c3062 in ?? ()
#16 0x081e1925 in ?? ()
#17 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 14 (Thread 0xab101b70 (LWP 7783)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb7629b86 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xaf754502 in ?? () from /usr/lib/libpulse.so.0
#3  0xaf740a59 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0xaf742a13 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#5  0xaf742ae4 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0xaf7542a3 in ?? () from /usr/lib/libpulse.so.0
#7  0xaf2f0e02 in ?? () from /usr/lib/libpulsecommon-0.9.21.so
#8  0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 13 (Thread 0xaa5ffb70 (LWP 7784)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac8b4 in ?? ()
#4  0x081c742f in ?? ()
#5  0x0814f763 in ?? ()
#6  0xb5911e45 in ?? ()
#7  0xb5911b94 in ?? ()
#8  0xafb1159f in ?? ()
#9  0xb71426f9 in ?? ()
#10 0x08110ef4 in mono_runtime_delegate_invoke ()
#11 0x0815285b in ?? ()
#12 0x081c3062 in ?? ()
#13 0x081e1925 in ?? ()
#14 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 12 (Thread 0xaa4feb70 (LWP 7785)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac8b4 in ?? ()
#4  0x081c742f in ?? ()
#5  0x0814f763 in ?? ()
#6  0xb5911e45 in ?? ()
#7  0xb5911b94 in ?? ()
#8  0xafb1159f in ?? ()
#9  0xb71426f9 in ?? ()
#10 0x08110ef4 in mono_runtime_delegate_invoke ()
#11 0x0815285b in ?? ()
#12 0x081c3062 in ?? ()
#13 0x081e1925 in ?? ()
#14 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 11 (Thread 0xaa3fdb70 (LWP 7786)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb7627e2b in read () from /lib/tls/i686/cmov/libc.so.6
#2  0xafb1500f in ?? ()
#3  0xafb14f26 in ?? ()
#4  0xb71426f9 in ?? ()
#5  0x08110ef4 in mono_runtime_delegate_invoke ()
#6  0x0815285b in ?? ()
#7  0x081c3062 in ?? ()
#8  0x081e1925 in ?? ()
#9  0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0xaa1fbb70 (LWP 7788)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac937 in ?? ()
#4  0x081c7a63 in ?? ()
#5  0x081512f9 in ?? ()
#6  0xafe4da75 in ?? ()
#7  0xafe4d829 in ?? ()
#8  0xafe4d4fd in ?? ()
#9  0xb713c087 in ?? ()
#10 0x08115d2f in mono_runtime_invoke_array ()
#11 0x08115f7e in ?? ()
#12 0x08155043 in ?? ()
#13 0x08155517 in ?? ()
#14 0x081527ea in ?? ()
#15 0x081c3062 in ?? ()
#16 0x081e1925 in ?? ()
#17 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xaa0fab70 (LWP 7789)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac937 in ?? ()
#4  0x081c7a63 in ?? ()
#5  0x081512f9 in ?? ()
#6  0xafe4da75 in ?? ()
#7  0xafe4d829 in ?? ()
#8  0xafe4d4fd in ?? ()
#9  0xb713c087 in ?? ()
#10 0x08115d2f in mono_runtime_invoke_array ()
#11 0x08115f7e in ?? ()
#12 0x08155043 in ?? ()
#13 0x08155517 in ?? ()
#14 0x081527ea in ?? ()
#15 0x081c3062 in ?? ()
#16 0x081e1925 in ?? ()
#17 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xa9ff9b70 (LWP 7790)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb7629b86 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb775d4eb in g_poll () from /lib/libglib-2.0.so.0
#3  0xb77500ac in ?? () from /lib/libglib-2.0.so.0
#4  0xb7750817 in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0xb56b3400 in ?? () from /usr/lib/libORBit-2.so.0
#6  0xb7776def in ?? () from /lib/libglib-2.0.so.0
#7  0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xa9fb8b70 (LWP 7791)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac937 in ?? ()
#4  0x081c7a63 in ?? ()
#5  0x081512f9 in ?? ()
#6  0xafe4da75 in ?? ()
#7  0xafe4d829 in ?? ()
#8  0xafe4d4fd in ?? ()
#9  0xb713c087 in ?? ()
#10 0x08115d2f in mono_runtime_invoke_array ()
#11 0x08115f7e in ?? ()
#12 0x08155043 in ?? ()
#13 0x08155517 in ?? ()
#14 0x081527ea in ?? ()
#15 0x081c3062 in ?? ()
#16 0x081e1925 in ?? ()
#17 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xa9d6db70 (LWP 7796)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f6f5b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6990452 in Mono_Posix_Syscall_read ()
   from /usr/lib/libMonoPosixHelper.so
#3  0xb69cb732 in ?? ()
#4  0xb69d0ae2 in ?? ()
#5  0xb69d0992 in ?? ()
#6  0xaa71e1b2 in ?? ()
#7  0xaa721525 in ?? ()
#8  0xaa713d4f in ?? ()
#9  0xb713c087 in ?? ()
#10 0x08115d2f in mono_runtime_invoke_array ()
#11 0x08115f7e in ?? ()
#12 0x08155043 in ?? ()
#13 0x08155517 in ?? ()
#14 0x081527ea in ?? ()
#15 0x081c3062 in ?? ()
#16 0x081e1925 in ?? ()
#17 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xa9affb70 (LWP 7797)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f7168 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081bfbae in ?? ()
#3  0x0815b32b in ?? ()
#4  0xa9c2fd35 in ?? ()
#5  0xa9c2fb60 in ?? ()
#6  0xa9c61e69 in ?? ()
#7  0xb71426f9 in ?? ()
#8  0x08110ef4 in mono_runtime_delegate_invoke ()
#9  0x0815285b in ?? ()
#10 0x081c3062 in ?? ()
#11 0x081e1925 in ?? ()
#12 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xaf9ffb70 (LWP 7798)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f6f5b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080ca87e in ?? ()
#3  0x080f6893 in ?? ()
#4  <signal handler called>
#5  0xb75dd7a0 in ?? () from /lib/tls/i686/cmov/libc.so.6
#6  0xa99e0cf5 in ?? () from /usr/lib/libmtp.so.8
#7  0xa99e18af in LIBMTP_Create_New_Album () from /usr/lib/libmtp.so.8
#8  0xa9973035 in ?? ()
#9  0xa9972e2c in ?? ()
#10 0xa9972d1a in ?? ()
#11 0xa9972ad2 in ?? ()
#12 0xa99712bb in ?? ()
#13 0xa9970bef in ?? ()
#14 0xa9989acd in ?? ()
#15 0xa9989397 in ?? ()
#16 0xa99889e7 in ?? ()
#17 0xa9988312 in ?? ()
#18 0xa998826b in ?? ()
#19 0xa9987d85 in ?? ()
#20 0xafb851ef in ?? ()
#21 0xafb85189 in ?? ()
#22 0xa9987c09 in ?? ()
#23 0xa9c3a61b in ?? ()
#24 0xb713c087 in ?? ()
#25 0x08115d2f in mono_runtime_invoke_array ()
#26 0x08115f7e in ?? ()
#27 0x08155043 in ?? ()
#28 0x08155517 in ?? ()
#29 0x081527ea in ?? ()
#30 0x081c3062 in ?? ()
#31 0x081e1925 in ?? ()
#32 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#33 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xaa2fcb70 (LWP 7799)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76f4342 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac76c in ?? ()
#3  0x081c728a in ?? ()
#4  0x0814f763 in ?? ()
#5  0xb5911e45 in ?? ()
#6  0xa97f06df in ?? ()
#7  0xa998053d in ?? ()
#8  0xa99803de in ?? ()
#9  0xa997ff2f in ?? ()
#10 0xa999aae9 in ?? ()
#11 0xa9995d20 in ?? ()
#12 0xb71426f9 in ?? ()
#13 0x08110ef4 in mono_runtime_delegate_invoke ()
#14 0x0815285b in ?? ()
#15 0x081c3062 in ?? ()
#16 0x081e1925 in ?? ()
#17 0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xa9e86b70 (LWP 7801)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb76382c6 in epoll_wait () from /lib/tls/i686/cmov/libc.so.6
#2  0x08156292 in ?? ()
#3  0x081527ea in ?? ()
#4  0x081c3062 in ?? ()
#5  0x081e1925 in ?? ()
#6  0xb76ef96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7637a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb75376f0 (LWP 7768)):
#0  0xb77f5430 in __kernel_vsyscall ()
#1  0xb7629b86 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb775d4eb in g_poll () from /lib/libglib-2.0.so.0
#3  0xb77500ac in ?? () from /lib/libglib-2.0.so.0
#4  0xb7750817 in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0xb5b6e3c9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#6  0xafb76290 in ?? ()
#7  0xafb76253 in ?? ()
#8  0xafb75fe5 in ?? ()
#9  0xb6935fad in ?? ()
#10 0xb6935e52 in ?? ()
#11 0xb6935d86 in ?? ()
#12 0xb692e771 in ?? ()
#13 0xb692ba46 in ?? ()
#14 0xb692b9b4 in ?? ()
#15 0x08113b1e in mono_runtime_exec_main ()
#16 0xb692b933 in ?? ()
#17 0xb692b81c in ?? ()
#18 0xb692b6f6 in ?? ()
#19 0xb692b6a0 in ?? ()
#20 0xb692b622 in ?? ()
#21 0xb692b5d3 in ?? ()
#22 0xb692ac92 in ?? ()
#23 0xb713c419 in ?? ()
#24 0xb713c1fb in ?? ()
#25 0x08113b1e in mono_runtime_exec_main ()
#26 0x0811429a in mono_runtime_run_main ()
#27 0x080b3524 in mono_main ()
#28 0x0805ad25 in ?? ()
#29 0xb7580bd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#30 0x0805ac61 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

It looks like the problems start at:

[7 Debug 11:29:28.650] GStreamer pipeline does not run: audioconvert ! novellaacenc bitrate=128000 profile=2 outputformat=0 ! novellqtmux
[7 Debug 11:29:28.663] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[7 Debug 11:29:28.673] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux


Any suggestions?  I'm stumped.

---

### Post by lunatico on 2010-10-31
I just dusted off my old Zen Vision M to start using it on my car and the first thing I did was charge and format it. Now I'm trying to sync my music library with Banshee and I'm having this same problem.
I'll try a few things and if I have success I'll post back.

Did you ever solve this?

Thanks!

---

### Post by lunatico on 2010-10-31
After messing around for a while somehow I broke the firmware and the device wasn't turning on anymore.
So went to Creative's website and downloaded the latest firmware. Loaded it on the device (from a Win XP VM on Virtualbox) and then used Rhythmbox to copy files over.

I copied them in chunks of 500 songs, just because I was paranoid that it could crash if I copied the entire library all at once.

It worked. So maybe it's something Banshee.

---

