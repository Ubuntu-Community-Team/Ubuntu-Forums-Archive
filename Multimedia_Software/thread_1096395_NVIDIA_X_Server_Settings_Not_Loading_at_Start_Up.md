---
title: "NVIDIA X Server Settings Not Loading at Start Up"
date: 2009-03-14
forum: Multimedia Software
---

### Post by AaronRGod on 2009-03-14
I used the NVIDIA X Server Settings application to set my resolution to 1440x900 and save the necessary information in my xorg.conf file, but the settings are being ignored at start up and I am forced to set them again manually.

Here is my xorg.conf file, as written by the application:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L194WTX"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by overdrank on 2009-03-14
Hi and are you using ```
gksu nvidia-settings
``` if you are using gnome to save the settings.

---

### Post by AaronRGod on 2009-03-14
No. There is a button in the Server Settings application that saves the settings in to xorg. Do I also need to use the command that you have provided?

---

### Post by overdrank on 2009-03-15
> **AaronRGod said:**
> No. There is a button in the Server Settings application that saves the settings in to xorg. Do I also need to use the command that you have provided?

Hi and sorry for the delay, but yes you will need to use root with the nvidia-settings for the settings to apply and save. :)

---

### Post by AaronRGod on 2009-03-15
No luck with that command. The settings still are not being applied until I load the application, and even then, I have to respecify the resolution that I want.

---

### Post by overdrank on 2009-03-15
> **AaronRGod said:**
> No luck with that command. The settings still are not being applied until I load the application, and even then, I have to respecify the resolution that I want.

Ok I am having a similar issues with my new laptop and only being able to use the nvidia 177.xxx driver. I see you are using a GeForce 8800 GTS, which driver (and how are you installing it) are you using?

---

### Post by AaronRGod on 2009-03-15
I am also using the 177 driver, which I installed through the Hardware Drivers application.

If it matters for any reason, I am currently running the 'Windows Install' version of Ubuntu.

---

### Post by lxowle on 2009-05-05
I have this problem - did you manage to fix it?

I have ensured that my xorg.conf file has been updated by the NVIDIA X Server Settings dialog. The login window has the correct resolution, but when I login the resolution defaults to 1024x768.

I'm running an nvidia 8800 GT card - newly installed on an existing ubuntu system.

---

### Post by AaronRGod on 2009-05-05
I did not actually figure out a solution; instead, I just moved Ubuntu to my IBM Thinkpad, which of course does not have a 8800 GTS like my desktop, so I do not have any Nvidida settings to worry about.

---

### Post by lxowle on 2009-05-05
Thanks anyway - for now I've just written a little script to change it to the correct resolution. If anyone has the EDID file for a Samsung 226bw (gained from a VGA connection), could they please let me know? I suspect that that will probably fix it.

---

