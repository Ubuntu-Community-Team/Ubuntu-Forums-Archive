---
title: "WMV wont play"
date: 2010-03-16
forum: Multimedia Software
---

### Post by sting3r on 2010-03-16
Hi everyone,

I ran into this problem that I read about all over the but still couldn't resolve it. I got some CBT WMV's and they just not playing. I installed players, codecs and still can only get sounds (no video). at this point I'm watching them over my 7 VM and really trying to avoid using it.. any ideas? I even tried mplayer over wine...

any help would be sweet.  Thanks!

---

### Post by mc4man on 2010-03-16
Don't know what CBT is (whatever business training..?), but maybe try a player from the terminal that can produce some decent error/info messages

mplayer /path/to/filename
or
vlc -vv /path/to/filename

---

### Post by sting3r on 2010-03-17
Thanks for the reply! VLC  gives me the follwing:

```
VLC media player 1.0.2 Goldeneye                                                               
[0xf60888] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team                                                                                    
[0xf60888] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1ubuntu2.1' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'                                                                              
[0xf60888] main libvlc debug: translation test: code is "C"                                    
[0xf60888] main libvlc debug: checking plugin modules                                          
[0xf60888] main libvlc debug: loading plugins cache file /home/enakdimon/.cache/vlc/plugins-04081e.dat                                                                                        
[0xf60888] main libvlc debug: recursively browsing `/usr/lib/vlc'                              
[0xf60888] main libvlc debug: module bank initialized (380 modules)                            
[0xf60888] main libvlc debug: opening config file (/home/enakdimon/.config/vlc/vlcrc)          
[0xf60888] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU             
[0xf60888] main libvlc debug: looking for memcpy module: 3 candidates                          
[0xf60888] main libvlc debug: using memcpy module "memcpymmxext"                               
[0x1054938] main input debug: Creating an input for 'Media Library'                            
[0x1054938] main input debug: Input is a meta file: disabling unneeded options                 
[0x1054938] main input debug: using timeshift granularity of 50 MBytes                         
[0x1054938] main input debug: using timeshift path '/tmp'                                      
[0x1054938] main input debug: `file/xspf-open:///home/enakdimon/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/enakdimon/.local/share/vlc/ml.xspf'               
[0x1054938] main input debug: creating demux: access='file' demux='xspf-open' path='/home/enakdimon/.local/share/vlc/ml.xspf'                                                                 
[0x1064368] main demux debug: looking for access_demux module: 1 candidate                     
[0x1064368] main demux warning: no access_demux module matching "file" could be loaded         
[0x1064368] main demux debug: TIMER module_need() : 36.163 ms - Total 36.163 ms / 1 intvls (Avg 36.163 ms)                                                                                    
[0x1054938] main input debug: creating access 'file' path='/home/enakdimon/.local/share/vlc/ml.xspf'                                                                                          
[0x1067c38] main access debug: looking for access module: 3 candidates                         
[0x1067c38] access_file access debug: opening file `/home/enakdimon/.local/share/vlc/ml.xspf'  
[0x1067c38] main access debug: using access module "access_file"                               
[0x1067c38] main access debug: TIMER module_need() : 12.676 ms - Total 12.676 ms / 1 intvls (Avg 12.676 ms)                                                                                   
[0x1067e98] main stream debug: Using AStream*Stream                                            
[0x1067e98] main stream debug: pre buffering                                                   
[0x1067e98] main stream debug: received first data after 12 ms                                 
[0x1067e98] main stream debug: pre-buffering done 296 bytes in 0s - 23 kbytes/s                
[0x1066e88] main stream debug: looking for stream_filter module: 4 candidates                  
[0x1066e88] main stream debug: TIMER module_need() : 4.316 ms - Total 4.316 ms / 1 intvls (Avg 4.316 ms)                                                                                      
[0x1070e48] main stream debug: looking for stream_filter module: 1 candidate                   
[0x1070e48] main stream debug: using stream_filter module "stream_filter_record"               
[0x1070e48] main stream debug: TIMER module_need() : 1.212 ms - Total 1.212 ms / 1 intvls (Avg 1.212 ms)                                                                                      
[0x1054938] main input debug: creating demux: access='file' demux='xspf-open' path='/home/enakdimon/.local/share/vlc/ml.xspf'                                                                 
[0x106f458] main demux debug: looking for demux module: 1 candidate                            
[0x106f458] playlist demux debug: using XSPF playlist reader                                   
[0x106f458] main demux debug: using demux module "playlist"                                    
[0x106f458] main demux debug: TIMER module_need() : 15.571 ms - Total 15.571 ms / 1 intvls (Avg 15.571 ms)                                                                                    
[0x1054938] main input debug: `file/xspf-open:///home/enakdimon/.local/share/vlc/ml.xspf' successfully opened                                                                                 
[0x10700b8] main xml debug: looking for xml module: 2 candidates                               
[0x10700b8] main xml debug: using xml module "xml"                                             
[0x10700b8] main xml debug: TIMER module_need() : 1.905 ms - Total 1.905 ms / 1 intvls (Avg 1.905 ms)                                                                                         
[0x106f458] playlist demux debug: parsed 0 tracks successfully                                 
[0x10700b8] main xml debug: removing module "xml"                                              
[0x1054938] main input debug: EOF reached                                                      
[0x106f458] main demux debug: removing module "playlist"                                       
[0x1070e48] main stream debug: removing module "stream_filter_record"                          
[0x1067c38] main access debug: removing module "access_file"                                   
[0x1054938] main input debug: TIMER input launching for 'Media Library' : 85.277 ms - Total 85.277 ms / 1 intvls (Avg 85.277 ms)                                                              
[0x1052288] main playlist debug: Activated                                                     
[0x1066a88] main interface debug: looking for interface module: 1 candidate                    
[0x1052288] main playlist debug: rebuilding array of current - root Playlist                   
[0x1052288] main playlist debug: rebuild done - 0 items, index -1                              
[0x1066a88] main interface debug: using interface module "hotkeys"                             
[0x1066a88] main interface debug: TIMER module_need() : 3.262 ms - Total 3.262 ms / 1 intvls (Avg 3.262 ms)                                                                                   
[0x1066a88] main interface debug: thread started                                               
[0x1066a88] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                                        
[0x1054af8] main interface debug: looking for interface module: 1 candidate                    
[0x1054af8] main interface debug: using interface module "inhibit"                             
[0x1054af8] main interface debug: TIMER module_need() : 10.476 ms - Total 10.476 ms / 1 intvls (Avg 10.476 ms)                                                                                
[0x1054af8] main interface debug: thread started                                               
[0x1054af8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                                        
[0x106f418] main interface debug: looking for interface module: 1 candidate                    
[0x106f418] main interface debug: using interface module "screensaver"                         
[0x106f418] main interface debug: TIMER module_need() : 5.998 ms - Total 5.998 ms / 1 intvls (Avg 5.998 ms)                                                                                   
[0x106f418] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                                        
[0x106f418] main interface debug: thread started                                               
[0x1052288] main playlist debug: adding item `36 - IPV6.wmv' ( 36 - IPV6.wmv )                 
[0x1062c48] main interface debug: looking for interface module: 1 candidate                    
[0x1062c48] main interface debug: using interface module "signals"                             
[0x1062c48] main interface debug: TIMER module_need() : 0.929 ms - Total 0.929 ms / 1 intvls (Avg 0.929 ms)                                                                                   
[0x1062c48] main interface debug: thread started                                               
[0x1062c48] main interface debug: thread ended                                                 
[0x1062c48] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                                        
[0x1071b08] main interface debug: looking for interface module: 1 candidate                    
[0x1071b08] main interface debug: using interface module "globalhotkeys"                       
[0x1071b08] main interface debug: TIMER module_need() : 27.833 ms - Total 27.833 ms / 1 intvls (Avg 27.833 ms)                                                                                
[0x1071b08] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                                        
[0x1071b08] main interface debug: thread started                                               
[0x1071b08] main interface debug: thread ended                                                 
[0xf60888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.                                                                                      
[0x107d928] main interface debug: looking for interface module: 4 candidates                   
[0x107d928] main interface debug: using interface module "qt4"                                 
[0x107d928] main interface debug: TIMER module_need() : 199.435 ms - Total 199.435 ms / 1 intvls (Avg 199.435 ms)                                                                             
[0x107d928] main interface debug: thread started                                               
[0x107d928] main interface debug: thread ended                                                 
[0x107d928] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                                        
[0x1052288] main playlist debug: rebuilding array of current - root Playlist                   
[0x1052288] main playlist debug: rebuild done - 1 items, index -1                              
[0x1052288] main playlist debug: processing request item null node Playlist skip 0             
[0x1052288] main playlist debug: starting new item                                             
[0x1052288] main playlist debug: creating new input thread                                     
[0x107e458] main input debug: Creating an input for '36 - IPV6.wmv'                            
[0x107e458] main input debug: thread (input) created at priority 10 (input/input.c:230)        
[0x107e458] main input debug: thread started                                                   
[0x107e458] main input debug: using timeshift granularity of 50 MBytes                         
[0x107e458] main input debug: using timeshift path '/tmp'                                      
[0x107e458] main input debug: `36 - IPV6.wmv' gives access `' demux `' path `36 - IPV6.wmv'    
[0x107e458] main input debug: creating demux: access='' demux='' path='36 - IPV6.wmv'          
[0x12ef508] main demux debug: looking for access_demux module: 7 candidates                    
[0x107d928] qt4 interface debug: Error while initializing qt-specific localization             
[0x107d928] qt4 interface debug: IM: Setting an input                                          
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x12ef508] main demux debug: TIMER module_need() : 110.869 ms - Total 110.869 ms / 1 intvls (Avg 110.869 ms)                                                                                 
[0x107e458] main input debug: creating access '' path='36 - IPV6.wmv'                          
[0x12f8098] main access debug: looking for access module: 7 candidates                         
[0x12f8098] vcd access debug: trying .cue file: 36 - IPV6.cue                                  
[0x12f8098] vcd access debug: could not find .cue file                                         
[0x12f8098] access_file access debug: opening file `36 - IPV6.wmv'                             
[0x12f8098] main access debug: using access module "access_file"                               
[0x12f8098] main access debug: TIMER module_need() : 63.839 ms - Total 63.839 ms / 1 intvls (Avg 63.839 ms)                                                                                   
[0x1218a18] main stream debug: Using AStream*Stream                                            
[0x1218a18] main stream debug: pre buffering                                                   
[0x1218a18] main stream debug: received first data after 20 ms                                 
[0x1218a18] main stream debug: pre-buffering done 1024 bytes in 0s - 48 kbytes/s               
[0x12f55c8] main stream debug: looking for stream_filter module: 4 candidates                  
[0x12f55c8] main stream debug: TIMER module_need() : 0.305 ms - Total 0.305 ms / 1 intvls (Avg 0.305 ms)                                                                                      
[0x12f55c8] main stream debug: looking for stream_filter module: 1 candidate                   
[0x12f55c8] main stream debug: using stream_filter module "stream_filter_record"               
[0x12f55c8] main stream debug: TIMER module_need() : 0.172 ms - Total 0.172 ms / 1 intvls (Avg 0.172 ms)                                                                                      
[0x107e458] main input debug: creating demux: access='' demux='' path='36 - IPV6.wmv'          
[0x12f2538] main demux debug: looking for demux module: 51 candidates                          
[0x12f55c8] asf stream debug: found object guid: 0x75b22630-0x668e-0x11cf-0xa6d900aa0062ce6c size:3551                                                                                        
[0x12f55c8] asf stream debug: read "header object" subobj:7, reserved1:1, reserved2:2          
[0x12f55c8] asf stream debug: found object guid: 0x8cabdca1-0xa947-0x11cf-0x8ee400c00c205365 size:104                                                                                         
[0x12f55c8] asf stream debug: read "file properties object" file_id:0x47bb777f-0x111d-0x4f93-0xb6514b3dece49c74 file_size:30870777 creation_date:127509753673900000 data_packets_count:21363 play_duration:31563990000 send_duration:31548230000 preroll:3000 flags:2 min_data_packet_size:1444  max_data_packet_size:1444 max_bitrate:295562                                               
[0x12f55c8] asf stream debug: found object guid: 0x5fbf03b5-0xa92e-0x11cf-0x8ee300c00c205365 size:1896                                                                                        
[0x12f55c8] asf stream debug: read "header extension object" reserved1:0xabd3d211-0xa9ba-0x11cf-0x8ee600c00c205365 reserved2:6 header_extension_size:1850                                     
[0x12f55c8] asf stream debug: found object guid: 0x7c4346a9-0xefe0-0x4bfc-0xb229393ede415c85 size:52                                                                                          
[0x12f55c8] asf stream debug: read "language list object" 2 entries                            
[0x12f55c8] asf stream debug:   - 'en-ie'                                                      
[0x12f55c8] asf stream debug:   - 'en-us'                                                      
[0x12f55c8] asf stream debug: found object guid: 0x26f18b5d-0x4584-0x47ec-0x9f5f0e651f0452c9 size:26                                                                                          
[0x12f55c8] asf stream warning: unknown asf object (not loaded)                                
[0x12f55c8] asf stream debug: found object guid: 0xc5f8cbea-0x5baf-0x4877-0x8467aa8c44fa4cca size:346                                                                                         
[0x12f55c8] asf stream debug: read "metadata object" 6 entries                                 
[0x12f55c8] asf stream debug:   - IsVBR=0                                                      
[0x12f55c8] asf stream debug:   - DeviceConformanceTemplate=L2                                 
[0x12f55c8] asf stream debug:   - IsVBR=0                                                      
[0x12f55c8] asf stream debug:   - DeviceConformanceTemplate=@                                  
[0x12f55c8] asf stream debug:   - WM/WMADRCPeakReference=18856                                 
[0x12f55c8] asf stream debug:   - WM/WMADRCAverageReference=886                                
[0x12f55c8] asf stream debug: found object guid: 0x1806d474-0xcadf-0x4509-0xa4ba9aabcb96aae8 size:1168                                                                                        
[0x12f55c8] asf stream warning: unknown asf object (not loaded)                                
[0x12f55c8] asf stream debug: found object guid: 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:88                                                                                          
[0x12f55c8] asf stream debug: read "extended stream properties object":                        
[0x12f55c8] asf stream debug:   - start=0 end=0                                                
[0x12f55c8] asf stream debug:   - data bitrate=32048 buffer=1578 initial fullness=0            
[0x12f55c8] asf stream debug:   - alternate data bitrate=32048 buffer=1578 initial fullness=0  
[0x12f55c8] asf stream debug:   - maximum object size=744                                      
[0x12f55c8] asf stream debug:   - flags=0x2                                                    
[0x12f55c8] asf stream debug:   - stream number=1 language=1                                   
[0x12f55c8] asf stream debug:   - average time per frame=1855664                               
[0x12f55c8] asf stream debug:   - stream name count=0                                          
[0x12f55c8] asf stream debug:   - payload extension system count=0                             
[0x12f55c8] asf stream debug: found object guid: 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:132                                                                                         
[0x12f55c8] asf stream debug: read "extended stream properties object":                        
[0x12f55c8] asf stream debug:   - start=0 end=0                                                
[0x12f55c8] asf stream debug:   - data bitrate=250000 buffer=3000 initial fullness=0           
[0x12f55c8] asf stream debug:   - alternate data bitrate=250000 buffer=3000 initial fullness=0 
[0x12f55c8] asf stream debug:   - maximum object size=35447                                    
[0x12f55c8] asf stream debug:   - flags=0x2                                                    
[0x12f55c8] asf stream debug:   - stream number=2 language=1                                   
[0x12f55c8] asf stream debug:   - average time per frame=1000000                               
[0x12f55c8] asf stream debug:   - stream name count=0                                          
[0x12f55c8] asf stream debug:   - payload extension system count=2                             
[0x12f55c8] asf stream debug: found object guid: 0xd9aade20-0x7c17-0x4f9c-0xbc288555dd98e2a2 size:38                                                                                          
[0x12f55c8] asf stream warning: unknown asf object (not loaded)                                
[0x12f55c8] asf stream debug: found object guid: 0xd2d0a440-0xe307-0x11d2-0x97f000a0c95ea850 size:162                                                                                         
[0x12f55c8] asf stream debug: read "extended content description object"                       
[0x12f55c8] asf stream debug:   - 'WMFSDKVersion' = '9.00.00.2980'                             
[0x12f55c8] asf stream debug:   - 'WMFSDKNeeded' = '0.0.0.0000'                                
[0x12f55c8] asf stream debug:   - 'IsVBR' = 'false'                                            
[0x12f55c8] asf stream debug: found object guid: 0x86d15240-0x311d-0x11d0-0xa3a400a0c90348f6 size:250                                                                                         
[0x12f55c8] asf stream debug: read "codec list object" reserved_guid:0x86d15241-0x311d-0x11d0-0xa3a400a0c90348f6 codec_entries_count:2                                                        
[0x12f55c8] asf stream debug:   - codec[0] audio name:"Windows Media Audio 9" description:" 32 kbps, 44 kHz, mono (A/V) 1-pass CBR" information_length:2                                      
[0x12f55c8] asf stream debug:   - codec[1] video name:"Windows Media Video 9 Screen" description:"" information_length:4                                                                      
[0x12f55c8] asf stream debug: found object guid: 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:114                                                                                         
[0x12f55c8] asf stream debug: read "stream Properties object" stream_type:0xf8699e40-0x5b4d-0x11cf-0xa8fd00805f5c442b error_correction_type:0xbfc3cd50-0x618f-0x11cf-0x8bb200aa00b4e220 time_offset:0 type_specific_data_length:28 error_correction_data_length:8 flags:0x1 stream_number:1  
[0x12f55c8] asf stream debug: found object guid: 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:957                                                                                         
[0x12f55c8] asf stream debug: read "stream Properties object" stream_type:0xbc19efc0-0x5b4d-0x11cf-0xa8fd00805f5c442b error_correction_type:0x20fb5700-0x5b55-0x11cf-0xa8fd00805f5c442b time_offset:0 type_specific_data_length:879 error_correction_data_length:0 flags:0x2 stream_number:2 
[0x12f55c8] asf stream debug: found object guid: 0x7bf875ce-0x468d-0x11d1-0x8d82006097c9a2b2 size:38                                                                                          
[0x12f55c8] asf stream debug: read "stream bitrate properties object"                          
[0x12f55c8] asf stream debug:   - stream=1 bitrate=35143                                       
[0x12f55c8] asf stream debug:   - stream=2 bitrate=260419                                      
[0x12f55c8] asf stream debug: found object guid: 0x75b22636-0x668e-0x11cf-0xa6d900aa0062ce6c size:30848222                                                                                    
[0x12f55c8] asf stream debug: read "data object" file_id:0x47bb777f-0x111d-0x4f93-0xb6514b3dece49c74 total data packet:21363 reserved:257                                                     
[0x12f55c8] asf stream debug: found object guid: 0x33000890-0xe5b1-0x11cf-0x89f400a0c90349cb size:19004                                                                                       
[0x12f55c8] asf stream debug: read "index object" file_id:0x47bb777f-0x111d-0x4f93-0xb6514b3dece49c74 index_entry_time_interval:10000000 max_packet_count:36 index_entry_count:3158           
[0x12f55c8] asf stream debug: + 'Unknown' GUID 0x0-0x0-0x0-0x0000000000000000 size:0pos:0      
[0x12f55c8] asf stream debug:      + 'Header' GUID 0x75b22630-0x668e-0x11cf-0xa6d900aa0062ce6c size:3551pos:0                                                                                 
[0x12f55c8] asf stream debug:      |    + 'File Properties' GUID 0x8cabdca1-0xa947-0x11cf-0x8ee400c00c205365 size:104pos:30                                                                   
[0x12f55c8] asf stream debug:      |    + 'Header Extension' GUID 0x5fbf03b5-0xa92e-0x11cf-0x8ee300c00c205365 size:1896pos:134                                                                
[0x12f55c8] asf stream debug:      |    |    + 'Language List' GUID 0x7c4346a9-0xefe0-0x4bfc-0xb229393ede415c85 size:52pos:180                                                                
[0x12f55c8] asf stream debug:      |    |    + 'Unknown' GUID 0x26f18b5d-0x4584-0x47ec-0x9f5f0e651f0452c9 size:26pos:232                                                                      
[0x12f55c8] asf stream debug:      |    |    + 'Metadata' GUID 0xc5f8cbea-0x5baf-0x4877-0x8467aa8c44fa4cca size:346pos:258                                                                    
[0x12f55c8] asf stream debug:      |    |    + 'Padding' GUID 0x1806d474-0xcadf-0x4509-0xa4ba9aabcb96aae8 size:1168pos:604                                                                    
[0x12f55c8] asf stream debug:      |    |    + 'Extended Stream Properties' GUID 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:88pos:1772                                                  
[0x12f55c8] asf stream debug:      |    |    + 'Extended Stream Properties' GUID 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:132pos:1860                                                 
[0x12f55c8] asf stream debug:      |    |    + 'Unknown' GUID 0xd9aade20-0x7c17-0x4f9c-0xbc288555dd98e2a2 size:38pos:1992                                                                     
[0x12f55c8] asf stream debug:      |    + 'Extended content description' GUID 0xd2d0a440-0xe307-0x11d2-0x97f000a0c95ea850 size:162pos:2030                                                    
[0x12f55c8] asf stream debug:      |    + 'Codec List' GUID 0x86d15240-0x311d-0x11d0-0xa3a400a0c90348f6 size:250pos:2192                                                                      
[0x12f55c8] asf stream debug:      |    + 'Stream Properties' GUID 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:114pos:2442                                                               
[0x12f55c8] asf stream debug:      |    + 'Stream Properties' GUID 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:957pos:2556                                                               
[0x12f55c8] asf stream debug:      |    + 'Stream Bitrate Properties' GUID 0x7bf875ce-0x468d-0x11d1-0x8d82006097c9a2b2 size:38pos:3513                                                        
[0x12f55c8] asf stream debug:      + 'Data' GUID 0x75b22636-0x668e-0x11cf-0xa6d900aa0062ce6c size:30848222pos:3551                                                                            
[0x12f55c8] asf stream debug:      + 'Index' GUID 0x33000890-0xe5b1-0x11cf-0x89f400a0c90349cb size:19004pos:30851773                                                                          
[0x12f2538] asf demux debug: found 2 streams                                                   
[0x107e458] main input debug: selecting program id=0                                           
[0x12f2538] asf demux debug: added new audio stream(codec:0x161,ID:1)                          
[0x12f2538] asf demux debug: added new video stream(ID:2)                                      
[0x12f2538] main demux debug: using demux module "asf"                                         
[0x12f2538] main demux debug: TIMER module_need() : 17.680 ms - Total 17.680 ms / 1 intvls (Avg 17.680 ms)                                                                                    
[0x107e458] main input debug: looking for a subtitle file in /home/enakdimon/CCIE-Study/CCIE/CCIE Certification Package/                                                                      
[0x1f047c8] main decoder debug: looking for decoder module: 31 candidates                      
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x1f047c8] avcodec decoder debug: libavcodec initialized (interface 0x341400)                 
[0x1f047c8] avcodec decoder debug: ffmpeg codec (Windows Media Audio 2) started                
[0x1f047c8] avcodec decoder debug: Using 192000 bytes output buffer                            
[0x1f047c8] main decoder debug: using decoder module "avcodec"                                 
[0x1f047c8] main decoder debug: TIMER module_need() : 243.293 ms - Total 243.293 ms / 1 intvls (Avg 243.293 ms)                                                                               
[0x1f047c8] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)   
[0x1f047c8] main decoder debug: thread started                                                 
[0x12ec848] main decoder debug: looking for decoder module: 31 candidates                      
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x107d928] qt4 interface debug: Updating the geometry                                         
[0x12ec848] main decoder debug: TIMER module_need() : 70.744 ms - Total 70.744 ms / 1 intvls (Avg 70.744 ms)                                                                                  
[COLOR=Red]**[0x12ec848] main decoder error: no suitable decoder module for fourcc `MSS2'.**[/COLOR]                  
VLC probably does not support this sound or video format.                                      
[0x12ec848] main decoder debug: killing decoder fourcc `MSS2', 0 PES in FIFO                   
[0x107e458] main input debug: `36 - IPV6.wmv' successfully opened                              
[0x107e458] main input debug: Buffering 0%                                                     
[0x107e458] main input debug: Buffering 0%                                                     
[0x107e458] main input debug: Buffering 46%                                                    
[0x107e458] main input debug: Stream buffering done (324 ms in 0 ms)                           
[0x1f047c8] avcodec decoder warning: Physical channel configuration not set : guessing         
[0x107e458] main input debug: creating aout                                                    
[0x1f9d128] main audio output debug: looking for audio output module: 4 candidates             
[0x107d928] qt4 interface debug: New caching: 100                                              
[0x107d928] qt4 interface debug: New caching: 100                                              
[0x1f9d128] pulse audio output: No. of Audio Channels: 1                                       
[0x1f9d128] pulse audio output debug: Pulse mainloop started                                   
[0x1f9d128] pulse audio output debug: Pulse stream connected                                   
[0x1f9d128] pulse audio output debug: Pulse initialized successfully                           
[0x1f9d128] pulse audio output debug: Buffer metrics: maxlength=70560, tlength=21168, prebuf=17640, minreq=3528                                                                               
[0x1f9d128] pulse audio output debug: Using sample spec 'float32le 1ch 44100Hz', channel map 'mono'.                                                                                          
[0x1f9d128] pulse audio output debug: Connected to device alsa_output.pci-0000_00_1b.0.analog-stereo (0, not suspended).                                                                      
[0x1f9d128] main audio output debug: using audio output module "pulse"                         
[0x1f9d128] main audio output debug: TIMER module_need() : 100.101 ms - Total 100.101 ms / 1 intvls (Avg 100.101 ms)                                                                          
[0x1f9d128] main audio output debug: output 'fl32' 44100 Hz Mono frame=1 samples/4 bytes       
[0x1f9d128] main audio output debug: mixer 'fl32' 44100 Hz Mono frame=1 samples/4 bytes        
[0x1f9d128] main audio output debug: no need for any filter                                    
[0x1f9d128] main audio output debug: looking for audio mixer module: 3 candidates              
[0x1f9d128] main audio output debug: using audio mixer module "float32_mixer"                  
[0x1f9d128] main audio output debug: TIMER module_need() : 21.095 ms - Total 21.095 ms / 1 intvls (Avg 21.095 ms)                                                                             
[0x1f9d128] main audio output debug: input 's16l' 44100 Hz Mono frame=1 samples/2 bytes        
[0x1fb5b08] main audio filter debug: looking for audio filter module: 1 candidate              
[0x1fb5b08] scaletempo audio filter warning: bad input or output format                        
[0x1fb5b08] scaletempo audio filter warning: input and output formats are not similar          
[0x1fb5b08] main audio filter warning: no audio filter module matching "scaletempo" could be loaded                                                                                           
[0x1fb5b08] main audio filter debug: TIMER module_need() : 2.146 ms - Total 2.146 ms / 1 intvls (Avg 2.146 ms)                                                                                
[0x1fb5b08] main audio filter debug: looking for audio filter module: 1 candidate              
[0x1fb5b08] scaletempo audio filter debug: format: 44100 rate, 1 nch, 4 bps, fl32              
[0x1fb5b08] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search         
[0x1fb5b08] scaletempo audio filter debug: 1.000 scale, 1323.000 stride_in, 1323 stride_out, 1059 standing, 264 overlap, 617 search, 2204 queue, fl32 mode                                    
[0x1fb5b08] main audio filter debug: using audio filter module "scaletempo"                    
[0x1fb5b08] main audio filter debug: TIMER module_need() : 0.725 ms - Total 0.725 ms / 1 intvls (Avg 0.725 ms)                                                                                
[0x1f9d128] main audio output debug: filter(s) 's16l'->'fl32' 44100 Hz->44100 Hz Mono->Mono    
[0x1fb7438] main audio output debug: looking for audio filter module: 24 candidates            
[0x1fb7438] main audio output debug: using audio filter module "converter_float"               
[0x1fb7438] main audio output debug: TIMER module_need() : 56.030 ms - Total 56.030 ms / 1 intvls (Avg 56.030 ms)
[0x1f9d128] main audio output debug: found a filter for the whole conversion
[0x1f9d128] main audio output debug: filter(s) 'fl32'->'fl32' 44100 Hz->44100 Hz Mono->Mono
[0x1fbc6c8] main audio output debug: looking for audio filter module: 24 candidates
[0x1fbc6c8] main audio output debug: using audio filter module "trivial_channel_mixer"
[0x1fbc6c8] main audio output debug: TIMER module_need() : 0.992 ms - Total 0.992 ms / 1 intvls (Avg 0.992 ms)
[0x1f9d128] main audio output debug: found a filter for the whole conversion
[0x1f9d128] main audio output debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Mono->Mono
[0x1fbc4f8] main audio output debug: looking for audio filter module: 24 candidates
[0x1fbc4f8] main audio output debug: using audio filter module "bandlimited_resampler"
[0x1fbc4f8] main audio output debug: TIMER module_need() : 0.451 ms - Total 0.451 ms / 1 intvls (Avg 0.451 ms)
[0x1f9d128] main audio output debug: found a filter for the whole conversion
[0x1f047c8] main decoder debug: End of audio preroll
[0x107e458] main input debug: Decoder buffering done in 185 ms
[0x1f9d128] pulse audio output debug: Pulse stream started
[0x1f9d128] main audio output warning: buffer is 46682 in advance, triggering downsampling
[0x1f9d128] main audio output warning: resampling stopped after 19076870 usec (drift: 14347)

```Doesn't look like it see the codec. mplayer gives me the following:

