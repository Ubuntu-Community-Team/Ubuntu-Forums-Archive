---
title: "Error: No TV Decoder/ 8.04 / Pinnacle DC30+"
date: 2008-07-08
forum: Multimedia Software
---

### Post by idcj on 2008-07-08
Hi,

Strange problem here.  My Pinnacle Miro DC30+ (Zoran chipset) is detected at startup but whenever I try to use it I get I/O errors.

List of modules - 

$lsmod|grep zr

zr36016                 7560  1 
zr36050                11144  1 
zr36067               180880  0 
compat_ioctl32         11136  1 zr36067
i2c_algo_bit            8452  1 zr36067
videocodec             10280  3 zr36016,zr36050,zr36067
i2c_core               28544  5 adv7175,vpx3220,zr36067,i2c_algo_bit,nvidia
videodev               30720  1 zr36067


(Ubuntu 8.04(amd64) on Intel Q9300x4, NVidia graphics)


I get the following showing up in dmesg:

$dmesg
[  961.213690] DC30plus[0]: no TV decoder loaded for device!


Anyone come across this before?


Output from $ lavrec -f a -i P -a 0 -v 2 -d 1 test.avi

   INFO: [lavrec] Recording parameters:
   INFO: [lavrec] Output format:      AVI
   INFO: [lavrec] Input Source:       S-Video PAL

   INFO: [lavrec] Decimation:         1
   INFO: [lavrec] Quality:            50
   INFO: [lavrec] Recording time:     -1 sec
   INFO: [lavrec]  
   INFO: [lavrec] MJPEG buffer size:  256 KB
   INFO: [lavrec] # of MJPEG buffers: 64
   INFO: [lavrec] Audio disabled
--DEBUG: [lavrec] Maximum size per file will be 1739 MB
**ERROR: [lavrec] Error opening video-device (/dev/video0): Input/output error
++ WARN: [lavrec] Not ready for capture (state = 0)!
Press enter to start recording>Segmentation fault

---

