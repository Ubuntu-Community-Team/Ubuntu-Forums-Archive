---
title: "User friendly ATI installation..please"
date: 2006-02-28
forum: Multimedia &amp; Video
---

### Post by cabber on 2006-02-28
I've been working on this for several days and finally looking to the experts to dial it back a bit.  I am very new to Linux and currently trying to stay in good gracess.  I've read, read, and read more in this forum over th epast few days about installing the Radeon driver for my vid card, but still unable to do it.

In summary, I have the Radeon X1800XT, Athlon 64 X2 processor on a 37 gig SATA hard drive.

Whe I install Ubuntu, all goes well until I get the Graphical error that looks like this. 
XIO: Fatal IO Error 104 (connection reset by peer) on Xserver ":0.0" after 0 request (o known processed) with o events remaining.

After reading the forum I went into the video settings of the xserver and changed the video to VESA.  This solved my problem and allowed me to boot into the OS.  :-k 

From here I am lost:confused: 

I sownloaded the latest drivers from ATI, but have no clue what I need to do to get all this working.  Please treat me like a rookie...I mean rookie.  Step by step explaination..please.  Thank you all very much.

By the way, I've read the ATI install links but get very confused.

---

### Post by hod139 on 2006-02-28
Have you read [this thread,]("http://ubuntuforums.org/showthread.php?p=408111") and if you have what in there is confusing you?

---

### Post by cabber on 2006-02-28
[QUOTE=hod139]Have you read [this thread,]("http://ubuntuforums.org/showthread.php?p=408111") and if you have what in there is confusing you?[/QUOTE]

Yes I have:  What I am confused about is this:
  Do I want to install Breezys included driver or go to the new 8.22.5?




I have an Athlon 64 so this states that I have to get the older version of libdri.a due to incompatibility:  I downloaded libdri from the link but not sure how to install it.

It also says: Change to Download directory.  not sure how to do this?  

As I mentioned, I'm a novice in the Linux world.  Thanks.

---

### Post by cabber on 2006-02-28
I've downloaded libdri.

I type gunzip libdri.a.gz in the terminal and get:  No such file or directory

---

### Post by hod139 on 2006-02-28
[quote=cabber]Yes I have:  What I am confused about is this:
  Do I want to install Breezys included driver or go to the new 8.22.5?
[/quote]
If you have a laptop, I would suggest the newer drivers as the support for acpi (sleep, suspend, hibernate) is greatly improved.  If not, sticking with the version in Breezy is easiest.

[quote=cabber]
I have an Athlon 64 so this states that I have to get the older version of libdri.a due to incompatibility: I downloaded libdri from the link but not sure how to install it.

It also says: Change to Download directory.  not sure how to do this?  

As I mentioned, I'm a novice in the Linux world.  Thanks.[/quote]
For this step, you must open a console and change to where you downloaded that file using the "cd" command.  Assuming you downloaded the file to the desktop
```

cd ~/Desktop

```
where ~ is a special/wild symbol that means "my home directory".  If you didn't download it to the desktop, you need to use the cd command to go where the file is.  The firefox dowload manager defaults to desktop, so if you didn't change anything the given command should work.

---

### Post by bluevoodoo1 on 2006-02-28
[QUOTE=cabber]It also says: Change to Download directory.  not sure how to do this? [/QUOTE]

If you downloaded the file to your home folder then you're all set, you don't need to change to your download directory. But if you downloaded it to a folder inside your home folder, let's say called goodies, you would write in the terminal
```

cd goodies
```

that will put you in your /home/goodies folder

if you saved it to your desktop it would be

```

cd Desktop

```

which would be your /home/USERNAME/Desktop area.

Edit: too slow.

---

### Post by hod139 on 2006-02-28
[quote=cabber]I've downloaded libdri.

I type gunzip libdri.a.gz in the terminal and get:  No such file or directory[/quote]

This is because you skipped the "Change to download directory step".  My above post shows how to do this (hopefully)

---

### Post by cabber on 2006-02-28
[QUOTE=bluevoodoo1]If you downloaded the file to your home folder then you're all set, you don't need to change to your download directory. But if you downloaded it to a folder inside your home folder, let's say called goodies, you would write in the terminal
```

cd goodies
```

that will put you in your /home/goodies folder

if you saved it to your desktop it would be

```

cd Desktop

```

which would be your /home/USERNAME/Desktop area.

Edit: too slow.[/QUOTE]
It saved to my desktop (default).  When you say console, are you referring to the Terminal?

---

### Post by bluevoodoo1 on 2006-02-28
[QUOTE=cabber]It saved to my desktop (default).  When you say console, are you referring to the Terminal?[/QUOTE]

Hmmm, I didn't mention console :confused:  but yes, type those commands in the terminal. That's what you've been doing right? I mean you've gotten this "I type gunzip libdri.a.gz in the terminal and get: No such file or directory" by typing it in the terminal. 

So, you said you downloaded it to the desktop, then you have to type in the terminal...

cd Desktop

then type gunzip libdri.a.gz

---

### Post by cabber on 2006-02-28
[QUOTE=hod139]If you have a laptop, I would suggest the newer drivers as the support for acpi (sleep, suspend, hibernate) is greatly improved.  If not, sticking with the version in Breezy is easiest.


