---
title: "more then 2 USB cameras not working"
date: 2009-10-08
forum: Multimedia Software
---

### Post by ELMIT on 2009-10-08
I noticed on my desktop (AMD Ubuntu 8.04, 3G RAM), that I can plug in 3 USB cameras and all are recognized, but only two at a time I can use. 

I get /dev/video0 1 and 2. I can use two out of them, but the third one will not work.

Currently I use motion with video1 and 2. When I start xawtv on video0, the picture remain black and the information I see:

>  xawtv 
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.24-24-generic)
xinerama 0: 1280x1024+1280+0
xinerama 1: 1280x1024+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x7fff8e43aad4 [PAL_G,PAL_I,PAL_D1,PAL_K,PAL_N,PAL_60,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_L,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
config: invalid value for norm: (null)
valid choices for "norm": 
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
ioctl: VIDIOC_STREAMON(int=1): No space left on device
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
ioctl: VIDIOC_STREAMON(int=1): No space left on device
v4l2: oops: select timeout


Where is the limitation?

bye

Ronald

---

### Post by ELMIT on 2009-10-10
anybody?
any hints or ideas?

bye

Ronald

---

### Post by ELMIT on 2009-10-10
I found a hint that I might have too many USB devices connected. I removed most of them now. However, it did not change. Below is the output of all three tries to start xawtv. Maybe that rings a bell, ... unfortunately not for me, ...

> ~$  xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.24-24-generic)
xinerama 0: 1280x1024+1280+0
xinerama 1: 1280x1024+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x7fff3fdef1e4 [PAL_G,PAL_D,PAL_D1,PAL_K,PAL_M,NTSC_M,NTSC_M_JP,?,?,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
config: invalid value for norm: (null)
valid choices for "norm": 
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument


~$  xawtv -c /dev/video1
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.24-24-generic)
xinerama 0: 1280x1024+1280+0
xinerama 1: 1280x1024+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x7fff9def72d4 [PAL_G,PAL_I,PAL_D1,PAL_K,PAL_N,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K1,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
config: invalid value for norm: (null)
valid choices for "norm": 
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument


~$  xawtv -c /dev/video2
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.24-24-generic)
xinerama 0: 1280x1024+1280+0
xinerama 1: 1280x1024+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x7fff63134514 [PAL_G,PAL_I,PAL_M,PAL_Nc,?,SECAM_B,SECAM_D,SECAM_K,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
config: invalid value for norm: (null)
valid choices for "norm": 
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  key
Warning: ... found while parsing '<Key>key: Command(setstation,"bookshelf")'
Warning: String to TranslationTable conversion encountered errors
ioctl: VIDIOC_STREAMON(int=1): No space left on device
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
ioctl: VIDIOC_STREAMON(int=1): No space left on device
v4l2: oops: select timeout




---

### Post by ELMIT on 2009-10-11
What does that mean:

> ioctl: VIDIOC_STREAMON(int=1): No space left on device


---

### Post by kampret on 2009-10-27
> **ELMIT said:**
> What does that mean:

try to put a USB PCI card ... should fix your problem ... and plug 1 camera on it and the other one on builtin port

---

