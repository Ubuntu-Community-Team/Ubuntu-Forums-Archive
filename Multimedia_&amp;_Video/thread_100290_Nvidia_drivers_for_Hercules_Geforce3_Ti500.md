---
title: "Nvidia drivers for Hercules Geforce3 Ti500?"
date: 2005-12-07
forum: Multimedia &amp; Video
---

### Post by shai on 2005-12-07
Hej,

I got a great problem with installing the nvidia drivers for the above mentioned video card.
I got Kernel 2.6.12.-9-686 running, did try it after installing all available updates, set up the system new and dismissed all the time to get the graphics driver run.
I tried several drivers from the nvidia page and I tried several methods as well, having telefphone support from two guys who are really into Linux at all...
After stopping gdm and using either nvidia-glx-config enable or changing the information in X11/xorg.conf devices section from "nv" to "nvidia" gmd can't be restarted. If I do so the system hangs, black screen with a not blinking cursor in the left upper corner.
To get back to the system I need to change xorg.conf or type disable and that of course in the save mode (or whatever it's called in English).
I really don't get the problem and although I don't need greatest graphic card I would like to get out of my card what it is able to do.
Maybe someone got the same card, experiencing similar problem and got some solution?
Hope to hear from you...
Thomas

---

### Post by Teroedni on 2005-12-07
You should not use the drivers from nvidia website
Its better tu use the ubuntu package ones
have you been able to get back into gdm again?
If so

Start Terminal
You find it in the ubuntu menu .

Then Follow this howtoo
[http://doc.gwos.org/index.php/Install_Nvidia_driver](http://doc.gwos.org/index.php/Install_Nvidia_driver)

---

### Post by shai on 2005-12-08
Hej again,

I followed the instructions; in fact I did it again as I also tried that way a few times before. The new thing was the entry after "smeg".
Anyway, the result unfortunately was the same. Everything works out fine, I reboot, than everything is loaded but it doesn't reach the login window for ubuntu. 
After loading all modules the monitor becomes black, cursor maybe 5 times blinking in the left corner on the top, it stops and the system is frozen.
After new reboot same effect. Then rebooting in recovery mode, reaching console, typing nvdia-glx-config disable --> reboot --> back to Ubuntu.
It's really strange that there seems no way to solve my card problem.
Hope to get some more suggestions;-)
Thomas

---

### Post by shai on 2005-12-12
Does really no one have further suggestions? I posted in another forum too, but no ideas at all...
Hope for help:-)

---

### Post by Teroedni on 2005-12-12
could you try to edit
sudo nano /etc/X11/xorg.conf


set driver as vesa
save and exit


This should get your into gui
and then we could go from there::=)

---

### Post by shai on 2005-12-12
Hej,

two things for getting clear what you mean.
I always get back to graphical apperance but only after disabling nvidia-glx-config or rechange of "nvidia" to "nv" in the xorg.conf. Depends on installation method.
So when and what should I change to vesa? Do you mean the "nv" or "nvidia" and should I do so after installation of the nvidia drivers?
Please make clear so we can go together:)

---

### Post by Teroedni on 2005-12-12
ahh okay
then you dont need vesa

try nvidia driver
and give me the output of 


sudo gedit /var/log/xorg.0.log

---

### Post by shai on 2005-12-12
You find the logfile attached. I also added Xorg.0.log.old if needed. the files were too big for txt-files, so I packed them. I didn't try the installation again, so maybe that's the wrong thing. If neccessary I will try the installation again after the way you suggested at first and give you the output after that when I can't come back to gdm.
Just let me know.

---

### Post by Teroedni on 2005-12-12
you seem to yse a bit worng horinz and vertical

please post your xorg.conf file in [www.pastebin.com](www.pastebin.com)

and link it here

command to get xorg.conf is
sudo gedit /etc/X11/xorg.conf

---

### Post by shai on 2005-12-12
Follow this:-)

[http://pastebin.com/460960](http://pastebin.com/460960)

---

### Post by Teroedni on 2005-12-12
here
taken from your xorg

```
#
Section "Monitor"
#
        Identifier      "Standardbildschirm"
#
        Option    "DPMS"
#
        HorizSync       28-204
#
        VertRefresh     43-60
#
EndSection
```


change to

```
#
Section "Monitor"
#
        Identifier      "Standardbildschirm"
#
        Option    "DPMS"
#
        HorizSync       28-98
#
        VertRefresh     43-160
#
EndSection
```


please dont mind the strange formatting i dont know why it becomes so
the point here is that your vertical was very low
horinzsync 28-98 and vertrefresh 43-160 should work better;)
Now they correspond to your monitor;)

---

### Post by shai on 2005-12-12
Hej again,

amazing results; I changed the stuff you mentioned and tried to change from "nv" to "nvidia" but that didn't work. After rechange to "nv" I could get back to graphical interface and got positive results.
I can change the screen resolution to several modes without mistakes. For example I can now change to 1024*768 what I wanted to with another frequency. This is now at 85Hz. If I try 1280*1024 I can't get 85Hz but 75Hz. 85Hz is possible with my monitor but anyway I don't mind.
Really strange is that I can't use any sreensavers anymore. Probably there is some problem with 3D-stuff? I don't know a good little game to test abilities. Some idea?
Beside I don't have nvidia settings in the menue but I didn't install, right?
I don't need that. What I would need is the understanding what I have installed now. And I don't really understand what I changed in those horicontal and vertical things...
So thanks a lot for making it work so far and I really hope for continuing support;-)

