---
title: "Not able to copy audio CD"
date: 2013-11-09
forum: Multimedia Software
---

### Post by johnaaronrose on 2013-11-09
Using Brasero to copy a CD, last part of session log is:
BraseroCdrdao got varg:
    cdrdao
    write
    --device
    /dev/sr0
    -n
    -v
    2
    --speed
    48
    /tmp/brasero_tmp_58FZ5W.toc
BraseroCdrdao Launching command
BraseroCdrdao called brasero_job_get_fd_in
BraseroCdrdao called brasero_job_get_fd_out
BraseroCdrdao stderr: WARNING: Environment variable 'HOME' not defined- cannot read .cdrdao.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Cdrdao version 1.2.3 - (C) Andreas Mueller <andreas@daneb.de>
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Cannot open toc file '/tmp/brasero_tmp_58FZ5W.toc' for reading: No such file or directory
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: HUP
BraseroCdrdao process finished with status 1
BraseroCdrdao called brasero_job_error
BraseroCdrdao finished with an error
BraseroCdrdao asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroCdrdao stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2859)

I've also tried using "cdrdao copy" etc on cli but it seems to finish after reading 40 tracks (out of 45 tracks) & does not create a .toc or ask for a cd to copy to on my single cd drive system. 

PS using Precise 64 bit.

---

