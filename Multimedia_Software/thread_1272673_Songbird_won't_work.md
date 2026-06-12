---
title: "Songbird won't work"
date: 2009-09-22
forum: Multimedia Software
---

### Post by mickie.kext on 2009-09-22
I have switched from Ubuntu to Kubuntu today, done fresh install and tried to install my favourite programs. But I got stuck on Songbird. I first downloaded from [here]("http://www.getsongbird.com/") but did not managed to install it. Did not feel like compiling so I grabed deb from [getdeb]("http://www.getdeb.net/release/4461"). It installed fine but when I click on icon, it does not do anything.

When type songbird in terminal I get this:

```
$ songbird 
*** glibc detected *** ././songbird-bin: munmap_chunk(): invalid pointer: 0x00007f3929f9e740 ***
======= Backtrace: =========                                                                    
/lib/libc.so.6[0x7f394c6abcb8]                                                                  
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7f39252c54ce]                                
/usr/lib/libvisual-0.4.so.0[0x7f39252be646]                                                     
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7f39252be7d8]                        
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7f39252cb703]                                  
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7f39254eccb1]                                    
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f3936b9a383]                                    
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x98c)[0x7f3936b9af7d]        
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f3936ba69fb]                                    
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7f3936ba6b7e]      
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f3936b5259b]                                    
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f3936b52a09]                                    
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f3936b52fd7]                                    
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f3936b53568]                                    
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x540)[0x7f3948a50020]                         
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7f3936b51936]               
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7f3936b51a23]                     
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7f39347ceb04]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f39347d65e5]                                      
/usr/share/Songbird/xulrunner/libxul.so[0x7f394a59659f]                                              
/usr/share/Songbird/xulrunner/libxul.so[0x7f394a5960e9]                                              
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f39347e492b]                                      
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f39347e4958]                                      
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f39347e4140]                                      
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f39347d502e]                                      
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7f39347d5601]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f39347d6555]                                              
/usr/share/Songbird/xulrunner/libxul.so[0x7f394a59659f]                                                      
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f3939d0e613]                                         
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f3939d0e650]                                         
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f3939d0df32]                                         
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7f3939cf9154]                                                                                                  
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7f3939cf6729]         
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f3939cf6b17]                                               
/usr/share/Songbird/xulrunner/libxul.so[0x7f394a576eba]                                                            
/usr/share/Songbird/xulrunner/libxul.so[0x7f394a57738c]                                                            
/usr/share/Songbird/xulrunner/libxul.so[0x7f3949e47f86]                                                            
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x177d)[0x7f3949e45c57]                                           
././songbird-bin[0x401417]                                                                                         
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f394c6525a6]                                                             
././songbird-bin[0x401009]                                                                                         
======= Memory map: ========                                                                                       
00400000-00408000 r-xp 00000000 08:03 182034                             /usr/share/Songbird/songbird-bin          
00608000-00609000 rw-p 00008000 08:03 182034                             /usr/share/Songbird/songbird-bin          
00cb4000-00cd5000 rw-p 00cb4000 00:00 0                                  [heap]                                    
7f3923857000-7f3923858000 r-xp 00000000 08:03 49609                      /usr/lib/tls/libnvidia-tls.so.180.44      
7f3923858000-7f3923958000 ---p 00001000 08:03 49609                      /usr/lib/tls/libnvidia-tls.so.180.44      
7f3923958000-7f3923959000 rw-p 00001000 08:03 49609                      /usr/lib/tls/libnvidia-tls.so.180.44      
7f39252ac000-7f39252e9000 r-xp 00000000 08:03 112673                     /usr/lib/libvisual-0.4.so.0.0.0           
7f39252e9000-7f39254e8000 ---p 0003d000 08:03 112673                     /usr/lib/libvisual-0.4.so.0.0.0           
7f39254e8000-7f39254e9000 r--p 0003c000 08:03 112673                     /usr/lib/libvisual-0.4.so.0.0.0           
7f39254e9000-7f39254ea000 rw-p 0003d000 08:03 112673                     /usr/lib/libvisual-0.4.so.0.0.0           
7f39254ea000-7f39254f0000 r-xp 00000000 08:03 112701                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f39254f0000-7f39256ef000 ---p 00006000 08:03 112701                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f39256ef000-7f39256f0000 r--p 00005000 08:03 112701                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f39256f0000-7f39256f1000 rw-p 00006000 08:03 112701                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f39256f1000-7f3925757000 r-xp 00000000 08:03 9743                       /usr/lib/libtag.so.1.5.0                  
7f3925757000-7f3925956000 ---p 00066000 08:03 9743                       /usr/lib/libtag.so.1.5.0                  
7f3925956000-7f3925958000 r--p 00065000 08:03 9743                       /usr/lib/libtag.so.1.5.0                  
7f3925958000-7f3925959000 rw-p 00067000 08:03 9743                       /usr/lib/libtag.so.1.5.0                  
7f3925959000-7f3925964000 r-xp 00000000 08:03 112789                     /usr/lib/gstreamer-0.10/libgsttaglib.so   
7f3925964000-7f3925b63000 ---p 0000b000 08:03 112789                     /usr/lib/gstreamer-0.10/libgsttaglib.so   
7f3925b63000-7f3925b64000 r--p 0000a000 08:03 112789                     /usr/lib/gstreamer-0.10/libgsttaglib.so   
7f3925b64000-7f3925b65000 rw-p 0000b000 08:03 112789                     /usr/lib/gstreamer-0.10/libgsttaglib.so   
7f3925b65000-7f3925baa000 r-xp 00000000 08:03 2428                       /lib/libncursesw.so.5.7                   
7f3925baa000-7f3925da9000 ---p 00045000 08:03 2428                       /lib/libncursesw.so.5.7                   
7f3925da9000-7f3925dad000 r--p 00044000 08:03 2428                       /lib/libncursesw.so.5.7                   
7f3925dad000-7f3925dae000 rw-p 00048000 08:03 2428                       /lib/libncursesw.so.5.7                   
7f3925dae000-7f3925dcc000 r-xp 00000000 08:03 8819                       /usr/lib/libcaca.so.0.99.16               
7f3925dcc000-7f3925fcc000 ---p 0001e000 08:03 8819                       /usr/lib/libcaca.so.0.99.16               
7f3925fcc000-7f3925fcd000 r--p 0001e000 08:03 8819                       /usr/lib/libcaca.so.0.99.16               
7f3925fcd000-7f3926054000 rw-p 0001f000 08:03 8819                       /usr/lib/libcaca.so.0.99.16               
7f3926054000-7f3926058000 rw-p 7f3926054000 00:00 0                                                                
7f3926058000-7f392605b000 r-xp 00000000 08:03 112751                     /usr/lib/gstreamer-0.10/libgstcacasink.so 
7f392605b000-7f392625a000 ---p 00003000 08:03 112751                     /usr/lib/gstreamer-0.10/libgstcacasink.so 
7f392625a000-7f392625b000 r--p 00002000 08:03 112751                     /usr/lib/gstreamer-0.10/libgstcacasink.so 
7f392625b000-7f392625c000 rw-p 00003000 08:03 112751                     /usr/lib/gstreamer-0.10/libgstcacasink.so 
7f392625c000-7f3926273000 r-xp 00000000 08:03 112706                     /usr/lib/gstreamer-0.10/libgsttcp.so      
7f3926273000-7f3926472000 ---p 00017000 08:03 112706                     /usr/lib/gstreamer-0.10/libgsttcp.so      
7f3926472000-7f3926473000 r--p 00016000 08:03 112706                     /usr/lib/gstreamer-0.10/libgsttcp.so      
7f3926473000-7f3926474000 rw-p 00017000 08:03 112706                     /usr/lib/gstreamer-0.10/libgsttcp.so      
7f3926474000-7f3926481000 r-xp 00000000 08:03 123857                     /usr/lib/gstreamer-0.10/libgstpango.so    
7f3926481000-7f3926680000 ---p 0000d000 08:03 123857                     /usr/lib/gstreamer-0.10/libgstpango.so    
7f3926680000-7f3926681000 r--p 0000c000 08:03 123857                     /usr/lib/gstreamer-0.10/libgstpango.so    
7f3926681000-7f3926682000 rw-p 0000d000 08:03 123857                     /usr/lib/gstreamer-0.10/libgstpango.so    
7f3926682000-7f3926686000 r-xp 00000000 08:03 112756                     /usr/lib/gstreamer-0.10/libgstefence.so   
7f3926686000-7f3926885000 ---p 00004000 08:03 112756                     /usr/lib/gstreamer-0.10/libgstefence.so   
7f3926885000-7f3926886000 r--p 00003000 08:03 112756                     /usr/lib/gstreamer-0.10/libgstefence.so   
7f3926886000-7f3926887000 rw-p 00004000 08:03 112756                     /usr/lib/gstreamer-0.10/libgstefence.so   
7f3926887000-7f392689f000 r-xp 00000000 08:03 9724                       /usr/lib/libspeex.so.1.5.0                
7f392689f000-7f3926a9f000 ---p 00018000 08:03 9724                       /usr/lib/libspeex.so.1.5.0                
7f3926a9f000-7f3926aa0000 r--p 00018000 08:03 9724                       /usr/lib/libspeex.so.1.5.0                
7f3926aa0000-7f3926aa1000 rw-p 00019000 08:03 9724                       /usr/lib/libspeex
7f3926aa1000-7f3926aad000 r-xp 00000000 08:03 112788                     /usr/lib/gstreame
7f3926aad000-7f3926cac000 ---p 0000c000 08:03 112788                     /usr/lib/gstreame
7f3926cac000-7f3926cad000 r--p 0000b000 08:03 112788                     /usr/lib/gstreame
7f3926cad000-7f3926cae000 rw-p 0000c000 08:03 112788                     /usr/lib/gstreame
7f3926cae000-7f3926d20000 r-xp 00000000 08:03 112618                     /usr/lib/liboil-0
7f3926d20000-7f3926f1f000 ---p 00072000 08:03 112618                     /usr/lib/liboil-0
7f3926f1f000-7f3926f20000 r--p 00071000 08:03 112618                     /usr/lib/liboil-0
7f3926f20000-7f3926f3b000 rw-p 00072000 08:03 112618                     /usr/lib/liboil-0
7f3926f3b000-7f3926f3d000 rw-p 7f3926f3b000 00:00 0
7f3926f3d000-7f3926faf000 r-xp 00000000 08:03 123834                     /usr/lib/libschro
7f3926faf000-7f39271ae000 ---p 00072000 08:03 123834                     /usr/lib/libschro
7f39271ae000-7f39271af000 r--p 00071000 08:03 123834                     /usr/lib/libschro
7f39271af000-7f39271b1000 rw-p 00072000 08:03 123834                     /usr/lib/libschro
7f39271b1000-7f39271c9000 r-xp 00000000 08:03 123845                     /usr/lib/gstreame
7f39271c9000-7f39273c9000 ---p 00018000 08:03 123845                     /usr/lib/gstreame
7f39273c9000-7f39273ca000 r--p 00018000 08:03 123845                     /usr/lib/gstreame
7f39273ca000-7f39273cc000 rw-p 00019000 08:03 123845                     /usr/lib/gstreame
7f39273cc000-7f39273ee000 r-xp 00000000 08:03 9096                       /usr/lib/libjpeg.
7f39273ee000-7f39275ee000 ---p 00022000 08:03 9096                       /usr/lib/libjpeg.
7f39275ee000-7f39275ef000 rw-p 00022000 08:03 9096                       /usr/lib/libjpeg.
7f39275ef000-7f39275fd000 r-xp 00000000 08:03 112770                     /usr/lib/gstreame
7f39275fd000-7f39277fc000 ---p 0000e000 08:03 112770                     /usr/lib/gstreame
7f39277fc000-7f39277fd000 r--p 0000d000 08:03 112770                     /usr/lib/gstreame
7f39277fd000-7f39277fe000 rw-p 0000e000 08:03 112770                     /usr/lib/gstreametialize GStreamer: Error re-scanning registry , child terminated by signal

```

I have 64-bit Kubuntu, meanwhile, trying to solve problem I installed GNOME (ubuntu-desktop and all dependences) and then even install UbuntuStudio, also via APT. 

I don't have a clue what the problem is:(. I still have old Ubuntu install on separate harddrive and SongBird works fine there both in GNOME and KDE. 

Any help would be apriciated...

---

