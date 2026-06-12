---
title: "Can't get Brasero to burn 298kb jpeg."
date: 2009-07-19
forum: Multimedia Software
---

### Post by badaveil on 2009-07-19
I just tried to burn a small jpeg on a brand new dvdr but Brasero stated there's insufficient space on media(see below). I don't understand. Can anyone help?

_________________________
Log:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile deactivating
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_set_current_action
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_add_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile finished track successfully
BraseroMd5sumFile stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
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
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-speed=22
	-use-the-force-luke=tty
	-Z
	/dev/scd1
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_MWNEXU
	-exclude-list
	/tmp/brasero_tmp_OQNEXU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: Total extents scheduled to be written = 331
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs stopping
Session error : Insufficient space on media (0 available for 331) (brasero_burn_record burn.c:2270)

---

