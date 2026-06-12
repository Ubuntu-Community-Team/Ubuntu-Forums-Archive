---
title: "I can't burn a dual-layer DVD? Help please?"
date: 2009-06-25
forum: Multimedia Software
---

### Post by elcisitiak on 2009-06-25
I'm trying to burn a dual-layer DVD, but it won't let me. I've burned working (single-layer) DVDs before. I have a dual-layer DVD burner. It spends an hour or so checking for everything, and I get this error-log: 

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI burn:// URI found burn:///VIDEO_TS
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///VIDEO_TS
BraseroBurnURI Adding directory (null) at /VIDEO_TS/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_02_0.BUP at /VIDEO_TS/VTS_02_0.BUP
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_02_0.IFO at /VIDEO_TS/VTS_02_0.IFO
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_02_0.VOB at /VIDEO_TS/VTS_02_0.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_03_0.BUP at /VIDEO_TS/VTS_03_0.BUP
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_03_0.IFO at /VIDEO_TS/VTS_03_0.IFO
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_03_0.VOB at /VIDEO_TS/VTS_03_0.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_02_1.VOB at /VIDEO_TS/VTS_02_1.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_01_1.VOB at /VIDEO_TS/VTS_01_1.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_01_4.VOB at /VIDEO_TS/VTS_01_4.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_01_5.VOB at /VIDEO_TS/VTS_01_5.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_01_2.VOB at /VIDEO_TS/VTS_01_2.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_01_0.VOB at /VIDEO_TS/VTS_01_0.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_03_1.VOB at /VIDEO_TS/VTS_03_1.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_02_2.VOB at /VIDEO_TS/VTS_02_2.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VIDEO_TS.BUP at /VIDEO_TS/VIDEO_TS.BUP
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VIDEO_TS.IFO at /VIDEO_TS/VIDEO_TS.IFO
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VIDEO_TS.VOB at /VIDEO_TS/VIDEO_TS.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_01_0.BUP at /VIDEO_TS/VTS_01_0.BUP
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_01_0.IFO at /VIDEO_TS/VTS_01_0.IFO
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_01_3.VOB at /VIDEO_TS/VTS_01_3.VOB
BraseroBurnURI Added file /home/rel/Videos/FILENAME/VIDEO_TS/VTS_01_6.VOB at /VIDEO_TS/VTS_01_6.VOB
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -dvd-compat
    -speed=4
    -use-the-force-luke=tty
    -Z
    /dev/sr0
    -dry-run
    -r
    -J
    -input-charset
    utf8
    -graft-points
    -path-list
    /tmp/brasero_tmp_5OP3VU
    -exclude-list
    /tmp/brasero_tmp_USP3VU
    -print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_5OP3VU -exclude-list /tmp/brasero_tmp_USP3VU -print-size | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 3831418
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs Finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -dvd-compat
    -speed=4
    -use-the-force-luke=tracksize:3831418
    -use-the-force-luke=tty
    -Z
    /dev/sr0
    -r
    -J
    -input-charset
    utf8
    -graft-points
    -path-list
    /tmp/brasero_tmp_MSZ8VU
    -exclude-list
    /tmp/brasero_tmp_AIZ8VU
    -V
    Data disc (25 Jun 09)
    -A
    Brasero-2.26.1
    -sysid
    LINUX
    -v
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_MSZ8VU -exclude-list /tmp/brasero_tmp_AIZ8VU -V Data disc (25 Jun 09) -A Brasero-2.26.1 -sysid LINUX -v | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: genisoimage 1.1.9 (Linux)
BraseroGrowisofs stderr: Scanning /tmp/brasero_tmp_A9iRC6
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17
BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 19
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 20
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 24
BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 28
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    3
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 31
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    2
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 33
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 33
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 34
BraseroGrowisofs stderr:   0.13% done, estimate finish Thu Jun 25 02:16:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.26% done, estimate finish Thu Jun 25 02:16:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.39% done, estimate finish Thu Jun 25 02:16:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stderr:   0.52% done, estimate finish Thu Jun 25 04:55:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.65% done, estimate finish Thu Jun 25 04:26:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.78% done, estimate finish Thu Jun 25 04:04:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.91% done, estimate finish Thu Jun 25 03:47:20 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   1.04% done, estimate finish Thu Jun 25 03:35:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   1.17% done, estimate finish Thu Jun 25 03:28:29 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   1.31% done, estimate finish Thu Jun 25 03:21:16 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   1.44% done, estimate finish Thu Jun 25 03:16:30 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   1.57% done, estimate finish Thu Jun 25 03:11:29 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   1.70% done, estimate finish Thu Jun 25 03:08:12 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   1.83% done, estimate finish Thu Jun 25 03:03:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   1.96% done, estimate finish Thu Jun 25 03:01:15 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   2.09% done, estimate finish Thu Jun 25 02:57:39 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   2.22% done, estimate finish Thu Jun 25 02:56:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   2.35% done, estimate finish Thu Jun 25 02:54:27 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   2.48% done, estimate finish Thu Jun 25 02:53:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   2.61% done, estimate finish Thu Jun 25 02:51:53 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   2.74% done, estimate finish Thu Jun 25 02:50:12 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   2.87% done, estimate finish Thu Jun 25 02:48:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   3.00% done, estimate finish Thu Jun 25 02:47:47 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   3.13% done, estimate finish Thu Jun 25 02:46:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   3.26% done, estimate finish Thu Jun 25 02:44:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   3.39% done, estimate finish Thu Jun 25 02:44:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   3.52% done, estimate finish Thu Jun 25 02:43:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   3.65% done, estimate finish Thu Jun 25 02:43:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   3.78% done, estimate finish Thu Jun 25 02:42:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   3.92% done, estimate finish Thu Jun 25 02:42:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   4.05% done, estimate finish Thu Jun 25 02:41:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   4.18% done, estimate finish Thu Jun 25 02:41:17 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   4.31% done, estimate finish Thu Jun 25 02:40:54 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   4.44% done, estimate finish Thu Jun 25 02:40:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   4.57% done, estimate finish Thu Jun 25 02:40:13 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   4.70% done, estimate finish Thu Jun 25 02:39:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   4.83% done, estimate finish Thu Jun 25 02:39:16 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   4.96% done, estimate finish Thu Jun 25 02:39:20 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   5.09% done, estimate finish Thu Jun 25 02:39:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   5.22% done, estimate finish Thu Jun 25 02:38:48 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   5.35% done, estimate finish Thu Jun 25 02:38:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   5.48% done, estimate finish Thu Jun 25 02:38:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   5.61% done, estimate finish Thu Jun 25 02:37:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   5.74% done, estimate finish Thu Jun 25 02:37:19 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   5.87% done, estimate finish Thu Jun 25 02:36:51 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   6.00% done, estimate finish Thu Jun 25 02:36:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   6.13% done, estimate finish Thu Jun 25 02:36:47 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   6.26% done, estimate finish Thu Jun 25 02:36:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   6.39% done, estimate finish Thu Jun 25 02:36:12 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   6.53% done, estimate finish Thu Jun 25 02:35:48 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   6.66% done, estimate finish Thu Jun 25 02:35:55 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   6.79% done, estimate finish Thu Jun 25 02:35:47 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   6.92% done, estimate finish Thu Jun 25 02:35:54 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   7.05% done, estimate finish Thu Jun 25 02:35:32 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   7.18% done, estimate finish Thu Jun 25 02:35:11 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   7.31% done, estimate finish Thu Jun 25 02:35:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   7.44% done, estimate finish Thu Jun 25 02:34:44 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   7.57% done, estimate finish Thu Jun 25 02:34:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   7.70% done, estimate finish Thu Jun 25 02:34:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   7.83% done, estimate finish Thu Jun 25 02:34:39 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   7.96% done, estimate finish Thu Jun 25 02:34:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   8.09% done, estimate finish Thu Jun 25 02:34:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   8.22% done, estimate finish Thu Jun 25 02:34:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   8.35% done, estimate finish Thu Jun 25 02:34:30 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   8.48% done, estimate finish Thu Jun 25 02:34:25 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   8.61% done, estimate finish Thu Jun 25 02:34:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   8.74% done, estimate finish Thu Jun 25 02:34:26 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   8.87% done, estimate finish Thu Jun 25 02:34:10 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   9.00% done, estimate finish Thu Jun 25 02:33:54 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   9.14% done, estimate finish Thu Jun 25 02:33:39 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   9.27% done, estimate finish Thu Jun 25 02:33:35 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   9.40% done, estimate finish Thu Jun 25 02:33:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   9.53% done, estimate finish Thu Jun 25 02:33:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   9.66% done, estimate finish Thu Jun 25 02:33:13 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   9.79% done, estimate finish Thu Jun 25 02:33:20 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   9.92% done, estimate finish Thu Jun 25 02:33:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  10.05% done, estimate finish Thu Jun 25 02:33:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  10.18% done, estimate finish Thu Jun 25 02:33:00 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  10.31% done, estimate finish Thu Jun 25 02:32:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  10.44% done, estimate finish Thu Jun 25 02:32:54 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  10.57% done, estimate finish Thu Jun 25 02:32:51 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  10.70% done, estimate finish Thu Jun 25 02:32:48 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  10.83% done, estimate finish Thu Jun 25 02:32:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  10.96% done, estimate finish Thu Jun 25 02:32:52 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  11.09% done, estimate finish Thu Jun 25 02:32:40 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  11.22% done, estimate finish Thu Jun 25 02:32:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  11.35% done, estimate finish Thu Jun 25 02:32:26 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  11.48% done, estimate finish Thu Jun 25 02:32:24 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  11.61% done, estimate finish Thu Jun 25 02:32:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  11.75% done, estimate finish Thu Jun 25 02:32:19 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  11.88% done, estimate finish Thu Jun 25 02:32:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  12.01% done, estimate finish Thu Jun 25 02:32:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  12.14% done, estimate finish Thu Jun 25 02:32:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  12.27% done, estimate finish Thu Jun 25 02:32:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  12.40% done, estimate finish Thu Jun 25 02:32:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  12.53% done, estimate finish Thu Jun 25 02:31:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  12.66% done, estimate finish Thu Jun 25 02:32:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  12.79% done, estimate finish Thu Jun 25 02:32:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  12.92% done, estimate finish Thu Jun 25 02:32:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  13.05% done, estimate finish Thu Jun 25 02:32:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  13.18% done, estimate finish Thu Jun 25 02:31:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  13.31% done, estimate finish Thu Jun 25 02:32:10 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  13.44% done, estimate finish Thu Jun 25 02:32:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  13.57% done, estimate finish Thu Jun 25 02:31:59 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  13.70% done, estimate finish Thu Jun 25 02:31:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  13.83% done, estimate finish Thu Jun 25 02:31:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  13.96% done, estimate finish Thu Jun 25 02:31:32 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  14.09% done, estimate finish Thu Jun 25 02:31:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  14.22% done, estimate finish Thu Jun 25 02:31:29 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  14.36% done, estimate finish Thu Jun 25 02:31:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  14.49% done, estimate finish Thu Jun 25 02:31:20 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  14.62% done, estimate finish Thu Jun 25 02:31:18 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  14.75% done, estimate finish Thu Jun 25 02:31:10 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  14.88% done, estimate finish Thu Jun 25 02:31:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  15.01% done, estimate finish Thu Jun 25 02:31:01 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  15.14% done, estimate finish Thu Jun 25 02:30:53 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  15.27% done, estimate finish Thu Jun 25 02:30:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  15.40% done, estimate finish Thu Jun 25 02:30:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  15.53% done, estimate finish Thu Jun 25 02:30:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  15.66% done, estimate finish Thu Jun 25 02:30:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  15.79% done, estimate finish Thu Jun 25 02:30:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  15.92% done, estimate finish Thu Jun 25 02:30:35 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  16.05% done, estimate finish Thu Jun 25 02:30:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  16.18% done, estimate finish Thu Jun 25 02:30:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  16.31% done, estimate finish Thu Jun 25 02:30:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  16.44% done, estimate finish Thu Jun 25 02:30:32 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  16.57% done, estimate finish Thu Jun 25 02:30:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  16.70% done, estimate finish Thu Jun 25 02:30:30 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  16.83% done, estimate finish Thu Jun 25 02:30:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  16.97% done, estimate finish Thu Jun 25 02:30:35 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  17.10% done, estimate finish Thu Jun 25 02:30:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  17.23% done, estimate finish Thu Jun 25 02:30:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  17.36% done, estimate finish Thu Jun 25 02:30:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  17.49% done, estimate finish Thu Jun 25 02:30:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  17.62% done, estimate finish Thu Jun 25 02:30:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  17.75% done, estimate finish Thu Jun 25 02:30:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  17.88% done, estimate finish Thu Jun 25 02:30:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  18.01% done, estimate finish Thu Jun 25 02:30:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  18.14% done, estimate finish Thu Jun 25 02:30:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  18.27% done, estimate finish Thu Jun 25 02:30:44 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  18.40% done, estimate finish Thu Jun 25 02:30:49 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  18.53% done, estimate finish Thu Jun 25 02:30:53 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  18.66% done, estimate finish Thu Jun 25 02:30:53 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  18.79% done, estimate finish Thu Jun 25 02:30:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  18.92% done, estimate finish Thu Jun 25 02:30:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  19.05% done, estimate finish Thu Jun 25 02:30:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  19.18% done, estimate finish Thu Jun 25 02:30:44 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  19.31% done, estimate finish Thu Jun 25 02:30:54 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  19.44% done, estimate finish Thu Jun 25 02:30:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  19.58% done, estimate finish Thu Jun 25 02:31:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  19.71% done, estimate finish Thu Jun 25 02:31:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  19.84% done, estimate finish Thu Jun 25 02:31:11 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  19.97% done, estimate finish Thu Jun 25 02:31:20 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  20.10% done, estimate finish Thu Jun 25 02:31:24 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  20.23% done, estimate finish Thu Jun 25 02:31:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  20.36% done, estimate finish Thu Jun 25 02:31:27 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  20.49% done, estimate finish Thu Jun 25 02:31:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  20.62% done, estimate finish Thu Jun 25 02:31:30 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  20.75% done, estimate finish Thu Jun 25 02:31:29 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  20.88% done, estimate finish Thu Jun 25 02:31:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  21.01% done, estimate finish Thu Jun 25 02:31:22 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  21.14% done, estimate finish Thu Jun 25 02:31:16 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  21.27% done, estimate finish Thu Jun 25 02:31:16 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  21.40% done, estimate finish Thu Jun 25 02:31:15 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  21.53% done, estimate finish Thu Jun 25 02:31:09 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  21.66% done, estimate finish Thu Jun 25 02:31:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  21.79% done, estimate finish Thu Jun 25 02:31:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  21.92% done, estimate finish Thu Jun 25 02:30:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  22.05% done, estimate finish Thu Jun 25 02:30:53 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  22.19% done, estimate finish Thu Jun 25 02:30:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  22.32% done, estimate finish Thu Jun 25 02:30:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  22.45% done, estimate finish Thu Jun 25 02:30:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  22.58% done, estimate finish Thu Jun 25 02:30:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  22.71% done, estimate finish Thu Jun 25 02:30:14 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  22.84% done, estimate finish Thu Jun 25 02:30:09 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  22.97% done, estimate finish Thu Jun 25 02:30:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  23.10% done, estimate finish Thu Jun 25 02:29:55 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  23.23% done, estimate finish Thu Jun 25 02:29:51 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  23.36% done, estimate finish Thu Jun 25 02:29:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  23.49% done, estimate finish Thu Jun 25 02:29:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  23.62% done, estimate finish Thu Jun 25 02:29:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  23.75% done, estimate finish Thu Jun 25 02:29:32 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  23.88% done, estimate finish Thu Jun 25 02:29:32 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  24.01% done, estimate finish Thu Jun 25 02:29:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  24.14% done, estimate finish Thu Jun 25 02:29:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  24.27% done, estimate finish Thu Jun 25 02:29:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  24.40% done, estimate finish Thu Jun 25 02:29:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  24.53% done, estimate finish Thu Jun 25 02:29:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  24.66% done, estimate finish Thu Jun 25 02:29:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  24.80% done, estimate finish Thu Jun 25 02:29:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  24.93% done, estimate finish Thu Jun 25 02:29:27 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  25.06% done, estimate finish Thu Jun 25 02:29:27 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  25.19% done, estimate finish Thu Jun 25 02:29:26 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  25.32% done, estimate finish Thu Jun 25 02:29:30 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  25.45% done, estimate finish Thu Jun 25 02:29:30 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  25.58% done, estimate finish Thu Jun 25 02:29:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  25.71% done, estimate finish Thu Jun 25 02:29:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  25.84% done, estimate finish Thu Jun 25 02:29:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  25.97% done, estimate finish Thu Jun 25 02:29:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  26.10% done, estimate finish Thu Jun 25 02:29:44 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  26.23% done, estimate finish Thu Jun 25 02:29:48 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  26.36% done, estimate finish Thu Jun 25 02:29:51 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  26.49% done, estimate finish Thu Jun 25 02:29:55 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  26.62% done, estimate finish Thu Jun 25 02:29:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  26.75% done, estimate finish Thu Jun 25 02:29:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  26.88% done, estimate finish Thu Jun 25 02:29:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  27.01% done, estimate finish Thu Jun 25 02:30:01 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  27.14% done, estimate finish Thu Jun 25 02:30:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  27.27% done, estimate finish Thu Jun 25 02:30:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  27.41% done, estimate finish Thu Jun 25 02:30:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  27.54% done, estimate finish Thu Jun 25 02:30:15 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  27.67% done, estimate finish Thu Jun 25 02:30:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  27.80% done, estimate finish Thu Jun 25 02:30:25 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  27.93% done, estimate finish Thu Jun 25 02:30:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  28.06% done, estimate finish Thu Jun 25 02:30:27 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  28.19% done, estimate finish Thu Jun 25 02:30:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  28.32% done, estimate finish Thu Jun 25 02:30:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  28.45% done, estimate finish Thu Jun 25 02:30:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  28.58% done, estimate finish Thu Jun 25 02:30:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  28.71% done, estimate finish Thu Jun 25 02:30:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  28.84% done, estimate finish Thu Jun 25 02:30:39 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  28.97% done, estimate finish Thu Jun 25 02:30:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  29.10% done, estimate finish Thu Jun 25 02:30:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  29.23% done, estimate finish Thu Jun 25 02:30:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  29.36% done, estimate finish Thu Jun 25 02:30:40 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  29.49% done, estimate finish Thu Jun 25 02:30:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  29.62% done, estimate finish Thu Jun 25 02:30:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  29.75% done, estimate finish Thu Jun 25 02:30:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  29.88% done, estimate finish Thu Jun 25 02:30:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  30.02% done, estimate finish Thu Jun 25 02:30:48 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  30.15% done, estimate finish Thu Jun 25 02:30:51 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  30.28% done, estimate finish Thu Jun 25 02:30:50 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  30.41% done, estimate finish Thu Jun 25 02:30:50 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  30.54% done, estimate finish Thu Jun 25 02:30:49 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  30.67% done, estimate finish Thu Jun 25 02:30:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  30.80% done, estimate finish Thu Jun 25 02:30:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  30.93% done, estimate finish Thu Jun 25 02:30:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  31.06% done, estimate finish Thu Jun 25 02:30:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  31.19% done, estimate finish Thu Jun 25 02:30:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  31.32% done, estimate finish Thu Jun 25 02:30:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  31.45% done, estimate finish Thu Jun 25 02:30:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  31.58% done, estimate finish Thu Jun 25 02:30:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  31.71% done, estimate finish Thu Jun 25 02:30:29 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  31.84% done, estimate finish Thu Jun 25 02:30:29 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  31.97% done, estimate finish Thu Jun 25 02:30:25 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  32.10% done, estimate finish Thu Jun 25 02:30:25 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  32.23% done, estimate finish Thu Jun 25 02:30:25 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  32.36% done, estimate finish Thu Jun 25 02:30:24 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  32.49% done, estimate finish Thu Jun 25 02:30:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  32.63% done, estimate finish Thu Jun 25 02:30:20 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  32.76% done, estimate finish Thu Jun 25 02:30:17 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  32.89% done, estimate finish Thu Jun 25 02:30:14 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  33.02% done, estimate finish Thu Jun 25 02:30:10 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  33.15% done, estimate finish Thu Jun 25 02:30:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  33.28% done, estimate finish Thu Jun 25 02:30:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  33.41% done, estimate finish Thu Jun 25 02:30:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  33.54% done, estimate finish Thu Jun 25 02:30:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  33.67% done, estimate finish Thu Jun 25 02:30:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  33.80% done, estimate finish Thu Jun 25 02:30:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  33.93% done, estimate finish Thu Jun 25 02:30:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  34.06% done, estimate finish Thu Jun 25 02:29:59 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  34.19% done, estimate finish Thu Jun 25 02:29:59 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  34.32% done, estimate finish Thu Jun 25 02:29:56 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  34.45% done, estimate finish Thu Jun 25 02:29:56 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  34.58% done, estimate finish Thu Jun 25 02:29:55 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  34.71% done, estimate finish Thu Jun 25 02:29:55 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  34.84% done, estimate finish Thu Jun 25 02:29:52 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  34.97% done, estimate finish Thu Jun 25 02:29:52 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  35.10% done, estimate finish Thu Jun 25 02:29:49 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  35.24% done, estimate finish Thu Jun 25 02:29:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  35.37% done, estimate finish Thu Jun 25 02:29:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  35.50% done, estimate finish Thu Jun 25 02:29:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  35.63% done, estimate finish Thu Jun 25 02:29:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  35.76% done, estimate finish Thu Jun 25 02:29:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  35.89% done, estimate finish Thu Jun 25 02:29:17 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  36.02% done, estimate finish Thu Jun 25 02:29:14 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  36.15% done, estimate finish Thu Jun 25 02:29:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  36.28% done, estimate finish Thu Jun 25 02:29:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  36.41% done, estimate finish Thu Jun 25 02:29:00 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  36.54% done, estimate finish Thu Jun 25 02:28:55 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  36.67% done, estimate finish Thu Jun 25 02:28:52 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  36.80% done, estimate finish Thu Jun 25 02:28:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  36.93% done, estimate finish Thu Jun 25 02:28:44 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  37.06% done, estimate finish Thu Jun 25 02:28:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  37.19% done, estimate finish Thu Jun 25 02:28:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  37.32% done, estimate finish Thu Jun 25 02:28:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  37.45% done, estimate finish Thu Jun 25 02:28:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  37.58% done, estimate finish Thu Jun 25 02:28:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  37.71% done, estimate finish Thu Jun 25 02:28:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  37.85% done, estimate finish Thu Jun 25 02:28:26 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  37.98% done, estimate finish Thu Jun 25 02:28:26 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  38.11% done, estimate finish Thu Jun 25 02:28:26 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  38.24% done, estimate finish Thu Jun 25 02:28:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  38.37% done, estimate finish Thu Jun 25 02:28:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  38.50% done, estimate finish Thu Jun 25 02:28:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  38.63% done, estimate finish Thu Jun 25 02:28:18 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  38.76% done, estimate finish Thu Jun 25 02:28:16 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  38.89% done, estimate finish Thu Jun 25 02:28:16 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  39.02% done, estimate finish Thu Jun 25 02:28:14 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  39.15% done, estimate finish Thu Jun 25 02:28:14 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  39.28% done, estimate finish Thu Jun 25 02:28:11 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  39.41% done, estimate finish Thu Jun 25 02:28:09 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  39.54% done, estimate finish Thu Jun 25 02:28:09 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  39.67% done, estimate finish Thu Jun 25 02:28:09 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  39.80% done, estimate finish Thu Jun 25 02:28:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  39.93% done, estimate finish Thu Jun 25 02:28:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  40.06% done, estimate finish Thu Jun 25 02:28:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  40.19% done, estimate finish Thu Jun 25 02:28:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  40.32% done, estimate finish Thu Jun 25 02:28:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  40.46% done, estimate finish Thu Jun 25 02:28:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  40.59% done, estimate finish Thu Jun 25 02:28:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  40.72% done, estimate finish Thu Jun 25 02:28:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  40.85% done, estimate finish Thu Jun 25 02:28:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  40.98% done, estimate finish Thu Jun 25 02:28:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  41.11% done, estimate finish Thu Jun 25 02:28:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  41.24% done, estimate finish Thu Jun 25 02:28:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  41.37% done, estimate finish Thu Jun 25 02:28:01 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  41.50% done, estimate finish Thu Jun 25 02:28:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  41.63% done, estimate finish Thu Jun 25 02:27:59 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  41.76% done, estimate finish Thu Jun 25 02:27:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  41.89% done, estimate finish Thu Jun 25 02:27:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  42.02% done, estimate finish Thu Jun 25 02:27:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  42.15% done, estimate finish Thu Jun 25 02:27:55 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  42.28% done, estimate finish Thu Jun 25 02:27:55 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  42.41% done, estimate finish Thu Jun 25 02:27:53 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  42.54% done, estimate finish Thu Jun 25 02:27:51 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  42.67% done, estimate finish Thu Jun 25 02:27:51 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  42.80% done, estimate finish Thu Jun 25 02:27:52 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  42.93% done, estimate finish Thu Jun 25 02:27:49 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  43.07% done, estimate finish Thu Jun 25 02:27:47 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  43.20% done, estimate finish Thu Jun 25 02:27:47 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  43.33% done, estimate finish Thu Jun 25 02:27:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  43.46% done, estimate finish Thu Jun 25 02:27:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  43.59% done, estimate finish Thu Jun 25 02:27:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  43.72% done, estimate finish Thu Jun 25 02:27:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  43.85% done, estimate finish Thu Jun 25 02:27:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  43.98% done, estimate finish Thu Jun 25 02:27:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  44.11% done, estimate finish Thu Jun 25 02:27:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  44.24% done, estimate finish Thu Jun 25 02:27:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  44.37% done, estimate finish Thu Jun 25 02:27:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  44.50% done, estimate finish Thu Jun 25 02:27:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  44.63% done, estimate finish Thu Jun 25 02:27:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  44.76% done, estimate finish Thu Jun 25 02:27:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  44.89% done, estimate finish Thu Jun 25 02:27:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  45.02% done, estimate finish Thu Jun 25 02:27:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  45.15% done, estimate finish Thu Jun 25 02:27:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  45.28% done, estimate finish Thu Jun 25 02:27:44 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  45.41% done, estimate finish Thu Jun 25 02:27:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  45.54% done, estimate finish Thu Jun 25 02:27:44 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  45.68% done, estimate finish Thu Jun 25 02:27:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  45.81% done, estimate finish Thu Jun 25 02:27:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  45.94% done, estimate finish Thu Jun 25 02:27:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  46.07% done, estimate finish Thu Jun 25 02:27:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  46.20% done, estimate finish Thu Jun 25 02:27:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  46.33% done, estimate finish Thu Jun 25 02:27:35 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  46.46% done, estimate finish Thu Jun 25 02:27:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  46.59% done, estimate finish Thu Jun 25 02:27:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  46.72% done, estimate finish Thu Jun 25 02:27:29 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  46.85% done, estimate finish Thu Jun 25 02:27:25 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  46.98% done, estimate finish Thu Jun 25 02:27:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  47.11% done, estimate finish Thu Jun 25 02:27:19 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  47.24% done, estimate finish Thu Jun 25 02:27:17 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  47.37% done, estimate finish Thu Jun 25 02:27:15 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  47.50% done, estimate finish Thu Jun 25 02:27:11 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  47.63% done, estimate finish Thu Jun 25 02:27:10 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  47.76% done, estimate finish Thu Jun 25 02:27:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  47.89% done, estimate finish Thu Jun 25 02:27:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  48.02% done, estimate finish Thu Jun 25 02:27:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  48.15% done, estimate finish Thu Jun 25 02:26:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  48.29% done, estimate finish Thu Jun 25 02:26:54 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  48.42% done, estimate finish Thu Jun 25 02:26:53 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  48.55% done, estimate finish Thu Jun 25 02:26:49 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  48.68% done, estimate finish Thu Jun 25 02:26:47 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  48.81% done, estimate finish Thu Jun 25 02:26:48 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  48.94% done, estimate finish Thu Jun 25 02:26:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  49.07% done, estimate finish Thu Jun 25 02:26:44 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  49.20% done, estimate finish Thu Jun 25 02:26:45 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  49.33% done, estimate finish Thu Jun 25 02:26:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  49.46% done, estimate finish Thu Jun 25 02:26:41 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  49.59% done, estimate finish Thu Jun 25 02:26:40 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  49.72% done, estimate finish Thu Jun 25 02:26:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  49.85% done, estimate finish Thu Jun 25 02:26:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  49.98% done, estimate finish Thu Jun 25 02:26:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  50.11% done, estimate finish Thu Jun 25 02:26:29 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  50.24% done, estimate finish Thu Jun 25 02:26:27 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  50.37% done, estimate finish Thu Jun 25 02:26:26 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  50.50% done, estimate finish Thu Jun 25 02:26:22 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  50.63% done, estimate finish Thu Jun 25 02:26:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  50.76% done, estimate finish Thu Jun 25 02:26:19 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  50.90% done, estimate finish Thu Jun 25 02:26:17 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  51.03% done, estimate finish Thu Jun 25 02:26:16 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  51.16% done, estimate finish Thu Jun 25 02:26:14 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  51.29% done, estimate finish Thu Jun 25 02:26:11 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  51.42% done, estimate finish Thu Jun 25 02:26:09 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  51.55% done, estimate finish Thu Jun 25 02:26:10 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  51.68% done, estimate finish Thu Jun 25 02:26:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  51.81% done, estimate finish Thu Jun 25 02:26:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  51.94% done, estimate finish Thu Jun 25 02:26:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  52.07% done, estimate finish Thu Jun 25 02:26:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  52.20% done, estimate finish Thu Jun 25 02:26:00 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  52.33% done, estimate finish Thu Jun 25 02:25:59 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  52.46% done, estimate finish Thu Jun 25 02:25:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  52.59% done, estimate finish Thu Jun 25 02:25:56 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  52.72% done, estimate finish Thu Jun 25 02:25:54 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  52.85% done, estimate finish Thu Jun 25 02:25:53 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  52.98% done, estimate finish Thu Jun 25 02:25:52 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  53.11% done, estimate finish Thu Jun 25 02:25:50 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  53.24% done, estimate finish Thu Jun 25 02:25:51 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  53.37% done, estimate finish Thu Jun 25 02:25:47 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  53.51% done, estimate finish Thu Jun 25 02:25:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  53.64% done, estimate finish Thu Jun 25 02:25:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  53.77% done, estimate finish Thu Jun 25 02:25:39 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  53.90% done, estimate finish Thu Jun 25 02:25:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  54.03% done, estimate finish Thu Jun 25 02:25:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  54.16% done, estimate finish Thu Jun 25 02:25:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  54.29% done, estimate finish Thu Jun 25 02:25:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  54.42% done, estimate finish Thu Jun 25 02:25:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  54.55% done, estimate finish Thu Jun 25 02:25:33 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  54.68% done, estimate finish Thu Jun 25 02:25:32 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  54.81% done, estimate finish Thu Jun 25 02:25:30 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  54.94% done, estimate finish Thu Jun 25 02:25:27 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  55.07% done, estimate finish Thu Jun 25 02:25:26 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  55.20% done, estimate finish Thu Jun 25 02:25:24 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  55.33% done, estimate finish Thu Jun 25 02:25:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  55.46% done, estimate finish Thu Jun 25 02:25:20 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  55.59% done, estimate finish Thu Jun 25 02:25:19 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  55.72% done, estimate finish Thu Jun 25 02:25:17 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  55.85% done, estimate finish Thu Jun 25 02:25:16 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  55.98% done, estimate finish Thu Jun 25 02:25:15 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  56.12% done, estimate finish Thu Jun 25 02:25:14 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  56.25% done, estimate finish Thu Jun 25 02:25:12 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  56.38% done, estimate finish Thu Jun 25 02:25:11 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  56.51% done, estimate finish Thu Jun 25 02:25:10 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  56.64% done, estimate finish Thu Jun 25 02:25:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  56.77% done, estimate finish Thu Jun 25 02:25:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  56.90% done, estimate finish Thu Jun 25 02:25:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  57.03% done, estimate finish Thu Jun 25 02:26:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  57.16% done, estimate finish Thu Jun 25 02:26:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  57.29% done, estimate finish Thu Jun 25 02:26:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-[ WRITE@LBA=214460h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: closing track
BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2602)

