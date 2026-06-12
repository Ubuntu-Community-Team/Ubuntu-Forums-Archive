---
title: "Nvidia 7600gs doesnt work"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by nin82 on 2006-09-05
I was wondering if any of u could help me with this.

I just upgraded my graphix card becuase I had the ATI Radeon 9600se and was never able to get it running with the 3D accelerator due to the wonderfull support ati has for linux... so i got the BFG Nvidiva  7600 gsoc 512 in order to solve my problem.

so i took out my ATI and dropped in the Nvidia, did everything that was suggested under the UBUNTU guide in order to get it running except for the "sududo gedit /etc/share/NVIDIA-settings.desktop" becuase it gave an error since the gui wasnt working i guess it said samething about that. so i did it with VIM and went ahead and added the lines or more like i created the file since there wasnt one.

so I rebooted the system everything was running great no fails during the loading screen of ubuntu but once its done loading and tries to switch over to Gnome or the GUI it freeezes on the blackscreen with the white dash(stops blinking)!!!!. so i dont know what to do anymore. this is the second time i have had to post since i got Ubuntu Breezy Badger. I usually get all my answers from previous posts, but if i missed this one Im very sorry and i would appreciated if one of u could send me in the right direction!!!!

this is what i did

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

* Insert the following lines into the new file

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

and did not worked. right now I am runnign it with the vesa drivers!

THX a lot for ur help guys xD!!!!

---

