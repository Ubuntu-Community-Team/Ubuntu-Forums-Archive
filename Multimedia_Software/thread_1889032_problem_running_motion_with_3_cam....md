---
title: "problem running motion with 3 cam..."
date: 2011-11-30
forum: Multimedia Software
---

### Post by Miouki on 2011-11-30
hello everyone 
i am on tango studio ( Ubuntu 10.04 (lucid), GNOME:2.30.2, kernel :2.6.32-35-lowlatency

i have some problem when i try torun 3 cam at the same time with motion:

```

~$ motion
[0] Processing thread 0 - config file /home/miouki/motion.conf
[0] Processing config file /usr/local/etc/thread1.conf
[0] Processing config file /usr/local/etc/thread2.conf
[0] Processing config file /usr/local/etc/thread3.conf
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
[0] Thread 1 is from /usr/local/etc/thread1.conf
[0] Thread 2 is from /usr/local/etc/thread2.conf
[1] Thread 1 started
[0] Thread 3 is from /usr/local/etc/thread3.conf
[1] cap.driver: "uvcvideo"
[1] cap.card: "Webcam C110"
[2] Thread 2 started
[1] cap.bus_info: "usb-0000:00:1d.7-2.2"
[1] cap.capabilities=0x04000001
[3] Thread 3 started
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Supported palettes:
[1] 0: YUYV (YUV 4:2:2 (YUYV))
[1] 1: MJPG (MJPEG)
[0] motion-httpd/3.2.11 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8080
[1] index_format 2 Test palette MJPG (320x288)
[1] Adjusting resolution from 320x288 to 352x288.
[1] Using palette MJPG (352x288) bytesperlines 0 sizeimage 304128 colorspace 00000008
[1] VIDIOC_G_JPEGCOMP not supported but it should be (does your webcam driver support this ioctl?)
[1] found control 0x00980900, "Brightness", range -64,64 
[1]     "Brightness", default 0, current 21
[1] found control 0x00980901, "Contrast", range 0,30 
[1]     "Contrast", default 13, current 13
[1] found control 0x00980902, "Saturation", range 0,127 
[1]     "Saturation", default 38, current 38
[1] found control 0x00980903, "Hue", range -16000,16000 
[1]     "Hue", default 0, current 0
[1] found control 0x00980910, "Gamma", range 20,250 
[1]     "Gamma", default 100, current 100
[1] mmap information:
[1] frames=4
[1] 0 length=304128
[1] 1 length=304128
[1] 2 length=304128
[1] 3 length=304128
[1] Using V4L2
[1] Resizing pre_capture buffer to 1 items
[2] cap.driver: "uvcvideo"
[2] cap.card: "Webcam C110"
[2] cap.bus_info: "usb-0000:00:1d.7-5.4"
[2] cap.capabilities=0x04000001
[2] - VIDEO_CAPTURE
[2] - STREAMING
[2] Supported palettes:
[2] 0: YUYV (YUV 4:2:2 (YUYV))
[2] 1: MJPG (MJPEG)
[2] index_format 2 Test palette MJPG (320x288)
[2] Adjusting resolution from 320x288 to 352x288.
[2] Using palette MJPG (352x288) bytesperlines 0 sizeimage 304128 colorspace 00000008
[2] VIDIOC_G_JPEGCOMP not supported but it should be (does your webcam driver support this ioctl?)
[2] found control 0x00980900, "Brightness", range -64,64 
[2]     "Brightness", default 0, current 0
[2] found control 0x00980901, "Contrast", range 0,30 
[2]     "Contrast", default 13, current 13
[2] found control 0x00980902, "Saturation", range 0,127 
[2]     "Saturation", default 38, current 38
[2] found control 0x00980903, "Hue", range -16000,16000 
[2]     "Hue", default 0, current 0
[2] found control 0x00980910, "Gamma", range 20,250 
[2]     "Gamma", default 100, current 100
[2] mmap information:
[2] frames=4
[2] 0 length=304128
[2] 1 length=304128
[2] 2 length=304128
[2] 3 length=304128
[2] Error starting stream VIDIOC_STREAMON: 
[2] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[2] V4L capturing using read is deprecated!
[2] Motion only supports mmap.
[2] Could not fetch initial image from camera
[2] Motion continues using width and height from config file(s)
[2] Resizing pre_capture buffer to 1 items
[3] Failed to open video device /dev/video2: 
[3] Could not fetch initial image from camera
[3] Motion continues using width and height from config file(s)
[3] Resizing pre_capture buffer to 1 items
[3] Started stream webcam server in port 8083
[2] Started stream webcam server in port 8082
[2] Resizing pre_capture buffer to 3 items
[3] Resizing pre_capture buffer to 3 items
[1] Started stream webcam server in port 8081
[1] Resizing pre_capture buffer to 3 items
[2] Retrying until successful connection with camera
[2] cap.driver: "uvcvideo"
[2] cap.card: "Webcam C110"
[2] cap.bus_info: "usb-0000:00:1d.7-5.4"
[2] cap.capabilities=0x04000001
[2] - VIDEO_CAPTURE
[2] - STREAMING
[2] Error selecting input 0 VIDIOC_S_INPUT: 
[2] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[2] V4L capturing using read is deprecated!
[2] Motion only supports mmap.
[3] Retrying until successful connection with camera
[3] Failed to open video device /dev/video2: 
[1] File of type 8 saved to: /home/miouki/Bureau/cam/cam1/01-20111130181236.swf
...
[1] File of type 1 saved to: /home/miouki/Bureau/cam/cam1/01-20111130181239-05.jpg
[2] Retrying until successful connection with camera
[2] cap.driver: "uvcvideo"
[2] cap.card: "Webcam C110"
[2] cap.bus_info: "usb-0000:00:1d.7-5.4"
[2] cap.capabilities=0x04000001
[2] - VIDEO_CAPTURE
[2] - STREAMING
[2] Error selecting input 0 VIDIOC_S_INPUT: 
[2] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[2] V4L capturing using read is deprecated!
[2] Motion only supports mmap.
[3] Retrying until successful connection with camera
[3] Failed to open video device /dev/video2: 
[1] File of type 1 saved to: /home/miouki/Bureau/cam/cam1/01-20111130181239-06.jpg
...
[1] File of type 1 saved to: /home/miouki/Bureau/cam/cam1/01-20111130181242-00.jpg
[2] Retrying until successful connection with camera
[2] cap.driver: "uvcvideo"
[3] Retrying until successful connection with camera
[2] cap.card: "Webcam C110"
[2] cap.bus_info: "usb-0000:00:1d.7-5.4"
[2] cap.capabilities=0x04000001
[2] - VIDEO_CAPTURE
[2] - STREAMING
[2] Error selecting input 0 VIDIOC_S_INPUT: 
[2] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[2] V4L capturing using read is deprecated!
[2] Motion only supports mmap.
[3] Failed to open video device /dev/video2: 
[3] Thread exiting
[2] Thread exiting
[1] Thread exiting
[1] Calling vid_close() from motion_cleanup
[1] Closing video device /dev/video0
[0] httpd - Finishing
[0] httpd Closing
[0] httpd thread exit
[0] Motion terminating
miouki@miouki-desktop:~$ 

```avec un -$sudo killall motion
voici mon montion.conf :
> **montion.conf]
# Rename this distribution example file to motion.conf
#
# This config file was generated by motion 3.2.11


