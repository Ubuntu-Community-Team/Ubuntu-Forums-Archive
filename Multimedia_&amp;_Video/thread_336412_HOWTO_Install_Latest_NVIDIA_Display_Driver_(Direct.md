---
title: "HOWTO: Install Latest NVIDIA Display Driver (Directly from Nvidia: current 1.0-9755)"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by Hub-1 on 2007-01-11
This howto will guide you trough a quick and easy install of the latest NVIDIA display drivers on **Ubuntu Edgy (6.10)**


*If you have **Ubuntu Feisty (7.04)**, you can install these drivers via*:
```
*System > Administration > Restricted Drivers Manager*
```


[I]IMPORTANT - Use this guide only under the following conditions:
- This guide is only meant for Ubuntu Edgy (6.10).
- You should not use this guide if use (or upgraded from) Ubuntu Dapper (6.06)
- Update your system before you install this driver (i.e. via synaptics or the update notifier)
- Only install this driver if you have a newer NVIDIA card. (check [here]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") if your videocard is supported by this driver)
- If you are new to Linux, I suggest you use the native ubuntu drivers or Alberto Milone's [envy]("http://albertomilone.com/nvidia_scripts1.html") instead of this guide.[/i]

**Current version:**
Linux Display Driver - x86

Version: 1.0-9755
Operating System: Linux x86
Release Date: March 7, 2007

[I][SIZE="1"]Release Highlights
    * Added support for Quadro FX 4600 and Quadro FX 5600
    * Added initial support for NVIDIA SLI with GeForce 8800, Quadro FX 4600, and Quadro FX 5600[/SIZE]
[/I]

*It is probably a good idea to print this guide or memorize it because you are working without X  on the last 2 points.*

**1. Grab the drivers from [www.nvidia.com](www.nvidia.com):**
Either get the drivers from [www.nvidia.com](www.nvidia.com) or download them directly. Open a terminal: *(Applications > Accessories > Terminal)*
```
 wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run 

```
Note: Don't delete this driver after the installation. You will have to reinstall it once ubuntu updates the kernel (This only happened once so far)

**2. Install system dependencies:**
```
 sudo apt-get install build-essential pkg-config xserver-xorg-dev 
```

**3. Prepare system:**
You have to disable Ubuntu's own drivers to avoid conflict.
To do this, edit  /etc/default/linux-restricted-modules-common with the editor of your choice.
```
 gksudo gedit /etc/default/linux-restricted-modules-common 
```
Modify the line *DISABLED_MODULES=""* to the following:
```
DISABLED_MODULES="nv"
```
If you previosly installed ubuntu's "nvidia-glx" delete the drivers and the init script:
```

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-glx-legacy
sudo rm /etc/init.d/nvidia-glx 
```

**4. Install the driver:**
 
4.1. You cannot have a running Desktop Environment/Xserver while installing the driver, thus you have to ***'end your current Session'***, which trows you back to the login screen (either kdm or gdm) then press the following keys to login on a terminal without X: 

```
**   CTRL+ALT+F2** *(if you want to go back to X, press CTRL+ALT+F7)*
```

 
4.2. Login and stop the session manager, gdm or kdm (gnome or kde) to shutdown the Xserver:
```

sudo /etc/init.d/gdm stop                      #  If you have gnome
sudo /etc/init.d/kdm stop                      #  If you have kde

```
Then install the driver (hint: use the Tab key to avoid unnecessary typing)
```
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```
Follow the instructions, you should say yes everywhere. When it asks you about changing the config file, choose **yes**.

**5. Check for a successful install**

5.1 *(Optional)*  Verify your config file (xorg.conf)
To make sure you pushed the right buttons during the install process, check */etc/X11/xorg.conf* file and look for  *"Section Device"*. If the *"Driver"* line shows "***nv***", change it to "***nvidia***". Use an editor of your choice to edit the file. 
```
sudo nano /etc/X11/xorg.conf 
```
It should look something like this (don't change your Identifier line!):
```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection
```
If everything is ok, press *CTRL+X* to exit nano.

5.2 Restart x (or reboot)
Rebooting should not be necessary, you should be able to startup X again with the new driver loaded.

Startup X: (with gnome or kde)
```

sudo /etc/init.d/gdm start                    #  If you have gnome
sudo /etc/init.d/kdm start                    #  If you have kde 
```
Or reboot the  PC:
*Press CTRL+ALT+DELETE - the PC will reboot.*

5.3 Check for the Nvidia driver.
In a Terminal, type:
```
glxinfo
```
It will spit out a bunch of messages, you should see the driver version in here.
For those who only want the relevant info. 
```
glxinfo | grep version
glxinfo | grep direct
```
Should show you:
[I]OpenGL version string: 2.1.0 NVIDIA 97.55
direct rendering: Yes[/I]
 

**Optional: Tweak your graphics card options with "nvidia-settings"**
Antialiasing, Antiisotropic filtering .. all that stuff. Try it :)

Accessible trough *(Applications > System Tools > NVIDIA X Server Settings)* after the driver installation.
Or in console, type:
```
nvidia-settings
```

Happy installing!

---

### Post by Enverex on 2007-01-11
hmm, upgraded myself a few minutes ago actually (just noticed that I was still running the horribly broken 8778 drivers which should never have been used by anyone, especially as the release drivers for Edgy). I didn't need to edit the restricted file or reboot, you just need to make sure the module is unloaded and load the new one.

---

### Post by DocGoodbyte on 2007-01-15
I wanted to pass along that I just download Ubuntu (first time with Linux) and then successfully installed the latest NVIDIA drivers  1.0-9746 on my computer. Just one comment for nubes, step 3 you call out vim as your editor, gedit comes standard with Ubuntu Edgy. I also was not able to verify the process in step 5, but finally rebooted and it came up fine. Delighted!:D

---

### Post by Hub-1 on 2007-01-15
> **DocGoodbyte said:**
> I wanted to pass along that I just download Ubuntu (first time with Linux) and then successfully installed the latest NVIDIA drivers  1.0-9746 on my computer. Just one comment for nubes, step 3 you call out vim as your editor, gedit comes standard with Ubuntu Edgy. I also was not able to verify the process in step 5, but finally rebooted and it came up fine. Delighted!:D
You are right, gedit is probably easier to handle than vim for new users. I will change the HOWTO accordingly. Also, could you please tell me how you were not able to verify in step 5?

---

### Post by DocGoodbyte on 2007-01-16
I entered code: /etc/X11/xorg.conf and it returned -bash: /etc/X11/xorg.conf: Permission denied. I also tried entering sudo /etc/X11/xorg.conf and it returned command not found. I suspect I am missing something that is common knowledge. A newb trait.

I also found that there is no need to enter code: nvidia-settings as they show up under Applications-System Tools-NVIDIA X Server Settings. There I can set resolution up to 1280x1024 which is native resolution for my display. It gives a choice of 7 resolutions for my display setting.

---

### Post by Enverex on 2007-01-16
> **DocGoodbyte said:**
> I entered code: /etc/X11/xorg.conf and it returned -bash: /etc/X11/xorg.conf: Permission denied. I also tried entering sudo /etc/X11/xorg.conf and it returned command not found. I suspect I am missing something that is common knowledge. A newb trait.

I also found that there is no need to enter code: nvidia-settings as they show up under Applications-System Tools-NVIDIA X Server Settings. There I can set resolution up to 1280x1024 which is native resolution for my display. It gives a choice of 7 resolutions for my display setting.

... you're trying to execute a text file which unsuprisingly doesn't work, heh. You need to open it with a text editor of some sort.

---

### Post by DocGoodbyte on 2007-01-16
I went through your revised guide and it worked like a champ! I think it is newbie proof. Thanks! :D

---

### Post by ashmew2 on 2007-01-17
Hi every1 , I have an Nvidia Geforce 4000 MX [AGP 8x] Graphic Card and im currently using Ubuntu Christmas Edition but when i foolow the steps in this guide , everything is fine until i acctually run the installer script. It says some error regarding 'nvidia.ko' after it compiles the kernels , i have followed all the other steps and im clueless.Thanks

---

### Post by Enverex on 2007-01-17
The GeForce 4MX series were dropped starting with the 97XX nVidia drivers, you need to use a 96XX driver.

---

### Post by trill on 2007-01-17
I just upgraded from Dapper to Edgy so I need to new drivers. I do everything above and then I get to the installation part. It says no matching kernel found. It then asks If i want the installer to make one I think? Anyways,I click yes and it says unable to find kernel source tree.Installation failed.I need help badly,just started using ubuntu a few days ago,on dapper I just used automatix to install drivers but there is no install nvidia drivers option on it now. BTW I  have a FX GeForce 5500.

---

### Post by trill on 2007-01-17
Help :(

---

### Post by DocGoodbyte on 2007-01-18
Thought I would pass along that your procedure works on Ubuntu for the AMD 64 drivers too. NVIDIA-Linux-x86_64-1.0-9746-pkg2. So far flawless. :D 

For trill: If you are doing a fresh install, I don't see how you can go wrong. You mentioned you had upgraded from Dapper to Edgy, maybe it is an upgrade problem.:confused:  
My system is: MSI RS482M4-ILD motherboard, PCI Express GeForce PCX 5300, AMD 64 3500+, WD400 Hard Drive.

---

### Post by tseliot on 2007-01-18
> **trill said:**
> I just upgraded from Dapper to Edgy so I need to new drivers. I do everything above and then I get to the installation part. It says no matching kernel found. It then asks If i want the installer to make one I think? Anyways,I click yes and it says unable to find kernel source tree.Installation failed.I need help badly,just started using ubuntu a few days ago,on dapper I just used automatix to install drivers but there is no install nvidia drivers option on it now. BTW I  have a FX GeForce 5500.
Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by MarkUK on 2007-01-19
I have tried this 5 times now , installs the drivers compiles the kernal but when i open up the xorg.conf its empty ! each time i have tried its been with a fresh install of 6.10 any ideas ?

---

### Post by daverave999 on 2007-01-19
MarkUK, I hope I'm not being patronising by suggesting this because I'm new to this too, but it's definitely /etc/X11/xorg.conf rather than /etc/x11/xorg.conf you are trying to look at? The capital X in X11 is essential. If not that, I'm clueless sorry! HTH

[EDIT] Also, I believe that checking xorg.conf is not required for the install. If you still can't pull up anything with text in it, just move on to the next step. Look if 'NVIDIA X Server Settings' is in Applications>System Tools to check if it's installed.

---

### Post by MarkUK on 2007-01-19
thnx for that :) , done the install everything went ok , no shiny nvidis plash screen but i have x server settings in applications .

i think it went wrong

---

### Post by Enverex on 2007-01-20
> **trill said:**
> I just upgraded from Dapper to Edgy so I need to new drivers. I do everything above and then I get to the installation part. It says no matching kernel found. It then asks If i want the installer to make one I think? Anyways,I click yes and it says unable to find kernel source tree.Installation failed.I need help badly,just started using ubuntu a few days ago,on dapper I just used automatix to install drivers but there is no install nvidia drivers option on it now. BTW I  have a FX GeForce 5500.

You need to install the "linux-sources" or "linux-headers" package like it says.

---

### Post by DocGoodbyte on 2007-01-20
> **MarkUK said:**
> thnx for that :) , done the install everything went ok , no shiny nvidis plash screen but i have x server settings in applications .

i think it went wrong

Don't count on seeing the NVIDIA splash screen . It depends on the speed of your processor and for me it barely observable. It goes by in the wink of an eye.

---

### Post by Severa on 2007-01-22
Hub-1, just wanted to drop a line and give you good news. I just did a fresh install of Feisty on my system (Athlon 2600+, 1GB RAM, GeForce FX 5900XT) 

Followed your guide and it went very smoothly. Like DocGoodbyte said, I also have the 'NVIDIA X Server Settings' selection in Applications - System Tools.

Thanks to Hub-1 and everyone else who helped on this thread! =D>

---

### Post by rbrueske on 2007-01-24
this thread is a godsend. I have about 2 days of ubuntu/linux under my belt and am desperately trying to make it a suitable replacement for windows. i thought i'd share my experience, should others care and ask a few questions.

I had previously installed the amd 64 bit version of ubuntu 6.10 and previously tried and failed to add the NVIDIA driver.

i have an amd 64 processor, as such i used the NVIDIA-Linux-x86_64-1.0-9746-pkg2.run file. once i was in the installation, I received a couple messages that I didn't know what to make of:

"No precompiled kernel interface was found to match your kernel. Would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site?"

I then received a message:

"No matching precompiled kernel was found on the NVIDIA ftp site." I was then able to download and recompile through the NVIDIA installation. I didn't think I would be recompiling my kernel shortly learning a couple basic commands.

Otherwise, the instructions worked flawlessly. But now that the NVIDIA X Server settings are installed, I have a couple questions. I have two displays running on an NVIDIA 6800GT. How do I rotate my displays to vertical dimensions (1200x1600 instead of 1600x1200)? What is the difference between TwinView and Separate X Screen (requires X restart)? I could only get TwinView to work properly. I'm used to the windows NVIDIA display manager which is much more elaborate (albeit buggy).

Any information is greatly appreciated. I'm trying to learn all of this after hours, so well written instructions like these are a godsend compared to poorly written, biased, incorrect/irrelevant info that's not fun to sift through for a nugget of goodness. thanks so so much!

---

### Post by old_geekster on 2007-01-29
Thanks for the great guide, Hub -1.  I appreciate your thoughtful help!

 I have installed Ubuntu approximately seven times in the past several days, because I continue to make blunders that I can't survive.  However, as a newbie to Ubuntu Edgy Eft 6.10, I figure that I won't forget how to install it.  They say practice makes perfect.  I should have it down by now.  Also, I am learning commands as I go.

I just got through following your guide.  The other six times I followed another guide, which worked great, however, I couldn't see proof of which drivers were installed.  This time, I have "NVIDIA X Server Settings" in the "System Tools" section.  It recognized my video card as a 7900GTX which truly amazed me.  It even gives me a temp monitor.

It would be nice if every manufacturer would make drivers available that are this good.  Most of my components are recognized, but not all of the functions work.

---

### Post by DocGoodbyte on 2007-01-31
> **rbrueske said:**
>  But now that the NVIDIA X Server settings are installed, I have a couple questions. I have two displays running on an NVIDIA 6800GT. How do I rotate my displays to vertical dimensions (1200x1600 instead of 1600x1200)?

Have you tried " sudo gedit /etc/X11/xorg.conf" in terminal mode and then modifying the display setting manually. I had to manually enter "1280x1024" to get the display to default to the proper resolution (1280x1024) automatically for my monitor. Note that I modified every setting to "1280x1024".

Good luck!

---

### Post by akrus on 2007-01-31
is there any way to compile 9746 under 2.6.20-6? because the one in the repos is not working and it does not compile at all :(

---

### Post by old_geekster on 2007-01-31
I simply had to add more accolades for this guide.

I just did a complete update of my new install (#7 since I began using Ubuntu a week ago).  There were 131 items.

I had installed "1.0-9746 nVidia drivers" prior to the update.  When I rebooted, I didn't get the GUI interface, but instead an error.  I read the log and it said that the nVidia drivers were not installed correctly.  So, I ran the last two lines of the script in this guide, which I had written down as suggested, and rebooted.  This time success!!  It worked great.

I had this happen one other time and did a complete reinstall.  This saved me about 2 hours of time.

Thanks again, Hub -1.:D

---

### Post by aimnano on 2007-02-09
I followed the guide to the letter, but after rebooting I get some error messages like:

"...API mismatch:  the NVIDIA kernal module has the version 1.0-7184 but this X module has the version 1.0-9746.  Please make sure that the kernel module and all NVIDIA driver components have the same version.'

Also 'Make sure the nvidia device files have been created properly.'

I also got errors during install that no matching kernel was found did I want to try to download one.  I said yes...then no matching were found.  Then the installer made one...and the drivers seemed to install fine.  It automatically change 'nv' to 'nvidia' in my xorg.conf as well.

However, I now do have NVIDIA X Server Settings in Applications > System.  But it's empty when it opens, just some checkboxes.  Nothing in the listbox on the right except nvidia-settings configuration.

Any help appreciated.

---

### Post by Joshua on 2007-02-10
I've also got this error.  
```
Error: API mismatch: the NVIDIA kernel module has the verion...
```
My version numbers are slightly different, but I'm sure it's the same problem.  I installed the more up-to-date AMD64 nVidia drivers from Alberto Milone's (tseliot's) repository.  Then, a month later (today), I used the Update Manager to get all the security updates and stuff.  I think there was a new kernel in there.  Now when I restart, I get the error.

I've had this happen before when installing the driver with the script from the nVidia website.  In that case, I would uninstall and reinstall with the script and it would work again, but just until I restarted the computer.

I saw a post somewhere once about a script that Alberto Milone wrote to fix this, but it looked like the script was just written for when you use the script on the nVidia website to install the driver.  Besides, I'd kind of like to understand how to fix this myself.  Can anyone explain it to me?  It seems like it should be pretty simple - like there's just a configuration file somewhere that got updated with the wrong version number from the official Ubuntu repositories rather than from the albertomilone.com repositories that I used...

---

### Post by IntoTheLight on 2007-02-10
A little help, please!

Following your guide, in step 4 it tells me that it can't sh: NVIDIA-Linux-x8...

I am new to this whole process.  Last time I typed in commands was around 1985!  I typed everything correctly (about 10 times) and tried some variations just in case (about 20 of them).

Also, what does this mean "hint: use the Tab key to avoid unneccessary typing".  Is there something I should know that the seasoned people aren't telling me?

Hoping to hear something soon.  I'm forced to use Windows till I do.:(

---

### Post by Tim T on 2007-02-11
Hub-1 , You saved my life! I have a half dozen assignments due on Monday, and I couldn't afford to be down trying to figure this out all weekend. Great tutorial, and Thanks a lot!

---

### Post by IntoTheLight on 2007-02-11
OK, just a thought...

When I download the file, by default it goes onto the desktop.  Then I disable the desktop as part of step 4, don't I?  Is this my problem?  Should I be saving it somewhere else?

Also, I am doing a fresh install of Edgy.  Is there another piece of the puzzle that I need to install first?

I'm just following the guide, word for word, and it keeps telling me that it can't open the file.  I have verified the file name is correct, and I know I'm typing correctly.

I could just go on getting everything else setup on Ubuntu, but this driver thing has caused me to have to reinstall about a gazillion times, so I want to get it done first.

---

### Post by nemanaldin on 2007-02-11
hi
i downloaded this version of driver and i want install it on my ubuntu system 6.06 lts
i tiped "uname -a" and it give this:Linux nemanaldin 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux
and i have fx 5200 graphic card
i cant install
i want know can i install it on this os?
thanks alot

---

### Post by IntoTheLight on 2007-02-11
OK, so apparently that was it.  I guess for those of us that know relatively zero, the instructions should be edited to only include the command line, of they should specify where to download the drivers to.  It would have saved me about 18 hours of reading/reinstalling/cursing.  

I know that's supposed to the fun of Linux, but I'm impatient with an anger management issue!  Still, now I know, *and knowing is half the battle!*

---

### Post by IntoTheLight on 2007-02-11
Now that I'm done with that (thank God), what do I NOT want to upgrade?  I get that little upgrade notification every day and I'm always afraid to do anything because I don't want it all to go to crap.  I hear that some updates screw the whole setup of the drivers.

I still haven't figured out how to backup AND restore.  I can backup, but have zero idea about restoring, especially when I can't even log in (a re-direct would be helpful).

---

### Post by Daminator on 2007-02-12
I've installed the drivers as the instructions on the first page. Is there anything else I should do to get the best out of my card? Don't want to push it too hard, just want to set settings ok.
I have a 5200.

> I've seen this post on a different thread:

If you use an nvidia GeForce FX 5200 GPU then there's no need for the above!

Simply open terminal and follow this ...

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config-enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

copy this into the file you just created

[Desktop Entry]
Name=NVIDIA Settings
Comment=Change various aspects of your NVIDIA Graphics
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Applications;System;

(then select save)

Now, hold down Ctrl+Alt+F1 and type in your username +password

Type the following

sudo nano /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf

Scroll down to the label "Modules" then comment out using # the following lines

Load "Dri"
Load "GLcore"

(if either or neither can be found then don't worry)

Scroll down and find the section called "Device". Make sure Driver="nvidia" and not Driver="nv"

Directly after you see the line BusID "PCI;1:0:0" add the following

Option "RenderAccel" "On"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "On"
Option "Accel" "On"
Option "AllowGLXWithComposite" "Off"

Press down Ctrl+o then press the enter key
Press down Ctrl+X

type..

sudo reboot

This method will of course render your tv out useless but in the 12 months i've owned the card, i've never had the need to use it!

Try it with all NVidia cards so that tseliot can add the results to his post 

But don't know if that info is valid for the driver I'm using and the way I installed it.

---

### Post by Joshua on 2007-02-12
> **IntoTheLight said:**
> Now that I'm done with that (thank God), what do I NOT want to upgrade?  I get that little upgrade notification every day and I'm always afraid to do anything because I don't want it all to go to crap.  I hear that some updates screw the whole setup of the drivers.

I'm don't know if this is exhaustive, and I'm not a guru, but you're probably pretty safe if you don't upgrade anything to do with the Kernal.  They will be packages like "linux-image", or "linux-generic", or "linux-restricted", etc.  You can just uncheck them in the list when you do the update.  But even if you do upgrade the Kernel, it's usually not that big of a deal because you can always boot into your old kernel.  Here's how it works.

Right now, when you boot, you probably get a couple lines at one point that say something like "Grub Loading..." and "Hit [something] to enter menu" and it counts down from something like 3 seconds before booting right into Ubuntu.  If you hit that [something] you'll see a list of boot options.  Those are usually Linux Kernel versions that you have installed, but it will even list MS Windows partitions that you can boot into if you have any.

When you upgrade the kernel, it will just add more options to the top of that list and shouldn't change any of the stuff associated with the old Kernel you were using.  So if you reboot into a new Kernel and something doesn't work, you should just be able to go into the Grub Menu and pick one of the older Kernel versions that did work and everything should be fine.

I do know that any time you update the kernel, the solution is supposed to be that you just reinstall the nVidia driver or you will get that "API mismatch" error.  However, I've found that to be easier said than done with packages I use.

If you want to give it a try, I used [***this***]("http://www.albertomilone.com/latest_nvidia_udsf_edgy.html") for directions on how to uninstall and reinstall the relevent stuff.

---

### Post by Joshua on 2007-02-12
> **Daminator said:**
> I've installed the drivers as the instructions on the first page. Is there anything else I should do to get the best out of my card? Don't want to push it too hard, just want to set settings ok.
I have a 5200.

If you already installed the drivers, and you get that nVidia splash screen, and 3D games seem to work ok, then the script probably figured things out pretty well for you.  The only thing you'll have to worry about, like in the previous two posts, is updating your Kernel packages.

That post you quoted looks like it is written for you to use the Ubuntu packages, but may be written with pre-Edgy packages in mind.  If you want to go that route, you'd have to uninstall what you just did.  ([***Alberto Milone***]("http://www.albertomilone.com/latest_nvidia_udsf_edgy.html") explains that pretty well.)  You wouldn't have the most recent drivers, but they will probably work just as well, and they may be easier to maintain along with upgrading your Kernels because Ubuntu should be keeping the packages compatible.

I think the commands in your quote should be more like:
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```
Then Alt-Ctl-Backspace to restart X, and everything should be working.

The "[Desktop Entry]" section is just to create a menu icon for launching the nvidia-settings utility.  I think the script from the nVidia website creates that for you (and it even has a nice nVidia logo to go with it), but you can launch if from command line without it.

For the rest of those options - I'm really only familiar with the device driver.  That should definately be "nvidia" rather than "nv".  For the others you should probably open the file that the script created for you and compare the options to the ones in that post you quoted.

It looks like the most basic options are explained [***here***.]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/chapter-03-section-02.html")

The others are explained pretty well [***here***]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-d.html").

---

### Post by snowdonkey on 2007-02-17
Hub-1, thanks a lot for this HOWTO!  You've ended what was more than a day of X server not starting whenever I changed the "Driver" to "nvidia" instead of "nv" in xorg.conf.  I had tried downloading the NVIDIA driver, another from the repositories, and using Envy.

For me the problem was that I had nvidia-glx installed and I wasn't disabling the "nv" module like you describe.

At least for me your method works flawflessly in Dapper 6.06 as well.

---

### Post by Yellowbelly on 2007-02-18
I just installed these drivers and I think it worked but I didn't see an nvidia splash screen...I think. I went through an nvidia menu but I don't remember when that was. I checked the xorg.conf file and it still said nvidia or whatever so that checked out. I also went to the menu and there's more settings so I assume it's updated. So am I still screwed?

---

### Post by elsenor on 2007-02-19
This is my first time using Linux, I installed ubuntu as a dual boot - wanted to try Linux out.  The guide to installing the nVidia drivers was real simple to follow.  I got everything working except one thing, I can't get the settings to stay.  I'll run "nvidia-settings" and change my resolution to 1680x1050x32bit@60Hz which is native to my monitor.  I'll click apply and it works fine.  I click on "Save to X Configuration File," then "save."  But when I restart, my settings get sent back to 1024x768x24bit@60Hz.


I tried editing the /etc/X11/xorg.conf file with gedit once by:

Changing "Default Depth 24" to "Default Depth 32"
and adding 

SubSection  "Display"
   Depth         32
   Mode         "1680x1050"
EndSubsection


Under the Section Screen portion of the xorg.conf file.  That made a fine mess out of everything and X wouldn't boot.  So I just finished installing the nvidia drivers on a fresh install of ubuntu.  My resolution is set to 1680x1050x32bit@60hz under the nvidia X server settings.  

How do I keep it this way?


<----Sorry, I'm a newb.

---

### Post by DocGoodbyte on 2007-02-24
> **elsenor said:**
> 
  My resolution is set to 1680x1050x32bit@60hz under the nvidia X server settings.  

How do I keep it this way?

Have you tried Hibernation instead of shut down? KUBUNTU does this by default, thus saves all settings including resolution settings.

---

### Post by adamthompson on 2007-02-24
> **tseliot said:**
> Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I had the same problem as Trill. How do you use Envy if you don't have a working X server?

---

### Post by adamthompson on 2007-02-25
After much thrashing, I managed to install the latest NVIDIA driver using Method 2 from this guide : [http://albertomilone.com/latest_nvidia_udsf_edgy.html]("http://albertomilone.com/latest_nvidia_udsf_edgy.html"). The shortcut methods just didn't work for me. But now my soundcard doesn't work.

---

### Post by williammanda on 2007-02-27
I just wanted to thank the authur of this post! I have used these instructions over and over and they work great everytime! 
Thanks

---

### Post by clooch on 2007-02-27
OH BOY, after almost 20 hours of frustrating trials. this post fixed the whole problem.

thank you very much  :guitar:

---

### Post by afham07 on 2007-02-27
> 
If a shiny flashy NVIDIA splash screen shows up before the session manager (gdm, kdm) starts up, then the install was successful. Otherwise, you are screwed. (you can change the driver in xorg.conf back to "nv")


guy, i have problem whch is no shiny flashy NVIDIA screen shows before starts up. Is my installation does not complete? what should i do?

for your information, I can setting everything using nvidia-settings. I also can access nvidia setting from Applications-->System Tools-->NVIDIA X server Setting. The matter is no NVIDIA screen shows at the start up. What should I do?

---

### Post by DocGoodbyte on 2007-02-27
> **afham07 said:**
> guy, i have problem whch is no shiny flashy NVIDIA screen shows before starts up. Is my installation does not complete? what should i do?

See my post #18.

---

### Post by afham07 on 2007-02-28
> **DocGoodbyte said:**
> See my post #18.

Then, I did a correct way la .. :D .. TQ TQ

---

### Post by Hub-1 on 2007-03-08
> **afham07 said:**
> guy, i have problem whch is no shiny flashy NVIDIA screen shows before starts up. Is my installation does not complete? what should i do?

for your information, I can setting everything using nvidia-settings. I also can access nvidia setting from Applications-->System Tools-->NVIDIA X server Setting. The matter is no NVIDIA screen shows at the start up. What should I do?

I edited the guide and removed this part to avoid unnecessary confusion. DocGoodbyte was right, the NVIDIA splash screen is not visible on every computer. Hence I added a more solid method to verify a successful install.

---

### Post by Syncman on 2007-03-08
hi thanks for the guide, yeah i installed nvidia but i mess up the identifier 

from:

```
Identifier     "NVIDIA Corporation NVIDIA 6600gt something forgot the exact line
```

to:
```
Identifier     "Device0"
```

when i try to change it to nVidia corporation... it does not show up the X login.

so is there anything i can do? or should i reinstall??? (pls NO :( reinstalling update took me 3hrs using DSL)

Thanks in advance
syncman

---

### Post by rotary on 2007-03-09
I just need to learn it hard way, I guess
First I had xserver shutdown problems, it was reporting:
```
no such command
```
but when I did ```
sudo invoke-rc.d kdm stop
``` I succeded to close it. Then I just got blank screen and typing ```
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
``` didn't do anything. As the matter of fact, nothing I typed did anything. I was forced to power off with a button. Can somebody help me? It is first 72h on Linux for me :)

---

### Post by dmg025 on 2007-03-09
I am, like several other people getting the "no matching kernel was found" message.  I allow it to download from the Nvidia site, but it says nothing is found.  And then another message about Downloading 'headers'?  Can anyone help me?  Thanks in advance

---

### Post by dmg025 on 2007-03-09
Oh, and to rotary, I am really new at this, but I think what you want to do is go to your login screen and then hit the Ctrl+Alt+F2 Button, that should allow you to start entering the commands correctly

---

### Post by rotary on 2007-03-09
True. Then it is necessary to shutdown x server. After I do it it is sopposed to input the cmd for the installation but nothing is happening.....

---

### Post by deepbluegene on 2007-03-09
hi

i have nvidia geforce4 mx 4000 card and followed step by step how to install latest drivers
but when i tried to install driver i got following error message 
'the nvidia geforce 4 mx 4000 GPU installed in this system is supported through the nvidia 1.0-96xx legacy linux graphics drivers.please visit httl://www.nvidia.com/object/unix.html for more information. the 1.0-9755 nvidia graphics driver will ignore this GPU'

and now xserver is not starting and giving message that xserver failed to start.

please help.how i can revert back to old drivers or how can install latest drivers for my card from command terminal.please help.

thanx

---

### Post by cocoviper on 2007-03-12
> **deepbluegene said:**
> hi

i have nvidia geforce4 mx 4000 card and followed step by step how to install latest drivers
but when i tried to install driver i got following error message 
'the nvidia geforce 4 mx 4000 GPU installed in this system is supported through the nvidia 1.0-96xx legacy linux graphics drivers.please visit httl://www.nvidia.com/object/unix.html for more information. the 1.0-9755 nvidia graphics driver will ignore this GPU'

and now xserver is not starting and giving message that xserver failed to start.

please help.how i can revert back to old drivers or how can install latest drivers for my card from command terminal.please help.

thanx

Ok well i hope ur still there because today the same thing happened to me!After searching for about 2 hours i finaly found out what to do to make it go back.

First step run in recovery mode and enter this line :

> $ dpkg-reconfigure xserver-xorg

When you will do this you will be sent into a menu.The computer will demand some info about your stuff when he will demand about ur Graphic Card simply select nvidia.

Finally, after doing this reconfiguration everything will work as it was before!!

only prob is that i haven't found out how to make the card to accept 3d acceleration yet if anyone could help me....

---

### Post by rotary on 2007-03-15
Just wanted to say that is working. When I had blank screen I was just sopposed to Ctrl+Alt+F1 again to enter cd without x-server. Easy but unknown for the newbies.Sorry dmg025, I guess I need to read it more than twice:) Anyway, looks great!

---

### Post by kgee on 2007-03-21
Having issues getting this exact driver going on a geforce 7950 GT

well, not exactly... The thing installs properly, and runs even better. I even managed to get a dual head configuration working. But when I reboot the thing fails to load. after much experimentation with this crash (happens 100% of the time, and so far it has been a daily routine to boot, crash, login to terminal, reinstall video drivers, continue.) I have noticed that /proc/driver/nvidia/version changes. when its working it refers to the 1.0-9755 driver I install, and when i reboot the line changes to 1.0-7184

when I try to boot without reinstalling drivers, X fails with a warning similar to:

API mismatch: module version 1.0-7184 but X module version 1.0-9755
failed to initialize driver.

when i DO get it running, dmesg has this buried in it:

[17179614.468000] NVRM: RM/client version mismatch!!
[17179614.468000] NVRM:    aborting to avoid catastrophe!

so i dont know if this /proc/driver/nvidia/version file changing is the key part of the problem, or if its simply another symptom, but something keeps changing when i reboot. I doubt it has to do with X restarting, since I can kill X and boot back into it without a problem, its only when the entire system reboots.

If you need any more info, just ask. I've been fighting with this one far too long :P

---

### Post by Hub-1 on 2007-03-23
> **kgee said:**
> Having issues getting this exact driver going on a geforce 7950 GT

well, not exactly... The thing installs properly, and runs even better. I even managed to get a dual head configuration working. But when I reboot the thing fails to load. after much experimentation with this crash (happens 100% of the time, and so far it has been a daily routine to boot, crash, login to terminal, reinstall video drivers, continue.) I have noticed that /proc/driver/nvidia/version changes. when its working it refers to the 1.0-9755 driver I install, and when i reboot the line changes to 1.0-7184

when I try to boot without reinstalling drivers, X fails with a warning similar to:

API mismatch: module version 1.0-7184 but X module version 1.0-9755
failed to initialize driver.

when i DO get it running, dmesg has this buried in it:

[17179614.468000] NVRM: RM/client version mismatch!!
[17179614.468000] NVRM:    aborting to avoid catastrophe!

so i dont know if this /proc/driver/nvidia/version file changing is the key part of the problem, or if its simply another symptom, but something keeps changing when i reboot. I doubt it has to do with X restarting, since I can kill X and boot back into it without a problem, its only when the entire system reboots.

If you need any more info, just ask. I've been fighting with this one far too long :P

You seem to have the nvidia legacy driver installed. Try:
```
sudo apt-get --purge remove nvidia-glx-legacy
```

---

### Post by shavenlunatic on 2007-03-24
THANK YOU!!!! best guide i've seen so far!

---

### Post by texasnub on 2007-03-24
I have DD 606. I tried the manual install of drivers using envy version 0.8.2 and I still have the same problem - screen blanking and green specks on the desktop - the desktop app DOES show I have the drivers installed. - but the problem still remains.. can anybody help?

It even has the right monitor displayed on the configuration screen

Thanks a bunch..

PS, its a 7600gt with a samsung 20.4" (204b) running at 1600x1200

**Update:**
It seems to be ok for a while after the monitor is powered off/on. It comes back with no green specks and until it blanks out again for the next time, the green specks dont show up.

---

### Post by the79bomb on 2007-03-24
Failed install:

I went through all the steps except for the verification (Don't have a printer). Disabled the nv package,  booted into recovery mode as ctl=alt f2 left me with a blank screen.  I then ran the installer from nvidia downloaded today and it warned me I was running in level 1 and level3 would be better for the installer and If I wanted to continue?  I said yes as I have no idea what level 1/3 is.   It warned me that it would have to compile something for my kernel as the nvidia ftp doesn't have one for Ubuntu Edgy I guess, so it does that and says everything is fine.  I reboot into blackness.  

I restore the xorg config file from the backup by luck alone (Capital X everyone) and am back to the shoddy default nv drivers which tend to black out or crash the system.  I did not have to re-enable the nv package for the screen to work but I did it anyways.  

Woe woe.  I am not happy with Nvidia drivers at all.  I have never had a good exerience with any of their cards (had 3 of them) but I don't know of a better alternative as I a have heard worse stories about ATI.   

Any pointers would be appreciated.
Yours, Tim:-({|=

ps; just tried again today with ctl-alt f1 which got me to login screen and I was able to stop the xserver.  I also moved the driver file into the /root directory.  It no longer mentioned the level 1/3 warning after this and install ran with no errors.  I checked the config file and driver said nvidia instead of the nv that was there before install.  I start the xserver and the screen goes dead.  I am able to switch back to terminal mode with ctl-alt f1 but I end up having to revert to nv driver again.   I was thinking maybe the monitor settings work for the nv driver but not nvidia? or maybe I have a faulty video card.  My system crashes sporradically and I assumed it might be the video drivers which I why I want to update them.

---

### Post by Mr. Nefarius on 2007-03-25
Yeah! Worked like a charm :KS I followed your steps exactly and viola.  Now running my desktop 1280x1024 (92Hz).  I am using a legacy card however (Ti 4200) so.....
installing the *1.0-9755* drivers were fruitless.  I used the *[COLOR="Red"]1.0-9631[/COLOR]* instead...

**[COLOR="Red"]"wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg1.run"[/COLOR]**

...then continued the rest of the process.  Kudos to **Hub-1** for the walkthru :-)

---

### Post by Greykrrr on 2007-03-25
Hi

I just want to add that I just had success running this guide with a GeForce fx5200 card, so it works for (some, at least) older cards too.

---

### Post by Theimon on 2007-03-26
When installing nvidia-glx through aptitude I get a black screen when I boot up and gdm is supposed to be loaded. I got tired of that, so I tried your guide.....but......it gives me the exact same damn trouble. After the splash screen, the screen goes black and the system fails to respond to keyboard input (hard reset is the only option to get the system to boot into recovery mode to edit xorg.conf to nv).
I don't see any errors in the follwing Xorg.log (better yet, everything loads like it should!)
```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux know-where-to-run 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686
Build Date: 20 March 2007
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 26 21:18:07 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Philips 107E6"
(**) |   |-->Device "nVidia Corporation N43 [GeForce 6600]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/X11R6/lib/X11/fonts/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/X11R6/lib/X11/fonts/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 1.1
    X.Org XInput driver : 0.7
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0282 card 1043,80a3 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 8086,1229 card 8086,0009 rev 05 class 02,00,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,812a rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f2 card 1043,81ad rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xf9f00000 - 0xfbffffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xe0000000 - 0xf8ffffff (0x19000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xfb000000/24, 0xe0000000/28, 0xfa000000/24, BIOS @ 0xf9f00000/17
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xf9e00000 - 0xf9e000ff (0x100) MX[B]
    [1] -1    0    0xf9c00000 - 0xf9cfffff (0x100000) MX[B]
    [2] -1    0    0xdff00000 - 0xdff00fff (0x1000) MX[B]
    [3] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [4] -1    0    0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
    [5] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [6] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [7] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [8] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [9] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [10] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [11] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [12] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[B]
    [13] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[B]
    [14] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [15] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [16] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[B]
    [17] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[B]
    [18] -1    0    0x0000c400 - 0x0000c407 (0x8) IX[B]
    [19] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[B]
    [20] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[B]
    [21] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xf9e00000 - 0xf9e000ff (0x100) MX[B]
    [1] -1    0    0xf9c00000 - 0xf9cfffff (0x100000) MX[B]
    [2] -1    0    0xdff00000 - 0xdff00fff (0x1000) MX[B]
    [3] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [4] -1    0    0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
    [5] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [6] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [7] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [8] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [9] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [10] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [11] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [12] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[B]
    [13] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[B]
    [14] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [15] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [16] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[B]
    [17] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[B]
    [18] -1    0    0x0000c400 - 0x0000c407 (0x8) IX[B]
    [19] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[B]
    [20] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[B]
    [21] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xf9e00000 - 0xf9e000ff (0x100) MX[B]
    [5] -1    0    0xf9c00000 - 0xf9cfffff (0x100000) MX[B]
    [6] -1    0    0xdff00000 - 0xdff00fff (0x1000) MX[B]
    [7] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [8] -1    0    0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
    [9] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [10] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [11] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [12] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [13] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [14] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [15] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [16] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [17] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [18] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[B]
    [19] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[B]
    [20] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [21] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [22] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[B]
    [23] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[B]
    [24] -1    0    0x0000c400 - 0x0000c407 (0x8) IX[B]
    [25] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[B]
    [26] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[B]
    [27] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 7.2.0, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.9755
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.9755
    Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
    compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xf9e00000 - 0xf9e000ff (0x100) MX[B]
    [5] -1    0    0xf9c00000 - 0xf9cfffff (0x100000) MX[B]
    [6] -1    0    0xdff00000 - 0xdff00fff (0x1000) MX[B]
    [7] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [8] -1    0    0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
    [9] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [10] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [11] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [12] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [13] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [14] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [15] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [16] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [17] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [18] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[B]
    [19] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[B]
    [20] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [21] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [22] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[B]
    [23] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[B]
    [24] -1    0    0x0000c400 - 0x0000c407 (0x8) IX[B]
    [25] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[B]
    [26] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[B]
    [27] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xf9e00000 - 0xf9e000ff (0x100) MX[B]
    [5] -1    0    0xf9c00000 - 0xf9cfffff (0x100000) MX[B]
    [6] -1    0    0xdff00000 - 0xdff00fff (0x1000) MX[B]
    [7] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [8] -1    0    0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
    [9] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [10] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [11] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [12] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [13] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [14] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [15] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [16] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [17] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [18] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [19] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [20] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [21] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[B]
    [22] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[B]
    [23] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [24] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [25] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[B]
    [26] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[B]
    [27] -1    0    0x0000c400 - 0x0000c407 (0x8) IX[B]
    [28] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[B]
    [29] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[B]
    [30] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[B]
    [31] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [32] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.39.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:1:0:0:
(--) NVIDIA(0):     PHILIPS 107E6 (CRT-0)
(--) NVIDIA(0): PHILIPS 107E6 (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1152 x 864
(--) NVIDIA(0): DPI set to (94, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B]
    [1] 0    0    0xe0000000 - 0xefffffff (0x10000000) MX[B]
    [2] 0    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B]
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [7] -1    0    0xf9e00000 - 0xf9e000ff (0x100) MX[B]
    [8] -1    0    0xf9c00000 - 0xf9cfffff (0x100000) MX[B]
    [9] -1    0    0xdff00000 - 0xdff00fff (0x1000) MX[B]
    [10] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [11] -1    0    0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
    [12] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [13] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [14] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [15] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [16] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [17] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [20] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [21] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [22] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [23] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [24] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[B]
    [25] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[B]
    [26] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [27] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [28] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[B]
    [29] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[B]
    [30] -1    0    0x0000c400 - 0x0000c407 (0x8) IX[B]
    [31] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[B]
    [32] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[B]
    [33] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[B]
    [34] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [35] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
```
My xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

    # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection


Section "Monitor"
    Identifier     "Philips 107E6"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation N43 [GeForce 6600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation N43 [GeForce 6600]"
    Monitor        "Philips 107E6"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```
I have no clue where to go now. The Envy script gives the same crap too. I checked the compatibility list, my nVidia card is supported by the 9755 driver. The video card runs well under Windows, so what the hell is going on?!

---

### Post by el mariachi on 2007-03-26
thanks for the guide! it work for me just fine!:popcorn:

---

### Post by Slimshady on 2007-03-27
hmm... i dont see any file called 'linux-restricted-modules-common' in the '/etc/default/' directory..... am i missing something?....
may be it has something to do with the fact that i already had a previous version of the nvidia driver and i removed it?

---

### Post by DjBee_1206GE on 2007-03-27
> **elsenor said:**
> This is my first time using Linux, I installed ubuntu as a dual boot - wanted to try Linux out.  The guide to installing the nVidia drivers was real simple to follow.  I got everything working except one thing, I can't get the settings to stay.  I'll run "nvidia-settings" and change my resolution to 1680x1050x32bit@60Hz which is native to my monitor.  I'll click apply and it works fine.  I click on "Save to X Configuration File," then "save."  But when I restart, my settings get sent back to 1024x768x24bit@60Hz.


I tried editing the /etc/X11/xorg.conf file with gedit once by:

Changing "Default Depth 24" to "Default Depth 32"
and adding 

SubSection  "Display"
   Depth         32
   Mode         "1680x1050"
EndSubsection


Under the Section Screen portion of the xorg.conf file.  That made a fine mess out of everything and X wouldn't boot.  So I just finished installing the nvidia drivers on a fresh install of ubuntu.  My resolution is set to 1680x1050x32bit@60hz under the nvidia X server settings.  

How do I keep it this way?


<----Sorry, I'm a newb.

The install worked  great on my Asus M2NPV-VM GeForce6150 but won't retain the native 1280x1024 resolution of my Sony SDM-HS73P. When I force the "save to X configuration file and then check xorg.conf, it's not updated - I still have just this entry:-

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"

etc.

The file properties show it's been modified, but nvidia-xconfig hasn't changed anything.  Anybody got any ideas?

Thanks.

A one-week old Ubuntu 6.10 baby :(

---

### Post by kanha on 2007-03-28
why is it not in howto section

---

### Post by Hub-1 on 2007-03-28
> The install worked  great on my Asus M2NPV-VM GeForce6150 but won't retain the native 1280x1024 resolution of my Sony SDM-HS73P. When I force the "save to X configuration file and then check xorg.conf, it's not updated - I still have just this entry:-

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"

etc.

The file properties show it's been modified, but nvidia-xconfig hasn't changed anything.  Anybody got any ideas?

Thanks.

A one-week old Ubuntu 6.10 baby :(

To change your default display resolution, you will have to modify all your "Modes" lines.
Change '*Modes      "1024x768" "800x600" "640x480"*' to:
```
Modes     "1280x1024" "1024x768" "800x600" "640x480"
```

The resolution you want ubuntu to start up with has to be the first in the line, like in the example above.

---

### Post by texasnub on 2007-03-28
Well, thats about all the time I can spend on this lark. I upgraded to EE6.10, and installed the latest drivers. Still same problems: screen blanking and no dual cores shown on the /proc/cpuinfo list. I looked at the grub/menu.lst file and all it has for kernels is the same 686 all the way down. 

It looks like Im going to susi linux bc I can get it through work and I will be using the same OS some of my customers and staff use.

take care

---

### Post by Slimshady on 2007-03-28
Please help me, why do i not see any file called 'linux-restricted-modules-common' in the '/etc/default/' directory?   should i create it?

---

### Post by Hub-1 on 2007-03-28
> **Slimshady said:**
> Please help me, why do i not see any file called 'linux-restricted-modules-common' in the '/etc/default/' directory?   should i create it?

If it worked with the previous version of this driver, it should also work this time.

---

### Post by Hub-1 on 2007-03-28
> **Theimon said:**
> 
```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux know-where-to-run 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686
Build Date: 20 March 2007
```

I have no clue where to go now. The Envy script gives the same crap too. I checked the compatibility list, my nVidia card is supported by the 9755 driver. The video card runs well under Windows, so what the hell is going on?!

You are using either a custom kernel or the beta version of Ubuntu (feisty, 7.04). This howto is only for edgy 6.10. I haven't tried the beta yet, therefore I cant help you there.

In case you use a custom kernel, I suggest you try it first with the native ubuntu kernel to see if the problem persists.

---

### Post by DjBee_1206GE on 2007-03-28
> **Hub-1 said:**
> To change your default display resolution, you will have to modify all your "Modes" lines.
Change '*Modes      "1024x768" "800x600" "640x480"*' to:
```
Modes     "1280x1024" "1024x768" "800x600" "640x480"
```

The resolution you want ubuntu to start up with has to be the first in the line, like in the example above.

Which I did and now it works great. Thanks for the help.

---

### Post by five01 on 2007-03-30
i wanna say thanks a bucket load... ive never used linux before today and its threads like this that make me more and more inclined to fully make the switch


thanks alot :D

---

### Post by apetits on 2007-03-30
OK, first off thanks for writing the guide...it worked...sort of.  Doing the set of instructions on the first page was successful.  I was able to reboot x-server and had the full nvidia-settings to do Twinview and all that wonderful stuff.  I set up my Laptop (A Dell Inspiron 5150 w/ nVidia Geforce Go5200) and it looked great.  The problem is that once a reboot after setting up twinview, it is unable to successfully load the settings again.  I rolled back to a previous xorg.conf, where Clone View works fine but Twinview is not possible.  I scanned through the xorg.conf and found that instead of nvidia it is nv.  I tried changing this back to nvidia and restarting x-server but I have the same issue (where it uses the secondary monitor at the native resolution of the first, and nvidia x server settings fails to load)

> 
Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Am I the only one with this issue?  It is very frustrating since Twinview and all the ncie graphics features work until I have to restart :(.  If anyone could help I'd appreciate it.

My full xorg.conf file (the one I roll back to, that works);
> #  /etc/X11/xorg.conf (xorg X Window System server configuration file)
# 
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by Tourmaline on 2007-04-01
Great howto, worked perfectly with my Galaxy 7900GS on an Asus P5PL2-SE.
Thank you Hub-1.

---

### Post by pljwebb on 2007-04-09
I have been desperately trying to fully enable my 7600GT in Feisty Beta for the past week. After many reinstalls, back ups and restores I have finally managed it thanks to this guide. It worked the first time I tried it. I was a little worried as I was going through all the steps. I did exactly as the guide suggested but during the process I got a couple of error messages, one stating that usr/lib/nvidia/libGL.so.1.2.xlibmesa and usr/lib/tls/libnvidia-tls.so.1.0.9755 didn't exist and couldn't be restored. But in the end it didn't matter because as soon as I restarted gnome I got the "you are using restricted drivers" message from Ubuntu and I knew that all was well.

Thanks a lot, you've been a god send.

---

### Post by eponymous on 2007-04-09
thanks so much hub-1! this helped out a ton
here's a few problems i had to get around for others:

i was switching to onboard video on a 2nd monitor through my bios (asus p5L mobo), i had to switch to the PCI-E video in the bios in order for the drivers installer to detect my card. this also meant i couldn't run the drivers by killing the X server from the Ubuntu login screen, because the screen was black and nothing would respond.

the remedy: boot in recovery mode, do "telinit 3", and then run the driver install

i could not start the X server upon reboot after installing the drivers. 
the remedy: once again boot in recovery mode, do "telinit 3" and this time the X server started from there. hopefully basic X server upgrades will fix this (i hadn't run any of the automatic updates after installing 7.04 and before installing these drivers)

i'm currently doing the updates, 241 of them. we'll see if my x server problems persist. everything else works out of the box, already an improvement over putting Edgy on my older comp.

specs:
core 2 duo, asus p5l-vm
evga 8800 gts 320mb
feisty fawn beta 64 bit
nvidia 64 bit drivers, pkg1

---

### Post by spencer_lai on 2007-04-10
When i try to install the driver from nvidia, it gave me an error saying it cannot find the Kernel source, any clue??

I'm using GeForce 8800 on nForce 680i mobo, the kernel version is 2.6.20.14

---

### Post by Hub-1 on 2007-04-10
> **spencer_lai said:**
> When i try to install the driver from nvidia, it gave me an error saying it cannot find the Kernel source, any clue??

I'm using GeForce 8800 on nForce 680i mobo, the kernel version is 2.6.20.14

You use either Ubuntu Feisty (7.04) or a custom Kernel. This guide is only meant for Ubuntu Edgy (6.10) with its native kernel.


On Feisty, install the drivers via:
```
System > Administration > Restricted Drivers Manager
```

---

### Post by upchucky on 2007-04-10
when i try to do sudo etc/init.d/gdm   it returns command not found

and when i try to do sudo sh Nvidia-Linux-x86-1.0-9755-pkg.run   it says it cant open it

everything in this guide worked untill the above parts

---

### Post by Hub-1 on 2007-04-11
> **upchucky said:**
> when i try to do sudo etc/init.d/gdm   it returns command not found

and when i try to do sudo sh Nvidia-Linux-x86-1.0-9755-pkg.run   it says it cant open it

everything in this guide worked untill the above parts

Well the command you typed doesn't do anything. Read the guide again carefully and you will notice that the actual command is this one:

```
sudo /etc/init.d/gdm stop
```

And the driver file you cannot open is probably in another directory. Judging from your post, you don't seem to be familiar with the commandline in linux, and as I already stated in the howto, new linux users should better not use this guide because there is a chance to end up with a non-functional system if you make a mistake.
Nevertheless, to change the current directory in the console, use "cd" to change your current directory:

```
cd /directory/where/your/driver/is/
```

Whenever you want to know something about a console command type "**man** *yourcommand*". In this case it would be:
```

man cd
```

Type "q" to exit the man-page

---

### Post by LaidbackBill on 2007-04-13
After installing edgy and getting the internet,mail and sound working the next step was to installthe drivers for the gragics card.  After reviewing this thread more than once I decided to take the plunge.  Unfortunately as easy as it looks, being a noob, I made several miscues in the directions, mostly missing "/"s,"."s or with the space bar.  After some tribulations I finally got out of X and to the point of installing drivers.

I downloaded the drivers straight from Nvidia to the desktop.  Unfortuately now when I try to open them I get a message that they cannot be opened, at least from the terminal.  Should I move the drivers to another directory or did I do something else wrong?


Thanks Bill

---

### Post by LaidbackBill on 2007-04-13
Sorry for the previous post.  I was concentrating so much on the directions on page 1 that I didn't pay attention to the post right  above mine.   I guess when I get to the terminal I should first  "cd/bill?/home/desktop" and then run the installation or change the location of the downloaded drivers? 
Thanks again, I really feel stupid>

Bill

---

### Post by v3ll0us on 2007-04-13
hye...i've juz install dapper drake on my pc.. currently installing nVidia driver NVIDIA-Linux-x86_64-1.0-9755-pkg2.run .. all went smoothly until it said  "no precompiled kernel interface was found to match your kernel.." what should i do?

---

### Post by Hub-1 on 2007-04-13
> **LaidbackBill said:**
> Sorry for the previous post.  I was concentrating so much on the directions on page 1 that I didn't pay attention to the post right  above mine.   I guess when I get to the terminal I should first  "cd/bill?/home/desktop" and then run the installation or change the location of the downloaded drivers? 

Yes you are probably in the wrong directory. Note that console commands are generally case-sensitive, thus you have to pay attention to Upper- and lowercase letters. If you downloaded the drivers to your desktop the command would be:
```

cd /home/bill/Desktop/

```
The next step would then be that you install the driver. Don't try to actually write the whole filename, just use the <Tab> key after a few letters, this will complete the filename if it is in the current directory. 

```
sudo sh NVIDI<Tab>
```

Good luck

---

### Post by Hub-1 on 2007-04-13
> **v3ll0us said:**
> hye...i've juz install dapper drake on my pc.. currently installing nVidia driver NVIDIA-Linux-x86_64-1.0-9755-pkg2.run .. all went smoothly until it said  "no precompiled kernel interface was found to match your kernel.." what should i do?

do diz:
```

sudo apt-get install linux-headers-$(uname -r)
```

and then try again.

---

### Post by djseto on 2007-04-13
I re-installed the drivers because I am having a problem with my 42" Panasonic Plasma where it is always using either 1280x720 or 800x600 for a resolution when I connect via an HDMI cable (I am using an DVI->HDMI adapter on an Asus M2NPV-VM motherboard w/ Ge6150 chip). When I do the install, everything installs fine, but when I go to a terminal and type "glxinfo", I get: 

Error: unable to open display (null)

What is causing this? I have tried removing and leaving only a 1024x768 resolution in my xorg.conf file and I still cannot get 1024x768 to work. I see every option but that in resolution settings. When it defaults to 1280x720, I get overscan and therefore my MythTV gui also overscans. It's been driving me nuts. Please help. I would rather not use my Plasma's VGA input as the picture is cleaner over HDMI and I belive this motherboards component outputs support only 720i.

---

### Post by upchucky on 2007-04-15
Thanks HUB-1, i was in the wrong directory when i tried to install Nvidia, on a lighter note the directory hint u gave saved me from the same mistake when editing my wireless info, thanks again. intel 2200bg wireless and nvidia working well due to these forums :)

---

### Post by LaidbackBill on 2007-04-17
Well I,m back after taking a little frustation break.  I started at the beginning again and watched the messages .  During the "install dependencies" I get a " package not availible" along with some other stuff.  My kernal is 2.6.17.10 generic but I tried a different method first which included getting the restricted drivers but I, not sure if I ever did as that method didn't work either.  Now I,m wondering if I may have installed something I should"t have.  How would one get back to initial install so as to start over with a clean slate.
Bill

---

### Post by LaidbackBill on 2007-04-17
Yea! Drivers installed.  Just had to go into synaptic preferences and check a couple more boxes.  Downloaded a archive file "build essential" and followed the rest of the instructions one more time and viola and restart the nvidia logo appeared.

Thanks for the directions.
Bill

---

### Post by underthehour2000 on 2007-04-22
Thx works fantastic on fiesty!  Finally a guide which works and easy to follow :KS

---

### Post by 77midget on 2008-02-11
I wish to add my thanks as well-I am a newb, and have been trying to my NVidia quadro fx1400 working properly. I was 90% there, but my install was never surviving reboot. Walking through this guide got me on the permissions scent, and I realized that my xorg changes were never taking, as the install, even though running in sudo, for some reason did not have perms. Exporting xorg.conf to desktop, and resaving in nano as root to /etc/X11 did the trick.

---

