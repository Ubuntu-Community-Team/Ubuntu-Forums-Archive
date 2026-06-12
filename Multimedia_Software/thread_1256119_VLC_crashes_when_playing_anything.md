---
title: "VLC crashes when playing anything"
date: 2009-09-02
forum: Multimedia Software
---

### Post by pmooney78 on 2009-09-02
I used to use VLC to play everything ... lately, though, it won't play any media at all. Attempting to play anything (by dragging it to the VLC window or playlist, by selecting it through a menu, or any other way) causes VLC to quit without displaying an error message.

I've tried running VLC (0.9.9a) in a terminal and watching the output, but different files give different error messages (although they all produce the same result: silently quitting).

Here are two output samples. Both of these files play under totem:

```

patrick@liniscient:~$ vlc                                                                                                                                                          
VLC media player 0.9.9a Grishenko                                                                                                                                                  
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team                                                                        
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'                        
[00000001] main libvlc debug: translation test: code is "C"                                                                                                                        
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU                                                                                                 
[00000001] main libvlc debug: looking for memcpy module: 3 candidates                                                                                                              
[00000001] main libvlc debug: using memcpy module "memcpymmxext"                                                                                                                   
[00000372] main interaction debug: thread 3080154000 (Interaction control) created at priority 0 (interface/interaction.c:382)                                                     
[00000374] main input debug: Creating an input for 'Media Library'                                                                                                                 
[00000374] main input debug: Input is a meta file: disabling unneeded options                                                                                                      
[00000374] main input debug: `file/xspf-open:///home/patrick/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/patrick/.local/share/vlc/ml.xspf'         
[00000374] main input debug: creating access 'file' path='/home/patrick/.local/share/vlc/ml.xspf'                                                                                  
[00000375] main access debug: looking for access module: 3 candidates                                                                                                              
[00000375] access_file access debug: opening file `/home/patrick/.local/share/vlc/ml.xspf'                                                                                         
[00000375] main access debug: using access module "access_file"                                                                                                                    
[00000375] main access debug: TIMER module_Need() : 1.049 ms - Total 1.049 ms / 1 intvls (Avg 1.049 ms)                                                                            
[00000380] main stream debug: Using AStream*Stream                                                                                                                                 
[00000380] main stream debug: pre-buffering...                                                                                                                                     
[00000380] main stream debug: received first data for our buffer                                                                                                                   
[00000374] main input debug: creating demux: access='file' demux='xspf-open' path='/home/patrick/.local/share/vlc/ml.xspf'                                                         
[00000381] main demux debug: looking for demux module: 1 candidate                                                                                                                 
[00000381] playlist demux debug: using XSPF playlist reader                                                                                                                        
[00000381] main demux debug: using demux module "playlist"                                                                                                                         
[00000381] main demux debug: TIMER module_Need() : 0.579 ms - Total 0.579 ms / 1 intvls (Avg 0.579 ms)                                                                             
[00000374] main input debug: `file/xspf-open:///home/patrick/.local/share/vlc/ml.xspf' successfully opened                                                                         
[00000396] main xml debug: looking for xml module: 2 candidates                                                                                                                    
[00000396] main xml debug: using xml module "xml"                                                                                                                                  
[00000396] main xml debug: TIMER module_Need() : 1.726 ms - Total 1.726 ms / 1 intvls (Avg 1.726 ms)                                                                               
[00000381] playlist demux debug: parsed 0 tracks successfully                                                                                                                      
[00000396] main xml debug: removing module "xml"                                                                                                                                   
[00000374] main input debug: EOF reached                                                                                                                                           
[00000374] main input debug: control type=1                                                                                                                                        
[00000381] main demux debug: removing module "playlist"                                                                                                                            
[00000375] main access debug: removing module "access_file"                                                                                                                        
[00000374] main input debug: TIMER input launching for 'Media Library' : 6.054 ms - Total 6.054 ms / 1 intvls (Avg 6.054 ms)                                                       
[00000398] main preparser debug: waiting for thread initialization                                                                                                                 
[00000398] main preparser debug: thread started                                                                                                                                    
[00000398] main preparser debug: thread 3071761296 (preparser) created at priority 0 (playlist/thread.c:79)                                                                        
[00000399] main fetcher debug: thread started                                                                                                                                      
[00000399] main fetcher debug: waiting for thread initialization                                                                                                                   
[00000399] main fetcher debug: thread 3057605520 (fetcher) created at priority 0 (playlist/thread.c:108)                                                                           
[00000373] main playlist debug: thread started                                                                                                                                     
[00000373] main playlist debug: waiting for thread initialization                                                                                                                  
[00000373] main playlist debug: rebuilding array of current - root Playlist                                                                                                        
[00000373] main playlist debug: rebuild done - 0 items, index -1                                                                                                                   
[00000373] main playlist debug: thread 3049212816 (playlist) created at priority 0 (playlist/thread.c:117)                                                                         
[00000400] main interface debug: looking for interface module: 1 candidate                                                                                                         
[00000400] main interface debug: using interface module "hotkeys"                                                                                                                  
[00000400] main interface debug: TIMER module_Need() : 0.666 ms - Total 0.666 ms / 1 intvls (Avg 0.666 ms)                                                                         
[00000400] main interface debug: thread started                                                                                                                                    
[00000400] main interface debug: thread 3040820112 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000402] main interface debug: looking for interface module: 1 candidate                                                                                                         
[00000372] main interaction debug: thread started                                                                                                                                  
[00000402] main interface debug: using interface module "inhibit"                                                                                                                  
[00000402] main interface debug: TIMER module_Need() : 3.626 ms - Total 3.626 ms / 1 intvls (Avg 3.626 ms)                                                                         
[00000402] main interface debug: thread started                                                                                                                                    
[00000402] main interface debug: thread 3032427408 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000404] main interface debug: looking for interface module: 1 candidate                                                                                                         
[00000404] main interface debug: using interface module "screensaver"                                                                                                              
[00000404] main interface debug: TIMER module_Need() : 2.510 ms - Total 2.510 ms / 1 intvls (Avg 2.510 ms)                                                                         
[00000404] main interface debug: thread started                                                                                                                                    
[00000404] main interface debug: thread 3024034704 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000406] main interface debug: looking for interface module: 22 candidates                                                                                                       
[00000406] main interface debug: using interface module "signals"                                                                                                                  
[00000406] main interface debug: TIMER module_Need() : 2.101 ms - Total 2.101 ms / 1 intvls (Avg 2.101 ms)                                                                         
[00000406] main interface debug: thread started                                                                                                                                    
[00000406] main interface debug: thread 3007249296 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.                                                                           
[00000408] main interface debug: looking for interface module: 4 candidates                                                                                                        
[00000408] main interface debug: using interface module "qt4"                                                                                                                      
[00000408] main interface debug: TIMER module_Need() : 300.048 ms - Total 300.048 ms / 1 intvls (Avg 300.048 ms)                                                                   
[00000408] main interface debug: thread started                                                                                                                                    
[00000408] main interface debug: thread 2984328080 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000408] qt4 interface debug: Error while initializing qt-specific localization                                                                                                  
[00000373] main playlist debug: adding item `indiana_jones_crystal_skull_TS_English_AD1.avi' ( /media/Externa/unloading-dock/DVD-rips/ready/indiana_jones_crystal_skull_TS_English_AD1.avi )                                                                                                                                                                          
[00000373] main playlist debug: rebuilding array of current - root Playlist                                                                                                        
[00000373] main playlist debug: rebuild done - 1 items, index -1                                                                                                                   
[00000373] main playlist debug: starting new item                                                                                                                                  
[00000373] main playlist debug: processing request item indiana_jones_crystal_skull_TS_English_AD1.avi node null skip 0                                                            
[00000373] main playlist debug: resyncing on indiana_jones_crystal_skull_TS_English_AD1.avi                                                                                        
[00000373] main playlist debug: indiana_jones_crystal_skull_TS_English_AD1.avi is at 0                                                                                             
[00000373] main playlist debug: creating new input thread                                                                                                                          
[00000411] main input debug: Creating an input for 'indiana_jones_crystal_skull_TS_English_AD1.avi'                                                                                
[00000411] main input debug: waiting for thread initialization                                                                                                                     
[00000411] main input debug: thread started                                                                                                                                        
[00000411] main input debug: thread 2963286928 (input) created at priority 10 (input/input.c:370)                                                                                  
[00000408] qt4 interface debug: Updating the stream status: 3                                                                                                                      
[00000411] main input debug: `/media/Externa/unloading-dock/DVD-rips/ready/indiana_jones_crystal_skull_TS_English_AD1.avi' gives access `' demux `' path `/media/Externa/unloading-dock/DVD-rips/ready/indiana_jones_crystal_skull_TS_English_AD1.avi'                                                                                                                
[00000411] main input debug: creating demux: access='' demux='' path='/media/Externa/unloading-dock/DVD-rips/ready/indiana_jones_crystal_skull_TS_English_AD1.avi'                 
[00000412] main demux debug: looking for access_demux module: 3 candidates                                                                                                         
[00000412] main demux debug: TIMER module_Need() : 395.172 ms - Total 395.172 ms / 1 intvls (Avg 395.172 ms)                                                                       
[00000411] main input debug: creating access '' path='/media/Externa/unloading-dock/DVD-rips/ready/indiana_jones_crystal_skull_TS_English_AD1.avi'                                 
[00000417] main access debug: looking for access module: 7 candidates                                                                                                              
[00000417] vcd access debug: trying .cue file: /media/Externa/unloading-dock/DVD-rips/ready/indiana_jones_crystal_skull_TS_English_AD1.cue                                         
[00000417] vcd access debug: could not find .cue file                                                                                                                              
[00000408] qt4 interface debug: New Event: type 1103                                                                                                                               
[00000408] qt4 interface debug: Updating the stream status: 1                                                                                                                      
[00000417] access_file access debug: opening file `/media/Externa/unloading-dock/DVD-rips/ready/indiana_jones_crystal_skull_TS_English_AD1.avi'                                    
[00000417] main access debug: using access module "access_file"                                                                                                                    
[00000417] main access debug: TIMER module_Need() : 156.439 ms - Total 156.439 ms / 1 intvls (Avg 156.439 ms)                                                                      
[00000408] qt4 interface debug: New Event: type 1103                                                                                                                               
[00000408] qt4 interface debug: Updating the stream status: 2                                                                                                                      
[00000420] main stream debug: Using AStream*Stream                                                                                                                                 
[00000420] main stream debug: pre-buffering...                                                                                                                                     
[00000420] main stream debug: received first data for our buffer                                                                                                                   
[00000420] main stream debug: pre-buffering done 98301 bytes in 0s - 232 kbytes/s                                                                                                  
[00000411] main input debug: creating demux: access='' demux='' path='/media/Externa/unloading-dock/DVD-rips/ready/indiana_jones_crystal_skull_TS_English_AD1.avi'                 
[00000421] main demux debug: looking for demux module: 60 candidates                                                                                                               
[00000420] avi stream debug: found Chunk fourcc:46464952 (RIFF) size:1368462114 pos:0                                                                                              
[00000420] avi stream debug: found LIST chunk: 'AVI '                                                                                                                              
[00000420] avi stream debug: <list 'AVI '>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:8830 pos:12                                                                                                   
[00000420] avi stream debug: found LIST chunk: 'hdrl'                                                                                                                              
[00000420] avi stream debug: <list 'hdrl'>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:68697661 (avih) size:56 pos:24                                                                                                     
[00000420] avi stream debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED 608x288                                                                                               
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4244 pos:88                                                                                                   
[00000420] avi stream debug: found LIST chunk: 'strl'                                                                                                                              
[00000420] avi stream debug: <list 'strl'>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:100                                                                                                    
[00000420] avi stream debug: strh: type:vids handler:0x64697678 samplesize:0 25.00fps                                                                                              
[00000420] avi stream debug: found Chunk fourcc:66727473 (strf) size:40 pos:164                                                                                                    
[00000420] avi stream debug: strf: video:XVID 608x288 planes:1 12bpp                                                                                                               
[00000420] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:212                                                                                                  
[00000420] avi stream debug: </list 'strl'>                                                                                                                                        
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4234 pos:4340                                                                                                 
[00000420] avi stream debug: found LIST chunk: 'strl'                                                                                                                              
[00000420] avi stream debug: <list 'strl'>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:4352                                                                                                   
[00000420] avi stream debug: strh: type:auds handler:0x00000000 samplesize:0 38.28fps                                                                                              
[00000420] avi stream debug: found Chunk fourcc:66727473 (strf) size:30 pos:4416                                                                                                   
[00000420] avi stream debug: strf: audio:0x0055 channels:2 44100Hz 0bits/sample 158kb/s                                                                                            
[00000420] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:4454                                                                                                 
[00000420] avi stream debug: </list 'strl'>                                                                                                                                        
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:260 pos:8582                                                                                                  
[00000420] avi stream debug: found LIST chunk: 'odml'                                                                                                                              
[00000420] avi stream debug: <list 'odml'>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:686c6d64 (dmlh) size:248 pos:8594                                                                                                  
[00000420] avi stream warning: unknown chunk (not loaded)                                                                                                                          
[00000420] avi stream debug: </list 'odml'>                                                                                                                                        
[00000420] avi stream debug: </list 'hdrl'>                                                                                                                                        
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:56 pos:8850                                                                                                   
[00000420] avi stream debug: found LIST chunk: 'INFO'                                                                                                                              
[00000420] avi stream debug: <list 'INFO'>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:54465349 (ISFT) size:44 pos:8862                                                                                                   
[00000420] avi stream debug: ISFT: software : VirtualDubMod 1.5.10.2 (build 2540/release)                                                                                          
[00000420] avi stream debug: </list 'INFO'>                                                                                                                                        
[00000420] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1318 pos:8914                                                                                                 
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:1361677594 pos:10240                                                                                          
[00000420] avi stream debug: skipping movi chunk                                                                                                                                   
[00000420] avi stream debug: found Chunk fourcc:31786469 (idx1) size:6774272 pos:1361687842                                                                                        
[00000420] avi stream debug: idx1: index entry:423392                                                                                                                              
[00000420] avi stream debug: </list 'AVI '>                                                                                                                                        
[00000420] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1230 pos:1368462122                                                                                           
[00000420] avi stream debug: * LIST-root size:1368463360 pos:0                                                                                                                     
[00000420] avi stream debug:      + RIFF-AVI  size:1368462114 pos:0                                                                                                                
[00000420] avi stream debug:      |    + LIST-hdrl size:8830 pos:12                                                                                                                
[00000420] avi stream debug:      |    |    + avih size:56 pos:24                                                                                                                  
[00000420] avi stream debug:      |    |    + LIST-strl size:4244 pos:88                                                                                                           
[00000420] avi stream debug:      |    |    |    + strh size:56 pos:100                                                                                                            
[00000420] avi stream debug:      |    |    |    + strf size:40 pos:164                                                                                                            
[00000420] avi stream debug:      |    |    |    + JUNK size:4120 pos:212                                                                                                          
[00000420] avi stream debug:      |    |    + LIST-strl size:4234 pos:4340                                                                                                         
[00000420] avi stream debug:      |    |    |    + strh size:56 pos:4352                                                                                                           
[00000420] avi stream debug:      |    |    |    + strf size:30 pos:4416                                                                                                           
[00000420] avi stream debug:      |    |    |    + JUNK size:4120 pos:4454                                                                                                         
[00000420] avi stream debug:      |    |    + LIST-odml size:260 pos:8582                                                                                                          
[00000420] avi stream debug:      |    |    |    + dmlh size:248 pos:8594                                                                                                          
[00000420] avi stream debug:      |    + LIST-INFO size:56 pos:8850                                                                                                                
[00000420] avi stream debug:      |    |    + ISFT size:44 pos:8862                                                                                                                
[00000420] avi stream debug:      |    + JUNK size:1318 pos:8914                                                                                                                   
[00000420] avi stream debug:      |    + LIST-movi size:1361677594 pos:10240                                                                                                       
[00000420] avi stream debug:      |    + idx1 size:6774272 pos:1361687842                                                                                                          
[00000420] avi stream debug:      + JUNK size:1230 pos:1368462122                                                                                                                  
[00000421] avi demux debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED                                                                                                        
[00000421] avi demux debug: stream[0] rate:25 scale:1 samplesize:0                                                                                                                 
[00000421] avi demux debug: stream[0] video(XVID) 608x288 12bpp 25.000000fps                                                                                                       
[00000411] main input debug: selecting program id=0                                                                                                                                
[00000408] qt4 interface debug: New Event: type 1108                                                                                                                               
[00000421] avi demux debug: stream[1] rate:44100 scale:1152 samplesize:0                                                                                                           
[00000421] avi demux debug: stream[1] audio(0x55) 2 channels 44100Hz 0bits                                                                                                         
[00000421] avi demux debug: stream[0] created 167266 index entries                                                                                                                 
[00000421] avi demux debug: stream[1] created 256126 index entries                                                                                                                 
[00000421] avi demux debug: stream[0] length:6690 (based on index)                                                                                                                 
[00000421] avi demux debug: stream[1] length:6690 (based on index)                                                                                                                 
[00000421] main demux debug: using demux module "avi"                                                                                                                              
[00000421] main demux debug: TIMER module_Need() : 990.538 ms - Total 990.538 ms / 1 intvls (Avg 990.538 ms)                                                                       
[00000411] main input debug: looking for a subtitle file in /media/Externa/unloading-dock/DVD-rips/ready/                                                                          
[00000423] main decoder debug: looking for decoder module: 30 candidates                                                                                                           
[00000423] avcodec decoder debug: libavcodec initialized (interface 3412992 )                                                                                                      
[00000423] avcodec decoder debug: using direct rendering                                                                                                                           
[00000423] avcodec decoder debug: ffmpeg codec (MPEG-4 Video) started                                                                                                              
[00000423] main decoder debug: using decoder module "avcodec"                                                                                                                      
[00000423] main decoder debug: TIMER module_Need() : 1142.533 ms - Total 1142.533 ms / 1 intvls (Avg 1142.533 ms)                                                                  
[00000423] main decoder debug: thread started                                                                                                                                      
[00000423] main decoder debug: thread 2908081040 (decoder) created at priority 0 (input/decoder.c:217)                                                                             
[00000456] main decoder debug: looking for decoder module: 30 candidates                                                                                                           
[00000456] main decoder debug: using decoder module "mpeg_audio"                                                                                                                   
[00000456] main decoder debug: TIMER module_Need() : 0.575 ms - Total 0.575 ms / 1 intvls (Avg 0.575 ms)                                                                           
[00000456] main decoder debug: thread started                                                                                                                                      
[00000456] main decoder debug: thread 2899688336 (decoder) created at priority 5 (input/decoder.c:217)                                                                             
[00000411] main input debug: `/media/Externa/unloading-dock/DVD-rips/ready/indiana_jones_crystal_skull_TS_English_AD1.avi' successfully opened                                     
[00000421] avi demux debug: old:0 < new 0                                                                                                                                          
[00000421] avi demux debug: old:0 < new 0                                                                                                                                          
[00000411] main input debug: control type=1                                                                                                                                        
[00000408] qt4 interface debug: New Event: type 1103                                                                                                                               
[00000408] qt4 interface debug: Updating the stream status: 3                                                                                                                      
[00000456] mpeg_audio decoder debug: MPGA channels:2 samplerate:44100 bitrate:160                                                                                                  
[00000456] main decoder debug: no aout present, spawning one                                                                                                                       
[00000457] main audio output debug: looking for audio output module: 5 candidates                                                                                                  
[00000423] avcodec decoder debug: Invalid and inefficient vfw-avi packed B frames detected                                                                                         
 (mpeg4@0x8d37240)                                                                                                                                                                 