############################################################
# Daemon
############################################################

# Start in daemon (background) mode and release terminal (default: off)
daemon off

# File to store the process ID, also called pid file. (default: not defined)
process_id_file /var/run/motion/motion.pid 

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

# v4l2_palette allows to choose preferable palette to be use by motion
# to capture from those supported by your videodevice. (default: 8)
# E.g. if your videodevice supports both V4L2_PIX_FMT_SBGGR8 and
# V4L2_PIX_FMT_MJPEG then motion will by default use V4L2_PIX_FMT_MJPEG.
# Setting v4l2_palette to 1 forces motion to use V4L2_PIX_FMT_SBGGR8
# instead.
#
# Values :
# V4L2_PIX_FMT_SN9C10X : 0  'S910'
# V4L2_PIX_FMT_SBGGR8  : 1  'BA81'
# V4L2_PIX_FMT_MJPEG   : 2  'MJPEG'
# V4L2_PIX_FMT_JPEG    : 3  'JPEG'
# V4L2_PIX_FMT_RGB24   : 4  'RGB3'
# V4L2_PIX_FMT_UYVY    : 5  'UYVY'
# V4L2_PIX_FMT_YUYV    : 6  'YUYV'
# V4L2_PIX_FMT_YUV422P : 7  '422P'
# V4L2_PIX_FMT_YUV420  : 8  'YU12'
v4l2_palette 8

