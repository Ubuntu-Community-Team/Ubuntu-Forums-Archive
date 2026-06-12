---
title: "Change in NVIDIA driver behavior with nvidia-304.88 driver update"
date: 2013-04-17
forum: Multimedia Software
---

### Post by T_W on 2013-04-17
Having lots of difficulties with the recent nvidia-304.88 driver update.  I am running Ubuntu 12.04.2 LTS.  I have a Dell M4400 with docking station.  I have two monitors plugged into the docking station.  All worked reasonable well before the update.  I had to disable the laptop panel as the card does not support three displays.

Since the update to the driver if I plug in a second external monitor all screens blink on and off continually and the system becomes unusable.  This can sometime lead to an X lock up where the screen is entirely black, but I can move the mouse.  This is sometime solved by unplugging the second monitor and restarting the X server.

I have noticed that the behavior of the driver has changed dramatically with an external monitor.  It used to be that if I plugged in an external monitor, nothing would happen until I reconfigured things with nvidia-settings.  With the driver update as soon as I plug in an external panel, something seems to detect the panel automatically sets up TwinView without any interaction.  Normally, this would be a good thing, but I think the problem has to do with auto detection of the 2nd external monitor and potential conflicts with the two external monitors and the internal panel.

Any ideas?   I checked the forums and the information on the nvidia-304.88 driver update, but I don't see anything indicating a change in behavior this big?  Any ideas how to prevent the nvidia driver from automatically reconfiguring the desktop when a panel is plugged in?  Any advice on how to rollback to the pre-304.88 version?

---

### Post by midnightramen on 2013-04-18
you might want to try the latest drivers from nvidia.com You'll have to go through a roundabout process by hitting Ctrl+Alt+F1 to get to the command prompt, stop the lightdm service, run the script to install the driver, blacklist the nouveau module, etc, but so far, I have not had any issues with the Nvidia 310.40 on an Ubuntu 12.10 desktop.

Alternatively, there is also a package out there "nvidia-experimental-310" which may be easier to install. should be accessible using 'apt-get install nvidia-experimental-310'. I would also suggest installing the 'nvidia-settings-experimental-310' as well.

**EDIT: changed 'yum' to 'apt-get' . Confusing my distros here.

---

### Post by T_W on 2013-04-18
No change in behavior with nvidia-experimental-310.  It does seem to the system trying to make all three displays active at the same time.  If I can manage to deactivate the panel on the laptop, then I can get the two external displays working.  Unfortunately this involves unpredictable pulling of monitor cables and rebooting until I can get the system stable.  

Man, the nvidia-304.88 driver update is a nightmare.

Any advice on downgrading the driver?

---

### Post by T_W on 2013-04-22
Well, I downgraded to nvidia-current-295.40-0ubuntu1.3 and  nvidia-settings-295.33-0ubuntu1 and the system is working again.  

To downgrade, I followed the instructions [here]("http://askubuntu.com/questions/129656/how-do-i-downgrade-nvidia-drivers-in-12-04").  Basically a manual download from launchpad followed by a manual 'dpkg -i' of the old driver.

As I had nvidia-experimental-310 installed, I also had to remove this package.

Anyone have any idea what in the nvidia-304.88 driver update caused such a radical change in behavior?

---

### Post by wojeda on 2013-04-30
> **T_W said:**
> ... Anyone have any idea what in the nvidia-304.88 driver update caused such a radical change in behavior?

I sure don't. All I know is that I was running on an old FX4000 and Kubuntu 10.04 LTS. What ever that driver was, was working flawlessly.

I just upgraded my card to a new GTX640 and since I was in upgrade mood, I went ahead and moved Kubuntu to 13.04. Then my old drivers were not an option anymore and was forced to apt-get "nvidia-current", which brought down v[COLOR=#000000][FONT=Trebuchet MS]304.88. [/FONT][/COLOR]Now all hell broke loose. My dual monitors do not clone anymore and my X11Vnc does not work any more either.
[COLOR=#000000][FONT=Trebuchet MS]
[/FONT][/COLOR]Why do people have to fix that which is not broken ?!?!? :confused:[COLOR=#000000][FONT=Trebuchet MS] [/FONT][/COLOR]

---

