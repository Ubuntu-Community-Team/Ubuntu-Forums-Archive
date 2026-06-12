---
title: "Help with built in web cam"
date: 2011-02-07
forum: Multimedia Software
---

### Post by saka on 2011-02-07
Hi guys 
some help plz with my built in web cam toshiba satellite L300 laptop ubuntu 10.10
it is not working
with Ekiga it says
Error while accessing video device CNF7051
Could not open the chosen channel. 

with chees is not working also

with camoram it says 
could not connect to (/dev/vedio) check the connection

this also might help
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: YUYV (MJPG is not supported by device)
libv4l2: error setting pixformat: Device or resource busy
Unable to set format: Device or resource busy
 Init v4L2 failed !! exit fatal

and also this 

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
libv4l2: error setting pixformat: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 640x480 [gstv4l2object.c(1951): gst_v4l2_object_set_format (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
Call to S_FMT failed for YUYV @ 640x480: Device or resource busy]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline2/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Invalid argument]
libv4l2: error setting pixformat: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 640x480 [gstv4l2object.c(1951): gst_v4l2_object_set_format (): /GstPipeline:pipeline3/GstV4l2Src:v4l2src2:
Call to S_FMT failed for YUYV @ 640x480: Device or resource busy]

thank you  :wink:

---

### Post by saka on 2011-02-07
come on guys any one

---

### Post by BicyclerBoy on 2011-02-07
From terminal

lsusb
dmesg | tail

and run 
gstreamer-properties
select video tab
select webcam device   "test"
select video4linux (1)  not (2)   & "test"

Any joy ??

You tried guvcview  ?

---

### Post by saka on 2011-02-07
Hi thanks for ur Re

unfortunately it is not yet here is what happend

lsusb output

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

 dmesg | tail 

[  159.567098] end_request: I/O error, dev sr0, sector 43016
[  159.706161] sr 0:0:0:0: [sr0] Unhandled sense code
[  159.706166] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  159.706171] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  159.706176] Info fld=0x2a03
[  159.706178] sr 0:0:0:0: [sr0] Add. Sense: CIRC unrecovered error
[  159.706184] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 2a 02 00 00 02 00
[  159.706196] end_request: I/O error, dev sr0, sector 43016
[  270.056138] Skipping EDID probe due to cached edid
[  280.144094] Skipping EDID probe due to cached edid
salah@salah-Satellite-L300:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Invalid argument]


I've also tried guvcview and guess what it is not  here is what happened


it says

[B]Guvcview error:

Unable to start with minimum setup

please reconnect the camera[/B]

it is built in :confused:

the terminal output

guvcview 1.4.1
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
/dev/video0 - device 1
Init. CNF7051 (location: usb-0000:00:1a.7-2)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
vid:04f2 
pid:b070 
driver:uvcvideo
checking format: 1196444237
Format unavailable: 1196444237.
Init v4L2 failed !! 
Init video returned -2
trying minimum setup ...
video device: /dev/video0 
/dev/video0 - device 1
Init. CNF7051 (location: usb-0000:00:1a.7-2)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
vid:04f2 
pid:b070 
driver:uvcvideo
checking format: 1448695129
libv4l2: error setting pixformat: Device or resource busy
VIDIOC_S_FORMAT - Unable to set format: Device or resource busy
Init v4L2 failed !! 
ERROR: Minimum Setup Failed.
 Exiting...
[B]
So enjoy with me[/B] :lolflag:




it says

---

### Post by BicyclerBoy on 2011-02-07
Looks bad like some regression bug..
This webcam has worked for some people..

Try some earlier or later kernel versions as an expt...(if you know how)
There is a ubuntu kernel ppa for the latest pre-release.

---

### Post by saka on 2011-02-08
i think so cuz this cam was working well with 8.10 but do you think it is a good idea to roll back to earlier karnel and is there an easy and smooth way to do it

---

### Post by no2498 on 2011-02-08
this does not look good to me

gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'


look in your package manager find and install wxcam

lets see what it loads

---

### Post by saka on 2011-02-08
actually i could not find wxcam in the package manager

---

### Post by gordintoronto on 2011-02-08
From issue 44 of Full Circle Magazine:
Download the latest gspca tarball from the gspca web site:
[http://moinejf.free.fr/](http://moinejf.free.fr/)
You might need to install build-essential using Synaptic.
Untar the file, then follow the readme instructions from the tarball:
Open a terminal, and cd to the directory where the make file is. Then:
make
sudo make install
Reboot to load the new modules. Run Cheese to confirm that it works.

You have to do the make and make install again every time there is a new kernel.

---

### Post by saka on 2011-02-08
I did that completely and still not working

---

### Post by no2498 on 2011-02-09
[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

they have it in a deb file also

---

### Post by saka on 2011-02-09
Breaking news ....
I installed mythbuntu 10.10 (witch is same karnel as my main os ) in vbox in the same machine and guess what it worked my webcam is working though it is not smooth but it works  with vlc and v4l1 so it is not the karnel nor the hardwar
so guys any ideas what it could be

---

