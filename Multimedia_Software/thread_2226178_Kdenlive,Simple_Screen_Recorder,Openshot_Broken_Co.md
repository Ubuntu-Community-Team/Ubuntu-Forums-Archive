---
title: "Kdenlive,Simple Screen Recorder,Openshot Broken Codecs"
date: 2014-05-25
forum: Multimedia Software
---

### Post by james0658 on 2014-05-25
Hello Forum 

I recently installed the latest packages and now Openhot and Kdenlive is now broke when trying to render in h264, the codecs are installed, but it just crashes same thing happens in simple screen recorder in h264.  But the weird thing is Kazam is not broke when recording in H264.  

I did an overview on my Youtube Channel of Ubuntu 14.04, and Ubuntu was running just fine at the time, but just recently I reinstalled 14.04 and now those same apps are broke.  I then installed Linux Mint 17 and after the updates directly from the Ubuntu trusty repos I was having the same issue.  Please check the screen shot I took it right before I did the updates and everything was running fine just before that.

After the update it manage to break 3 popular apps that a lot of people use.  I know that they use to run on libavcodec-53 but everything looks like it was changed to 54 I don't know if it's becuase these softwares are outdated or not?

This is the error I'm getting in kdenlive after updates
 
Rendering of /home/jefflinuxturner/kdenlive/mess.mp4 crashed
 No LADSPA plugins were found! Check your LADSPA_PATH environment variable.
[NULL @ 0x7f7e5c2c7a60] [Eval @ 0x7f7e628a5530] Undefined constant or missing '(' in 'dct8x8' [NULL @ 0x7f7e5c2c7a60] Unable to parse option value "dct8x8"
[NULL @ 0x7f7e5c2c8ea0] [Eval @ 0x7f7e628a54e0] Undefined constant or missing '(' in 'dct8x8' [NULL @ 0x7f7e5c2c8ea0] Unable to parse option value "dct8x8"

This is the error in SImple Screen Recorder:

SimpleScreenRecorder 0.2.2
Compiled with GCC 4.8.2
Qt: header 4.8.6, lib 4.8.6
libavformat: header 54.20.3, lib 54.63.104
libavcodec: header 54.35.0, lib 54.92.100
libavutil: header 52.3.0, lib 52.18.100
libswscale: header 2.1.1, lib 2.2.100
[DetectCPUFeatures] CPU features: mmx sse sse2 sse3 ssse3 sse4_1 sse4_2 avx
"sni-qt/10401" WARN  20:22:13.383 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 

(simplescreenrecorder:10401): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

(simplescreenrecorder:10401): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
[PageRecord::StartPage] Starting page ...
[PageRecord::StartPage] Started page.
[PageRecord::StartOutput] Starting output ...
[Muxer::Init] Using format mp4 (MP4 (MPEG-4 Part 14)).
[BaseEncoder::CreateCodec] Using codec libx264 (libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10).
[libx264 @ 0x2256c20] using SAR=1/1
Segmentation fault

the libx264 is installed, I checked.

This is the error on Openshot:

state saved
on_tlbImportFiles_clicked called with self.GtkToolButton
[image2 @ 0x7f8258000b00] Encoder did not produce proper pts, making some up.
project state modified
state saved
project state modified
state saved
on_tlbMakeMovie_clicked called with self.GtkToolButton
on_cboExportType_changed
on_cboUploadServices_changed
on_cboProjectType_changed
on_cboExportTo_changed
on_cboProjectType_changed
on_btnExportVideo_clicked
on_btnExportVideo_clicked
NEW SDL CONSUMER
[NULL @ 0x7f82842c7980] [Eval @ 0x7f828f7fd530] Undefined constant or missing '(' in 'dct8x8'
[NULL @ 0x7f82842c7980] Unable to parse option value "dct8x8"
[NULL @ 0x7f82842c9180] [Eval @ 0x7f828f7fd4e0] Undefined constant or missing '(' in 'dct8x8'
[NULL @ 0x7f82842c9180] Unable to parse option value "dct8x8"
Segmentation fault

I am not a computer programmer but I tried my best to get these working but failed.  I also thought that posting the error output from the terminal might at least gove you guys an idea on how to make things work again.  I do a lot of videos on Youtube promoting Ubuntu and just Linux in general I'd appreciate any assistance you can give me.

Thanks 

Jeff Linux Turner :)

---

