---
title: "VLC &amp; Totem run poorly in jaunty"
date: 2009-04-26
forum: Multimedia Software
---

### Post by The Pinny Parlour on 2009-04-26
Performed an upgrade... all went smoothly.  Play back in previous version was fine on the system I have, now is is poor.  I can run movies in both VLC and Totem but soon it will become seriously frame skipping and image and sound pauses.  

Anyone have a similar experience, and you have solved it... please reply.

Thank you.

I should note that I have reinstalled the Medibuntu packages as per their website.

---

### Post by amor0fati on 2009-05-04
I have the exact same problem.  Seemed to work fine shortly after the upgrade, but now skips.

---

### Post by riza hylviu on 2009-05-04
hi
what video card do you have? i have an intel video card and i had the same issue, so i downgraded the driver to intrepid's version and it worked for me

---

### Post by binbash on 2009-05-04
what is your video card?

---

### Post by amor0fati on 2009-05-04
I have an Nvidia, and trying to downgrade the driver definitely did not work--exact same problem.  Now I've got another problem, it won't let me reactivate my driver, I can't get out of low graphics mode, and I lost my second screen.

---

### Post by amor0fati on 2009-05-04
I followed this:
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
    1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
    4.a) Add "nvidia" without quotes to the list.
    4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
    5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
    5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
    7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
    7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
        -------------------------------------------------------------------------------------------------------
        If you used Envy to attempt a previous nvidia install please run this command now before you go on:

        sudo envy --uninstall-all 
        sudo dpkg -P envy 
        sudo envyng --uninstall-all
        sudo dpkg -P envyng
        In Depth Instructions on Envy and EnvyNG install/uninstall [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu)




        -------------------------------------------------------------------------------------------------------
        If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

        sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

        -------------------------------------------------------------------------------------------------------
        If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

        sudo nvidia-installer --uninstall

        -------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
    8.a) Okay were in Command Line only now, we have a little left to do in here.
    8.b)login:
    8.c)Password:

9) sudo /etc/init.d/gdm stop
    9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
    10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
    11.a) Answer to the affirmative for all questions.
    11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
    11.c) If you somehow answered incorrectly on the last question in the installer then:
        c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
    12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     [http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)
```

But the install failed and I can't even see any drivers in Hardware Drivers.  Plus VLC is running the same way as it was before.  I'm running an e-GeForce 8400 GS.

---

### Post by amor0fati on 2009-05-05
I got my driver problems fixed, but VLC had the same problems throughout; so somehow I doubt that it's a driver problem.

---

### Post by amor0fati on 2009-05-11
The last update seemed to fixed my problems.

---

### Post by amor0fati on 2009-06-11
My problems were fixed for a while but now I've got sound cutting in and out with VLC, video getting behind the sound and having to race to catch up in totem and flash video, and to top it all off, now my color's all screwed up on my second screen!

---

