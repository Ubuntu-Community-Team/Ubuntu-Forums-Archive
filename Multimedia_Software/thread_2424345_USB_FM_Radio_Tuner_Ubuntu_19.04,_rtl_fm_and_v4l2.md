---
title: "USB FM Radio Tuner Ubuntu 19.04, rtl_fm and v4l2"
date: 2019-08-07
forum: Multimedia Software
---

### Post by andrewfer000 on 2019-08-07
So I purchased  a FM radio tuner from eBay. I learned  using the rtl_fm command I can make it work really well. BUT I would  love to have a GUI for accessibility purposes for family members. I  can't seem to pinpoint the issue and after working for days I've been  hoping the community has an answer. My radio device is mounted at  /dev/swradio0 which I have also created a symlink to /dev/radio0 but I  do not use that often. When it comes to errors Kradio4 gives me a  invalid freqency error and gnome-radio doesn't even start. GNU Radio is  cool but I am "Missing Modules" and I have no clue what to do and I hate  compiling from source. This is one of these things I want to "just  work" with my system because I am not an experenced radio tech. If  anyone knows anything please help me out or point me in the right  direction.  

Output of rtl_fm when I tune into a station ```
rtl_fm  -f 94.5e6 -s 200000 -r 48000 | aplay -r 48000 -f S16_LE
``` (This  works well but no quick tuning and using ctrl+c every time to change  stations sucks)

```

Found 1 device(s):
  0:  Realtek, RTL2838UHIDIR, SN: 00000001

Using device 0: Generic RTL2832U OEM
Detached kernel driver
Found Fitipower FC0012 tuner
Tuner gain set to automatic.
Tuned to 94800000 Hz.
Oversampling input by: 6x.
Oversampling output by: 1x.
Buffer size: 6.83ms
Sampling at 1200000 S/s.
Output at 200000 Hz.
Allocating 15 zero-copy buffers
Playing raw data 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
underrun!!! (at least 109.024 ms long)


```

Output of v4l2-compliance -d /dev/swradio0  

```

v4l2-compliance SHA: not available, 64 bits

Compliance test for device /dev/swradio0:

Driver Info:
    Driver name      : rtl2832_sdr
    Card type        : Realtek RTL2832 SDR
    Bus info         : usb-0000:06:00.4-1.4
    Driver version   : 5.2.2
    Capabilities     : 0x85310000
        SDR Capture
        Tuner
        Read/Write
        Streaming
        Extended Pix Format
        Device Capabilities
    Device Caps      : 0x05310000
        SDR Capture
        Tuner
        Read/Write
        Streaming
        Extended Pix Format

Required ioctls:
    test VIDIOC_QUERYCAP: OK

Allow for multiple opens:
    test second /dev/swradio0 open: OK
    test VIDIOC_QUERYCAP: OK
    test VIDIOC_G/S_PRIORITY: OK
    test for unlimited opens: OK

Debug ioctls:
    test VIDIOC_DBG_G/S_REGISTER: OK (Not Supported)
    test VIDIOC_LOG_STATUS: OK

Input ioctls:
    test VIDIOC_G/S_TUNER/ENUM_FREQ_BANDS: OK
    test VIDIOC_G/S_FREQUENCY: OK
    test VIDIOC_S_HW_FREQ_SEEK: OK (Not Supported)
    test VIDIOC_ENUMAUDIO: OK (Not Supported)
    test VIDIOC_G/S/ENUMINPUT: OK (Not Supported)
    test VIDIOC_G/S_AUDIO: OK (Not Supported)
    Inputs: 0 Audio Inputs: 0 Tuners: 2

Output ioctls:
    test VIDIOC_G/S_MODULATOR: OK (Not Supported)
    test VIDIOC_G/S_FREQUENCY: OK
    test VIDIOC_ENUMAUDOUT: OK (Not Supported)
    test VIDIOC_G/S/ENUMOUTPUT: OK (Not Supported)
    test VIDIOC_G/S_AUDOUT: OK (Not Supported)
    Outputs: 0 Audio Outputs: 0 Modulators: 0

Input/Output configuration ioctls:
    test VIDIOC_ENUM/G/S/QUERY_STD: OK (Not Supported)
    test VIDIOC_ENUM/G/S/QUERY_DV_TIMINGS: OK (Not Supported)
    test VIDIOC_DV_TIMINGS_CAP: OK (Not Supported)
    test VIDIOC_G/S_EDID: OK (Not Supported)

Control ioctls:
    test VIDIOC_QUERY_EXT_CTRL/QUERYMENU: OK
    test VIDIOC_QUERYCTRL: OK
    test VIDIOC_G/S_CTRL: OK
    test VIDIOC_G/S/TRY_EXT_CTRLS: OK
    test VIDIOC_(UN)SUBSCRIBE_EVENT/DQEVENT: OK
    test VIDIOC_G/S_JPEGCOMP: OK (Not Supported)
    Standard Controls: 3 Private Controls: 0

Format ioctls:
    test VIDIOC_ENUM_FMT/FRAMESIZES/FRAMEINTERVALS: OK
    test VIDIOC_G/S_PARM: OK (Not Supported)
    test VIDIOC_G_FBUF: OK (Not Supported)
    test VIDIOC_G_FMT: OK
    test VIDIOC_TRY_FMT: OK
    test VIDIOC_S_FMT: OK
    test VIDIOC_G_SLICED_VBI_CAP: OK (Not Supported)
    test Cropping: OK (Not Supported)
    test Composing: OK (Not Supported)
    test Scaling: OK (Not Supported)

Codec ioctls:
    test VIDIOC_(TRY_)ENCODER_CMD: OK (Not Supported)
    test VIDIOC_G_ENC_INDEX: OK (Not Supported)
    test VIDIOC_(TRY_)DECODER_CMD: OK (Not Supported)

Buffer ioctls:
        fail: v4l2-test-buffers.cpp(485): check_0(reqbufs.reserved, sizeof(reqbufs.reserved))
    test VIDIOC_REQBUFS/CREATE_BUFS/QUERYBUF: FAIL
    test VIDIOC_EXPBUF: OK (Not Supported)

Total: 43, Succeeded: 42, Failed: 1, Warnings: 0


```

btw, for the guy who keeps editing my posts for "please  use standard fonts." Please PM me and explain so i can stop making that  mastake (if i did)

---

