---
title: "Brasero Disc Burn error"
date: 2010-07-01
forum: Multimedia Software
---

### Post by billiusmaximus on 2010-07-01
I have never had a problem with Brasero, but for some reason I am now encountering an error once it attempts to burn the audio files to disc.

I should specify that it normalizes my tracks and converts the mp3's to audio files just fine, but the error occurs once the burn process begins.

I saved the log file and copied the last portion here:

BraseroWodim got varg:
	wodim
	-v
	dev=/dev/sr0
	speed=8
	-dao
	fs=16m
	-text
	cuefile=/tmp/brasero_tmp_B6H9EV.cue
BraseroWodim Launching command in /tmp
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsidev: '/dev/sr0'
BraseroW

Can anyone provide some insight on how this started and how I can resolve it? Much appreciated.

Thanks,
Billius

---

