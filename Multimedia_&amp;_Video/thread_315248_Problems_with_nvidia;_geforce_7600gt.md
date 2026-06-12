---
title: "Problems with nvidia; geforce 7600gt"
date: 2006-12-08
forum: Multimedia &amp; Video
---

### Post by maniacmusician on 2006-12-08
hey,

I never thought I would say this, but I'm actually having problems with my nvidia card. i'm running kubuntu 6.10, and have a GeForce 7600GT from eVGA. my main problem is that I can't get the resolution to be any higher than 1280x1024. I have other problems as well, but figured I'd start with this. My ideal resolution is 1400x1050. Sad thing is, I was actually able to run this resolution with the open source ATI drivers!

the nvidia-settings dialog does not let me pick 1400x1050 as an option. I can't choose it with the Display KCM either, even after manually adding xorg.conf to add it in. So what's going on here? would appreciate some help. Attaching my xorg.conf.

Oh, by the way, I used Automatix Bleeder to install Amaranth's packages. 

Thanks.

---

### Post by halfvolle melk on 2006-12-09
Try adding **Option "UseEDID" "FALSE"** to the device section. That should prevent the driver from skipping mode lines.

---

### Post by maniacmusician on 2006-12-10
no, sorry, that doesn't work at all. In fact, that reduces the available resolution to 640x480!!

and by the way, I reinstalled and am now using tseliot's drivers from his website. Still can't get that resolution.

thanks,

---

### Post by halfvolle melk on 2006-12-10
Ok, another thought (in addition to UseEDIT perhaps) is to add the appropriate HorizSync and VertRefresh to the Monitor section.

---

### Post by maniacmusician on 2006-12-10
> **halfvolle melk said:**
> Ok, another thought (in addition to UseEDIT perhaps) is to add the appropriate HorizSync and VertRefresh to the Monitor section.
i'm not sure of these numbers, I havn't been able to find them for my monitor. xorg.conf identifies as a 107s and it says philips magnavox on the front of it, but I havn't been able to find those values for it when googling...

---

### Post by halfvolle melk on 2006-12-10
On the back of your monitor it'll probably say what the exact model is (it does on all of my screens anyway). Then check if it's listed here:
[http://www.si87.com/MonitorSolutions/philips/](http://www.si87.com/MonitorSolutions/philips/)

---

### Post by thedark1 on 2006-12-10
Open this file: **/var/log/Xorg.0.log** and look for Modeline lines in it. Pick up your desired resolution from the supported modelines. Example in my case:
(II) NV(0): **Modeline "1600x1200"  229.50  1600 1664 1856 2160  1200 1201 1204 1250** +hsync +vsync


Put the following modeline in your XF86Config in the Monitors section:
[B]Modeline "1600x1200" 229.50  1600 1664 1856 2160  1200 1201 1204 1250
[/B]
and add/modify it to your active modes in the Screen section:
SubSection "Display"
                Depth           24
                **Modes           "1600x1200"**

EndSubSection
This will tell your xserver to use 1600x1200 @ 24 bpp 
Copy the modelines values exactly as in /var/log/Xorg.0.log

**!!! Remember to use your own values, the values provided here may not work for you!**

---

### Post by maniacmusician on 2006-12-11
thanks I will try again when I get back home

---

### Post by maniacmusician on 2006-12-11
> **thedark1 said:**
> Open this file: **/var/log/Xorg.0.log** and look for Modeline lines in it. Pick up your desired resolution from the supported modelines. Example in my case:
(II) NV(0): **Modeline "1600x1200"  229.50  1600 1664 1856 2160  1200 1201 1204 1250** +hsync +vsync


Put the following modeline in your XF86Config in the Monitors section:
[B]Modeline "1600x1200" 229.50  1600 1664 1856 2160  1200 1201 1204 1250
[/B]
and add/modify it to your active modes in the Screen section:
SubSection "Display"
                Depth           24
                **Modes           "1600x1200"**

EndSubSection
This will tell your xserver to use 1600x1200 @ 24 bpp 
Copy the modelines values exactly as in /var/log/Xorg.0.log

**!!! Remember to use your own values, the values provided here may not work for you!**
I can't find any Modeline lines. when searching for "mode", though, this is one thing that comes up

> (WW) NVIDIA(0): No valid modes for "1400x1050_60"; removing.

what does that mean for me?

I also found the following lines that I thought were interesting (they were right below the previously quoted line):
> (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0):
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (104, 113); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp


any suggestions?

---

### Post by tseliot on 2006-12-12
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by solitary on 2006-12-12
Hello,

I have similar hardware to you. Leadtek Geforce 7600GT AGP with a Philips 109B6 Monitor (CRT). Typing this in 1400x1050 @ 85 Hz and it works fine (I normally run 1280x960 @ 85 Hz). Driver version is 9631 from [http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html).

I recommend using the possibility to autogenerate an config from within nvidia-settings. And when its working customize options for beryl, etc. Remember to sudo nvidia-settings because it dosn't overwrite your old settings otherwise (remember to backup too). For me Display KCM caused strange results, so I am leaving it alone.

Attaching my current xorg.conf maybe it can help you. I have a tv connected too, so it's a little large.

---

### Post by maniacmusician on 2006-12-12
> **tseliot said:**
> Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)
Thanks, will try when I get home...but that last would be irrelevant for me, I think, as I'm using a CRT.
> **solitary said:**
> Hello,