For this step, you must open a console and change to where you downloaded that file using the "cd" command.  Assuming you downloaded the file to the desktop
```

cd ~/Desktop

```
where ~ is a special/wild symbol that means "my home directory".  If you didn't download it to the desktop, you need to use the cd command to go where the file is.  The firefox dowload manager defaults to desktop, so if you didn't change anything the given command should work.[/QUOTE]
I open a terminal: type cd ~/desktop and get:
bash: cd: /home/cabber/desktop: no such file or directory.  SOrry I know this must be frustrating for you all

---

### Post by bluevoodoo1 on 2006-02-28
[QUOTE=cabber]I open a terminal: type cd ~/desktop and get:
bash: cd: /home/cabber/desktop: no such file or directory.  SOrry I know this must be frustrating for you all[/QUOTE]

just type...

```

cd Desktop

```

it's case sensitive.

---

### Post by hod139 on 2006-02-28
[quote=cabber]I open a terminal: type cd ~/desktop and get:
bash: cd: /home/cabber/desktop: no such file or directory.  SOrry I know this must be frustrating for you all[/quote] 
case is very important in Linux.  You need a capital D in Desktop cd ~/Desktop

edit:  Looks like bluevoodoo1 is way faster than me tonight!!

Note though, that ```
cd Desktop
``` only works if you are in your home dir.  ~/Desktop always works

Edit2: console == terminal

---

### Post by bluevoodoo1 on 2006-02-28
[QUOTE=hod139]case is very important in Linux.  You need a capital D in Desktop cd ~/Desktop

edit:  Looks like bluevoodoo1 is way faster than me tonight!!

Note though, that ```
cd Desktop
```
only works if you are in your home dir.  ~/Desktop always works[/QUOTE]

That is true! I wasn't thinking of that at all!

---

### Post by cabber on 2006-02-28
We are so close.  I can feel it.  Thaks again for your help:D

---

### Post by hod139 on 2006-02-28
[quote=cabber]We are so close.  I can feel it.  Thaks again for your help:D[/quote]

Hopefully the rest works out for you, because my laptop battery is about to die and I need to get some sleep anyways.  Good luck and I'll check back some time tomorrow.

---

### Post by cabber on 2006-02-28
[QUOTE=hod139]case is very important in Linux.  You need a capital D in Desktop cd ~/Desktop

edit:  Looks like bluevoodoo1 is way faster than me tonight!!

Note though, that ```
cd Desktop
``` only works if you are in your home dir.  ~/Desktop always works

Edit2: console == terminal[/QUOTE]
How do I get back to the regular terminal from the cd ~ Desktop?  I aaume one has to finish the commands with the default terminal?

---

### Post by hod139 on 2006-02-28
[quote=cabber]How do I get back to the regular terminal from the cd ~ Desktop? I aaume one has to finish the commands with the default terminal?[/quote] If you mean how do you get back to your home dir, just type "cd" and press enter. But, you can finish the commands from your Desktop.

---

### Post by cabber on 2006-02-28
Well,  I'm back to square one:evil: 

I rebooted and nothing works same error.

When I entered the gunzip line it worked


from the terminal (desktop) I entered the next line then enter and nothing changed

I then entered the third command then enter and nothing changed...is that normal?

---

### Post by bluevoodoo1 on 2006-03-01
[QUOTE=cabber]Well,  I'm back to square one:evil: 

I rebooted and nothing works same error.

When I entered the gunzip line it worked


from the terminal (desktop) I entered the next line then enter and nothing changed

I then entered the third command then enter and nothing changed...is that normal?[/QUOTE]

Perhaps you can paste the contents of your terminal window here, so we can see what is going on?

---

### Post by cabber on 2006-03-01
[QUOTE=bluevoodoo1]Perhaps you can paste the contents of your terminal window here, so we can see what is going on?[/QUOTE]
started new thread above

---

### Post by cabber on 2006-03-01
I believe I have called it quits with Ubuntu.  Too much work to get a simple video card working.  thanks all.

---

### Post by hod139 on 2006-03-01
Sorry to hear you are leaving and that I wasn't enough help.  If you are still willing to give it another go I can do my best to help.  I just won't be able to give instant feedback all the time.

---

### Post by bluevoodoo1 on 2006-03-01
[QUOTE=cabber]I believe I have called it quits with Ubuntu.  Too much work to get a simple video card working.  thanks all.[/QUOTE]

That's too bad. Video cards can be tricky though!... I've been with Ubuntu for about 6 months now and I dual booted for about 3 months just so I could build up the knowledge to set up my printer and wine etc. etc. Anything new takes time to learn. But like hod139 said if you want to give it another shot, I'll try to help too...

