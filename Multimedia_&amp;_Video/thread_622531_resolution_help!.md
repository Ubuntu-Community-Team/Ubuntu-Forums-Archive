---
title: "resolution help!"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by tyle6 on 2007-11-24
OK, so im pretty new to linux here. im trying to change my resolution to 1280x1024. I do not have this option under screen resolution :confused: i know the monitor supports it. its what i run in windows all the time.

---

### Post by mouseboyx on 2007-11-24
Under screens and graphics change your monitor to a LCD 1280x1024 even if this is not your monitor it will allow you to change the resolution.

---

### Post by Yellow Pasque on 2007-11-24
We're going to need a little info.
What kind of video card do you have? Run:
```
sudo update-pciids
lspci | grep "VGA"
```
Also, post your /etc/X11/xorg.conf file in a [ CODE ]  (no spaces between the brackets) block please.

---

### Post by ijason on 2007-11-24
you'll need to edit your xorg.conf. to be sure it has the resolution you want as an option.

open a terminal and go to /etc/X11
> sudo cp xorg.conf xorg.conf.back
this will make a back-up of the file. 

then edit xorg.conf with an editor of your choice and down at the bottom where it says 
> Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1920x1200" "800x600"
        EndSubSection
EndSection

you want to make sure your screen resolution is listed. so it would say:
     Modes "1280x1024"

don't worry if the device name is different. it will be whatever brand your video card is.

---

### Post by tyle6 on 2007-11-24
im running a 7800gt right now. I dont even know how to get my Xorg file right now guys.
I haven't used linux in soo long and the last time was a just a brief touch with sabayon.
This same issue actually ended things for me and her. lol

---

### Post by mikewhatever on 2007-11-24
sudo cat /etc/X11/xorg.conf

and post the output here please.

---

### Post by tyle6 on 2007-11-24
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
looks like i need to install my drivers LOL

---

### Post by tyle6 on 2007-11-25
ummmm any ideas>?

---

### Post by Yellow Pasque on 2007-11-25
> **tyle6 said:**
> ummmm any ideas>?
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

---