```

This is after I had deleted the empty AUDIO_TS folder I thought was necessary. I was receiving an error message about the VIDEO_TS folder being missing or invalid with it, and I read that the AUDIO_TS directory could be causing that problem. The VOBs are good, they play on my harddrive just fine, and I've tried a couple different projects, both with the same results. Please help me!

---

### Post by khelben1979 on 2009-06-25
Try [k3b]("http://en.wikipedia.org/wiki/K3b") instead.

```
sudo apt-get install k3b
```
to install it.

---

### Post by elcisitiak on 2009-06-27
Alright, I tried that, but K3b doesn't even recognize that there's media in the drive.

---

### Post by khelben1979 on 2009-06-27
Have you tried with other brands? I've read before on this forum that some brands is not working very good with Linux, I can't still confirm to why, but they have said that [Verbatim]("http://en.wikipedia.org/wiki/Verbatim_Corporation") discs should be okay.

What type of discs are you trying with at the present? And what are their burning attributes (2x, 4x etc etc.) ?

---

### Post by elcisitiak on 2009-07-04
I'm using Memorex, I haven't seen a whole lot of selection but I can look again if necessary... this is going to get expensive... I was trying to burn at max, then 4x, then 2x when that didn't work, nothing seems to be helping. 

If I can't do this, do you know of something that will allow me to split the DVD and put it on two disks?

---

### Post by khelben1979 on 2009-07-05
What is the exact model of your burner and have you tried to upgrade the firmware hardware for it?

I think it's worth a try.

---