---

### Post by Teroedni on 2005-12-12
Yes i was changing your 
horinzontal scan rate
and your vertical scan rate
They tell your monitor which  frequency it can run on:)


Could you tell me what the name on your monitor is
I need that in order to find out how high your monitor can go;)


as for the nv and nvidia thingy
Nv=open source driver which dont support 3d(games and screensaver

nividia is the driver from nvidia which support your card 3d functions
so if you wanna play games and such you have to use the nvidia driver

---

### Post by shai on 2005-12-12
Ok,

I got that, the Monitor is a Gericom 997N with 19inches...
I would be happy if I could run the whole abilities of my card such as 3D.
But if I would try to install nvidia again I am quite sure that I will get the same black screen again. Or don't you think so?
I am really more concerned about that; so don't give too much enrgy to find out what the monitor can, please;-)
3D and stuff around really seems to be more relevant...

---

### Post by Teroedni on 2005-12-14
IN terminal write

sudo apt-get install nvidia-glx

then write 

sudo nvidia-glx-config enable


again in terminal write
sudo nano /etc/X11/xorg.conf

change horinzsync to 28-98
change vertrefresh to 43-160

ctrl-o(save)
ctrl-x(exit)


Ok:) Now your doon reebot your computer and all should be ok;)

---

### Post by shai on 2005-12-14
Hej again,

now I did what you suggested. I just changed 
horizontal to 30-98 and
vertical to     50-160
as this is what the monitors book says.
Well, but after typing "sudo nvidia-glx-config enable"
the following error message appears:

"Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia."

I don't really understand what that means. And 3D screen savers still don't work...
But I can run my monitor with full abilities it can...
Do you get what that means with md5sum and stuff?
Thanks in advance...

---

### Post by Teroedni on 2005-12-14
yep
your almost there;)

write 
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum


and if that dont work change driver in xorg.conf from nv to nvidia;)

---

### Post by shai on 2005-12-14
Me again,

it's strange, it accepted the line you gave. Output was some kind of number.
Then I restarted, it worked so far but 3D Screenssavers still didn't.
Then I changed in xorg.conf from nv to nividis, rebooted and the system stopped.
The same way I have seen several times before. Cursor in the upper left corner. 
No way out. I didn't get what the line does but this changing from nv to nvidia is always too much as it seems:-(
More ideas?

---

### Post by Teroedni on 2005-12-15
what really?

okey give me output of

sudo nano /var/logs/xorg.0.log

paste thw whole text here
the information there should be enough to see whats wrong

---

### Post by shai on 2005-12-15
Hej again...
That's the log file...
Cu:-)


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux SOJUS 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686
Build Date: 10 October 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-686 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 $Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 15 19:01:45 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Standardbildschirm"
(**) |   |-->Device "NVIDIA Corporation NV20 [GeForce3 Ti 500]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/$(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:

^G Hilfe            ^O Speichern        ^R Datei öffnen     ^Y Seite zurück     ^K Ausschneiden

---

### Post by Teroedni on 2005-12-15
I need the whole file .
You only posted a 1/8 part of it which tell me nothing at all

Pleas post it all
use
[www.pastebin.com](www.pastebin.com)



Quicker way to fix this;)
Go into synaptic
search for nvidia
find the nvidia-glx package there and mark it for reinstall
then do the command if you get the same question again
Lastly if all work we can add monitor refresh rates

---

### Post by shai on 2005-12-17
Hej again,

it took a while this time but I tried some things. First I reinstalled nvidia-glx as you suggested, I told to enable nvidia-glx-config and gave the line md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum and rebooted. Monitor resolution stayed at the wished level which I got from the user's manual.
3D stuff still didn't work. So I changed in xorg.conf from nv to nvidia, rebooting, old system hang-up.
Reboot in recoevery mode, changing back to nv and back to graphical interface.
To make sure it's not a problem of not installed sreensavers or something I installed "Armagetron" but it doesn't start.
I guess that's because of missing 3D-abilities.
Therefore I paste my Xorg.0.log into pastebin.com. 
You find it here: [http://pastebin.com/467652](http://pastebin.com/467652)

To be sure that you get every information I can provide I paste also Xorg.0.log.old.
Find it here: [http://pastebin.com/467654](http://pastebin.com/467654)

So maybe you get some information out. Or is it just something I need to tell the system to activate 3D?
Ubuntu in some ways is cofusing, ins't it?
:-)

---

### Post by shai on 2005-12-20
Hi again,

maybe you are in semester, maybe you are just not there at the moment, but my problem continues. Yesterday I changed the kernel with the help of friend to 2.6.12-386 and after that trying again to install drivers.
Now the error appears in a little different version, doesn't give me a black monitor but telling the X-Server can't be loaded.
So something changed and it tells in the xorg.log.0 file that it is not able to find a screen with a usable configuration.
You find the logfile at [http://pastebin.com/471547](http://pastebin.com/471547)
I filled in the xorg.conf the levels for horizontal and vertical frequency after the recommendations of the manual.
Any ideas?
Thanks in advance:-)
If the pastebin will be erase soon, I can send the logfile via email of course, too...

---

### Post by Teroedni on 2005-12-20
Please check your personal Profile 
I Have sent message to you

---

### Post by shai on 2005-12-20
I can't post the files here...
Therefore I attach them as a gz-file...
You will find the Xorg.0.log and the Xorg.0.log.old there...
Hope we can proceed soon:-)

---