EDIT: In fact, I only started messing with improving my video card settings a few weeks ago (if it's not broken, why fix it?!)

---

### Post by cabber on 2006-03-01
[QUOTE=bluevoodoo1]That's too bad. Video cards can be tricky though!... I've been with Ubuntu for about 6 months now and I dual booted for about 3 months just so I could build up the knowledge to set up my printer and wine etc. etc. Anything new takes time to learn. But like hod139 said if you want to give it another shot, I'll try to help too...

EDIT: In fact, I only started messing with improving my video card settings a few weeks ago (if it's not broken, why fix it?!)[/QUOTE]


Thanks guys.  I think the reality is that there are not enough Ubuntu installs with the Radeon X1800XT.  From a few searches I've read, I'm starting to believe that card is not supported.  Which could make for a long experiment.   I have the Dell 24 inch LCD monitor as well and looking at Ubuntu witih "vesa" installed at 1024X768 is a tough pill to swallow.

---

### Post by bluevoodoo1 on 2006-03-01
[QUOTE=cabber] I have the Dell 24 inch LCD monitor as well and looking at Ubuntu witih "vesa" installed at 1024X768 is a tough pill to swallow.[/QUOTE]

You can't get your 24 inch monitor over 1024x768??? Hmmm... I have a 17 inch monitor at 1280x1024 with the vesa driver... 

sudo dpkg-reconfigure xserver-xorg

... that should be able to let you change your resolution, but you've probably tried that... maybe it's something to do with your 64 bit system??

---

### Post by hod139 on 2006-03-01
[quote=cabber]Thanks guys.  I think the reality is that there are not enough Ubuntu installs with the Radeon X1800XT.  From a few searches I've read, I'm starting to believe that card is not supported.  Which could make for a long experiment.   I have the Dell 24 inch LCD monitor as well and looking at Ubuntu witih "vesa" installed at 1024X768 is a tough pill to swallow.[/quote] 
It seems like you were close last time, just had trouble with the 64-bit only dri issue.  I can try and help you through that.  

If you are willing, there are 2 things I want to try.  First is to remove the fglrx driver that you might be using, and use the open source ATI driver instead of the vesa driver.  This will get you at least good 2D.  After that, we can try to get 3D support using the fglrx driver again.

To set up your system to stop using the vesa driver and to start using the open source ATI driver should be very easy.  Here is what you have to do:
```

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #*Select the ATI driver*

```

And then reboot.  This should get you better resolution.  After we get this working, and if you are interested, we can try to get the 3D driver working again.

---

### Post by cabber on 2006-03-01
[QUOTE=hod139]It seems like you were close last time, just had trouble with the 64-bit only dri issue.  I can try and help you through that.  

If you are willing, there are 2 things I want to try.  First is to remove the fglrx driver that you might be using, and use the open source ATI driver instead of the vesa driver.  This will get you at least good 2D.  After that, we can try to get 3D support using the fglrx driver again.

To set up your system to stop using the vesa driver and to start using the open source ATI driver should be very easy.  Here is what you have to do:
```

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #*Select the ATI driver*

```

And then reboot.  This should get you better resolution.  After we get this working, and if you are interested, we can try to get the 3D driver working again.[/QUOTE]

Okay.  I've been down the road with the ati driver to no avail.  I'm open to suggestions.

---

### Post by cabber on 2006-03-01
What if I switch to my GeForce 6600GT?  It is a PCIe card and may be easier to install.  After reading through the ATI FOrum, I truly believe my X1800XT is not compatible with Ubuntu.

---

### Post by hod139 on 2006-03-01
[quote=cabber]Okay.  I've been down the road with the ati driver to no avail.  I'm open to suggestions.[/quote] 
Ok, then lets just skip the open source ATI driver, and install ATI's proprietary fglrx driver (horrible naming isn't it).  We still need to remove the non-working drivers, so you still need to perform the step listed above, but select vesa instead of ATI.

Then, we need to try reinstalling the driver again.
```

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r) #*Okay if it is already installed*
sudo dpkg-reconfigure xserver-xorg #*Select the fglrx driver*

``` 
Next we have to deal with the 64-bit bug.  Since you downloaded the file "libdri.a.gz" to your desktop, I'm going to rewrite the commands in the howto guide specifically for your situation.  Open a console and type
```

gunzip ~/Desktop/libdri.a.gz
sudo cp /usr/X11R6/lib/modules/extensions/libdri.a /usr/X11R6/lib/modules/extensions/libdri.a.old
sudo cp ~/Desktop/libdri.a /usr/X11R6/lib/modules/extensions/

```

and then reboot.

If any of the console commands give an error message let me know, and we can try to debug.

---

### Post by hod139 on 2006-03-01
[quote=cabber]What if I switch to my GeForce 6600GT?  It is a PCIe card and may be easier to install.  After reading through the ATI FOrum, I truly believe my X1800XT is not compatible with Ubuntu.[/quote] 
It seems you are right. X1800 cards are not officially supported.  We could try installing the latest driver if you want.  Though I'm not sure if that will support your card either.

Edit:  Just read that the newest ATI driver doesn't support your card either.

---

### Post by cabber on 2006-03-01
[QUOTE=hod139]Ok, then lets just skip the open source ATI driver, and install ATI's proprietary fglrx driver (horrible naming isn't it).  We still need to remove the non-working drivers, so you still need to perform the step listed above, but select vesa instead of ATI.

Then, we need to try reinstalling the driver again.
```

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r) #*Okay if it is already installed*
sudo dpkg-reconfigure xserver-xorg #*Select the fglrx driver*

``` 
Next we have to deal with the 64-bit bug.  Since you downloaded the file "libdri.a.gz" to your desktop, I'm going to rewrite the commands in the howto guide specifically for your situation.  Open a console and type
```

gunzip ~/Desktop/libdri.a.gz
sudo cp /usr/X11R6/lib/modules/extensions/libdri.a /usr/X11R6/lib/modules/extensions/libdri.a.old
sudo cp ~/Desktop/libdri.a /usr/X11R6/lib/modules/extensions/

```

