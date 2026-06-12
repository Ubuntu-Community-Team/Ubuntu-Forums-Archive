---
title: "netbook video issue with Gateway ZA8 with ubuntu 10.4"
date: 2010-08-10
forum: Multimedia Software
---

### Post by rj44319 on 2010-08-10
I installed flowing the instructions provided...
It works great and all of the parts work great except the video card...
It will boot up fine and show the home screen just like it should then
if I open a game on it like battle tanks it will go to ****... (it semes that
if an app demands high render it will crash the screen)
the screen looks like it got cracked and colors and lines all over the place.
I looked similar problems up on the search and found out some one had an 
issue with the same net book but nothing like mine as it sounds..
The computer never fresses when this happens.
It sounds like a driver issue with the built on video chip set?

---

### Post by pastalavista on 2010-08-10
Have you run the Hardware Drivers tool in the System-->Administration menu? Activate the driver, if you haven't already. If you have more than one entry, try another one. To find out what video chip and driver module is running, open a terminal (Applications-->Accessories-->Terminal) enter the following command and post the output here```
sudo lshw -c video
```

---

### Post by rj44319 on 2010-08-10
In the menu you are talking about there are no preferred drivers listed..
I will check the other suggestion tonight...

---

### Post by rj44319 on 2010-08-25
Sorry for the laaaate reply...
here is the reply:
*-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:27 memory:d0000000-dfffffff(prefetchable) memory:f0100000-f010ffff ioport:9000(size=256) memory:f0000000-f00fffff

---

### Post by no2498 on 2010-08-25
wright down your settings so you can change it back if needed
and try this btw i do not know if your on a pc or a mac

this comes the program cheese help files


5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.

---

### Post by rj44319 on 2010-08-26
I have a PC
I tried your ideas and it still dos this:
Like when i go to Google it dos this, Is this Google crashing the screen? 
I have nver had it happen at this form...

---

### Post by jarrpa on 2011-04-25
Reporting the same issue on my Gateway ZA8 with Ubuntu 10.10. I tried [no2498]("http://ubuntuforums.org/member.php?u=906707")'s solution but that did not work for me either. My screen ends up looking my like the screenshots posted by rj44319.

I recall not having this problem a while back while I was either on 9.04 or 9.10, so I will be trying to downgrade tomorrow and seeing if I can get that to work.

I would like to be able to keep up to date with Ubuntu releases, but if they don't fix this issue I can't say I'll be sticking with it very long.

---

### Post by rj44319 on 2011-04-25
Me too... no fix
I ended up going to linux mint DB
It still happens, but as long as i stay away from some websites its ok...
You said you had no issues with a earlier release?
I will try that too.

---

### Post by jarrpa on 2011-04-25
Yup. I installed 9.10 Netbook Remix and after installing the linux-backports wireless module to deal with a flaky wireless connection, the laptop seems to be working like a charm.

I tried running a live CS (USB) of 11.04 Beta 2, but that has the same problems as 10.10 and 10.04.

---

### Post by rj44319 on 2011-04-25
Were did you download 9.10?

---

### Post by jarrpa on 2011-04-25
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/) under "UNR live CD"

Unfortunately it's 32-bit only, but for my purposes that doesn't matter much.

---

