---
title: "Ironhide problems"
date: 2012-01-22
forum: Multimedia Software
---

### Post by Welly Wu on 2012-01-22
I have an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 gigabyte Solid State Drive running Ubuntu 11.10 64 bit. I followed the directions to add and install Ironhide. My ASUS N61JV-X2 notebook PC has a Nvidia GeForce GT 325M GPU and Optimus technology. I know that Nvidia does not officially support Optimus in GNU/Linux environments. When I run the Ironhide configuration, I selected the first configuration that was tested on Ubuntu 11.04 by 21 other users and I also selected the XV (default). I do not see any graphics when it runs glxgears using my Intel HD or Nvidia GeForce GPU during the configuration. When I am in the terminal, I ran glxgears and glxspheres with and without the optirun command. I can see the graphics when it uses my Intel HD graphics card and it displays a rather decent frame rate, but when I run it with the optirun command, no graphics appear in the window, yet it tells me that I am getting well over 120+ frames per second. I am able to use Unity 3D and it is running just fine. How do I get the optirun command to function properly? I want to see the highly accelerated 3D graphics using my Nvidia GeForce GT 325M GPU.

What more information do you need for me to be of better help to the community?

How do I solve this problem?

Thank you for your help.

---

### Post by Welly Wu on 2012-01-22
I rebooted my ASUS N61JV-X2 notebook PC and I ran the Ironhide configuration again. This time it worked. The reboot made all the difference. I can run glxgears and glxspheres with and without the optirun command and I see graphics on my screen albeit the optirun command makes the graphics go much much faster. Now, I can not run my Ironhide Application Settings. When I launch it in Dash, nothing happens. How do I solve this simple problem so that I can assign my favorite software packages to use the optirun command and use my Nvidia GeForce GT 325M GPU?

---

### Post by Lekensteyn on 2012-01-22
Ironhide is deprecated, there is now Bumblebee: [http://askubuntu.com/a/36936/6969](http://askubuntu.com/a/36936/6969)
This version does not have a UI for configuring programs to be run with the nvidia card yet, work is in progress for that.

For now, either use the terminal with "optirun yourprogram" or edit the menu items and prepend "optirun" to it.

---

### Post by Welly Wu on 2012-01-22
I read that Bumblebee 3.0 was recently released. Should I remove Ironhide and install Bumblebee? I had problems with the older version of Bumblebee and the X server not starting. I am having minor problems with Ironhide in that I can not select which software applications to use my Nvidia GeForce GT 325M GPU. I know that Ironhide is deprecated. What should I do?

---

### Post by Lekensteyn on 2012-01-22
You should indeed remove Ironhide. You can read the answer that I've linked before which also points to [http://wiki.bumblebee-project.org/Upgrading-on-Ubuntu](http://wiki.bumblebee-project.org/Upgrading-on-Ubuntu)

---

### Post by Welly Wu on 2012-01-22
Okay. I completely removed Ironhide by following the directions and I installed Bumblebee 3.0. I rebooted my ASUS N61JV-X2 notebook PC. I tested glxspheres with and without the optirun command and it worked both times. I am getting 4 times the 3D graphics speed using my Nvidia GeForce GT325M GPU.

Bumblebee 3.0 works on my ASUS N61JV-X2 notebook PC running Ubuntu 11.10 64 bit.

Now, I have to include the optirun command for 3D graphics intensive software applications that can use the 3D acceleration from my Nvidia GeForce GT 325M GPU such as Google Chromium. How do I make that change in the launcher and other software applications so I can just click it using my mouse within my Unity 3D interface?

I just switched to Ubuntu 64 bit less than two weeks ago so please be patient with me. Thank you.

---

### Post by Lekensteyn on 2012-01-23
Try copying the systemwide launcher, modify it and save it in your user-specific settings:
```
sed 's,^Exec=/,Exec=optirun -- /,' /usr/share/applications/chromium-browser.desktop > ~/.local/share/applications/
```
A re-login may be necessary.

---

### Post by Welly Wu on 2012-01-24
Is there a command line that I can type in to run optirun and the software application that I wish to use with my Nvidia GeForce GT 325M GPU so that I do not have to have an open terminal running at all times for the software application to keep running?

---

### Post by Lekensteyn on 2012-01-25
> **Welly Wu said:**
> Is there a command line that I can type in to run optirun and the software application that I wish to use with my Nvidia GeForce GT 325M GPU so that I do not have to have an open terminal running at all times for the software application to keep running?
You can open a run dialog and type the optirun command in, nothing fancy ;) The other way is to run optirun detached like this:```
optirun yourprogram &
```

---

