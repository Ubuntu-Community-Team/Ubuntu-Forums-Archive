---
title: "GnomeBaker crashing"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by rkrizan on 2007-05-19
GnomeBaker worked great when I installed my Sony CRX230EE into my Dell desktop PC which was running Ubuntu 6.10. However, I just upgraded (yesterday) to 7.04 and GnomeBaker no longer works. It says its converting the mp3s to record as a data CD, then never starts actually burning and crashes. I have uninstalled GnomeBaker via apt-get remove gnomebaker and reinstalled hoping it would fix this problem via apt-get install gnomebaker. No change, does the same thing. Is there something I can do to fix this?

The machine that GnomeBaker is not working on is actually my sister's machine. I convinced her to try Ubuntu Linux after showing her what my Inspiron laptop could do with Beryl and such. I also showed her GnomeBaker, and explained to her that it was completely free and did the same thing that either Roxio and Nero did for burning audio cds.

Any help will be appreciated. I will post log output after I get done running gnomebaker via a shell and see what the output says from there.

Here is how the terminal log goes:

stacey@ubuntu:~$ gnomebaker

(process:7806): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
called, but the GLib threading system has not been initialised yet, something that must happen before
any other GLib function is called. The application needs to be fixed so that it calls if (!g_thread_supported()) g_thread_unit(NULL);
as very first thing in its main() function. Please file a bug against this application.

** ERROR **: file mp3-c.c: line 518 (III_huffman_decode): assertion failed: (i <= SSLIMIT * SBLIMIT)
aborting...
Aborted (core dumped)
stacey@ubuntu:~$


.... yea "g_thread_supported" and "g_thread_unit".... sounds like a garbage rap song to me.

---

### Post by rkrizan on 2007-05-19
Nobody has any idea? Anyone know of a way to speak with the developers or something, maybe via an IRC channel on FreeNode or something?

---

### Post by RHTopics on 2007-05-19
There is a bug report filed in launchpad for the problem you are having with gnomebaker.

[https://bugs.launchpad.net/ubuntu/+source/gnomebaker/+bug/113871](https://bugs.launchpad.net/ubuntu/+source/gnomebaker/+bug/113871)

---