and then reboot.

If any of the console commands give an error message let me know, and we can try to debug.[/QUOTE]


I'm reinstalling Ubuntu.

---

### Post by cabber on 2006-03-01
[QUOTE=hod139]It seems you are right. X1800 cards are not officially supported.  We could try installing the latest driver if you want.  Though I'm not sure if that will support your card either.

Edit:  Just read that the newest ATI driver doesn't support your card either.[/QUOTE]


Okay,

I'm going with the GeForce card.  I installed it earlier and the NV Drivers installed fine.  The problem was the resolution would only go to 1024X768.  Can you guys helo with getting my resolution fixed with the NVIDIA Card?

---

### Post by hod139 on 2006-03-01
[quote=cabber]I'm reinstalling Ubuntu.[/quote]

Why?  This won't fix anything.  You are right about your ATI card though, it simply has no driver support.  You are forced to use the vesa driver, or switch to your nvidia card.

---

### Post by cabber on 2006-03-01
[QUOTE=hod139]Why?  This won't fix anything.  You are right about your ATI card though, it simply has no driver support.  You are forced to use the vesa driver, or switch to your nvidia card.[/QUOTE]

I uninstalled due to frustration.  I have it installing with the NVIDIA card right now.  Can you assist with getting the proper resolution?

---

### Post by hod139 on 2006-03-01
Hopefully the nvidia card will be easier to set up than ATIs. The nv drivers are the open source drivers, if you want 3D and full card potential you are going to have to install the proprietary nvidia drivers.

I'm going to use [this guide]("http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers") , and method 1.

Open a terminal and type
```

[LEFT]sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`[/LEFT]
      
``` 
then in the terminal type:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

``` 
Then
```

sudo gedit /etc/X11/xorg.conf
``` scroll the file down until you find the line with &#8220;Modules&#8221; and comment out (by putting a "#" before the line) the 2 lines in blue and add Load "glx". It should look like the example below:

```

Section "Module"
[LEFT] Load "bitmap"
Load "dbe"
Load "ddc"
#[COLOR=Blue]Load "dri"[/COLOR]
#[COLOR=Blue]Load &#8220;GLcore&#8221;[/COLOR]
Load "extmod"
Load "freetype"
[COLOR=Lime]Load "glx"[/COLOR]
Load "int10"
Load "record"
Load "type1"
Load "vbe"[/LEFT]
    
 
``` 

Then find the section Device and make sure the word after Driver (shown in red) is &#8220;nvidia&#8221;. Don't worry if your identifier string doesn't match.

```
    [LEFT]Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR=Red]nvidia[/COLOR]"
[/LEFT]
 
```[LEFT]
Then save and restart.
Hopefully that works for you.
[/LEFT]

---

### Post by hod139 on 2006-03-01
If you want the nice nvidia control panel, you will have to open a console and do this:
```

 sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
 
```
 
 Insert the following lines into the new file:
  	```

 	[LEFT][Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;[/LEFT]
 
  
```
 Save the edited file.
 
 Log out and press CTRL+ALT+BACKSPACE (so as to restart the xserver).

---

### Post by cabber on 2006-03-01
Okay,

I'm starting the process.  Ubuntu booted and I'm in the OS.  Resolution is still stuck at 1024X768.  We'll get to that later.

I'll walk through the guide you listed.  

A few questions:  What is the best way to "save" from the terminal, and "reboot or restart"

---

### Post by hod139 on 2006-03-01
[quote=cabber]
A few questions:  What is the best way to "save" from the terminal, and "reboot or restart"[/quote]

Anytime I say "save" or the guide I follow says save, it means save the file opened in the text editor.  It should more accurately state, save and close gedit (or preferred editor).

To restart from the terminal you can type 
```
sudo restart
```
You don't have to use the console to restart the machine, you can always close it and restart using the gnome menu.

---

### Post by cabber on 2006-03-01
[QUOTE=hod139]Hopefully the nvidia card will be easier to set up than ATIs. The nv drivers are the open source drivers, if you want 3D and full card potential you are going to have to install the proprietary nvidia drivers.

I'm going to use [this guide]("http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers") , and method 1.

Open a terminal and type
```

[LEFT]sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`[/LEFT]
      
``` 
then in the terminal type:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

``` 
Then
```

sudo gedit /etc/X11/xorg.conf
``` scroll the file down until you find the line with “Modules” and comment out (by putting a "#" before the line) the 2 lines in blue and add Load "glx". It should look like the example below:

```

Section "Module"
[LEFT] Load "bitmap"
Load "dbe"
Load "ddc"
#[COLOR=Blue]Load "dri"[/COLOR]
#[COLOR=Blue]Load “GLcore”[/COLOR]
Load "extmod"
Load "freetype"
[COLOR=Lime]Load "glx"[/COLOR]
Load "int10"
Load "record"
Load "type1"
Load "vbe"[/LEFT]
    
 
``` 

Then find the section Device and make sure the word after Driver (shown in red) is “nvidia”. Don't worry if your identifier string doesn't match.

```
    [LEFT]Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR=Red]nvidia[/COLOR]"
[/LEFT]
 
```[LEFT]
Then save and restart.
Hopefully that works for you.
[/LEFT][/QUOTE]

