---
title: "dual layer error message"
date: 2009-01-19
forum: Multimedia Software
---

### Post by f76 on 2009-01-19
Im having trouble burning .iso to DL disks with brasero on my acer aspire 5920g running 8.10 ibex
i got the following error message. Burning disks i working out fine in vista. Any idea what the error is, do i need to use another program/driver?

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_EWA7NU toc = nil
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
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
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=4
	-use-the-force-luke=tracksize:4148096
	-use-the-force-luke=tty
	-Z
	/dev/scd0=/home/tony/usenet/done/smokin aces/Smokin.aces.1080p.ps3avchd.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/tony/usenet/done/smokin aces/Smokin.aces.1080p.ps3avchd.iso of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd0: splitting layers at 2074048 blocks
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stdout:     9732096/8495300608 ( 0.1%) @1.8x, remaining 72:39 RBU 100.0% UBU   2.9%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    20905984/8495300608 ( 0.2%) @2.4x, remaining 60:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    32112640/8495300608 ( 0.4%) @2.4x, remaining 52:42 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    43319296/8495300608 ( 0.5%) @2.4x, remaining 48:46 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    54525952/8495300608 ( 0.6%) @2.4x, remaining 49:01 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    65699840/8495300608 ( 0.8%) @2.4x, remaining 47:02 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    76906496/8495300608 ( 0.9%) @2.4x, remaining 45:36 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    88113152/8495300608 ( 1.0%) @2.4x, remaining 46:06 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    99319808/8495300608 ( 1.2%) @2.4x, remaining 45:05 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   110526464/8495300608 ( 1.3%) @2.4x, remaining 44:15 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   121765888/8495300608 ( 1.4%) @2.4x, remaining 44:41 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   132972544/8495300608 ( 1.6%) @2.4x, remaining 44:01 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   144179200/8495300608 ( 1.7%) @2.4x, remaining 43:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   155385856/8495300608 ( 1.8%) @2.4x, remaining 43:49 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   166592512/8495300608 ( 2.0%) @2.4x, remaining 43:19 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   177831936/8495300608 ( 2.1%) @2.4x, remaining 42:52 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   189038592/8495300608 ( 2.2%) @2.4x, remaining 43:12 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   200245248/8495300608 ( 2.4%) @2.4x, remaining 42:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   211484672/8495300608 ( 2.5%) @2.4x, remaining 42:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   222691328/8495300608 ( 2.6%) @2.4x, remaining 42:43 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   233930752/8495300608 ( 2.8%) @2.4x, remaining 42:22 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   245137408/8495300608 ( 2.9%) @2.4x, remaining 42:04 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   256376832/8495300608 ( 3.0%) @2.4x, remaining 42:18 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   259588096/8495300608 ( 3.1%) @0.7x, remaining 43:21 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   266928128/8495300608 ( 3.1%) @1.6x, remaining 44:11 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   285605888/8495300608 ( 3.4%) @4.0x, remaining 42:38 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   304250880/8495300608 ( 3.6%) @4.0x, remaining 41:16 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   322928640/8495300608 ( 3.8%) @4.0x, remaining 40:29 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   341573632/8495300608 ( 4.0%) @4.0x, remaining 39:23 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   360251392/8495300608 ( 4.2%) @4.0x, remaining 38:23 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   378929152/8495300608 ( 4.5%) @4.0x, remaining 37:50 RBU 100.0% UBU  94.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   397606912/8495300608 ( 4.7%) @4.0x, remaining 36:59 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   416284672/8495300608 ( 4.9%) @4.0x, remaining 36:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   434962432/8495300608 ( 5.1%) @4.0x, remaining 35:49 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   453640192/8495300608 ( 5.3%) @4.0x, remaining 35:09 RBU 100.0% UBU  94.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   472317952/8495300608 ( 5.6%) @4.0x, remaining 34:32 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   490995712/8495300608 ( 5.8%) @4.0x, remaining 34:14 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   509673472/8495300608 ( 6.0%) @4.0x, remaining 33:41 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   528384000/8495300608 ( 6.2%) @4.0x, remaining 33:10 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   547061760/8495300608 ( 6.4%) @4.0x, remaining 32:55 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session

BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   565772288/8495300608 ( 6.7%) @4.0x, remaining 32:28 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   579502080/8495300608 ( 6.8%) @3.0x, remaining 32:19 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   598147072/8495300608 ( 7.0%) @4.0x, remaining 32:07 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   616824832/8495300608 ( 7.3%) @4.0x, remaining 31:43 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   635502592/8495300608 ( 7.5%) @4.0x, remaining 31:19 RBU  99.9% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   654147584/8495300608 ( 7.7%) @4.0x, remaining 31:09 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   672825344/8495300608 ( 7.9%) @4.0x, remaining 30:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   691503104/8495300608 ( 8.1%) @4.0x, remaining 30:28 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   710180864/8495300608 ( 8.4%) @4.0x, remaining 30:19 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   728858624/8495300608 ( 8.6%) @4.0x, remaining 30:00 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   747503616/8495300608 ( 8.8%) @4.0x, remaining 29:42 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   766214144/8495300608 ( 9.0%) @4.0x, remaining 29:35 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   784891904/8495300608 ( 9.2%) @4.0x, remaining 29:18 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   803569664/8495300608 ( 9.5%) @4.0x, remaining 29:02 RBU 100.0% UBU  94.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   822247424/8495300608 ( 9.7%) @4.0x, remaining 28:55 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   840925184/8495300608 ( 9.9%) @4.0x, remaining 28:40 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   859602944/8495300608 (10.1%) @4.0x, remaining 28:25 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   878313472/8495300608 (10.3%) @4.0x, remaining 28:19 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   892141568/8495300608 (10.5%) @3.0x, remaining 28:15 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   910819328/8495300608 (10.7%) @4.0x, remaining 28:02 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   929464320/8495300608 (10.9%) @4.0x, remaining 27:56 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   948142080/8495300608 (11.2%) @4.0x, remaining 27:43 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   966819840/8495300608 (11.4%) @4.0x, remaining 27:30 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   985464832/8495300608 (11.6%) @4.0x, remaining 27:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1004142592/8495300608 (11.8%) @4.0x, remaining 27:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1022820352/8495300608 (12.0%) @4.0x, remaining 27:01 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1041498112/8495300608 (12.3%) @4.0x, remaining 26:57 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1060208640/8495300608 (12.5%) @4.0x, remaining 26:45 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1078886400/8495300608 (12.7%) @4.0x, remaining 26:34 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1097531392/8495300608 (12.9%) @4.0x, remaining 26:30 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1116209152/8495300608 (13.1%) @4.0x, remaining 26:19 RBU 100.0% UBU  88.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1134886912/8495300608 (13.4%) @4.0x, remaining 26:09 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1153597440/8495300608 (13.6%) @4.0x, remaining 26:05 RBU 100.0% UBU  85.3%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1172275200/8495300608 (13.8%) @4.0x, remaining 25:55 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1190952960/8495300608 (14.0%) @4.0x, remaining 25:51 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1204879360/8495300608 (14.2%) @3.0x, remaining 25:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1223524352/8495300608 (14.4%) @4.0x, remaining 25:39 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1242202112/8495300608 (14.6%) @4.0x, remaining 25:35 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1260879872/8495300608 (14.8%) @4.0x, remaining 25:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1279557632/8495300608 (15.1%) @4.0x, remaining 25:16 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1298202624/8495300608 (15.3%) @4.0x, remaining 25:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1316880384/8495300608 (15.5%) @4.0x, remaining 25:04 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1335558144/8495300608 (15.7%) @4.0x, remaining 24:55 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1354235904/8495300608 (15.9%) @4.0x, remaining 24:52 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1372913664/8495300608 (16.2%) @4.0x, remaining 24:43 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1391591424/8495300608 (16.4%) @4.0x, remaining 24:35 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1410269184/8495300608 (16.6%) @4.0x, remaining 24:31 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1428979712/8495300608 (16.8%) @4.0x, remaining 24:23 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1447624704/8495300608 (17.0%) @4.0x, remaining 24:15 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1466302464/8495300608 (17.3%) @4.0x, remaining 24:12 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1485012992/8495300608 (17.5%) @4.0x, remaining 24:04 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1501626368/8495300608 (17.7%) @3.6x, remaining 23:59 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1517551616/8495300608 (17.9%) @3.4x, remaining 23:59 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1536196608/8495300608 (18.1%) @4.0x, remaining 23:51 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1554874368/8495300608 (18.3%) @4.0x, remaining 23:43 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1573552128/8495300608 (18.5%) @4.0x, remaining 23:40 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1592229888/8495300608 (18.7%) @4.0x, remaining 23:33 RBU 100.0% UBU  91.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1610874880/8495300608 (19.0%) @4.0x, remaining 23:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1629585408/8495300608 (19.2%) @4.0x, remaining 23:22 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1648230400/8495300608 (19.4%) @4.0x, remaining 23:15 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1666940928/8495300608 (19.6%) @4.0x, remaining 23:08 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1685618688/8495300608 (19.8%) @4.0x, remaining 23:05 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1704263680/8495300608 (20.1%) @4.0x, remaining 22:58 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1722941440/8495300608 (20.3%) @4.0x, remaining 22:51 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1741619200/8495300608 (20.5%) @4.0x, remaining 22:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1760296960/8495300608 (20.7%) @4.0x, remaining 22:42 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1778974720/8495300608 (20.9%) @4.0x, remaining 22:35 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1797652480/8495300608 (21.2%) @4.0x, remaining 22:32 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1812004864/8495300608 (21.3%) @3.1x, remaining 22:29 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1830256640/8495300608 (21.5%) @3.9x, remaining 22:23 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1848901632/8495300608 (21.8%) @4.0x, remaining 22:20 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1867579392/8495300608 (22.0%) @4.0x, remaining 22:14 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1886257152/8495300608 (22.2%) @4.0x, remaining 22:07 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1904934912/8495300608 (22.4%) @4.0x, remaining 22:05 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1923612672/8495300608 (22.6%) @4.0x, remaining 21:58 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1942257664/8495300608 (22.9%) @4.0x, remaining 21:52 RBU 100.0% UBU  91.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1960935424/8495300608 (23.1%) @4.0x, remaining 21:49 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1979645952/8495300608 (23.3%) @4.0x, remaining 21:43 RBU  99.9% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  1998323712/8495300608 (23.5%) @4.0x, remaining 21:37 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2016968704/8495300608 (23.7%) @4.0x, remaining 21:34 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2035679232/8495300608 (24.0%) @4.0x, remaining 21:28 RBU  99.9% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2054324224/8495300608 (24.2%) @4.0x, remaining 21:22 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2073001984/8495300608 (24.4%) @4.0x, remaining 21:19 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2091679744/8495300608 (24.6%) @4.0x, remaining 21:13 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2110357504/8495300608 (24.8%) @4.0x, remaining 21:10 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2124316672/8495300608 (25.0%) @3.0x, remaining 21:08 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2142994432/8495300608 (25.2%) @4.0x, remaining 21:02 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2161639424/8495300608 (25.4%) @4.0x, remaining 20:59 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2180317184/8495300608 (25.7%) @4.0x, remaining 20:54 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2198994944/8495300608 (25.9%) @4.0x, remaining 20:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2217672704/8495300608 (26.1%) @4.0x, remaining 20:45 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2236350464/8495300608 (26.3%) @4.0x, remaining 20:39 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2254995456/8495300608 (26.5%) @4.0x, remaining 20:34 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2273673216/8495300608 (26.8%) @4.0x, remaining 20:31 RBU 100.0% UBU  94.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2292350976/8495300608 (27.0%) @4.0x, remaining 20:25 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2311028736/8495300608 (27.2%) @4.0x, remaining 20:20 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2329706496/8495300608 (27.4%) @4.0x, remaining 20:17 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2348384256/8495300608 (27.6%) @4.0x, remaining 20:11 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2367062016/8495300608 (27.9%) @4.0x, remaining 20:06 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2385739776/8495300608 (28.1%) @4.0x, remaining 20:03 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2404417536/8495300608 (28.3%) @4.0x, remaining 19:58 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2423062528/8495300608 (28.5%) @4.0x, remaining 19:52 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2437021696/8495300608 (28.7%) @3.0x, remaining 19:53 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2455666688/8495300608 (28.9%) @4.0x, remaining 19:47 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2474344448/8495300608 (29.1%) @4.0x, remaining 19:42 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2493022208/8495300608 (29.3%) @4.0x, remaining 19:39 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2511699968/8495300608 (29.6%) @4.0x, remaining 19:34 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2530377728/8495300608 (29.8%) @4.0x, remaining 19:29 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2549022720/8495300608 (30.0%) @4.0x, remaining 19:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2567700480/8495300608 (30.2%) @4.0x, remaining 19:21 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2586378240/8495300608 (30.4%) @4.0x, remaining 19:16 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2605056000/8495300608 (30.7%) @4.0x, remaining 19:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2623733760/8495300608 (30.9%) @4.0x, remaining 19:08 RBU  99.8% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2642411520/8495300608 (31.1%) @4.0x, remaining 19:02 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2661089280/8495300608 (31.3%) @4.0x, remaining 19:00 RBU  99.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2679767040/8495300608 (31.5%) @4.0x, remaining 18:54 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2698444800/8495300608 (31.8%) @4.0x, remaining 18:49 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2717122560/8495300608 (32.0%) @4.0x, remaining 18:47 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2735800320/8495300608 (32.2%) @4.0x, remaining 18:42 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2749726720/8495300608 (32.4%) @3.0x, remaining 18:39 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2768404480/8495300608 (32.6%) @4.0x, remaining 18:37 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2787049472/8495300608 (32.8%) @4.0x, remaining 18:32 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2805727232/8495300608 (33.0%) @4.0x, remaining 18:27 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2824306688/8495300608 (33.2%) @4.0x, remaining 18:24 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2843049984/8495300608 (33.5%) @4.1x, remaining 18:19 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2861727744/8495300608 (33.7%) @4.0x, remaining 18:14 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2880405504/8495300608 (33.9%) @4.0x, remaining 18:11 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2899083264/8495300608 (34.1%) @4.0x, remaining 18:06 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2917761024/8495300608 (34.3%) @4.0x, remaining 18:01 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2936406016/8495300608 (34.6%) @4.0x, remaining 17:59 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2955083776/8495300608 (34.8%) @4.0x, remaining 17:54 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2973761536/8495300608 (35.0%) @4.0x, remaining 17:51 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  2992439296/8495300608 (35.2%) @4.0x, remaining 17:46 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3011117056/8495300608 (35.4%) @4.0x, remaining 17:41 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3029696512/8495300608 (35.7%) @4.0x, remaining 17:38 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3048439808/8495300608 (35.9%) @4.1x, remaining 17:34 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3061940224/8495300608 (36.0%) @2.9x, remaining 17:32 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3080617984/8495300608 (36.3%) @4.0x, remaining 17:29 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3099295744/8495300608 (36.5%) @4.0x, remaining 17:24 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3117940736/8495300608 (36.7%) @4.0x, remaining 17:19 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3136651264/8495300608 (36.9%) @4.0x, remaining 17:16 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3155296256/8495300608 (37.1%) @4.0x, remaining 17:12 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3173974016/8495300608 (37.4%) @4.0x, remaining 17:07 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3192619008/8495300608 (37.6%) @4.0x, remaining 17:04 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3211296768/8495300608 (37.8%) @4.0x, remaining 17:00 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3229974528/8495300608 (38.0%) @4.0x, remaining 16:55 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3248652288/8495300608 (38.2%) @4.0x, remaining 16:52 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3267297280/8495300608 (38.5%) @4.0x, remaining 16:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3285975040/8495300608 (38.7%) @4.0x, remaining 16:43 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3304652800/8495300608 (38.9%) @4.0x, remaining 16:40 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3323330560/8495300608 (39.1%) @4.0x, remaining 16:36 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3342008320/8495300608 (39.3%) @4.0x, remaining 16:31 RBU  99.9% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3360653312/8495300608 (39.6%) @4.0x, remaining 16:28 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3374448640/8495300608 (39.7%) @3.0x, remaining 16:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3393093632/8495300608 (39.9%) @4.0x, remaining 16:21 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3411804160/8495300608 (40.2%) @4.0x, remaining 16:18 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3430449152/8495300608 (40.4%) @4.0x, remaining 16:14 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3449126912/8495300608 (40.6%) @4.0x, remaining 16:09 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3467771904/8495300608 (40.8%) @4.0x, remaining 16:07 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3486449664/8495300608 (41.0%) @4.0x, remaining 16:02 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3505094656/8495300608 (41.3%) @4.0x, remaining 15:58 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3523772416/8495300608 (41.5%) @4.0x, remaining 15:55 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3542450176/8495300608 (41.7%) @4.0x, remaining 15:50 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3561127936/8495300608 (41.9%) @4.0x, remaining 15:46 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3579772928/8495300608 (42.1%) @4.0x, remaining 15:43 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3598450688/8495300608 (42.4%) @4.0x, remaining 15:38 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3617128448/8495300608 (42.6%) @4.0x, remaining 15:34 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3635806208/8495300608 (42.8%) @4.0x, remaining 15:31 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3654451200/8495300608 (43.0%) @4.0x, remaining 15:27 RBU 100.0% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3673128960/8495300608 (43.2%) @4.0x, remaining 15:22 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3674537984/8495300608 (43.3%) @0.3x, remaining 15:27 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3677683712/8495300608 (43.3%) @0.7x, remaining 15:30 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3696328704/8495300608 (43.5%) @4.0x, remaining 15:25 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3715006464/8495300608 (43.7%) @4.0x, remaining 15:22 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3733684224/8495300608 (43.9%) @4.0x, remaining 15:18 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3752329216/8495300608 (44.2%) @4.0x, remaining 15:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3771006976/8495300608 (44.4%) @4.0x, remaining 15:10 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3789684736/8495300608 (44.6%) @4.0x, remaining 15:06 RBU 100.0% UBU  94.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:  3808329728/8495300608 (44.8%) @4.0x, remaining 15:02 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: :-[ WRITE@LBA=1c7470h failed with SK=4h/ASC=44h/ACQ=90h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2524)

```

---

### Post by f76 on 2009-01-20
maybe the make of my dvd burner will help?


the site: [http://www.hardware.info/en-US/productdb/bGRkZpiUmJTK/viewproduct/Acer_Aspire_5920/#]("http://www.hardware.info/en-US/productdb/bGRkZpiUmJTK/viewproduct/Acer_Aspire_5920/#")
says it is Hitachi LG GSA-T20N  - is there any way to check?

this site says it has a driver for linux, how do i install this? [http://ar-domena.com.pl/gsa-t20n/](http://ar-domena.com.pl/gsa-t20n/)

---

### Post by mc4man on 2009-01-20
Here's the capabilities of your drive

[http://www.videohelp.com/dvdwriters/lg-gsa-t20n/2121](http://www.videohelp.com/dvdwriters/lg-gsa-t20n/2121)

I'm not sure what that 'driver' is, maybe firmware?

To ck. the firmware of the drive run 
```
sudo lshw -C disk 
```

Usually shows ver. xx

What you really need is a burning app that can do dual layer, maybe try k3b (I wouldn't know from experience, use Imgburn in wine

---

