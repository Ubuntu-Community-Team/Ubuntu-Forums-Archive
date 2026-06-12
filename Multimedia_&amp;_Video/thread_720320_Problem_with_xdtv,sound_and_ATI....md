---
title: "Problem with xdtv,sound and ATI..."
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by Allexandar on 2008-03-10
Hi to all members of this great forum :)

I'm new in linux world and i have few problems...
(I'm sorry in advance if i'm braking any posting rule,i've read them but... who knows)

I have problem with xdtv and this is my terminal  output on "xdtv":

```
allexandart@allexandar-desktop:~$ xdtv

This is xdtv 2.4.0 running on Linux/i686 (2.6.22-14-generic).
scandir: No such file or directory
filename = /home/allexandart/.xdtv/xdtvrc
WARNING: No DGA support available for this display.
/dev/video0 [v4l2]: no overlay support
xdtv_v4l-conf had some trouble, trying to continue anyway
xinerama 0: 1024x768+0+0
Warning: Missing charsets in String to FontSet conversion
wmhooks: netwm detected
wmhooks: netwm state above supported
wmhooks: netwm fullscreen supported
wmhooks: nothing found...
VidMode: server=2.2, include=2.2
  available video mode(s): 1280x1024 1280x1024 1280x1024 1152x864 1152x864 1152x864 1152x864 1152x864 1024x768 1024x768 1024x768 1024x768 1024x768 800x600 800x600 800x600 800x600 800x600 800x600 800x600 800x600 640x480 640x480 640x480 640x480 640x480 640x480 640x480 1280x960 1280x768 1280x720 960x720 864x648 720x576 640x400 640x400 400x300 400x300 320x240 320x240 320x200 320x200
Selected XvImage adaptor with yuyv support: ATI Radeon Video Overlay on port 59 (grabdisplay)
No XvVideo port available.
Warning: Cannot convert string "none" to type relief
ioctl VIDIOC_G_FBUF: Invalid argument
classical overlay is disabled*** GRABBER DEVICE TYPE = v4l2
Warning: Missing charsets in String to FontSet conversion
MMX, SSE, AMD MMX extensions, SSE2, 3DNOW, have been detected.
Method mmxext_64K
*** AUDIO DEVICE TYPE = alsa
*** MIXER DEVICE TYPE = alsa
ioctl VIDIOC_STREAMON: Invalid argument
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
ioctl VIDIOC_REQBUFS: Device or resource busy
channel=SE4 freq=126.250 tvname=unknown (SE4)        
channel=SE5 freq=133.250 tvname=unknown (SE5)        
channel=SE6 freq=140.250 tvname=unknown (SE6)        
channel=SE7 freq=147.250 tvname=unknown (SE7)        
channel=SE8 freq=154.250 tvname=CNN International        
channel=SE10 freq=168.250 tvname=unknown (SE10)        
channel=E5 freq=175.250 tvname=unknown (E5)        
channel=E7 freq=189.250 tvname=unknown (E7)        
channel=E8 freq=196.250 tvname=unknown (E8)        
channel=E9 freq=203.250 tvname=unknown (E9)        
channel=E10 freq=210.250 tvname=unknown (E10)        
channel=E11 freq=217.250 tvname=unknown (E11)        
channel=E12 freq=224.250 tvname=unknown (E12)        
channel=SE11 freq=231.250 tvname=unknown (SE11)        
channel=SE12 freq=238.250 tvname=unknown (SE12)        
channel=SE13 freq=245.250 tvname=unknown (SE13)        
channel=SE14 freq=252.250 tvname=unknown (SE14)        
channel=SE15 freq=259.250 tvname=unknown (SE15)        
channel=SE16 freq=266.250 tvname=unknown (SE16)        
channel=SE17 freq=273.250 tvname=unknown (SE17)        
channel=SE18 freq=280.250 tvname=unknown (SE18)        
channel=SE19 freq=287.250 tvname=RAI 2        
channel=SE20 freq=294.250 tvname=unknown (SE20)        
channel=S21 freq=303.250 tvname=unknown (S21)        
channel=S22 freq=311.250 tvname=unknown (S22)        
channel=S23 freq=319.250 tvname=unknown (S23)        
channel=S24 freq=327.250 tvname=Eurosport        
channel=S25 freq=335.250 tvname=unknown (S25)        
channel=S26 freq=343.250 tvname=unknown (S26)        
channel=S27 freq=351.250 tvname=unknown (S27)        
channel=S28 freq=359.250 tvname=unknown (S28)        
channel=S29 freq=367.250 tvname=unknown (S29)        
channel=S30 freq=375.250 tvname=unknown (S30)        
channel=S31 freq=383.250 tvname=unknown (S31)        
channel=S32 freq=391.250 tvname=unknown (S32)        
channel=S33 freq=399.250 tvname=unknown (S33)        
channel=S34 freq=407.250 tvname=TV5        
channel=S35 freq=415.250 tvname=unknown (S35)        
channel=S36 freq=423.250 tvname=unknown (S36)        
channel=S37 freq=431.250 tvname=unknown (S37)        
channel=S40 freq=455.250 tvname=unknown (S40)        
channel=S41 freq=463.250 tvname=unknown (S41)        
channel=21 freq=471.250 tvname=unknown (21)        
channel=22 freq=479.250 tvname=unknown (22)        
channel=23 freq=487.250 tvname=unknown (23)        
channel=24 freq=495.250 tvname=unknown (24)        
channel=25 freq=503.250 tvname=unknown (25)        
channel=26 freq=511.250 tvname=unknown (26)        
channel=29 freq=535.250 tvname=unknown (29)        
channel=30 freq=543.250 tvname=unknown (30)        
channel=31 freq=551.250 tvname=unknown (31)        
channel=32 freq=559.250 tvname=unknown (32)        
channel=33 freq=567.250 tvname=unknown (33)        
channel=34 freq=575.250 tvname=unknown (34)        
channel=35 freq=583.250 tvname=RAI 1        
channel=36 freq=591.250 tvname=unknown (36)        
channel=38 freq=607.250 tvname=HRT        
channel=39 freq=615.250 tvname=Eurosport        
channel=40 freq=623.250 tvname=unknown (40)        
channel=41 freq=631.250 tvname=unknown (41)        
channel=42 freq=639.250 tvname=National Geographic Channel        
channel=43 freq=647.250 tvname=unknown (43)        
channel=44 freq=655.250 tvname=unknown (44)        
channel=53 freq=727.250 tvname=unknown (53)        
channel=57 freq=759.250 tvname=unknown (57)        
channel=60 freq=783.250 tvname=unknown (60)        
channel=61 freq=791.250 tvname=BBC World        
channel=62 freq=799.250 tvname=unknown (62)        
channel=63 freq=807.250 tvname=TVE Internacional Europa        
channel=65 freq=823.250 tvname=unknown (65)        
channel=67 freq=839.250 tvname=unknown (67)        
channel=69 freq=855.250 tvname=unknown (69)        
*** glibc detected *** xdtv: double free or corruption (out): 0x08654b78 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb738fd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7393800]
/usr/lib/libzvbi.so.0[0xb77a6ef4]
/usr/lib/libzvbi.so.0[0xb77aaa8d]
/usr/lib/libzvbi.so.0(vbi_capture_delete+0x13)[0xb77a1633]
xdtv(scan_v4l+0x43f)[0x80cb75f]
======= Memory map: ========
08048000-083d5000 r-xp 00000000 03:06 295899     /usr/bin/xdtv
083d5000-083fa000 rw-p 0038d000 03:06 295899     /usr/bin/xdtv
083fa000-08f52000 rw-p 083fa000 00:00 0          [heap]
4a400000-4a421000 rw-p 4a400000 00:00 0 
4a421000-4a500000 ---p 4a421000 00:00 0 
4a53d000-4a53e000 ---p 4a53d000 00:00 0 
4a53e000-4ad3e000 rwxp 4a53e000 00:00 0 
4ad3e000-4ad3f000 ---p 4ad3e000 00:00 0 
4ad3f000-4b53f000 rwxp 4ad3f000 00:00 0 
4b53f000-4b540000 ---p 4b53f000 00:00 0 
4b540000-4bd40000 rwxp 4b540000 00:00 0 
4bd40000-4bd41000 ---p 4bd40000 00:00 0 
4bd41000-4c541000 rwxp 4bd41000 00:00 0 
4c541000-4c542000 ---p 4c541000 00:00 0 
4c542000-4cd42000 rwxp 4c542000 00:00 0 
4cd42000-4cd43000 ---p 4cd42000 00:00 0 
4cd43000-4d543000 rwxp 4cd43000 00:00 0 
4d543000-4d544000 ---p 4d543000 00:00 0 
4d544000-4dd44000 rwxp 4d544000 00:00 0 
4dd44000-4dd45000 ---p 4dd44000 00:00 0 
4dd45000-4e545000 rwxp 4dd45000 00:00 0 
4e545000-4e546000 ---p 4e545000 00:00 0 
4e546000-4ed46000 rwxp 4e546000 00:00 0 
4ed46000-4ed47000 ---p 4ed46000 00:00 0 
4ed47000-4f547000 rwxp 4ed47000 00:00 0 
4f547000-4f548000 ---p 4f547000 00:00 0 
4f548000-4fd48000 rwxp 4f548000 00:00 0 
4fd48000-4fd49000 ---p 4fd48000 00:00 0 
4fd49000-50549000 rwxp 4fd49000 00:00 0 
50549000-5054a000 ---p 50549000 00:00 0 
5054a000-50d4a000 rwxp 5054a000 00:00 0 
50d4a000-50d4b000 ---p 50d4a000 00:00 0 
50d4b000-5154b000 rwxp 50d4b000 00:00 0 
5154b000-5154c000 ---p 5154b000 00:00 0 
5154c000-51d4c000 rwxp 5154c000 00:00 0 
51d4c000-51d4d000 ---p 51d4c000 00:00 0 
51d4d000-5254d000 rwxp 51d4d000 00:00 0 
5254d000-5254e000 ---p 5254d000 00:00 0 
5254e000-52d4e000 rwxp 5254e000 00:00 0 
52d4e000-52d4f000 ---p 52d4e000 00:00 0 
52d4f000-5354f000 rwxp 52d4f000 00:00 0 
5354f000-53550000 ---p 5354f000 00:00 0 
53550000-53d50000 rwxp 53550000 00:00 0 
53d50000-53d51000 ---p 53d50000 00:00 0 
53d51000-54551000 rwxp 53d51000 00:00 0 
54551000-54552000 ---p 54551000 00:00 0 
54552000-54d52000 rwxp 54552000 00:00 0 
54d52000-54d53000 ---p 54d52000 00:00 0 
54d53000-55553000 rwxp 54d53000 00:00 0 
55553000-55554000 ---p 55553000 00:00 0 
55554000-55d54000 rwxp 55554000 00:00 0 
55d54000-55d55000 ---p 55d54000 00:00 0 
55d55000-56555000 rwxp 55d55000 00:00 0 
56555000-56556000 ---p 56555000 00:00 0 
56556000-56d56000 rwxp 56556000 00:00 0 
56d56000-56d57000 ---p 56d56000 00:00 0 
56d57000-57557000 rwxp 56d57000 00:00 0 
57557000-57558000 ---p 57557000 00:00 0 
57558000-57d58000 rwxp 57558000 00:00 0 
57d58000-57d59000 ---p 57d58000 00:00 0 
57d59000-58559000 rwxp 57d59000 00:00 0 
58559000-5855a000 ---p 58559000 00:00 0 
5855a000-58d5a000 rwxp 5855a000 00:00 0 
58d5a000-58d5b000 ---p 58d5a000 00:00 0 
58d5b000-5955b000 rwxp 58d5b000 00:00 0 
5955b000-5955c000 ---p 5955b000 00:00 0 
5955c000-59d5c000 rwxp 5955c000 00:00 0 
59d5c000-59d5d000 ---p 59d5c000 00:00 0 
59d5d000-5a55d000 rwxp 59d5d000 00:00 0 
5a55d000-5a55e000 ---p 5a55d000 00:00 0 
5a55e000-5ad5e000 rwxp 5a55e000 00:00 0 
5ad5e000-5ad5f000 ---p 5ad5e000 00:00 0 
5ad5f000-5b55f000 rwxp 5ad5f000 00:00 0 
5b55f000-5b560000 ---p 5b55f000 00:00 0 
5b560000-5bd60000 rwxp 5b560000 00:00 0 
5bd60000-5bd61000 ---p 5bd60000 00:00 0 
5bd61000-5c561000 rwxp 5bd61000 00:00 0 
5c561000-5c562000 ---p 5c561000 00:00 0 
5c562000-5cd62000 rwxp 5c562000 00:00 0 
5cd62000-5cd63000 ---p 5cd62000 00:00 0 
5cd63000-5d563000 rwxp 5cd63000 00:00 0 
5d563000-5d564000 ---p 5d563000 00:00 0 
5d564000-5dd64000 rwxp 5d564000 00:00 0 
5dd64000-5dd65000 ---p 5dd64000 00:00 0 
5dd65000-5e565000 rwxp 5dd65000 00:00 0 
5e565000-5e566000 ---p 5e565000 00:00 0 
5e566000-5ed66000 rwxp 5e566000 00:00 0 
5ed66000-5ed67000 ---p 5ed66000 00:00 0 
5ed67000-5f567000 rwxp 5ed67000 00:00 0 
5f567000-Aborted (core dumped)
allexandart@allexandar-desktop:~$ 
```

I can't see picture,only black xdtv screen,i have no sound and after scanning xdtv close himself...

I have radeon 9550 and ubuntu 7.10

Thanks in advance!

---

### Post by Allexandar on 2008-03-21
Noone with this problem?

---

