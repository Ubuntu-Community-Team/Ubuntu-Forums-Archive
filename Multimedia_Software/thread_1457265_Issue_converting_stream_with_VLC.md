---
title: "Issue converting stream with VLC"
date: 2010-04-18
forum: Multimedia Software
---

### Post by calande on 2010-04-18
Hello,

I'm trying to save a DVB-T stream with VLC, transcoding the audio channel into MP3 (otherwise I can't have sound in the resulting MPEG file). So, I'm using this command: ```
vlc "rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=210&flavour=ld" --run-time="30" --rtsp-caching="1000" --sout="#transcode{acodec=mp3}:std{access=file,mux=ps,dst='video.mpg'}"
```But I get this error message in a VLC dialog window:> Streaming / Transcoding failed:
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG Audio layer 1/2/3.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.
And this one in my terminal:> $ vlc "rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=210&flavour=ld" --run-time="30" --rtsp-caching="1000" --sout="#transcode{acodec=mp3}:std{access=file,mux=ps,dst='video.mpg'}"
VLC media player 1.0.2 Goldeneye
[0x8072140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x831c710] mux_ps mux: Open
libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 0) for PID 256
[0x83698b8] ts demux error: MPEG-4 descriptor not found
[0x83a7b90] packetizer_mpeg4audio packetizer: AAC channels: 2 samplerate: 24000
[0x84431e0] avcodec encoder error: cannot find encoder MPEG Audio layer 1/2/3
*** Your FFMPEG installation is crippled.   ***
*** Please check with your FFMPEG packager. ***
*** This is NOT a VLC media player issue.   ***
[0x832bde8] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:mp3 )
[0x832bde8] stream_out_transcode stream out error: cannot create audio chain
[0x83a7b90] main packetizer error: cannot create packetizer output (mp4a)
[0x831c710] mux_ps mux: Close
$The same command works properly with Win7 but not with Ubuntu. I reinstalled ffmpeg as suggested but this didn't solve the problem. Could you help me out, please?
Thanks :)

---

### Post by WinterRain on 2010-04-18
You simply need some codecs.
Do:
```
sudo apt-get install non-free-codecs
```
You may need the medibuntu repos for this. Do first:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by calande on 2010-04-18
Thank you. I ran the second snippet but I ran into trouble:```
Hit http://downloads.sourceforge.net all Release.gpg
Hit http://downloads.sourceforge.net all Release
Ign http://downloads.sourceforge.net all/main Packages
Ign http://downloads.sourceforge.net all/main Packages
Hit http://downloads.sourceforge.net all/main Packages

Err http://packages.medibuntu.org karmic Release.gpg
  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out
Err http://packages.medibuntu.org karmic/free Translation-en_US
  Unable to connect to packages.medibuntu.org http:
Err http://packages.medibuntu.org karmic/non-free Translation-en_US
  Unable to connect to packages.medibuntu.org http:
Reading package lists...
W: Failed to fetch http://packages.medibuntu.org/dists/karmic/Release.gpg  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2  Unable to connect to packages.medibuntu.org http:

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2  Unable to connect to packages.medibuntu.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package medibuntu-keyring
$ 
```
Could you help me please?
Thanks,

---

### Post by marcoftheknight on 2010-04-19
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Packages             
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
  Unable to connect to packages.medibuntu.org http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
  Unable to connect to packages.medibuntu.org http:
Reading package lists... Done

---

### Post by calande on 2010-04-24
Today it worked fine installing :)

---

### Post by calande on 2011-02-14
Hello,

I'm having the problem again. Here's the output:
```
$ vlc "rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=210&flavour=ld" --run-time="10" --rtsp-caching="1000" --sout="#transcode{acodec=mp3}:std{access=file,mux=ps,dst='video3.mpg'}"
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8072914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb75520d4, 0xb7552048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1297343451)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3449): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
[0x83a128c] mux_ps mux: Open
libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 0) for PID 66
[0x83bcc94] ts demux error: MPEG-4 descriptor not found
[0x83e34bc] packetizer_mpeg4audio decoder: AAC channels: 2 samplerate: 24000
[0x839fb74] main stream out error: Failed to create audio filter
[0x839fb74] stream_out_transcode stream out error: Failed to find conversion filter for resampling
[0x839fb74] stream_out_transcode stream out error: cannot create audio chain
[0x83e34bc] main decoder error: cannot create packetizer output (mp4a)
[0x83a128c] mux_ps mux: Close
```

I reinstalled ffmpeg, w32codecs, and non-free-codecs, but this didn't help...Any idea?
Thanks,

---

### Post by kifetew on 2012-08-11
I had the same problem and I resolved it by installing: sudo apt-get install libavcodec-extra-53

---

### Post by wildmanne39 on 2012-08-11
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

