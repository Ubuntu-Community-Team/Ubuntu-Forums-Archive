---
title: "Require Better Display Resoltion"
date: 2009-06-29
forum: Multimedia Software
---

### Post by opm595 on 2009-06-29
My old 15" CRT monitor died (yeah, nothing fancy around here :)) and a friend gave me a working, much larger screen, Compaq P1220  as a freebie to help me out. However, I can't get my resolution to be any more then 960 x 600. Is there anything I can install to fix this? 

Thanks in advance.

Regards,
Rob

---

### Post by jargoman on 2009-06-29
You probably already tried the obvious but rebooting the system with the monitor plugged in might do the trick. 

Other than that you could edit your /etc/X11/xorg.conf. Make sure you make a back up first. However misconfiguring that file could render your system without graphics and You'll need to know your way around the command line to replace the backup. Or you'll need to use a livecd to replace the backup.

a google search for "xorg resolution ubuntu" might lead you in the right direction.

You should only edit that file to a resolution your monitor can handle. If you post your current xorg.conf then myself or someone else may be able to help you further.

---

### Post by opm595 on 2009-06-29
Thanks for the response and advice.
I checked my /etc/X11/xorg.conf and strangley it's absolutely empty. I mean zippo'- not a thing in it. That can't be a good thing, right?
I did a Google search, as advised but nothing really there either.
However the rest of my system is working fantastically well. Just the monitor resolution is a bit of a pain. 
Anyway, thanks for your help on this.

---

### Post by jargoman on 2009-06-30
Actually that's not so bad since you don't an xorg file to mess up in the first place. Without an xorg.conf then xorg will just autodetect your hardware and use the default settings. You can generate an xorf file automatically with...

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
   
but you'll need to reboot your computer in recovery mode and log into a console session because xorg can't detect your hardware properly while Xorg is running. 

If after running that command you can't log into a normal graphical environment again, all you gotta do is reboot your computer in recovery mode again and rename the file to something else so it isn't used. Xorg will go back to autodetect.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.didntwork
```


You could also try editing this one to your needs. 
```

#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa" 
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"

        DefaultDepth    32

        SubSection "Display"
            Depth        32
            Modes      "1024x768"  "960x600" "800x600" "640x480 #resolutions!
        EndSubSection

EndSection


```

```

Driver "vesa" 

```

Is the line specifying your video card driver. The "vesa" driver is a basic failsafe driver. You should look in your xorg log and try and see what driver you've been using. /var/log/messages/Xorg.log or something.

You could also look into installing non open source proprietary drivers. Recommended if you have a newer Nvidia. 

If you don't know what card you have try this command
```
lspci | grep VGA
```

---

### Post by jargoman on 2009-06-30
After writing all that I closed the programs I had running and just noticed something. 

System > Preferences > Display > Detect Monitors  !!!

lol....

---

### Post by opm595 on 2009-07-03
Many, many thanks for your time and effort, Jargoman.
However, after investigating and acting upon the information you've supplied here (hence the delay in this response) I feel I maybe beating the proverbial 'dead horse'.

> System > Preferences > Display > Detect Monitors !!!
I did try this but nothing was detected, therefore the information in your first post prior to this, was most valid and useful.

As instructed, I toyed around and adjusted my Xorg.conf file accordingly, but this was to no avail. I reviewed my Xorg.log, and running lspci  | grep gave me:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

Armed with this information I then did some further Googling and after reviewing several other forums and sites about this it seems that SiS and Linux aren't a real good combination. It seems many others have had my exact same headache . This further led me to the SiS site ([www.sis.com](www.sis.com)) where I downloaded, supposedly a Linux compatible diver, [ sis_drv.o-402 ]  - a binary file. However, I'm still in the process of learning how to install such a file as this. Although, according to what I have read so far, this too is quiet a challenge. 

Once again, thank you so very much for your time, effort and assistance on this matter.

Best regards,
Rob

---

### Post by coffeecat on 2009-07-03
> **opm595 said:**
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

Now that you've discovered that SiS chipsets are somewhat less welcome than an infestation of cockroaches, what's your budget like? If you can afford one, you'll save yourself a load of blood, sweat, tears and heartache by replacing that card with an nvidia one. It wouldn't have to be state of the art. Something modest like a Geforce 6200 or a little better would be fine. Your resolution would be autoconfigured and if you installed the proprietary 'nvidia' driver, you'd be able to get all the compiz bells and whistles. Just be sure whether that's a PCI or AGP slot for the card.

---

### Post by opm595 on 2009-07-03
Thanks for the tip, Coffeecat.
Step a head of you, though. I thought if it's any consolation from the time and frustration I've spent on this, I'm eyeing up a whole new system. 

One that's all so Ubuntu Linux happy. And I'll definitely take your advice and make sure it has the Nvidia card for sure ;)

Cheers,
Rob

---