[00000423] main decoder debug: no usable vout present, spawning one                                                                                                                
[00000458] main video output debug: window size: 608x288                                                                                                                           
[00000458] main video output debug: looking for video output module: 7 candidates                                                                                                  
[00000458] xvideo video output debug: adaptor 0, port 81, format 0x32315659 (YV12) planar                                                                                          
[00000457] alsa audio output debug: opening ALSA device `default'                                                                                                                  
[00000457] main audio output debug: thread 2815245200 (aout) created at priority 15 (alsa.c:687)                                                                                   
[00000457] main audio output debug: using audio output module "alsa"                                                                                                               
[00000457] main audio output debug: thread started                                                                                                                                 
[00000457] main audio output debug: TIMER module_Need() : 577.356 ms - Total 577.356 ms / 1 intvls (Avg 577.356 ms)                                                                
[00000457] main audio output debug: output 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes                                                                                          
[00000457] main audio output debug: mixer 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes                                                                                           
[00000457] main audio output debug: no need for any filter                                                                                                                         
[00000457] main audio output debug: looking for audio mixer module: 3 candidates                                                                                                   
[00000457] main audio output debug: using audio mixer module "float32_mixer"                                                                                                       
[00000457] main audio output debug: TIMER module_Need() : 56.326 ms - Total 56.326 ms / 1 intvls (Avg 56.326 ms)                                                                   
[00000457] main audio output debug: input 'mpga' 44100 Hz Stereo frame=1152 samples/1053 bytes                                                                                     
[00000457] main audio output debug: filter(s) 'mpga'->'fl32' 44100 Hz->44100 Hz Stereo->Stereo                                                                                     
[00000462] main audio output debug: looking for audio filter module: 24 candidates                                                                                                 
[00000463] main window debug: looking for vout window module: 1 candidate                                                                                                          
[00000462] main audio output debug: using audio filter module "mpgatofixed32"                                                                                                      
[00000462] main audio output debug: TIMER module_Need() : 111.314 ms - Total 111.314 ms / 1 intvls (Avg 111.314 ms)                                                                
[00000457] main audio output debug: found a filter for the whole conversion                                                                                                        
[00000457] main audio output debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Stereo->Stereo                                                                                     
[00000466] main audio output debug: looking for audio filter module: 24 candidates                                                                                                 
[00000466] main audio output debug: using audio filter module "bandlimited_resampler"                                                                                              
[00000466] main audio output debug: TIMER module_Need() : 175.978 ms - Total 175.978 ms / 1 intvls (Avg 175.978 ms)                                                                
[00000457] main audio output debug: found a filter for the whole conversion                                                                                                        
[00000457] main audio output warning: PTS is out of range (691071), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (664993), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (638899), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (612802), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (586707), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (560610), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (534515), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (508419), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (482350), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (456256), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (430161), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (404066), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (377969), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (351873), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (325776), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (299680), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (273583), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (247488), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (221392), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (195296), dropping buffer                                                                                                
[00000457] message audio output warning: message queue overflowed                                                                                                                  
[00000457] main audio output warning: PTS is out of range (169201), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (143115), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (117020), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (90924), dropping buffer                                                                                                 
[00000457] main audio output warning: PTS is out of range (64829), dropping buffer                                                                                                 
[00000457] main audio output warning: PTS is out of range (38733), dropping buffer                                                                                                 
[00000457] main audio output warning: PTS is out of range (12637), dropping buffer                                                                                                 
[00000457] main audio output warning: PTS is out of range (-13459), dropping buffer                                                                                                
[00000457] main audio output warning: PTS is out of range (-39555), dropping buffer                                                                                                
[00000457] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                             
[00000457] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                             
[00000457] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                             
[00000457] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                             
[00000457] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                             
[00000457] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                             
[00000457] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                             
[00000457] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                             
[00000457] main audio output warning: output date isn't PTS date, requesting resampling (111080)                                                                                   
[00000457] main audio output warning: buffer is 111080 late, triggering upsampling                                                                                                 
[00000457] alsa audio output debug: recovered from buffer underrun
[00000457] main audio output debug: audio output is starving (267220), playing silence
[00000463] main window debug: TIMER module_Need() : 647.885 ms - Total 647.885 ms / 1 intvls (Avg 647.885 ms)
[00000463] main window debug: no window provider available
[00000458] xvideo video output debug: XShm video extension v1.1 (without pixmaps, opcode: 139)
[00000457] main audio output warning: output date isn't PTS date, requesting resampling (64485)
[00000458] xvideo video output debug: Window manager supports NetWM
[00000458] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000458] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000458] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000458] main video output debug: using video output module "xvideo"
[00000458] main video output debug: TIMER module_Need() : 1588.369 ms - Total 1588.369 ms / 1 intvls (Avg 1588.369 ms)
[00000458] main video output debug: thread started
[00000458] main video output debug: got 8 direct buffer(s)
[00000458] main video output debug: picture in 608x288 (0,0,608x288), chroma I420, ar 911999:432000, sar 1:1
[00000458] main video output debug: picture user 608x288 (0,0,608x288), chroma I420, ar 911999:432000, sar 1:1
[00000458] main video output debug: picture out 608x288 (0,0,608x288), chroma I420, ar 911999:432000, sar 1:1
[00000458] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000457] main audio output warning: audio drift is too big (175179), dropping buffer
[00000457] main audio output warning: audio drift is too big (149057), dropping buffer
[00000458] main video output debug: waiting for thread initialization
[00000458] main video output debug: thread 2803891088 (video output) created at priority 15 (video_output/video_output.c:502)
[00000408] qt4 interface debug: New Event: type 1109
[00000457] main audio output warning: audio drift is too big (122934), dropping buffer
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

```

