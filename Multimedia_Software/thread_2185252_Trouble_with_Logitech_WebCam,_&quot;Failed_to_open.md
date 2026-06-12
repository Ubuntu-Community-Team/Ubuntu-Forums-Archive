---
title: "Trouble with Logitech WebCam, &quot;Failed to open /dev/video0: No such file or directory&quot;"
date: 2013-11-01
forum: Multimedia Software
---

### Post by Keith_Beef on 2013-11-01
As in the thread title, I'm having trouble getting this to work in Ubuntu 12.04 LTS.

I know that this camera has worked in the past, I had a Skype conversation with a friend a little over two years ago on this hardware with a previous release of Ubuntu, but it's been packed away in a box for over a year, and the computer has had an Ubuntu upgrade since.

```
lsusb
…snip…
Bus 001 Device 007: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 008: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks
```

So it's identified.

```
guvcview 
guvcview 1.5.3
Could not open /home/me/.guvcviewrc for read,
 will try to create it
write /home/me/.guvcviewrc OK
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: No such file or directory
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.
```

There is no /dev/video0 device.

I remember having to create device files, years ago… do I really need to do that these days?

---

### Post by warp99 on 2013-11-02
Make the node and see what happens

```
sudo mknod /dev/video0 c 81 0
```

---

### Post by Keith_Beef on 2013-11-02
> **warp99 said:**
> Make the node and see what happens

```
sudo mknod /dev/video0 c 81 0
```

Thanks for that. I'd forgotten how to do it, and your reply was quicker than me looking back in notes. ;)

```
guvcview 
guvcview 1.5.3
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: Permission denied
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.
```

Better, but still not quite there.

```
sudo guvcview 
guvcview 1.5.3
Could not open /root/.guvcviewrc for read,
 will try to create it
write /root/.guvcviewrc OK
Home directory /home/me not ours.
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
Home directory /home/me not ours.
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Home directory /home/me not ours.
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused


ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: No such device or address
Init video returned -1
Home directory /home/me not ours.
Home directory /home/me not ours.
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.
```

```
sudo chmod a+rx /dev/video0
guvcview 
guvcview 1.5.3
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: Permission denied
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.
```

Even if I open the permissions completely (sudo chmod a+rwx /dev/video0) I get the same "unable to detect video devices on your system" message. Maybe a kernel module is not loaded?
```
lsmod | grep uvc
```
Nothing found… So where is the module?
```
locate uvc | grep `uname -r`
/lib/modules/3.2.0-52-generic/kernel/drivers/media/video/uvc
/usr/src/linux-headers-3.2.0-52-generic/include/linux/uvcvideo.h
```

So, try loading one of those, eh?
```
sudo modprobe uvc
FATAL: Module uvc not found.
sudo modprobe uvcvideo
FATAL: Module uvcvideo not found.

ls -al /lib/modules/3.2.0-52-generic/kernel/drivers/media/video/uvc
total 8
drwxr-xr-x  2 root root 4096 Oct 17 17:02 .
drwxr-xr-x 27 root root 4096 Oct 17 17:02 ..

```


Now this is puzzling… because on the [Linux UVC driver and tools page]("http://www.ideasonboard.org/uvc/"), I read the following.

> Linux 2.6.26 and newer includes the Linux UVC driver natively. You will not need to download the driver sources manually unless you want to test a newer version or help with development.

And I would have expected the presence of the required drivers to have already been verified when I installed cheese, guvcview and all the rest through Synaptic.

I'll poke around some more, maybe I need to compile and install the drivers myself; I already have some source code for V4L from when I was setting up a DVB-T receiver.

---

### Post by warp99 on 2013-11-02
What's the model of the webcam? Sometimes a "quirk" has to be enabled to get it to run correctly.

---

### Post by warp99 on 2013-11-02
Well the module is there, but not loading.

---

