---
title: "&quot;motion&quot; program: snapshots in motion detection are generated with strips"
date: 2011-11-28
forum: Multimedia Software
---

### Post by Patagon on 2011-11-28
Hello,

I have a security system with the program "motion", a bt878 Card and 4 analogic cameras, all working fine. 

The problem is when I setup with motion detection, some snapshots of the cameras are stored with stripes (when the motion is fast):

Images:
[http://imageshack.us/photo/my-images/827/80015502.jpg/](http://imageshack.us/photo/my-images/827/80015502.jpg/)
[http://imageshack.us/photo/my-images/265/14957661.jpg/](http://imageshack.us/photo/my-images/265/14957661.jpg/)
[http://imageshack.us/photo/my-images/803/59231162.jpg/](http://imageshack.us/photo/my-images/803/59231162.jpg/)

This is the motion detection config: 


```
############################################################
# Motion Detection Settings:
############################################################

# Threshold for number of changed pixels in an image that
# triggers motion detection (default: 1500)
threshold 1500

# Automatically tune the threshold down if possible (default: off)
threshold_tune off

# Noise threshold for the motion detection (default: 32)
noise_level 32

# Automatically tune the noise threshold (default: on)
noise_tune on

# Despeckle motion image using (e)rode or (d)ilate or (l)abel (Default: not defined)
# Recommended value is EedDl. Any combination (and number of) of E, e, d, and D is valid.
# (l)abeling must only be used once and the 'l' must be the last letter.
# Comment out to disable
despeckle EedDl

# Detect motion in predefined areas (1 - 9). Areas are numbered like that:  1 2 3
# A script (on_area_detected) is started immediately when motion is         4 5 6
# detected in one of the given areas, but only once during an event.        7 8 9
# One or more areas can be specified with this option. (Default: not defined)
; area_detect value

# PGM file to use as a sensitivity mask.
# Full path name to. (Default: not defined)
; mask_file value

# Dynamically create a mask file during operation (default: 0)
# Adjust speed of mask changes from 0 (off) to 10 (fast)
smart_mask_speed 0

# Ignore sudden massive light intensity changes given as a percentage of the picture
# area that changed intensity. Valid range: 0 - 100 , default: 0 = disabled
lightswitch 0

# Picture frames must contain motion at least the specified number of frames
# in a row before they are detected as true motion. At the default of 1, all
# motion is detected. Valid range: 1 to thousands, recommended 1-5
minimum_motion_frames 1

# Specifies the number of pre-captured (buffered) pictures from before motion
# was detected that will be output at motion detection.
# Recommended range: 0 to 5 (default: 0)
# Do not use large values! Large values will cause Motion to skip video frames and
# cause unsmooth mpegs. To smooth mpegs use larger values of post_capture instead.
pre_capture 1

# Number of frames to capture after motion is no longer detected (default: 0)
post_capture 1

# Gap is the seconds of no motion detection that triggers the end of an event
# An event is defined as a series of motion images taken within a short timeframe.
# Recommended value is 60 seconds (Default). The value 0 is allowed and disables
# events causing all Motion to be written to one single mpeg file and no pre_capture.
gap 60

# Maximum length in seconds of an mpeg movie
# When value is exceeded a new mpeg file is created. (Default: 0 = infinite)
max_mpeg_time 0

# Always save images even if there was no motion (default: off)
output_all off
```



[IMG]http://imageshack.us/photo/my-images/827/80015502.jpg/[/IMG]

[IMG]http://imageshack.us/photo/my-images/265/14957661.jpg/[/IMG]

[IMG]http://imageshack.us/photo/my-images/803/59231162.jpg/[/IMG]



Any idea to solve this problem?


Thanks!

---

