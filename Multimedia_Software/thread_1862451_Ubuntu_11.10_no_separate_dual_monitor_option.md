---
title: "Ubuntu 11.10 no separate dual monitor option"
date: 2011-10-16
forum: Multimedia Software
---

### Post by Tom77 on 2011-10-16
I have Win 7 and no problem using dual monitors i split-screen mode.  
Ubuntu 11.10 loads fine and gives me a mirror image on the second monitor.
System Settings Hardware>Additional Drivers Shows ATI/AMD proprietary FGLRX graphics driver active.

Display shows a single monitor with the mirror display applied. Uncheck the mirror display and shows dual monitors BUT when I select apply receive this message "The selected configuration for displays could not be applied:required virtual size does not fit available size: requested=(2560, 1024), minimum=(320, 200), maximum=(1280, 1280)

What do I have to do to get the dual monitors separated?[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by wihenao on 2011-10-16
Same problem over here.  No dual monitor.

---

### Post by olamaekle on 2011-10-17
Same here, only mine is maximum=(1920, 1920) (probably because my res is 1920 x 1200).

---

### Post by vaughany on 2011-10-17
Same problem here. The thing is, I swear it was working after first install of 11.10, but next day, after boot-up, it doesn't.

No idea what happened!

---

### Post by weelk on 2011-10-17
Have the same problem with ATI HD4870X2 also cannot finalize driver installation.
Another thread on failed installation [here]("http://askubuntu.com/questions/50611/trouble-installing-additional-driver/67967#67967")

For me it was working fine after upgrade to 11.10. I think it might be a problem with compiz. Once I wanted to change some settings I've lost unity immediately so was forced to terminal and unity --reset and everything came back to normal. Each time I change anything in compiz manager unity fails and have to reset it. Then Restarted and can only have mirrored displays. 

requested=(3840, 1200) maximum=(1920, 1200)

I have also added to xorg.conf

    Virtual        3840 1200

but no luck so far. ](*,)

----------[Update]-----------

I've got Multi-monitor desktop (not mirrored) only when I uninstall ATI binary X.Org driver fglrx 2:8.881-0ubuntu4 but then unity is not working in either 2d or 3d mode.

---

### Post by osarusan on 2011-10-17
This happened to me too, and the solution was simple.

Run ```
sudo aticonfig --initial

```
This will re-initialize your xorg.conf. Then when you reboot you should be able to active your 2nd monitor with ```
gksu amdcccle
``` and set it up correctly; or you may also be able to use the Ubuntu Display manager.

---

### Post by flakeman2 on 2011-10-17
osarusan's fix worked for me :) 

After running 'gksu amdcccle' I had to log out one more time but after getting back in I was able to go into System Settings -> Displays and uncheck 'Mirror displays' and it worked this time.

Thanks!

---

### Post by nozyczek on 2011-10-18
> **osarusan said:**
> This happened to me too, and the solution was simple.

Run ```
sudo aticonfig --initial

```
This will re-initialize your xorg.conf. Then when you reboot you should be able to active your 2nd monitor with ```
gksu amdcccle
``` and set it up correctly; or you may also be able to use the Ubuntu Display manager.

Worked, thx

---

### Post by Pioneer5000 on 2011-10-18
Thank you osarusan your fix worked for me as well. Thanks!

---

### Post by daneren2005 on 2011-10-18
Am I really the only one that didn't solve my problem for?  Using amdcccle doesn't actually apply the setting and then when i log out and back in only 1 monitor is working and then only a single monitor is being displayed as available.  I had to restore the backup xorg file

Edit: If anyone can provide me a copy of their xorg.conf after they got it to work that would be nice.  Especially if it is from a computer with AMD graphics

---

### Post by osarusan on 2011-10-19
-Did you run amcdddle with gksudo?
-Did you select Multiple Displays in the dispays option?
-Did you remember to hit apply?

Note that after applying you'll still have to restart the PC one more time. That should work for you.

Anyway, if not, here's my xorg. YMMV.

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x1200"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1600 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3280 1680
		Depth     24
	EndSubSection
EndSection

