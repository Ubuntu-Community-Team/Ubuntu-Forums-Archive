---
title: "banshee crashes when trying to play anything"
date: 2010-02-27
forum: Multimedia Software
---

### Post by evanct on 2010-02-27
This is 9.10 recently upgraded from 9.04

So today banshee stopped working properly, every time I try to play any media file, audio or video, banshee immediately crashes with this error:

"Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application."

The full output:

```
[Info  04:02:24.185] Running Banshee 1.5.1: [Ubuntu karmic (development branch) (linux-gnu, i486) @ 2009-10-19 14:46:07 UTC]

(/usr/lib/banshee-1/Banshee.exe:3839): GLib-WARNING **: g_set_prgname() called multiple times
[Info  04:02:25.881] All services are started 1.50449s                                       
[Info  04:02:27.774] nereid Client Started                                                   

Native stacktrace:

        banshee-1 [0x80c8824]
        banshee-1 [0x805d448]
        [0xa6b410]           
        /usr/lib/gstreamer-0.10/libgstbluetooth.so [0x24c015b]
        /usr/lib/gstreamer-0.10/libgstbluetooth.so [0x24c0b41]
        /usr/lib/libgstbase-0.10.so.0 [0x11d2d0f]             
        /usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x2606005]
        /usr/lib/libgstreamer-0.10.so.0 [0x2609614]                               
        /usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x2605260]   
        /usr/lib/gstreamer-0.10/libgstbluetooth.so [0x24c157c]                    
        /usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x2606005]
        /usr/lib/libgstreamer-0.10.so.0 [0x2609614]                               
        /usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x2605260]   
        /usr/lib/libgstreamer-0.10.so.0 [0x25f4477]                               
        /usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x2606005]
        /usr/lib/libgstreamer-0.10.so.0 [0x2609614]                               
        /usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x2605260]   
        /usr/lib/gstreamer-0.10/libgstgconfelements.so [0x83938fe]                
        /usr/lib/gstreamer-0.10/libgstgconfelements.so [0x8390be7]                
        /usr/lib/gstreamer-0.10/libgstgconfelements.so [0x8390f3d]                
        /usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x2606005]
        /usr/lib/libgstreamer-0.10.so.0 [0x2609614]                               
        /usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x2605260]   
        /usr/lib/libgstreamer-0.10.so.0 [0x25f4477]                               
        /usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x2606005]
        /usr/lib/libgstreamer-0.10.so.0 [0x2609614]                               
        /usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x2605260]   
        /usr/lib/libgstreamer-0.10.so.0 [0x25f4477]                               
        /usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x2606005]
        /usr/lib/libgstreamer-0.10.so.0 [0x2609614]                               
        /usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x2605260]   
        /usr/lib/gstreamer-0.10/libgstplaybin.so [0x497b905]                      
        /usr/lib/gstreamer-0.10/libgstplaybin.so [0x497d8d7]                      
        /usr/lib/gstreamer-0.10/libgstplaybin.so [0x4992334]                      
        /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0x8b59fc]
        /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x8a8072]            
        /usr/lib/libgobject-2.0.so.0 [0x8bd7a8]                                    
        /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0x8beb2d]        
        /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x8befb6]                
        /usr/lib/libgstreamer-0.10.so.0(gst_element_no_more_pads+0x8a) [0x26079da] 
        /usr/lib/gstreamer-0.10/libgstdecodebin.so [0x24a075e]                     
        /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0x8b59fc]
        /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x8a8072]            
        /usr/lib/libgobject-2.0.so.0 [0x8bd7a8]                                    
        /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0x8beb2d]        
        /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x8befb6]                
        /usr/lib/libgstreamer-0.10.so.0(gst_element_no_more_pads+0x8a) [0x26079da] 
        /usr/lib/gstreamer-0.10/libgstmatroska.so [0x2591fde]                      
        /usr/lib/gstreamer-0.10/libgstmatroska.so [0x25928c4]                      
        /usr/lib/libgstreamer-0.10.so.0 [0x2646895]                                
        /usr/lib/libgstreamer-0.10.so.0 [0x26481a7]                                
        /lib/libglib-2.0.so.0 [0x18e9af]                                           
        /lib/libglib-2.0.so.0 [0x18d37f]                                           
        /lib/tls/i686/cmov/libpthread.so.0 [0x7ff80e]                              
        /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xba18de]                        

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0xafffeb70 (LWP 3869)]           
[New Thread 0xaf7fdb70 (LWP 3868)]           
[New Thread 0x1d96b70 (LWP 3867)]            
[New Thread 0x29c7b70 (LWP 3866)]            
[New Thread 0xb07ffb70 (LWP 3863)]           
[New Thread 0x20adb70 (LWP 3856)]            
[New Thread 0x6562b70 (LWP 3855)]            
[New Thread 0x2a49b70 (LWP 3853)]            
[New Thread 0x278cb70 (LWP 3849)]            
[New Thread 0x238bb70 (LWP 3848)]            
[New Thread 0x21aeb70 (LWP 3847)]            
[New Thread 0x1595b70 (LWP 3843)]            
[New Thread 0x5b9b70 (LWP 3842)]             
[New Thread 0x448b70 (LWP 3841)]             
0x081a0ef1 in ?? ()                          
  15 Thread 0x448b70 (LWP 3841)  0x00a6b422 in __kernel_vsyscall ()
  14 Thread 0x5b9b70 (LWP 3842)  0x00a6b422 in __kernel_vsyscall ()
  13 Thread 0x1595b70 (LWP 3843)  0x00a6b422 in __kernel_vsyscall ()
  12 Thread 0x21aeb70 (LWP 3847)  0x00a6b422 in __kernel_vsyscall ()
  11 Thread 0x238bb70 (LWP 3848)  0x00a6b422 in __kernel_vsyscall ()
  10 Thread 0x278cb70 (LWP 3849)  0x00a6b422 in __kernel_vsyscall ()
  9 Thread 0x2a49b70 (LWP 3853)  0x00a6b422 in __kernel_vsyscall () 
  8 Thread 0x6562b70 (LWP 3855)  0x00a6b422 in __kernel_vsyscall () 
  7 Thread 0x20adb70 (LWP 3856)  0x00a6b422 in __kernel_vsyscall () 
  6 Thread 0xb07ffb70 (LWP 3863)  0x00a6b422 in __kernel_vsyscall ()
  5 Thread 0x29c7b70 (LWP 3866)  0x00a6b422 in __kernel_vsyscall () 
  4 Thread 0x1d96b70 (LWP 3867)  0x00a6b422 in __kernel_vsyscall () 
  3 Thread 0xaf7fdb70 (LWP 3868)  0x00a6b422 in __kernel_vsyscall ()
  2 Thread 0xafffeb70 (LWP 3869)  0x00a6b422 in __kernel_vsyscall ()
* 1 Thread 0x74e6f0 (LWP 3839)  0x081a0ef1 in ?? ()                 

Thread 15 (Thread 0x448b70 (LWP 3841)):
#0  0x00a6b422 in __kernel_vsyscall () 
#1  0x00807466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a3658 in ?? ()                                               
#3  0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6             

Thread 14 (Thread 0x5b9b70 (LWP 3842)):
#0  0x00a6b422 in __kernel_vsyscall () 
#1  0x00805f75 in sem_wait@@GLIBC_2.1 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0812bb29 in ?? ()                                                         
#3  0x0814f96c in ?? ()                                                         
#4  0x081bf9f2 in ?? ()                                                         
#5  0x081de055 in ?? ()                                                         
#6  0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0       
#7  0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                    

Thread 13 (Thread 0x1595b70 (LWP 3843)):
#0  0x00a6b422 in __kernel_vsyscall ()  
#1  0x00803e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()                                                                    
#3  0x081a84f4 in ?? ()                                                                    
#4  0x081c3dcf in ?? ()                                                                    
#5  0x0814c923 in ?? ()                                                                    
#6  0x00ab9abd in ?? ()                                                                    
#7  0x00ab98d5 in ?? ()                                                                    
#8  0x00ab8e1a in ?? ()                                                                    
#9  0x00223df0 in ?? ()                                                                    
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()                                          
#11 0x0814f9d7 in ?? ()                                                                    
#12 0x081bf9f2 in ?? ()                                                                    
#13 0x081de055 in ?? ()                                                                    
#14 0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                  
#15 0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                               

Thread 12 (Thread 0x21aeb70 (LWP 3847)):
#0  0x00a6b422 in __kernel_vsyscall ()  
#1  0x00803e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()                                                                    
#3  0x081a8577 in ?? ()                                                                    
#4  0x081c4403 in ?? ()                                                                    
#5  0x0814e4a8 in ?? ()                                                                    
#6  0x01fa56cd in ?? ()                                                                    
#7  0x01fa5359 in ?? ()                                                                    
#8  0x01fa4f45 in ?? ()                                                                    
#9  0x00221086 in ?? ()                                                                    
#10 0x08114f4b in mono_runtime_invoke_array ()                                             
#11 0x0811512e in ?? ()                                                                    
#12 0x081520a3 in ?? ()                                                                    
#13 0x08152577 in ?? ()                                                                    
#14 0x0814f96c in ?? ()                                                                    
#15 0x081bf9f2 in ?? ()                                                                    
#16 0x081de055 in ?? ()                                                                    
#17 0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                  
#18 0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                               

Thread 11 (Thread 0x238bb70 (LWP 3848)):
#0  0x00a6b422 in __kernel_vsyscall ()  
#1  0x00803e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()                                                                    
#3  0x081a8577 in ?? ()                                                                    
#4  0x081c4403 in ?? ()                                                                    
#5  0x0814e4a8 in ?? ()                                                                    
#6  0x01fa56cd in ?? ()                                                                    
#7  0x01fa5359 in ?? ()                                                                    
#8  0x01fa4f45 in ?? ()                                                                    
#9  0x00221086 in ?? ()                                                                    
#10 0x08114f4b in mono_runtime_invoke_array ()                                             
#11 0x0811512e in ?? ()                                                                    
#12 0x081520a3 in ?? ()                                                                    
#13 0x08152577 in ?? ()                                                                    
#14 0x0814f96c in ?? ()                                                                    
#15 0x081bf9f2 in ?? ()                                                                    
#16 0x081de055 in ?? ()                                                                    
#17 0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                  
#18 0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                               

Thread 10 (Thread 0x278cb70 (LWP 3849)):
#0  0x00a6b422 in __kernel_vsyscall ()  
#1  0x00803e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()                                                                    
#3  0x081a8577 in ?? ()                                                                    
#4  0x081c4403 in ?? ()                                                                    
#5  0x0814e4a8 in ?? ()                                                                    
#6  0x01fa56cd in ?? ()                                                                    
#7  0x01fa5359 in ?? ()                                                                    
#8  0x01fa4f45 in ?? ()                                                                    
#9  0x00221086 in ?? ()                                                                    
#10 0x08114f4b in mono_runtime_invoke_array ()                                             
#11 0x0811512e in ?? ()                                                                    
#12 0x081520a3 in ?? ()                                                                    
#13 0x08152577 in ?? ()                                                                    
#14 0x0814f96c in ?? ()                                                                    
#15 0x081bf9f2 in ?? ()                                                                    
#16 0x081de055 in ?? ()                                                                    
#17 0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                  
#18 0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                               

Thread 9 (Thread 0x2a49b70 (LWP 3853)):
#0  0x00a6b422 in __kernel_vsyscall () 
#1  0x00b93c96 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x0017354b in IA__g_poll (fds=0x8afed70, nfds=5, timeout=-1) at /build/buildd/glib2.0-2.22.3/glib/gpoll.c:127
#3  0x0016656b in g_main_context_poll (context=0x8b26008, block=<value optimized out>, dispatch=1, self=0x8b0f900)
    at /build/buildd/glib2.0-2.22.3/glib/gmain.c:2904                                                             
#4  g_main_context_iterate (context=0x8b26008, block=<value optimized out>, dispatch=1, self=0x8b0f900)           
    at /build/buildd/glib2.0-2.22.3/glib/gmain.c:2586                                                             
#5  0x00166b9f in IA__g_main_loop_run (loop=0x8b24cb0) at /build/buildd/glib2.0-2.22.3/glib/gmain.c:2799          
#6  0x066c88c0 in ?? () from /usr/lib/libORBit-2.so.0                                                             
#7  0x0018d37f in g_thread_create_proxy (data=0x8b0f900) at /build/buildd/glib2.0-2.22.3/glib/gthread.c:635       
#8  0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                                         
#9  0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                                                      

Thread 8 (Thread 0x6562b70 (LWP 3855)):
#0  0x00a6b422 in __kernel_vsyscall () 
#1  0x00806c8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x00893482 in Mono_Posix_Syscall_read () from /usr/lib/libMonoPosixHelper.so
#3  0x0022e3ca in ?? ()                                                         
#4  0x003fa212 in ?? ()                                                         
#5  0x003fa0c2 in ?? ()                                                         
#6  0x03008fca in ?? ()                                                         
#7  0x075f621d in ?? ()                                                         
#8  0x03000fd0 in ?? ()                                                         
#9  0x00221086 in ?? ()                                                         
#10 0x08114f4b in mono_runtime_invoke_array ()                                  
#11 0x0811512e in ?? ()                                                         
#12 0x081520a3 in ?? ()                                                         
#13 0x08152577 in ?? ()                                                         
#14 0x0814f96c in ?? ()                                                         
#15 0x081bf9f2 in ?? ()                                                         
#16 0x081de055 in ?? ()                                                         
#17 0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0       
#18 0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                    

Thread 7 (Thread 0x20adb70 (LWP 3856)):
#0  0x00a6b422 in __kernel_vsyscall () 
#1  0x00806e98 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081bc73e in ?? ()                                            
#3  0x0815838b in ?? ()                                            
#4  0x0378eae5 in ?? ()                                            
#5  0x0378e928 in ?? ()                                            
#6  0x0378e829 in ?? ()                                            
#7  0x00223df0 in ?? ()                                            
#8  0x0810e6a4 in mono_runtime_delegate_invoke ()                  
#9  0x0814f9d7 in ?? ()                                            
#10 0x081bf9f2 in ?? ()                                            
#11 0x081de055 in ?? ()                                            
#12 0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6             

Thread 6 (Thread 0xb07ffb70 (LWP 3863)):
#0  0x00a6b422 in __kernel_vsyscall ()  
#1  0x00806c8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080c89be in ?? ()                                          
#3  0x0805d448 in ?? ()                                          
#4  <signal handler called>                                      
#5  0x024c015b in ?? () from /usr/lib/gstreamer-0.10/libgstbluetooth.so
#6  0x024c0b41 in ?? () from /usr/lib/gstreamer-0.10/libgstbluetooth.so
#7  0x011d2d0f in ?? () from /usr/lib/libgstbase-0.10.so.0             
#8  0x02606005 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#9  0x02609614 in ?? () from /usr/lib/libgstreamer-0.10.so.0                      
#10 0x02605260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0   
#11 0x024c157c in ?? () from /usr/lib/gstreamer-0.10/libgstbluetooth.so           
#12 0x02606005 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#13 0x02609614 in ?? () from /usr/lib/libgstreamer-0.10.so.0                      
#14 0x02605260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0   
#15 0x025f4477 in ?? () from /usr/lib/libgstreamer-0.10.so.0                      
#16 0x02606005 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#17 0x02609614 in ?? () from /usr/lib/libgstreamer-0.10.so.0                      
#18 0x02605260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0   
#19 0x083938fe in ?? () from /usr/lib/gstreamer-0.10/libgstgconfelements.so       
#20 0x08390be7 in ?? () from /usr/lib/gstreamer-0.10/libgstgconfelements.so       
#21 0x08390f3d in ?? () from /usr/lib/gstreamer-0.10/libgstgconfelements.so       
#22 0x02606005 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#23 0x02609614 in ?? () from /usr/lib/libgstreamer-0.10.so.0                      
#24 0x02605260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0   
#25 0x025f4477 in ?? () from /usr/lib/libgstreamer-0.10.so.0                      
#26 0x02606005 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#27 0x02609614 in ?? () from /usr/lib/libgstreamer-0.10.so.0                      
#28 0x02605260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0   
#29 0x025f4477 in ?? () from /usr/lib/libgstreamer-0.10.so.0                      
#30 0x02606005 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#31 0x02609614 in ?? () from /usr/lib/libgstreamer-0.10.so.0                      
#32 0x02605260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0   
#33 0x0497b905 in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so             
#34 0x0497d8d7 in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so             
#35 0x04992334 in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so             
#36 0x008b59fc in IA__g_cclosure_marshal_VOID__VOID (closure=0x1e03e0, return_value=0x0, n_param_values=1, param_values=0xb0963920, 
    invocation_hint=0xb07feb80, marshal_data=0xb08f6638) at /build/buildd/glib2.0-2.22.3/gobject/gmarshal.c:77                      
#37 0x008a8072 in IA__g_closure_invoke (closure=0xb08d8080, return_value=0x0, n_param_values=1, param_values=0xb0963920,            
    invocation_hint=0xb07feb80) at /build/buildd/glib2.0-2.22.3/gobject/gclosure.c:767                                              
#38 0x008bd7a8 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb08f6038,            
    emission_return=0x0, instance_and_params=0xb0963920) at /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:3247                     
#39 0x008beb2d in IA__g_signal_emit_valist (instance=0xb08f6038, signal_id=281, detail=0,                                           
    var_args=0xb07fed3c "\364OJ\002\364OJ\002\070`\217\260\210\355\177\260^\aJ\002\070`\217\260\300\004T\267\254i\200")             
    at /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:2980                                                                          
#40 0x008befb6 in IA__g_signal_emit (instance=0xb08f6038, signal_id=281, detail=0) at /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:3037
#41 0x026079da in gst_element_no_more_pads () from /usr/lib/libgstreamer-0.10.so.0                                                       
#42 0x024a075e in ?? () from /usr/lib/gstreamer-0.10/libgstdecodebin.so                                                                  
#43 0x008b59fc in IA__g_cclosure_marshal_VOID__VOID (closure=0x268aef8, return_value=0x0, n_param_values=1, param_values=0xb0963a00,     
    invocation_hint=0xb07feee0, marshal_data=0xb08f6038) at /build/buildd/glib2.0-2.22.3/gobject/gmarshal.c:77                           
#44 0x008a8072 in IA__g_closure_invoke (closure=0xb08ea410, return_value=0x0, n_param_values=1, param_values=0xb0963a00,                 
    invocation_hint=0xb07feee0) at /build/buildd/glib2.0-2.22.3/gobject/gclosure.c:767                                                   
#45 0x008bd7a8 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb08eb010,                 
    emission_return=0x0, instance_and_params=0xb0963a00) at /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:3247                          
#46 0x008beb2d in IA__g_signal_emit_valist (instance=0xb08eb010, signal_id=281, detail=0,                                                
    var_args=0xb07ff09c "\364?Z\002\364?Z\002\020\260\216\260x\361\177\260\336\037Y\002\020\260\216\260\300\004T\267")                   
    at /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:2980                                                                               
#47 0x008befb6 in IA__g_signal_emit (instance=0xb08eb010, signal_id=281, detail=0) at /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:3037
#48 0x026079da in gst_element_no_more_pads () from /usr/lib/libgstreamer-0.10.so.0                                                       
#49 0x02591fde in ?? () from /usr/lib/gstreamer-0.10/libgstmatroska.so                                                                   
#50 0x025928c4 in ?? () from /usr/lib/gstreamer-0.10/libgstmatroska.so                                                                   
#51 0x02646895 in ?? () from /usr/lib/libgstreamer-0.10.so.0                                                                             
#52 0x026481a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0                                                                             
#53 0x0018e9af in g_thread_pool_thread_proxy (data=0xb08c62d8) at /build/buildd/glib2.0-2.22.3/glib/gthreadpool.c:265                    
#54 0x0018d37f in g_thread_create_proxy (data=0xb73e2b48) at /build/buildd/glib2.0-2.22.3/glib/gthread.c:635                             
#55 0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                                                                
#56 0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                                                                             

Thread 5 (Thread 0x29c7b70 (LWP 3866)):
#0  0x00a6b422 in __kernel_vsyscall () 
#1  0x00804142 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a83c4 in ?? ()                                                                         
#3  0x081c3c28 in ?? ()                                                                         
#4  0x081525c7 in ?? ()                                                                         
#5  0x0814f96c in ?? ()                                                                         
#6  0x081bf9f2 in ?? ()                                                                         
#7  0x081de055 in ?? ()                                                                         
#8  0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                       
#9  0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                                    

Thread 4 (Thread 0x1d96b70 (LWP 3867)):
#0  0x00a6b422 in __kernel_vsyscall () 
#1  0x00803e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x06e61d71 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so                 
#3  0x02646895 in ?? () from /usr/lib/libgstreamer-0.10.so.0                               
#4  0x026481a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0                               
#5  0x0018e9af in g_thread_pool_thread_proxy (data=0xb1114bf8) at /build/buildd/glib2.0-2.22.3/glib/gthreadpool.c:265
#6  0x0018d37f in g_thread_create_proxy (data=0xb0950af0) at /build/buildd/glib2.0-2.22.3/glib/gthread.c:635         
#7  0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                                            
#8  0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                                                         

Thread 3 (Thread 0xaf7fdb70 (LWP 3868)):
#0  0x00a6b422 in __kernel_vsyscall ()  
#1  0x00803e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x06e61d71 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so                 
#3  0x02646895 in ?? () from /usr/lib/libgstreamer-0.10.so.0                               
#4  0x026481a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0                               
#5  0x0018e9af in g_thread_pool_thread_proxy (data=0xb1114bf8) at /build/buildd/glib2.0-2.22.3/glib/gthreadpool.c:265
#6  0x0018d37f in g_thread_create_proxy (data=0xb09540f0) at /build/buildd/glib2.0-2.22.3/glib/gthread.c:635         
#7  0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                                            
#8  0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                                                         

Thread 2 (Thread 0xafffeb70 (LWP 3869)):
#0  0x00a6b422 in __kernel_vsyscall ()  
#1  0x00803e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x06e61d71 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so                 
#3  0x02646895 in ?? () from /usr/lib/libgstreamer-0.10.so.0                               
#4  0x026481a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0                               
#5  0x0018e9af in g_thread_pool_thread_proxy (data=0xb1114bf8) at /build/buildd/glib2.0-2.22.3/glib/gthreadpool.c:265
#6  0x0018d37f in g_thread_create_proxy (data=0xb095fbc0) at /build/buildd/glib2.0-2.22.3/glib/gthread.c:635         
#7  0x007ff80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0                                            
#8  0x00ba18de in clone () from /lib/tls/i686/cmov/libc.so.6                                                         

Thread 1 (Thread 0x74e6f0 (LWP 3839)):
#0  0x081a0ef1 in ?? ()               
#1  0x081a0fd9 in ?? ()               
#2  0x0807c77f in ?? ()               
#3  0x080614b8 in ?? ()               
#4  0x08062c98 in ?? ()               
#5  0x080d2226 in ?? ()               
#6  0x00117066 in ?? ()               
#7  0x01450f1a in ?? ()               
#8  0x01450e56 in ?? ()               
#9  0x07605814 in ?? ()               
#10 0x07605719 in ?? ()               
#11 0x014518cf in ?? ()               
#12 0x076056fd in ?? ()               
#13 0x01fa3000 in ?? ()               
#14 0x01247ca9 in ?? ()               
#15 0x012479aa in ?? ()               
#16 0x012478d0 in ?? ()               
#17 0x076055b1 in ?? ()               
#18 0x03792176 in ?? ()               
#19 0x07f19816 in ?? ()               
#20 0x07f1978d in ?? ()               
#21 0x004081c6 in ?? ()               
#22 0x00161101 in g_idle_dispatch (source=0x8bb52c0, callback=0xb759e4f0, user_data=0x0) at /build/buildd/glib2.0-2.22.3/glib/gmain.c:4065
#23 0x00162e88 in g_main_dispatch (context=0xb7579368) at /build/buildd/glib2.0-2.22.3/glib/gmain.c:1960                                  
#24 IA__g_main_context_dispatch (context=0xb7579368) at /build/buildd/glib2.0-2.22.3/glib/gmain.c:2513                                    
#25 0x00166730 in g_main_context_iterate (context=0xb7579368, block=<value optimized out>, dispatch=1, self=0x8833d40)                    
    at /build/buildd/glib2.0-2.22.3/glib/gmain.c:2591                                                                                     
#26 0x00166b9f in IA__g_main_loop_run (loop=0xb0a33788) at /build/buildd/glib2.0-2.22.3/glib/gmain.c:2799                                 
#27 0x0523b419 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0                                                                           
#28 0x029f9140 in ?? ()                                                                                                                   
#29 0x029f9103 in ?? ()                                                                                                                   
#30 0x029f8e95 in ?? ()                                                                                                                   
#31 0x00a76fdd in ?? ()                                                                                                                   
#32 0x00a76e8a in ?? ()                                                                                                                   
#33 0x00a76dbe in ?? ()                                                                                                                   
#34 0x004b1169 in ?? ()                                                                                                                   
#35 0x004ae366 in ?? ()                                                                                                                   
#36 0x004ae2d3 in ?? ()                                                                                                                   
#37 0x081112ae in mono_runtime_exec_main ()                                                                                               
#38 0x004ae253 in ?? ()                                                                                                                   
#39 0x004ae13c in ?? ()                                                                                                                   
#40 0x004ae016 in ?? ()                                                                                                                   
#41 0x004adfc0 in ?? ()                                                                                                                   
#42 0x004adf42 in ?? ()                                                                                                                   
#43 0x004adef3 in ?? ()
#44 0x004ad452 in ?? ()
#45 0x002213f9 in ?? ()
#46 0x002211fa in ?? ()
#47 0x081112ae in mono_runtime_exec_main ()
#48 0x081134da in mono_runtime_run_main ()
#49 0x080b19bd in mono_main ()
#50 0x0805aba5 in ?? ()
#51 0x00aebb56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#52 0x0805aae1 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Aborted

```

Only significant change I've made today is installing ubuntu-restricted-extras and installing libdvdread4 as in [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

any ideas?

---

### Post by evanct on 2010-02-27
bump?

---

### Post by strobe on 2010-03-01
I don't even know if I'm getting an error. When I try to play mp4's is just instantly closes. Bump for me too.

---

