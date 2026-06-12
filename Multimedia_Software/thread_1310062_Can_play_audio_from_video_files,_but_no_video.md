---
title: "Can play audio from video files, but no video"
date: 2009-11-01
forum: Multimedia Software
---

### Post by WindPower on 2009-11-01
Hi, I'm trying to play video files using VLC 1.0.2 and Dragon Player on Kubuntu 9.10 64-bit. And here's what happens: [http://uppix.net/1/8/5/cfa940d0942e298b19a2733db68b0.png](http://uppix.net/1/8/5/cfa940d0942e298b19a2733db68b0.png)
VLC complains about not being able to decode the video format (it's not always XVID, it's whatever-codec-the-video-file-uses), but can play the audio of the video file. Same with Dragon Player, but it creates a see-through area where the video should be.
I have installed the following packages: libavformat52, libavcodec-extra-52, libavcodec-unstripped-52, and vlc.
I'm using Compiz with the Video playback plugin enabled, on an NVIDIA GeForce 9600M GT :o
I have had this problem in Jaunty too :(

---

### Post by giostark on 2009-11-03
Same situation.
So, tried different solutions.
In your screen i haven't seen cairo-dock but I suggest to reflect about.

> I managed to solve my problem but not sure if it will apply to your situation.
I was running the opengl version of cairo-dock from [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) and it was interfering with the xv and x11 output from vlc and skype. As soon as I ran the cairo version 'cairo-dock -c' the problem went away. 

[http://ubuntuforums.org/showthread.php?p=8211992#post8211992](http://ubuntuforums.org/showthread.php?p=8211992#post8211992)

I just notice that are drivers problems. I'm using from nvidia the 190.42 and all work fine except for  mplayer/kmplayer , dragon player , and for vlc i have to disable something ..
[http://forum.ubuntu-it.org/index.php?topic=330551.msg2539274](http://forum.ubuntu-it.org/index.php?topic=330551.msg2539274)

I have tried also the 150 version on my laptop but they are not able to load composite so i return back to 190.
If i disable on kde the desktop effects the video became black and not transparent.
I think that could be a problem of the composite. 

Also the audio section present several problems ...

---

### Post by WindPower on 2009-11-03
> **giostark said:**
> Same situation.
So, tried different solutions.
In your screen i haven't seen cairo-dock but I suggest to reflect about.


[http://ubuntuforums.org/showthread.php?p=8211992#post8211992](http://ubuntuforums.org/showthread.php?p=8211992#post8211992)

I just notice that are drivers problems. I'm using from nvidia the 190.42 and all work fine except for  mplayer/kmplayer , dragon player , and for vlc i have to disable something ..
[http://forum.ubuntu-it.org/index.php?topic=330551.msg2539274](http://forum.ubuntu-it.org/index.php?topic=330551.msg2539274)

I have tried also the 150 version on my laptop but they are not able to load composite so i return back to 190.
If i disable on kde the desktop effects the video became black and not transparent.
I think that could be a problem of the composite. 

Also the audio section present several problems ...
I do have Cairo-dock installed and running in OpenGL mode (it's auto-hidden), but killing it did not fix the problem. Besides, VLC does say it's a codec problem, not XVideo output, and trying the other output modules of VLC also fails, so it's not Cairo-dock's fault.

---

### Post by fabounet on 2009-11-04
this is a known bug in Qt (VLC and Skype are Qt-based applications)
it's been many months since it has been first noticed, and the Qt devs didn't pay attention to it :-/

you can report this bug on Launchpad or on the Qt's site to urge them to care this bug.

a workaround exists :
```
export XLIB_SKIP_ARGB_VISUALS=1 && vlc 
```

---

### Post by WindPower on 2009-11-04
> **fabounet said:**
> this is a known bug in Qt (VLC and Skype are Qt-based applications)
it's been many months since it has been first noticed, and the Qt devs didn't pay attention to it :-/

you can report this bug on Launchpad or on the Qt's site to urge them to care this bug.

a workaround exists :
```
export XLIB_SKIP_ARGB_VISUALS=1 && vlc 
```
Same thing, it says the same error.
Running "export XLIB_SKIP_ARGB_VISUALS=1 && dragon" turned the transparent part of the window black, though.

I should repeat myself, because it's not a X11/XVideo issue, it's more of a codec issue:

**This is a codec issue**!

---

### Post by WindPower on 2009-11-06
Bump.

---

### Post by WindPower on 2009-11-07
Bump~ I want video playback :(

---

### Post by WindPower on 2009-11-13
Bump again~ Seriously, no video = not happy

However I did find that mplayer can play some of these videos :)

---

### Post by Poyntz on 2009-11-24
Bump.

ps, it's strange, but dragon player works when I insert a DVD into the drive. that's the only time I see video (not good quality video, but video nonetheless). so this is definitely a bug

---

### Post by WindPower on 2009-12-17
Bump, still can't play videos...

---

### Post by mc4man on 2009-12-17
maybe try this
Don't know what package manager you have on kubuntu, but open it up, search ffmpeg and *remove all the ffmpeg libs* in whatever versions you have (normal, extra, unstripped
You'll lose vlc, but no matter, you can re-install later.

Then just because 9.10 can be funny this way do a restart.

Then install only the regular **or** extra versions of the ffmpeg libs (libavcodec52 or libavcodec-extra-52 being the main one

(the extra versions mainly add encoding support for some formats, I'd go with those even though they don't particularly help playback -the ones you don't want  are the 'unstripped'

Then re-install vlc, open the first time from konsole as such and see
```

vlc --reset-config --reset-plugins-cache
```

You will probably need to account for cairo-dock by one means or an other

---

### Post by WindPower on 2009-12-17
Nope, same story... Here's what I did:
```
sudo apt-get remove libavcodec* libavformat* libswscale* libpostproc* cairo-dock*
```
Then rebooted, then:
```
sudo apt-get install libavcodec-extra-52 libavformat-extra-52 libpostproc-extra-51 libswscale-extra-0 vlc
```
So far so good, and then:
```
$ vlc --reset-config --reset-plugins-cache
VLC media player 1.0.4 Goldeneye
[0x14e1ca8] main interface error: no interface module matched "globalhotkeys,none"
[0x14e1ca8] main interface error: no suitable interface module
[0x1360888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x1360888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
(4121) findLibraryInternal: plugins should not have a 'lib' prefix: "libkfilemodule.so"
(4121) KPluginLoader::load: The plugin "libkfilemodule" doesn't contain a kde_plugin_verification_data structure
[0x7fc854047f68] main decoder error: no suitable decoder module for fourcc `DX50'.
VLC probably does not support this sound or video format.
[0x1a384b8] pulse audio output: No. of Audio Channels: 2
Segmentation fault
```
(Note: the segfault only happens when I click on the "Close" button in VLC. It does not happen during playback).

---

### Post by mc4man on 2009-12-17
I don't know kubuntu very well, haven't used since 7.10, maybe I'll try a live cd this weekrnd for curiosities sake and see if I can get your errors.

This doesn't look that good, though vlc does report things that while they look bad are irrelevant
> 4121) findLibraryInternal: plugins should not have a 'lib' prefix: "libkfilemodule.so"
(4121) KPluginLoader::load: The plugin "libkfilemodule" doesn't contain a kde_plugin_verification_data structure


divx and xvid decoding in vlc are handled thru avcodec (libavcodec), so you should have support

Ex. clipped lines from an xvid avi I have
> [0x913bae0] access_file access debug: opening file `/home/doug/Desktop/AMV - MIX - Studio Ghibli - Memories Dance [Vlad G Pohnert].avi'
0x9140780] avi stream debug: strf: video: DX50 512x384 planes:1 24bpp
[0x913bae0] main access debug: using access module "access_file"
[0x9140918] main demux debug: using demux module "avi"
0x9147a80] avcodec decoder debug: using direct rendering
[0x9147a80] avcodec decoder debug: ffmpeg codec (MPEG-4 Video) started
[0x9147a80] main decoder debug: using decoder module "avcodec"


Using a divx file (a little broken) from mplayer samples, vlc should offer to repair, and then playback with similar output as above (from vlc -vv

[http://samples.mplayerhq.hu/V-codecs/DX50-DivX5/](http://samples.mplayerhq.hu/V-codecs/DX50-DivX5/) (divx502

You could test your libavcodec by installing the repo ffmpeg and then going

ffplay /path/to/filename

If ffplay can decode ( for audio in ffplay usually you'll need  libsdl1.2debian-all or if pulseaudio is being used then libsdl1.2debian-pulseaudio ) then there is something borked in your vlc install.

Maybe try with vlc -vv and see if file access is created (  main access debug: using access module "access_file"

---

### Post by Yvan300 on 2009-12-17
I had the same problem as you. This is what i did. I installed ubuntu tweak and cleaned the config, cache and unneeded applications. Then i install gstreamer -ffmpeg + libavcodec and now all my videos work:)

P.S i installed kubuntu but am now using ubuntu by installing ubuntu-packages, hope it applies to you. Oh and yeah it is a codec problem.

---

### Post by WindPower on 2009-12-17
Thanks, good progress. I downloaded divx502.avi from there and launched ffplay with it and it worked, the sound and the video worked.
Now here's the output with VLC -vv (It did ask if it should repair the file):
```
$ vlc --reset-config --reset-plugins-cache -vv                                                                                                               
VLC media player 1.0.4 Goldeneye                                                                                                                                            
[0x250b888] main libvlc debug: VLC media player - version 1.0.4 Goldeneye - (c) 1996-2009 the VideoLAN team                                                                 
[0x250b888] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1~getdeb1' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'                             
[0x250b888] main libvlc debug: translation test: code is "C"                                                                                                                
[0x250b888] main libvlc debug: checking plugin modules                                                                                                                      
[0x250b888] main libvlc debug: removing plugins cache file /home/etienne/.cache/vlc/plugins-04081e.dat                                                                      
[0x250b888] main libvlc debug: recursively browsing `/usr/lib/vlc'                                                                                                          
[0x250b888] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libx264_plugin.so' (libx264.so.67: cannot open shared object file: No such file or directory)       
[0x250b888] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libavcodec_plugin.so' (libavutil.so.49: cannot open shared object file: No such file or directory)  
[0x250b888] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (libavutil.so.49: cannot open shared object file: No such file or directory) 
[0x250b888] main libvlc debug: module bank initialized (373 modules)                                                                                                        
[0x250b888] main libvlc debug: opening config file (/home/etienne/.config/vlc/vlcrc)                                                                                        
[0x250b888] main libvlc debug: opening config file (/home/etienne/.config/vlc/vlcrc)                                                                                        
[0x250b888] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU                                                                                         
[0x250b888] main libvlc debug: looking for memcpy module: 3 candidates                                                                                                      
[0x250b888] main libvlc debug: using memcpy module "memcpymmxext"                                                                                                           
[0x253f298] main input debug: Creating an input for 'Media Library'                                                                                                         
[0x253f298] main input debug: Input is a meta file: disabling unneeded options                                                                                              
[0x253f298] main input debug: using timeshift granularity of 50 MBytes                                                                                                      
[0x253f298] main input debug: using timeshift path '/tmp'                                                                                                                   
[0x253f298] main input debug: `file/xspf-open:///home/etienne/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/etienne/.local/share/vlc/ml.xspf' 
[0x253f298] main input debug: creating demux: access='file' demux='xspf-open' path='/home/etienne/.local/share/vlc/ml.xspf'                                                 
[0x2689b28] main demux debug: looking for access_demux module: 1 candidate                                                                                                  
[0x2689b28] main demux warning: no access_demux module matching "file" could be loaded                                                                                      
[0x2689b28] main demux debug: TIMER module_need() : 0.071 ms - Total 0.071 ms / 1 intvls (Avg 0.071 ms)                                                                     
[0x253f298] main input debug: creating access 'file' path='/home/etienne/.local/share/vlc/ml.xspf'                                                                          
[0x2689f58] main access debug: looking for access module: 3 candidates                                                                                                      
[0x2689f58] access_file access debug: opening file `/home/etienne/.local/share/vlc/ml.xspf'                                                                                 
[0x2689f58] main access debug: using access module "access_file"                                                                                                            
[0x2689f58] main access debug: TIMER module_need() : 0.136 ms - Total 0.136 ms / 1 intvls (Avg 0.136 ms)                                                                    
[0x2689cd8] main stream debug: Using AStream*Stream                                                                                                                         
[0x2689cd8] main stream debug: pre buffering                                                                                                                                
[0x2689cd8] main stream debug: received first data after 0 ms                                                                                                               
[0x2689cd8] main stream debug: pre-buffering done 296 bytes in 0s - 20647 kbytes/s                                                                                          
[0x268b988] main stream debug: looking for stream_filter module: 5 candidates                                                                                               
[0x268b988] main stream debug: TIMER module_need() : 0.047 ms - Total 0.047 ms / 1 intvls (Avg 0.047 ms)                                                                    
[0x268c818] main stream debug: looking for stream_filter module: 1 candidate                                                                                                
[0x268c818] main stream debug: using stream_filter module "stream_filter_record"                                                                                            
[0x268c818] main stream debug: TIMER module_need() : 0.044 ms - Total 0.044 ms / 1 intvls (Avg 0.044 ms)                                                                    
[0x253f298] main input debug: creating demux: access='file' demux='xspf-open' path='/home/etienne/.local/share/vlc/ml.xspf'                                                 
[0x268c958] main demux debug: looking for demux module: 1 candidate                                                                                                         
[0x268c958] playlist demux debug: using XSPF playlist reader                                                                                                                
[0x268c958] main demux debug: using demux module "playlist"                                                                                                                 
[0x268c958] main demux debug: TIMER module_need() : 0.061 ms - Total 0.061 ms / 1 intvls (Avg 0.061 ms)                                                                     
[0x253f298] main input debug: `file/xspf-open:///home/etienne/.local/share/vlc/ml.xspf' successfully opened                                                                 
[0x268c608] main xml debug: looking for xml module: 2 candidates                                                                                                            
[0x268c608] main xml debug: using xml module "xtag"                                                                                                                         
[0x268c608] main xml debug: TIMER module_need() : 0.048 ms - Total 0.048 ms / 1 intvls (Avg 0.048 ms)                                                                       
[0x268c958] playlist demux debug: parsed 0 tracks successfully                                                                                                              
[0x268c608] main xml debug: removing module "xtag"                                                                                                                          
[0x253f298] main input debug: EOF reached                                                                                                                                   
[0x268c958] main demux debug: removing module "playlist"                                                                                                                    
[0x268c818] main stream debug: removing module "stream_filter_record"                                                                                                       
[0x2689f58] main access debug: removing module "access_file"                                                                                                                
[0x253f298] main input debug: TIMER input launching for 'Media Library' : 2.592 ms - Total 2.592 ms / 1 intvls (Avg 2.592 ms)                                               
[0x253c998] main playlist debug: Activated                                                                                                                                  
[0x253c998] main playlist debug: rebuilding array of current - root Playlist                                                                                                
[0x253c998] main playlist debug: rebuild done - 0 items, index -1                                                                                                           
[0x253f298] main interface debug: looking for interface module: 1 candidate                                                                                                 
[0x253f298] main interface debug: using interface module "hotkeys"                                                                                                          
[0x253f298] main interface debug: TIMER module_need() : 0.106 ms - Total 0.106 ms / 1 intvls (Avg 0.106 ms)                                                                 
[0x253f298] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                      
[0x253f298] main interface debug: thread started                                                                                                                            
[0x253fb68] main interface debug: looking for interface module: 1 candidate                                                                                                 
[0x253fb68] main interface debug: using interface module "inhibit"                                                                                                          
[0x253fb68] main interface debug: TIMER module_need() : 0.710 ms - Total 0.710 ms / 1 intvls (Avg 0.710 ms)                                                                 
[0x253fb68] main interface debug: thread started                                                                                                                            
[0x253fb68] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                      
[0x268c738] main interface debug: looking for interface module: 1 candidate                                                                                                 
[0x268c738] main interface debug: using interface module "screensaver"                                                                                                      
[0x268c738] main interface debug: TIMER module_need() : 0.058 ms - Total 0.058 ms / 1 intvls (Avg 0.058 ms)                                                                 
[0x268c738] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                      
[0x268c5e8] main interface debug: looking for interface module: 1 candidate                                                                                                 
[0x268c5e8] main interface debug: using interface module "signals"                                                                                                          
[0x268c5e8] main interface debug: TIMER module_need() : 0.073 ms - Total 0.073 ms / 1 intvls (Avg 0.073 ms)                                                                 
[0x268c5e8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                      
[0x2690498] main interface debug: looking for interface module: 0 candidates                                                                                                
[0x2690498] main interface error: no interface module matched "globalhotkeys,none"                                                                                          
[0x2690498] main interface debug: TIMER module_need() : 0.054 ms - Total 0.054 ms / 1 intvls (Avg 0.054 ms)                                                                 
[0x2690498] main interface error: no suitable interface module                                                                                                              
[0x250b888] main libvlc error: interface "globalhotkeys,none" initialization failed                                                                                         
[0x250b888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.                                                                   
[0x2690498] main interface debug: looking for interface module: 4 candidates                                                                                                
[0x268c5e8] main interface debug: thread started                                                                                                                            
[0x268c5e8] main interface debug: thread ended                                                                                                                              
[0x268c738] main interface debug: thread started                                                                                                                            
[0x2690498] main interface debug: opening config file (/home/etienne/.config/vlc/vlcrc)                                                                                     
[0x2690498] qt4 interface debug: Error while initializing qt-specific localization                                                                                          
[0x2690498] main interface debug: using interface module "qt4"                                                                                                              
[0x2690498] main interface debug: TIMER module_need() : 2627.783 ms - Total 2627.783 ms / 1 intvls (Avg 2627.783 ms)                                                        
[0x2690498] main interface debug: thread started                                                                                                                            
[0x2690498] main interface debug: thread ended                                                                                                                              
[0x2690498] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)                                                                      
(9993) findLibraryInternal: plugins should not have a 'lib' prefix: "libkfilemodule.so"                                                                                     
(9993) KPluginLoader::load: The plugin "libkfilemodule" doesn't contain a kde_plugin_verification_data structure                                                            
[0x253c998] main playlist debug: adding item `divx502.avi' ( /home/etienne/Desktop/divx502.avi )                                                                            
[0x2690498] qt4 interface debug: Adding a new MRL to recent ones: /home/etienne/Desktop/divx502.avi                                                                         
[0x253c998] main playlist debug: rebuilding array of current - root Playlist                                                                                                
[0x253c998] main playlist debug: rebuild done - 1 items, index -1                                                                                                           
[0x253c998] main playlist debug: processing request item divx502.avi node null skip 0                                                                                       
[0x253c998] main playlist debug: resyncing on divx502.avi                                                                                                                   
[0x253c998] main playlist debug: divx502.avi is at 0                                                                                                                        
[0x253c998] main playlist debug: starting new item                                                                                                                          
[0x253c998] main playlist debug: creating new input thread                                                                                                                  
[0x7f2600003ee8] main input debug: Creating an input for 'divx502.avi'                                                                                                      
[0x7f2600003ee8] main input debug: thread (input) created at priority 10 (input/input.c:230)                                                                                
[0x7f2600003ee8] main input debug: thread started                                                                                                                           
[0x7f2600003ee8] main input debug: using timeshift granularity of 50 MBytes                                                                                                 
[0x7f2600003ee8] main input debug: using timeshift path '/tmp'                                                                                                              
[0x7f2600003ee8] main input debug: `/home/etienne/Desktop/divx502.avi' gives access `' demux `' path `/home/etienne/Desktop/divx502.avi'                                    
[0x7f2600003ee8] main input debug: creating demux: access='' demux='' path='/home/etienne/Desktop/divx502.avi'                                                              
[0x2690498] qt4 interface debug: IM: Setting an input                                                                                                                       
[0x2c5b908] main demux debug: looking for access_demux module: 7 candidates                                                                                                 
[0x2c5b908] main demux debug: TIMER module_need() : 0.133 ms - Total 0.133 ms / 1 intvls (Avg 0.133 ms)                                                                     
[0x7f2600003ee8] main input debug: creating access '' path='/home/etienne/Desktop/divx502.avi'                                                                              
[0x2c67588] main access debug: looking for access module: 7 candidates                                                                                                      
[0x2c67588] vcd access debug: trying .cue file: /home/etienne/Desktop/divx502.cue                                                                                           
[0x2c67588] vcd access debug: could not find .cue file                                                                                                                      
[0x2c67588] access_file access debug: opening file `/home/etienne/Desktop/divx502.avi'                                                                                      
[0x2c67588] main access debug: using access module "access_file"                                                                                                            
[0x2c67588] main access debug: TIMER module_need() : 0.709 ms - Total 0.709 ms / 1 intvls (Avg 0.709 ms)                                                                    
[0x7f2600006618] main stream debug: Using AStream*Stream                                                                                                                    
[0x7f2600006618] main stream debug: pre buffering                                                                                                                           
[0x7f2600006618] main stream debug: received first data after 0 ms                                                                                                          
[0x7f2600006618] main stream debug: pre-buffering done 1024 bytes in 0s - 66666 kbytes/s                                                                                    
[0x7f260000f5f8] main stream debug: looking for stream_filter module: 5 candidates                                                                                          
[0x7f260000f5f8] main stream debug: TIMER module_need() : 0.076 ms - Total 0.076 ms / 1 intvls (Avg 0.076 ms)                                                               
[0x2a95398] main stream debug: looking for stream_filter module: 1 candidate                                                                                                
[0x2a95398] main stream debug: using stream_filter module "stream_filter_record"                                                                                            
[0x2a95398] main stream debug: TIMER module_need() : 0.073 ms - Total 0.073 ms / 1 intvls (Avg 0.073 ms)                                                                    
[0x7f2600003ee8] main input debug: creating demux: access='' demux='' path='/home/etienne/Desktop/divx502.avi'                                                              
[0x2c6be58] main demux debug: looking for demux module: 50 candidates                                                                                                       
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2a95398] avi stream debug: found Chunk fourcc:46464952 (RIFF) size:759622254 pos:0                                                                                       
[0x2a95398] avi stream debug: found LIST chunk: 'AVI '                                                                                                                      
[0x2a95398] avi stream debug: <list 'AVI '>                                                                                                                                 
[0x2a95398] avi stream debug: found Chunk fourcc:5453494c (LIST) size:8830 pos:12                                                                                           
[0x2a95398] avi stream debug: found LIST chunk: 'hdrl'                                                                                                                      
[0x2a95398] avi stream debug: <list 'hdrl'>                                                                                                                                 
[0x2a95398] avi stream debug: found Chunk fourcc:68697661 (avih) size:56 pos:24                                                                                             
[0x2a95398] avi stream debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED 560x224                                                                                       
[0x2a95398] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4244 pos:88                                                                                           
[0x2a95398] avi stream debug: found LIST chunk: 'strl'                                                                                                                      
[0x2a95398] avi stream debug: <list 'strl'>                                                                                                                                 
[0x2a95398] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:100                                                                                            
[0x2a95398] avi stream debug: strh: type:vids handler:0x78766964 samplesize:0 25.00fps                                                                                      
[0x2a95398] avi stream debug: found Chunk fourcc:66727473 (strf) size:40 pos:164                                                                                            
[0x2a95398] avi stream debug: strf: video:DX50 560x224 planes:1 24bpp                                                                                                       
[0x2a95398] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:212                                                                                          
[0x2a95398] avi stream debug: </list 'strl'>                                                                                                                                
[0x2a95398] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4234 pos:4340                                                                                         
[0x2a95398] avi stream debug: found LIST chunk: 'strl'                                                                                                                      
[0x2a95398] avi stream debug: <list 'strl'>                                                                                                                                 
[0x2a95398] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:4352                                                                                           
[0x2a95398] avi stream debug: strh: type:auds handler:0x00000000 samplesize:1 16000.00fps                                                                                   
[0x2a95398] avi stream debug: found Chunk fourcc:66727473 (strf) size:30 pos:4416                                                                                           
[0x2a95398] avi stream debug: strf: audio:0x0055 channels:2 44100Hz 0bits/sample 125kb/s                                                                                    
[0x2a95398] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:4454                                                                                         
[0x2a95398] avi stream debug: </list 'strl'>                                                                                                                                
[0x2a95398] avi stream debug: found Chunk fourcc:5453494c (LIST) size:260 pos:8582                                                                                          
[0x2a95398] avi stream debug: found LIST chunk: 'odml'                                                                                                                      
[0x2a95398] avi stream debug: <list 'odml'>                                                                                                                                 
[0x2a95398] avi stream debug: found Chunk fourcc:686c6d64 (dmlh) size:248 pos:8594                                                                                          
[0x2a95398] avi stream warning: unknown chunk (not loaded)                                                                                                                  
[0x2a95398] avi stream debug: </list 'odml'>                                                                                                                                
[0x2a95398] avi stream debug: </list 'hdrl'>                                                                                                                                
[0x2a95398] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1382 pos:8850                                                                                         
[0x2a95398] avi stream debug: found Chunk fourcc:5453494c (LIST) size:753117622 pos:10240                                                                                   
[0x2a95398] avi stream debug: skipping movi chunk                                                                                                                           
[0x2a95398] avi stream debug: </list 'AVI '>                                                                                                                                
[0x2a95398] avi stream debug: * LIST-root size:8388608 pos:0                                                                                                                
[0x2a95398] avi stream debug:      + RIFF-AVI  size:759622254 pos:0                                                                                                         
[0x2a95398] avi stream debug:      |    + LIST-hdrl size:8830 pos:12                                                                                                        
[0x2a95398] avi stream debug:      |    |    + avih size:56 pos:24                                                                                                          
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2a95398] avi stream debug:      |    |    + LIST-strl size:4244 pos:88                                                                                                   
[0x2a95398] avi stream debug:      |    |    |    + strh size:56 pos:100                                                                                                    
[0x2a95398] avi stream debug:      |    |    |    + strf size:40 pos:164                                                                                                    
[0x2a95398] avi stream debug:      |    |    |    + JUNK size:4120 pos:212                                                                                                  
[0x2a95398] avi stream debug:      |    |    + LIST-strl size:4234 pos:4340                                                                                                 
[0x2a95398] avi stream debug:      |    |    |    + strh size:56 pos:4352                                                                                                   
[0x2a95398] avi stream debug:      |    |    |    + strf size:30 pos:4416                                                                                                   
[0x2a95398] avi stream debug:      |    |    |    + JUNK size:4120 pos:4454                                                                                                 
[0x2a95398] avi stream debug:      |    |    + LIST-odml size:260 pos:8582                                                                                                  
[0x2a95398] avi stream debug:      |    |    |    + dmlh size:248 pos:8594                                                                                                  
[0x2a95398] avi stream debug:      |    + JUNK size:1382 pos:8850                                                                                                           
[0x2a95398] avi stream debug:      |    + LIST-movi size:753117622 pos:10240                                                                                                
[0x2c6be58] avi demux debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED                                                                                                
[0x2c6be58] avi demux debug: stream[0] rate:25000 scale:1000 samplesize:0                                                                                                   
[0x2c6be58] avi demux debug: stream[0] video(DX50) 560x224 24bpp 25.000000fps                                                                                               
[0x7f2600003ee8] main input debug: selecting program id=0                                                                                                                   
[0x2c6be58] avi demux debug: stream[1] rate:16000 scale:1 samplesize:1                                                                                                      
[0x2c6be58] avi demux debug: stream[1] audio(0x55) 2 channels 44100Hz 0bits                                                                                                 
[0x2c6be58] avi demux warning: cannot find idx1 chunk, no index defined                                                                                                     
[0x2c6be58] avi demux warning: cannot find indx (misdetect/broken OpenDML file?)                                                                                            
[0x2c6be58] avi demux warning: cannot find indx (misdetect/broken OpenDML file?)                                                                                            
[0x2c6be58] avi demux debug: stream[0] created 0 index entries                                                                                                              
[0x2c6be58] avi demux debug: stream[1] created 0 index entries                                                                                                              
[0x2c6be58] avi demux warning: broken or missing index, 'seek' will be approximative or will exhibit strange behavior                                                       
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2c6be58] avi demux debug: Fixing AVI index                                                                                                                               
[0x2c6be58] avi demux warning: creating index from LIST-movi, will take time !                                                                                              
[0x2c6be58] avi demux debug: stream[0] creating 2764 index entries                                                                                                          
[0x2c6be58] avi demux debug: stream[1] creating 2764 index entries                                                                                                          
[0x2c6be58] avi demux debug: stream[0] length:110 (based on index)                                                                                                          
[0x2c6be58] avi demux debug: stream[1] length:110 (based on index)                                                                                                          
[0x2c6be58] avi demux warning: broken or missing index, 'seek' will be approximative or will exhibit strange behavior                                                       
[0x2c6be58] main demux debug: using demux module "avi"                                                                                                                      
[0x2c6be58] main demux debug: TIMER module_need() : 4602.158 ms - Total 4602.158 ms / 1 intvls (Avg 4602.158 ms)                                                            
[0x7f2600003ee8] main input debug: looking for a subtitle file in /home/etienne/Desktop/                                                                                    
[0x7f26000103f8] main decoder debug: looking for decoder module: 30 candidates                                                                                              
[0x7f26000103f8] main decoder debug: TIMER module_need() : 0.415 ms - Total 0.415 ms / 1 intvls (Avg 0.415 ms)                                                              
[0x7f26000103f8] main decoder error: no suitable decoder module for fourcc `DX50'.                                                                                          
VLC probably does not support this sound or video format.                                                                                                                   
[0x7f26000103f8] main decoder debug: killing decoder fourcc `DX50', 0 PES in FIFO                                                                                           
[0x2c4b3f8] main decoder debug: looking for decoder module: 30 candidates                                                                                                   
[0x2c4b3f8] main decoder debug: using decoder module "mpeg_audio"                                                                                                           
[0x2c4b3f8] main decoder debug: TIMER module_need() : 0.188 ms - Total 0.188 ms / 1 intvls (Avg 0.188 ms)                                                                   
[0x2c4b3f8] main decoder debug: thread started                                                                                                                              
[0x2c4b3f8] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)                                                                                
[0x7f2600003ee8] main input debug: `/home/etienne/Desktop/divx502.avi' successfully opened                                                                                  
[0x7f2600003ee8] main input debug: Buffering 0%                                                                                                                             
[0x7f2600003ee8] main input debug: Buffering 8%                                                                                                                             
[0x7f2600003ee8] main input debug: Buffering 16%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 25%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 33%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 41%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 50%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 58%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 66%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 75%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 83%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 91%                                                                                                                            
[0x7f2600003ee8] main input debug: Buffering 100%                                                                                                                           
[0x7f2600003ee8] main input debug: Stream buffering done (325 ms in 0 ms)                                                                                                   
[0x2c4b3f8] mpeg_audio decoder debug: MPGA channels:2 samplerate:44100 bitrate:128                                                                                          
[0x7f2600003ee8] main input debug: creating aout                                                                                                                            
[0x2c46fd8] main audio output debug: looking for audio output module: 4 candidates                                                                                          
[0x2c46fd8] pulse audio output: No. of Audio Channels: 2                                                                                                                    
[0x2c46fd8] pulse audio output debug: Pulse mainloop started                                                                                                                
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2690498] qt4 interface debug: Updating the geometry                                                                                                                      
[0x2c46fd8] pulse audio output debug: Pulse stream connected                                                                                                                
[0x2c46fd8] pulse audio output debug: Pulse initialized successfully                                                                                                        
[0x2c46fd8] pulse audio output debug: Buffer metrics: maxlength=141120, tlength=42336, prebuf=35280, minreq=7056                                                            
[0x2c46fd8] pulse audio output debug: Using sample spec 'float32le 2ch 44100Hz', channel map 'front-left,front-right'.                                                      
[0x2c46fd8] pulse audio output debug: Connected to device alsa_output.pci-0000_00_08.0.analog-stereo (0, not suspended).                                                    
[0x2c46fd8] main audio output debug: using audio output module "pulse"                                                                                                      
[0x2c46fd8] main audio output debug: TIMER module_need() : 400.512 ms - Total 400.512 ms / 1 intvls (Avg 400.512 ms)                                                        
[0x2c46fd8] main audio output debug: output 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes                                                                                  
[0x2c46fd8] main audio output debug: mixer 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes                                                                                   
[0x2c46fd8] main audio output debug: no need for any filter                                                                                                                 
[0x2c46fd8] main audio output debug: looking for audio mixer module: 3 candidates                                                                                           
[0x2c46fd8] main audio output debug: using audio mixer module "float32_mixer"                                                                                               
[0x2c46fd8] main audio output debug: TIMER module_need() : 0.143 ms - Total 0.143 ms / 1 intvls (Avg 0.143 ms)                                                              
[0x2c46fd8] main audio output debug: input 'mpga' 44100 Hz Stereo frame=1152 samples/1053 bytes                                                                             
[0x2a89128] main audio filter debug: looking for audio filter module: 1 candidate                                                                                           
[0x2a89128] scaletempo audio filter warning: bad input or output format                                                                                                     
[0x2a89128] main audio filter warning: no audio filter module matching "scaletempo" could be loaded                                                                         
[0x2a89128] main audio filter debug: TIMER module_need() : 0.123 ms - Total 0.123 ms / 1 intvls (Avg 0.123 ms)                                                              
[0x2a89128] main audio filter debug: looking for audio filter module: 1 candidate                                                                                           
[0x2a89128] scaletempo audio filter debug: format: 44100 rate, 2 nch, 4 bps, fl32                                                                                           
[0x2a89128] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search                                                                                      
[0x2a89128] scaletempo audio filter debug: 1.000 scale, 1323.000 stride_in, 1323 stride_out, 1059 standing, 264 overlap, 617 search, 2204 queue, fl32 mode                  
[0x2a89128] main audio filter debug: using audio filter module "scaletempo"                                                                                                 
[0x2a89128] main audio filter debug: TIMER module_need() : 0.403 ms - Total 0.403 ms / 1 intvls (Avg 0.403 ms)                                                              
[0x2c46fd8] main audio output debug: filter(s) 'mpga'->'fl32' 44100 Hz->44100 Hz Stereo->Stereo                                                                             
[0x2c66368] main audio output debug: looking for audio filter module: 24 candidates                                                                                         
[0x2c66368] main audio output debug: using audio filter module "mpgatofixed32"                                                                                              
[0x2c66368] main audio output debug: TIMER module_need() : 0.127 ms - Total 0.127 ms / 1 intvls (Avg 0.127 ms)                                                              
[0x2c46fd8] main audio output debug: found a filter for the whole conversion                                                                                                
[0x2c46fd8] main audio output debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Stereo->Stereo                                                                             
[0x2c4d478] main audio output debug: looking for audio filter module: 24 candidates                                                                                         
[0x2c4d478] main audio output debug: using audio filter module "bandlimited_resampler"                                                                                      
[0x2c4d478] main audio output debug: TIMER module_need() : 0.222 ms - Total 0.222 ms / 1 intvls (Avg 0.222 ms)                                                              
[0x2c46fd8] main audio output debug: found a filter for the whole conversion                                                                                                
[0x2c4b3f8] main decoder debug: End of audio preroll                                                                                                                        
[0x7f2600003ee8] main input debug: Decoder buffering done in 403 ms                                                                                                         
[0x2c46fd8] main audio output warning: PTS is out of range (-9822), dropping buffer                                                                                         
[0x2c46fd8] main audio output warning: PTS is out of range (-34802), dropping buffer                                                                                        
[0x2c46fd8] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                     
[0x2c46fd8] pulse audio output debug: Pulse stream started                                                                                                                  
[0x2c46fd8] main audio output warning: output date isn't PTS date, requesting resampling (121545)                                                                           
[0x2c46fd8] main audio output warning: audio drift is too big (139503), dropping buffer                                                                                     
[0x2c46fd8] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer                                                                                     
[0x2c46fd8] main audio output warning: buffer is 114503 late, triggering upsampling                                                                                         
***** Audio playback can be heard now *****

[0x2c46fd8] main audio output warning: resampling stopped after 13024688 usec (drift: -24767)                                                  

[0x2c46fd8] main audio output warning: buffer is 40728 late, triggering upsampling                                                                                        
[0x2c46fd8] main audio output warning: resampling stopped after 250015 usec (drift: -21189)                                                                                
[0x2c46fd8] main audio output warning: buffer is 41521 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 200036 usec (drift: -24072)                                                                                
[0x2c46fd8] main audio output warning: buffer is 42338 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 200120 usec (drift: -25013)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 43154 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 124961 usec (drift: -23585)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 40603 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 249723 usec (drift: -25501)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 41397 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 199930 usec (drift: -23885)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 42213 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 199894 usec (drift: -23639)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 43029 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 149915 usec (drift: -23460)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 41601 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 199981 usec (drift: -24089)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 42417 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 149976 usec (drift: -22848)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 43233 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 125015 usec (drift: -23664)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 40682 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 249943 usec (drift: -24643)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 41476 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 199883 usec (drift: -23715)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 42292 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 99845 usec (drift: -20478)                                                                                  
[0x2c46fd8] main audio output warning: buffer is 43109 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 124966 usec (drift: -23540)                                                                                 
[0x2c46fd8] main audio output warning: buffer is 40558 late, triggering upsampling                                                                                          
[0x2c46fd8] main audio output warning: resampling stopped after 250026 usec (drift: -25456)                                                                                 
[0x250b888] main libvlc debug: deactivating the playlist                                                                                                                    
[0x253c998] main playlist debug: Deactivate                                                                                                                                 
[0x253c998] main playlist debug: incoming request - stopping current input                                                                                                  
[0x253c998] main playlist debug: dying input                                                                                                                                
[0x7f2600003ee8] main input debug: control type=0                                                                                                                           
[0x7f2600003ee8] main input debug: control: stopping input                                                                                                                  
[0x2c4b3f8] main decoder debug: removing module "mpeg_audio"                                                                                                                
[0x2c4b3f8] main decoder debug: killing decoder fourcc `mpga', 0 PES in FIFO                                                                                                
[0x2c66368] main audio output debug: removing module "mpgatofixed32"                                                                                                        
[0x2a89128] main audio filter debug: removing module "scaletempo"                                                                                                           
[0x2c4d478] main audio output debug: removing module "bandlimited_resampler"                                                                                                
[0x2c46fd8] pulse audio output debug: Pulse Close                                                                                                                           
[0x253c998] main playlist debug: dying input                                                                                                                                
[0x2c46fd8] main audio output debug: removing module "pulse"                                                                                                                
[0x2c46fd8] main audio output debug: removing module "float32_mixer"                                                                                                        
[0x7f2600003ee8] main input debug: releasing aout                                                                                                                           
[0x2a95398] avi stream debug: free chunk avih                                                                                                                               
[0x2a95398] avi stream debug: free chunk strh                                                                                                                               
[0x2a95398] avi stream debug: free chunk strf                                                                                                                               
[0x2a95398] avi stream debug: free chunk JUNK                                                                                                                               
[0x2a95398] avi stream debug: free chunk LIST                                                                                                                               
[0x2a95398] avi stream debug: free chunk strh                                                                                                                               
[0x2a95398] avi stream debug: free chunk strf                                                                                                                               
[0x2a95398] avi stream debug: free chunk JUNK
[0x2a95398] avi stream debug: free chunk LIST
[0x2a95398] avi stream warning: unknown chunk (not unloaded)
[0x2a95398] avi stream debug: free chunk LIST
[0x2a95398] avi stream debug: free chunk LIST
[0x2a95398] avi stream debug: free chunk JUNK
[0x2a95398] avi stream debug: free chunk LIST
[0x2a95398] avi stream debug: free chunk RIFF
[0x2a95398] avi stream debug: free chunk LIST
[0x2c6be58] main demux debug: removing module "avi"
[0x2a95398] main stream debug: removing module "stream_filter_record"
[0x2c67588] main access debug: removing module "access_file"
[0x7f2600003ee8] main input debug: Program doesn't contain anymore ES
[0x7f2600003ee8] main input debug: thread ended
[0x253c998] main playlist debug: dead input
[0x2690498] qt4 interface debug: IM: Deleting the input
[0x2690498] qt4 interface debug: Updating the geometry
[0x2690498] qt4 interface debug: Updating the geometry
[0x7f2600003ee8] main input debug: TIMER input launching for 'divx502.avi' : 4607.454 ms - Total 4607.454 ms / 1 intvls (Avg 4607.454 ms)
[0x253c998] main playlist debug: saving Media Library to file /home/etienne/.local/share/vlc/ml.xspf
[0x253c998] main playlist debug: looking for playlist export module: 1 candidate
[0x253c998] main playlist debug: using playlist export module "export"
[0x253c998] main playlist debug: TIMER module_need() : 0.155 ms - Total 0.155 ms / 1 intvls (Avg 0.155 ms)
[0x253c998] main playlist debug: removing module "export"
[0x253c998] main playlist debug: Deactivated
[0x250b888] main libvlc debug: removing all services discovery tasks
[0x250b888] main libvlc debug: removing all interfaces
[0x2690498] qt4 interface debug: Quitting the Qt4 Interface
[0x2690498] qt4 interface debug: destroying the main Qt4 interface
[0x2690498] qt4 interface debug: Destroying the main interface
[0x2690498] main interface debug: removing module "qt4"
[0x268c5e8] main interface debug: removing module "signals"
[0x268c738] main interface debug: removing module "screensaver"
[0x253fb68] main interface debug: removing module "inhibit"
[0x253f298] main interface debug: removing module "hotkeys"
[0x250b888] main libvlc debug: removing playlist
[0x253c998] main playlist debug: Destroyed
[0x250b888] main libvlc debug: TIMER ML Load : Total 2.777 ms / 1 intvls (Avg 2.777 ms)
[0x250b888] main libvlc debug: TIMER Items array build : Total 0.037 ms / 2 intvls (Avg 0.019 ms)
[0x250b888] main libvlc debug: TIMER ML Dump : Total 0.307 ms / 1 intvls (Avg 0.307 ms)
[0x250b888] main libvlc debug: removing stats
[0x250b888] main libvlc debug: removing module "memcpymmxext"
[0x250b888] main libvlc debug: opening config file (/home/etienne/.config/vlc/vlcrc)
[0x250b888] main libvlc debug: writing plugins cache /home/etienne/.cache/vlc/plugins-04081e.dat
Segmentation fault
```

Here are the lines that look the most suspicious to me:
```
[0x250b888] main libvlc debug: recursively browsing `/usr/lib/vlc'                                                                                                          
[0x250b888] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libx264_plugin.so' (libx264.so.67: cannot open shared object file: No such file or directory)       
[0x250b888] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libavcodec_plugin.so' (libavutil.so.49: cannot open shared object file: No such file or directory)  
[0x250b888] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (libavutil.so.49: cannot open shared object file: No such file or directory) 
```
Here is what is in /usr/lib/vlc/codec:
```
$ ls -al /usr/lib/vlc/codec/
total 792
drwxr-xr-x  2 root root   4096 2009-12-17 16:43 .
drwxr-xr-x 22 root root   4096 2009-12-17 16:39 ..
-rw-r--r--  1 root root  14376 2009-12-11 12:26 liba52_plugin.so
-rw-r--r--  1 root root  18456 2009-12-11 12:26 libadpcm_plugin.so
-rw-r--r--  1 root root  10256 2009-12-11 12:26 libaes3_plugin.so
-rw-r--r--  1 root root  22560 2009-12-11 12:26 libaraw_plugin.so
-rw-r--r--  1 root root  68152 2009-12-11 12:26 libavcodec_plugin.so
-rw-r--r--  1 root root  18488 2009-12-11 12:26 libcc_plugin.so
-rw-r--r--  1 root root  14328 2009-12-11 12:26 libcdg_plugin.so
-rw-r--r--  1 root root  31336 2009-12-11 12:26 libcmml_plugin.so
-rw-r--r--  1 root root  14360 2009-12-11 12:26 libcvdsub_plugin.so
-rw-r--r--  1 root root  14384 2009-12-11 12:26 libdts_plugin.so
-rw-r--r--  1 root root 129168 2009-12-11 12:26 libdvbsub_plugin.so
-rw-r--r--  1 root root  14488 2009-12-11 12:26 libfaad_plugin.so
-rw-r--r--  1 root root  14536 2009-12-11 12:26 libfake_plugin.so
-rw-r--r--  1 root root  22720 2009-12-11 12:26 libflac_plugin.so
-rw-r--r--  1 root root  10248 2009-12-11 12:26 libinvmem_plugin.so
-rw-r--r--  1 root root  18720 2009-12-11 12:26 liblibass_plugin.so
-rw-r--r--  1 root root  18640 2009-12-11 12:26 liblibmpeg2_plugin.so
-rw-r--r--  1 root root  10264 2009-12-11 12:26 liblpcm_plugin.so
-rw-r--r--  1 root root  14392 2009-12-11 12:26 libmpeg_audio_plugin.so
-rw-r--r--  1 root root  10376 2009-12-11 12:26 libpng_plugin.so
-rw-r--r--  1 root root  10296 2009-12-11 12:26 librawvideo_plugin.so
-rw-r--r--  1 root root  10368 2009-12-11 12:26 libschroedinger_plugin.so
-rw-r--r--  1 root root  10360 2009-12-11 12:26 libsdl_image_plugin.so
-rw-r--r--  1 root root  22896 2009-12-11 12:26 libspeex_plugin.so
-rw-r--r--  1 root root  14384 2009-12-11 12:26 libspudec_plugin.so
-rw-r--r--  1 root root  31048 2009-12-11 12:26 libsubsdec_plugin.so
-rw-r--r--  1 root root  22784 2009-12-11 12:26 libsubsusf_plugin.so
-rw-r--r--  1 root root  14408 2009-12-11 12:26 libsvcdsub_plugin.so
-rw-r--r--  1 root root   6136 2009-12-11 12:26 libt140_plugin.so
-rw-r--r--  1 root root  14408 2009-12-11 12:26 libtelx_plugin.so
-rw-r--r--  1 root root  18712 2009-12-11 12:26 libtheora_plugin.so
-rw-r--r--  1 root root  14528 2009-12-11 12:26 libtwolame_plugin.so
-rw-r--r--  1 root root  22936 2009-12-11 12:26 libvorbis_plugin.so
-rw-r--r--  1 root root  35008 2009-12-11 12:26 libx264_plugin.so
```
And /usr/lib/vlc/demux:
```
$ ls -al /usr/lib/vlc/demux/
total 1828
drwxr-xr-x  2 root root   4096 2009-12-17 16:43 .
drwxr-xr-x 22 root root   4096 2009-12-17 16:39 ..
-rw-r--r--  1 root root  10264 2009-12-11 12:26 libaiff_plugin.so
-rw-r--r--  1 root root  55560 2009-12-11 12:26 libasf_plugin.so
-rw-r--r--  1 root root  10264 2009-12-11 12:26 libau_plugin.so
-rw-r--r--  1 root root  47536 2009-12-11 12:27 libavformat_plugin.so
-rw-r--r--  1 root root  63816 2009-12-11 12:26 libavi_plugin.so
-rw-r--r--  1 root root  10296 2009-12-11 12:26 libdemux_cdg_plugin.so
-rw-r--r--  1 root root  10288 2009-12-11 12:26 libdemuxdump_plugin.so
-rw-r--r--  1 root root  10288 2009-12-11 12:27 libdirac_plugin.so
-rw-r--r--  1 root root  18592 2009-12-11 12:26 libes_plugin.so
-rw-r--r--  1 root root  22696 2009-12-11 12:26 libflacsys_plugin.so
-rw-r--r--  1 root root  10280 2009-12-11 12:26 libh264_plugin.so
-rw-r--r--  1 root root 476040 2009-12-11 12:26 liblive555_plugin.so
-rw-r--r--  1 root root  10280 2009-12-11 12:26 libm4v_plugin.so
-rw-r--r--  1 root root  14440 2009-12-11 12:26 libmjpeg_plugin.so
-rw-r--r--  1 root root 303008 2009-12-11 12:26 libmkv_plugin.so
-rw-r--r--  1 root root  26968 2009-12-11 12:26 libmod_plugin.so
-rw-r--r--  1 root root 141936 2009-12-11 12:26 libmp4_plugin.so
-rw-r--r--  1 root root  10312 2009-12-11 12:26 libmpc_plugin.so
-rw-r--r--  1 root root  10264 2009-12-11 12:26 libmpgv_plugin.so
-rw-r--r--  1 root root  10304 2009-12-11 12:26 libnsc_plugin.so
-rw-r--r--  1 root root  14360 2009-12-11 12:26 libnsv_plugin.so
-rw-r--r--  1 root root  18472 2009-12-11 12:26 libnuv_plugin.so
-rw-r--r--  1 root root  51592 2009-12-11 12:26 libogg_plugin.so
-rw-r--r--  1 root root  84560 2009-12-11 12:26 libplaylist_plugin.so
-rw-r--r--  1 root root  26696 2009-12-11 12:26 libps_plugin.so
-rw-r--r--  1 root root  14376 2009-12-11 12:26 libpva_plugin.so
-rw-r--r--  1 root root  10296 2009-12-11 12:26 librawaud_plugin.so
-rw-r--r--  1 root root  10304 2009-12-11 12:26 librawdv_plugin.so
-rw-r--r--  1 root root  14560 2009-12-11 12:26 librawvid_plugin.so
-rw-r--r--  1 root root  26712 2009-12-11 12:26 libreal_plugin.so
-rw-r--r--  1 root root  14408 2009-12-11 12:26 libsmf_plugin.so
-rw-r--r--  1 root root  30984 2009-12-11 12:26 libsubtitle_plugin.so
-rw-r--r--  1 root root  84576 2009-12-11 12:26 libts_plugin.so
-rw-r--r--  1 root root  10280 2009-12-11 12:26 libtta_plugin.so
-rw-r--r--  1 root root  30912 2009-12-11 12:26 libty_plugin.so
-rw-r--r--  1 root root  10280 2009-12-11 12:26 libvc1_plugin.so
-rw-r--r--  1 root root  22632 2009-12-11 12:26 libvobsub_plugin.so
-rw-r--r--  1 root root  14416 2009-12-11 12:26 libvoc_plugin.so
-rw-r--r--  1 root root  14504 2009-12-11 12:26 libwav_plugin.so
-rw-r--r--  1 root root  10288 2009-12-11 12:26 libxa_plugin.so
```

---

### Post by mc4man on 2009-12-17
**Where did you get vlc from? **

This is your main issue with that test file (which while is broken should play

> [0x2c6be58] main demux debug: using demux module "avi"                                                                                                                      
[0x2c6be58] main demux debug: TIMER module_need() : 4602.158 ms - Total 4602.158 ms / 1 intvls (Avg 4602.158 ms)                                                            
[0x7f2600003ee8] main input debug: looking for a subtitle file in /home/etienne/Desktop/                                                                                    
[0x7f26000103f8] main decoder debug: looking for decoder module: 30 candidates                                                                                              
[0x7f26000103f8] main decoder debug: TIMER module_need() : 0.415 ms - Total 0.415 ms / 1 intvls (Avg 0.415 ms)                                                              
[0x7f26000103f8] main decoder error: no suitable decoder module for fourcc `DX50'.                                                                                          
VLC probably does not support this sound or video format.                                                                                                                   
[0x7f26000103f8] main decoder debug: killing decoder fourcc `DX50', 0 PES in FIFO        
And as you noted these are definitely showstoppers
> 0x250b888] main libvlc debug: recursively browsing `/usr/lib/vlc'                                                                                                          
[0x250b888] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libx264_plugin.so' (libx264.so.67: cannot open shared object file: No such file or directory)       
[0x250b888] main libvlc warning: cannot load module `[COLOR="Red"]/usr/lib/vlc/codec/libavcodec_plugin.so[/COLOR]' (libavutil.so.49: cannot open shared object file: No such file or directory)  
[0x250b888] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (libavutil.so.49: cannot open shared object file: No such file or directory) 


You may want to consider installing synaptic for the moment, if so search ffmpeg and see what version of libavutil is installed. (thru properties of package

Also the suggestion  to clean your apt cache before installing is a good one.

If you built vlc run this ( or do anyway
```
sudo ldconfig
```

Edit: scratch the above about ldconfig, it would have been run when you installed ffmpeg, if you do install synaptic (only because  it's easier to work with), also search vlc and see if you have multiple versions of libvlcX or libvlccoreX installed

---

### Post by WindPower on 2009-12-17
Alright, the thing is that the libraries seem to be coming from multiple PPAs. VLC was from GetDeb's PPA, libavutil and libx264 were from [https://launchpad.net/~thefirstm/+archive/karmic-testing](https://launchpad.net/~thefirstm/+archive/karmic-testing) (which I use to get more recent NVIDIA drivers), and the other libav's were from the official repos. So I disabled all non-official repos in /etc/apt/sources.list, did an apt-get update / apt-get autoremove / apt-get autoclean, then reinstalled VLC from the official repos and all the libav's from the official repos as well. Then I started VLC with --reset-config --reset-plugins-cache -vv, opened the same file, and got this:
```
[????????] x11 video output error: X11 request 133.19 failed with error code 8:                                                                                             
 BadMatch (invalid parameter attributes)                                                                                                                                    
X Error of failed request:  BadMatch (invalid parameter attributes)                                                                                                         
  Major opcode of failed request:  133 (XVideo)                                                                                                                             
  Minor opcode of failed request:  19 ()                                                                                                                                    
  Serial number of failed request:  101                                                                                                                                     
  Current serial number in output stream:  102                                                                                                                              
Segmentation fault
```
This looked like an X-related error, so I changed VLC's output module to "OpenGL" and... It worked! :guitar:
Then I looked back at the replies at the beginning of this topic; those who thought it wasn't a codec problem but more of an X problem, so I set VLC's output module back to the default (XVideo) and tried running VLC with XLIB_SKIP_ARGB_VISUALS=1, and lo and behold, it worked~ (Albeit with a segfault on exit)

So, it wasn't a codec problem, it wasn't an X problem, it was both :D

So now I'm happy and it works, but... I have disabled all of my PPAs, and if I reenable them and run an update, all the libav's will be replaced by the PPA ones, right? So, I'd like to know, is there any way to enable those PPAs but "refuse" some packages from them, in order to keep the ones I have installed in sync with the official Ubuntu repositories?

Thanks for all the help~

---

### Post by mc4man on 2009-12-17
A few things
The vlc that's coming in lucid has been patched to help with cairo-dock, ( or a 1.0.4 vlc build, either yourself or from a ppa

When using ppa's you should only leave them enabled to acquire **only the package(s) you want**, if they contain other packages and you run an update then any you also have will be  updated.

I believe the firstm ppa has multiple packages, while I guess some of them could be of value if not wanting to build, running the update manager while that ppa is enabled will lead to issues.
So if you were using that for display drivers then just enable the ppa, update the sources and ck. in your package manager for nvidia updates only. Then disable the ppa till the next time you wish to ck.

It can be tricky using a ppa for shared ffmpeg and x264 libs, the chance of moving out of sync with your repo apps and or plug-ins is good.

Far better ways to get an updated ffmpeg and put it to use, either as a standalone (ffmpeg) or to build apps that use it.

---

### Post by WindPower on 2009-12-17
Okay, guess I'll just abandon that PPA then. Marking as solved.

For the record, I re-enabled the GetDeb PPA and isntalled VLC 1.0.4 from there and it indeed works without XLIB_SKIP_ARGB_VISUALS=1. I also reinstalled the libav*-unstripped packages, and it worked fine. :)

---

### Post by mc4man on 2009-12-17
Glad your back in business,
> I re-enabled the GetDeb PPA

Again, the getdeb repo has a lot of packages, so either disable for the moment, ( till you want to ck .for upadates or get something else) or if not, when you run an update (update manager or cli), then look at what's being updated so your not possibly surprised...

---

