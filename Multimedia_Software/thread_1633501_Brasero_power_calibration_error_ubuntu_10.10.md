---
title: "Brasero power calibration error ubuntu 10.10"
date: 2010-11-29
forum: Multimedia Software
---

### Post by thomasmilo on 2010-11-29
I am unable to burn cd's using Brasero and consistently get the following error message when burning is about to start:
QUOTE
SCSI error on write(0,16): [3 73 03] Power calibration area error
END QUOTE

I completely deistalled Brasero using Synaptic and reinstalled it, but the error remains.  I have changed blank cd's multiple times to no avail.

Can anyone advise me?

Here is my error log file from Brasero:
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_PXYVMV.bin toc = none
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_G8IVMV.bin toc = none
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_A09UMV.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/tomsomers/Downloads/ubuntu-10.10-desktop-i386.iso (size = 726827008)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 59d15a16ce90c8ee97fa7c211b7673a8 ((null) before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_tracks
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 1
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn cd Profile= 09h , obs= 32768 , obs_pad= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn TAO pre-track 01 : get_nwa(0)=1, d=0 , demand=726827008 , cap=736958464

BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [3 73 03] Power calibration area error
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(0,16): [3 73 03] Power calibration area error
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 1
	message	= "SCSI error on write(0,16): [3 73 03] Power calibration area error"
BraseroLibburn stopping
Session error : SCSI error on write(0,16): [3 73 03] Power calibration area error (brasero_burn_record brasero-burn.c:2862)

END OF LOG

Thank You for any suggestions.

---

### Post by tonighx on 2010-12-09
I have discovered this issue trying to burn a DVD the first time since installing Ubuntu 10.10
Googling I found many forums that blame the hardware.
I'm convinced that my burner works fine, as it did with previous versions of Ubuntu
I'll post back after trying with an older Ubuntu live CD

EDIT:
I was unable toburn from any live CD but succeeded on another computer with ubuntu 10.10, so it is alt least hardware-related

---

### Post by Munschy_00 on 2012-08-03
sudo apt-get install libbrasero-media3-dev

brasero doesn't burn dvd's out of the box


fixed the issue for me.

ubuntu 12.04

---

### Post by overdrank on 2012-08-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

