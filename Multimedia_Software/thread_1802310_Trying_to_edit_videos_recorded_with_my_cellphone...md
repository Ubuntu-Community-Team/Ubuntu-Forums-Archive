---
title: "Trying to edit videos recorded with my cellphone.."
date: 2011-07-11
forum: Multimedia Software
---

### Post by Guitar-maniac on 2011-07-11
They're mp4:s of course, and i choose the safe mode when it prompts it. When trying to add them to a joblist in avidemux it gives me:

Assert failed :0
 at line 386, file /build/buildd/avidemux-2.5.4/avidemux/ADM_encoder/adm_encConfig.cppADM_backTrack
videoCodecGetMode()
ADM_Composer::saveAsScript(char const*, char const*)
saveCrashProject()
ADM_backTrack
videoCodecGetMode()
ADM_Composer::saveAsScript(char const*, char const*)
A_addJob()
HandleAction(Action)
guiCallback(_GtkMenuItem*, void*)
g_cclosure_marshal_VOID__VOID
g_closure_invoke

g_signal_emit_valist
g_signal_emit
gtk_menu_item_activate

g_cclosure_marshal_VOID__UINT
g_closure_invoke

Haven't had this problem before upgrading to ubuntu 11,04. I tried LIVES but it couldn't even open mp4 videos.

---

### Post by handy on 2011-07-13
It might be worth a try, to make a copy of one of your vids, then convert it to another editor friendly format with Winff.

You never know your luck.

---

