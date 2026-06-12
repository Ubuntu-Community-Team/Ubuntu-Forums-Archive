---
title: "Permission denied"
date: 2008-10-27
forum: Multimedia Software
---

### Post by DarkLion on 2008-10-27
I am trying to stop flicker from happening every time I start Blender or watch video in full screen. This is what I get in terminal:

tom@tom-desktop:~$ /etc/X11/xorg.conf    Driver "fglrx"
bash: /etc/X11/xorg.conf: Permission denied
tom@tom-desktop:~$     Option "VideoOverlay" "off"
bash: Option: command not found
tom@tom-desktop:~$     Option "OpenGLOverlay" "on"
bash: Option: command not found
tom@tom-desktop:~$ /etc/X11/xorg.conf Section "Device"                                                  Driver "fglrx"
bash: /etc/X11/xorg.conf: Permission denied
tom@tom-desktop:~$     Option "VideoOverlay" "off"
bash: Option: command not found
tom@tom-desktop:~$     Option "OpenGLOverlay" "on"
bash: Option: command not found
tom@tom-desktop:~$     Option "TexturedVideo" "off"

How would I get permission that is required for this to work and does anyone think it is the drivers or not? I do not wish to switch back to Windows and am still learning Ubuntu. I am running Hardy Heron 2.6.24-21-generic. It also says  Package xserver-xgl is not installed. If this is the problem then how would I obtain xserver-xgl? I appreciate any and all the help that I receive.

---

### Post by ad_267 on 2008-10-27
I think what you are trying to do is edit the /etc/X11/xorg.conf file and add those lines.

First do a back up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
sudo means run the command as root so that you have privileges to write to the /etc/X11 directory.

Then to edit the file:
```
gksu gedit /etc/X11/xorg.conf
```
gksu is the graphical version of sudo.

Anyways I don't know if editing the xorg.conf file is really a good idea unless you know what you're doing.

It sounds like you could be having problems because of comiz-fusion, which controls the desktop effects. Try going to System - Preferences - Appearance - Visual Effects and setting them to none.

To install xserver-xgl you can go to System - Administration - Synaptic Package Manager and search for xserver-xgl then mark it for installation. I'm not sure whether you need this or not though.

---

### Post by DarkLion on 2008-10-27
I thank you much for the information. Setting the visual effects to 0 did work. Now I don't have to think about Windows! LOL. I appreciate the information again and am glad it was a simple fix. May you have a good evening.

---

### Post by ad_267 on 2008-10-27
Thanks, glad I could help. The desktop effects are really nice if everything works smoothly but sadly there's often issues like this where they don't work well with other applications. 

If you do want some basic eye-candy like shadows or need compositing for something like gnome-do or a dock like AWN you can always use compositing with metacity as explained at [http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

---

