---
title: "Cant change resolution on 8.04 install"
date: 2008-05-06
forum: Mythbuntu
---

### Post by paeron on 2008-05-06
Hi, 

I just installed mythbuntu 8.04 which was really easy.
I got everything (i think) set up, except for one thing that bugs me...

I cant change the screen resolution all I got is 640x480 and 320x240 :-(

I use a leadtek Geforce 8500GT and the nvidia 169.12 driver on an amd_64 system installation.

Anyone got a clue on what I'm missing??

Cheers / P

---

### Post by warp99 on 2008-05-06
> **paeron said:**
> Hi, 

I just installed mythbuntu 8.04 which was really easy.
I got everything (i think) set up, except for one thing that bugs me...

I cant change the screen resolution all I got is 640x480 and 320x240 :-(

I use a leadtek Geforce 8500GT and the nvidia 169.12 driver on an amd_64 system installation.

Anyone got a clue on what I'm missing??

Cheers / P

In the Mythbuntu-Control-Centre there should be an application called 'nvidia-settings' or 'Nvidia Control Panel" or something similar to that so you can set up the card to change resolutions. If not you can do it directly using the 'nvdia-settings' program.

If you don't have the program already install the 'nvidia-settings' application from the 'universe' repositories through apt-get or Synaptic. Once installed open a terminal and issue 'sudo nvidia-settings', make the changes you want, then use the 'Save to X Configuration' dialog and save the file to /etc/X11/xorg.conf. Press ctrl+alt+backspace to reload xserver and you should have the resolution you want that your hardware is capable of producing.

---

### Post by paeron on 2008-05-06
> **warp99 said:**
> In the Mythbuntu-Control-Centre there should be an application called 'nvidia-settings' or 'Nvidia Control Panel" or something similar to that so you can set up the card to change resolutions. If not you can do it directly using the 'nvdia-settings' program.

If you don't have the program already install the 'nvidia-settings' application from the 'universe' repositories through apt-get or Synaptic. Once installed open a terminal and issue 'sudo nvidia-settings', make the changes you want, then use the 'Save to X Configuration' dialog and save the file to /etc/X11/xorg.conf. Press ctrl+alt+backspace to reload xserver and you should have the resolution you want that your hardware is capable of producing.

In the nvidia-settings all I got is the 2 options mentioned above 640x480 & 320x240...

This is the core of my problem, I dont know how to "get more resolution options" in the nvidia-settings?

is it possible to do the settings directly into the xorg.conf?
if so, how?

Cheers / P

---

### Post by superm1 on 2008-05-06
These resolutions are typically populated from EDID information.  See /var/log/Xorg.0.log for errors about reading the EDID.

---

### Post by warp99 on 2008-05-06
> **superm1 said:**
> These resolutions are typically populated from EDID information.  See /var/log/Xorg.0.log for errors about reading the EDID.

If there are some errors the OP may have to manually set the information by choosing a "generic" monitor in the display dialog. I had to do this with my Niko 22" monitor because it could not read the correct EDID. Somewhere along the line this corrected itself and started to show the EDID info, but I'm not sure when.

---

### Post by paeron on 2008-05-06
> **warp99 said:**
> If there are some errors the OP may have to manually set the information by choosing a "generic" monitor in the display dialog. I had to do this with my Niko 22" monitor because it could not read the correct EDID. Somewhere along the line this corrected itself and started to show the EDID info, but I'm not sure when.

That solved it!
Thx, I set the display to generic & 1024x768 Lcd.

Cheers / P

---

