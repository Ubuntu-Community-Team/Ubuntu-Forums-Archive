---
title: "Crossover tablet/desktop: Should I use Ubuntu or Ubuntu Touch"
date: 2014-03-21
forum: Mobile Technology Discussions (CLOSED)
---

### Post by zhangweiwu on 2014-03-21
Ubuntu Touch description says it is for tablet. I have a tablet, but it is 11inch big with a pedestal and for 70% of the time I am sitting straight in front of it with a seperate keyboard, doing LibreOffice speadsheet editing, GIMP and a lot of console programming work. Yet I expect it to replace my newspaper, kindle reader and sheet music (not to play music but to display sheet music when I am playing an instrument), so yes I intend to use it as a tablet too.

When 14.04 comes out, should I download the Ubuntu, or the "Ubuntu Touch for x86 tablet"?

FYI: the 11 inch tablet device is bModo 11.

---

### Post by grahammechanical on 2014-03-21
Does this tablet have hardware that Ubuntu can run on? I think that is the first question to answer.

Ubuntu developers intend to converge Ubuntu Touch for phones and tablets with Ubuntu for desktops and laptops. This will not happen in time for the release of Ubuntu 14.04 but it may arrive by the release date of Ubuntu 14.10 or Ubuntu 15.04 at the very latest. One day there will be one Ubuntu that will run on phones, tablet, PCs and TVs. 

Installing Ubuntu Touch on an existing mobile device is still classed as "experimental." This is because the main focus of development is to get the code ready for being used on retail devices pre-installed with Ubuntu.

In some ways installing Ubuntu on any device/machine is also a bit of an experiment. There can be problems. It depends a lot on what the present operating system is and what the OEM has done to the BIOS/UEFI and hard disk.

I can tell you this: Ubuntu 14.04 will not be upgraded with the converged code base. It will not be until the release of 16.04 that an LTS release will get the converged code base.

So, If you install 14.04 desktop and Touch better suits your needs than you should upgrade to 14.10 and then 15.04 when they are released. If you install the Touch version you should expect to do image upgrades because the code is still under development and image upgrades is what is done in Ubuntu Touch.

To be frank I am not sure if Gimp will run on Ubuntu Touch. I have heard that Gimp interacts directly with the Xserver. Well, 14.04 will use the Xserver and Unity 7 throughout its 5 years support period. But Touch is already running on Mir and Unity 8 and that is what 14.10 and 15.04 will be running on. Time will tell if programs like Gimp can be made to work as well with Mir as they do with Xserver. But as Mir and Unity 8 are not yet on Ubuntu desktop and no one would think of running Gimp on a mobile phone device I do not think that much work been done on making Gimp ready for Mir. That is all in the future.

Regards.

---

### Post by zhangweiwu on 2014-03-21
Thank you. So clear and detailed is your answer!!