Okay, I did this and rebooted and the OS was loading.  I heard the drum intro to the OS and then the screen went blank.  Now it is frozen at a blank screen.

---

### Post by cabber on 2006-03-01
Tried to restart again and got the same thing.  Houston, we have a problem!

---

### Post by hod139 on 2006-03-01
Gah!!  How do you manage to have so many problems :)

Do you see any error messages?  Can you boot into recovery mode and type 
```

less /var/log/Xorg.0.log | grep EE

```

And tell me any error messages that were logged.

---

### Post by cabber on 2006-03-01
[QUOTE=hod139]Gah!!  How do you manage to have so many problems :)

Do you see any error messages?  Can you boot into recovery mode and type 
```

less /var/log/Xorg.0.log | grep EE

```

And tell me any error messages that were logged.[/QUOTE]


In recovery mode, I am at root@ubuntu:~#:  I type the line above and get,

(WW) warning, (EE) error, NI (not implemented), (??) unknown, (ll) Loading extentions MIT Screen saver?

---

### Post by hod139 on 2006-03-01
[quote=cabber]In recovery mode, I am at root@ubuntu:~#:  I type the line above and get,

(WW) warning, (EE) error, NI (not implemented), (??) unknown, (ll) Loading extentions MIT Screen saver?[/quote]

That's fine.  There are no errors.  So, now lets try this:

 sudo nano /etc/X11/xorg.conf
 Add the lines in red at this section of the file (DO NOT add the blue line now):

 Section "Device"
 Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
 Driver "nvidia"
[COLOR=Red] BusID "PCI:1:0:0"[/COLOR]
 [COLOR=Red]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
[COLOR=Blue]Option "Accel" "Off"[/COLOR]
Option "AllowGLXWithComposite" “Off”[/COLOR]
 
 EndSection
 
 CTRL+O to save (yes, use the same name and overwrite the file)
 CTRL+X to exit
 
 [COLOR=Black]If it doesn't solve the problem add the Blue line[/COLOR]

---

### Post by cabber on 2006-03-01
[QUOTE=hod139]That's fine.  There are no errors.  So, now lets try this:

 sudo nano /etc/X11/xorg.conf
 Add the lines in red at this section of the file (DO NOT add the blue line now):

 Section "Device"
 Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
 Driver "nvidia"
[COLOR=Red] BusID "PCI:1:0:0"[/COLOR]
 [COLOR=Red]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
[COLOR=Blue]Option "Accel" "Off"[/COLOR]
Option "AllowGLXWithComposite" “Off”[/COLOR]
 
 EndSection
 
 CTRL+O to save (yes, use the same name and overwrite the file)
 CTRL+X to exit
 
 [COLOR=Black]If it doesn't solve the problem add the Blue line[/COLOR][/QUOTE]

As I mentioned, I'm in the root@ubuntu command.  Do I need to change that to something because when I type the "sudo" line above it says command not found

---

### Post by cabber on 2006-03-01
Nevermind.  Fatfingered a key

---

### Post by cabber on 2006-03-01
Do I just type in the line or is there something special to do to add a line into this.

---

### Post by hod139 on 2006-03-01
[quote=cabber]Do I just type in the line or is there something special to do to add a line into this.[/quote]

After starting Nano, you can use the arrow keys to move the cursor and just start typing to add text.  If you are more familar with another text based editor (e.g. VI) feel free to use that.  Nano tends to be the easiest for simple jobs.

---

### Post by hod139 on 2006-03-01
BTW if you want to access GNOME again you can use this quick fix:
      ```

     [LEFT]sudo nano /etc/X11/xorg.conf
[/LEFT]

```[LEFT]
[/LEFT]
  
  Set the driver back to "nv" instead of "nvidia"
 CTRL+O to save
 CTRL+X to exit

---

### Post by cabber on 2006-03-01
Okay, we are making headway.  Ubuntu did load, but I cannot see it.  I heard the nifty intro, but the monitor is hibernate mode.  just a blank screen.  I move the mouse, turn the onitor on and off, but nothing.  It loaded though.  Should I put in the red line above?

---

### Post by hod139 on 2006-03-01
Yeah, try the red lines and see what happens.  The red lines are for the nvidia driver, not the nv driver.  I added the post about going back to the nv driver just so you can have a working gui.  So, if you are going to add the red lines, also make sure that Driver=nvidia

---

### Post by cabber on 2006-03-01
Put in "Accell" Off and nothing changed.

---

### Post by cabber on 2006-03-01
I changed the driver back to nv and working in the Ubuntu OS now.

---

### Post by hod139 on 2006-03-01
The only problem with the nv driver is you won't have 3D support, and probably can't get a high enough resolution for your huge monitor. Here's the last thing I want you to do before I go to bed. Comment out (using #) 
[COLOR=Red][COLOR=Blue]Option "Accel" "Off"
[/COLOR][/COLOR]in /etc/X11/xorg.conf

Then do this:
 Press CTRL+ALT+F1 (so as to get out of the xserver, i.e. no graphical interface)
 
 Then type:
      ```

     [LEFT]sudo /etc/init.d/gdm stop 

startx -- -verbose 5 -logverbose 5[/LEFT]
  
  
```  and post the output (which you can find under /var/log/Xorg.0.log )

