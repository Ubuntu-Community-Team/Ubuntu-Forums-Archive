---
title: "Brasero Seek Error"
date: 2011-12-14
forum: Multimedia Software
---

### Post by nmyrick on 2011-12-14
Can anyone help me with this error I am getting when trying to make an iso image with Brasero?

Instantly, when I try to make an iso image of DVDs, I get the attached error.  The DVD's play perfectly fine in VLC media player, so they are readable from my DVD drive, and are not scratched.  The issue is obviously with brasero or the plugins.

I am running Ubuntu 10.04 with Ubuntu Restricted Extras installed.

I have libdvdcss2 version 1.2.10-0.3medibuntu1 installed, which I think has been updated in the last few months.  Do I need a different version?

Here is the error log:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_output_size_for_current_track
BraseroDvdcss stopping
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_session_output_size
BraseroDvdcss output set (IMAGE) image = /media/1TB-NTFS/Images/brasero.iso toc = none
BraseroDvdcss called brasero_job_get_session_output_size
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_set_use_average_rate
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_error
BraseroDvdcss finished with an error
BraseroDvdcss asked to stop because of an error
    error        = 1
    message    = "Error reading video DVD (seek error)"
BraseroDvdcss stopping
Session error : Error reading video DVD (seek error) (brasero_burn_record brasero-burn.c:2839)

---

### Post by nmyrick on 2011-12-15
t

---

### Post by nmyrick on 2012-01-01
Just figured out the actual fix for this error in brasero.  This will also fix burning errors with brasero, because even before I was getting errors creating images, brasero was giving me an 'unknown error' when trying to burn ISO images to Dual Layer DVD's. 

Run the following commands in terminal:

sudo chmod 4711 /usr/bin/cdrdao
sudo chmod 4711 /usr/bin/wodim
sudo chmod 0755 /usr/bin/growisofs

These commands change CD/DVD drive access permissions for the plugins cdrdao, wodim, and growisofs.
 
Now brasero creates and burns images to and from all types of CD's and  DVD's, without issue.

---

