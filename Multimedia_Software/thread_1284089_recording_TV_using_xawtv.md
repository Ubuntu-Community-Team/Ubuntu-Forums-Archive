---
title: "recording TV using xawtv"
date: 2009-10-06
forum: Multimedia Software
---

### Post by madsmaddad on 2009-10-06
Hi,  I am trying to set up a PC using kubuntu 9.04 and a borrowed Hauppauge analog TV card to convert stuff from my VCR to digital format. I have the system operating in that I can display a TV channel.  to record some data  I use the command 'R' to bring up a recording menu. I have used 'touch to create a test.avi file. I then changed the permissions on this to 777. 

whether I set the file name to ./test.avi  or /home/peterm/test.avi  I get the same error message

File not found. 

Can someone advise of possible ways to get this working? Is xawtv looking for the file somewhere else? 

here is a bit of the dmesg output:


15.650706] tuner' 0-0061: chip found @ 0xc2 (bt848 #0 [sw])                                        
[   15.763501] tuner-simple 0-0061: creating new instance                                              
[   15.763511] tuner-simple 0-0061: type set to 7 (Temic PAL_I (4062 FY5))                             
[   15.775762] bttv0: registered device video0                                                         
[   15.776089] bttv0: registered device vbi0    


and the start output when I start xawtv:

peterm@peterm-desktop:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-15-generic)
xinerama 0: 1280x960+0+0
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct


Thanks for any help.

---

### Post by SteveDee on 2009-10-06
I can't help you with xawtv, but if you have VLC installed you could try running this command in a terminal:-
 vlc -width=1000 v4l2:///dev/video0:norm=pal:input=1 --sout '#duplicate{dst=display,dst="transcode{vcodec=mp4v,vb=4096,scale=1,acodec=mp4a,ab=64,channel=1}:duplicate{dst=std{access=file,mux=mp4,dst=/home/steve/Videos/myVideo.mp4}}"'

This will give you an MP4 in a file specified in the "dst=" part of this command. The command structure assumes you have VLC 0.9.x installed (I think the format for VLC 0.8.x and earlier versions is different).

---

### Post by Jose Catre-Vandis on 2009-10-06
or use mencoder (mplayer)

---

### Post by madsmaddad on 2009-10-11
Mencoder looks pretty old - The history file only updated up to 2003. 

Doesn't look that easy to use from the faq's and I notice that line 2 of getting it to work with TV  says- "Make sure the TV card works with another program such as xawtv".

Any thoughts on my original question?

cheers all

---

### Post by madsmaddad on 2009-10-13
Steve -  tried this: And following all this stuff shown below I got all the man help.  It looks more like debug information than error  messages.:confused:

peterm@peterm-desktop:~$ vlc -width=1000 v4l2:///dev/video0:norm=pal:input=1 --sout '#duplicate{dst=display,dst="transcode{vcodec=mp4v ,vb=4096,scale=1,acodec=mp4a,ab=64,channel=1}:dupl icate{dst=std{access=file,mux=mp4,dst=/home/peterm/test.mp4}}"'                                        
VLC media player 0.9.9a Grishenko                                                  
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team                                                                                                   
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'                                                             
[00000001] main libvlc debug: translation test: code is "en_GB"                                        
Usage: vlc [options] [stream] ...                                                                      
You can specify multiple streams on the commandline. They will be enqueued in the playlist.            
The first item specified will be played first.                                                         

Options-styles:
  --option  A global option that is set for the duration of the program.
   -option  A single letter version of a global --option.               
   :option  An option that only applies to the stream directly before it
            and that overrides previous settings.                       

Stream MRL syntax:
  [[access][/demux]://]URL[@[title][:chapter][-[title][:chapter]]] [:option=value ...]

  Many of the global --options can also be used as MRL specific :options.
  Multiple :option=value pairs can be specified.                         

URL syntax:
  [file://]filename              Plain media file
  [http://ip:port/file](http://ip:port/file)            HTTP URL        
  [ftp://ip:port/file](ftp://ip:port/file)             FTP URL         
  mms://ip:port/file             MMS URL         
  screen://                      Screen capture  
  [dvd://][device][@raw_device]  DVD device      
  [vcd://][device]               VCD device      
  [cdda://][device]              Audio CD device 
  udp://[[<source address>]@[<bind address>][:<bind port>]]
                                 UDP stream sent by a streaming server
  vlc://pause:<seconds>          Special item to pause the playlist for a certain time
  vlc://quit                     Special item to quit VLC

---

### Post by SteveDee on 2009-10-13
Sorry mate, I think I see the problem.

When I copied the vlc instruction out of my personal wiki, the word "duplicate" must have been split onto 2 lines so it ended up in my post as "dupl icate". So (quite rightly) VLC does not know what we want it to do!

So try removing the space and trying again. Don't know if you are familiar with the Linux terminal, but if not, I would do this by opening a terminal and pressing the up arrow a few times until the command appears. Then use left arrow to reach the space and delete it. Then use "end" key to get back to end of line, the press "enter".

If you can't find the original command this way, just copy & paste again, then edit. Either way, this command line has to be character perfect.

I hope this helps.

---

