---
title: "Can't Play DVD -No permission"
date: 2010-11-09
forum: Multimedia Software
---

### Post by AbdRahim on 2010-11-09
Message from Avidemux when trying to Open commercial DVD

Assert failed :rewind
 at line 247, file /build/buildd/avidemux-2.5.3/avidemux/ADM_editor/ADM_edRender.cppADM_backTrack
ADM_Composer::getUncompressedFrame(unsigned int, ADMImage*, unsigned int*)
admPreview::update(unsigned int)
updateLoaded()
avidemux2_gtk() [0x808a75d]
automation()
avidemux2_gtk() [0x817334c]

g_main_context_dispatch

g_main_loop_run
gtk_dialog_run
ADM_GtkCoreUIToolkit::GUI_Confirmation_HIG(char const*, char const*, char const*)
GUI_Confirmation_HIG(char const*, char const*, char const*, ...)
checkCrashFile()
UI_RunApp()
main
__libc_start_main
avidemux2_gtk() [0x8086171]

---

### Post by blackmail on 2010-11-09
First how did you install avidemux? and second if you want only to play dvds then you could also try gxine, it works very well for me.

---

