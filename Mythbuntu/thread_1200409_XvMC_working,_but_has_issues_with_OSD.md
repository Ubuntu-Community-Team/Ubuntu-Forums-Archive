---
title: "XvMC working, but has issues with OSD"
date: 2009-06-30
forum: Mythbuntu
---

### Post by thegooch49 on 2009-06-30
Hi! I'm running 9.04 with a GeForce 6600GT. I got XvMC running after some trial and error. My OSD (title bar with prgramming info) is black and white, which others have said is the clear sign that XvMC is running. 

So that is good, but some new problems have cropped up now. Anytime the OSD is on the screen, the mythfrontend process hits 100%. Playback pretty much halts, and the entire system is unresponsive. Once the OSD goes away, the system is responsive again and playback resumes. 

I think it's simply the OSD causing this. Even turn the volume up/down halts the system (since this puts something on the OSD). Changing channels is impossible. Again, once the OSD goes away, playback resumes and looks great.

Any ideas what is going on here? I'm digging XvMC because my playback looks great while I'm watching TV. 

Thanks for the help.

---

### Post by novellahub on 2009-06-30
Find out what theme you are running in the frontend.  Then edit the following file:

```
osd.xml
```

For example if you are running the isthums theme:

```
/usr/share/mythtv/themes/isthmus/osd.xml
```

Set the fadeaway value to zero:

```
<fadeaway>0</fadeaway>
```

You will most likely need to restart the frontend by simply exiting and then re-launching it.

---

### Post by crez79 on 2009-06-30
The same place you set it up to use XvMC, is an option for OSD renderer. Try using a different renderer and see if that helps. There is also a checkbox to disable the fade away novellahub suggested.

---

### Post by jMon54 on 2009-06-30
I ended up downgrading to an older driver for my nVidia card to solve this OSD pain-in-the-butt issue.

---

### Post by thegooch49 on 2009-06-30
Thanks for the suggestions. I edited the osd.xml file for my theme and that didn't help unfortunately. 

> **crez79 said:**
> The same place you set it up to use XvMC, is an option for OSD renderer. Try using a different renderer and see if that helps. There is also a checkbox to disable the fade away novellahub suggested.

crez79: Where exactly do I set this renderer? You said to do it in the same place I set it up to use Xv. To use Xv, I just modified my xorg and XvMCConfig. Is there something I set there? 

This also got me looking at playback profiles. I was using CPU+ for Xv. I tried CPU-- as well. Same problem. Any other suggestions? Thanks a bunch for all the help.

---

### Post by crez79 on 2009-07-01
The setting I was talking about is in the playback profiles. Select which profile you want and edit the conditions on the bottom and osd renderer and fade setting is in there for each resolution condition named.

---

### Post by thegooch49 on 2009-07-01
I changed my playback profile to 'slim' and that seemed to do the trick. Playback looks great, and the OSD doesn't freeze the system anymore. Thanks again to all for the advice.

---

