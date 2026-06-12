---
title: "Unable to create new X config backup file - &quot;/etc/X11/xorg.conf&quot;"
date: 2009-02-04
forum: Multimedia Software
---

### Post by Sillywombat on 2009-02-04
Hi, i have been using ubuntu 8.04 for a while now, and have been using my X server for a dual screen setup for a while. 

But then °°flash, bang, horror:!:°° My graphics card goes. Iv since replaced it, and gave my pc a new install, again, 8.04. Card is a nvidia GeForce 7600 GT. (nvidia drivers installed)

Everything went well, until i tried to change my screens into seperate X screens, which requires the X server to restart. Easy right? But i cant seem to rewrite my xorg.conf file, or my backup xorg.conf file. Meaning if i do restart the computer, im left back at the start.

Error message is [PHP]"Unable to create new X config backup file '/etc/X11/xorg.conf.backup'"[/PHP]

I checked it out, and it seems i can only change the file via root. How would one do that?
Any help on this would be great, iv been fiddling for a few days to no avail.

---

### Post by Vadi on 2009-02-04
Use alt+f2 and "gksu nvidia-settings" to launch it as root - it'll then be able to write to the file okay.

---

### Post by meldon12 on 2009-02-17
> **Vadi said:**
> Use alt+f2 and "gksu nvidia-settings" to launch it as root - it'll then be able to write to the file okay.

yeaahh, thank you so much, i has the same problem but your solution work !!!

greetings !!!

meldon12

---

### Post by Sillywombat on 2009-02-20
Sorry, couldnt say thank you. was abroad.

But yes, it does work. Thank you so much, your a life saver!

---

### Post by Vadi on 2009-02-20
Cool, glad it helped.

---

### Post by CyberZilla1 on 2009-04-03
This not working for me :-| Did the alt f2 thing ... pressed enter and nada... wtf?
Don't tell me 'enter' don't work! Got a nVidia 6800 vid card and want the 2nd monitor to keep working after restart.. uggh. Why is everything so cryptic in Linux?

---

### Post by Arch enemy on 2009-04-17
I just installed Jaunty Jackalope and your solution worked right for me too. But now I'm experiencing OS hang-ons, and I've got the latest Nvidia drivers.
In anyway, thanks from Spain.

---

### Post by city-17 on 2009-09-06
:P Thanks for the solution

---

### Post by city-17 on 2009-09-06
I think a better idea would be to append the 'gksudo' to the menu entry.

In other words, find the menu entry for Nvidia X server settings and edit the command field so that it reads 

```
gksudo /usr/bin/nvidia-settings
```

The advantage of this is that this setting will remain fixed as opposed to having to use alt f2 every time you need to modify something

---

### Post by MohanaRao on 2009-09-29
Hi friends

When i am trying change my display settings using sudo nvidia-settings i am getting the following errors through your ideas.
ERROR: Cannot open display 'Mohan:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/home/mohan/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 36 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 37 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 38 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 39 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 40 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 41 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 42 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 43 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 44 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 45 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 46 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 47
       of configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 48 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 49 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 50
       of configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       51 of configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).

^C
mohan@Mohan:~$ sudo nvidia-settings

ERROR: Cannot open display 'Mohan:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/home/mohan/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 36 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 37 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 38 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 39 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 40 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 41 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 42 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 43 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 44 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 45 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 46 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 47
       of configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 48 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 49 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 50
       of configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       51 of configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52 of
       configuration file '/home/mohan/.nvidia-settings-rc' (no Display
       connection).

---

### Post by pdwOnline on 2009-12-02
> **meldon12 said:**
> yeaahh, thank you so much, i has the same problem but your solution work !!!

greetings !!!

meldon12

[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] Heey... This is what keeps Linux from taking the Windows world. 
When a user needs to open a command prompt, you're out. Command lines should be reserved for world lost tech hobbyists instead of users.

Now, how to solve this then?  Well, first of all, the VMware installation should install the stuff in that way that is actually works in the first place. But I have had this problem in the past. I changed the security settings for this config file. Something unexplainable as "sudo chmod 777 /etc/X11"   (shht, don tell the security purtistics..)

Still it sucks, because this command line is involved again, but al least it is a one time operation.

[IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG] When will it finally be possible select the option "run as root" from all the menu´s..

---

### Post by webchimp on 2010-01-20
Worked for me. Using 9.10 on an old 6600 card.

Just got a nice new HD TV after a couple of years of squinting to read stuff on an old CRT, and the display kept reverting to 1024x768 when I re-started the machine because I couldn't save this file.

Will look into upgrading gpu now I have a decent display.

---

### Post by markackerman8@gmail.com on 2010-03-22
I have a new problem when saving after a new install of 9.10.

"Unable to open X config file '/etc/X11/xorg.conf' for writing."

And I thought I would tell you my solution.  After selecting "Save configuration file", in the new window select "Show Preview", and copy over the contents of file with

#gksudo gedit /etc/X11/xorg.conf

---

### Post by Nikos.Alexandris on 2010-03-29
> **markackerman8@gmail.com said:**
> I have a new problem when saving after a new install of 9.10.

"Unable to open X config file '/etc/X11/xorg.conf' for writing."

And I thought I would tell you my solution.  After selecting "Save configuration file", in the new window select "Show Preview", and copy over the contents of file with

#gksudo gedit /etc/X11/xorg.conf

I do (currently) the same. Still, this is not a solution to the "bug" [*].

Regards, Nikos

---

[*] [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/477309](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/477309)

---

### Post by ingeon on 2010-04-08
> **markackerman8@gmail.com said:**
> I have a new problem when saving after a new install of 9.10.

"Unable to open X config file '/etc/X11/xorg.conf' for writing."

And I thought I would tell you my solution.  After selecting "Save configuration file", in the new window select "Show Preview", and copy over the contents of file with

#gksudo gedit /etc/X11/xorg.conf

I have been using Karmic_64bit on my machine for a while now and everything was fine,
could write xorg.conf using sudo no problem.
I then upgraded from nvidia 185.18.36_amd64 to nvidia-195.36.15_amd64
and had an issue getting past the libvdpau issue.

Yesterday i tried this new nvidia driver on another machine fresh install
with Intrepid and Karmic (both_32bit) and get the same issue "can`t parse xorg.conf"

I followed the two links below with apparently "solved" but my issue remains on both machines...

[http://ubuntuforums.org/showthread.php?t=1321327]("http://ubuntuforums.org/showthread.php?t=1321327")

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1382171]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1382171")

---