So the idea is clear that I should use Ubuntu 14.10 the desktop edition, and bare with it the short-comings of touch-control, e.g. no right mouse click (Windows emulates it with a prolonged press) and hard to scroll while reading (the scroll bar is usually out of reach and sweeping the content won't move it), and hope Ubuntu Touch in 14.10 deliver the "converged code", which I assume meant integration of the two worlds.

I can give up GIMP, and leave it to my dusted desktop computer, but from your description I am sure I am heading towards a lot of trouble trying to make my old tool-set (rxvt, libreoffice and 100+ other desktop tools) to work on Touch. I can as well go across the bridge, adapting my desktop usage pattern towards a mir-friendly set, e.g. switching from the X11 tool rxvt to Gnome Terminal, so I use the same tools on and off desk - but I better do so when the other side is stable and well supported.

Alternative idea is to dual-boot the machine with another Touch-ready OS. Windows 8 is a bad option, 'cos it takes 16GB out of the 32GB SSD when it only cover a small set of usage (the kind of thing that takes the advantage of a large portable display: reading, browsing and sheet music displaying. Mobile usages are reserved to my android phone: weather info and chatting). Sailfish OS is perhaps too young and not reported to work on this device (the hardware is basically WeTab with 11inch screen, every other detail configuration matches). Firefox OS? I wish they are well adapted to this x86 hardware, need to check. Android? Perhaps won't be easy to get it work on this x86 device, anything require +3hour hacking is not going to work for me.

Alternative of the alternative is to find tools that allows me to sweep browsing and reading window while staying on the Ubuntu desktoip distribution boat.

---

### Post by grahammechanical on 2014-03-21
Imagine this. A Ubuntu phone that plugs into a hub which is connected to a monitor and a mouse and a keyboard and now the Ubuntu phone is a fully functional Ubuntu desktop PC with all the phone applications available as well as the desktop applications. And if the monitor is a touch screen monitor then the phone swipe gestures will work as well. That is the vision of a converged Ubuntu. 

Desktop Ubuntu already has support for what is called multitouch. And it has a very good on screen touch keyboard called Onboard. I do not have a touch screen monitor so I would have to use mouse clicks. We can activate it in System Settings>Accessibility.

[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

[https://apps.ubuntu.com/cat/applications/precise/onboard/](https://apps.ubuntu.com/cat/applications/precise/onboard/)

I am not sure if there is an ISO image for Ubuntu Touch on x86 architecture. There is another idea that I would like to present to you. Those of us on this section of the forum use the development branch. At the moment we are using Trusty Tahr (14.04 soon to be) but when 14.04 is released and development work starts on 14.10 we shall move our 14.04 installations over to the 14.10 development branch. Keep an eye on this section of the forum and see how well 14.10 is running you might want to convert 14.04 to 14.10 and get the converged code as it is put into the development branch.

Right now we can install the phone core apps on the desktop by using a PPA. Some of us tried this a few months ago but the apps were very lacking in features. Things are a lot better now. And I am going to put in another installation of Trusty Tahr and install the core apps and see how they work. So, if you do install 14.04 on that device you might want to do the same.

This video is an advertisement to be sure but it is still interesting and you will find something of interest to you towards the end of the video. And Remember, this is not two separate Ubuntu operating systems (one for mobile and one for laptops/desktops) but one Ubuntu.

[https://www.youtube.com/watch?v=h384z7Ph0gU](https://www.youtube.com/watch?v=h384z7Ph0gU)

Regards.

---

### Post by zhangweiwu on 2014-03-21
> "I am not sure if there is an ISO image for Ubuntu Touch on x86 architecture. "

There is a pre-installed image, as good as ISO image for experienced users: [http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/)

I just watched the youtube commercial. The new UI is brilliantly designed. I am tempted to run it as dual-boot, but I heard what you say and won't do it until 14.10. Give developers some time and I am not able to spare the focus to report bugs hence is not going for development copies. I'll keep hoping. I will be tempted to buy a phone with Touch preinstalled, once they are shipping. And I will be using desktop edition as long as I can get by.

Thanks!

---

### Post by grahammechanical on 2014-03-22
I been trying to remember something I heard at the recent virtual Ubuntu Developer Summit that was relevant to using the Gimp on Mir and Unity 8. The relevant points are at 5 mins and 9 mins into this session. It is a progress report on the development of Mir which is the display manager which is used in Ubuntu Touch and which will replace the Xserver, LighDM and Compiz on the desktop when convergence is complete. And that will not happen for 14.04 but 14.10 or later.

[http://summit.ubuntu.com/uds-1403/meeting/22188/mir-updates/](http://summit.ubuntu.com/uds-1403/meeting/22188/mir-updates/) 

There are slides. Look for references to Rootless Xapp support. That is what is needed for using programs like the Gimp. It is described as in progress. Another reference is Rootless X phase 1 on Mir. It has been moved from being in 14.04 to being ready for 14.10.

So, some work is being done in making everything that we use at present in desktop Ubuntu to be available in Converged Ubuntu.

Regards.

---

