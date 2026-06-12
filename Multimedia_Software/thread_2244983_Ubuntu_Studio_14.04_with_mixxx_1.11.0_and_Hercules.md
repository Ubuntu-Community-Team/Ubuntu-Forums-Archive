---
title: "Ubuntu Studio 14.04 with mixxx 1.11.0 and Hercules DJ controller Mp3 e2"
date: 2014-09-20
forum: Multimedia Software
---

### Post by versus69 on 2014-09-20
Hello!
I upgrade from ubuntu 12.04 to 14.04 and after that, I find some problem in Mixxx 1.11.0 with Hercules Dj Control Mp3 e2. Before it was working with 12.04.
The first was a Kenel panic message, that I solved installing snd-usb-audio-rmx2-dkms_0.12_all.deb (here: [https://bugs.launchpad.net/mixxx/+bug/1096687](https://bugs.launchpad.net/mixxx/+bug/1096687) ).
Now mixxx is partially working, cause I lost controllers: in preferences, controllers I see "No controllers available".
If I run with *sudo mixxx*, I find controllers, but not working (there's also an usb controller).
After that I decided to install ubuntu studio 12.04, but still same problem...
How I can solve this?  
Any help? 
Thank you

---

### Post by versus69 on 2014-09-23
Ciao!
I do not find solution. I format and install ubuntu studio 14.04 and I have same problem: no conttrolers available.
Here I post mixxx from terminal:

[I][SIZE=1]```
~$ mixxx
Debug [Main]: Mixxx 1.11.0 "(bzr 1.11 r3885+; built on: Apr 25 2014 @ 04:13:53; flags: bulk hid hifieq mad optimize=9 qdebug shoutcast vamp verbose vinylcontrol)" is starting... 
Debug [Main]: Qt version is: 4.8.6 
Debug [Main]: Configuration file is at the current version 1.11.0 
Debug [Main]: Loading translations for locale "it_CH" from translations folder "/usr/share/mixxx/translations/" : success 
Debug [Main]: ConfigObject: Could not read "" 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Channel1]" , "vinylcontrol_mode" ) 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Channel2]" , "vinylcontrol_mode" ) 
Debug [Main]: JACK client name set 
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connessione rifiutata (111)
bt_audio_service_open: connect() failed: Connessione rifiutata (111)
bt_audio_service_open: connect() failed: Connessione rifiutata (111)
bt_audio_service_open: connect() failed: Connessione rifiutata (111)
Cannot connect to server socket err = File o directory non esistente
Cannot connect to server request channel
jack server is not running or cannot be started
Warning [Main]: ControlObject::getControl returning NULL for ( "[Flanger]" , "lfoDepth" ) 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Flanger]" , "lfoDelay" ) 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Flanger]" , "lfoPeriod" ) 
Debug [Main]: Available QtSQL drivers: ("QSQLITE", "QMYSQL3", "QMYSQL") 
Debug [Main]: DB status: "/home/stefano/.mixxx/mixxxdb.sqlite" = true 
Debug [Main]: SchemaManager::upgradeToSchemaVersion already at version 17 
Debug [Main]: TrackDAO::initialize QThread(0x934c450, name = "Main") "qt_sql_default_connection" 
Debug [Main]: CrateDAO::initialize() 
Debug [Main]: CueDAO::initialize QThread(0x934c450, name = "Main") "qt_sql_default_connection" 
Debug [Main]: Default quick links: ("/home/stefano/Musica/", "/home/stefano/Scrivania/", "/home/stefano/Documenti/") 
Debug [Main]: Appending Quick Link:  "Musica" --- "/home/stefano/Musica/" 
Debug [Main]: Appending Quick Link:  "Scrivania" --- "/home/stefano/Scrivania/" 
Debug [Main]: Appending Quick Link:  "Documenti" --- "/home/stefano/Documenti/" 
Debug [Main]: Creating session history playlist name: "2014-09-23" 
Debug [Main]: Committing transaction on "qt_sql_default_connection" result: true 
Debug [Main]: Traktor Library Location=[ "/home/stefano/collection.nml" ] 
Debug [Main]: AnalyserWaveform::AnalyserWaveform() 
Debug [Main]: Setting VAMP_PATH to:  "/usr/lib/mixxx/plugins/vamp:/home/stefano/.mixxx/plugins/vamp/:/usr/bin/lin32_build/vamp-plugins:/usr/bin/lin64_build/vamp-plugins" 
Debug [Main]: Creating ControllerManager 
Debug [Main]: Extension ".bulk.xml" total 1 presets 
Debug [Main]: Extension ".hid.xml" total 7 presets 
Debug [Main]: Extension ".midi.xml" total 79 presets 
Debug [Main]: Setting VAMP_PATH to:  "/usr/lib/mixxx/plugins/vamp:/home/stefano/.mixxx/plugins/vamp/:/usr/bin/lin32_build/vamp-plugins:/usr/bin/lin64_build/vamp-plugins:/usr/lib/mixxx/plugins/vamp:/home/stefano/.mixxx/plugins/vamp/:/usr/bin/lin32_build/vamp-plugins:/usr/bin/lin64_build/vamp-plugins" 
Debug [Main]: VampPluginLoader::listPlugins() returned 3 plugins 
Debug [Main]: Plugin output displayname: "mixxxbpmdetection:0" "SoundTouch BPM Detector (Legacy)" 
Debug [Main]: Plugin output displayname: "qm-barbeattracker:0" "Bar and Beat Tracker" 
Debug [Main]: Plugin output displayname: "qm-barbeattracker:1" "Bar and Beat Tracker" 
Debug [Main]: Plugin output displayname: "qm-barbeattracker:2" "Bar and Beat Tracker" 
Debug [Main]: Plugin output displayname: "qm-barbeattracker:3" "Bar and Beat Tracker" 
Debug [Main]: Plugin output displayname: "qm-tempotracker:0" "Queen Mary Tempo and Beat Tracker" 
Debug [Main]: Plugin output displayname: "qm-tempotracker:1" "Queen Mary Tempo and Beat Tracker" 
Debug [Main]: Plugin output displayname: "qm-tempotracker:2" "Queen Mary Tempo and Beat Tracker" 
Debug [Main]: ControllerManager::getControllerList 
Debug [Main]: SoundManager::setupDevices() 
Debug [Main]: SoundDevicePortAudio::open() "0, HDA Intel PCH: ALC269VB Analog (hw:0,0)" 
Debug [Main]: framesPerBuffer: 1024 
Debug [Main]: Requested sample rate:  44100 Hz, latency: 23.22 ms 
Debug [Main]: Output channels: 2 | Input channels: 0 
Debug [Main]: Opening stream with id 0 
Debug [Main]: Opened PortAudio stream successfully... starting 
Debug [Main]: Dynamically loaded PortAudio library 
Debug [Main]: PortAudio: Started stream successfully 
Debug [Main]:    Actual sample rate:  44100 Hz, latency: 23.22 ms 
Debug [Main]: Using "HDA Intel PCH: ALC269VB Analog (hw:0,0)" as output sound device clock reference 
Debug [Main]: 1 output sound devices opened 
Debug [Main]: 0 input  sound devices opened 
Debug [Main]: Set root GL Context widget valid: QGLWidget(0x9bc8bd8) true 
Debug [Main]: Created root GL Context valid: 0x9d68f68 true 
Debug [Main]: Root GL Context format: 
Debug [Main]: Double Buffering: true 
Debug [Main]: Swap interval: 0 
Debug [Main]: Depth buffer: true 
Debug [Main]: Direct rendering: true 
Debug [Main]: Has overlay: false 
Debug [Main]: RGBA: true 
Debug [Main]: Sample buffers: false 
Debug [Main]: Stencil buffers: true 
Debug [Main]: Stereo: false 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Spinny1]" , "show_spinny" ) 
Warning [Main]: Requested control does not exist: "[Spinny1],show_spinny" Creating it. 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Spinny2]" , "show_spinny" ) 
Warning [Main]: Requested control does not exist: "[Spinny2],show_spinny" Creating it. 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Samplers]" , "show_samplers" ) 
Warning [Main]: Requested control does not exist: "[Samplers],show_samplers" Creating it. 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Vinylcontrol]" , "show_vinylcontrol" ) 
Warning [Main]: Requested control does not exist: "[Vinylcontrol],show_vinylcontrol" Creating it. 
Warning [Main]: ControlObject::getControl returning NULL for ( "[PreviewDeck]" , "show_previewdeck" ) 
Warning [Main]: Requested control does not exist: "[PreviewDeck],show_previewdeck" Creating it. 
Debug [Main]: Invalid node name in skin: "manifest" 
Debug [Main]: Making property binder for "visible" 
Warning [Main]: WaveformSignalColors::fallBackFromSignalColor - skin do not provide low/mid/high signal colors 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Sampler1]" , "" ) 
Warning [Main]: WaveformSignalColors::fallBackFromSignalColor - skin do not provide low/mid/high signal colors 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Sampler2]" , "" ) 
Warning [Main]: WaveformSignalColors::fallBackFromSignalColor - skin do not provide low/mid/high signal colors 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Sampler3]" , "" ) 
Warning [Main]: WaveformSignalColors::fallBackFromSignalColor - skin do not provide low/mid/high signal colors 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Sampler4]" , "" ) 
Debug [Main]: Making property binder for "visible" 
Warning [Main]: ControlObject::getControl returning NULL for ( "[PreviewDeck1]" , "" ) 
Debug [Main]: Recordings folder set to "/home/stefano/Musica/Mixxx/Recordings" 
Debug [Main]: PrepareLibraryTableModel(0xa4f5360) select() took 1 ms 
Debug [Main]: PrepareLibraryTableModel(0xa4f5360) select() took 1 ms 
Debug [Main]: DlgPrepare(0xa4c6798, name = "DlgPrepare") analysisActive false 
Debug [Main]: Making property binder for "visible" 
Debug [Main]: Making property binder for "visible" 
Debug [Main]: WSpinny(): Created QGLWidget, Context Valid: true Sharing: true 
Debug [Main]: Created QGLWidget. Context Valid: true Sharing: true 
Warning [Main]: WaveformSignalColors::fallBackFromSignalColor - skin do not provide low/mid/high signal colors 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Channel1]" , "" ) 
Debug [Main]: WaveformWidgetFactory::setWaveformWidget - waveform widget added in factory, index 0 
Debug [Main]: Created QGLWidget. Context Valid: true Sharing: true 
Warning [Main]: WaveformSignalColors::fallBackFromSignalColor - skin do not provide low/mid/high signal colors 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Channel2]" , "" ) 
Debug [Main]: WaveformWidgetFactory::setWaveformWidget - waveform widget added in factory, index 1 
Debug [Main]: Making property binder for "visible" 
Debug [Main]: WSpinny(): Created QGLWidget, Context Valid: true Sharing: true 
Debug [Main]: Making property binder for "visible" 
Warning [Main]: WaveformSignalColors::fallBackFromSignalColor - skin do not provide low/mid/high signal colors 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Channel1]" , "" ) 
Warning [Main]: WaveformSignalColors::fallBackFromSignalColor - skin do not provide low/mid/high signal colors 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Channel2]" , "" ) 
Warning [Main]: ControlObject::getControl returning NULL for ( "[Microphone]" , "show_microphone" ) 
Debug [Main]: MixxxLibraryFeature::activate() 
Debug [Main]: LibraryTableModel(0x99a1c48) select() took 0 ms 
Debug [Main]: WSearchLineEdit::restoreSearch( "" ) 
Debug [Controller]: ControllerManager: Setting up devices 
Debug [Main]: Constructed LibraryScanner 
Debug [Controller]: Scanning PortMIDI devices: 
Debug [Main]: iTunes Album Art path is: "" 
Debug [Main]: Displaying mixxx 
Debug [Controller]: Scanning USB Bulk devices: 
Debug [Controller]: Scanning HID devices: 
Debug [Controller]: Found 0x0 0x0 "r8192" S/N 0x0 "Interface 0" 
Warning [Controller]: USB permissions problem (or device error.) Your account needs write access to USB HID controllers. 
Debug [Controller]: ControllerManager::getControllerList 
Debug [Controller]: Controller polling stopped. 
Debug [Main]: resize QSize(1366, 727) 
Debug [Main]: Running Mixxx 
Warning [Main]: WaveformRenderBackground::generateImage() - file( "/usr/share/mixxx/skins/LateNight1366x768-WXGA/style/style_bg_waveform1.png" ) 1050 x 72 do not fit the waveform widget size 859 x 74 
Warning [Main]: WaveformRenderBackground::generateImage() - file( "/usr/share/mixxx/skins/LateNight1366x768-WXGA/style/style_bg_waveform2.png" ) 1050 x 74 do not fit the waveform widget size 859 x 74 
```
[/SIZE][/I]
Any help?
Thanks and buena vida!

---

### Post by versus69 on 2014-09-26
I solved the problem thanks to the support forum of Mixxx. 
Here is the discussion: [No]("http://mixxx.org/forums/viewtopic.php?f=3&t=6624")[ controllers available]("http://mixxx.org/forums/viewtopic.php?f=3&t=6624") 
Here the page where I found the solution in the "**Mixxx says I have no HID controllers attached even though ****I do**": [http://www.mixxx.org/wiki/doku.php/troubleshooting](http://www.mixxx.org/wiki/doku.php/troubleshooting) 
Buena vida-)

---

### Post by mörgæs on 2014-09-26
Good, please mark the thread solved using 'thread tools'.

---

