---
title: "Color calibrating or profiling your screen"
date: 2008-05-26
forum: Multimedia Software
---

### Post by john_navarro on 2008-05-26
These are more notes than a how-to; but if you're struggling like I was then hopefully this will get you to where you want to be.

Setup: Hardy (8.04) on 32bit Intel  
Calibration Device: Xrite DTP94

Software to use build ICC profile:
[http://www.argyllcms.com/](http://www.argyllcms.com/)

Software used to load and clear ICC profile:
(also available via Synaptic as XCALIB)
[http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/](http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/)


Step 1: Download Argyll and untar binary.

Step 2: Create Profile

ARGYLL .6
(4 steps are needed to create an ICC profile in this version)
sudo ./dispcal -v -a -i 94 -y l lcdprofile
sudo ./targen -v -d3 -f500 lcdprofile
sudo ./dispread -v -y l -i 94 -a -k lcdprofile.cal lcdprofile
sudo ./profile -v -A "Viewsonic" -M "Viewsonic VP191b" -D "May 8 2008" -d mt -c mt -q m -as lcdprofile

ARGYLL .7  (beta 8 in my case - only one step needed)
sudo ./dispcal -v -y l -o lcdprofile

Step 3: Load profile
xcalib lcdprofile.icc     (you may have to specify entire path to icc profile)


To clear profile:  xcalib -c

---

