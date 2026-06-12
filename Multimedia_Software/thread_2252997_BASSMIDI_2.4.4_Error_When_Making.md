---
title: "BASSMIDI 2.4.4 Error When Making"
date: 2014-11-16
forum: Multimedia Software
---

### Post by tdogmonster1337 on 2014-11-16
I am trying to build the 'miditest' program that comes with the BASSMIDI Audio Library.

I downloaded it here:
[http://www.mediafire.com/download/t2gpvvoq7n21asi/BASSMIDI.zip](http://www.mediafire.com/download/t2gpvvoq7n21asi/BASSMIDI.zip)

when using the 'make command to try to build the 'miditest' program that came with BASSMIDI, make gives me errors. Here is the full output:

```

cc -Os -I/home/blueberrypie87/BASSMIDI/linux/BASSMIDI -L/home/blueberrypie87/BASSMIDI/linux/BASSMIDI -L/home/blueberrypie87/BASSMIDI/linux/BASSMIDI/x64 -lbassmidi -lbass -Wl,-rpath,/home/blueberrypie87/BASSMIDI/linux/BASSMIDI:/home/blueberrypie87/BASSMIDI/linux/BASSMIDI/x64 `pkg-config gtk+-2.0 --cflags --libs` `pkg-config libglade-2.0 --cflags --libs` `pkg-config gthread-2.0 --cflags --libs` -export-dynamic -D'GLADE_PATH="/home/blueberrypie87/BASSMIDI/linux/BASSMIDI/miditest/"' miditest.c -o miditest
miditest.c: In function ‘LyricSync’:
miditest.c:56:34: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  BASS_MIDI_StreamGetMark(channel,(DWORD)user,data,&mark); // get the lyric/text
                                  ^
miditest.c:69:2: warning: field precision specifier ‘.*’ expects argument of type ‘int’, but argument 3 has type ‘long int’ [-Wformat=]
  sprintf(p,"%.*s",lyrics+sizeof(lyrics)-p-1,text); // add the text to the lyrics buffer
  ^
miditest.c: In function ‘main’:
miditest.c:249:2: warning: ‘g_thread_init’ is deprecated (declared at /usr/include/glib-2.0/glib/deprecated/gthread.h:261) [-Wdeprecated-declarations]
  g_thread_init(NULL);
  ^
/tmp/ccOS51Jp.o: In function `EndSync':
miditest.c:(.text+0x9): undefined reference to `gdk_threads_enter'
miditest.c:(.text+0xe): undefined reference to `gtk_label_get_type'
miditest.c:(.text+0x22): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x2d): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x3a): undefined reference to `gtk_label_set_text'
/tmp/ccOS51Jp.o: In function `LyricSync':
miditest.c:(.text+0x53): undefined reference to `BASS_MIDI_StreamGetMark'
miditest.c:(.text+0x11a): undefined reference to `gdk_threads_enter'
miditest.c:(.text+0x11f): undefined reference to `gtk_label_get_type'
miditest.c:(.text+0x133): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x13e): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x14b): undefined reference to `gtk_label_set_text'
miditest.c:(.text+0x150): undefined reference to `gdk_threads_leave'
/tmp/ccOS51Jp.o: In function `TimerProc':
miditest.c:(.text+0x1e1): undefined reference to `gtk_label_get_type'
miditest.c:(.text+0x1f5): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x200): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x20d): undefined reference to `gtk_label_set_text'
miditest.c:(.text+0x21d): undefined reference to `BASS_ChannelGetPosition'
miditest.c:(.text+0x225): undefined reference to `gtk_range_get_type'
miditest.c:(.text+0x239): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x244): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x25e): undefined reference to `gtk_range_set_value'
miditest.c:(.text+0x2aa): undefined reference to `BASS_MIDI_FontGetInfo'
miditest.c:(.text+0x2e8): undefined reference to `gtk_label_get_type'
miditest.c:(.text+0x2fc): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x307): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x314): undefined reference to `gtk_label_set_text'
/tmp/ccOS51Jp.o: In function `Error':
miditest.c:(.text+0x34c): undefined reference to `BASS_ErrorGetCode'
miditest.c:(.text+0x353): undefined reference to `gtk_window_get_type'
miditest.c:(.text+0x362): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x389): undefined reference to `gtk_message_dialog_new'
miditest.c:(.text+0x391): undefined reference to `gtk_dialog_get_type'
miditest.c:(.text+0x39c): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x3a4): undefined reference to `gtk_dialog_run'
/tmp/ccOS51Jp.o: In function `SetTempo':
miditest.c:(.text+0x3cd): undefined reference to `BASS_MIDI_StreamGetEvent'
/tmp/ccOS51Jp.o: In function `FindMarker':
miditest.c:(.text+0x426): undefined reference to `BASS_MIDI_StreamGetMark'
/tmp/ccOS51Jp.o: In function `LoopSync':
miditest.c:(.text+0x47e): undefined reference to `BASS_ChannelSetPosition'
/tmp/ccOS51Jp.o: In function `OpenClicked':
miditest.c:(.text+0x496): undefined reference to `gtk_dialog_get_type'
miditest.c:(.text+0x4a5): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x4ad): undefined reference to `gtk_dialog_run'
miditest.c:(.text+0x4bb): undefined reference to `gtk_widget_hide'
miditest.c:(.text+0x4c9): undefined reference to `gtk_file_chooser_get_type'
miditest.c:(.text+0x4d8): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x4e0): undefined reference to `gtk_file_chooser_get_filename'
miditest.c:(.text+0x4ee): undefined reference to `BASS_StreamFree'
miditest.c:(.text+0x4f3): undefined reference to `gtk_label_get_type'
miditest.c:(.text+0x507): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x512): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x51f): undefined reference to `gtk_label_set_text'
miditest.c:(.text+0x524): undefined reference to `gtk_toggle_button_get_type'
miditest.c:(.text+0x538): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x543): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x54b): undefined reference to `gtk_toggle_button_get_active'
miditest.c:(.text+0x570): undefined reference to `BASS_MIDI_StreamCreateFile'
miditest.c:(.text+0x587): undefined reference to `gtk_button_set_label'
miditest.c:(.text+0x598): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x5a3): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x5b0): undefined reference to `gtk_label_set_text'
miditest.c:(.text+0x5b5): undefined reference to `gtk_range_get_type'
miditest.c:(.text+0x5c9): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x5d4): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x5e3): undefined reference to `gtk_range_set_range'
miditest.c:(.text+0x5fd): undefined reference to `gtk_button_set_label'
miditest.c:(.text+0x612): undefined reference to `BASS_MIDI_StreamGetMark'
miditest.c:(.text+0x632): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x63d): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x653): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x65e): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x66b): undefined reference to `gtk_label_set_text'
miditest.c:(.text+0x67b): undefined reference to `BASS_ChannelGetLength'
miditest.c:(.text+0x683): undefined reference to `gtk_range_get_type'
miditest.c:(.text+0x697): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x6a2): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x6bf): undefined reference to `gtk_range_set_range'
miditest.c:(.text+0x6f2): undefined reference to `BASS_ChannelSetSync'
miditest.c:(.text+0x70c): undefined reference to `BASS_ChannelSetSync'
miditest.c:(.text+0x728): undefined reference to `BASS_MIDI_StreamGetMark'
miditest.c:(.text+0x756): undefined reference to `BASS_MIDI_StreamGetMark'
miditest.c:(.text+0x77a): undefined reference to `BASS_ChannelSetSync'
miditest.c:(.text+0x794): undefined reference to `BASS_ChannelSetSync'
miditest.c:(.text+0x7bb): undefined reference to `BASS_ChannelSetSync'
miditest.c:(.text+0x7d5): undefined reference to `BASS_ChannelSetSync'
miditest.c:(.text+0x7e8): undefined reference to `BASS_MIDI_StreamGetFonts'
miditest.c:(.text+0x7fe): undefined reference to `BASS_ChannelPlay'
miditest.c:(.text+0x806): undefined reference to `g_free'
/tmp/ccOS51Jp.o: In function `OpenFontClicked':
miditest.c:(.text+0x81c): undefined reference to `gtk_dialog_get_type'
miditest.c:(.text+0x82b): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x833): undefined reference to `gtk_dialog_run'
miditest.c:(.text+0x841): undefined reference to `gtk_widget_hide'
miditest.c:(.text+0x84f): undefined reference to `gtk_file_chooser_get_type'
miditest.c:(.text+0x85e): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x866): undefined reference to `gtk_file_chooser_get_filename'
miditest.c:(.text+0x873): undefined reference to `BASS_MIDI_FontInit'
miditest.c:(.text+0x89e): undefined reference to `BASS_MIDI_StreamSetFonts'
miditest.c:(.text+0x8b3): undefined reference to `BASS_MIDI_StreamSetFonts'
miditest.c:(.text+0x8be): undefined reference to `BASS_MIDI_FontFree'
miditest.c:(.text+0x8cc): undefined reference to `g_free'
/tmp/ccOS51Jp.o: In function `PositionChange':
miditest.c:(.text+0x937): undefined reference to `BASS_ChannelSetPosition'
miditest.c:(.text+0x943): undefined reference to `gtk_label_get_type'
miditest.c:(.text+0x957): undefined reference to `glade_xml_get_widget'
miditest.c:(.text+0x962): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text+0x96f): undefined reference to `gtk_label_set_text'
/tmp/ccOS51Jp.o: In function `TempoChanged':
miditest.c:(.text+0x979): undefined reference to `gtk_range_get_value'
/tmp/ccOS51Jp.o: In function `EndSync':
miditest.c:(.text+0x40): undefined reference to `gdk_threads_leave'
/tmp/ccOS51Jp.o: In function `Error':
miditest.c:(.text+0x3b1): undefined reference to `gtk_widget_destroy'
/tmp/ccOS51Jp.o: In function `WindowDestroy':
miditest.c:(.text+0x3b6): undefined reference to `gtk_main_quit'
/tmp/ccOS51Jp.o: In function `SetTempo':
miditest.c:(.text+0x3fb): undefined reference to `BASS_MIDI_StreamEvent'
/tmp/ccOS51Jp.o: In function `FXToggled':
miditest.c:(.text+0x8f3): undefined reference to `BASS_ChannelFlags'
/tmp/ccOS51Jp.o: In function `main':
miditest.c:(.text.startup+0x14): undefined reference to `g_thread_init'
miditest.c:(.text.startup+0x19): undefined reference to `gdk_threads_init'
miditest.c:(.text.startup+0x28): undefined reference to `gtk_init'
miditest.c:(.text.startup+0x2f): undefined reference to `BASS_GetVersion'
miditest.c:(.text.startup+0x51): undefined reference to `BASS_Init'
miditest.c:(.text.startup+0x72): undefined reference to `glade_xml_new'
miditest.c:(.text.startup+0x8f): undefined reference to `glade_xml_get_widget'
miditest.c:(.text.startup+0xab): undefined reference to `glade_xml_signal_autoconnect'
miditest.c:(.text.startup+0xb0): undefined reference to `gtk_window_get_type'
miditest.c:(.text.startup+0xc2): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text.startup+0xf4): undefined reference to `gtk_file_chooser_dialog_new'
miditest.c:(.text.startup+0x100): undefined reference to `gtk_file_filter_new'
miditest.c:(.text.startup+0x110): undefined reference to `gtk_file_filter_set_name'
miditest.c:(.text.startup+0x147): undefined reference to `gtk_file_filter_add_custom'
miditest.c:(.text.startup+0x14c): undefined reference to `gtk_file_chooser_get_type'
miditest.c:(.text.startup+0x15e): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text.startup+0x169): undefined reference to `gtk_file_chooser_add_filter'
miditest.c:(.text.startup+0x16e): undefined reference to `gtk_file_filter_new'
miditest.c:(.text.startup+0x17e): undefined reference to `gtk_file_filter_set_name'
miditest.c:(.text.startup+0x18b): undefined reference to `gtk_file_filter_add_pattern'
miditest.c:(.text.startup+0x19a): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text.startup+0x1a5): undefined reference to `gtk_file_chooser_add_filter'
miditest.c:(.text.startup+0x1b4): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text.startup+0x1e6): undefined reference to `gtk_file_chooser_dialog_new'
miditest.c:(.text.startup+0x1f2): undefined reference to `gtk_file_filter_new'
miditest.c:(.text.startup+0x202): undefined reference to `gtk_file_filter_set_name'
miditest.c:(.text.startup+0x239): undefined reference to `gtk_file_filter_add_custom'
miditest.c:(.text.startup+0x248): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text.startup+0x253): undefined reference to `gtk_file_chooser_add_filter'
miditest.c:(.text.startup+0x258): undefined reference to `gtk_file_filter_new'
miditest.c:(.text.startup+0x268): undefined reference to `gtk_file_filter_set_name'
miditest.c:(.text.startup+0x275): undefined reference to `gtk_file_filter_add_pattern'
miditest.c:(.text.startup+0x284): undefined reference to `g_type_check_instance_cast'
miditest.c:(.text.startup+0x28f): undefined reference to `gtk_file_chooser_add_filter'
miditest.c:(.text.startup+0x29b): undefined reference to `BASS_PluginLoad'
miditest.c:(.text.startup+0x2a7): undefined reference to `BASS_PluginLoad'
miditest.c:(.text.startup+0x2b8): undefined reference to `g_timeout_add'
miditest.c:(.text.startup+0x2bd): undefined reference to `gdk_threads_enter'
miditest.c:(.text.startup+0x2c2): undefined reference to `gtk_main'
miditest.c:(.text.startup+0x2c7): undefined reference to `gdk_threads_leave'
miditest.c:(.text.startup+0x2d3): undefined reference to `gtk_widget_destroy'
miditest.c:(.text.startup+0x2df): undefined reference to `gtk_widget_destroy'
miditest.c:(.text.startup+0x2e6): undefined reference to `BASS_Free'
miditest.c:(.text.startup+0x2ed): undefined reference to `BASS_PluginFree'
collect2: error: ld returned 1 exit status
make: *** [miditest] Error 1

```

Any help would be **greatly** appreciated.

---