---

### Post by hod139 on 2006-03-01
Just wondering, are you using the DVI connection or the analog?

---

### Post by cabber on 2006-03-01
[QUOTE=hod139]Just wondering, are you using the DVI connection or the analog?[/QUOTE]
DVI

---

### Post by hod139 on 2006-03-01
What happens if you use the analog connection?

---

### Post by hod139 on 2006-03-01
Just so you know, you aren't alone [http://www.nvnews.net/vbulletin/showthread.php?t=50254](http://www.nvnews.net/vbulletin/showthread.php?t=50254)


Maybe tomorrow night we can try to install the latest and greatest nvidia driver, using method 2.

---

### Post by cabber on 2006-03-01
[QUOTE=hod139]The only problem with the nv driver is you won't have 3D support, and probably can't get a high enough resolution for your huge monitor. Here's the last thing I want you to do before I go to bed. Comment out (using #) 
[COLOR=Red][COLOR=Blue]Option "Accel" "Off"
[/COLOR][/COLOR]in /etc/X11/xorg.conf

Then do this:
 Press CTRL+ALT+F1 (so as to get out of the xserver, i.e. no graphical interface)
 
 Then type:
      ```

     [LEFT]sudo /etc/init.d/gdm stop 

startx -- -verbose 5 -logverbose 5[/LEFT]
  
  
```  and post the output (which you can find under /var/log/Xorg.0.log )[/QUOTE]

I did this and typed "/var/log/Xorg.0.log" in the terminal (Ubuntu OS) and got bash: /var/log/Xorg.0.log: Permission denied

---

### Post by hod139 on 2006-03-01
[quote=cabber]I did this and typed "/var/log/Xorg.0.log" in the terminal (Ubuntu OS) and got bash: /var/log/Xorg.0.log: Permission denied[/quote]

type ```
less /var/log/Xorg.0.log
```

---

### Post by cabber on 2006-03-01
[QUOTE=cabber]I did this and typed "/var/log/Xorg.0.log" in the terminal (Ubuntu OS) and got bash: /var/log/Xorg.0.log: Permission denied[/QUOTE]


We can try tomorrow...Thanks.

---

### Post by hod139 on 2006-03-01
It might be as simple as using the standard vga cable or finding a converter for the dvi.  This seems to be a very common problem though.  Anyways, I got to get some sleep.  If you feel brave you can always try method 2 from the [howto]("http://ubuntuforums.org/showthread.php?t=75074") , but it is more complicated.  It would be a shame if the problem is the dvi cable.

---

