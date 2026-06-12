---
title: "Avidemux crash when combining JPEGs into video"
date: 2010-03-21
forum: Multimedia Software
---

### Post by knahrvorn on 2010-03-21
Trying to combine a bunch of .jpg's into a video stream, and everything seems to work perfectly, until I actually run then project -- which triggers a crash.

In more detail:
Selecting the first of 18 JPEG images, named m001.jpg through m018.jpg, which opens all images in Avidemux as a video sequence. I am running Avidemux 2.5.1 from the Ubuntu 9.10 repository. I set "MPEG-4 AVC (x264)" as video codec, apply the MPlayer resize filter for resizing to 1024x768, select "Copy" for audio (I don't want audio), and "MP4" as container. I add the job to joblæist, and when I run the job, the following crash report appears in the terminal:

```
*********** BACKTRACK **************
Frame  0: /usr/lib/libADM_core.so(ADM_backTrack+0x6d) [0x1f592d] 
Frame  1: avidemux(_Z24loadVideoCodecConfStringPKc+0x107) [0x8124a57] 
    <loadVideoCodecConfString>()
Frame  2: avidemux(_ZN19ADM_JSAvidemuxVideo5CodecEP9JSContextP8JSObjectjPlS4_+0x14b) [0x80ba96b] 
    <>()
Frame  3: /usr/lib/libADM_smjs.so(js_Invoke+0x4ab) [0x149e8b] 
Frame  4: /usr/lib/libADM_smjs.so(js_Interpret+0x70b0) [0x143c20] 
Frame  5: /usr/lib/libADM_smjs.so(js_Execute+0x1fb) [0x14a99b] 
Frame  6: /usr/lib/libADM_smjs.so(JS_ExecuteScript+0x4a) [0x1220ea] 
Frame  7: avidemux(_Z15parseECMAScriptPKc+0xfc) [0x80b8fbc] 
    <parseECMAScript>()
Frame  8: avidemux(_Z7DIA_jobjPPc+0xd41) [0x81a7f61] 
    <DIA_job>()
Frame  9: avidemux(_Z8GUI_jobsv+0x62) [0x809d142] 
    <GUI_jobs>()
Frame 10: avidemux(_Z12HandleAction6Action+0x4b5) [0x809b4f5] 
    <HandleAction>()
Frame 11: avidemux(_Z11guiCallbackP12_GtkMenuItemPv+0x20) [0x81b1950] 
    <guiCallback>(_GtkMenuItem,)
Frame 12: /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0x7f19fc] 
Frame 13: /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x7e4072] 
Frame 14: /usr/lib/libgobject-2.0.so.0 [0x7f97a8] 
Frame 15: /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0x7fab2d] 
Frame 16: /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x7fafb6] 
Frame 17: /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_activate+0x95) [0x3109525] 
Frame 18: /usr/lib/libgtk-x11-2.0.so.0(gtk_menu_shell_activate_item+0x120) [0x2ff5590] 
Frame 19: /usr/lib/libgtk-x11-2.0.so.0 [0x2ff6f7f] 
*********** BACKTRACK **************
Info: Crash
Assert failed :extraSize < MAX_STRING
 at line 729, file /build/buildd/avidemux-2.5.1+repack/avidemux/ADM_encoder/adm_encConfig.cpp/usr/lib/libADM_core.so(ADM_backTrack+0x6d) [0x1f592d]
avidemux(_Z24loadVideoCodecConfStringPKc+0x107) [0x8124a57]
avidemux(_ZN19ADM_JSAvidemuxVideo5CodecEP9JSContextP8JSObjectjPlS4_+0x14b) [0x80ba96b]
/usr/lib/libADM_smjs.so(js_Invoke+0x4ab) [0x149e8b]
/usr/lib/libADM_smjs.so(js_Interpret+0x70b0) [0x143c20]
/usr/lib/libADM_smjs.so(js_Execute+0x1fb) [0x14a99b]
/usr/lib/libADM_smjs.so(JS_ExecuteScript+0x4a) [0x1220ea]
avidemux(_Z15parseECMAScriptPKc+0xfc) [0x80b8fbc]
avidemux(_Z7DIA_jobjPPc+0xd41) [0x81a7f61]
avidemux(_Z8GUI_jobsv+0x62) [0x809d142]
avidemux(_Z12HandleAction6Action+0x4b5) [0x809b4f5]
avidemux(_Z11guiCallbackP12_GtkMenuItemPv+0x20) [0x81b1950]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0x7f19fc]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x7e4072]
/usr/lib/libgobject-2.0.so.0 [0x7f97a8]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_val
Cleaning up
[lavc] Destroyed
Deleting post proc
Waiting for Spidermonkey to finish...
Cleaning up Spidermonkey.
[SDL] Quitting...
End of cleanup

Images stat:
___________
Max memory consumed (MB)     : 65664
Current memory consumed (MB) : 10368
Max image used               : 16
Cur image used               : 3
Global mem stat
______________
    Memory consumed: 13 (MB)

Goodbye...
```

What might be the cause of this? Thanks in advance!

---

