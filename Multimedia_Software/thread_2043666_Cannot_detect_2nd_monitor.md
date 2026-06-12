---
title: "Cannot detect 2nd monitor"
date: 2012-08-17
forum: Multimedia Software
---

### Post by CJ_Hudson on 2012-08-17
Hi, in the 'Displays' box I can't get Ubuntu to detect my second monitor.
Plus it seems to think the PC is a laptop, which is strange.
I have NVidia Ge Force 8400 and using the HDMI output for the second monitor and the DIV-X port (with a VGA adapter) for 1st, using the proprietory driver.
Thanks in advance for any assistance.

---

### Post by CJ_Hudson on 2012-08-21
Bump.

---

### Post by beboylips on 2012-08-23
Are you using nVidia proprietary driver or the ones included with Ubuntu on fresh install?

---

### Post by CJ_Hudson on 2012-08-27
Hi, thanks for your response.
I am using NVidia proprietory driver.
Dual monitors works fine in both the other dual-boot Windows installations on the same desktop so I doubt it's a hardware issue.
By the way I would like the two displays "cloned".

---

### Post by CJ_Hudson on 2012-08-28
Bump.

---

### Post by CJ_Hudson on 2012-09-08
Bump.

---

### Post by CJ_Hudson on 2012-09-19
Oh I get it, can't comment because p.d.s frowned upon eh?
By the way its an Nvidia 8400 GS 256 Mb graphics card. 

:lolflag:

---

### Post by BicyclerBoy on 2012-09-19
Okay I give in 3 weeks is long enough.. & what is p.d.s ?

You can't use the "Displays" tool with any of the proprietary drivers. (think the **latest** nVidia randr changes might let it work)

Use the nVidia-settings tool from terminal or unity search thing..

The DVI-I port with VGA adapter is denoted as crt0 or crt1 etc

---

### Post by CJ_Hudson on 2012-10-03
What I meant by P.d.s. is *proprietory drivers*.
So they are the culprits.
Thanks for your help.

---

### Post by BicyclerBoy on 2012-10-03
Not sure you can draw that conclusion..

It is possible nVidia made it very hard for the gnome display tool to work because of their (nVidia) complicated modeline reporting..
This modeline reporting has changed in drivers >=302 series.

Just use:
nvidia-settings 
it is a GUI & should be in the menus (non unity) etc..You can stick any running application on the unity menu strip..

---

### Post by CJ_Hudson on 2012-10-03
Thanks will try that.