### Post by cabber on 2006-03-01
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 [email]root@crested.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF]
Current Operating System: Linux ubuntu 2.6.12-10-amd64-k8 #1 Mon Feb 13 12:18:46 UTC 2006 x86_64
Build Date: 10 October 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-amd64-k8 (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:18:46 UTC 2006
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar  1 22:40:26 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
/var/log/Xorg.0.log

---

### Post by hod139 on 2006-03-01
That can't be all the output in the log.  Instead of using less, try an editor 
gedit  /var/log/Xorg.0.log

It might also be better to paste the log into a code block.

---

### Post by hod139 on 2006-03-01
Well, I'm really off to bed now.  Sorry that I'm not able to get video working for you faster.  If your still game to keep trying, I'll do my best tomorrow.

---

### Post by cabber on 2006-03-01
Might take all week to get through this log (1st half)
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 root@crested.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-10-amd64-k8 #1 Mon Feb 13 12:18:46 UTC 2006 x86_64
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-amd64-k8 (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:18:46 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar  1 22:40:26 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2

	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0140 card 0000,0000 rev a2 class 03,00,00 hdr 00
(II) PCI: 05:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd00fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0140) rev 162, Mem @ 0xc8000000/26, 0xc0000000/27, 0xcc000000/24, BIOS @ 0xcd000000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[1] -1	0	0xd0004000 - 0xd00047ff (0x800) MX[B]
	[2] -1	0	0xd0100000 - 0xd0100fff (0x1000) MX[B]
	[3] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[4] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[5] -1	0	0xd0103000 - 0xd0103fff (0x1000) MX[B]
	[6] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[7] -1	0	0xd0104000 - 0xd0104fff (0x1000) MX[B]
	[8] -1	0	0xcd000000 - 0xcd01ffff (0x20000) MX[B](B)
	[9] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[12] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[14] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[15] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[16] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[17] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[19] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[20] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[21] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[22] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[26] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[27] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[1] -1	0	0xd0004000 - 0xd00047ff (0x800) MX[B]
	[2] -1	0	0xd0100000 - 0xd0100fff (0x1000) MX[B]
	[3] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[4] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[5] -1	0	0xd0103000 - 0xd0103fff (0x1000) MX[B]
	[6] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[7] -1	0	0xd0104000 - 0xd0104fff (0x1000) MX[B]
	[8] -1	0	0xcd000000 - 0xcd01ffff (0x20000) MX[B](B)
	[9] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[12] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[14] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[15] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[16] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[17] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[19] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[20] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[21] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[22] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[26] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[27] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[6] -1	0	0xd0004000 - 0xd00047ff (0x800) MX[B]
	[7] -1	0	0xd0100000 - 0xd0100fff (0x1000) MX[B]
	[8] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[9] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[10] -1	0	0xd0103000 - 0xd0103fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xd0104000 - 0xd0104fff (0x1000) MX[B]
	[13] -1	0	0xcd000000 - 0xcd01ffff (0x20000) MX[B](B)
	[14] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[33] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[34] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7667
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nv"
(II) Loading /usr/X11R6/lib/modules/drivers/nv_drv.o
(II) Module nv: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro4 NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 280 NVS, Quadro4 380 XGL, Quadro NVS 50 PCI, GeForce4 448 Go,
	GeForce4 MX Integrated GPU, GeForce3, GeForce3 Ti 200,
	GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600, GeForce4 Ti 4400,
	0x0252, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, 0x0313, GeForce FX 5600SE,
	0x0316, 0x0317, GeForce FX Go5600, GeForce FX Go5650,
	Quadro FX Go700, 0x031D, 0x031E, 0x031F, GeForce FX 5200,
	GeForce FX 5200 Ultra, GeForce FX 5200, GeForce FX 5200SE,
	GeForce FX Go5200, GeForce FX Go5250, GeForce FX 5500,
	GeForce FX 5100, GeForce FX Go5200 32M/64M, 0x0329,
	Quadro NVS 280 PCI, Quadro FX 500/600 PCI, GeForce FX Go53xx Series,
	GeForce FX Go5100, 0x032F, GeForce FX 5900 Ultra, GeForce FX 5900,
	GeForce FX 5900XT, GeForce FX 5950 Ultra, Quadro FX 700,
	GeForce FX 5900ZT, Quadro FX 3000, GeForce FX 5700 Ultra,
	GeForce FX 5700, GeForce FX 5700LE, GeForce FX 5700VE, 0x0345,
	GeForce FX Go5700, GeForce FX Go5700, 0x0349, 0x034B,
	Quadro FX Go1000, Quadro FX 1100, 0x034F, GeForce 6800 Ultra,
	GeForce 6800, GeForce 6800 LE, 0x0043, GeForce 6800 GT, 0x0049,
	Quadro FX 4000, 0x00C0, GeForce 6800, GeForce 6800 LE,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400, 0x00CD,
	Quadro FX 1400, GeForce 6600 GT, GeForce 6600, 0x0142, 0x0143,
	GeForce Go 6600, GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, 0x0147,
	GeForce Go 6600, 0x0149, 0x014B, 0x014C, 0x014D, Quadro FX 540,

	GeForce 6200, 0x0160, GeForce 6200 TurboCache(TM), 0x0162, 0x0163,
	GeForce Go 6200, 0x0163, GeForce Go 6250, GeForce Go 6200,
	GeForce Go 6250, 0x0169, 0x016B, 0x016C, 0x016D, 0x016E, 0x0210,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, 0x0220, 0x0221,
	0x0222, 0x0228
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce 6600 GT found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[6] -1	0	0xd0004000 - 0xd00047ff (0x800) MX[B]
	[7] -1	0	0xd0100000 - 0xd0100fff (0x1000) MX[B]
	[8] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[9] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[10] -1	0	0xd0103000 - 0xd0103fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xd0104000 - 0xd0104fff (0x1000) MX[B]
	[13] -1	0	0xcd000000 - 0xcd01ffff (0x20000) MX[B](B)
	[14] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[33] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[34] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[6] -1	0	0xd0004000 - 0xd00047ff (0x800) MX[B]
	[7] -1	0	0xd0100000 - 0xd0100fff (0x1000) MX[B]
	[8] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[9] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[10] -1	0	0xd0103000 - 0xd0103fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xd0104000 - 0xd0104fff (0x1000) MX[B]
	[13] -1	0	0xcd000000 - 0xcd01ffff (0x20000) MX[B](B)
	[14] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[25] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[26] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[27] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[29] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[30] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[31] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[32] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[35] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[36] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[37] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
0
```

---

### Post by cabber on 2006-03-02
```
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NV(0): Initializing int10
(WW) NV(0): Bad V_BIOS checksum
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 6600 GT"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xC0000000
(--) NV(0): MMIO registers at 0xC8000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/X11R6/lib/modules/libi2c.a
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: DEL  Model: a010  Serial#: 825707603
(II) NV(0): Year: 2005  Week: 42
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 52  vert.: 33
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.607
(II) NV(0): blueX: 0.149 blueY: 0.060   whiteX: 0.312 whiteY: 0.328
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 154.0 MHz   Image Size:  519 x 324 mm
(II) NV(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) NV(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) NV(0): Serial No: T61335AA17LS
(II) NV(0): Monitor name: DELL 2405FPW
(II) NV(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 1024
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(WW) NV(0): config file hsync range 28-96kHz not within DDC hsync ranges.
(WW) NV(0): config file vrefresh range 43-60Hz not within DDC vrefresh ranges.
(II) NV(0): Generic Monitor: Using hsync range of 28.00-96.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1792x1344" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1792x1344" (unknown reason)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1792x1344" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1792x1344" (unknown reason)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1856x1392" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1856x1392" (unknown reason)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1856x1392" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1856x1392" (unknown reason)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1440" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1920x1440" (unknown reason)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1440" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1920x1440" (unknown reason)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (vrefresh out of range)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1400x1050" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1400x1050" (unknown reason)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1400x1050" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1400x1050" (unknown reason)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1400x1050" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1400x1050" (unknown reason)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1400x1050" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1400x1050" (unknown reason)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1440x900" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1440x900" (unknown reason)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1024" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1600x1024" (unknown reason)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1680x1050" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1680x1050" (unknown reason)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1200" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1920x1200" (unknown reason)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1200" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1920x1200" (unknown reason)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1440" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "1920x1440" (unknown reason)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "2048x1536" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "2048x1536" (unknown reason)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "2048x1536" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "2048x1536" (unknown reason)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "2048x1536" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.
(II) NV(0): Not using default mode "2048x1536" (unknown reason)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using mode "1920x1440" (no mode of this name)
(II) NV(0): Not using mode "1920x1200" (no mode of this name)
(II) NV(0): Not using mode "1856x1392" (no mode of this name)
(II) NV(0): Not using mode "1792x1344" (no mode of this name)
(II) NV(0): Not using mode "1680x1050" (no mode of this name)
(II) NV(0): Not using mode "1600x1200" (no mode of this name)
(II) NV(0): Not using mode "1440x900" (no mode of this name)
(II) NV(0): Not using mode "1400x1050" (no mode of this name)
(II) NV(0): Not using mode "1280x854" (no mode of this name)
(II) NV(0): Not using mode "1200x800" (no mode of this name)
(II) NV(0): Not using mode "1152x864" (no mode of this name)
(--) NV(0): Virtual size is 1280x1024 (pitch 1280)
(**) NV(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) NV(0): *Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) NV(0): *Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) NV(0): *Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Mode "1280x800@60": 83.9 MHz, 50.7 kHz, 60.3 Hz
(II) NV(0): Modeline "1280x800@60"   83.91  1280 1312 1624 1656  800 816 824 841
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(--) NV(0): Display dimensions: (520, 330) mm
(--) NV(0): DPI set to (62, 78)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xcc000000 - 0xccffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[2] 0	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B]
	[3] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[9] -1	0	0xd0004000 - 0xd00047ff (0x800) MX[B]
	[10] -1	0	0xd0100000 - 0xd0100fff (0x1000) MX[B]
	[11] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[12] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[13] -1	0	0xd0103000 - 0xd0103fff (0x1000) MX[B]
	[14] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[15] -1	0	0xd0104000 - 0xd0104fff (0x1000) MX[B]
	[16] -1	0	0xcd000000 - 0xcd01ffff (0x20000) MX[B](B)
	[17] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[19] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[28] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[29] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[30] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[32] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[33] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[34] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[35] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[38] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[39] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[40] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[41] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xc0000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(WW) NV(0): Option "NvAGP" is not used
