---
title: "Webcam won't work"
date: 2008-12-16
forum: Multimedia Software
---

### Post by Zebediah49 on 2008-12-16
A bit ago I started trying to these webcams that I have working with linux. (They work fine on windows).

I plug it in, try random stuff, nothing works.  The results of as many tests as I can remember to try are here:

System: Ubuntu 8.10 on a Thinkpad T60; Centrino duo; 2 GB ram, ATI x1600(?).
fglrx drivers; using compiz usually (using the metacity switch to allow things that don't work nicely with it).  Audio--don't want to go into it, but that shouldn't be significant, and it works.

The camera does show up as /dev/video0

```

zeb@LAPPY:~$ cheese                                                                  
libv4l2: error dequeuing buf: Input/output error                                                                                                                                   
zeb@LAPPY:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-10-generic)
xinerama 0: 1680x1050+0+0                                             
/dev/video0 [v4l2]: no overlay support                                
v4l-conf had some trouble, trying to continue anyway                  
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
v4l2: oops: select timeout                                                                  
^Clibv4l2: error dequeuing buf: Interrupted system call                                     
v4l2: read: Interrupted system call                                                         
X Error of failed request:  BadWindow (invalid Window parameter)                            
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)                             
  Resource id in failed request:  0x4c00062                                                 
  Serial number of failed request:  3969                                                    
  Current serial number in output stream:  3971                                             
zeb@LAPPY:~$ xawtv -c /dev/video0 
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-10-generic)
xinerama 0: 1680x1050+0+0                                             
/dev/video0 [v4l2]: no overlay support                                
v4l-conf had some trouble, trying to continue anyway                  
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
v4l2: oops: select timeout                                                                  
station "next" not found                                                                    
^C^Clibv4l2: error dequeuing buf: Input/output error                                        
v4l2: read: Input/output error                                                              
*** glibc detected *** /usr/bin/xawtv: double free or corruption (!prev): 0x0000000000a296f0 ***
======= Backtrace: =========                                                                    
/lib/libc.so.6[0x7f5c6211e938]                                                                  
/lib/libc.so.6(cfree+0x76)[0x7f5c62120f86]                                                      
/usr/lib/xawtv/drv0-v4l2.so[0x7f5c6048c802]                                                     
/usr/bin/xawtv(ExitCB+0x73)[0x419b63]                                                           
/usr/lib/libXt.so.6[0x7f5c63b00d5a]                                                             
/usr/lib/libXt.so.6(XtAppNextEvent+0xa2)[0x7f5c63b00e32]                                        
/usr/bin/xawtv(xt_main_loop+0x4f)[0x41773f]                                                     
/usr/bin/xawtv(main+0x1742)[0x4121b2]                                                           
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f5c620c3466]                                          
/usr/bin/xawtv[0x40f0b9]                                                                        
======= Memory map: ========                                                                    
00400000-0043e000 r-xp 00000000 08:05 1355519                            /usr/bin/xawtv.bin     
0063d000-0063e000 r--p 0003d000 08:05 1355519                            /usr/bin/xawtv.bin     
0063e000-00646000 rw-p 0003e000 08:05 1355519                            /usr/bin/xawtv.bin     
00646000-0064d000 rw-p 00646000 00:00 0                                                         
009e0000-01633000 rw-p 009e0000 00:00 0                                  [heap]                 
7f5c58000000-7f5c58021000 rw-p 7f5c58000000 00:00 0                                             
7f5c58021000-7f5c5c000000 ---p 7f5c58021000 00:00 0                                             
7f5c5c00b000-7f5c5c021000 r-xp 00000000 08:05 581650                     /lib/libgcc_s.so.1     
7f5c5c021000-7f5c5c221000 ---p 00016000 08:05 581650                     /lib/libgcc_s.so.1     
7f5c5c221000-7f5c5c222000 r--p 00016000 08:05 581650                     /lib/libgcc_s.so.1     
7f5c5c222000-7f5c5c223000 rw-p 00017000 08:05 581650                     /lib/libgcc_s.so.1     
7f5c5c240000-7f5c5c442000 rw-p 7f5c5c240000 00:00 0                                             
7f5c5c442000-7f5c5c449000 rwxp 7f5c5c442000 00:00 0                                             
7f5c5c449000-7f5c5c64b000 rw-p 7f5c5c449000 00:00 0                                             
7f5c5c64b000-7f5c5c66e000 rwxp 7f5c5c64b000 00:00 0                                             
7f5c5c674000-7f5c5cd74000 rw-s 33f2f000 00:0e 19001                      /dev/dri/card0         
7f5c5cd74000-7f5c5dd2e000 r-xp 00000000 08:05 1687605                    /usr/lib/dri/fglrx_dri.so
7f5c5dd2e000-7f5c5de2e000 ---p 00fba000 08:05 1687605                    /usr/lib/dri/fglrx_dri.so
7f5c5de2e000-7f5c5df20000 rw-p 00fba000 08:05 1687605                    /usr/lib/dri/fglrx_dri.so
7f5c5df20000-7f5c5e0d1000 rw-p 7f5c5df20000 00:00 0
7f5c5e0db000-7f5c5e0dc000 rw-s 3507b000 00:0e 19001                      /dev/dri/card0
7f5c5e0dc000-7f5c5e0dd000 rw-s 35070000 00:0e 19001                      /dev/dri/card0
7f5c5e0dd000-7f5c5e0de000 rw-s 33f2e000 00:0e 19001                      /dev/dri/card0
7f5c5e0de000-7f5c5e0ee000 rw-s 33f2d000 00:0e 19001                      /dev/dri/card0
7f5c5e0ee000-7f5c5e0f0000 rw-s 33f2b000 00:0e 19001                      /dev/dri/card0
7f5c5e0f0000-7f5c5e192000 rwxp 7f5c5e0f0000 00:00 0
7f5c5e192000-7f5c5e197000 r-xp 00000000 08:05 1355916                    /usr/lib/libXfixes.so.3.1.0
7f5c5e197000-7f5c5e396000 ---p 00005000 08:05 1355916                    /usr/lib/libXfixes.so.3.1.0
7f5c5e396000-7f5c5e397000 rw-p 00004000 08:05 1355916                    /usr/lib/libXfixes.so.3.1.0
7f5c5e397000-7f5c5e3a0000 r-xp 00000000 08:05 1355920                    /usr/lib/libXcursor.so.1.0.2
7f5c5e3a0000-7f5c5e5a0000 ---p 00009000 08:05 1355920                    /usr/lib/libXcursor.so.1.0.2
7f5c5e5a0000-7f5c5e5a1000 rw-p 00009000 08:05 1355920                    /usr/lib/libXcursor.so.1.0.2
7f5c5e5a1000-7f5c5e5a3000 r-xp 00000000 08:05 1433937                    /usr/lib/xawtv/write-dv.so
7f5c5e5a3000-7f5c5e7a2000 ---p 00002000 08:05 1433937                    /usr/lib/xawtv/write-dv.so
7f5c5e7a2000-7f5c5e7a3000 r--p 00001000 08:05 1433937                    /usr/lib/xawtv/write-dv.so
7f5c5e7a3000-7f5c5e7a4000 rw-p 00002000 08:05 1433937                    /usr/lib/xawtv/write-dv.so
7f5c5e7a4000-7f5c5e7a7000 r-xp 00000000 08:05 1433936                    /usr/lib/xawtv/write-avi.so
7f5c5e7a7000-7f5c5e9a6000 ---p 00003000 08:05 1433936                    /usr/lib/xawtv/write-avi.so
7f5c5e9a6000-7f5c5e9a7000 r--p 00002000 08:05 1433936                    /usr/lib/xawtv/write-avi.so
7f5c5e9a7000-7f5c5e9a8000 rw-p 00003000 08:05 1433936                    /usr/lib/xawtv/write-avi.so
7f5c5e9a8000-7f5c5e9ac000 r-xp 00000000 08:05 143Aborted
zeb@LAPPY:~$ gst-launch v4l2src ! video/x-raw-yuv,width=320,height=240 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...                                                                               
Pipeline is live and does not need PREROLL ...                                                               
Setting pipeline to PLAYING ...                                                                              
New clock: GstSystemClock                                                                                    
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
libv4l2: error dequeuing buf: Input/output error                                                             
^CCaught interrupt -- handling interrupt.                                                                    
Interrupt: Stopping pipeline ...                                                                             
Execution ended after 42241551300 ns.                                                                        
Setting pipeline to PAUSED ...                                                                               
libv4l2: error dequeuing buf: Input/output error                                                             
^C                                                                                                           
zeb@LAPPY:~$ camorama -D -d /dev/video0 -R
gah!                                             

VIDIOCGCAP
device name = USB camera
device type = 1         
# of channels = 1       
# of audio devices = 0  
max width = 640         
max height = 480        
min width = 48          
min height = 32         

VIDIOCGWIN
x = 0     
y = 0     
width = 320
height = 240
chromakey = 0
flags = 0    

VIDIOCGWIN
x = 0     
y = 0     
width = 320
height = 240
chromakey = 0
flags = 0    

VIDIOCGPICT:
bright = 32512
hue = 0       
colour = 32768
contrast = 32509
whiteness = 0
colour depth = 8
using read()

(camorama:14655): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
update_tooltip called
tip - acap off
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
update_tooltip called
tip - acap off
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
^C
//I removed and then re-attached the camera before running the command here:
zeb@LAPPY:~$ dmesg | tail -20
[97356.673240] gspca: frame overflow 118812 > 118784
[97370.913246] gspca: frame overflow 118966 > 118784
[97398.913252] gspca: frame overflow 118803 > 118784
[97424.161255] gspca: frame overflow 118821 > 118784
[97459.105234] gspca: frame overflow 119031 > 118784
[97581.880666] gspca: usb_submit_urb [0] err -28
[97582.292572] gspca: usb_submit_urb [0] err -28
[97582.696571] gspca: usb_submit_urb [0] err -28
[97583.100565] gspca: usb_submit_urb [0] err -28
[97583.516622] gspca: usb_submit_urb [0] err -28
[97583.929438] gspca: usb_submit_urb [0] err -28
[97596.825281] gspca: frame overflow 32944 > 32768
[97600.505283] gspca: frame overflow 32801 > 32768
[97735.114651] usb 5-5.4.2: USB disconnect, address 66
[97735.115896] gspca: disconnect complete
[97737.872424] usb 5-5.4.2: new full speed USB device using ehci_hcd and address 67
[97737.966699] usb 5-5.4.2: configuration #1 chosen from 1 choice
[97737.968643] gspca: probing 0c45:6143
[97737.970659] sonixj: Sonix chip id: 12
[97737.975166] gspca: probe ok
zeb@LAPPY:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000413] v4l demux error: cannot open audio device (Device or resource busy)

```

Any suggestions?

---

### Post by seaq on 2008-12-16
Hi, i've put in the wiki a list for known bugs with webcam cameras. 


[https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams](https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams)

---

