---
title: "Video Problems"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by pstlwppd102 on 2006-07-14
For some unknown reason my monitor resolution is stuck on 800X600 and there are no alternative options.  Recently installed fresh copy of 6.06.  Still no change.  Any thoughts

---

### Post by Dr. Nick on 2006-07-14
yep, I bet I know why, check out the first link in my signature

[http://www.geocities.com/aebcoat/index.html](http://www.geocities.com/aebcoat/index.html)

Try to add the desired res per my instructuions and see if it helps

---

### Post by jaywatkins on 2006-07-18
Umm... No...

I am having the same problem.  I tried your suggestions, which are great, but have been unable to get my resolution above 640x480.

U606 does not like my hardware...

/J

---

### Post by Dr. Nick on 2006-07-18
> **jaywatkins said:**
> Umm... No...

I am having the same problem.  I tried your suggestions, which are great, but have been unable to get my resolution above 640x480.

U606 does not like my hardware...

/J


Have you also re ran the xorg config program  and choose a monitor in the 'medium'  section that has support for your desired res? If simply adding the line for the new res to your xorg.conf doesnt work it may be your refresh rate is improperly set, If you tried that aswell then I am not sure where to go from their.

---

### Post by jaywatkins on 2006-07-18
Hello,

Yes, I did try the "medium" option with the xorg config settings, and I basically copied the refresh ratings verbatim from Dell's site.  Ubuntu does not like my hardware.  I'll try another distro...

Thanks

---

### Post by tseliot on 2006-07-18
You might try this guide first:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by jaywatkins on 2006-07-18
Definetley, thanks...

I want this to work, but it has been a flaming pain in the ***. 

/J

---

### Post by jaywatkins on 2006-07-19
In the end it was a BIOS update that fixed the driver issue.  

IF ANYONE HAS AN OPTIPLEX GX260 WITH THIS PROBLEM, CHECK YOUR BIOS.

If it is at rev. a06, update to a09 from:

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=555&l=en&s=biz&releaseid=R89214&SystemID=PLX_PNT_P4_GX260&os=WW1&osl=en&deviceid=162&devlib=0&typecnt=1&vercnt=7&formatcnt=3&libid=0&fileid=116401](http://support.dell.com/support/downloads/download.aspx?c=us&cs=555&l=en&s=biz&releaseid=R89214&SystemID=PLX_PNT_P4_GX260&os=WW1&osl=en&deviceid=162&devlib=0&typecnt=1&vercnt=7&formatcnt=3&libid=0&fileid=116401)

/J

---

