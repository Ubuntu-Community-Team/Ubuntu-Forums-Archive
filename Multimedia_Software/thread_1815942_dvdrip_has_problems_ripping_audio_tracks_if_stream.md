---
title: "dvd::rip has problems ripping audio tracks if stream id is not 0x80, but 0x81"
date: 2011-08-01
forum: Multimedia Software
---

### Post by derolf on 2011-08-01
Hi guys,

-- if this post is at the wrong place, please move --

I had problems with dvd::rip ripping a DVD, where the FIRST audio track had stream id 0x81 instead of the default 0x80.

The reason is that neither tcprobe nor lsdvd check the audio_control value of the pgc to identify the correct stream id, they by default assume that the first track maps to 0x80, the second to 0x81, and so on (for DTS, the first one is 0x88). (BTW. k9copy correctly identifies the stream.)

I did a quickfix in the source code of tcprobe and purged lsdvd from my Ubuntu installation, and now dvd::rip correctly identifies the FIRST track as true track number 2 and passes this along transcoder to extract the right track. It's important to remove lsdvd because dvd::rip uses lsdvd as default and only tcprobe as fall back if lsdvd doesn't exist.

The correct fix would be to pass along the stream id all the way the whole tool chain.

Here is the patch for transcoder/import/dvd_reader.c of transcode 1.1.5

```

--- dvd_reader.c.old    2009-10-31 17:38:18.000000000 +0100
+++ dvd_reader.c        2011-08-01 12:05:48.646680927 +0200
@@ -586,6 +586,7 @@
     ifo_handle_t   *vmg_file;
     pgc_t          *cur_pgc;
     ifo_handle_t   *vts_file;
+    ifo_handle_t   *tvts_file;
     vts_ptt_srpt_t *vts_ptt_srpt;
     video_attr_t   *v_attr;
     audio_attr_t   *a_attr;
@@ -611,25 +612,44 @@
         goto bad_title;
     }
 
+    tvts_file = ifoOpen(dvd, tt_srpt->title[ titleid ].title_set_nr);
+    if (!tvts_file) {
+        tc_log_error(__FILE__, "Can't open the title %d info file.",
+                     tt_srpt->title[ titleid ].title_set_nr );
+        goto bad_title;
+    }
+
     vts_file = ifoOpen(dvd, tt_srpt->title[ titleid ].title_set_nr);
     if (!vts_file) {
         tc_log_error(__FILE__, "Can't open the title %d info file.",
-                     tt_srpt->title[ titleid ].title_set_nr );
+                               tt_srpt->title[ titleid ].title_set_nr);
         goto bad_title;
     }
 
-    if (vts_file->vtsi_mat) {
-        v_attr = &vts_file->vtsi_mat->vts_video_attr;
+    ttn = tt_srpt->title[ titleid ].vts_ttn;
+    vts_ptt_srpt = vts_file->vts_ptt_srpt;
+    pgc_id = vts_ptt_srpt->title[ ttn - 1 ].ptt[0].pgcn;
+    cur_pgc = vts_file->vts_pgcit->pgci_srp[ pgc_id - 1 ].pgc;
+    
+    if (tvts_file->vtsi_mat) {
+        v_attr = &tvts_file->vtsi_mat->vts_video_attr;
 
         stats_video_attributes(v_attr, info);
 
-        for (i = 0; i < vts_file->vtsi_mat->nr_of_vts_audio_streams; i++) {
-            a_attr = &vts_file->vtsi_mat->vts_audio_attr[i];
-            stats_audio_attributes(a_attr, i, info);
+        for (i = 0; i < tvts_file->vtsi_mat->nr_of_vts_audio_streams; i++) {
+           int streamId= cur_pgc->audio_control[i] >> 8;
+           if( streamId != 0 )
+           {
+              a_attr = &tvts_file->vtsi_mat->vts_audio_attr[i];
+             streamId-= 0x80;
+             if( a_attr->audio_format == 6 ) 
+               streamId-= 0x8; // for DTS
+              stats_audio_attributes(a_attr, streamId, info);
+           }
         }
 
-        for (i = 0; i < vts_file->vtsi_mat->nr_of_vts_subp_streams; i++) {
-            s_attr = &vts_file->vtsi_mat->vts_subp_attr[i];
+        for (i = 0; i < tvts_file->vtsi_mat->nr_of_vts_subp_streams; i++) {
+            s_attr = &tvts_file->vtsi_mat->vts_subp_attr[i];
             stats_subp_attributes(s_attr, i, info);
         }
     } else {
@@ -637,19 +657,6 @@
         goto bad_title;
     }
 
-    vts_file = NULL; /* uh?!? -- FR */
-
-    vts_file = ifoOpen(dvd, tt_srpt->title[ titleid ].title_set_nr);
-    if (!vts_file) {
-        tc_log_error(__FILE__, "Can't open the title %d info file.",
-                               tt_srpt->title[ titleid ].title_set_nr);
-        goto bad_title;
-    }
-
-    ttn = tt_srpt->title[ titleid ].vts_ttn;
-    vts_ptt_srpt = vts_file->vts_ptt_srpt;
-    pgc_id = vts_ptt_srpt->title[ ttn - 1 ].ptt[0].pgcn;
-    cur_pgc = vts_file->vts_pgcit->pgci_srp[ pgc_id - 1 ].pgc;
 
     switch (((cur_pgc->playback_time).frame_u & 0xc0) >> 6) {
       case 1:

```

dero

---

