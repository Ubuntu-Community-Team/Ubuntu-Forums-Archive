---
title: "Brasero Burn Error"
date: 2009-05-20
forum: Multimedia Software
---

### Post by novio8 on 2009-05-20
Ubuntu 9.04 HP Compaq 6820s
When I tried to burn I got the following
Brasero error



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
BraseroBurnURI burn:// URI found burn:///NLP%2013%20The%20Milton%20Model.avi
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///NLP%2013%20The%20Milton%20Model.avi
BraseroBurnURI Added file /media/sda3/Pe&#269;icaZ/NLP Colorado/NLP 13 The Milton Model.avi at /NLP 13 The Milton Model.avi
BraseroBurnURI Information retrieval for burn:///NLP%207%20Information%20Gathering%202.avi
BraseroBurnURI Added file /media/sda3/Pe&#269;icaZ/NLP Colorado/NLP 7 Information Gathering 2.avi at /NLP 7 Information Gathering 2.avi
BraseroBurnURI Information retrieval for burn:///NlP%2009%20Setting%20Useful%20Outcome%202.avi
BraseroBurnURI Added file /media/sda3/Pe&#269;icaZ/NLP Colorado/NlP 09 Setting Useful Outcome 2.avi at /NlP 09 Setting Useful Outcome 2.avi
BraseroBurnURI Information retrieval for burn:///NLP%2010%20Milton%20Model.avi
BraseroBurnURI Added file /media/sda3/Pe&#269;icaZ/NLP Colorado/NLP 10 Milton Model.avi at /NLP 10 Milton Model.avi
BraseroBurnURI Information retrieval for burn:///NLP%208%20Setting%20Useful%20Outcome.avi
BraseroBurnURI Added file /media/sda3/Pe&#269;icaZ/NLP Colorado/NLP 8 Setting Useful Outcome.avi at /NLP 8 Setting Useful Outcome.avi
BraseroBurnURI Information retrieval for burn:///NLP%2011%20The%20Language%20of%20Influence.avi
BraseroBurnURI Added file /media/sda3/Pe&#269;icaZ/NLP Colorado/NLP 11 The Language of Influence.avi at /NLP 11 The Language of Influence.avi
BraseroBurnURI Information retrieval for burn:///NLP%2012%20The%20Milton%20Model.avi
BraseroBurnURI Added file /media/sda3/Pe&#269;icaZ/NLP Colorado/NLP 12 The Milton Model.avi at /NLP 12 The Milton Model.avi
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_2YMDUU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
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
	-speed=8
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
	/tmp/brasero_tmp_VPIJUU
	-exclude-list
	/tmp/brasero_tmp_LLIJUU
	-print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_VPIJUU -exclude-list /tmp/brasero_tmp_LLIJUU -print-size | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 2131079
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
	-speed=8
	-use-the-force-luke=tracksize:2131079
	-use-the-force-luke=tty
	-Z
	/dev/sr0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_AGV5TU
	-exclude-list
	/tmp/brasero_tmp_9BV5TU
	-V
	92005 Colorado 2
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-v
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.9 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_AGV5TU -exclude-list /tmp/brasero_tmp_9BV5TU -V 92005 Colorado 2 -A Brasero-2.26.1 -sysid LINUX -v | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
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
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 29
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 30
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 30
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 31
BraseroGrowisofs stderr:   0.23% done, estimate finish Wed May 20 11:05:35 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.47% done, estimate finish Wed May 20 11:09:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.70% done, estimate finish Wed May 20 11:07:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=220h failed with SK=3h/WRITE ERROR]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2602)

---

### Post by psyke83 on 2009-05-20
It would be better to file a bug on Launchpad against the "brasero" package.

---

### Post by jaime256 on 2009-05-21
I second this. I've been trying to burn an iso, and I thought it was my download that was bad. I kept getting similar errors and just got a bunch of coasters. So I installed windows xp on another machine to burn the iso and everything burned fine on the first try without a hicup. That's a week Ubuntu won't give me back, but that's okay. There is something wrong with the burning part right now. I have the exact same dvd burner on both machines so now I know that's fine.

---

### Post by johnjohn2 on 2009-05-21
In jaunty this is an issue for me also and i have filled a bug report already.

Regards John

---

### Post by javyn999 on 2009-05-27
I get this error as well.  Thing is though, sometimes my disks work.  Sometimes they don't.  Brasero worked fine the little I used it in Intrepid.

If it's any consolation K3B works great.

---

### Post by whitingjr on 2009-05-31
I have had the same problem. Tried upgrading from the current version of 0.7.1 installed on Hardy Heron.

 All versions of brasero after 0.7.1 do not compile during make. Tried installing from source nearly all versions upto and including the latest v2.27.2.

 My advice is to try installing the 0.7.1 which still compiles.

Regards,
Jeremy

---

### Post by drew2222 on 2009-06-09
I am using Ubuntu 9.04 and have tried to burn cd's using Brasero with similar errors reported. I have done two Ubuntu installs on seperate machines and Brasero gives different results.
PC with Asus A8NSLI mainboard and AMD 64 cpu. Ubuntu 9.04

A Plextor DVD writer connected via SATA returns burn errors.
An External HP DVD Writer connected via Firewire = Success

PC with MSI mainboard and AMD cpu.Ubuntu 9.04

LG DVD CD Combo connected via IDE would not recognize blank cd's
OEM DVD writer connected via IDE = Success
In both cases a change of hardware solved the issue.

---

### Post by alanwalterthomas on 2009-06-11
Brasero reports errors once it finishes burning on my Samsung SATA TSST Corp. SH-S223Q dvd drive since I upgraded to 9.04. It works find with an older LG IDE drive.

What's odd is the disks work, I can watch the video or read the files. I just get an error message at the end.

Erasing disks is also a problem.

If I tell Brasero to erase the disk, it does so & says the disk was successfully blanked. On top of that though it shows this message upon finishing.

Unable to mount media.
There is probably no media in the drive.

Strange, since the disk hasn't been ejected.


Anyway, here's the end of the error log after what was really a successful burn:


BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4692115456/4692121600 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-[ WRITE@LBA=22f580h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2602)

If more info would help, let me know.

---

### Post by jaime256 on 2009-12-12
I was just wondering if there's a fix for this. I'm again trying to burn an iso image again and I get this error from Brasero on Ubuntu 9.04. It's the first image. I have uninstalled it and was hoping to use GnomeBaker. Unfortunately the system doesn't pick it up automatically.

 I have also tried burning regular data, but it just makes coasters and the errors on the second image.

---

### Post by dbuster1 on 2009-12-24
having the same problem with brasero, is there another burner that works.

---