```

---

### Post by bembelritter on 2011-10-19
Many thanks, osarusan, for your fast and competent help []("http://ubuntuforums.org/member.php?u=167078")to this problem! :D

For me as total beginner - first time installing ubuntu instead of Win7 on my notebook - the boundless usage of two monitors is a critical factor in my decision of choosing ubuntu or not.

I followed your instructions and first the failure-message appeared again. But - after another reboot - it workes fine now\\:D/

---

### Post by Prodoc on 2011-10-19
> **daneren2005 said:**
> Am I really the only one that didn't solve my problem for?  Using amdcccle doesn't actually apply the setting and then when i log out and back in only 1 monitor is working and then only a single monitor is being displayed as available.  I had to restore the backup xorg file

I had the same issue at first. Using amdcccle I was able to activate the dual monitor set-up but the app disappeared right away, not allowing me to press OK on the following confirmation dialog. Not doing so will cause the settings to be restored again.

In my case the disappearing amdcccle issue occurred when I started it from the Dash. It did not happen when I started the app from the terminal, as osarusan mentioned using:

```
gksu amdcccle
```

> **daneren2005 said:**
> Edit: If anyone can provide me a copy of their xorg.conf after they got it to work that would be nice.  Especially if it is from a computer with AMD graphics

Be VERY careful using xorg.conf files from others. You can definitely NOT use them directly on your system. Several settings need to be adapted for your hardware.

---

### Post by osarusan on 2011-10-20
Glad to hear it works!

Prodoc is right, you really should be using your own xorg.conf. Mine is autogenerated and thus fairly generic, but you can see it is customized for my two monitor resolutions and refresh rates. You don't want to force your system to use incorrect resolution or refresh rates.

If you got amdcccle to work, it will automatically update your xorg.conf. Unfortunately with ATI you have to restart the system over and over again like with Windows... but once you get it working it's a huge relief.

---

### Post by weelk on 2011-10-21
@osarusan thanks for advice.  I managed to get the second monitor working but now gnome task bar is completely broken. Fonts are displayed as sqares the same with icons on the task bar. I run Gnome 3 and it seems like the task bar is overlayed with old style standard Gnome bar. 

I cant even take a screen shot because if I do it comes out as desktop background with only a cursor on it.

I'm currently using ATI/AMD proprietary FGLRX (post-release updates) I will try to use the other driver and see what happens. But for now it is #-o

Here is my xorg.conf

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3840 1920
        Depth     24
    EndSubSection
EndSection
```

---

### Post by osarusan on 2011-10-23
That sounds like either a package problem or a compiz problem rather than an fglrx problem. Did you uninstall a lot of packages? Was this an upgrade or a fresh install to 11.10?

---

### Post by bangbong on 2011-10-23
Hi...

I am also having the same issue, after upgrading, I did remove the old packages suggested by the installer... 13* packages ... :popcorn:

Would you like to see my xorg.conf ?

Sorry to jump in ...

---

### Post by Prodoc on 2011-10-23
> **bangbong said:**
> I am also having the same issue, after upgrading, I did remove the old packages suggested by the installer... 13* packages ... :popcorn:
You'd have to be more specific. What have you actually done, what have you tried and what does and does not work?

---

### Post by bangbong on 2011-10-23
My bad for giving less informations... Hi Prodoc and all. 

My lspci
> 01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]

After Upgrading to 11.10
My xorg.conf {which is not giving me any good results for multiple display}
> 
Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "0-LVDS"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1366x768"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "0-CRT1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1366x768"
        Option      "TargetRefresh" "60"
        Option      "Position" "1366 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "Monitor-LVDS" "0-LVDS"
        Option      "Monitor-CRT1" "0-CRT1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection 

* I have tried, both works. but the results on the display are rather disappointing. 
> 
aticonfig --initialize
gksu amdcccle


I am using additional driver for the above settings// 
Do assist.... Thanks!

---

### Post by Prodoc on 2011-10-23
> **bangbong said:**
> My bad for giving less informations...
Your xorg.conf file should be OK.

Please try the following:
[LIST]
[*]Delete the file ***"~/.config/monitors.xml"*** to make sure the GNOME display settings aren't conflicting with AMD's
[*]Run the following command in the terminal ***"sudo cp /etc/ati/amdpcsdb.default /etc/ati/amdpcsdb"*** to restore AMD's settings db
[/LIST]

After you've done this you should only use AMD Catalyst Control Center (AMDCCCLE) to change your display settings. It's better not to touch the **"Displays"** section in the GNOME settings any more before and after you used AMDCCCLE. All you need can be done by using AMDCCCLE.

