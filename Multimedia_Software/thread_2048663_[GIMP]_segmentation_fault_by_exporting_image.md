---
title: "[GIMP] segmentation fault by exporting image"
date: 2012-08-27
forum: Multimedia Software
---

### Post by pierreb24 on 2012-08-27
Hello.

Well, I've a very painfull problem : when I export some image with gimp, I always hget teh same error :

```
gimp:20832): Gtk-CRITICAL **: IA__gtk_tree_model_get: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(script-fu:20837): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault (core dumped)
```

Numbers change, but error remains. It appears when I export image in .png or .jpg, and if it's not teh first time, it crashs after two or three exports. Sometimes, it does the same with saving in XCF, but rarely. So GIMP became unuseable and that's a pitty for this powerfull prggramm. I first notice this error with the version of GIMP in the depot, so I update it to 2.8.0, and then, after founding the same issue, I compile 2.8.2. But still the same :(

Just to have fun, I use gdb :

```
pierre@pierre-Linux:~/Downloads/gimp-2.8.2$ gdb /opt/gimp-2.8/bin/gimp
GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2) 7.4-2012.04
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>...
Reading symbols from /opt/gimp-2.8/bin/gimp...done.
(gdb) r
Starting program: /opt/gimp-2.8/bin/gimp 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[New Thread 0x7fffeb971700 (LWP 20908)]
[New Thread 0x7fffeb170700 (LWP 20909)]
[New Thread 0x7fffea96f700 (LWP 20910)]
[New Thread 0x7fffe8c7d700 (LWP 20911)]
[New Thread 0x7fffe1004700 (LWP 20913)]
[New Thread 0x7fffd7a3f700 (LWP 20914)]
[Thread 0x7fffe8c7d700 (LWP 20911) exited]
[Thread 0x7fffe1004700 (LWP 20913) exited]
[New Thread 0x7fffe1004700 (LWP 20915)]
[New Thread 0x7fffe8c7d700 (LWP 20916)]
[New Thread 0x7fffd723e700 (LWP 20917)]
[New Thread 0x7fffd6a3d700 (LWP 20918)]
[New Thread 0x7fffd623c700 (LWP 20919)]
[New Thread 0x7fffd5a3b700 (LWP 20920)]
[New Thread 0x7fffd523a700 (LWP 20921)]
[New Thread 0x7fffd4a39700 (LWP 20922)]
[New Thread 0x7fffcffff700 (LWP 20923)]
[Thread 0x7fffd5a3b700 (LWP 20920) exited]
[Thread 0x7fffd723e700 (LWP 20917) exited]
[Thread 0x7fffd6a3d700 (LWP 20918) exited]
[Thread 0x7fffd623c700 (LWP 20919) exited]
[Thread 0x7fffd523a700 (LWP 20921) exited]
[Thread 0x7fffe1004700 (LWP 20915) exited]
[Thread 0x7fffd7a3f700 (LWP 20914) exited]
[Thread 0x7fffd4a39700 (LWP 20922) exited]
[Thread 0x7fffe8c7d700 (LWP 20916) exited]
[New Thread 0x7fffe8c7d700 (LWP 20924)]
[New Thread 0x7fffd4a39700 (LWP 20925)]
[New Thread 0x7fffd7a3f700 (LWP 20926)]
[Thread 0x7fffd4a39700 (LWP 20925) exited]
[Thread 0x7fffd7a3f700 (LWP 20926) exited]
[Thread 0x7fffe8c7d700 (LWP 20924) exited]
[New Thread 0x7fffe8c7d700 (LWP 20927)]
[New Thread 0x7fffd7a3f700 (LWP 20928)]
[New Thread 0x7fffd4a39700 (LWP 20929)]
[New Thread 0x7fffe1004700 (LWP 20930)]
[New Thread 0x7fffd723e700 (LWP 20931)]
[New Thread 0x7fffd6a3d700 (LWP 20932)]
[New Thread 0x7fffd623c700 (LWP 20933)]
[New Thread 0x7fffd5a3b700 (LWP 20934)]
[New Thread 0x7fffd523a700 (LWP 20935)]
[Thread 0x7fffd7a3f700 (LWP 20928) exited]
[Thread 0x7fffd623c700 (LWP 20933) exited]
[Thread 0x7fffcffff700 (LWP 20923) exited]
[Thread 0x7fffe1004700 (LWP 20930) exited]
[Thread 0x7fffd723e700 (LWP 20931) exited]
[Thread 0x7fffd6a3d700 (LWP 20932) exited]
[Thread 0x7fffd4a39700 (LWP 20929) exited]
[Thread 0x7fffd523a700 (LWP 20935) exited]
[Thread 0x7fffe8c7d700 (LWP 20927) exited]
[New Thread 0x7fffe8c7d700 (LWP 20936)]
[New Thread 0x7fffd523a700 (LWP 20937)]
[New Thread 0x7fffd4a39700 (LWP 20938)]
[New Thread 0x7fffd6a3d700 (LWP 20939)]
[New Thread 0x7fffe1004700 (LWP 20940)]
[New Thread 0x7fffd7a3f700 (LWP 20941)]
[New Thread 0x7fffd723e700 (LWP 20942)]
[New Thread 0x7fffd623c700 (LWP 20943)]
[New Thread 0x7fffcffff700 (LWP 20944)]
[Thread 0x7fffd523a700 (LWP 20937) exited]
[Thread 0x7fffd5a3b700 (LWP 20934) exited]
[Thread 0x7fffd723e700 (LWP 20942) exited]
[Thread 0x7fffd623c700 (LWP 20943) exited]
[Thread 0x7fffe1004700 (LWP 20940) exited]
[Thread 0x7fffd7a3f700 (LWP 20941) exited]
[Thread 0x7fffe8c7d700 (LWP 20936) exited]
[Thread 0x7fffd4a39700 (LWP 20938) exited]
[Thread 0x7fffd6a3d700 (LWP 20939) exited]
[New Thread 0x7fffd6a3d700 (LWP 20945)]
[Thread 0x7fffd6a3d700 (LWP 20945) exited]
[New Thread 0x7fffd6a3d700 (LWP 20946)]
[Thread 0x7fffcffff700 (LWP 20944) exited]
[New Thread 0x7fffcffff700 (LWP 20948)]
[New Thread 0x7fffd4a39700 (LWP 20949)]
[New Thread 0x7fffe8c7d700 (LWP 20950)]
[New Thread 0x7fffd7a3f700 (LWP 20951)]
[New Thread 0x7fffe1004700 (LWP 20952)]
[Thread 0x7fffd6a3d700 (LWP 20946) exited]
[Thread 0x7fffd7a3f700 (LWP 20951) exited]
[Thread 0x7fffd4a39700 (LWP 20949) exited]
[Thread 0x7fffcffff700 (LWP 20948) exited]
[Thread 0x7fffe8c7d700 (LWP 20950) exited]
[New Thread 0x7fffe8c7d700 (LWP 20954)]
[Thread 0x7fffe8c7d700 (LWP 20954) exited]

(gimp:20904): Gtk-CRITICAL **: IA__gtk_tree_model_get: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff3db4b91 in ?? () from /lib/x86_64-linux-gnu/libc.so.6
(gdb) bt
#0  0x00007ffff3db4b91 in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff7553e5a in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#2  0x00007ffff7537b0a in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#3  0x00007ffff767f6ee in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#4  0x00007ffff7681084 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#5  0x00007ffff7682321 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#6  0x00007fffec23ca35 in ?? ()
   from /usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libgail.so
#7  0x00007fffec23cb43 in ?? ()
   from /usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libgail.so
#8  0x00007fffec241ef0 in ?? ()
   from /usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libgail.so
#9  0x00007ffff480ceca in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#10 0x00007ffff4825741 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#11 0x00007ffff4826242 in g_signal_emit ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#12 0x00007ffff769bb87 in gtk_tree_view_remove_column ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#13 0x00007ffff76a1387 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#14 0x00007ffff480cc1b in g_closure_invoke ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#15 0x00007ffff481dc31 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#16 0x00007ffff4826099 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#17 0x00007ffff4826242 in g_signal_emit ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#18 0x00007ffff75c92c0 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#19 0x00007ffff4813000 in g_object_run_dispose ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#20 0x00007ffff753796b in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#21 0x00007ffff4811e93 in g_object_unref ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#22 0x00007ffff75340c3 in gtk_entry_set_completion ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#23 0x00007ffff75341e0 in ?? ()
---Type <return> to continue, or q <return> to quit---
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#24 0x00007ffff4811e93 in g_object_unref ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#25 0x00007ffff7628d88 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#26 0x00007ffff7523dcf in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#27 0x00007ffff480cc1b in g_closure_invoke ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#28 0x00007ffff481dc31 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#29 0x00007ffff4826099 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#30 0x00007ffff4826242 in g_signal_emit ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#31 0x00007ffff75c92c0 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#32 0x00007ffff4813000 in g_object_run_dispose ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#33 0x00007ffff74ee89b in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#34 0x00007ffff7523dcf in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#35 0x00007ffff480cc1b in g_closure_invoke ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#36 0x00007ffff481dc31 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#37 0x00007ffff4826099 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#38 0x00007ffff4826242 in g_signal_emit ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#39 0x00007ffff75c92c0 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#40 0x00007ffff4813000 in g_object_run_dispose ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#41 0x00007ffff74ee89b in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#42 0x00007ffff7523dcf in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#43 0x00007ffff480cc1b in g_closure_invoke ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#44 0x00007ffff481dc31 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#45 0x00007ffff4826099 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#46 0x00007ffff4826242 in g_signal_emit ()
---Type <return> to continue, or q <return> to quit---
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#47 0x00007ffff75c92c0 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#48 0x00007ffff4813000 in g_object_run_dispose ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#49 0x00007ffff74ee89b in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#50 0x00007ffff7523dcf in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#51 0x00007ffff480cc1b in g_closure_invoke ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#52 0x00007ffff481dc31 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#53 0x00007ffff4826099 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#54 0x00007ffff4826242 in g_signal_emit ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#55 0x00007ffff75c92c0 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#56 0x00007ffff4813000 in g_object_run_dispose ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#57 0x00007ffff74ee89b in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#58 0x00007ffff7523dcf in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#59 0x00007ffff480cc1b in g_closure_invoke ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#60 0x00007ffff481dc31 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#61 0x00007ffff4826099 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#62 0x00007ffff4826242 in g_signal_emit ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#63 0x00007ffff75c92c0 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#64 0x00007ffff4813000 in g_object_run_dispose ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#65 0x00007ffff7523dcf in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#66 0x00007ffff480cca2 in g_closure_invoke ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#67 0x00007ffff481dc31 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#68 0x00007ffff4826099 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#69 0x00007ffff4826242 in g_signal_emit ()
---Type <return> to continue, or q <return> to quit---
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#70 0x00007ffff75c92c0 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#71 0x000000000059da1b in gimp_file_dialog_dispose (object=0x1deae00)
    at gimpfiledialog.c:173
#72 0x00007ffff4813000 in g_object_run_dispose ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#73 0x00000000004b0888 in file_save_dialog_response (save_dialog=0x1deae00, 
    response_id=<optimized out>, gimp=<optimized out>)
    at file-save-dialog.c:238
#74 0x00007ffff480cca2 in g_closure_invoke ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#75 0x00007ffff481dd71 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#76 0x00007ffff4826099 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#77 0x00007ffff4826242 in g_signal_emit ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#78 0x00007ffff480ceca in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#79 0x00007ffff4825741 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#80 0x00007ffff4826242 in g_signal_emit ()
---Type <return> to continue, or q <return> to quit---
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#81 0x00007ffff74f873e in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#82 0x00007ffff71d5d56 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0
#83 0x00007ffff434e91b in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#84 0x00007ffff434dd53 in g_main_context_dispatch ()
   from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#85 0x00007ffff434e0a0 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#86 0x00007ffff434e49a in g_main_loop_run ()
   from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#87 0x000000000047e763 in app_run (full_prog_name=<optimized out>, 
    filenames=<optimized out>, alternate_system_gimprc=0x0, 
    alternate_gimprc=0x0, session_name=<optimized out>, batch_interpreter=0x0, 
    batch_commands=0x0, as_new=0, no_interface=0, no_data=0, no_fonts=0, 
    no_splash=0, be_verbose=0, use_shm=1, use_cpu_accel=1, console_messages=0, 
    use_debug_handler=0, stack_trace_mode=GIMP_STACK_TRACE_NEVER, 
    pdb_compat_mode=GIMP_PDB_COMPAT_ON) at app.c:256
#88 0x000000000047e25e in main (argc=1, argv=0x7fffffffe108) at main.c:440
```

Well, it's chineese to me, but I hope it helps someone. 

The option "--verbose" doesn't give more explanation, "--stack-trace-mode=always" neither. And if I look for it in internet, problem is many times reported (most of it in redhat's bugzilla), but no one gives solutions. So if you've an idea, I'll be very happy.

Thanks,

Pierre.

---

