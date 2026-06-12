---
title: "Problem with Radeon HD6870 drivers and GPU temperatures"
date: 2011-02-02
forum: Multimedia Software
---

### Post by Newbie1979 on 2011-02-02
Hello!

This is my first post at the forum. I am not so profficient with Linux but I have to use it at my University so I hope you guys can help me out here. I am really lost...

I have recently installed Ubuntu 10.10 on my new computer. I have a Radeon HD 6870. I have had great problems with getting the graphics driver to work. After 2 days of research (I am new to this so it took some time) I have followed and completed this guide (by editing xorg.conf):
[URL="http://justbloodywork.blogspot.com/2010/12/linux-from-scratch-radeon-hd-6870.html"]

Now Ubuntu seems to work with my graphics card since I get the well known water mark in the down-right corner. 
However, I am worried that the drivers doesnt work as they are supposed to do since the graphic card doesnt sound at all.
When I run Windows 7 and manually set GPU fan speed >35% the fans sound terribly high. Now they doesnt sound at all. I can not tell if the just simpy running very low or if they are completely shut down...

I have run Im-sensor (and Xsensors 0.70) to check my temperatures. Here follows what Im-sensors says:



fan1:       1328 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +42.0°C  sensor = thermistor
temp2:       +32.0°C  sensor = thermal diode
temp3:       +49.0°C  sensor = thermistor

It seems that either is my GPU fan not active at all or Im-sensor does not detect that sensor.

When I try this command: "aticonfig"
Then I get: "aticonfig: No supported adapters detected"

Which means that I can not use this command: "aticonfig --od-gettemperature"


I dont want to overheat/destory my new graphics cards so right now I am only running Windows.

What should I do? Can I simply trust that the GPU fan works?

Thanks in advance!

---

### Post by khamil8686 on 2011-02-02
when i run sensors mine says

fan1:       2547 RPM  (min =   10 RPM)
fan2:        641 RPM  (min =   10 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =   10 RPM)

and i know the fan is working because if i open the case and look i can see it spinning, fan 3 and 4 for me probably report 0 because they are non existent, to check for sure id just start your computer into linux and remove the cover for a minute to check if the fan is running :) it might be running but at a lower speed because it doesnt need the extra cooling. from what ive seen linux doesnt require the amount of resources windows wants and generally runs quieter. to see if you have the graphics driver installed and activated goto System > Adminstration > Hardware Drivers and see if you have the recommended graphics driver activated, if not then click the recommended one and click activate and it should auto install for you, no need to do it manually unless theres a problem with the auto installer :)

---

### Post by Newbie1979 on 2011-02-02
Thank you for your help =).

I have som comments about your advices (excuse my bad English)

> **khamil8686 said:**
> when i run sensors mine says

fan1:       2547 RPM  (min =   10 RPM)
fan2:        641 RPM  (min =   10 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =   10 RPM)

and i know the fan is working because if i open the case and look i can see it spinning, fan 3 and 4 for me probably report 0 because they are non existent, to check for sure id just start your computer into linux and remove the cover for a minute to check if the fan is running :) it might be running but at a lower speed because it doesnt need the extra cooling.


Hmm... your fan2 is probably for the graphics and it is spinning. I dont like that only my CPU-fan is detected as spinning (I guess that fan1 is for CPU). 
I guess that taken the cover off is the best way of doing this, and this might sound extremely idotic but I actually cant tell when lifting the cover off. It is not only very dark but it is very difficult really see the fan because of the location. I will try to check it out with a flashlight.
But even if the fan is spinning a bit there is no garantuee in my opinion that the drivers will take care of speeding up the fans if nessecary. That is why I would like to detect the fan speed and GPU temperature with a program but so forth I have failed despite of trying out a number of ways.

> **khamil8686 said:**
> 
 from what ive seen linux doesnt require the amount of resources windows wants and generally runs quieter.


I indeed hope so :)

> **khamil8686 said:**
> 
 to see if you have the graphics driver installed and activated goto System > Adminstration > Hardware Drivers and see if you have the recommended graphics driver activated, if not then click the recommended one and click activate and it should auto install for you, no need to do it manually unless theres a problem with the auto installer :)

Ok, thanks! :)
It says that the driver is installed but the weird thing is that even if I delete the "xorg.conf" file so the driver doesnt work for sure (the resolution gets very low when I restart and the water mark stamp dissapear) Ubuntu tells me that the driver is activited nevertheless.

I also tried to automatically fix this problem by reinstalling Ubuntu and choose "install property driver" but then the screen turned blank when rebooting...

---

### Post by khamil8686 on 2011-02-02
glad to help :)
the program to activate proprietary drivers probably just has a variable somewhere that is set when a driver is activated instead of manually checking if all files are present so that might by why it will still say you have a driver activated when you moved the xorg.conf
if you deleted the xorg.conf file and want to get the graphics back there is probably a xorg.conf.backup file somewhere in the same directory, i think whenever a proprietary driver gets activated it makes a backup of the original and the new xorg.conf in case problems ever arise and the user needs to restore them, im not sure why after a new install of ubuntu and installation of the propriety driver gives you a blank screen on reboot, only things i can think of are when you installed ubuntu again did the old one get formatted or did you just install over? if you install without formatting some old settings can get mixed in and interfere with the new settings, you could also start ubuntu in failsafe graphics mode (choose the 2nd option, recovery kernel from the grub menu when booting and then choose to start in failsafe graphics mode) and then try to deactivate and then activate the proprietary driver or instead of the hardware drivers program you could use synaptic package manager to reinstall the nvidia/ati graphics card driver

