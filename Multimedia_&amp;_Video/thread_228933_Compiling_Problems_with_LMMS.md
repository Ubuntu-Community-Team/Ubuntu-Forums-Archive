---
title: "Compiling Problems with LMMS"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by megamaced on 2006-08-03
Hello

I can't compile LMMS - The configure seems to go OK, but making the source comes out with lots of errors:


This is the output of 'make'

```
megamaced@emachines3220:~/lmms-0.2.1$ make
/usr/bin/moc -o about_dialog.moc include/about_dialog.h
/usr/bin/moc -o arp_and_chords_tab_widget.moc include/arp_and_chords_tab_widget.h
/usr/bin/moc -o automatable_button.moc include/automatable_button.h
/usr/bin/moc -o automatable_slider.moc include/automatable_slider.h
/usr/bin/moc -o automation_editor.moc include/automation_editor.h
/usr/bin/moc -o automation_pattern.moc include/automation_pattern.h
/usr/bin/moc -o automation_track.moc include/automation_track.h
/usr/bin/moc -o bb_editor.moc include/bb_editor.h
/usr/bin/moc -o bb_track.moc include/bb_track.h
/usr/bin/moc -o instrument_track.moc include/instrument_track.h
/usr/bin/moc -o combobox.moc include/combobox.h
/usr/bin/moc -o config_mgr.moc include/config_mgr.h
/usr/bin/moc -o cpuload_widget.moc include/cpuload_widget.h
/usr/bin/moc -o envelope_and_lfo_widget.moc include/envelope_and_lfo_widget.h
/usr/bin/moc -o envelope_tab_widget.moc include/envelope_tab_widget.h
/usr/bin/moc -o export_project_dialog.moc include/export_project_dialog.h
/usr/bin/moc -o fade_button.moc include/fade_button.h
/usr/bin/moc -o file_browser.moc include/file_browser.h
/usr/bin/moc -o group_box.moc include/group_box.h
/usr/bin/moc -o kmultitabbar.moc include/kmultitabbar.h
/usr/bin/moc -o kmultitabbar-qt3.moc include/kmultitabbar-qt3.h
/usr/bin/moc -o knob.moc include/knob.h
/usr/bin/moc -o lcd_spinbox.moc include/lcd_spinbox.h
/usr/bin/moc -o led_checkbox.moc include/led_checkbox.h
/usr/bin/moc -o main_window.moc include/main_window.h
/usr/bin/moc -o mixer.moc include/mixer.h
/usr/bin/moc -o name_label.moc include/name_label.h
/usr/bin/moc -o nstate_button.moc include/nstate_button.h
/usr/bin/moc -o midi_alsa_seq.moc include/midi_alsa_seq.h
/usr/bin/moc -o midi_tab_widget.moc include/midi_tab_widget.h
/usr/bin/moc -o note_play_handle.moc include/note_play_handle.h
/usr/bin/moc -o pattern.moc include/pattern.h
/usr/bin/moc -o piano_roll.moc include/piano_roll.h
/usr/bin/moc -o piano_widget.moc include/piano_widget.h
/usr/bin/moc -o pixmap_button.moc include/pixmap_button.h
/usr/bin/moc -o plugin_browser.moc include/plugin_browser.h
/usr/bin/moc -o project_notes.moc include/project_notes.h
/usr/bin/moc -o rubberband.moc include/rubberband.h
/usr/bin/moc -o qxembed.moc include/qxembed.h
/usr/bin/moc -o rename_dialog.moc include/rename_dialog.h
/usr/bin/moc -o sample_buffer.moc include/sample_buffer.h
/usr/bin/moc -o sample_track.moc include/sample_track.h
/usr/bin/moc -o setup_dialog.moc include/setup_dialog.h
/usr/bin/moc -o side_bar.moc include/side_bar.h
/usr/bin/moc -o side_bar_widget.moc include/side_bar_widget.h
/usr/bin/moc -o song_editor.moc include/song_editor.h
/usr/bin/moc -o surround_area.moc include/surround_area.h
/usr/bin/moc -o tab_bar.moc include/tab_bar.h
/usr/bin/moc -o tab_button.moc include/tab_button.h
/usr/bin/moc -o tab_widget.moc include/tab_widget.h
/usr/bin/moc -o tempo_sync_knob.moc include/tempo_sync_knob.h
/usr/bin/moc -o timeline.moc include/timeline.h
/usr/bin/moc -o tool_button.moc include/tool_button.h
/usr/bin/moc -o track_container.moc include/track_container.h
/usr/bin/moc -o track.moc include/track.h
/usr/bin/moc -o visualization_widget.moc include/visualization_widget.h
/usr/bin/moc -o volume_knob.moc include/volume_knob.h
make  all-recursive
make[1]: Entering directory `/home/megamaced/lmms-0.2.1'
Making all in buildtools
make[2]: Entering directory `/home/megamaced/lmms-0.2.1/buildtools'
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -floop-optimize2 -fgcse-sm  -fgcse-las -ftree-vectorize -ftree-loop-linear -DSINGLE_SOURCE_COMPILE -ansi -Wall -fno-exceptions -I/usr/local/include -MT bin2res.o -MD -MP -MF ".deps/bin2res.Tpo" -c -o bin2res.o bin2res.cpp; \
        then mv -f ".deps/bin2res.Tpo" ".deps/bin2res.Po"; else rm -f ".deps/bin2res.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CXX --mode=link g++  -g -O2 -floop-optimize2 -fgcse-sm  -fgcse-las -ftree-vectorize -ftree-loop-linear -DSINGLE_SOURCE_COMPILE -ansi -Wall -fno-exceptions -I/usr/local/include  -L/usr/local/lib -o bin2res  bin2res.o  -lwine
mkdir .libs
g++ -g -O2 -floop-optimize2 -fgcse-sm -fgcse-las -ftree-vectorize -ftree-loop-linear -DSINGLE_SOURCE_COMPILE -ansi -Wall -fno-exceptions -I/usr/local/include -o bin2res bin2res.o  -L/usr/local/lib -lwine
make[2]: Leaving directory `/home/megamaced/lmms-0.2.1/buildtools'
Making all in data
make[2]: Entering directory `/home/megamaced/lmms-0.2.1/data'
Making all in locale
make[3]: Entering directory `/home/megamaced/lmms-0.2.1/data/locale'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/megamaced/lmms-0.2.1/data/locale'
Making all in midi-maps
make[3]: Entering directory `/home/megamaced/lmms-0.2.1/data/midi-maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/megamaced/lmms-0.2.1/data/midi-maps'
Making all in presets
make[3]: Entering directory `/home/megamaced/lmms-0.2.1/data/presets'
Making all in AudioFileProcessor
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/presets/AudioFileProcessor'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/presets/AudioFileProcessor'
Making all in BitInvader
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/presets/BitInvader'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/presets/BitInvader'
Making all in Organic
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/presets/Organic'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/presets/Organic'
Making all in PluckedStringSynth
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/presets/PluckedStringSynth'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/presets/PluckedStringSynth'
Making all in TripleOscillator
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/presets/TripleOscillator'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/presets/TripleOscillator'
Making all in VeSTige
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/presets/VeSTige'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/presets/VeSTige'
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/presets'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/presets'
make[3]: Leaving directory `/home/megamaced/lmms-0.2.1/data/presets'
Making all in projects
make[3]: Entering directory `/home/megamaced/lmms-0.2.1/data/projects'
Making all in cool_songs
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/projects/cool_songs'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/projects/cool_songs'
Making all in covers
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/projects/covers'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/projects/covers'
Making all in demos
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/projects/demos'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/projects/demos'
Making all in misc
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/projects/misc'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/projects/misc'
Making all in recorded_loops
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/projects/recorded_loops'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/projects/recorded_loops'
Making all in templates
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/projects/templates'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/projects/templates'
Making all in tutorials
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/projects/tutorials'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/projects/tutorials'
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/projects'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/projects'
make[3]: Leaving directory `/home/megamaced/lmms-0.2.1/data/projects'
Making all in samples
make[3]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples'
Making all in basses
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/basses'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/basses'
Making all in bassloopes
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/bassloopes'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/bassloopes'
Making all in beats
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/beats'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/beats'
Making all in drums
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/drums'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/drums'
Making all in effects
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/effects'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/effects'
Making all in instruments
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/instruments'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/instruments'
Making all in latin
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/latin'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/latin'
Making all in misc
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/misc'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/misc'
Making all in shapes
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/shapes'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/shapes'
Making all in stringsnpads
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples/stringsnpads'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples/stringsnpads'
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/data/samples'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples'
make[3]: Leaving directory `/home/megamaced/lmms-0.2.1/data/samples'
Making all in themes
make[3]: Entering directory `/home/megamaced/lmms-0.2.1/data/themes'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/megamaced/lmms-0.2.1/data/themes'
Making all in track_icons
make[3]: Entering directory `/home/megamaced/lmms-0.2.1/data/track_icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/megamaced/lmms-0.2.1/data/track_icons'
make[3]: Entering directory `/home/megamaced/lmms-0.2.1/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/megamaced/lmms-0.2.1/data'
make[2]: Leaving directory `/home/megamaced/lmms-0.2.1/data'
Making all in plugins
make[2]: Entering directory `/home/megamaced/lmms-0.2.1/plugins'
Making all in audio_file_processor
make[3]: Entering directory `/home/megamaced/lmms-0.2.1/plugins/audio_file_processor'
../../buildtools/bin2res artwork.png logo.png loop_off.png loop_on.png reverse_off.png reverse_on.png > embedded_resources.h
/usr/bin/moc -o audio_file_processor.moc audio_file_processor.h
make  all-am
make[4]: Entering directory `/home/megamaced/lmms-0.2.1/plugins/audio_file_processor'
if /bin/sh ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -I../../src/lib -I.    -DQT3 -I/usr/include/qt3 -D_REENTRANT -DQT_THREAD_SUPPORT -DPLUGIN_NAME="audiofileprocessor" -g -O2 -floop-optimize2 -fgcse-sm  -fgcse-las -ftree-vectorize -ftree-loop-linear -DSINGLE_SOURCE_COMPILE -ansi -Wall -fno-exceptions -I/usr/local/include -MT audio_file_processor.lo -MD -MP -MF ".deps/audio_file_processor.Tpo" -c -o audio_file_processor.lo audio_file_processor.cpp; \
        then mv -f ".deps/audio_file_processor.Tpo" ".deps/audio_file_processor.Plo"; else rm -f ".deps/audio_file_processor.Tpo"; exit 1; fi
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -I../../src/lib -I. -DQT3 -I/usr/include/qt3 -D_REENTRANT -DQT_THREAD_SUPPORT -DPLUGIN_NAME=audiofileprocessor -g -O2 -floop-optimize2 -fgcse-sm -fgcse-las -ftree-vectorize -ftree-loop-linear -DSINGLE_SOURCE_COMPILE -ansi -Wall -fno-exceptions -I/usr/local/include -MT audio_file_processor.lo -MD -MP -MF .deps/audio_file_processor.Tpo -c audio_file_processor.cpp  -fPIC -DPIC -o .libs/audio_file_processor.o
In file included from ../../include/qt3support.h:33,
                 from audio_file_processor.cpp:26:
/usr/include/qt3/qglobal.h:773:21: error: qconfig.h: No such file or directory
/usr/include/qt3/qglobal.h:783:22: error: qmodules.h: No such file or directory
../../include/automatable_object.h: In member function 'virtual void automatableObject<T, EDIT_STEP_TYPE>::saveSettings(QDomDocument&, QDomElement&, const QString&)':
../../include/automatable_object.h:285: error: 'QDomNode' was not declared in this scope
../../include/automatable_object.h:285: error: expected `;' before 'node'
../../include/automatable_object.h:287: error: 'node' was not declared in this scope
../../include/automatable_object.h:293: error: invalid use of undefined type 'struct QDomDocument'
../../include/journalling_object.h:52: error: forward declaration of 'struct QDomDocument'
../../include/automatable_object.h:295: error: invalid use of undefined type 'struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'struct QDomElement'
../../include/automatable_object.h:297: error: invalid use of undefined type 'struct QDomDocument'
../../include/journalling_object.h:52: error: forward declaration of 'struct QDomDocument'
../../include/automatable_object.h:299: error: invalid use of undefined type 'struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'struct QDomElement'
../../include/automatable_object.h:303: error: invalid use of undefined type 'struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'struct QDomElement'
../../include/automatable_object.h: In member function 'virtual void automatableObject<T, EDIT_STEP_TYPE>::loadSettings(const QDomElement&, const QString&)':
../../include/automatable_object.h:310: error: 'QDomNode' was not declared in this scope
../../include/automatable_object.h:310: error: expected `;' before 'node'
../../include/automatable_object.h:312: error: 'node' was not declared in this scope
../../include/automatable_object.h:325: error: invalid use of undefined type 'const struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'const struct QDomElement'
../../include/mmp.h: At global scope:
../../include/mmp.h:45: error: invalid use of undefined type 'struct QDomDocument'
../../include/journalling_object.h:52: error: forward declaration of 'struct QDomDocument'
../../include/mmp.h:103: error: field 'm_content' has incomplete type
../../include/mmp.h:104: error: field 'm_head' has incomplete type
../../include/mmp.h: In member function 'QDomElement& multimediaProject::content()':
../../include/mmp.h:74: error: 'm_content' was not declared in this scope
../../include/mmp.h: In member function 'QDomElement& multimediaProject::head()':
../../include/mmp.h:78: error: 'm_head' was not declared in this scope
../../include/config_mgr.h: At global scope:
../../include/config_mgr.h:72: error: invalid use of undefined type 'struct QDialog'
/usr/include/qt3/qwindowdefs.h:54: error: forward declaration of 'struct QDialog'
../../include/config_mgr.h:73: warning: 'class configManager' has virtual functions but non-virtual destructor
audio_file_processor.cpp: In member function 'virtual void audioFileProcessor::saveSettings(QDomDocument&, QDomElement&)':
audio_file_processor.cpp:292: error: invalid use of undefined type 'struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'struct QDomElement'
audio_file_processor.cpp:296: error: invalid use of undefined type 'struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'struct QDomElement'
audio_file_processor.cpp:298: error: invalid use of undefined type 'struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'struct QDomElement'
audio_file_processor.cpp:301: error: invalid use of undefined type 'struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'struct QDomElement'
audio_file_processor.cpp: In member function 'virtual void audioFileProcessor::loadSettings(const QDomElement&)':
audio_file_processor.cpp:314: error: invalid use of undefined type 'const struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:316: error: invalid use of undefined type 'const struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:318: error: invalid use of undefined type 'const struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:320: error: invalid use of undefined type 'const struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:322: error: invalid use of undefined type 'const struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:323: error: invalid use of undefined type 'const struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp: In member function 'virtual void audioFileProcessor::dropEvent(QDropEvent*)':
audio_file_processor.cpp:451: error: invalid use of undefined type 'struct QDomElement'
../../include/journalling_object.h:53: error: forward declaration of 'struct QDomElement'
../../include/automatable_object.h: In member function 'void automatableObject<T, EDIT_STEP_TYPE>::saveSettings(QDomDocument&, QDomElement&, const QString&) [with T = bool, EDIT_STEP_TYPE = signed char]':
audio_file_processor.cpp:304:   instantiated from here
../../include/automatable_object.h:284: error: 'pattern_element' has incomplete type
../../include/automatable_object.h:284: error: storage size of 'pattern_element' isn't known
../../include/automatable_object.h:297: error: 'element' has incomplete type
../../include/automatable_object.h:297: error: storage size of 'element' isn't known
../../include/automatable_object.h: In member function 'void automatableObject<T, EDIT_STEP_TYPE>::saveSettings(QDomDocument&, QDomElement&, const QString&) [with T = float, EDIT_STEP_TYPE = float]':
audio_file_processor.cpp:306:   instantiated from here
../../include/automatable_object.h:284: error: 'pattern_element' has incomplete type
../../include/automatable_object.h:284: error: storage size of 'pattern_element' isn't known
../../include/automatable_object.h:297: error: 'element' has incomplete type
../../include/automatable_object.h:297: error: storage size of 'element' isn't known
make[4]: *** [audio_file_processor.lo] Error 1
make[4]: Leaving directory `/home/megamaced/lmms-0.2.1/plugins/audio_file_processor'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/megamaced/lmms-0.2.1/plugins/audio_file_processor'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/megamaced/lmms-0.2.1/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/megamaced/lmms-0.2.1'
make: *** [all] Error 2
megamaced@emachines3220:~/lmms-0.2.1$
```

Anyone know what the problem might be?

Thanks in advance

---

### Post by megamaced on 2006-08-03
okay, nevermind!

Google turned up the answers I was looking for!

---

### Post by dolson on 2006-08-03
sudo apt-get build-dep lmms

:)

You could also make your own .deb package easily.. I should make it into a tutorial.

---

### Post by megamaced on 2006-08-04
I would have installed the LMMS package in the ubuntu repositories, but it's lacking VST support and it's quite old anyway.

I have successfully compiled LMMS now. Turns out I was missing one of the QT3 development packages.

---

### Post by Alchemist00 on 2008-06-24
i know this has been dormant for quite a while. but i ran into the same error, what exactly did you do to fix it? btw i am using fedora 9. anyway please help its driving me crazy!

---

