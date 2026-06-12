---
title: "Command Line after nVidia update"
date: 2008-11-27
forum: Multimedia Software
---

### Post by Mckooy on 2008-11-27
Hello All,

I am very new to Linux and installed Ubuntu yesterday (latest version downloaded from Ubuntu website on Tuesday)

I installed and played around, did some updates rebooted and all was well.  I then got  a graphics card update suggested by Linux. I rebooted and now cannot get into the GUI and only get command line. 

I log in and type startx and get the following message

Fatal Server Error;
no screens found
giving up
.......................unable to connect to xserver

I have had a look online but can find lots of people with old versions with this problem but no fixes that work.
1
any help appreciated!

---

### Post by kpholmes on 2009-09-05
i have this same problem, i have an ati card though. i was able to install the driver properly but when ubuntu updates its self, something in the updates makes it unable to connect to xorg. its really agrovating. if anyone has a solution that would be great. by the way ive used ubuntu 8.10 and 9.04 and get the same problem after updates.

---

### Post by RedRat on 2009-09-05
> **kpholmes said:**
> i have this same problem, i have an ati card though. i was able to install the driver properly but when ubuntu updates its self, something in the updates makes it unable to connect to xorg. its really agrovating. if anyone has a solution that would be great. by the way ive used ubuntu 8.10 and 9.04 and get the same problem after updates.

I too have had this problem in the past with Ubuntu updates with my Nvidia card. The only way round this seems to use EnvyNG and nvidia-settings. Envy is in the Hardy repos and so is nvidia-settings. So you can use synaptic. You might want to try these. First run EnvyNg and be sure that the proper driver is installed for your version of Ubuntu, then run nvidia-settings from the command line using sudo or gksudo.

---

### Post by kpholmes on 2009-09-05
thanks for the quick reply, but i happen to have an ati card, should i try to install the restricted drivers for ati on top of envyng?

---

### Post by RedRat on 2009-09-05
> **kpholmes said:**
> thanks for the quick reply, but i happen to have an ati card, should i try to install the restricted drivers for ati on top of envyng?
Well no! EnvyNG installs the appropriate drivers I believe from either the Nvidia or ATI sites. When you run it, it will install the version for your card. However, after that, I can't say since I do not have an ATI card, mine is an Nvidia and you use nvidia-settings to set the resolution and monitor, this then is written to the xorg.conf file. Now ATI may have the equivalent program, so you ought to look into that. Maybe it is called "ati-settings" or something similar. 

You may want to Google EnvyNG and go to the software home site. Check this out:
[HTML]http://albertomilone.com/nvidia_scripts1.html[/HTML]

---

