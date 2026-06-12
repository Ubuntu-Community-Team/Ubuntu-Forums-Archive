---
title: "Ati Drivers,  It can't be this hard......"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by 22350 on 2006-06-19
Ok, I am coming to the conclusion that I am just stupid.  Maybe someone can use pictures for me at this point.

it always seems that installing things in linux just don't work for me.....

I am using 6.06 and have been following the instructions on this site.

Per the instructions, i did the following:

1. downloaded the install package from the site (ati-driver-installer-8.25.18-x86.run)
2. installed gcc -3.4
3. drilled down to the directory holding the installer (on the desktop)
4. opened a terminal
5 ran (chmod +x ati-driver-installer-8.25.18-x86.run)
6. ran (fakeroot ./ati-driver-installer-8.25.18-x86.run)
7. makes a fglrx installer folder, then takes me into the ATI Installer
8. at this point, there is no guidence as to what to do.  there are two options:
        a.  Install Driver 8.25.18 on X.Org 7.0.x
        b.  generate Distribution Specific Driver Package

9.  I tried both, 
        a.  the org option does an install by itself. it tells me that it doesn't have permission to install in the director.  it then suggests that i go to expert mode, which doesn't exist.  i assumed it meant custom install.  i selected all the modules and proceeded.
        b. the distribution specific option drops a bunch of folders on the desktop.  when i try and install them, it gives me a myriad of errors, like: "there is a newer version online", "there is a conflict with a file by the same name"

10.  when i perform both types of installs,  i get a message telling me to "Save my X Window configuration file"  I don't know what that means.  it would be nice if they didn't assume that you understood that. It also mentions that there is a log file in a directory /usr/share/fglrx.  it is there.

11. next it tells me to run "aticonfig", so i do it. this fails, of course.  this is what the terminal spits out:

paul@paul-laptop:~$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

then i tried something different, per the terminal's suggestion:
aticonfig --initial --input=/etc/X11/xorg.conf

got the same result.

I am not sure what i should expect here.  i think i am supposted to end up with a regular ati control panel that will let me adjust this device.

I have to admit that the page that gives you this instructions on how to do this, starts off by tell us how easy this is.  i find that frustrating.

any ideas what the hell is going on here.

does it really need to be this hard??

---

### Post by dcatdemon on 2006-06-19
You need to invoke *sudo* before your *aticonfig* commands, it'll prompt you for your password before invoking aticonfig as you'll need root access to your /etc/X11 directory.

e.g **sudo** aticonfig --initial

As for your points on how to go forward after getting the ati driver, you'll have to do this:

[FONT="Courier New"]X_VERSION=x690 fakeroot ./ati-driver-installer-<version>.run[/FONT]

This is because Dapper comes with **X 7.0.x**

2. The choose "**generate Distribution Specific Driver Package**" which you have done.  Do not choose the other one.

It is normal to indicate that there is a new version out there running because you are actually downgrading the ati driver version as compared to that in the repository.  To turn that off, I'll just launch Synaptic, search for every instance of fglrx and under Package->Lock version.  That will exempt these packages you have installed for updates.

I got help from here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

And I managed to get my ati drivers downgraded and running (at least quite normally O:)  ).  

One caveat about this way of installing ati drivers though, is that everytime there is a kernel upgrade, you would probably need to do this:

[FONT="Courier New"]sudo module-assistant build,install fglrx-kernel[/FONT]

and remove your previous fglrx-kernel package if you so deem fit via Synaptic.

I agree, it's hard to go through all these mumbo jumbo just to get the best out of your hardware.  It shouldn't have happened and I think this affects quite a bit of other people using ATI cards as well, at least its better than when linux first started ;) .

HTH.

k-leb.

---

