---
title: "Installing ATI Mobility Radeon 9600 M10 drivers"
date: 2010-07-20
forum: Multimedia Software
---

### Post by goldfish777 on 2010-07-20
Hello, I have ubuntu on a Vaio VGN-A290 with the ATI Mobility Radeon 9600 M10 graphics card. I I installed the Eternal Lands client but it keeps crashing on me. Upon crashing a massage told me that I should make sure the video drivers are up to date. I then went into system --> Administration --> Hardware drivers and it says "no proprietary drivers are in use on this system." So my question is how do I install a driver for the  ATI Mobility Radeon 9600 M10?

---

### Post by cascade9 on 2010-07-20
You cant. Well, if you want to use a much older version you could. 

ATI dropped support for the older cards in 2008. The only drivers for the 9XXX ATI cards on newer versions of ubuntu are the open source drivers.

---

### Post by goldfish777 on 2010-07-20
So what should I do?

---

### Post by goldfish777 on 2010-07-20
This is the error output:

Oh my, Eternal Lands Crashed - Don't Panic!

A few of things you can try:
1) Make sure your system is up to date, especially your video drivers.
2) If the client crashes repeatedly, try changing some settings.  Either by directly modifying the configuration file (e.g. gedit ~/.elc/main/el.ini). Or clicking the settings button window at the login screen.
    i) Enable the "Poor Man" option in the "Details" tab of the setting window.  Or edit the configuration file and set "#poor_man=1".
    ii) Disable the "Use animation program" option in the "Adv Video" tab of the setting window.  Or edit the configuration file and set "#use_animation_program=0".
    iii) Disable the "Custom Looks Updates" option in the "Server" tab of the setting windows.  Or edit the configuration file and set "#customupdate=0".

If you continue to have problems check the Eternal Lands forums, especially the "Help Me" and "Bug Report" sections.  If you post a message make sure you include information about your system; i.e video driver and version, operating system and version.  Make sure you check your error log for clues too and include the contents in any forum report.

The following is your error log contents.  Note it is overwritten each time you run the game.



Log started at 2010-07-20 10:03:59 localtime (EDT)

[10:03:59] Using the server profile: official
[10:03:59] Window size adjusted to 1014x713

---

### Post by cascade9 on 2010-07-20
There isnt much you can do. There might be PPAs with newer versions of the opensource drivers, but thats about it.

---

### Post by goldfish777 on 2010-07-20
ok thanks.

---

