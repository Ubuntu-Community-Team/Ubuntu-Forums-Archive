---
title: "Error burning DVD -R"
date: 2010-07-30
forum: Multimedia Software
---

### Post by keithclark on 2010-07-30
I'm trying to burn a DVD here with absolutely no luck.  I have Maxell DVD -Rs and no matter which one I try with both K3B or Brasero I only get errors.

Ubuntu 10.04
Asus SDRW-08D 1 S-U DVD drive

Any help appreciated.


Brasero log file:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs creating input
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-path-list
	/tmp/brasero_tmp_13XYGV
	-exclude-list
	/tmp/brasero_tmp_E4XYGV
	-V
	Data disc (30 Jul 10)
	-A
	Brasero-2.30.2
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 2283075
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage Finished track successfully
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage stopping
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs creating input
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=8
	-use-the-force-luke=tracksize:2283075
	-use-the-force-luke=tty
	-Z
	/dev/sr0=/proc/self/fd/0
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroGrowisofs
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-path-list
	/tmp/brasero_tmp_X76JGV
	-exclude-list
	/tmp/brasero_tmp_PO7JGV
	-V
	Data disc (30 Jul 10)
	-A
	Brasero-2.30.2
	-sysid
	LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/proc/self/fd/0 of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGenisoimage stderr:   0.22% done, estimate finish Fri Jul 30 14:43:33 2010
BraseroGenisoimage stderr:   0.44% done, estimate finish Fri Jul 30 14:43:33 2010
BraseroGenisoimage stderr:   0.66% done, estimate finish Fri Jul 30 14:43:33 2010
BraseroGrowisofs stderr: :-( unable to PERFORM OPC: Input/output error
BraseroGrowisofs stderr: :-( unable to GET EVENT: Input/output error
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr: :-( unable to WRITE@LBA=0h: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroGrowisofs
BraseroGrowisofs stopping
BraseroGrowisofs closing connection for BraseroGrowisofs
Session error : unknown (brasero_burn_record brasero-burn.c:2842)

---