[LIST]
[*]Run ***"gksu amdcccle"*** in the terminal to bring up the Control Center.
[*]Go to the **"Monitor management"** section (translated to English, beneath the **"Color"** section if it's called different)
[*]On the **"Multi-display"** tab (the second one), select ***"Multi-display desktop with display(s) 2"*** from the dropdown/combobox
[*]Arrange the displays in the top section of the same page to how you've set them up
[*]Press **"Apply"**
[/LIST]

Does it work now? Do the displays change to how you want it?

If yes, and if everything went OK you should get a confirmation dialog asking if you want to keep the current (new) settings or not.
If you get this dialog then answers yes.
If you don't get the dialog then the settings will be reset the next time you login. Make the settings again and keep trying it until you get this dialog. In my case I sometimes get the dialog and sometimes I don't. Just try again and you'll get it eventually.

If you didn't get the multi-display setup you wanted after you pressed **"Apply"**, let us know what did happen. Did you get any errors e.g.?

In that case try to answer the following questions:
[LIST]
[*]What does happen?
[*]Did the ATI drivers install properly without any errors?
[*]Are both monitor at least showing something?
[*]Is the content of both monitors identical (mirror/clone)?
[*]Do you get the same error as in the first post of this thread? (**"The selected configuration for displays could not be applied:required virtual size does not fit available size: requested=(2560, 1024), minimum=(320, 200), maximum=(1280, 1280)"**)
[*]Do you get any other errors?
[/LIST]

---

### Post by osarusan on 2011-10-24
I don't know why it's not working right for you guys, but just to make sure we didn't overlook something let's start with a clean slate. Try this:

Backup and then completely delete everything in your xorg.conf file so its totally empty.

Then run
sudo apt-get remove --purge xorg-driver-fglrx fglrx*

Then reinstall the driver with
sudo apt-get install fglrx

Finally, run
sudo aticonfig --initial -f

Reboot, run
gkdu amdcccle

and set up your monitors as Prodoc outlined above.

Then reboot once more.

See if that fixes things.

---

### Post by bangbong on 2011-10-24
Thanks Prodoc and Osarusan....

Here my screenshot to reproduce as on my previous post. On my right monitor... its overlapping,snapshot can only be taken by recording.

From now, I will try to follow prodoc and the newest osarusan solution.

Will update, soon...
[U]
Update on **Prodoc**:[/U]

   -> Delete the file "~/.config/monitors.xml" to make sure the GNOME display settings aren't conflicting with AMD's
   => monitor.xml (good one and proceeding)
   -> Run the following command in the terminal "sudo cp /etc/ati/amdpcsdb.default /etc/ati/amdpcsdb" to restore AMD's settings db
   => overwrite amdpcsdb file after backup.
  
   -> The rest, no change has been made after confirming on amdcccle settings.
   => confirming and reboot... 
   => scattering space/overlapping in the attached file has been fixed.
   => some improvement here... my mouse cursor seems missing when I move to second desktop. <any idea>

To-Do if the mouse cursor can be fix, I will change my second desktop(external) LCD resolution to 1920x1080

I will wait for some advice before implementing Osarusan advice...

---

### Post by Prodoc on 2011-10-24
> **bangbong said:**
>    => some improvement here... my mouse cursor seems missing when I move to second desktop. <any idea>
...not to make you sound like a fool, but just in case you overlooked it in a hurry: Are you sure you are moving the mouse out of the first monitor?
Try moving your mouse out of the left-hand side of your primary monitor, even though the monitor is physically on the right-hand side. Does the mouse pointer show on your second monitor now?
It could be that the orientation is set up wrong and the computer thinks the monitor is one the left of your primary display.

If this is the case, open AMDCCCLE again and turn the monitors around in the previously mentioned **"Monitor management"** section by dragging one of the displays to the other side.

> **bangbong said:**
> I will wait for some advice before implementing Osarusan advice...

If this did not solve your problem then I'm afraid you'd do the right thing by following Osarusan's advice. A clean slate would be good to rule out mistakes in that area.

---

### Post by bangbong on 2011-10-24
Hi Prodoc...

I am in hurry actually but acting like a fool... :guitar:

Things work after making external LCD position on the left.

Do > # aticonfig --desktop-setup=horizontal
will make my LCD to be on the right?

Need to catch up some sleep now, 

:KS Prodoc  :KS Osarusan

---

### Post by Prodoc on 2011-10-24
> **bangbong said:**
> Do 
will make my LCD to be on the right?
No, that won't work. Just use the AMDCCCLE interface again.
[LIST]
[*]Run ***"gksu amdcccle"*** in the terminal to bring up the Control Center.
[*]Go to the **"Monitor management"** section (translated to English, beneath the **"Color"** section if it's called different)
[*]You'll see 2 images of a display next to each other at the top of that page.
[*]Drag one of them to the other side of the other. E.g. hold down the left mouse button on the display on the left-hand side. Move the display to the right of the display on the right-hand side while holding the mouse button down.
[*] Click on the **Apply** button
[/LIST]

---

### Post by cmavr8 on 2011-10-26
Thanks Prodoc and osarusan, I tried your guide-posts (posts #20 and #21) but I always get amdcccle crashing when I hit apply!

Also, jockey is unable to install the post-release driver (bug has been filed and waiting...).

Any other ideas?
Did anyone get past this?

For the moment I only get dual-monitors with the opensource drivers which sucks in performance..

Thanks

---

### Post by Prodoc on 2011-10-26
> **cmavr8 said:**
> Any other ideas?
Did anyone get past this?
You can either install the non-post-release jockey driver, which might not give the installation error or install the latest AMD drivers manually.

If you choose the latter then do the following:
Download [http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run)
```
$ sudo apt-get remove --purge fglrx*
$ sudo chmod +x ati-driver-installer-11-9-x86.x86_64.run
$ sudo ./ati-driver-installer-11-9-x86.x86_64.run
$ sudo aticonfig --initial -f
```

I [ran into an installation issue](http://ubuntuforums.org/showthread.php?t=1865263) myself this way. Normally you would not have to do this but just to be on the safe side it would be good to run the following as well right after the installation and before you reboot:

```
$ sudo update-initramfs -u
```

After this reboot and follow the steps again in the previous posts.

---

### Post by cmavr8 on 2011-10-26
First of all thanks again for helping and giving out exact commands! 

I was actually using the non-post-release drivers from jockey..
Also, I was avoiding to install stock AMD drivers as people say they are usually even worse..

Anyway, I ran the commands, but AMD drivers refuse to install (it stated that another version is already installed so I thought a reboot might work). 

Then I rebooted and I had no monitors any more... After grub they're dead.
Logged in via ssh, tried the AMD drivers again, they said "another version is already installed" and I needed to uninstall it or force installation. Forced installation failed.
Reinstalled fglrx, rebooted.
Then I got my login screen, but one of the screens would not even turn on. No matter what I did in amdcccle. 
Rebooted, fixed.

Uninstalled fglrx, retried AMD with the --force option and installation succeeded! It suggested a reboot.
Rebooted and I was stuck at the loading screen. Rebooted and was stuck at "* Checking battery state...  [OK]". I can see an error: "Warning: failed to open config file /etc/modprobe.d/fglrx.conf: No such file or directory"
Via ssh I ran update-initramfs -u.

Rebooted, stuck at loading screen. Rebooted, the same.
Via ssh I run the uninstall script, which reports that it cannot find some files.. corrupted install etc. 
I use the not-recommended --force option to run the uninstaller.
Apt-get install fglrx. Reboot and I'm working on one screen now.


This is really, really sad... How many hours do we have to loose on basic stuff everytime we upgrade? Why do they have to mess with the basics every time??? (rhetorical questions, don't bother to answer)

---

### Post by bangbong on 2011-10-26
> **Prodoc said:**
> No, that won't work. Just use the AMDCCCLE interface again.[LIST][*] Click on the **Apply** button
[/LIST]

I am just able to reply to you today... I tried, and it works right after I click apply... no issues, the desktop position switched without issues. 

But, when I reboot the system... the mouse can freely move to 30% on the right space of the LCD screen. 

Now, I am reverting to the working config right after this, by rebooting. 

big thanks! for the hint... will try to check over the weekend.... or just leave this settings like this, as I might be using the monitor at my left side when I got my monitor arm.... :KS

---

### Post by Prodoc on 2011-10-26
> **cmavr8 said:**
> This is really, really sad... How many hours do we have to loose on basic stuff everytime we upgrade? Why do they have to mess with the basics every time??? (rhetorical questions, don't bother to answer)
Yeah, it really is terribly sad and shameful. I ran in the exact same issues you had but got it working eventually. So it can be done.
On the other hand, AMD's CCC 11.10 will be out in a day or 2, maybe that release will address some more Ubuntu 11.10/Unity/GNOME 3 issues. So if you have a usable system now, hold up for a day or 2 and then try again.

If you don't manage with CCC 11.10 then let us know. I'll write the lengthy process I had to go through myself to get it running then. It would be a waste of time to do it now if all is fixed with 11.10 ;-)

---

### Post by cmavr8 on 2011-10-27
Ok, I can definitely wait for a few days or even weeks!

---

### Post by bangbong on 2011-10-27
optimistic ubuntu users!......

---

### Post by osarusan on 2011-10-27
Yes, this happens with *every* update Ubuntu releases it seems. I am getting very frustrated... In fact I am using Linux Mint now, which is still Ubuntu, but minus a lot of the problems.

Since Natty I have been performing clean reinstalls instead of upgrades every time a new release comes out. That's the only way it works for me.

Are you actually purging fglrx or just ininstalling it? Make sure you completely purge it. Also, I would stay away from the drivers from the AMD website. They have a way of making themselves impossible to truly remove. Stick with the drivers in the repositories.

See if you can completely purge them and get to a working desktop using the regular open source drivers. If you're able to do that, you can try running jockey again to see if it works.

---

### Post by cmavr8 on 2011-10-27
I've been using purge all the time.

I did a clean install, tried the various options once again and finally rolled back to the opensource driver, in order to use the second monitor.

I'll retry jockey in a few days..

(BTW, I had to write this answer twice, because of a wifi bug on my laptop (connected but no internet))

---

### Post by scottrasmussen on 2012-04-15
holy cow i got it to work!

---

### Post by cmavr8 on 2012-04-16
Please share details :)

---

### Post by scottrasmussen on 2012-04-16
cmavr8:

all i can say is that i followed the instructions re: 


```

sudo aticonfig --initial

```and

```
gksu amdcccle
```from checking around i believe that the ati drivers have been updated as of march (i installed them from the additional drivers option in systems settings - however they were the initial and not the post-release drivers).

also when using catalyst and selecting the desktop settings,  catalyst would sometimes close without asking if i wanted to save the changes.  it took multiple attempts, but when i finally got the prompt "do you want to save these changes" (or something similar) and a notification to reboot, everything just fell into place.  

best of luck!

-s

---

### Post by cmavr8 on 2012-04-16
> **scottrasmussen said:**
> cmavr8:

all i can say is that i followed the instructions re: 


```

sudo aticonfig --initial

```and

```
gksu amdcccle
```from checking around i believe that the ati drivers have been updated as of march (i installed them from the additional drivers option in systems settings - however they were the initial and not the post-release drivers).

also when using catalyst and selecting the desktop settings,  catalyst would sometimes close without asking if i wanted to save the changes.  it took multiple attempts, but when i finally got the prompt "do you want to save these changes" (or something similar) and a notification to reboot, everything just fell into place.  

best of luck!

-s

Thanks so much! I'll try it as soon as I can afford to lose a few hours try to get X up :lolflag:

(Irony not intended to you offcourse!)

---

### Post by zigac on 2012-06-12
I have a problem with configuring Multi-Display. I want to have multi-display on my monitor and TV. I configure in amdcccle. I had no problem with previous version of Kubuntu 11.10, now i am using 12.04. It's working, the only problem is that the TV is always the primary and monitor secondary, even if i switch monitors in the amdcccle. The login and desktop is always on the tv. If i don't use amd additional drivers, there is no problem, i can have multi desktop, but i need amd driver to adjust the fan speed. Can anyone help?

---

### Post by AustenG on 2012-08-11
Hey guys. I'm having an issue with catalyst 12.6 (running Ubuntu 12.04 LTS) with a Radeon 7xxx HD card, trying to setup dual-monitors. 

I've tried running:
```

sudo aticonfig --initial
gksu amdcccle

```

but my real problem is that catalyst (using 12-6) says my second monitor has 640x480 as "preferred" resolution and won't let me change it. It's supposed to be 1920x1080. 

I also tried purging and re-installing fglrx, no luck. If this helps anybody figure out my problem I found this ([http://wiki.cchtml.com/index.php/Hardware]("http://wiki.cchtml.com/index.php/Hardware")), which basically says that the officially supported version for my graphics card is 12-1. I tried catalyst 12-1 and it made it much worse. 

Any advice would be appreciated!

---

### Post by Peter LaValle on 2012-09-27
> **osarusan said:**
> This happened to me too, and the solution was simple.

Run ```
sudo aticonfig --initial

```
This will re-initialize your xorg.conf. Then when you reboot you should be able to active your 2nd monitor with ```
gksu amdcccle
``` and set it up correctly; or you may also be able to use the Ubuntu Display manager.

This works for me. I suspect that the "Special Sauce" was using ATI's configuration utility.

Setup;
[LIST]
[*]Ubuntu 12.04.1
[*]Asus Radeon HD 6770
[*]Acer ?? 1920x1080 monitor (DVI)
[*]Acer AL1717 1280x1024 (VGA)
[*]Asus M5 A99X Evo
[/LIST]

---

