---
title: "NVIDIA GeForce 6150SE &amp; VX20LHD Monitor"
date: 2010-09-09
forum: Multimedia Software
---

### Post by henjj on 2010-09-09
I recently purchased a cheap computer to use for everyday tasks.  It came pre-loaded with Windows 7.  The monitor I am using is a Vizio VX20L.  It's native resolution is 1366X768.  I have no problem with the screen resolution in Windows 7 but in Ubuntu, I am having some issues.  I have the propriatary Nvidia driver installed in Ubuntu but for some reason I cannot get the screen resolution right.  I am currently using a resolution of 1360x768 and the right part of my desktop is not on the screen.  I have tried to adjust the screen size using the monitor settings, but I still cannot get the whole screen to show up.  If I set the resolution to Auto in the NVIDIA X Server Settings, it defaults to 1280X1024 and I can see my whole desktop, but it is streeeeetched. Any help would be much appreciated.

Here is some relevant information pertaining to my system:
I'm using Ubuntu 10.04
Integrated Video chip is NVIDIA GeForce 6150SE
The driver I'm using is NVIDIA accelerated graphic driver (version current)[Recommended]
screen is a Vizio VX20LHD

Thanks,

---

### Post by henjj on 2010-09-10
Ok, I finally figured it out.  If you are having the same issue that I was here is what I did:  I opened up the NVIDIA XServer Settings.  I hit "Save to X Configuration File".  Then I went into the X Configuration File and edited it with modeline information I pulled from my windows 7 install.  Here are two links that were helpful to me in figuring this out:

[http://ubuntuforums.org/showthread.php?t=789173&highlight=vx20l](http://ubuntuforums.org/showthread.php?t=789173&highlight=vx20l)
[http://www.x.org/wiki/FAQVideoModes#head-82230a582646cbf28ac41dec2139732ee868e0d2](http://www.x.org/wiki/FAQVideoModes#head-82230a582646cbf28ac41dec2139732ee868e0d2)   (the secion in the page titled "Obtaining modelines from Windows program PowerStrip")

Also, I have posted my xorg.conf file for your reference.

Hope this helps someone.

---

### Post by Lemler33 on 2011-02-25
> **henjj said:**
> Ok, I finally figured it out.  If you are having the same issue that I was here is what I did:  I opened up the NVIDIA XServer Settings.  I hit "Save to X Configuration File".  Then I went into the X Configuration File and edited it with modeline information I pulled from my windows 7 install.  Here are two links that were helpful to me in figuring this out:

[http://ubuntuforums.org/showthread.php?t=789173&highlight=vx20l](http://ubuntuforums.org/showthread.php?t=789173&highlight=vx20l)
[http://www.x.org/wiki/FAQVideoModes#head-82230a582646cbf28ac41dec2139732ee868e0d2](http://www.x.org/wiki/FAQVideoModes#head-82230a582646cbf28ac41dec2139732ee868e0d2)   (the secion in the page titled "Obtaining modelines from Windows program PowerStrip")

Also, I have posted my xorg.conf file for your reference.

Hope this helps someone.

i have this very same problem, but i cant figure out how to fix it, and it seems that no one uses linux so my resources are very limited can you please describe in detail on what you did to fix this problem?

---

### Post by henjj on 2011-03-03
What version of Ubuntu are you using?  I just installed 10.10 and I haven't had an issue with my graphics card and monitor.  I haven't downloaded the restricted NVIDIA driver yet, so I'm not sure if I will have to go through the process I described in my post above.  After I get it installed, I'll let you know.  In the meantime, give me some more details of your system and I can try and help.

---