EDIT:
Hmmm.... actually I think this is solved (for me at any rate) here: [http://ubuntuforums.org/showthread.php?p=12276247#post12276247](http://ubuntuforums.org/showthread.php?p=12276247#post12276247)

EDIT: That Nvidia control panel is a nightmare- I tried for hours and could not get two cloned monitors in operation!

---

### Post by CJ_Hudson on 2012-11-25
Sorry to multiple post however I am still having difficulties.
When I use the Nvidia GUI to try and set up the dual monitors, nothing happens even though I have all the settings correctly assignated.
Using the built-in "Display" utility in Ubuntu when I click on "Mirror displays" I get my main monitor in a hopeless resolution. Have not checked what happe4ns to the other screen because it's in another room and I don't want to stick with these settings!
I think my only option is to purge the proprietory driver and use the Nouveau one. Please could someone instruct/direct me to appropriate instructions? Thanks in advance.

:guitar:

---

### Post by BicyclerBoy on 2012-11-25
The gnome "display" tool does not work with nVidia driver..except possibly for the latest version..
Just don't use it..

When you install the nVidia driver you need to logout/login to activate (X server limitation).

If additional drivers offers an older version (175..xx) try that..
I doubt the later driver makes any difference for the old cards.
The 8400GS is bit limited by memory & clock speed & feature set A.
VDPAU video decode recommends min 512MB.

From memory the clone screen requires twinview enabled..

---

### Post by CJ_Hudson on 2012-12-02
Thankyou.

---

### Post by dannyboy79 on 2012-12-03
i am running 10.04.4, having trouble getting my current geforce 6200 working with ANY drivers. All the nvidia propreitary drivers result in my TV (vga hookup) into DPMS SUSPEND, so I trying to get teh nouveau driver to work since it works in 12.04.1 ubuntu from a live usb, its 1440x900

Anyway, back on topic. I ordered an 8400 gs from newegg last night, which drivers are you using with your GeForce 8400 GS? I will only need to power 1 display, an Olevia 23" TV which has a VGA port or an HDMI, I'll probably use the HDMI port because it will allow greater resolution I would think. Do you use HDMI?

---

### Post by CJ_Hudson on 2012-12-19
I am using the proprietory drivers, but think I might try the noveau ones again if I could find out how to purge the prop. drivers.
EDIT: Also, by the way, when I get a moment (v. busy right now with accountancy exams!) I am going to install 64 bit Ubuntu, so not sure which drivers are/aren't available there. :-)

---

### Post by dannyboy79 on 2012-12-20
> **MogBug said:**
> I am using the proprietory drivers, but think I might try the noveau ones again if I could find out how to purge the prop. drivers.
EDIT: Also, by the way, when I get a moment (v. busy right now with accountancy exams!) I am going to install 64 bit Ubuntu, so not sure which drivers are/aren't available there. :-)using the nvidia gui, you need to make sure you start it with gksudo so it can write to the xorg.conf file. so it would be
```
gksudo nvidia-settings
```

I gave up on the geforce 6200, i believe it was a hardware issue, overheating so I went with a 8400 GS and using the nvidia binary from their website, 310.19 and it's working great but I don't run a dual display like you.
GOod luck

PS I am running xubuntu 12.04 64 bit

---

### Post by BicyclerBoy on 2012-12-20
It can be a bad idea to launch apps as sudo; for one thing it changes the user home folder.
nvidia-settings should prompt for the sudo password if & when it tries to save to xorg.conf..

Most people do not need any xorg.conf file & it can cause problems.

nvidia-settings needs "user" r/w access to 'home/"user"/.nvidia-settings-rc

---

### Post by dannyboy79 on 2012-12-20
> **BicyclerBoy said:**
> It can be a bad idea to launch apps as sudo; for one thing it changes the user home folder.
nvidia-settings should prompt for the sudo password if & when it tries to save to xorg.conf..

Most people do not need any xorg.conf file & it can cause problems.

nvidia-settings needs "user" r/w access to 'home/"user"/.nvidia-settings-rci didn't say to launch it with sudo, i said to launch it with gksudo, when you make changes with nvidia-settings, you have to launch it with gksudo in order to write to the xorg.conf file otherwise it gives you a permission error when trying to save xorg.conf.

---

### Post by CJ_Hudson on 2012-12-21
Well I installed 64 bit 12.04 and it's running sweet.
However I still have a display problem- when I first booted both panels were at the resolution of the bigger of the two panels, causing chaos on my desktop. I had to physically unplug the bigger of the two panels to get it to work.
Now I have just switched the bigger panel off completely. Is there a control panel for the Nouveau driver somewhere?
EDIT:
Oh yeah, also I forgot, when I boot, inbetween the splash screen with the Ubuntu logo and the log-in screen, I get random coloured lines across the screen (almost like you sometimes get whilst experimenting with overclocking a CPU but less intense. Just a few coloured lines in horizontal bars across the screen.) Not sure if this is because I had to unplug the 2nd monitor whilst installing 12.04 64-bit?)
EDIT #2: Just to clairify the Gnome control panel does not allow a higher resolution than the standard for monitor #1 (1280 x 800,) which is the default for that monitor,) so of course when I clone the monitors I am effectively using a quarter of the available desktop in the smaller monitor, which makes the desktop unusable. There must be a way to set the bigger panel at a bigger resolution than the default? Or maybe the graphics card is just not capable of this.
EDIT #3 Sorry about all these messy edits. :-)
Aha! I have now discovered the screen only goes into oversize mode whilst entering your machine password after  booting up. I don't need to unplug anything, because once you have entered the password correctly, the screen reverts back to correct resolution and positioning, with the smaller of the two monitors as prime. (The other one is in the other room and I use it for watching You Tube videos etc.)

By the way Ubuntu 64 bit installed now with default Video driver.

---

### Post by CJ_Hudson on 2013-02-03
Just had accountancy exams (which I passed) hence not been active in this topic for a while.
Ubuntu can duplicate the displays using the Displays control panel (tick button for Mirror Displays,) but apparently the only resolution available is 640 x 800 which doesn't work with my configuration.
Any sugestions?

EDIT: Tried with Nouveau driver as above, didn't work, so tried porprietory driver again (this time in 64 bit Ubuntu) and got the following error mesage when I started the Nvidia control panel:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by Bucky Ball on 2013-02-03
*Thread moved to **Multimedia & Video**.*

... seeing as you're still here. Frankly, you might be better re-posting in this sub-forum with your current situation. And remember; wait twenty four hours before bumping threads. You may have known that but just in case. Better luck this time. ;)

---

### Post by CJ_Hudson on 2013-02-03
A:D ha working okay now with prop. driver. Selected Clone Displays, Twin View configuration and tweaked second monitor settings to get all the gubbins on screen. A-OK ! Cheers guys.

---

### Post by Bucky Ball on 2013-02-03
Great news! Enjoy. ;)

---

