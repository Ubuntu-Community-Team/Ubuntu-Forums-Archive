---
title: "Help With Songbird On Kubuntu 9.04"
date: 2009-07-30
forum: Multimedia Software
---

### Post by izizzle on 2009-07-30
I decided to try out Songbird on Kubuntu, after hearing alot of good things about it. I downloaded the Songbird 1.2 DEB and installed it. When I try to run it, I get the following error:

```
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0x00007f94676698b0 ***                      
======= Backtrace: =========                           
/lib/libc.so.6[0x7f949f0f3cb8]                         
/lib/libc.so.6(cfree+0x76)[0x7f949f0f6276]             
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7f94638184ce]                                              
/usr/lib/libvisual-0.4.so.0[0x7f9463811646]            
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7f94638117d8]                                      
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7f946381e703]                                                
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7f9463a3fcb1]                                                  
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f948959a383]                                                  
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x98c)[0x7f948959af7d]                      
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f94895a69fb]                                                  
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7f94895a6b7e]                    
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f948955259b]                                                  
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f9489552a09]                                                  
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f9489552fd7]                                                  
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f9489553568]                                                  
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x540)[0x7f949b450020]                                       
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7f9489551936]                             
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7f9489551a23]                                   
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7f94871ceb04]         
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f94871d65e5]                                               
/usr/share/Songbird/xulrunner/libxul.so[0x7f949cf9659f]
/usr/share/Songbird/xulrunner/libxul.so[0x7f949cf960e9]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f94871e492b]                                               
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f94871e4958]                                               
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f94871e4140]                                               
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f94871d502e]                                               
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7f94871d5601] 
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f94871d6555]                                               
/usr/share/Songbird/xulrunner/libxul.so[0x7f949cf9659f]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f948c70e613]                                          
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f948c70e650]                                          
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f948c70df32]                                          
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7f948c6f9154]                                 
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7f948c6f6729]    
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f948c6f6b17]                                          
/usr/share/Songbird/xulrunner/libxul.so[0x7f949cf76eba]
/usr/share/Songbird/xulrunner/libxul.so[0x7f949cf7738c]
/usr/share/Songbird/xulrunner/libxul.so[0x7f949c847f86]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x177d)[0x7f949c845c57]                                      
././songbird-bin[0x401417]                             
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f949f09a5a6] 
././songbird-bin[0x401009]                             
======= Memory map: ========                           
00400000-00408000 r-xp 00000000 08:02 161353                             /usr/share/Songbird/songbird-bin     
00608000-00609000 rw-p 00008000 08:02 161353                             /usr/share/Songbird/songbird-bin     
01161000-01182000 rw-p 01161000 00:00 0                                  [heap]                               
7f9461daa000-7f9461dab000 r-xp 00000000 08:02 36985                      /usr/lib/tls/libnvidia-tls.so.180.44 
7f9461dab000-7f9461eab000 ---p 00001000 08:02 36985                      /usr/lib/tls/libnvidia-tls.so.180.44 
7f9461eab000-7f9461eac000 rw-p 00001000 08:02 36985                      /usr/lib/tls/libnvidia-tls.so.180.44 
7f94637ff000-7f946383c000 r-xp 00000000 08:02 132738                     /usr/lib/libvisual-0.4.so.0.0.0      
7f946383c000-7f9463a3b000 ---p 0003d000 08:02 132738                     /usr/lib/libvisual-0.4.so.0.0.0      
7f9463a3b000-7f9463a3c000 r--p 0003c000 08:02 132738                     /usr/lib/libvisual-0.4.so.0.0.0      
7f9463a3c000-7f9463a3d000 rw-p 0003d000 08:02 132738                     /usr/lib/libvisual-0.4.so.0.0.0      
7f9463a3d000-7f9463a43000 r-xp 00000000 08:02 132766                     /usr/lib/gstreamer-0.10/libgstlibvisual.so                                                  
7f9463a43000-7f9463c42000 ---p 00006000 08:02 132766                     /usr/lib/gstreamer-0.10/libgstlibvisual.so                                                  
7f9463c42000-7f9463c43000 r--p 00005000 08:02 132766                     /usr/lib/gstreamer-0.10/libgstlibvisual.so                                                  
7f9463c43000-7f9463c44000 rw-p 00006000 08:02 132766                     /usr/lib/gstreamer-0.10/libgstlibvisual.so                                                  
7f9463c44000-7f9463c47000 r-xp 00000000 08:02 116201                     /usr/lib/gstreamer-0.10/libgstdeinterlace.so                                                
7f9463c47000-7f9463e46000 ---p 00003000 08:02 116201                     /usr/lib/gstreamer-0.10/libgstdeinterlace.so                                                
7f9463e46000-7f9463e47000 r--p 00002000 08:02 116201                     /usr/lib/gstreamer-0.10/libgstdeinterlace.so                                                
7f9463e47000-7f9463e48000 rw-p 00003000 08:02 116201                     /usr/lib/gstreamer-0.10/libgstdeinterlace.so                                                
7f9463e48000-7f9463ee1000 r-xp 00000000 08:02 9696                       /usr/lib/libsmbios.so.2.1.0          
7f9463ee1000-7f94640e0000 ---p 00099000 08:02 9696                       /usr/lib/libsmbios.so.2.1.0          
7f94640e0000-7f94640e8000 r--p 00098000 08:02 9696                       /usr/lib/libsmbios.so.2.1.0          
7f94640e8000-7f94640e9000 rw-p 000a0000 08:02 9696                       /usr/lib/libsmbios.so.2.1.0          
7f94640e9000-7f94640f9000 r-xp 00000000 08:02 35063                      /usr/lib/libhal.so.1.0.0             
7f94640f9000-7f94642f8000 ---p 00010000 08:02 35063                      /usr/lib/libhal.so.1.0.0             
7f94642f8000-7f94642f9000 r--p 0000f000 08:02 35063                      /usr/lib/libhal.so.1.0.0             
7f94642f9000-7f94642fa000 rw-p 00010000 08:02 35063                      /usr/lib/libhal.so.1.0.0             
7f94642fa000-7f94642ff000 r-xp 00000000 08:02 132905                     /usr/lib/gstreamer-0.10/libgsthalelements.so                                                
7f94642ff000-7f94644fe000 ---p 00005000 08:02 132905                     /usr/lib/gstreamer-0.10/libgsthalelements.so                                                
7f94644fe000-7f94644ff000 r--p 00004000 08:02 132905                     /usr/lib/gstreamer-0.10/libgsthalelements.so                                                
7f94644ff000-7f9464500000 rw-p 00005000 08:02 132905                     /usr/lib/gstreamer-0.10/libgsthalelements.so                                                
7f9464500000-7f946450a000 r-xp 00000000 08:02 116220                     /usr/lib/gstreamer-0.10/libgstliveadder.so                                                  
7f946450a000-7f9464709000 ---p 0000a000 08:02 116220                     /usr/lib/gstreamer-0.10/libgstliveadder.so                                                  
7f9464709000-7f946470a000 r--p 00009000 08:02 116220                     /usr/lib/gstreamer-0.10/libgstliveadder.so                                                  
7f946470a000-7f946470b000 rw-p 0000a000 08:02 116220                     /usr/lib/gstreamer-0.10/libgstliveadder.so                                                  
7f946470b000-7f9464716000 r-xp 00000000 08:02 8993                       /usr/lib/libgstapp-0.10.so.0.0.0     
7f9464716000-7f9464915000 ---p 0000b000 08:02 8993                       /usr/lib/libgstapp-0.10.so.0.0.0     
7f9464915000-7f9464916000 r--p 0000a000 08:02 8993                       /usr/lib/libgstapp-0.10.so.0.0.0     
7f9464916000-7f9464917000 rw-p 0000b000 08:02 8993                       /usr/lib/libgstapp-0.10.so.0.0.0     
7f9464917000-7f9464918000 r-xp 00000000 08:02 132755                     /usr/lib/gstreamer-0.10/libgstapp.so 
7f9464918000-7f9464b17000 ---p 00001000 08:02 132755                     /usr/lib/gstreamer-0.10/libgstapp.so 
7f9464b17000-7f9464b18000 r--p 00000000 08:02 132755                     /usr/lib/gstreamer-0.10/libgstapp.so 
7f9464b18000-7f9464b19000 rw-p 00001000 08:02 132755                     /usr/lib/gstreamer-0.10/libgstapp.so 
7f9464b19000-7f9464b20000 r-xp 00000000 08:02 116329                     /usr/lib/gstreamer-0.10/libgstx264.so
7f9464b20000-7f9464d1f000 ---p 00007000 08:02 116329                     /usr/lib/gstreamer-0.10/libgstx264.so
7f9464d1f000-7f9464d20000 r--p 00006000 08:02 116329                     /usr/lib/gstreamer-0.10/libgstx264.so
7f9464d20000-7f9464d21000 rw-p 00007000 08:02 116329                     /usr/lib/gstreamer-0.10/libgstx264.so
7f9464d21000-7f9464d26000 r-xp 00000000 08:02 116254                     /usr/lib/gstreamer-0.10/libgstvideosignal.so                                                
7f9464d26000-7f9464f25000 ---p 00005000 08:02 116254                     /usr/lib/gstreamer-0.10/libgstvideosignal.so                                                
7f9464f25000-7f9464f26000 r--p 00004000 08:02 116254                     /usr/lib/gstreamer-0.10/libgstvideosignal.so                                                
7f9464f26000-7f9464f27000 rw-p 00005000 08:02 116254                     /usr/lib/gstreamer-0.10/libgstvideosignal.so                                                
7f9464f27000-7f9464f33000 r-xp 00000000 08:02 132927                     /usr/lib/gstreamer-0.10/libgstspeex.so                                                      
7f9464f33000-7f9465132000 ---p 0000c000 08:02 132927                     /usr/lib/gstreamer-0.10/libgstspeex.so                                                      
7f9465132000-7f9465133000 r--p 0000b000 08:02 132927                     /usr/lib/gstreamer-0.10/libgstspeex.so                                                      
7f9465133000-7f9465134000 rw-p 0000c000 08:02 132927                     /usr/lib/gstreamer-0.10/libgstspeex.so                                                      
7f9465134000-7f9465139000 r-xp 00000000 08:02 116327                     /usr/lib/gstreamer-0.10/libgstfaac.so
7f9465139000-7f9465338000 ---p 00005000 08:02 116327                     /usr/lib/gstreamer-0.10/libgstfaac.so
7f9465338000-7f9465339000 r--p 00004000 08:02 116327                     /usr/lib/gstreamer-0.10/libgstfaac.so
7f9465339000-7f946533a000 rw-p 00005000 08:02 116327                     /usr/lib/gstreamer-0.10/libgstfaac.so
7f946533a000-7f9465342000 r-xp 00000000 08:02 132901                     /usr/lib/gstreamer-0.10/libgstgconfelements.so                                              
7f9465342000-7f9465541000 ---p 00008000 08:02 132901                     /usr/lib/gstreamer-0.10/libgstgconfelements.so                                              
7f9465541000-7f9465542000 r--p 00007000 08:02 132901                     /usr/lib/gstreamer-0.10/libgstgconfelements.so                                              
7f9465542000-7f9465543000 rw-p 00008000 08:02 132901                     /usr/lib/gstreamer-0.10/libgstgconfelements.so                                              
7f9465543000-7f9465547000 r-xp 00000000 08:02 132899                     /usr/lib/gstreamer-0.10/libgstflxdec.so
7f9465547000-7f9465746000 ---p 00004000 08:02 132899                     /usr/lib/gstreamer-0.10/libgstflxdec.so
7f9465746000-7f9465747000 r--p 00003000 08:02 132899                     /usr/lib/gstreamer-0.10/libgstflxdec.so
7f9465747000-7f9465748000 rw-p 00004000 08:02 132899                     /usr/lib/gstreamer-0.10/libgstflxdec.so
7f9465748000-7f946574b000 r-xp 00000000 08:02 116209                     /usr/lib/gstreamer-0.10/libgstfbdevsink.so
7f946574b000-7f946594b000 ---p 00003000 08:02 116209                     /usr/lib/gstreamer-0.10/libgstfbdevsink.so
7f946594b000-7f946594c000 r--p 00003000 08:02 116209                     /usr/lib/gstreamer-0.10/libgstfbdevsink.so
7f946594c000-7f946594d000 rw-p 00004000 08:02 116209                     /usr/lib/gstreamer-0.10/libgstfbdevsink.so
7f946594d000-7f9465962000 r-xp 00000000 08:02 35797                      /usr/lib/libmpeg2.so.0.0.0
7f9465962000-7f9465b61000 ---p 00015000 08:02 35797                      /usr/lib/libmpeg2.so.0.0.0
7f9465b61000-7f9465b62000 rw-p 00014000 08:02 35797                      /usr/lib/libmpeg2.so.0.0.0
7f9465b62000-7f9465b64000 rw-p 7f9465b62000 00:00 0
7f9465b64000-7f9465b6d0

```

Any ideas?

Thanks.

---

### Post by martinbaselier on 2009-07-30
You probably have more chance posing this question with songbird, since it's their error report. Have you tried download the gzipped tar from them? You don't need to compile it, you can just unpack and run it.

---

### Post by vinutux on 2009-07-31
1.1.2 work for me....1.2...not good with ubuntu...coz of ton of problems

some says uninstall libvisual-0.4-plugins may fixing that prob.....there are enough threads here...just search:(

---

### Post by izizzle on 2009-07-31
Thanks guys. I decided to give up on it after trying the .tar version. It gave me a similar error. I'm fine with Amarok...

---

