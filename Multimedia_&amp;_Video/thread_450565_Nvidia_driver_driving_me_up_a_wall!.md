---
title: "Nvidia driver driving *me* up a wall!"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by Shadoglare on 2007-05-21
OK guys, this driver has about got me to the point where I'm thiking of just formatting the danged partition and starting over again. 

Back before doing the update to the latest Ubuntu, I had used Nvidia's installer, and the driver worked beautifully. 

Well, the update apparently felt it needed to update my video driver as well, and broke it (along with a few other things, but that's a different story). 

Anyway, it didn't work right after the update (my basic desktop worked OK, but any time I would try to run something with 3D it would crash & reboot X), so I tried to "downgrade" back to the driver that I knew worked... and thus it seems opened a major can of worms. 

I keep getting problems with x not wanting to start due to a conflict between the driver version and the kernel module version. What's especially weird is I get two different errors - if I let it go through a full boot and let it try to start x automatically to log on, it tells me the kernel module is a different version than when I do a "safe boot" and start to start it with just the startx command.

I've tried to clean everything having to do with nvidia off of the system, have tried installing a few different versions of the driver, have tried re-installing the drivers from the ubuntu distributions, and for the life of me I can't get the thing to work.

I tried over at the nvidia support forums and was basically told to read the FAQs... yeah, thanks guys, did that, doesn't answer my question *grumble*

So... anybody have any ideas before I format this sucker??

---

### Post by gwoodard on 2007-05-21
What model of card do you have? (Geforce, Vanta, or any others?)

---

### Post by dabl on 2007-05-21
No guarantee, but I would download and run the Envy script installer before I threw in the towel and started over.  It is here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

:)

---

### Post by click4851 on 2007-05-21
have generally the same problem, using a FX5900 MSI agp card, currently set to "nv", not sure what to do, use ENVY, try dowload/install from NVIDIA?

---

### Post by Shadoglare on 2007-05-22
> **gwoodard said:**
> What model of card do you have? (Geforce, Vanta, or any others?)

It's a GeForce FX 5200.

---

### Post by kingbuxton on 2007-05-23
I was messing for 5 days trying to get drivers on my 8800Gts

sudo apt-get install build-essential

sudo apt-get install xserver-xorg-dev

sudo pico /etc/default/linux-restricted-modules*

Change the DISABLED_MODULES=&#8221;" to DISABLED_MODULES=&#8221;nv&#8221;

Save the file and exit. Now you need to reboot your machine.

After reboot, download the proper driver package from the nVidia website and save it somewhere where you can easily access it.

Now you need to press Ctrl-Alt-F2 to open up a console and login

Use the following command to shutdown Xorg

sudo /etc/init.d/gdm stop

Now run the following command from the location where you saved the nV file.

sudo sh NV* (Where * is the full filename of the driver you just downloaded)

Run through the installer and tell it to update your xorg.conf for you.

Reboot once again (just type reboot at the console) and you should have full nVidia acceleration.

This was the one that worked for me.

---

### Post by Shadoglare on 2007-05-23
Wooo! \\:D/ Actually it looks like the disabled module edit was the only thing keeping mine from working... 
This actually *was* in nvidia's faq post, but it came *after* the steps that royally horked up the system :/

> **kingbuxton said:**
> I was messing for 5 days trying to get drivers on my 8800Gts

sudo apt-get install build-essential

sudo apt-get install xserver-xorg-dev

sudo pico /etc/default/linux-restricted-modules*

Change the DISABLED_MODULES=”" to DISABLED_MODULES=”nv”

Save the file and exit. Now you need to reboot your machine.

After reboot, download the proper driver package from the nVidia website and save it somewhere where you can easily access it.

Now you need to press Ctrl-Alt-F2 to open up a console and login

Use the following command to shutdown Xorg

sudo /etc/init.d/gdm stop

Now run the following command from the location where you saved the nV file.

sudo sh NV* (Where * is the full filename of the driver you just downloaded)

Run through the installer and tell it to update your xorg.conf for you.

Reboot once again (just type reboot at the console) and you should have full nVidia acceleration.

This was the one that worked for me.

---

