---
title: "Dragon Player frozen (paused?) at startup on Oneiric"
date: 2013-02-14
forum: Multimedia Software
---

### Post by sbalfour on 2013-02-14
Symptoms
--------
When I open Dragon Player from UI and browse to a .wmv file (for example) and 
select it to play, the first frame is displayed, and the video appears paused.
If I manually move the slider, it will similarly display the first frame at the
stop point, and no more.  Clicking the Play/Pause button repeatedly yields no
response.  All file types yield the same result.  These files play ok on other
players on Kubuntu (VLC, RealPlayer) and Windows XP (Windows Media Player), so 
the files are probably ok.  Large and small video files are similarly affected.

I tried executing Dragon from command line, with the same results. 

I tried reinstalling phonon-backend-gstreamer, and it changed nothing.

I tried the following:

$ export PHONON_DEBUG=5
$ export PHONON_BACKEND_DEBUG=5
$ export PHONON_PULSEAUDIO_DEBUG=5
$ export PHONON_VLC_DEBUG=5
$ export PHONON_GST_DEBUG=5
$ dragon ./video384.wmv

The terminal output was:

Phonon::KdePlatformPlugin(0x88df128) 
0x88df130 
"PulseSupport(2): Probing for PulseAudio..." 
"PulseSupport(2): context_state_callback Authorizing" 
"PulseSupport(2): context_state_callback Setting Name" 
"PulseSupport(2): context_state_callback Ready" 
"PulseSupport(2): Brand New Output Device Found." 
"PulseSupport(2): Brand New Capture Device Found." 
"PulseSupport(2): Output Device Priority List:" 
"PulseSupport(2):   Phonon Category -1" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 0" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 1" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 2" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 3" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 4" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 5" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2): Capture Device Priority List:" 
"PulseSupport(2):   Phonon Category -1" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 3" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 4" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 5" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2): context_state_callback Terminated" 
"PulseSupport(2): PulseAudio probe complete." 
"PulseSupport(2): PulseAudio support enabled" 
"PulseSupport(2): Enabled Breakdown: mEnabled: Yes, s_pulseActive Yes" 
"PGST(2): Using GStreamer 0.10.35" 
"PGST(2): AudioOutput using pulsesink" 
"PGST(2): Creating X11 overlay renderer" 
calling setAspectRatio on the backend  0 
"PGST(2): AudioOutput using pulsesink" 
"PulseSupport(2): Initialising streamindex {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
"PulseSupport(2): Setting role to video for streamindex {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
void Phonon::FrontendInterfacePrivate::_backendObjectChanged() 
void Phonon::FrontendInterfacePrivate::_backendObjectChanged() 
"PGST(2): Backend connected Phonon::Gstreamer::MediaObject to Phonon::Gstreamer::VideoWidget" 
"PGST(2): Backend connected Phonon::Gstreamer::MediaObject to Phonon::Gstreamer::AudioOutput" 
"PulseSupport(2): Attempting to set volume to 1 for Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::begin: Paint device returned engine == 0, type: 2
"PGST(2): Backend connected Phonon::Gstreamer::MediaObject to Phonon::Gstreamer::AudioDataOutput" 
QPainter::begin: Paint device returned engine == 0, type: 2
"PulseSupport(2): context_state_callback Authorizing" 
"PulseSupport(2): context_state_callback Setting Name" 
"PulseSupport(2): context_state_callback Ready" 
"PulseSupport(2): Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc} is gone at the PA end. Marking it as invalid in our cache as we may reuse it." 
"PulseSupport(2): Found PulseAudio stream index 7 for Phonon Output Stream {f691d6a4-1cfa-4acb-9a1d-0724db989b51}" 
"PulseSupport(2): Found PulseAudio stream index 8 for Phonon Output Stream {f691d6a4-1cfa-4acb-9a1d-0724db989b51}" 
"PulseSupport(2): Found PulseAudio stream index 10 for Phonon Output Stream {f691d6a4-1cfa-4acb-9a1d-0724db989b51}" 
"PulseSupport(2): Found PulseAudio stream index 205 for Phonon Output Stream {f691d6a4-1cfa-4acb-9a1d-0724db989b51}" 
"PulseSupport(2): Found PulseAudio stream index 207 for Phonon Output Stream {f691d6a4-1cfa-4acb-9a1d-0724db989b51}" 
"PulseSupport(2): Found PulseAudio stream index 253 for Phonon Output Stream {f691d6a4-1cfa-4acb-9a1d-0724db989b51}" 
"PulseSupport(2): Change to Existing Output Device (may be Added/Removed or something else)" 
"PulseSupport(2): Change to Existing Capture Device (may be Added/Removed or something else)" 
void Phonon::FactoryPrivate::objectDescriptionChanged(Phonon::ObjectDescriptionType) 0 
void Phonon::FactoryPrivate::objectDescriptionChanged(Phonon::ObjectDescriptionType) 4 
"PulseSupport(2): Output Device Priority List:" 
"PulseSupport(2):   Phonon Category -1" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 0" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 1" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 2" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 3" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 4" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 5" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2): Capture Device Priority List:" 
"PulseSupport(2):   Phonon Category -1" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 3" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 4" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
"PulseSupport(2):   Phonon Category 5" 
"PulseSupport(2):     1. Internal Audio Analog Stereo (Available: 1)" 
void Phonon::MediaObject::setCurrentSource(const Phonon::MediaSource&) 1  QUrl( "file:///media/cc8a8bb1-7a08-4046-8497-33cb5405b6b3/Video/Porn/VRundressinginbed.wmv" )  "" 
void Phonon::MediaObjectPrivate::_k_currentSourceChanged(const Phonon::MediaSource&) 
"PGST(3): Dumping setSource-mrl-file%3A%2F%2F%2Fmedia%2Fcc8a8bb1-7a08-4046-8497-33cb5405b6b3%2FVideo%2FPorn%2FVRundressinginbed.wmv.dot  (MediaObject 0x8d65c98)" 
"PGST(3): Dumping setSource-complete-file%3A%2F%2F%2Fmedia%2Fcc8a8bb1-7a08-4046-8497-33cb5405b6b3%2FVideo%2FPorn%2FVRundressinginbed.wmv.dot  (MediaObject 0x8d65c98)" 
"PGST(2): Begin source load  (MediaObject 0x8d65c98)" 
QPainter::begin: Paint device returned engine == 0, type: 2
"PGST(3): State changed from null to ready  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 2 time(s) 
"PGST(3): gstreamer: pipeline state set to ready  (MediaObject 0x8d65c98)" 
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::begin: Paint device returned engine == 0, type: 2
  PGST: Last message repeated 2 time(s) 
