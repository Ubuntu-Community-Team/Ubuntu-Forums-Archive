---
title: "nVidia on Ubuntu 7.04 Questions"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by ToyImp on 2007-09-02
I am running an nVidia 7600 GS running the restricted drivers. My first question is, should I update my drivers and second is, When I reboot my resolution is always at 1024x768x75Hz. I have to set 1440x900 resolution manually and what I want is so that it will automatically be set to 1440x900x75Hz. Any information on this would be greatly appreciated. Thanks in advance.

---

### Post by CRCarl on 2007-09-02
I can't tell you if you need to update your drivers without knowing what version you are running now.... :)

If you are absolutely sure that your monitor can handle 1440x900 then modify your /etc/X11/xorg.conf file.

FIRST BACK IT UP - 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.modifying.modes.backup
```

Fine the "Screen" section, then the SubSection "Display"; modify the modes line - 

```
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
```

Save your changes, press ctrl-alt-backspace to restart X.

If that does not work, restore the backed up xorg.cong file.

C

---

### Post by ToyImp on 2007-09-02
The resolution worked thank you very much. As far as the drivers are, I am running version 96. I know the most recent ones are 100.x but just wondering if its worth installing them. I know how to do the installation, but not sure if it worth it or not. Thanks again.

---

### Post by cdekter on 2007-09-02
Generally speaking, with nVidia drivers the motto is, if it ain't broke, don't fix it. They do have a tendency to introduce bugs in their drivers, whether on Windows or Linux. So if you are not having any problems with performance/stability/functionality, I would stick with the driver you are currently using.

---

### Post by ToyImp on 2007-09-03
Awesome thank you so much for the help.

---

