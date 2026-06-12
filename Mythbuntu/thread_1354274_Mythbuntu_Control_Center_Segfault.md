---
title: "Mythbuntu Control Center Segfault"
date: 2009-12-13
forum: Mythbuntu
---

### Post by rfpeake on 2009-12-13
Starting Mythbuntu Control Center from System/Administration menu or from the command line generates a Python segfault. The Control Center is visible for an instant and then disappears.  I am running 8.04 (Hardy) Kernal 2.6.24-26.  System is an Athlon 64 X2 with 2Gb DDR RAM.  

Any help would be greatly appreciated.

OUTPUT
From /var/log/messages:
Dec 13 17:20:49 asus kernel: [26325.648273] python[15669]: segfault at 00000004 eip b58ddaa0 esp bffac530 error 4

FROM TERMINAL:
:~$ /usr/bin/mythbuntu-control-centre

Reading package lists... Done

Building dependency tree       

Reading state information... Done

/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:208: Warning: g_error_free: assertion `error != NULL' failed

  gtk.main()

( mythbuntu-control-centre:16098 ): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

( mythbuntu-control-centre:16098 ): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249): IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)

---