"PGST(3): State changed from null to ready  (MediaObject 0x8d65c98)" 
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
"PGST(2): Video track connected  (MediaObject 0x8d65c98)" 
"PGST(2): Audio track connected  (MediaObject 0x8d65c98)" 
QPainter::begin: Paint device returned engine == 0, type: 2
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 1 time(s) 
"PGST(2): Meta tags found  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 2 time(s) 
"PGST(3): State changed from null to ready  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 12 time(s) 
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 7 time(s) 
"PGST(3): State changed from null to ready  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 13 time(s) 
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 12 time(s) 
"PGST(2): New video size 450 x 300" 
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
"PulseSupport(2): Found PulseAudio stream index 301 for Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
"PulseSupport(2): Found PulseAudio stream index 301 for Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
"PulseSupport(2): Found PulseAudio stream index 301 for Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
"PulseSupport(2): Found PulseAudio stream index 301 for Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
  PGST: Last message repeated 7 time(s) 
"PGST(2): gstreamer: pipeline state set to paused  (MediaObject 0x8d65c98)" 
"PGST(2): Stream is seekable  (MediaObject 0x8d65c98)" 
"PGST(3): Dumping updateSeekable-true.dot  (MediaObject 0x8d65c98)" 
"PGST(2): phonon state request: Playing  (MediaObject 0x8d65c98)" 
"PGST(2): Playing state is now pending" 
Metadata ready, sending to zeitgeist 
"PGST(2): Video track connected  (MediaObject 0x8d65c98)" 
"PGST(2): Audio track connected  (MediaObject 0x8d65c98)" 
"PGST(3): State changed from paused to ready  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 34 time(s) 
"PGST(3): gstreamer: pipeline state set to ready  (MediaObject 0x8d65c98)" 
"PGST(3): State changed from ready to null  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 30 time(s) 
"PGST(3): State changed from null to ready  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 29 time(s) 
"PGST(3): gstreamer: pipeline state set to ready  (MediaObject 0x8d65c98)" 
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 19 time(s) 
"PGST(3): State changed from null to ready  (MediaObject 0x8d65c98)" 
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
QPainter::begin: Paint device returned engine == 0, type: 2
  PGST: Last message repeated 2 time(s) 
