---
title: "Resolution Problem on HD TV"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by HyperY2K on 2007-12-21
I try to use my ubuntu media pc on my new hd television (Toshiba Z3030DG), but via a DVI/HDMI cable I got no picture. Its an resolution problem. I want to use 1920 x 1080, but i won't work...

Here is Xorg.0.log

root@ubuntuMedia:~# cat /var/log/Xorg.0.log | grep 1920
(II) RADEON(0): Panel infos found from DDC detailed: 1920x1080
(II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) RADEON(0): Modeline "1920x1080"  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync
(II) RADEON(0): Not using mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) RADEON(0): Modeline "1920x1080"  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync
(II) RADEON(0): Not using mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) RADEON(0): Modeline "1920x1080"  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync
(II) RADEON(0): Not using mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) RADEON(0): Modeline "1920x1080"  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync
(II) RADEON(0): Not using mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)

here's my 1920x1080 modeline

ModeLine "1920x1080" 160.90 1920 1980 2040 2160 1080 1081 1084 1234     +hsync +vsync


TV resolution information:

root@ubuntuMedia:~# xresprobe radeon
id: TOSHIBA-TV
res: 1920x1080 720x576 640x480
freq: 15-68 23-61
disptype:
root@ubuntuMedia:~#

with 720x576 it works, but it's litte low resolution ;-)

Any suggestions?

---

