---
title: "Ubuntu 8.04 changing Nvidia graphic card to ATI Radeon, Problems?"
date: 2010-01-06
forum: Multimedia Software
---

### Post by TelcontarVI on 2010-01-06
Hi, i'm going to change my old Nvidia Graphic card wich runs very well in Ubuntu by an ATI HD Radeon 4770. 

Will Ubuntu recognize it when i plug it and start the computer, will Ubuntu reconfigure by itself?... or i'm going to have problems like not to be able to start the X server and only be able to enter to the console.

Need i to remove the nvidia graphics driver before to plug in the new card?

I have downloaded a program called Envy, which is supposed to reconfigure ubuntu properly... it's ok?

Finllay, can i backup the curent configuration so that if the new card is not well installed i can return to the old without problems?

P.D Sorry for my bad english, but un the spanish ubuntu forums nobody answer me.

---

### Post by markbuntu on 2010-01-06
This is not particularly simple but no drastic trouble will result if you follow these few simple steps exactly. Do not use Envy.

First remove the nvidia driver completely, this depends on how you installed it. If you used Synaptic then use Synaptic to remove it, If you used Envy, remove it with envy. If you installed it from the nvidia site follow their directions for removing it. It is very important that this driver be completely removed since it has replaced many files that are incompatible with other drivers and will cause you problems.

Reboot into recovery kernel from the grub  menu and use the fix x option. continue the boot and verify that the VESA driver is being used by checking in the var/log/Xorg.0.log. This will be low graphics but do not panic, it is a necessary and temporary step.

Shut down the machine and remove the nvidia card and install the ati card. Once again boot into recovery kernel and use the fix x option. This should get you a working desktop with the VESA driver and your new card.

Reboot again as normal this time. Go to the ati site and download the latest driver from ati to your desktop or wherever. (You can do this in advance if you want.) Be sure to get the proper linux driver.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Right click on the file and choose properties/permissions and check the execute box to allow the installer to be executable.

Open a terminal and navigate to whever you put the file (ie cd Desktop) type in the terminal

sudo sh ./ati-driver-installer-whatever the rest of it is

The installer will start, if it asks anything just click OK.
After the installer finishes running in the terminal do

sudo aticonfig --initial

reboot

The Catalyst Control Center will be in your menu. Use it to configure the driver/displays etc. Do only one thing at a time. If the super user catalyst does not start from the menu just type

sudo amdcccle

from a terminal.

good luck

Do not use older ati drivers, they are not aware of that card and will not work. You should only use the latest 9.12 driver from ati.

If you have any problems come back here and we will give you help.

---

### Post by TelcontarVI on 2010-01-06
Many thanx in advance, i'm only preparing the change (i haven't bouhgt the card yet), but 'im going to print your instructions and follow it step by step

Only one thing i haven't used envy to install the nvidia drivers ubuntu asked me if i want to use restricted drivers and i say yes... so that i must uninstall them by synaptic, no?

I have enter synaptic and the nvidia modules i have installed are:

nvidia-glx-new
nvidia-kernel-common

To uninstall i only have to uncheck them and aply changes, no? ¿Are there more modules which i'm missing?

---

### Post by markbuntu on 2010-01-06
You should choose to remove them completely. Right click on them and you should see that option.

---

### Post by TelcontarVI on 2010-01-07
Ok, i found the option, thanks again :)

---

### Post by TelcontarVI on 2010-01-17
Thx Markubuntu, i 'have succesffully change my graphic card with your instructions.

---

### Post by markbuntu on 2010-02-05
Once you install the card if you run into any trouble you may need to reinstall alsa so it can automagically detect the card and get the proper driver set up for it. Then reboot. Other than that you should have no problems.

---

