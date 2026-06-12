---
title: "Mounting backend directory ?"
date: 2010-01-29
forum: Mythbuntu
---

### Post by Speedy2k on 2010-01-29
Is it normal then if i want to play primary backend video on the secondary backent pc, i need to mount the /var/lib/mythtv/videos folder of the backend to my frontend ?? I was thinking the video was streaming from the primary backend ?? am i missing something in the configuration or it is just the way it is ? thanx a lot!

---

### Post by ian dobson on 2010-01-29
Hi,

There's an option in mythfrontend to always stream from backend. Maybe you need to set this option, I think it's in playback somewhere.

Regards
Ian Dobson

---

### Post by 4dognight on 2010-01-29
I am using 9.10 and I do not need to mount the remote directory locally.
I do have the directories defined on the master backend(I think its a requirement)

---

### Post by Speedy2k on 2010-01-29
But why everytime i try to play a file that is on the primary backend, it always try to play it from the secondary backend, the backend where this frontend is running on ?

---

### Post by tgm4883 on 2010-01-29
What version of MythTV/Mythbuntu are you using?

---

### Post by Speedy2k on 2010-01-29
Mythbuntu 9.10 and i have applied all update, i i have reinstalled many time, right now i have enabled the Daily repo and everything is up to date!

---

### Post by Speedy2k on 2010-01-29
Ok a little update, i have managed to make it read the remote backend file, the sound is perfect, but i got a problem on the video, the screen is just gree and here is the error i got from the log file:

> 

2010-01-29 17:21:45.724 TV: Attempting to change from None to Watching Video
2010-01-29 17:21:46.035 TV: StartPlayer(0, Watching Video, main) -- begin
2010-01-29 17:21:47.160 AFD: Opened codec 0xae3fe960, id(MPEG4) type(Video)
2010-01-29 17:21:47.161 AFD: codec MP3 has 2 channels
2010-01-29 17:21:47.223 AFD: Opened codec 0xae3960b0, id(MP3) type(Audio)
2010-01-29 17:21:47.243 Opening audio device 'default'. ch 2(2) sr 48000
2010-01-29 17:21:47.243 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2010-01-29 17:21:47.305 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2010-01-29 17:21:47.495 VideoOutputXv: XVideo Adaptor Name: 'Intel Video Using Overlay'
2010-01-29 17:21:47.570 OSD Theme Dimensions W: 1280 H: 720
2010-01-29 17:21:48.434 TV: StartPlayer(0, Watching Video, main) -- end ok
2010-01-29 17:21:48.435 TV: Changing from None to Watching Video
2010-01-29 17:21:48.435 New DB connection, total: 3
2010-01-29 17:21:48.440 Connected to database 'mythconverg' at host: 10.1.0.117
2010-01-29 17:21:48.442 New DB connection, total: 4
2010-01-29 17:21:48.446 Connected to database 'mythconverg' at host: 10.1.0.117
2010-01-29 17:21:48.447 Video timing method: USleep with busy wait
2010-01-29 17:21:48.448 Realtime priority would require SUID as root.
2010-01-29 17:21:48.459 [mp3 @ 0x1a406c0]mdb:22, lastbuf:0 skipping granule 0
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    133 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x3800001
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    133 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x3800001
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    133 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x3800001



Does someone know what can cause this problem? thanx!

---

### Post by nickrout on 2010-01-29
problem is with your video card and/or the way it is setup.

What is your video card?

what does xvinfo tell you?

---

### Post by Speedy2k on 2010-01-29
This is a FitPC2 with this video card:Intel GMA500 graphics acceleration with this processor: Intel Atom Z530 1.6GHz

I have installed the driver as in the FitPC wiki, but this not seems to be working ? is there anything i can do for that ?
Here is the xvinfo log:

```

X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel Video Using Overlay"
    number of ports: 1
    port base: 56
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 6
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is -16711936)
      "XV_GAMMA" (range 0 to 65535)
              client settable attribute
              client gettable attribute (current value is 2105376)
      "XV_SATURATION" (range 0 to 65535)
              client settable attribute
              client gettable attribute (current value is 32768)
      "XV_BRIGHTNESS" (range 0 to 65535)
              client settable attribute
              client gettable attribute (current value is 32768)
      "XV_CONTRAST" (range 0 to 65535)
              client settable attribute
              client gettable attribute (current value is 32768)
      "XV_ALPHA" (range 0 to 65535)
              client settable attribute
              client gettable attribute (current value is 136208372)
    number of encodings: 3
      encoding ID #1: "XV_YUV_PACKED_IMAGE"
        size: 1920 x 1088
        rate: 1.000000
      encoding ID #2: "XV_YUV_PLANAR_IMAGE"
        size: 1920 x 1088
        rate: 1.000000
      encoding ID #3: "XV_RGB_IMAGE"
        size: 960 x 1080
        rate: 1.000000
    maximum XvImage size: 1920 x 1088
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)

```

---