and 

```

patrick@liniscient:~$ vlc                                                                                                                                                          
VLC media player 0.9.9a Grishenko                                                                                                                                                  
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team                                                                        
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'                        
[00000001] main libvlc debug: translation test: code is "C"                                                                                                                        
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU                                                                                                 
[00000001] main libvlc debug: looking for memcpy module: 3 candidates                                                                                                              
[00000001] main libvlc debug: using memcpy module "memcpymmxext"                                                                                                                   
[00000372] main interaction debug: thread started                                                                                                                                  
[00000372] main interaction debug: thread 3079822224 (Interaction control) created at priority 0 (interface/interaction.c:382)                                                     
[00000374] main input debug: Creating an input for 'Media Library'                                                                                                                 
[00000374] main input debug: Input is a meta file: disabling unneeded options                                                                                                      
[00000374] main input debug: `file/xspf-open:///home/patrick/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/patrick/.local/share/vlc/ml.xspf'         
[00000374] main input debug: creating access 'file' path='/home/patrick/.local/share/vlc/ml.xspf'                                                                                  
[00000375] main access debug: looking for access module: 3 candidates                                                                                                              
[00000375] access_file access debug: opening file `/home/patrick/.local/share/vlc/ml.xspf'                                                                                         
[00000375] main access debug: using access module "access_file"                                                                                                                    
[00000375] main access debug: TIMER module_Need() : 30.277 ms - Total 30.277 ms / 1 intvls (Avg 30.277 ms)                                                                         
[00000380] main stream debug: Using AStream*Stream                                                                                                                                 
[00000380] main stream debug: pre-buffering...                                                                                                                                     
[00000380] main stream debug: received first data for our buffer                                                                                                                   
[00000374] main input debug: creating demux: access='file' demux='xspf-open' path='/home/patrick/.local/share/vlc/ml.xspf'                                                         
[00000381] main demux debug: looking for demux module: 1 candidate                                                                                                                 
[00000381] playlist demux debug: using XSPF playlist reader                                                                                                                        
[00000381] main demux debug: using demux module "playlist"                                                                                                                         
[00000381] main demux debug: TIMER module_Need() : 16.469 ms - Total 16.469 ms / 1 intvls (Avg 16.469 ms)                                                                          
[00000374] main input debug: `file/xspf-open:///home/patrick/.local/share/vlc/ml.xspf' successfully opened                                                                         
[00000396] main xml debug: looking for xml module: 2 candidates                                                                                                                    
[00000396] main xml debug: using xml module "xml"                                                                                                                                  
[00000396] main xml debug: TIMER module_Need() : 33.241 ms - Total 33.241 ms / 1 intvls (Avg 33.241 ms)                                                                            
[00000381] playlist demux debug: parsed 0 tracks successfully                                                                                                                      
[00000396] main xml debug: removing module "xml"                                                                                                                                   
[00000374] main input debug: EOF reached                                                                                                                                           
[00000374] main input debug: control type=1                                                                                                                                        
[00000381] main demux debug: removing module "playlist"                                                                                                                            
[00000375] main access debug: removing module "access_file"                                                                                                                        
[00000374] main input debug: TIMER input launching for 'Media Library' : 65.350 ms - Total 65.350 ms / 1 intvls (Avg 65.350 ms)                                                    
[00000398] main preparser debug: waiting for thread initialization                                                                                                                 
[00000398] main preparser debug: thread started                                                                                                                                    
[00000398] main preparser debug: thread 3071429520 (preparser) created at priority 0 (playlist/thread.c:79)                                                                        
[00000399] main fetcher debug: waiting for thread initialization                                                                                                                   
[00000399] main fetcher debug: thread started                                                                                                                                      
[00000399] main fetcher debug: thread 3057273744 (fetcher) created at priority 0 (playlist/thread.c:108)                                                                           
[00000373] main playlist debug: waiting for thread initialization                                                                                                                  
[00000373] main playlist debug: thread started                                                                                                                                     
[00000373] main playlist debug: rebuilding array of current - root Playlist                                                                                                        
[00000373] main playlist debug: rebuild done - 0 items, index -1                                                                                                                   
[00000373] main playlist debug: thread 3048881040 (playlist) created at priority 0 (playlist/thread.c:117)                                                                         
[00000400] main interface debug: looking for interface module: 1 candidate                                                                                                         
[00000400] main interface debug: using interface module "hotkeys"                                                                                                                  
[00000400] main interface debug: TIMER module_Need() : 22.083 ms - Total 22.083 ms / 1 intvls (Avg 22.083 ms)                                                                      
[00000400] main interface debug: thread 3040488336 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000400] main interface debug: thread started                                                                                                                                    
[00000402] main interface debug: looking for interface module: 1 candidate                                                                                                         
[00000402] main interface debug: using interface module "inhibit"                                                                                                                  
[00000402] main interface debug: TIMER module_Need() : 26.363 ms - Total 26.363 ms / 1 intvls (Avg 26.363 ms)                                                                      
[00000402] main interface debug: thread started                                                                                                                                    
[00000402] main interface debug: thread 3032095632 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000404] main interface debug: looking for interface module: 1 candidate                                                                                                         
[00000404] main interface debug: using interface module "screensaver"                                                                                                              
[00000404] main interface debug: TIMER module_Need() : 8.011 ms - Total 8.011 ms / 1 intvls (Avg 8.011 ms)                                                                         
[00000404] main interface debug: thread started                                                                                                                                    
[00000404] main interface debug: thread 3023702928 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000406] main interface debug: looking for interface module: 22 candidates                                                                                                       
[00000406] main interface debug: using interface module "signals"                                                                                                                  
[00000406] main interface debug: TIMER module_Need() : 8.637 ms - Total 8.637 ms / 1 intvls (Avg 8.637 ms)                                                                         
[00000406] main interface debug: thread started                                                                                                                                    
[00000406] main interface debug: thread 3006917520 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.                                                                           
[00000408] main interface debug: looking for interface module: 4 candidates                                                                                                        
[00000408] main interface debug: using interface module "qt4"                                                                                                                      
[00000408] main interface debug: TIMER module_Need() : 593.340 ms - Total 593.340 ms / 1 intvls (Avg 593.340 ms)                                                                   
[00000408] main interface debug: thread 2983996304 (interface) created at priority 0 (interface/interface.c:168)                                                                   
[00000408] main interface debug: thread started                                                                                                                                    
[00000408] qt4 interface debug: Error while initializing qt-specific localization                                                                                                  
[00000373] main playlist debug: adding item `Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi' ( /media/Externa/unloading-dock/DVD-rips/ready/Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi )                                                                                                                        
[00000373] main playlist debug: rebuilding array of current - root Playlist                                                                                                        
[00000373] main playlist debug: rebuild done - 1 items, index -1                                                                                                                   
[00000373] main playlist debug: starting new item                                                                                                                                  
[00000373] main playlist debug: processing request item Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi node null skip 0                                   
[00000373] main playlist debug: resyncing on Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi                                                               
[00000373] main playlist debug: Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi is at 0                                                                    
[00000373] main playlist debug: creating new input thread                                                                                                                          
[00000411] main input debug: Creating an input for 'Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi'                                                       
[00000411] main input debug: waiting for thread initialization                                                                                                                     
[00000411] main input debug: thread started                                                                                                                                        
[00000411] main input debug: thread 2961177488 (input) created at priority 10 (input/input.c:370)                                                                                  
[00000408] qt4 interface debug: Updating the stream status: 3                                                                                                                      
[00000411] main input debug: `/media/Externa/unloading-dock/DVD-rips/ready/Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi' gives access `' demux `' path `/media/Externa/unloading-dock/DVD-rips/ready/Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi'                                                              
[00000411] main input debug: creating demux: access='' demux='' path='/media/Externa/unloading-dock/DVD-rips/ready/Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi'                                                                                                                                                                           
[00000412] main demux debug: looking for access_demux module: 3 candidates                                                                                                         
[00000412] main demux debug: TIMER module_Need() : 154.425 ms - Total 154.425 ms / 1 intvls (Avg 154.425 ms)                                                                       
[00000411] main input debug: creating access '' path='/media/Externa/unloading-dock/DVD-rips/ready/Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi'        
[00000417] main access debug: looking for access module: 7 candidates                                                                                                              
[00000417] vcd access debug: trying .cue file: /media/Externa/unloading-dock/DVD-rips/ready/Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.cue                
[00000417] vcd access debug: could not find .cue file                                                                                                                              
[00000417] access_file access debug: opening file `/media/Externa/unloading-dock/DVD-rips/ready/Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi'           
[00000417] main access debug: using access module "access_file"                                                                                                                    
[00000417] main access debug: TIMER module_Need() : 107.699 ms - Total 107.699 ms / 1 intvls (Avg 107.699 ms)                                                                      
[00000420] main stream debug: Using AStream*Stream                                                                                                                                 
[00000420] main stream debug: pre-buffering...                                                                                                                                     
[00000420] main stream debug: received first data for our buffer                                                                                                                   
[00000420] main stream debug: pre-buffering done 1408981 bytes in 0s - 56488 kbytes/s                                                                                              
[00000411] main input debug: creating demux: access='' demux='' path='/media/Externa/unloading-dock/DVD-rips/ready/Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi'                                                                                                                                                                           
[00000421] main demux debug: looking for demux module: 60 candidates                                                                                                               
[00000420] avi stream debug: found Chunk fourcc:46464952 (RIFF) size:736219354 pos:0                                                                                               
[00000420] avi stream debug: found LIST chunk: 'AVI '                                                                                                                              
[00000420] avi stream debug: <list 'AVI '>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:306 pos:12                                                                                                    
[00000420] avi stream debug: found LIST chunk: 'hdrl'                                                                                                                              
[00000420] avi stream debug: <list 'hdrl'>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:68697661 (avih) size:56 pos:24                                                                                                     
[00000420] avi stream debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED 616x336                                                                                               
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:116 pos:88                                                                                                    
[00000420] avi stream debug: found LIST chunk: 'strl'                                                                                                                              
[00000420] avi stream debug: <list 'strl'>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:100                                                                                                    
[00000420] avi stream debug: strh: type:vids handler:0x44495658 samplesize:0 23.98fps                                                                                              
[00000420] avi stream debug: found Chunk fourcc:66727473 (strf) size:40 pos:164                                                                                                    
[00000420] avi stream debug: strf: video:DX50 616x336 planes:1 12bpp                                                                                                               
[00000420] avi stream debug: </list 'strl'>                                                                                                                                        
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:106 pos:212                                                                                                   
[00000420] avi stream debug: found LIST chunk: 'strl'                                                                                                                              
[00000420] avi stream debug: <list 'strl'>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:224                                                                                                    
[00000420] avi stream debug: strh: type:auds handler:0x00000000 samplesize:336 41.67fps                                                                                            
[00000420] avi stream debug: found Chunk fourcc:66727473 (strf) size:30 pos:288                                                                                                    
[00000420] avi stream debug: strf: audio:0x0055 channels:2 48000Hz 0bits/sample 109kb/s                                                                                            
[00000420] avi stream debug: </list 'strl'>                                                                                                                                        
[00000420] avi stream debug: </list 'hdrl'>                                                                                                                                        
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:56 pos:326                                                                                                    
[00000420] avi stream debug: found LIST chunk: 'INFO'                                                                                                                              
[00000420] avi stream debug: <list 'INFO'>                                                                                                                                         
[00000420] avi stream debug: found Chunk fourcc:54465349 (ISFT) size:44 pos:338                                                                                                    
[00000420] avi stream debug: ISFT: software : VirtualDubMod 1.5.10.1 (build 2366/release)                                                                                          
[00000420] avi stream debug: </list 'INFO'>                                                                                                                                        
[00000420] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:7794 pos:390                                                                                                  
[00000420] avi stream debug: found Chunk fourcc:5453494c (LIST) size:730854498 pos:8192                                                                                            
[00000420] avi stream debug: skipping movi chunk                                                                                                                                   
[00000420] avi stream debug: found Chunk fourcc:31786469 (idx1) size:5356656 pos:730862698                                                                                         
[00000420] avi stream debug: idx1: index entry:334791                                                                                                                              
[00000420] avi stream debug: </list 'AVI '>                                                                                                                                        
[00000420] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1814 pos:736219362                                                                                            
[00000420] avi stream debug: * LIST-root size:736221184 pos:0                                                                                                                      
[00000420] avi stream debug:      + RIFF-AVI  size:736219354 pos:0                                                                                                                 
[00000420] avi stream debug:      |    + LIST-hdrl size:306 pos:12                                                                                                                 
[00000420] avi stream debug:      |    |    + avih size:56 pos:24                                                                                                                  
[00000420] avi stream debug:      |    |    + LIST-strl size:116 pos:88                                                                                                            
[00000420] avi stream debug:      |    |    |    + strh size:56 pos:100                                                                                                            
[00000420] avi stream debug:      |    |    |    + strf size:40 pos:164                                                                                                            
[00000420] avi stream debug:      |    |    + LIST-strl size:106 pos:212                                                                                                           
[00000420] avi stream debug:      |    |    |    + strh size:56 pos:224                                                                                                            
[00000420] avi stream debug:      |    |    |    + strf size:30 pos:288                                                                                                            
[00000420] avi stream debug:      |    + LIST-INFO size:56 pos:326                                                                                                                 
[00000420] avi stream debug:      |    |    + ISFT size:44 pos:338                                                                                                                 
[00000420] avi stream debug:      |    + JUNK size:7794 pos:390                                                                                                                    
[00000420] avi stream debug:      |    + LIST-movi size:730854498 pos:8192                                                                                                         
[00000420] avi stream debug:      |    + idx1 size:5356656 pos:730862698                                                                                                           
[00000420] avi stream debug:      + JUNK size:1814 pos:736219362                                                                                                                   
[00000421] avi demux debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED                                                                                                        
[00000421] avi demux debug: stream[0] rate:2997 scale:125 samplesize:0                                                                                                             
[00000421] avi demux debug: stream[0] video(DX50) 616x336 12bpp 23.976000fps                                                                                                       
[00000411] main input debug: selecting program id=0                                                                                                                                
[00000421] avi demux debug: stream[1] rate:14000 scale:336 samplesize:336                                                                                                          
[00000421] avi demux debug: stream[1] audio(0x55) 2 channels 48000Hz 0bits                                                                                                         
[00000421] avi demux debug: stream[0] created 167401 index entries                                                                                                                 
[00000421] avi demux debug: stream[1] created 167390 index entries                                                                                                                 
[00000421] avi demux debug: stream[0] length:6982 (based on index)                                                                                                                 
[00000421] avi demux debug: stream[1] length:6982 (based on index)                                                                                                                 
[00000421] main demux debug: using demux module "avi"                                                                                                                              
[00000421] main demux debug: TIMER module_Need() : 154.837 ms - Total 154.837 ms / 1 intvls (Avg 154.837 ms)                                                                       
[00000411] main input debug: looking for a subtitle file in /media/Externa/unloading-dock/DVD-rips/ready/                                                                          
[00000423] main decoder debug: looking for decoder module: 30 candidates                                                                                                           
[00000408] qt4 interface debug: New Event: type 1103                                                                                                                               
[00000408] qt4 interface debug: Updating the stream status: 2                                                                                                                      
[00000408] qt4 interface debug: New Event: type 1103                                                                                                                               
[00000408] qt4 interface debug: New Event: type 1108                                                                                                                               
[00000423] avcodec decoder debug: libavcodec initialized (interface 3412992 )                                                                                                      
[00000423] avcodec decoder debug: using direct rendering                                                                                                                           
[00000423] avcodec decoder debug: ffmpeg codec (MPEG-4 Video) started                                                                                                              
[00000423] main decoder debug: using decoder module "avcodec"                                                                                                                      
[00000423] main decoder debug: TIMER module_Need() : 239.369 ms - Total 239.369 ms / 1 intvls (Avg 239.369 ms)                                                                     
[00000423] main decoder debug: thread started                                                                                                                                      
[00000423] main decoder debug: thread 2910567312 (decoder) created at priority 0 (input/decoder.c:217)                                                                             
[00000456] main decoder debug: looking for decoder module: 30 candidates                                                                                                           
[00000456] main decoder debug: using decoder module "mpeg_audio"                                                                                                                   
[00000456] main decoder debug: TIMER module_Need() : 0.406 ms - Total 0.406 ms / 1 intvls (Avg 0.406 ms)                                                                           
[00000456] main decoder debug: thread started                                                                                                                                      
[00000456] main decoder debug: thread 2902174608 (decoder) created at priority 5 (input/decoder.c:217)                                                                             
[00000411] main input debug: `/media/Externa/unloading-dock/DVD-rips/ready/Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[2007]DvDrip[Eng]-aXXo.avi' successfully opened            
[00000421] avi demux debug: old:0 < new 0                                                                                                                                          
[00000411] main input debug: control type=1                                                                                                                                        
[00000408] qt4 interface debug: New Event: type 1103                                                                                                                               
[00000408] qt4 interface debug: Updating the stream status: 3                                                                                                                      
[00000456] mpeg_audio decoder debug: MPGA channels:2 samplerate:48000 bitrate:112                                                                                                  
[00000456] main decoder debug: no aout present, spawning one                                                                                                                       
[00000457] main audio output debug: looking for audio output module: 5 candidates                                                                                                  
[00000423] avcodec decoder debug: disabling direct rendering
[00000423] main decoder debug: no usable vout present, spawning one
[00000458] main video output debug: window size: 616x336
[00000458] main video output debug: looking for video output module: 7 candidates
[00000458] xvideo video output debug: adaptor 0, port 81, format 0x32315659 (YV12) planar
[00000461] main window debug: looking for vout window module: 1 candidate
[00000461] main window debug: TIMER module_Need() : 177.456 ms - Total 177.456 ms / 1 intvls (Avg 177.456 ms)
[00000461] main window debug: no window provider available
[00000458] xvideo video output debug: XShm video extension v1.1 (without pixmaps, opcode: 139)
[00000458] xvideo video output debug: Window manager supports NetWM
[00000458] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000458] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000458] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000458] main video output debug: using video output module "xvideo"
[00000458] main video output debug: TIMER module_Need() : 641.248 ms - Total 641.248 ms / 1 intvls (Avg 641.248 ms)
[00000458] main video output debug: thread started
[00000458] main video output debug: waiting for thread initialization
[00000458] main video output debug: got 8 direct buffer(s)
[00000458] main video output debug: picture in 616x336 (0,0,616x336), chroma I420, ar 11:6, sar 1:1
[00000458] main video output debug: picture user 616x336 (0,0,616x336), chroma I420, ar 11:6, sar 1:1
[00000458] main video output debug: picture out 616x336 (0,0,616x336), chroma I420, ar 11:6, sar 1:1
[00000458] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000458] main video output debug: thread 2892106640 (video output) created at priority 15 (video_output/video_output.c:502)
[00000408] qt4 interface debug: New Event: type 1109
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

