---
title: "can't burn dvd &quot;unhandled error&quot;"
date: 2008-07-08
forum: Multimedia Software
---

### Post by Choad on 2008-07-08
Trying to clear off some space on my hard drive so i have bought a load of dvds (dvd+r single layer)

when i try and burn using either the built in nautilus burner or brasero (i assume they use the same burning backend) i get an "unhandled error"

```
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
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
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
	-use-the-force-luke=dao
	-dvd-compat
	-speed=8
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_Z58XDU
	-exclude-list
	/tmp/brasero_tmp_Z1DYDU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_Z58XDU -exclude-list /tmp/brasero_tmp_Z1DYDU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 1612775
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs finished successfully session
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
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=8
	-use-the-force-luke=tracksize:1612775
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_FTT4DU
	-exclude-list
	/tmp/brasero_tmp_RRT4DU
	-V
	Death Note 1 - 18
	-A
	Brasero-0.7.1
	-sysid
	LINUX
	-v
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.6 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_FTT4DU -exclude-list /tmp/brasero_tmp_RRT4DU -V Death Note 1 - 18 -A Brasero-0.7.1 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=0'
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
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    2
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 30
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 31
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 31
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 32
BraseroGrowisofs stderr:   0.31% done, estimate finish Tue Jul  8 14:36:26 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   0.62% done, estimate finish Tue Jul  8 14:39:07 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   0.93% done, estimate finish Tue Jul  8 14:38:13 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)

```

any ideas? running hardy btw

---

### Post by ROWDY!!! on 2008-07-15
Same problem:
```

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1810)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_NN86DU toc = (null)
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum output set (IMAGE) image = /tmp/brasero_tmp_2F96DU toc = (null)
BraseroMd5sum called brasero_job_get_session_output_size
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum called brasero_job_set_current_action
BraseroMd5sum called brasero_job_start_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum setting new checksum 65e96e29439578d5c0c11a85fce075e7 ((null) before)
BraseroMd5sum finished track successfully
BraseroMd5sum stopping
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
    -speed=1
    -use-the-force-luke=tracksize:292272
    -use-the-force-luke=tty
    -Z
    /dev/scd0=/home/james/Downloads/Disk_Images/xubuntu-8.04.1-alternate-i386.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/james/Downloads/Disk_Images/xubuntu-8.04.1-alternate-i386.iso of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=5h/ASC=27h/ACQ=00h]: Input/output error
BraseroGrowisofs stderr: /dev/scd0: reserving 292272 blocks, warning for short DAO recording
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 2.0x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=5h/ASC=27h/ACQ=00h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 1
    message    = "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)

```

---

### Post by ben2talk on 2008-09-01
Me too :(
BraseroGrowisofs stderr: 1153461 extents written (2252 MB)
BraseroGrowisofs stderr: :-[ WRITE@LBA=1199b0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error

I'm going to try it again with Nautilus - or should K9copy?

Bored now. Even Vista could manage this.

---

### Post by Choad on 2008-09-23
ok this is my laptop drive

[http://www1.uk.shopping.com/xPF-Sony-Sony-DWQ78A13-Slim-Slot-DL-DVDRW-8x8x4x-8x6x4x-Black-OEM](http://www1.uk.shopping.com/xPF-Sony-Sony-DWQ78A13-Slim-Slot-DL-DVDRW-8x8x4x-8x6x4x-Black-OEM)

it deffinitely handles dvd+r but i am still up the creek without a paddle. i really want this to work, i have bought 50 of these dvds!!!

---

### Post by markbuntu on 2008-09-23
I had that problem with memorex dvds and so did a lot of other people. Verbatim, Sony, TDK all seem to work OK though.

---

### Post by greymoose58 on 2008-11-25
Choad,

Did you ever solve this burning problem? I've got the same error and I'm using Sony DVD's (as per Markbuntu's comment).

Thanks.

---

### Post by Choad on 2008-11-27
nope, never. i think trying it on windows would be a good idea if you have a windows install. i think it's most likely a hardware incompatability between the cheap dvds and the burner.... so if windows can't burn them either then that would all but confirm it. if however windows can burn the same combination that linux can't then i have no idea :(

---

