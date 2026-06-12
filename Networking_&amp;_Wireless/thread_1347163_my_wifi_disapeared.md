---
title: "my wifi disapeared"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by Nailox on 2009-12-05
Im on wire now. it was working just fine some days ago and now there is no wifi icon at all. what happened and how do i fix my wifi?

---

### Post by wilee-nilee on 2009-12-05
You may have removed the notification area it is in add to panel, right click on panel then add to panel.

---

### Post by sgosnell on 2009-12-05
You're going to have to give us more information than that.  Nobody on here is psychic, and we can't read your computer through the intertubes.  Could you have disabled your wifi some way?  Is the wireless radio on, or at least the indicator?  Have you made any changes to your panel?  Lots of things are possible, but it's hard to know where to start with no information other than 'it doesn't work'.

---

### Post by Nailox on 2009-12-06
the wifi radio is on, the indicator is on, there is the bluetooth icon on the panel but no network icon at all.. be4 it used to show the type of connection like wire, wifi , etc. i can't remember making any changes on the panel. I right click > add to panel but I can't find it.. what's the name of the item ? i tried "network" but it didn't find it ?

---

### Post by QwUo173Hy on 2009-12-06
You can start this applet by typing the command:

nm-applet

---

### Post by sgosnell on 2009-12-06
If the wifi isn't working on your computer, there will be no wireless icon on the panel.  Just because the light is on, it doesn't mean that it is actually working.  There could be a problem with the driver, or with the hardware.  

If your run 'nm-applet' in a terminal, and get ```
** (nm-applet:9065): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3
```then the network manager applet is running, and you just don't see the icon in the panel.  If that's the case, you have a wireless problem.  If it runs, then it has been removed from the panel, and you can put it back through System/Preferences/Startup Programs, using a custom launcher with 'nm-applet' in the command box.

---

### Post by sgosnell on 2009-12-06
Can you post the output of ifconfig and iwconfig?

---

### Post by Nailox on 2009-12-07
this is when i enter nm-applet in terminal

** Message: <info>  No keyring secrets found for Auto redman&methodman/802-11-wireless-security; asking user.


(nm-applet:2243): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 3: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;
** (nm-applet:2243): DEBUG: foo_client_state_changed_cb
** (nm-applet:2243): DEBUG: foo_client_state_changed_cb

if i close the teminal the thing says its still got procesess in it and the connection is lost. I check in startup applications and there is no network manager ? is this the problem ?

---

### Post by sgosnell on 2009-12-07
You may have a corrupt network manager.  Try removing it and reinstalling via Synaptic, or with apt-get, whichever you're comfortable with.

---

### Post by Nailox on 2009-12-14
when i remove the nm applet, i will be offline.. so will i be able to install it again since Im offline ?

---

### Post by QwUo173Hy on 2009-12-14
Good question. I can't tell you for certain, but if I were in your position, I would try connecting with ethernet. I would also download the network manager .deb file and have a local copy before you uninstall. That way you can install it even if you do loose your connection.

See here [http://packages.ubuntu.com/search?keywords=network-manager](http://packages.ubuntu.com/search?keywords=network-manager)

---

### Post by Nailox on 2009-12-19
I have the package on my hdd now but i cant uninstall it with 
> sudo apt-get remove NetworkManager

how to proceed?

---

### Post by coffeecat on 2009-12-19
> **Nailox said:**
> I have the package on my hdd now but i cant uninstall it with 

> sudo apt-get remove NetworkManager                      how to proceed?

That's because the package name is 'network-manager', not 'NetworkManager'. But don't uninstall it without making sure you have the appropriate .deb packages in /var/cache/apt/archives. A safer way would be to open Synaptic and mark network-manager for reinstallation. That way Synaptic will download any deb packages it needs before it does the re-installation.

---

### Post by sgosnell on 2009-12-19
You need to remember that Linux is not Windows, and that commands and application names are case-sensitive, and have to be exact.  I agree that using Synaptic is the best way to add or remove programs.  The add/remove applet is a rather poor substitute, but it usually works.  Synaptic gives more control, and lets you see more of what is happening,  Apt-get is ok, but you have to know the exact package name before you can do anything, while Synaptic lets you browse the available packages using many different views, or search for term, in the package names or in the descriptions.  System/Administration/Synaptic Package Manager opens it.

---

### Post by Nailox on 2009-12-19
i was stupid enough to go to synaptic and mark network manager and wpa_supplicant for complete removal and hit apply :( :( :( now Im netless... b4  that i had downloaded a package called network manager somting.deb and after i removed nm and wpa from synaptic, i tried installiing this package with GDebi installer but it says it cant fetch some things from some rep.. how was I suppose to know that after i had downloaded the package it will STILL require internet connection to be installed - thats really confusing for a linux beginner like me.. how can i bring the www back in my sweet home ?? (Im in a net cafe now)

---

### Post by Nailox on 2009-12-22
bump - please read my last post

---

### Post by coffeecat on 2009-12-22
Gdebi is asking for some dependencies that network manager needs. Dependencies are other packages that are normally downloaded by the package manager. But, of course, since you have uninstalled network manager, there is no way of downloading these packages. You have also uninstalled wpa-supplicant which means that you cannot now connect to your wireless network from the terminal. You could, in theory, download the deb for wpa_supplicant, but that will probably need a whole load of dependencies as well.

Finding and downloading all the deb packages for the dependencies and making sure one was getting the correct versions would be time-consuming for an experienced user. It is going to be far quicker to simply reinstall Ubuntu.

Backup your personal data and reinstall. Seriously - it will take less than an hour. And put this unfortunate episode down to a learning experience. Tell yourself not to uninstall stuff unless you know exactly what you are doing.

---

### Post by Nailox on 2009-12-22
most of the time idk what Im doing and this is how I learn.. until that unfortunate day.. I tried to reinstall ubuntu but when I inserted the cd nothing happened and idk what should i start.. how to start the re-installation ?

---

### Post by coffeecat on 2009-12-22
> **Nailox said:**
> I tried to reinstall ubuntu but when I inserted the cd nothing happened

How did you originally install Ubuntu to that machine? Is the BIOS set to boot from the CD drive before the HD? Have you used that CD before?

---

### Post by Nailox on 2009-12-22
oops.. forgot that i set the machine to boot from usb first .. thanks I will try it and hopefully write my next post from my own hardware

---

### Post by coffeecat on 2009-12-22
Good luck!

---

