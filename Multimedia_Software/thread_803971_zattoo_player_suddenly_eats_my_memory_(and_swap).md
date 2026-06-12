---
title: "zattoo_player suddenly eats my memory (and swap)"
date: 2008-05-22
forum: Multimedia Software
---

### Post by hal10000 on 2008-05-22
Hi,

Zattoo player always worked well on my system (ubuntu 8.04). But this evening, when starting the player, it showed a very strange behaviour.

After login everything seemed to be ok, but when i choose a tv-station i get only audio, but no video and then a few seconds later it begins to grab all my memory and swap space.

The zattoo.errlog file (in /home/myname/.Zattoo/Data/logs/) shows the following messages:

> 
(zattoo_player:10195): GdkGLExt-CRITICAL **: gdk_gl_window_impl_x11_make_context_current: assertion `GDK_IS_GL_CONTEXT_IMPL_X11 (glcontext)' failed

(zattoo_player:10195): GtkGLExt-WARNING **: cannot create GdkGLContext


(zattoo_player:10195): GdkGLExt-CRITICAL **: gdk_gl_window_impl_x11_make_context_current: assertion `GDK_IS_GL_CONTEXT_IMPL_X11 (glcontext)' failed
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xb6fc2ec8]negative ctts, ignoring
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xb6fc2ec8]negative ctts, ignoring

(zattoo_player:10195): GtkGLExt-WARNING **: cannot create GdkGLContext


(zattoo_player:10195): GdkGLExt-CRITICAL **: gdk_gl_window_impl_x11_make_context_current: assertion `GDK_IS_GL_CONTEXT_IMPL_X11 (glcontext)' failed

(zattoo_player:10195): GtkGLExt-WARNING **: cannot create GdkGLContext


(zattoo_player:10195): GdkGLExt-CRITICAL **: gdk_gl_window_impl_x11_make_context_current: assertion `GDK_IS_GL_CONTEXT_IMPL_X11 (glcontext)' failed


I didn't do any changes in system-settings or upgrades since the last time when zattoo was working well (yesterday).
Removing (incl. conffiles and files in homedirectory) and reinstalling the player had no effect.

I have no idea what went wrong and would appreciate if anyone can help me with my problem.

---

### Post by hal10000 on 2008-05-22
problem solvrd

In my first post i wrote that i did no upgrades, but that was wrong i updated the xserver, and somehow my nvidia-glx package disappeared. After reinstalling it, everything works.

---