# Tuner device to be used for capturing using tuner as source (default /dev/tuner0)
# This is ONLY used for FreeBSD. Leave it commented out for Linux
 said:**
> 


with


[quote=thread1.conf]
# /usr/local/etc/thread1.conf
#
# This config file was generated by motion 3.2.11 

process_id_file /var/run/motion/motion.pid 

###########################################################
# Capture device options
############################################################

# Videodevice to be used for capturing  (default /dev/video0)
# for FreeBSD default is /dev/bktr0
videodevice /dev/video0



# The video input to be used (default: 8)
# Should normally be set to 1 for video/TV cards, and 8 for USB cameras 
input 8

# Image width (pixels). Valid range: Camera dependent, default: 352
# width 352

# Image height (pixels). Valid range: Camera dependent, default: 288
# height 288

# Maximum number of frames to be captured per second.
# Valid range: 2-100. Default: 100 (almost no limit).
framerate 20

auto_brightness on

threshold 200

# Specifies the number of pre-captured (buffered) pictures from before motion
# was detected that will be output at motion detection.
# Recommended range: 0 to 5 (default: 0)
# Do not use large values! Large values will cause Motion to skip video frames and
# cause unsmooth mpegs. To smooth mpegs use larger values of post_capture instead.
pre_capture 2

# Draw a user defined text on the images using same options as C function strftime(3)
# Default: Not defined = no text
# Text is placed in lower left corner
text_left Miouki/1 C110/video0


############################################################
# Target Directories and filenames For Images And Films
# For the options snapshot_, jpeg_, mpeg_ and timelapse_filename
# you can use conversion specifiers
# %Y = year, %m = month, %d = date,
# %H = hour, %M = minute, %S = second,
# %v = event, %q = frame number, %t = thread (camera) number,
# %D = changed pixels, %N = noise level,
# %i and %J = width and height of motion area,
# %K and %L = X and Y coordinates of motion center
# %C = value defined by text_event
# Quotation marks round string are allowed.
############################################################

# Target base directory for pictures and films
# Recommended to use absolute path. (Default: current working directory)
target_dir /home/miouki/Bureau/cam/cam1

webcam_port 8081


and

[quote=thread2.conf]
# /usr/local/etc/thread2.conf
#
# This config file was generated by motion 3.2.11 

process_id_file /var/run/motion/motion.pid 

###########################################################
# Capture device options
############################################################

# Videodevice to be used for capturing  (default /dev/video0)
# for FreeBSD default is /dev/bktr0
videodevice /dev/video1


# The video input to be used (default: 8)
# Should normally be set to 1 for video/TV cards, and 8 for USB cameras 
input 8

# Image width (pixels). Valid range: Camera dependent, default: 352
# width 352

# Image height (pixels). Valid range: Camera dependent, default: 288
# height 288

# Maximum number of frames to be captured per second.
# Valid range: 2-100. Default: 100 (almost no limit).
framerate 20

auto_brightness on

threshold 200

# Specifies the number of pre-captured (buffered) pictures from before motion
# was detected that will be output at motion detection.
# Recommended range: 0 to 5 (default: 0)
# Do not use large values! Large values will cause Motion to skip video frames and
# cause unsmooth mpegs. To smooth mpegs use larger values of post_capture instead.
pre_capture 2

# Draw a user defined text on the images using same options as C function strftime(3)
# Default: Not defined = no text
# Text is placed in lower left corner
text_left Miouki/2 C110/video1


