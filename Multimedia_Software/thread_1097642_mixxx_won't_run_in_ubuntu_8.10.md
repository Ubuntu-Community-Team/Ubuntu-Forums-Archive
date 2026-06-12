---
title: "mixxx won't run in ubuntu 8.10"
date: 2009-03-16
forum: Multimedia Software
---

### Post by arturieto on 2009-03-16
I installed ubuntu studio for i am interested of mixxx.  after installation i tried Mixxx but it won't run. after initial run, the application get lost.

I run it in a terminal and the text is:

[I]art@home-desktop:/$ mixxx
Debug: Mixxx 1.6.0~beta3 "" is starting... 
Debug: SoundManager::SoundManager() 
Debug: SampleRate 44100 
Debug: Latency 64 
Debug: SoundManager::queryDevices() 
Debug: SoundManager::clearDeviceList() 
Debug: SoundManager::closeDevices() 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Warning: QGLContext::makeCurrent(): Cannot make invalid context current.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Debug: Loading playlists and library tracks from XML... 
Debug: Track::readXML "/home/art/.mixxxtrack.xml" 
Debug: Break 
Debug: Found promo track: "Carlo Carosi - Stonewalled.mp3" 
Debug: Found promo track: "promo.xml" 
Debug: Could not parse "promo.xml" 
Debug: Found promo track: "UgressFeatChristineLitle-Redrum.mp3" 
Debug: Promo playlist has 2 songs. 
Debug: Constructed LibraryScanner!!! 
Debug: No playlists, returning 
Debug: FIXME: Need to tell the m_pPlaylistListModel to refresh in src/track.cpp on line: 1284 
Debug: Starting Library Scanner... 
Debug: Trying to add 7 songs to the library playlist 
Debug: Adjusting column widths: tracktable width = 582  1% of that is: 5.82  FIXME: this should be done when initalizing the skin. 
Debug: Shrinking Title/Comment for small screen...  
Debug: FIXME: repaintEverything switches table model and shouldn't do that when viewing the playlist model in  src/wtracktableview.cpp:  203 
Debug: selectedAPI is:  "ALSA" 
Debug: SoundManager::getDeviceList 
Debug: SoundManager::getDeviceList 
Debug: SoundManager::getDeviceList 
Debug: Warning: Creation of the midi queue failed.  Operation not permitted 
Debug: PowerMate: write():  Bad file descriptor 
Debug: PowerMate: write():  Bad file descriptor 
Debug: HerculesLinux: Constructor called 
Debug: m_pHercules init:  QThread(0x8b2bef0) 
Debug: Starting Hercules DJ Console detection 
No Hercules DJ Console found
Debug: Sorry, no love. 
Debug: isRMX =  false 
Debug: Midi OK (Workaround not required) 
Debug: setupMappings( "/usr/share/mixxx/midi/Akai MPD24.midi.xml" ) 
Debug: loadSettings: 1 0 "SlowFade" 
Debug: slotApply crossfader: 1 "SlowFade" 
Debug: BpmSchemes::readXML "/home/art/.mixxxbpmscheme.xml" 
Debug: SoundManager::setupDevices() 
Debug: Xwax Vinyl control starting with a sample rate of: 44100 
Debug: Building timecode lookup tables... 
Allocating 2097152 slots (8192Kb) for 20 bit timecode (Serato 2nd Ed., side A)
Debug: Created new VinylControlXwax! 
Debug: Xwax Vinyl control starting with a sample rate of: 44100 
Debug: Building timecode lookup tables... 
Allocating 2097152 slots (8192Kb) for 20 bit timecode (Serato 2nd Ed., side A)
Debug: Created new VinylControlXwax! 
terminate called after throwing an instance of 'int'
Aborted
art@home-desktop:/$ [/I]


please help

---

