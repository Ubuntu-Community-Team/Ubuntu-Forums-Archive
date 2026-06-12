---
title: "nvidia driver problemos"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by electroconvulsive on 2006-07-11
My Ubuntu machine has a nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) video card <(from lspci output). I installed the nvidia driver following the instructions on [www.ubuntu guide.org](www.ubuntu guide.org) using the commands: 
[COLOR="Red"]sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable[/COLOR]
After restasrting X Unsucessfully I was led to the command prompt where I logged in and executed the command: 
[COLOR="Red"]dpkg-reconfigure xserver-xorg[/COLOR] 
and reconfigured X back to its defaults for the video card etc. But since doing this one or two apps have reported an inability to draw waveforms (mixxx was one). During the installation of the nvidia driver it said that it backed up a file for the video settings which I cannot remeber what it was and of course I didnt take any notice as I believed at the time that everything was going to run smoothly and I really would like to restore that backup file so if can anyone tell me the name of the file it would help a little. Also I would like to know why the installation of the nvidia driver didnt pull off. Was I installing the right driver? Do I need to update Dapper? or is there something else that wasnt mentioned at [www.ubuntu guide.org](www.ubuntu guide.org)? 

As usual any help would be appreciated.

---

### Post by MonkeyNet on 2006-07-11
nVidia drivers can be a tricky one to install properly.

I followed an excellent HOWTO located [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") and apart from having to tweak a couple of settings (running an old GeForce4 MX 440) everything worked well

The file that you are talking about that was backed up could be the xorg.conf file

Have a look in /etc/X11/ and see how many copies of xorg.conf there are. I always copy this file to xorg.backup whenever I make changes.

See how you go

Andrew

---

### Post by tseliot on 2006-07-11
> **electroconvulsive said:**
> Was I installing the right driver?
No, you need the legacy driver.

Please, follow MonkeyNet's suggestion

---

### Post by electroconvulsive on 2006-07-12
Yeah thanks man the driver has loaded up but I still cant seem to get the control panel to load. I followed the guide that you provided but there was no enty in the problems section concerining the control panel. I can bring up the settings from terminal. Anyway Im going to try to add it manually using alacarte. 
Correct me if im wrong about this but I think that maybe in the file
[COLOR="RoyalBlue"]/usr/share/applications/NVIDIA-Settings.desktop[/COLOR]
[COLOR="Red"]Type=Application Categories=Application;System;[/COLOR]
Should read [COLOR="Red"]Type=Application Categories=Application;System;Administration;[/COLOR]

---

### Post by tseliot on 2006-07-12
> **electroconvulsive said:**
> Yeah thanks man the driver has loaded up but I still cant seem to get the control panel to load. I followed the guide that you provided but there was no enty in the problems section concerining the control panel. I can bring up the settings from terminal. Anyway Im going to try to add it manually using alacarte. 
Correct me if im wrong about this but I think that maybe in the file
[COLOR="RoyalBlue"]/usr/share/applications/NVIDIA-Settings.desktop[/COLOR]
[COLOR="Red"]Type=Application Categories=Application;System;[/COLOR]
Should read [COLOR="Red"]Type=Application Categories=Application;System;Administration;[/COLOR]

[COLOR="Red"]If you used Method 1[/COLOR], here's a quotation from my guide:
> 6) Create a link to the &#8220;Nvidia-Settings&#8221; Panel in your application menu:
file.pngCode:

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop


OR (if you use KDE)
file.pngCode:

kdesu kate /usr/share/applications/NVIDIA-Settings.desktop


NOTE: do not worry if the file is empty

Insert the following lines into the new file:
file.pngCode:

[Desktop Entry] Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon=
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;


Save the edited file.

Log out and press CTRL+ALT+BACKSPACE (so as to restart the xserver). 


[COLOR="Red"]If you used Method 2 or my script[/COLOR]:
just Log out and press CTRL+ALT+BACKSPACE (so as to restart the xserver) and you should be able to see Nvidia-settings in the Menu.

---

### Post by electroconvulsive on 2006-07-12
Oops my bad. I will be a little more observant next time. Thanks for your help.

---

