---
title: "Flashplayer fullscreen crashes"
date: 2010-12-05
forum: Multimedia Software
---

### Post by Quanzel on 2010-12-05
Hello,

When I press for example the fullscreen button from a Youtube video the flashplayer crashes. I've searched this problem but there are many solutions that doesn't work or don't exactly fit my problem.
My guess is that is has something to do with my videocard driver (ati mobility x300) because is happens in both firefox and chrome.

In chrome I get the following error: The following plug-in has crashed opt/google/chrome/libgcflashplayer.so

In firefox: The Adobe Flash plugin has crashed. No report available.

I've tried to reinstall the flash player but thats kinda hard and the extra problem is that in the new Chrome releases the flash player is fully integrated.

But as I said I think it that it is more a videocard/driver problem. As far as I understand is that I can't install the proprietary ATI driver (fglrx) so I have to use the open source driver. 

So does anyone know how I can fix this? Maybe reinstall the open source driver, how can I do that?

OS: Ubuntu 10.10 32bit
Chrome: 8.0.552.215

---

### Post by lovinglinux on 2010-12-05
Try [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html).

---

### Post by Quanzel on 2010-12-09
Isn't that only for Firefox issues? My problem occurs in every browser so it seems a more wider problem. 

Does anyone know how I can reinstall / 'recover' my open source driver for my GPU?

---

### Post by lovinglinux on 2010-12-09
> **Quanzel said:**
> Isn't that only for Firefox issues? My problem occurs in every browser so it seems a more wider problem. 

Does anyone know how I can reinstall / 'recover' my open source driver for my GPU?

The crash fix available there works for all browsers. Might not be a solution for you, but worth a try.

---

### Post by GreekRockNRoller on 2011-01-15
Hello i had the same problem with flash player so i tried the first solution in "Flash infullscreen is choppy, completely white or crashes" and it solved me problem. thxxx alot!   **Flash infullscreen is choppy, completely white or crashes**

 Try these commands:
 sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/ Restart the browser.

If that doesn't work, then right-click  the flash video, select "Settings", then untick the option "Enable  hardware acceleration".
 **Source:** [https://bugs.launchpad.net/ubuntu/+bug/346289](https://bugs.launchpad.net/ubuntu/+bug/346289)

---

### Post by Ajay Ramaseshan on 2011-04-15
@GreekRockNRoller:

I have Ubuntu 10.10 32 bit and am running Firefox 3.6-13. The youtube video upon fullscreening, crashes the plugin acrross all tabs.
And there is no provision to send a crash report, which is usually present.
This problem occurs in other browsers too ie Chrome 9 and Opera 11.
I have an ATI Mobility Card

You gave a suggestion to write mms.cfg file . However this file already exists in my /etc/adobe directory. also, hardware acceleration is enabled in the flash player settings, inspite of this there is a full screen  crash.

Could you please help me out??

---