############################################################
# Target Directories and filenames For Images And Films
# For the options snapshot_, jpeg_, mpeg_ and timelapse_filename
# you can use conversion specifiers
# %Y = year, %m = month, %d = date,
# %H = hour, %M = minute, %S = second,
# %v = event, %q = frame number, %t = thread (camera) number,
# %D = changed pixels, %N = noise level,
# %i and %J = width and height of motion area,
# %K and %L = X and Y coordinates of motion center
# %C = value defined by text_event
# Quotation marks round string are allowed.
############################################################

# Target base directory for pictures and films
# Recommended to use absolute path. (Default: current working directory)
target_dir /home/miouki/Bureau/cam/cam2

webcam_port 8082
[/quote]

and 

[quote=thread3.conf]
# /usr/local/etc/thread3.conf
#
# This config file was generated by motion 3.2.11 

process_id_file /var/run/motion/motion.pid 

###########################################################
# Capture device options
############################################################

# Videodevice to be used for capturing  (default /dev/video0)
# for FreeBSD default is /dev/bktr0
videodevice /dev/video2



# The video input to be used (default: 8)
# Should normally be set to 1 for video/TV cards, and 8 for USB cameras 
input 8

# Image width (pixels). Valid range: Camera dependent, default: 352
# width 352

# Image height (pixels). Valid range: Camera dependent, default: 288
# height 288

# Maximum number of frames to be captured per second.
# Valid range: 2-100. Default: 100 (almost no limit).
framerate 20

auto_brightness on

threshold 200

# Specifies the number of pre-captured (buffered) pictures from before motion
# was detected that will be output at motion detection.
# Recommended range: 0 to 5 (default: 0)
# Do not use large values! Large values will cause Motion to skip video frames and
# cause unsmooth mpegs. To smooth mpegs use larger values of post_capture instead.
pre_capture 2

# Draw a user defined text on the images using same options as C function strftime(3)
# Default: Not defined = no text
# Text is placed in lower left corner
text_left Miouki/3 C110/video2


############################################################
# Target Directories and filenames For Images And Films
# For the options snapshot_, jpeg_, mpeg_ and timelapse_filename
# you can use conversion specifiers
# %Y = year, %m = month, %d = date,
# %H = hour, %M = minute, %S = second,
# %v = event, %q = frame number, %t = thread (camera) number,
# %D = changed pixels, %N = noise level,
# %i and %J = width and height of motion area,
# %K and %L = X and Y coordinates of motion center
# %C = value defined by text_event
# Quotation marks round string are allowed.
############################################################

# Target base directory for pictures and films
# Recommended to use absolute path. (Default: current working directory)
target_dir /home/miouki/Bureau/cam/cam3

webcam_port 8083
[/quote]


the 3 webcams are well conected with usb ,  gstreamer-properties cans see them:
UVC camera (046d:0817) : v4l2src device="/dev/video2"
Webcam C110 : v4l2src device="/dev/video0"
Webcam C110 : v4l2src device="/dev/video1"
they each work one at a time , and two by two i think, but it is impossible to makethem work together...
```

-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
libv4l2: error turning on stream: Aucun espace disponible sur le périphérique
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1952): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: Aucun espace disponible sur le périphérique]

```Does anyone would have a solution for this problem?
an other seing-angle?
thanks a lot !

miouki

---

### Post by Cool Javelin on 2011-12-27
Are you sure the data rate through the USB port is fast enough to do the job?

As I understand USB, there may be 2 or more ports in the machine, but they may go through one hub and the transfer rate for that hub may be too slow.

Do you have some ports in back of the machine and some in the front, they may be on different hubs.

Also, There are external USB splitters (plug into one USB port on the computer, then attach many USB devices.) Stay away from these using multiple video cameras.

The uncompressed data rate for video can be pretty fast and you may simply be overloading the IO.

However, I may be way off in this area too.

Good luck, Mark.

---

### Post by arfiansyah on 2012-07-05
this is my thread1.conf configuration
```
netcam_url http://192.168.0.99/video.cgi

```

```
netcam_url http://192.168.0.99/video.jpg
 
```
i take the netcam_url from motion webhome, thats the url for dlink ip cameras..
but i still didnt see a picture or a video..

---

### Post by arfiansyah on 2012-07-06
a video from my netcam already showed in 
```

localhost:8081

```

how to access that link from other PC??
i didnt see anything in my windows webbrowser...
i'm using VM Ware...

---

