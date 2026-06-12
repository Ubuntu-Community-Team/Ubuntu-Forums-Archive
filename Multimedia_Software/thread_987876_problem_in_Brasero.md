---
title: "problem in Brasero"
date: 2008-11-20
forum: Multimedia Software
---

### Post by prince.buster on 2008-11-20
Trying to burn a data DVD with folders more than 6 deep, Brasero intelligently gives me this message:

> The children of this directory will have 6 parent directories. This is a violation of the ISO9660 standard which only allows 6.
Brasero can create an image of such a file hierarchy and burn it; but the media may not be readable on all operating systems.
NOTE: such a file hierarchy is known to work on linux.

Hey, that's fine - so I go ahead and add the files, then start the burn. Brasero then not-so-intelligently gives me this message:

> An unknown error occured. Check your disc.

I have a nagging feeling that my disc is just fine, thank-you-very-much. My log:

> Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_start_progress
BraseroChecksumFiles Called brasero_job_set_progress (0.031250)
BraseroChecksumFiles Called brasero_job_set_progress (0.062500)
BraseroChecksumFiles Called brasero_job_set_progress (0.093750)
BraseroChecksumFiles Called brasero_job_set_progress (0.125000)
BraseroChecksumFiles Called brasero_job_set_progress (0.156250)
BraseroChecksumFiles Called brasero_job_set_progress (0.187500)
BraseroChecksumFiles Called brasero_job_set_progress (0.218750)
BraseroChecksumFiles Called brasero_job_set_progress (0.250000)
BraseroChecksumFiles Called brasero_job_set_progress (0.281250)
BraseroChecksumFiles Called brasero_job_set_progress (0.312500)
BraseroChecksumFiles Called brasero_job_set_progress (0.343750)
BraseroChecksumFiles Called brasero_job_set_progress (0.375000)
BraseroChecksumFiles Called brasero_job_set_progress (0.406250)
BraseroChecksumFiles Called brasero_job_set_progress (0.437500)
BraseroChecksumFiles Called brasero_job_set_progress (0.468750)
BraseroChecksumFiles Called brasero_job_set_progress (0.500000)
BraseroChecksumFiles Called brasero_job_set_progress (0.531250)
BraseroChecksumFiles Called brasero_job_set_progress (0.562500)
BraseroChecksumFiles Called brasero_job_set_progress (0.593750)
BraseroChecksumFiles Called brasero_job_set_progress (0.625000)
BraseroChecksumFiles Called brasero_job_set_progress (0.656250)
BraseroChecksumFiles Called brasero_job_set_progress (0.687500)
BraseroChecksumFiles Called brasero_job_set_progress (0.718750)
BraseroChecksumFiles Called brasero_job_set_progress (0.750000)
BraseroChecksumFiles Called brasero_job_set_progress (0.781250)
BraseroChecksumFiles Called brasero_job_set_progress (0.812500)
BraseroChecksumFiles Called brasero_job_set_progress (0.843750)
BraseroChecksumFiles Called brasero_job_set_progress (0.875000)
BraseroChecksumFiles Called brasero_job_set_progress (0.906250)
BraseroChecksumFiles Called brasero_job_set_progress (0.937500)
BraseroChecksumFiles Called brasero_job_set_progress (0.968750)
BraseroChecksumFiles Called brasero_job_set_progress (1.000000)
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_8VX2KU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles finished track successfully
BraseroChecksumFiles stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
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
BraseroGrowisofs Using genisoimage
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
	-speed=3
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_YHN9KU
	-exclude-list
	/tmp/brasero_tmp_8CN9KU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: **Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_YHN9KU -exclude-list /tmp/brasero_tmp_8CN9KU -print-size** | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: **genisoimage: Directories too deep for '/home/XXX/XXX/XXX/XXX/XXX/XXX/XXX/XXX/XXX/XXX' (7) max is 6.**
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
Session error : unknown (brasero_burn_record burn.c:2527)


Seems to me they got this command wrong:

> genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_YHN9KU -exclude-list /tmp/brasero_tmp_8CN9KU -print-size

Particularly, the -D option should have been added. From the man page:

>        -D     Do not use deep directory relocation, and instead just pack them in the way we see them. If ISO9660:1999 has not been selected, this violates the ISO9660 standard, but it happens to work on many systems.  Use with cau&#8208;ion.

Is this registered as a bug? And can anyone suggest a quick way to get around it?

Cheers

---

### Post by prince.buster on 2008-11-21
filed a bug at [http://bugzilla.gnome.org/show_bug.cgi?id=561764](http://bugzilla.gnome.org/show_bug.cgi?id=561764)

---

### Post by danduq on 2009-03-27
I too am getting this problem. The solution appears to be to install Brasero 0.8.4 from the Gnome svn repository.

I'm having a problem compiling though. I run autoconf to create a configure file and get the following errors;
```
configure.in:31: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:32: error: possibly undefined macro: AM_CONFIG_HEADER
configure.in:34: error: possibly undefined macro: AM_MAINTAINER_MODE
configure.in:49: error: possibly undefined macro: AC_DISABLE_STATIC
configure.in:50: error: possibly undefined macro: AC_PROG_LIBTOOL
configure.in:99: error: possibly undefined macro: AM_CONDITIONAL
configure.in:228: error: possibly undefined macro: AM_GLIB_DEFINE_LOCALEDIR
configure.in:383: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
configure.in:404: error: possibly undefined macro: AM_GCONF_SOURCE_2
```

I have installed libgtk2.0-dev but this has not helped. Any ideas? I'm not so hot on compiling! :confused:

---

### Post by danduq on 2009-03-27
OK, well I never fixed my compile problem, but I found a workaround to burning discs with deep directories.

1. Create an ISO image of the directory you want to back up
```
genisoimage -r -J -D -o output_file.iso /directory
```
2. Use Brasero to burn the ISO image to disc. (can probably use wodim from command line, but didn't need to go that far)

I guess a lot of you already know this method, but I've spent most of my afternoon trying to get somewhere with this, so hopefully will help someone!

---

### Post by danduq on 2009-03-27
Doh, just found all this documented on [https://help.ubuntu.com/community/CdDvd/Burning](https://help.ubuntu.com/community/CdDvd/Burning)

Waste of an afternoon...  :lolflag:

---

