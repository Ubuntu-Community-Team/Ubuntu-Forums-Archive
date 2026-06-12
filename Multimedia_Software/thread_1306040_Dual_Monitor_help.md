---
title: "Dual Monitor help"
date: 2009-10-30
forum: Multimedia Software
---

### Post by toddbmobile on 2009-10-30
I have a hp desktop I just installed 9.10 on. I am using the restricted video driver 185 for Nvidia. The Nvidia utility will config and set up both monitors (Acer flat, 20' Dell CRT) like I want(Left of, Right of, etc), and even let me appy the changes. The bad new is when I click the save to xconf file it wont save and gives me an error message. So when I reboot, I am back to only one monitor and I have to start the process all over again. How can I get the settings to stay?

---

### Post by pawhtiobo on 2009-10-30
Hi :)

Your xorg is write protected...that's the reason why you can't save the changes, i had also that problem, i solved it by changing the security properties of the **xorg.conf**, using the **sudo nautilus** code in the console and navigating to is location **etc\X11**. I think you can also launch Nvidia control panel in sudo mode, by typing **sudo nvidia-settings**, and maybe (not sure) in sudo mode it allows you to save changes to xorg.

See ya

---

### Post by themusicalduck on 2009-10-30
Best way to do it is to run nvidia-settings as root.

Easiest way to do this is to just press alt+f2 and in the box that appears type 'gksudo nvidia-settings' and hit enter.

---

### Post by toddbmobile on 2009-10-30
Thanks for the advise but I still can't get either suggestion to take. I changed owner to myself w/ read and write permissions for xconf file. When I save to it I get a window that pops up the message "Failed to parse existing xconfig file" and the path etc/x11. In the terminal window I get 

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen"

any other ideas? Please help....thank you in advance.

---

### Post by toddbmobile on 2009-10-30
I found the solution from johnnydopefish's website.

[http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html](http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html)

Below is the solution that worked:

The NVIDIA applet in Ubuntu 9.04 (works w/ 9.10 as well) will not write to the stock xorg.conf regardless of permissions set, and regardless of whether or not it's running as root.

Here's what I did to get around it:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-xconfig
sudo nvidia-settings

The first step creates a backup of your currently working xorg.conf file.
Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.

If this does not work then after step 1, do sudo rm /etc/X11/xorg.conf to delete your current xorg.conf file. Then run sudo nvidia-xconfig and sudo nvidia-settings. 

I hope this helps someone else.....:o

---

### Post by bcooperb on 2009-11-06
> **toddbmobile said:**
> I found the solution from johnnydopefish's website.

[http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html](http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html)

Below is the solution that worked:

The NVIDIA applet in Ubuntu 9.04 (works w/ 9.10 as well) will not write to the stock xorg.conf regardless of permissions set, and regardless of whether or not it's running as root.

Here's what I did to get around it:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-xconfig
sudo nvidia-settings

The first step creates a backup of your currently working xorg.conf file.
Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.

If this does not work then after step 1, do sudo rm /etc/X11/xorg.conf to delete your current xorg.conf file. Then run sudo nvidia-xconfig and sudo nvidia-settings. 

I hope this helps someone else.....:o

Thanks Todd! This fixed my prob. Even if I ran it as root I couldn't get it to save to the settings. I had followed a walkthrough on another post, but I think doing the "sudo nvidia-xconfig" is what worked for me! Thanks!

---

### Post by bcooperb on 2009-11-06
[U][COLOR="Silver"]Ok...so I can see my display on both windows now....but something odd. I can't share between my screens? My mouse will go back and forth, but I can't drag any windows or applications to the other screen? I have my **main monitor is a 24" Dell**...and then my system is a **Dell XPS m1730 laptop.**

I use to run 8.10 with this setup and compiz and dual screen worked just fine. 

Now when I try to do 3D Cube, only the main screen rotates 4 sided cube, if i move my cursor to the other screen(the laptop screen) it just rotates a 2side page front and back. Use to one screen ran to the next and it would rotate one large image.

I do have it set to Separate X screen...any advice?[/COLOR][/U]

I could have sworn it was Separate X screen i used last time! But no it was Twin View. That fixed it...with a combination of using the sudo nvidia-settings and deleting the old backup (always having the basic orginal one still handy) I just had to keep goign back and forth deleting the backups that nvidia-settings would make or it wouldn't save the next time i tried to make a change. All is good now.

---

### Post by mk4umha on 2009-11-15
> **bcooperb said:**
> [U][COLOR="Silver"]Ok...so I can see my display on both windows now....but something odd. I can't share between my screens? My mouse will go back and forth, but I can't drag any windows or applications to the other screen? I have my **main monitor is a 24" Dell**...and then my system is a **Dell XPS m1730 laptop.**

I use to run 8.10 with this setup and compiz and dual screen worked just fine. 

Now when I try to do 3D Cube, only the main screen rotates 4 sided cube, if i move my cursor to the other screen(the laptop screen) it just rotates a 2side page front and back. Use to one screen ran to the next and it would rotate one large image.

I do have it set to Separate X screen...any advice?[/COLOR][/U]

I could have sworn it was Separate X screen i used last time! But no it was Twin View. That fixed it...with a combination of using the sudo nvidia-settings and deleting the old backup (always having the basic orginal one still handy) I just had to keep goign back and forth deleting the backups that nvidia-settings would make or it wouldn't save the next time i tried to make a change. All is good now.


So do you have 2 cubes now? 1 per monitor? How did you make it work?

---

### Post by ChrisWebb on 2009-11-28
To get multiple cubes on the desktop use the Compiz Config Settings Manager (System-Preferences-Compiz Config Settings Manager). You may need to install this from Synaptic.

Under CCSM, go to "Desktop Cube" and change the Multi Output Mode to "Multiple Cubes".

The change is immediate :)

---

