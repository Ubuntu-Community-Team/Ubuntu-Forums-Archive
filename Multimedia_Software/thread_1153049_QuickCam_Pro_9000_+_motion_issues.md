---
title: "QuickCam Pro 9000 + motion issues"
date: 2009-05-08
forum: Multimedia Software
---

### Post by jjmatt on 2009-05-08
Hey all

So, I just got the webcam, it works fine independent of motion. (i.e. it works in skype and vlc). Motion is configured correctly (insofar as it records data), as the first time I run it, it captures video. However, whenever I kill it (either by ctrl+c or killall motion) I don't think it releases my webcam properly. I try to test it in skype and it fails, and the next time I try to run motion I get an error saying it cannot connect to my webcam (see error below). If I logout or reboot, motion/skype with my webcam work fine again, until I use motion once. Anyone have and ideas/suggestions on how to fix this?

The not working motion output:

```

[0] Processing thread 0 - config file /home/[USER]/.motion/motion.conf
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3410688 LIBAVFORMAT_BUILD 3414017
[0] Thread 1 is from /home/[USER]/.motion/motion.conf
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:0990)"
[1] cap.bus_info: "0000:00:1d.7"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Supported palettes:
[1] 0: MJPG (MJPEG)
[1] 1: YUYV (YUV 4:2:2 (YUYV))
[0] motion-httpd/3.2.11 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8000
[1] VIDIOC_TRY_FMT failed for format YUYV: Input/output error
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] Resizing pre_capture buffer to 2 items
[1] Retrying until successful connection with camera
```

The above repeats over and over until I kill motion. The below is the working output:

```
[0] Processing thread 0 - config file /home/[USER]/.motion/motion.conf
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3410688 LIBAVFORMAT_BUILD 3414017
[0] Thread 1 is from /home/[USER]/.motion/motion.conf
[0] motion-httpd/3.2.11 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8000
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:0990)"
[1] cap.bus_info: "0000:00:1d.7"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Supported palettes:
[1] 0: MJPG (MJPEG)
[1] 1: YUYV (YUV 4:2:2 (YUYV))
[1] index_format 6 Test palette YUYV (800x640)
[1] Adjusting resolution from 800x640 to 800x600.
[1] Using palette YUYV (800x600) bytesperlines 1600 sizeimage 960000 colorspace 00000008
[1] found control 0x00980900, "Brightness", range 0,255 
[1] 	"Brightness", default 128, current 128
[1] found control 0x00980901, "Contrast", range 0,255 
[1] 	"Contrast", default 32, current 32
[1] found control 0x00980902, "Saturation", range 0,255 
[1] 	"Saturation", default 32, current 32
[1] found control 0x00980913, "Gain", range 0,255 
[1] 	"Gain", default 0, current 234
[1] mmap information:
[1] frames=4
[1] 0 length=960000
[1] 1 length=960000
[1] 2 length=960000
[1] 3 length=960000
[1] Using V4L2
[1] Resizing pre_capture buffer to 1 items
[1] Resizing pre_capture buffer to 2 items
[1] File of type 8 saved to: /home/[LOCATION]/[LOCATION]/01-20090508102839.avi
^C[1] Thread exiting
[1] Calling vid_close() from motion_cleanup
[1] Closing video device /dev/video0
[0] httpd - Finishing
[0] httpd Closing
[0] httpd thread exit
[0] Motion terminating
```

My motion.config