as for fan speeds i usually just monitor the temperatures of my gpu and cpu through a conky script which i have run on my desktop 
but if you want to control the fan speed i did a quick search for fan control in the repos and theres a program in there that will allow you to control your fan speeds, you can also goto somewhere like gnome-look.org and see if they have any applets with that functionality :)

---

### Post by Newbie1979 on 2011-02-03
Hello again!

I took the cover off and titled the computer together with a strong flashlight. The fans are running but very very slow. I really do hope that they gear up if needed but I dont know how to test that...

> **khamil8686 said:**
> glad to help :)
the program to activate proprietary drivers probably just has a variable somewhere that is set when a driver is activated instead of manually checking if all files are present so that might by why it will still say you have a driver activated when you moved the xorg.conf
if you deleted the xorg.conf file and want to get the graphics back there is probably a xorg.conf.backup file somewhere in the same directory, i think whenever a proprietary driver gets activated it makes a backup of the original and the new xorg.conf in case problems ever arise and the user needs to restore them, im not sure why after a new install of ubuntu and installation of the propriety driver gives you a blank screen on reboot, only things i can think of are when you installed ubuntu again did the old one get formatted or did you just install over? if you install without formatting some old settings can get mixed in and interfere with the new settings, you could also start ubuntu in failsafe graphics mode (choose the 2nd option, recovery kernel from the grub menu when booting and then choose to start in failsafe graphics mode) and then try to deactivate and then activate the proprietary driver or instead of the hardware drivers program you could use synaptic package manager to reinstall the nvidia/ati graphics card driver


Ok, tanks for the advices and info :)
I have reinstalled Ubuntu 3 times in total. Upon the last installation the screen didnt turn black/blank however when I and activated the  proprietary drivers. But when I tried to open Catalyst Control Center I got this message:
"No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."

That is why I followed the manual configuration of xorg.conf
But after that the command: "aticonfig -<some attribute>" did not work. I got this message:
"aticonfig: No supported adapters detected"
That is also why the conky scripts doesnt work since they are using "aticonfig" as I understand it.

Do I have some kind of a weird mix of proprietary and open source drivers installed?

> **khamil8686 said:**
> 
as for fan speeds i usually just monitor the temperatures of my gpu and cpu through a conky script which i have run on my desktop 
but if you want to control the fan speed i did a quick search for fan control in the repos and theres a program in there that will allow you to control your fan speeds, you can also goto somewhere like gnome-look.org and see if they have any applets with that functionality :) 

Oh, this is way over my knowledge... I dont know what the "repos" are. I will try the gnome-look.org.

Thank you very much for you answers! :)

---

### Post by khamil8686 on 2011-02-03
yes the gnome-look.org applets you can add to your desktop (you can also try to look for gDesklets which are widgets and things you can add to your desktop but ive never used these, or you can search for screenlets that have this function and i have used screenlets before) that is probably the easiest way to monitor your gpu temperature. and when you activate the proprietary drivers im not certain that it will install the aticonfig tool from amd for you and i dont think aticonfig from amd will report that you have a driver installed since it was installed the ubuntu way instead of the ati manual way so you could have it installed and working and that program just doesnt think you have it installed. there is a version of the ati control center in the repos (a repo is a repository, its where ubuntu keeps all its stable and tested software for download by users, any program you download using synaptic package manager is from a repo :) that is called fglrx-amdcccle that you could download and see if it detects that you have the proprietary driver installed and see if it provides that aticonfig hardware temperature monitoring option

for the conky script using aticonfig program to report temperatures, you could see if the lm_sensors program picks up your gpu temp and then create your own script that cuts out everything except the desired temp reading from the output of the scripts program and then put that script in your home directory
```
${execgraph /home/khamil8686/temp1.sh}
           Temp 1 - ${exec /home/khamil8686/temp1.sh}/127°C
${execgraph /home/khamil8686/temp2.sh}
           Temp 2 - ${exec /home/khamil8686/temp2.sh}/60°C
${execgraph /home/khamil8686/temp3.sh}
           Temp 3 - ${exec /home/khamil8686/temp3.sh}/127°C

```
is what the bottom of my conky script looks like, this runs the scripts temp1.sh, temp2.sh, and temp3.sh to output the temperature sensors readings of my cpu

heres what one of my scripts to cut out all the output except the temperature reading from the sensors script looks like
```
#!/bin/bash
sensors | tail -n 5 | head -n 1 | head --bytes 16 | tail --bytes 2
```

---

### Post by Yellow Pasque on 2011-02-03
> **Newbie1979 said:**
>  I have followed and completed this guide (by editing xorg.conf)

The guide installs Catalyst 10-11 (which is from November). If you installed that version, remove it: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

Then, install the latest Catalyst. It may fully support your card: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

If not, the card will probably be fully supported in the next Catalyst release (11-2).

---

### Post by Newbie1979 on 2011-02-07
Now everything works :)!

Thank you very much for your kind and instructive help! Great with a forum which have so many members that knows a lot and are very helpful. Indeed a good start at this forum to me!

Thanks again :)

---