"PGST(2): Meta tags found  (MediaObject 0x8d65c98)" 
Metadata ready, sending to zeitgeist 
Metadata ready, sending to zeitgeist 
  PGST: Last message repeated 2 time(s) 
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 3 time(s) 
"PGST(2): New video size 450 x 300" 
"PGST(3): State changed from ready to paused  (MediaObject 0x8d65c98)" 
"PulseSupport(2): Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc} is gone at the PA end. Marking it as invalid in our cache as we may reuse it." 
"PulseSupport(2): Found PulseAudio stream index 302 for Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
"PulseSupport(2): Found PulseAudio stream index 302 for Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
"PulseSupport(2): Found PulseAudio stream index 302 for Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
"PulseSupport(2): Found PulseAudio stream index 302 for Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 
  PGST: Last message repeated 7 time(s) 
"PGST(2): gstreamer: pipeline state set to paused  (MediaObject 0x8d65c98)" 
"PGST(2): Stream is seekable  (MediaObject 0x8d65c98)" 
"PGST(3): Dumping updateSeekable-true.dot  (MediaObject 0x8d65c98)" 
"PGST(2): phonon state request: Playing  (MediaObject 0x8d65c98)" 
Metadata ready, sending to zeitgeist 
"PGST(3): State changed from paused to playing  (MediaObject 0x8d65c98)" 
  PGST: Last message repeated 34 time(s) 
"PGST(2): gstreamer: pipeline state set to playing  (MediaObject 0x8d65c98)" 
"PGST(2): phonon state changed: Playing  (MediaObject 0x8d65c98)" 
State changed from 0 to 2 -> sending to zeitgeist. 
"PulseSupport(2): Found PulseAudio stream index 302 for Phonon Output Stream {a5483418-0609-42c0-9eb5-b20f2491c3dc}" 

$ file ./video384.wmv
./video384 Microsoft ASF

$ mediainfo video384.wmv
General
Complete name                            : video384.wmv
Format                                   : Windows Media
File size                                : 38.1 MiB
Duration                                 : 6mn 43s
Overall bit rate mode                    : Variable
Overall bit rate                         : 793 Kbps
Maximum Overall bit rate                 : 1 047 Kbps
Movie name                               : BTS - 2932 Strip
Encoded date                             : UTC 2006-07-25 07:23:08.733
Copyright                                : 2006 Suze Randall

Video
ID                                       : 2
Format                                   : VC-1
Format profile                           : MP@ML
Codec ID                                 : WMV3
Codec ID/Info                            : Windows Media Video 9
Codec ID/Hint                            : WMV3
Description of the codec                 : Windows Media Video 9
Duration                                 : 6mn 43s
Bit rate mode                            : Variable
Bit rate                                 : 748 Kbps
Width                                    : 450 pixels
Height                                   : 300 pixels
Display aspect ratio                     : 3:2
Frame rate                               : 29.970 fps
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.185
Stream size                              : 36.0 MiB (94%)
Language                                 : English (US)

Audio
ID                                       : 1
Format                                   : WMA
Format version                           : Version 2
Codec ID                                 : 161
Codec ID/Info                            : Windows Media Audio
Description of the codec                 : Windows Media Audio 9.1 -  22 kbps, 22 kHz, stereo 2-pass CBR
Duration                                 : 6mn 43s
Bit rate mode                            : Constant
Bit rate                                 : 22.0 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 22.05 KHz
Bit depth                                : 16 bits
Stream size                              : 1.06 MiB (3%)
Language                                 : English (US)


Hardware
--------
4G ram
Opteron 285 2.6Ghz (dual core)
74Gb Raptor 10K RPM
Nvidia GeForce 8800

Software Versions
-----------------
Kububtu 11.10 with all available updates
KDE 4.7.4
Qt 4.7.4
Dragon Player 2.0

Relevant packages installed
--------------------------
gstreamer0.10-alsa                             
gstreamer0.10-ffmpeg                          
gstreamer0.10-fluendo-mp3                    
gstreamer0.10-gconf                         
gstreamer0.10-packagekit                   
gstreamer0.10-pitfdll                     
gstreamer0.10-plugins-bad                
gstreamer0.10-plugins-bad-multiverse    
gstreamer0.10-plugins-base             
gstreamer0.10-plugins-good            
gstreamer0.10-plugins-ugly           
gstreamer0.10-pulseaudio            
gstreamer0.10-qapt                 
gstreamer0.10-x                    
libgstreamer-plugins-base0.10-0   
libgstreamer0.10-0               
libqtgstreamer-0.10-0           
phonon-backend-gstreamer       
w32codecs
dragonplayer4:4.7.4-0ubuntu0.1
kubuntu-restricted-extras

What's the story here?  The codes are being found, or no image at all could be displayed.  It's like some pipe isn't being buffered or connected.
                                                                                         Stuart

---

