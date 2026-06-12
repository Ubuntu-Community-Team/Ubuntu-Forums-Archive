---
title: "Viewsonic VX2260wm LCD with Nvidia 7200 GS monitor problem"
date: 2009-01-04
forum: Multimedia Software
---

### Post by angeloio on 2009-01-04
Dear all,

First of all me warmest wishes for a healthy and prosperous New Year.

I am running a live CD with ubuntu 8.10 i386 Desktop (the same issue applies also to 8.04.1) to test my new mobo (gigabyte X48-DS5) and my card (nvidia GeForce 7200 GS - *lspci identifies it as G72 GeForce 7300 SE rev a1*).
My monitor is a new Viewsonic VX2260wm 1080p Full HD HDMI monitor.
I am having the most weird problem:
When the cd initially booted the screen flickers.
I downloaded an i386 linux driver from nvidia.com, killed the x server, run the downloaded NVIDIA-Linux-x86-177.82-pkg1.run file and let it configure the xorg.conf. Then started X again and it still flickered!
I changed the horiz and vertical freq inside the xorg according to monitor tech specs and restarted X. The resolution was 1920x1080 but the vertical freq was 50 Hz! I tried to change it to 60 HZ from System->Preferences->Screen Resolution but there was available only 50 HZ and 51 Hz. 
From the Applications->System Tools->NVIDIA X server Settings the monitor is recognized and I can set the display at 1920x1080@60HZ but when I do the System->Preferences->Screen Resolution reports it as 50 Hz and there is no other option available (and the screen flickers).
If I go down to 1400x1050 then the 60 Hz is available and the monitor does NOT flicker!

How is it possible that the  **Applications->System Tools->NVIDIA X server Settings** and **System->Preferences->Screen Resolution** to report (and have available) two different things :confused:
It seems that even though from the nvidia utility I can set the vert freq at 60 Hz this is NOT actually set from what I can see from  Screen Resolution and there is not even an option there!!!

New Data:
-------------------------------------------------------------------------------------
I found somewhere on the net an example xorg.conf for the monitor so I included:
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
	Option         "AddARGBGLXVisuals" "true"
    Option         "metamodes" "CRT: 1280x1024_60 +1920+0, DFP: 1920x1080 +0+0"
in xorg.conf
----------------------------------------------------------------------------------------
Now the 1920x1080@60 Hz is reported from Screen Resolution as being 103 Hz (!?!?!) the monitor still flickers and when I go down to 1440x900@60Hz the vert freq is still reported from Screen Resolution as being 103 Hz, the monitor does NOT flicker and appears **clearer** then before when the above lines have not been included .
----------------------------------------------------------------------------------------------
I thank you all for your time and help.
Best Regards
Ioannis

---