```
# /etc/motion/motion.conf
#
# This config file was created by Andrew from InfectedProject


############################################################
# Daemon
############################################################

# Start in daemon (background) mode and release terminal (default: off)
daemon off

############################################################
# Basic Setup Mode
############################################################

# Start in Setup-Mode, daemon disabled. (default: off)
setup_mode off


###########################################################
# Capture device options
############################################################

# Videodevice to be used for capturing  (default /dev/video0)
# for FreeBSD default is /dev/bktr0
videodevice /dev/video0

# The video input to be used (default: 8)
# Should normally be set to 1 for video/TV cards, and 8 for USB cameras
input 8

# The video norm to use (only for video capture and TV tuner cards)
# Values: 0 (PAL), 1 (NTSC), 2 (SECAM), 3 (PAL NC no colour). Default: 0 (PAL)
norm 0

# The frequency to set the tuner to (kHz) (only for TV tuner cards) (default: 0)
frequency 0

# Rotate image this number of degrees. The rotation affects all saved images as
# well as mpeg movies. Valid values: 0 (default = no rotation), 90, 180 and 270.
rotate 0

# Image width (pixels). Valid range: Camera dependent, default: 352
width 800

# Image height (pixels). Valid range: Camera dependent, default: 288
height 640

# Maximum number of frames to be captured per second.
# Valid range: 2-100. Default: 100 (almost no limit).
framerate 2

# URL to use if you are using a network camera, size will be autodetected (incl http://)
# Must be a URL that returns single jpeg pictures or a raw mjpeg stream. Default: Not defined
; netcam_url value

# Username and password for network camera (only if required). Default: not defined
# Syntax is user:password
; netcam_userpass value

# URL to use for a netcam proxy server, if required, e.g. "http://myproxy".
# If a port number other than 80 is needed, use "http://myproxy:1234".
# Default: not defined
; netcam_proxy value

# Let motion regulate the brightness of a video device (default: off).
# The auto_brightness feature uses the brightness option as its target value.
# If brightness is zero auto_brightness will adjust to average brightness value 128.
# Only recommended for cameras without auto brightness
auto_brightness off

# Set the initial brightness of a video device.
# If auto_brightness is enabled, this value defines the average brightness level
# which Motion will try and adjust to.
# Valid range 0-255, default 0 = disabled
brightness 100

# Set the contrast of a video device.
# Valid range 0-255, default 0 = disabled
contrast 50

# Set the saturation of a video device.
# Valid range 0-255, default 0 = disabled
saturation 25

# Set the hue of a video device (NTSC feature).
# Valid range 0-255, default 0 = disabled
hue 0


############################################################
# Round Robin (multiple inputs on same video device name)
############################################################

# Number of frames to capture in each roundrobin step (default: 1)
roundrobin_frames 1

# Number of frames to skip before each roundrobin step (default: 1)
roundrobin_skip 1

# Try to filter out noise generated by roundrobin (default: 0)
switchfilter off


############################################################
# Motion Detection Settings:
############################################################

# Threshold for number of changed pixels in an image that
# triggers motion detection (default: 1500)
threshold 4000

# Automatically tune the threshold down if possible (default: off)
threshold_tune off

# Noise threshold for the motion detection (default: 32)
noise_level 64

# Automatically tune the noise threshold (default: on)
noise_tune on

# Enables motion to adjust its detection/noise level for very dark frames
# Don't use this with noise_tune on. (default: off)
#night_compensate off #(DEPREACATED)

# Despeckle motion image using (e)rode or (d)ilate or (l)abel (Default: not defined)
# Recommended value is EedDl. Any combination (and number of) of E, e, d, and D is valid.
# (l)abeling must only be used once and the 'l' must be the last letter.
# Comment out to disable
; despeckle value

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
minimum_motion_frames 2

# Specifies the number of pre-captured (buffered) pictures from before motion
# was detected that will be output at motion detection.
# Recommended range: 0 to 5 (default: 0)
# Do not use large values! Large values will cause Motion to skip video frames and
# cause unsmooth mpegs. To smooth mpegs use larger values of post_capture instead.
pre_capture 0

# Number of frames to capture after motion is no longer detected (default: 0)
post_capture 0

# Gap is the seconds of no motion detection that triggers the end of an event
# An event is defined as a series of motion images taken within a short timeframe.
# Recommended value is 60 seconds (Default). The value 0 is allowed and disables
# events causing all Motion to be written to one single mpeg file and no pre_capture.
gap 60

# Minimum gap in seconds between the storing pictures while detecting motion.
# Default: 0 = as fast as possible (given by the camera framerate)
# Note: This option has nothing to do with the option 'gap'
#minimum_gap 0 #(DEPRECATED)

# Maximum length in seconds of an mpeg movie
# When value is exceeded a new mpeg file is created. (Default: 0 = infinite)
max_mpeg_time 60

# Number of frames per second to capture when not detecting
# motion (saves CPU load) (Default: 0 = disabled)
#low_cpu 0 #(DEPRECATED)

# Always save images even if there was no motion (default: off)
output_all off


############################################################
# Image File Output
############################################################

# Output 'normal' pictures when motion is detected (default: on)
# Valid values: on, off, first, best
# When set to 'first', only the first picture of an event is saved.
# Picture with most motion of an event is saved when set to 'best'.
# Can be used as preview shot for the corresponding movie.
output_normal off

# Output pictures with only the pixels moving object (ghost images) (default: off)
output_motion off

# The quality (in percent) to be used by the jpeg compression (default: 75)
quality 80

# Output ppm images instead of jpeg (default: off)
ppm off


############################################################
# Film (mpeg) File Output - ffmpeg based
############################################################

# Use ffmpeg to encode mpeg movies in realtime (default: off)
ffmpeg_cap_new on

# Use ffmpeg to make movies with only the pixels moving
# object (ghost images) (default: off)
ffmpeg_cap_motion off

# Use ffmpeg to encode a timelapse movie
# Default value 0 = off - else save frame every Nth second
ffmpeg_timelapse 0

# The file rollover mode of the timelapse video
# Valid values: hourly, daily (default), weekly-sunday, weekly-monday, monthly, manual
ffmpeg_timelapse_mode daily

# Bitrate to be used by the ffmpeg encoder (default: 400000)
# This option is ignored if ffmpeg_variable_bitrate is not 0 (disabled)
ffmpeg_bps 400000

# Enables and defines variable bitrate for the ffmpeg encoder.
# ffmpeg_bps is ignored if variable bitrate is enabled.
# Valid values: 0 (default) = fixed bitrate defined by ffmpeg_bps,
# or the range 2 - 31 where 2 means best quality and 31 is worst.
ffmpeg_variable_bitrate 0

# Codec to used by ffmpeg for the video compression.
# Timelapse mpegs are always made in mpeg1 format independent from this option.
# Supported formats are: mpeg1 (ffmpeg-0.4.8 only), mpeg4 (default), and msmpeg4.
# mpeg1 - gives you files with extension .mpg
# mpeg4 or msmpeg4 - give you files with extension .avi
# msmpeg4 is recommended for use with Windows Media Player because
# it requires no installation of codec on the Windows client.
ffmpeg_video_codec mpeg4


############################################################
# Snapshots (Traditional Periodic Webcam File Output)
############################################################

# Make automated snapshot every N seconds (default: 0 = disabled)
snapshot_interval 0


############################################################
# Text Display
# %Y = year, %m = month, %d = date,
# %H = hour, %M = minute, %S = second, %T = HH:MM:SS,
# %v = event, %q = frame number, \n = new line,
# %D = changed pixels, %N = noise level,
# %i and %J = width and height of motion area,
# %K and %L = X and Y coordinates of motion center
# You can put quotation marks around the text to allow
# leading spaces
############################################################

# Locate and draw a box around the moving object.
# Valid values: on, off and preview (default: off)
# Set to 'preview' will only draw a box in preview_shot pictures.
locate off

# Draws the timestamp using same options as C function strftime(3)
# Default: %Y-%m-%d\n%T = date in ISO format and time in 24 hour clock
# Text is placed in lower right corner
text_right %Y-%m-%d\n%T

# Draw a user defined text on the images using same options as C function strftime(3)
# Default: Not defined = no text
# Text is placed in lower left corner
; text_left value

# Draw the number of changed pixed on the images (default: off)
# Will normally be set to off except when you setup and adjust the motion settings
# Text is placed in upper right corner
text_changes off

# Draw characters at twice normal size on images. (default: off)
text_double off


############################################################
# Target Directories and filenames For Images And Films
# For the options snapshot_, jpeg_, mpeg_ and timelapse_filename
# you can use conversion specifiers
# %Y = year, %m = month, %d = date,
# %H = hour, %M = minute, %S = second,
# %v = event, %q = frame number
# %D = changed pixels, %N = noise level,
# %i and %J = width and height of motion area,
# %K and %L = X and Y coordinates of motion center
# Quotation marks round string are allowed.
############################################################

# Target base directory for pictures and films
# Recommended to use absolute patch. (Default: current working directory)
target_dir /home/[LOCATION]/.security

# File path for snapshots (jpeg or ppm) relative to target_dir
# Default: %v-%Y%m%d%H%M%S-snapshot
# Default value is equivalent to legacy oldlayout option
# For Motion 3.0 compatible mode choose: %Y/%m/%d/%H/%M/%S-snapshot
# File extension .jpg or .ppm is automatically added so do not include this.
# Note: A symbolic link called lastsnap.jpg created in the target_dir will always
# point to the latest snapshot, unless snapshot_filename is exactly 'lastsnap'
snapshot_filename %v-%Y%m%d%H%M%S-snapshot

# File path for motion triggered images (jpeg or ppm) relative to target_dir
# Default: %v-%Y%m%d%H%M%S-%q
# Default value is equivalent to legacy oldlayout option
# For Motion 3.0 compatible mode choose: %Y/%m/%d/%H/%M/%S-%q
# File extension .jpg or .ppm is automatically added so do not include this
# Set to 'preview' together with best-preview feature enables special naming
# convention for preview shots. See motion guide for details
jpeg_filename %v-%Y%m%d%H%M%S-%q

# File path for motion triggered ffmpeg films (mpeg) relative to target_dir
# Default: %v-%Y%m%d%H%M%S
# Default value is equivalent to legacy oldlayout option
# For Motion 3.0 compatible mode choose: %Y/%m/%d/%H%M%S
# File extension .mpg or .avi is automatically added so do not include this
movie_filename %v-%Y%m%d%H%M%S

# File path for timelapse mpegs relative to target_dir
# Default: %Y%m%d-timelapse
# Default value is near equivalent to legacy oldlayout option
# For Motion 3.0 compatible mode choose: %Y/%m/%d-timelapse
# File extension .mpg is automatically added so do not include this
timelapse_filename %Y%m%d-timelapse


############################################################
# Live Webcam Server
############################################################

# The mini-http server listens to this port for requests (default: 0 = disabled)
webcam_port 0

# Quality of the jpeg images produced (default: 30)
webcam_quality 80

# Output frames at 1 fps when no motion is detected and increase to the
# rate given by webcam_maxrate when motion is detected (default: off)
webcam_motion off

# Maximum framerate for webcam streams (default: 1)
webcam_maxrate 2

# Restrict webcam connections to localhost only (default: on)
webcam_localhost off

# Limits the number of images per connection (default: 0 = unlimited)
# Number can be defined by multiplying actual webcam rate by desired number of seconds
# Actual webcam rate is the smallest of the numbers framerate and webcam_maxrate
webcam_limit 0


############################################################
# HTTP Based Control
############################################################

# TCP/IP port for the http server to listen on (default: 0 = disabled)
control_port 8000

# Restrict control connections to localhost only (default: on)
control_localhost off

# Output for http server, select off to choose raw text plain (default: on)
control_html_output on

# Authentication for the http based control. Syntax username:password
# Default: not defined (Disabled)
control_authentication [user]:[password]


############################################################
# Tracking (Pan/Tilt)
############################################################

# Type of tracker (0=none (default), 1=stepper, 2=iomojo, 3=pwc, 4=generic)
# The generic type enables the definition of motion center and motion size to
# be used with the convertion specifiers for options like on_motion_detected
track_type 0

# Serial port of motor (default: none)
; track_port value

# Motor number for x-axis (default: -1)
track_motorx 0

# Maximum value on x-axis (default: 0)
track_maxx 0

# ID of an iomojo camera if used (default: 0)
track_iomojo_id 0

# Speed to set the motor to (default: 255)
track_speed 255

# Number of steps to make (default: 40)
track_stepsize 40


############################################################
# External Commands, Warnings and Logging:
# You can use conversion specifiers for the on_xxxx commands
# %Y = year, %m = month, %d = date,
# %H = hour, %M = minute, %S = second,
# %v = event, %q = frame number
# %D = changed pixels, %N = noise level,
# %i and %J = width and height of motion area,
# %K and %L = X and Y coordinates of motion center
# Quotation marks round string are allowed.
############################################################

# Do not sound beeps when detecting motion (default: on)
# Note: Motion never beeps when running in daemon mode.
quiet on

# Command to be executed when an event starts. (default: none)
# An event starts at first motion detected after a period of no motion defined by gap 
; on_event_start value

# Command to be executed when an event ends after a period of no motion
# (default: none). The period of no motion is defined by option gap.
; on_event_end value

# Command to be executed when a picture (.ppm|.jpg) is saved (default: none)
# The filename of the picture is appended as an argument for the command.
;on_picture_save wput ftp://USERNAME:PASSWORD@REMOTE SERVER %f

# Command to be executed when a motion frame is detected (default: none)
; on_motion_detected value

# Command to be executed when a movie file (.mpg|.avi) is created. (default: none)
# Filename of movie is appended as an argument for the command.
; on_movie_start value

# Command to be executed when a movie file (.mpg|.avi) is closed. (default: none)
# Filename of movie is appended as an argument for the command.
; on_movie_end value


############################################################
# Common Options For MySQL and PostgreSQL database features.
# Options require the MySQL/PostgreSQL options to be active also.
############################################################

# Log to the database when creating motion triggered image file  (default: on)
sql_log_image on

# Log to the database when creating a snapshot image file (default: on)
sql_log_snapshot on

# Log to the database when creating motion triggered mpeg file (default: off)
sql_log_mpeg off

# Log to the database when creating timelapse mpeg file (default: off)
sql_log_timelapse off


############################################################
# Database Options For MySQL
############################################################

# Mysql database to log to (default: not defined)
; mysql_db value

# The host on which the database is located (default: not defined)
; mysql_host value

# User account name for MySQL database (default: not defined)
; mysql_user value

# User password for MySQL database (default: not defined)
; mysql_password value


############################################################
# Database Options For PostgreSQL
############################################################

# PostgreSQL database to log to (default: not defined)
; pgsql_db value

# The host on which the database is located (default: not defined)
; pgsql_host value

# User account name for PostgreSQL database (default: not defined)
; pgsql_user value

# User password for PostgreSQL database (default: not defined)
; pgsql_password value

# Port on which the PostgreSQL database is located (default: 5432)
pgsql_port 5432


############################################################
# Video Loopback Device (vloopback project)
############################################################

# Output images to a video4linux loopback device
# The value '-' means next available (default: not defined)
; video_pipe value

# Output motion images to a video4linux loopback device
# The value '-' means next available (default: not defined)
; motion_video_pipe value


##############################################################
# Thread config files - One for each camera.
# Except if only one camera - You only need this config file.
# If you have more than one camera you MUST define one thread
# config file for each camera in addition to this config file.
##############################################################

;thread /etc/motion/thread0.conf


```

---

### Post by jjmatt on 2009-05-11
Anyone?

---

### Post by SteveDee on 2009-06-08
> **jjmatt said:**
> Anyone?

I don't think "motion" likes your width & height values, as I can replicate your problem using your settings.

Try width 640, height 480.

---