```
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team                                               
mplayer: could not connect to socket                                                           
mplayer: No such file or directory                                                             
Failed to open LIRC support. You will not be able to use your remote control.                  

Playing 36 - IPV6.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS2]  640x480  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
open: No such file or directory                                        
[MGA] Couldn't open: /dev/mga_vid                                      
open: No such file or directory                                        
[MGA] Couldn't open: /dev/mga_vid                                      
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.            
[VO_3DFX] Unable to open /dev/3dfx.                                    
==========================================================================
Requested video codec family [wmsdmod] (vfm=dmo) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x3253534D.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 32.0 kbit/4.54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  24.3 (24.2) of 3156.0 (52:36.0)  0.4%

MPlayer interrupted by signal 2 in module: play_audio
A:  24.3 (24.2) of 3156.0 (52:36.0)  0.4%

```Any ideas? 

Thanks!

---

### Post by mc4man on 2010-03-17
> Any ideas?
Well you have mss2 video, so vlc, while it can use dmo (w32codecs) is out, mss2 is not supported.

> Selected video codec: [wmsdmod] vfm: dmo (Windows Media Screen Codec 2)

As you can see above mplayer can decode, but only a 32 bit mplayer, if you are using a 64 bit ubuntu, (as it appears you are), then your options are limited...

2 choices are to run a win version of mplayer thru wine or build a 32 bit mplayer, - the first is fairly easy, the latter a bit involved 
(I have both on a 64 bit test install of karmic,  - if you wish to pursue I'll track down some posts, links, notes later - have to get to work

---

### Post by sting3r on 2010-03-17
I grabbed MPUI.2010-03-02.Full-Package.exe and installed it (wine). I can now see video!

Thanks!

---