(WW) NV(0): Option "RenderAccel" is not used
(WW) NV(0): Option "IgnoreDisplay" is not used
(WW) NV(0): Option "NoRenderExtention" is not used
(WW) NV(0): Option "AllowGLXWithComposite" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

```

---

### Post by hod139 on 2006-03-02
This log output was for the nv driver, not the nvidia!!  Anyways, lets see if we can get it working.  
First, you said that you had the dell 24 inch monitor.  I assume you mean the [2405FPW]("http://support.dell.com/support/edocs/monitors/2405fpw/En/about.htm#Specifioications") . If I guessed wrong, don't do anything, as the numbers I wrote down are based on that documentation. Just post back with your model number.

Assuming I have the correct monitor specs, here's what I want you to do. Edit /etc/X11/xorg.conf (use nano or gedit) and make the following changes. Red lines are what you need to add. Black lines will be dependent on your machine and don't edit. If you have other lines in one of your sections that I don't have in black, comment them out (using #). There will most likely be a ton of extra *SubSection "Display"* lines in your Screen section, you can delete all those.

```

Section "Monitor"
    Identifier    "CM752ET"
    [COLOR=Red]HorizSync     30-81
    VertRefresh    56-76
ModeLine  "1920x1200" 154.0 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync
[/COLOR]EndSection 

Section "Device"
    Identifier  "Card0" 
    [COLOR=Red]Driver      "nvidia"[/COLOR]
    VendorName  "NVIDIA"
    BoardName   "NVIDIA Geforce 7800 GT"
    [COLOR=Red]Option        "RenderAccel"    "on"
    Option        "DPMS"        "on"
        Option "TwinView"[/COLOR]
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    [COLOR=Red]DefaultColorDepth 24
    Subsection "Display"
        Depth 24
        Modes    "1920x1200"
    EndSubsection[/COLOR]
EndSection

``` 
Then restart and cross your fingers.  If X still doesn't start, paste the contents of /var/log/Xorg.0.log like last time.

---

### Post by cabber on 2006-03-08
Okay,  I'm back.  Took a deep breath and tried to make this all work.  Ended up installing Linspire (for rookies) and was quite pleased with the ease of installation.  Once I got going on that I realized that the VGA versus DVI was my main issue with my display.  Once I got it working with Linspire, I figured I'd give Uuntu another go.  I currently have XP on its own drive, Linspire and Ubuntu 64 booting on another drive.  The resolution is 1920X1200 on all three OS's which is a great start for me.

Now its time to have some fun with Ubuntu.  I'd still like to get the NV or nvidia driver working.  Maybe I'll retrace the steps in this post and see if it all works.

---