```

I've tried removing and reinstalling VLC, including using the "complete removal (including configuration files)" option in Synaptic. I've also tried deleting the ~/.local/share/vlc directory, too.

VLC has run on this computer before, but I recently borked the hard drive trying to repartition while running Windows (stupid ...). I rebuilt the Ubuntu installation and VLC now refuses to run. I can't for the life of me figure out what's going on.

Currently running Ubuntu 9.04 on a Dell Latitude D420 laptop with a 1.2 GHz Core Duo processors and 1 GB of RAM. Any help is much appreciated.

---

### Post by jerrrys on 2009-09-02
have you seen this?

[https://lists.ubuntu.com/archives/universe-bugs/2009-May/091614.html](https://lists.ubuntu.com/archives/universe-bugs/2009-May/091614.html)

[https://lists.ubuntu.com/archives/universe-bugs/2009-May/091668.html](https://lists.ubuntu.com/archives/universe-bugs/2009-May/091668.html)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/374258](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/374258)

---

### Post by pmooney78 on 2009-09-02
I hadn't, actually.

The first two don't seem relevant because they describe bugs that affect other applications ... I can use other applications to play video but VLC crashes silently. The third link might describe the same problem; in fact, it also happened to me when I upgraded from 8.10 to 9.04. I suppose, in that case, the solution is just to use other applications to play video until the driver issue is fixed?

---

### Post by khelben1979 on 2009-09-02
Download directly [from the VLC homepage]("http://www.videolan.org/vlc/") instead.

---

### Post by pmooney78 on 2009-09-02
Well, damn. That doesn't work either. There seem to be no .deb packages available, and alien fails to convert other package types with a variety of errors.

Guess I'm stuck using Totem for now ...

---

### Post by mc4man on 2009-09-03
You may want to give karmic a try when it releases, should offer better performance overall, particularly with intel graphics, (if that's what you have.

In the meantime you could try a different video output with vlc than the default (Xv

Open vlc -> tools -> preferences, click on the video icon and in the "output" box change the drop down from default  to "X11 Video Output"

Click save or enter on keyboard to set change

May help, may not

---

### Post by Conu on 2009-09-22
I had this problem after installing Cairo-dock. [html]http://www.cairo-dock.org/bg_topic.php?t=2156&pos=0[/html]

---

### Post by pmooney78 on 2009-10-03
I don't use Cairo Dock, so that's not the problem for me ...

I actually went back to Ubuntu 8.10 (there were other motivations involved, too), which fixed that problem for me.

---

### Post by pmooney78 on 2010-08-04
and it doesn't seem to be a problem under 9.10. Guess I'll chalk it up as an issue with 9.04, which I'm no longer using.

---

