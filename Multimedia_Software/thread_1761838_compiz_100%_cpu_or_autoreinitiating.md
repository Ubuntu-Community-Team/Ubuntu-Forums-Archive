---
title: "compiz 100% cpu or autoreinitiating"
date: 2011-05-18
forum: Multimedia Software
---

### Post by jperelli on 2011-05-18
Hello,

well, my problem comes from update to 11.04, compiz hanged up at 100% cpu usage, now when I enter in gnome 3d accelerated desktop with compiz, I move some window, and all the windows dissapear and 2 seconds later all reapear (I think compiz detects a failure and auto reinitiates himself)

I don't know how to fix this, maybe is a known bug in a plugin or something? does compiz has a crash log?

---

### Post by jperelli on 2011-05-19
Could someone give me a hand?
Ok, I may talk to myself, but maybe it helps somebody:

I activated the crashhandler plugin via ccsm

then I took the trace from /tmp/compiz_crash-****.out

this is the (back)trace:
```

Hilo 2 (Thread 0x7f1e5aa90700 (LWP 2871)):
#0  0x00007f1e5d218f03 in __poll (fds=<value optimized out>, nfds=<value optimized out>, timeout=<value optimized out>) at ../sysdeps/unix/sysv/linux/poll.c:87
        resultvar = 18446744073709551100
        oldtype = 0
        result = <value optimized out>
#1  0x00007f1e5e554104 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f1e5e5549f2 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f1e5f57fc44 in ?? () from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#4  0x00007f1e5e57b3e4 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f1e5de7fd8c in start_thread (arg=0x7f1e5aa90700) at pthread_create.c:304
        pd = 0x7f1e5aa90700
        now = <value optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {139768346773248, 2422423191567741260, 140736305746896, 139768346773952, 0, 3, -2332134122720317108, -2332135900819738292}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = 0
        robust = <value optimized out>
        sp = <value optimized out>
        freesize = <value optimized out>
        __PRETTY_FUNCTION__ = "start_thread"
#6  0x00007f1e5d22604d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
No locales.
#7  0x0000000000000000 in ?? ()

Hilo 1 (Thread 0x7f1e6170a820 (LWP 2863)):
#0  0x00007f1e5d1ed1ed in __libc_waitpid (pid=<value optimized out>, stat_loc=<value optimized out>, options=<value optimized out>) at ../sysdeps/unix/sysv/linux/waitpid.c:41
        resultvar = 18446744073709551104
        oldtype = 0
        result = <value optimized out>
        __result = <value optimized out>
        _buffer = {__routine = 0x7f1e5d182060 <cancel_handler>, __arg = 0x7fffb982af30, __canceltype = 1, __prev = 0x0}
        _avail = 1
        status = <value optimized out>
        save = <value optimized out>
        pid = 3076
        sa = {__sigaction_handler = {sa_handler = 0x1, sa_sigaction = 0x1}, sa_mask = {__val = {65536, 0 <repeats 15 times>}}, sa_flags = 0, sa_restorer = 0x7fffb982b0c0}
        omask = {__val = {1024, 13557024, 139768387367328, 139768460560832, 2863, 2863, 4294967295, 139768388372165, 206158430256, 13557024, 2199608, 0, 2863, 20025080, 139768401203200, 139768458603812}}
#2  0x00007f1e5d182180 in __libc_system (line=<value optimized out>) at ../sysdeps/posix/system.c:190
        oldtype = 0
        result = <value optimized out>
#3  0x00007f1e56864610 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0x00007f1e52e43335 in RegexExp::evaluate(CompWindow*) () from /usr/lib/compiz/libregex.so
#6  0x00000000004480bf in ?? ()
#7  0x000000000044807b in ?? ()
#8  0x000000000044807b in ?? ()
#9  0x00007f1e5643d939 in DecorWindow::update(bool) () from /usr/lib/compiz/libdecor.so
#10 0x00007f1e56440854 in DecorWindow::DecorWindow(CompWindow*) () from /usr/lib/compiz/libdecor.so
#11 0x00007f1e56443eb9 in CompPlugin::VTableForScreenAndWindow<DecorScreen, DecorWindow>::initWindow(CompWindow*) () from /usr/lib/compiz/libdecor.so
#12 0x0000000000450e95 in CompPlugin::windowInitPlugins(CompWindow*) ()
#13 0x0000000000442007 in CompWindow::CompWindow(unsigned long, XWindowAttributes&, PrivateWindow*) ()
#14 0x0000000000442470 in CoreWindow::manage(unsigned long, XWindowAttributes&) ()
#15 0x000000000044f473 in CompScreen::handleEvent(_XEvent*) ()
#16 0x00007f1e598482d4 in PrivateCompositeScreen::handleEvent(_XEvent*) () from /usr/lib/compiz/libcomposite.so
#17 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#18 0x00007f1e5961c1df in PrivateGLScreen::handleEvent(_XEvent*) () from /usr/lib/compiz/libopengl.so
#19 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#20 0x00007f1e5643eff3 in DecorScreen::handleEvent(_XEvent*) () from /usr/lib/compiz/libdecor.so
#21 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#22 0x00007f1e559d7396 in ResizeScreen::handleEvent(_XEvent*) () from /usr/lib/compiz/libresize.so
#23 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#24 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#25 0x00007f1e54f813c7 in PrivateScaleScreen::handleEvent(_XEvent*) () from /usr/lib/compiz/libscale.so
#26 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#27 0x00007f1e52e434bf in RegexScreen::handleEvent(_XEvent*) () from /usr/lib/compiz/libregex.so
#28 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#29 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#30 0x00007f1e520fa7bc in MoveScreen::handleEvent(_XEvent*) () from /usr/lib/compiz/libmove.so
#31 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#32 0x00007f1e51ee21ad in WorkaroundsScreen::handleEvent(_XEvent*) () from /usr/lib/compiz/libworkarounds.so
#33 0x000000000044e9a3 in CompScreen::handleEvent(_XEvent*) ()
#34 0x000000000042e59b in PrivateScreen::processEvents() ()
#35 0x0000000000455958 in CompEventSource::callback() ()
#36 0x00007f1e5f0a4daf in Glib::Source::dispatch_vfunc(_GSource*, int (*)(void*), void*) () from /usr/lib/libglibmm-2.4.so.1
#37 0x00007f1e5e553bcd in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#38 0x00007f1e5e5543a8 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#39 0x00007f1e5e5549f2 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#40 0x000000000042a2ea in CompScreen::eventLoop() ()
#41 0x0000000000423160 in main ()

```

I thought the crash was made by the animationsplugin, that depends on regex.
Here in the trace, it seems that the plugin that generates the crash is the regex
```
#5  0x00007f1e52e43335 in RegexExp::evaluate(CompWindow*) () from /usr/lib/compiz/libregex.so

```

without regex I cant have the animations plugin that I like.
So I keep activated the regex and animations, but I deleted some regex that I had in windowdecorator (the only regex that I used) and now it seems to work all good...

This regex I used were for taking out the decorator in firefox (make firefox like chrome) and the other to take out the shadows from the gnome-panel. I like to have this improvements, but for now it seems to be the only choice to fix things.

Where can I send some bugreport?

---