### Post by Keith_Beef on 2013-11-02
> **warp99 said:**
> What's the model of the webcam? Sometimes a "quirk" has to be enabled to get it to run correctly.
It's a Logitech QuickCam Pro.
```
lsusb | grep Logitech
Bus 001 Device 005: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks
Bus 001 Device 007: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 008: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
lsusb -d 046d:0991 -v | grep "14 Video"
Couldn't open device, some information will be missing
      bFunctionClass         14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
```


> **warp99 said:**
> Well the module is there, but not loading.

I can see that it's not being loaded, but why do you think it is present?

> **Keith_Beef said:**
> 
```
sudo modprobe uvc
FATAL: Module uvc not found.
sudo modprobe uvcvideo
FATAL: Module uvcvideo not found.

ls -al /lib/modules/3.2.0-52-generic/kernel/drivers/media/video/uvc
total 8
drwxr-xr-x  2 root root 4096 Oct 17 17:02 .
drwxr-xr-x 27 root root 4096 Oct 17 17:02 ..

```


The directory /lib/modules/3.2.0-52-generic/kernel/drivers/media/video/uvc is empty…

---

### Post by Keith_Beef on 2013-11-02
After a lot of thinking about this, I had a look in Syanptic at the files contained in the package linux-image-3.2.0-52-generic. Guess what I saw? That it contained the /lib/modules/3.2.0-52-generic/kernel/drivers/media/video/uvc/uvcvideo.ko driver file.

I reinstalled the package and I'm about the reboot the system.

---

### Post by warp99 on 2013-11-02
Did you try a different kernel or update the kernel? Looks like in precise-updates the most recent kernel is 3.8.0-32-generic and the module uvcvideo.ko is there:

[http://packages.ubuntu.com/precise-updates/amd64/linux-image-3.8.0-32-generic/filelist](http://packages.ubuntu.com/precise-updates/amd64/linux-image-3.8.0-32-generic/filelist)

---

### Post by Keith_Beef on 2013-11-02
> **warp99 said:**
> Did you try a different kernel or update the kernel? Looks like in precise-updates the most recent kernel is 3.8.0-32-generic and the module uvcvideo.ko is there:

[http://packages.ubuntu.com/precise-updates/amd64/linux-image-3.8.0-32-generic/filelist](http://packages.ubuntu.com/precise-updates/amd64/linux-image-3.8.0-32-generic/filelist)

I've not tried any other kernels, but I did build new modules to get ny DVB-T receiver to work, and maybe at some point I managed to wipe out the original V4L2 UVC drivers.

I reinstalled the kernel image, got back the uvcvideo driver and look what I see now.
```

lsusb -d 046d:0991 -v | grep "14 Video"
Couldn't open device, some information will be missing
      bFunctionClass         14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video

lsmod | grep uvc
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
```

```
guvcview 
guvcview 1.5.3
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
Init. UVC Camera (046d:0991) (location: usb-0000:00:1a.7-4.2)
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
vid:046d 
pid:0991 
driver:uvcvideo
Adding control for Pan (relative)
UVCIOC_CTRL_ADD - Error: Invalid argument
checking format: 1196444237
VIDIOC_G_COMP:: Invalid argument
   compression control not supported
fps is set to 1/25
drawing controls

Checking video mode 640x480@32bpp : OK 
```

And now I see myself. The camera is working.

---

### Post by warp99 on 2013-11-02
Glad you got it working. Don't forget to mark the thread solved.

---

### Post by Keith_Beef on 2013-11-02
> **warp99 said:**
> Glad you got it working. Don't forget to mark the thread solved.

It isn't entirely solved… I have an image but no sound.

Pulse Audio was not working correctly, hence all the messages like "ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused". It's probably not been working since I upgraded to 12.04, but I hadn't noticed that because Rhytmbox and a few other apps were still able to play through ALSA without Pulse.

I've got Pulse Audio running, now, but still no sound is being captured by the webcam microphone. If I remember correctly, though, when I had this webcam working a couple of years ago I used an external microphone.

---