I have similar hardware to you. Leadtek Geforce 7600GT AGP with a Philips 109B6 Monitor (CRT). Typing this in 1400x1050 @ 85 Hz and it works fine (I normally run 1280x960 @ 85 Hz). Driver version is 9631 from [http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html).

I recommend using the possibility to autogenerate an config from within nvidia-settings. And when its working customize options for beryl, etc. Remember to sudo nvidia-settings because it dosn't overwrite your old settings otherwise (remember to backup too). For me Display KCM caused strange results, so I am leaving it alone.

Attaching my current xorg.conf maybe it can help you. I have a tv connected too, so it's a little large.

Thanks for the tips....I'm using the 9626 driver from the unstable section of the site...is the 9631 actually newer?? If so, why is the unstable section still up there? I actually didn't do sudo nvidia-settings...last time I tried this on an older installation, what it did was make root own nvidia-settings.rc, so it couldn't automatically load the settings from that file because I don't log on as root...or that's the explanation I got anyways. I will try the sudo nvidia-settings again. I'd appreciate an answer about which driver is the newest, because that's the one I was trying to install...I just assumed 9626 from unstable was the newest one.

Thanks

---

### Post by solitary on 2006-12-12
I can help you with the driver versions.

The 9631 version is the latest stable driver according to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).

Latest beta is 9742 [http://www.nzone.com/object/nzone_downloads_rel70betadriver.html](http://www.nzone.com/object/nzone_downloads_rel70betadriver.html)

The unstable repository probably just isn't updated yet, but this is just my guess?

EDIT: 

I use kdesu nvidia-settings from Run Command... in K-menu to gain root-power instead of sudo.

I didn't know that issuing sudo nvidia-settings changed the rights of any file. My computer is running stable sofar anyway (weeks aleast).

---

### Post by maniacmusician on 2006-12-12
it wooooooooorks!!! 

I don't know how! I did a dpkg-reconfigure xserver-xorg (replacing the nvidia-xconfig file), change the modeline to say "1400x1050_50" and set the UseEDID to false, and it worked. I'm going to try and get a better refresh rate...maybe that made the difference though, I went for a lower refresh rate this time.

I still have a couple of questions. I read somewhere that LCDs and CRTs demand different aspect ratios. ie, 1280x1024 is an LCD aspect ratio whereas 1400x1050 is a CRT ratio. Since I have a CRT, do you think there's a smaller, better resolution I can get with the correct aspect ratio?


And, one last question....Is it normal for my GPU fan to get really loud when I do 3D related stuff? because If I'm going to be running beryl, I don't want a loud fan to be on all the time....Thanks for all the help again, you guys were great.


PS: another thing that could've made a difference; the dpkg-reconfigre also added in some generic Sync ranges for the monitor so that could be part of the solution.

---

### Post by maniacmusician on 2006-12-13
[conspicuous bump] pretty please? The questions are not too hard, I think, and I can mark this thread resolved after them :)

---

### Post by solitary on 2006-12-13
Glad that you are up and running. Try searching Philips site for your monitors HorizSync and VertRefresh. Seems like 50 Hz refreshrate is a little low and could be a little tiresome on the eyes if you use your computer alot. 

You can check if your monitor has a optimal resolution on Philips site. But the beauty of CRT is that you can pretty much choose one. Try any resolution that has a 4:3 ratio. If you divide hight with width you get 1.3333. Like 1024*768, 1152*864, 1280*960 or 1400*1050. 
Also check that you get a decent refreshrate, the available refreshrate gets lower with higher resolution.
 
Yes you are right on. LCDs often have a native resolution of 5:4 like 1280*1024. But many new LCDs have other native resolutions for example the widescreen format. 

Yes its normal, my fan speeds up in 3D mode too. Things you can do is get an more quiet aftermarket fan like the ones from ZALMAN, they have models wich fit the 7600GT (also check that you have room for it in your case). I think they are expensive, but they are among the best. Some people have modded CPU fans to fit their videocards for a cheaper but more improvised solution. And then the cheapest is you can always try to postion the case further away from your ears. Maybe in another room, or a closet.

---

### Post by maniacmusician on 2006-12-13
okay, thanks for all your help! the fan actually slows back down after a while of running beryl, so i'm okay with it. I think I'll also stick with 1400x1050 for now. For my xorg. the beginning of my modeline is 
> "1400x1050_75" "1400x1050_60" "1400x1050_50" "1280x1024"

so how can I check which one it's actually using?

---

### Post by solitary on 2006-12-14
I am not completely sure, KCM Display gives me a different vaule than nvidia-settings. I am hoping nvidia-settings is in control. Try this in terminal: nvidia-settings -q all | grep RefreshRate

---

### Post by maniacmusician on 2006-12-14
I got:

>   Attribute 'RefreshRate' (Alexis:0.0; display device: CRT-0): 59.98 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.


pretty much 60, which was the second option on my modeline, so I guess that's the best my monitor can do?

---

### Post by solitary on 2006-12-15
If your xorg.conf have the right sync ranges for your monitor, then 60 seems to be the higest. Check the documentation for your monitor to be sure because this differ between diffrent models.

---

### Post by maniacmusician on 2006-12-15
yeah, thanks again for all your help; appreciate it.

---

