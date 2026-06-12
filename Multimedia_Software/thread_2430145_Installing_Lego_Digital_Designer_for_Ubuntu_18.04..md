---
title: "Installing Lego Digital Designer for Ubuntu 18.04.3 LTS"
date: 2019-10-28
forum: Multimedia Software
---

### Post by nocruoro on 2019-10-28
Former windows user here trying to find a user friendly way to install and play with a brick building program called Lego Digital Designer.
[https://lego-digital-designer.en.softonic.com/](https://lego-digital-designer.en.softonic.com/)


I'm not good at using the built in Terminal (what windows users call a Command Prompt) to install things like Wine although thats what people mention is needed ([https://www.eurobricks.com/forum/index.php?/forums/topic/85670-is-there-a-brick-building-program-for-linux/](https://www.eurobricks.com/forum/index.php?/forums/topic/85670-is-there-a-brick-building-program-for-linux/)) Google searches also refer to Wine as needed. 

I've browsed the built in Ubuntu Software store but it only has a brick program called **LeoCAD** but it's a complete *wimp* compared to how Lego Digital Designer works and how many advanced bricks are available.

Any help. This is one of my favorite past-time programs to fiddle with as a adult lego collector after working hours.

---

### Post by nocruoro on 2019-10-29
bump

---

### Post by Autodave on 2019-10-29
The software store should have *Wine* listed for install.  You have to install Wine and then, from within Wine, install your Lego program.

---

### Post by nocruoro on 2019-10-30
[SIZE=3]> **Autodave said:**
> The software store should have *Wine* listed for install.  You have to install Wine and then, from withinrWine, install your Lego program.

Does wine use a browser or do i download through chrome and launch the lego installation through wine?

i want to be careful

---

### Post by Autodave on 2019-10-30
You will have to d-l the program.  Then you will use Wine to install the program.

---

### Post by nocruoro on 2019-11-01
> **Autodave said:**
> You will have to d-l the program.  Then you will use Wine to install the program.


[SIZE=2]Didn't work tried installing wine with this from here [https://linuxconfig.org/install-wine-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/install-wine-on-ubuntu-18-04-bionic-beaver-linux)[/SIZE]
> 
Install Wine from Ubuntu repository
To install Wine from a standard Ubuntu repository [open up terminal]("https://linuxconfig.org/how-to-open-a-terminal-on-ubuntu-bionic-beaver-18-04-linux") and enter:FOR 64bit:
$ sudo apt install wine64

Check your version once the Wine installation is complete:$ wine --version
wine-3.0

[SIZE=2]After that i tried to check my computer, no way to launch wine. Tried installing both from software store too. Both failed to launch. and Wine didn't show up if i right clicked the installation file. Why is the no easy way instead of learning/digging through folders and code. 

My brain hurts.[/SIZE]

---

### Post by Holger_Gehrke on 2019-11-02
Since wine is (somewhat) useless without programs written for Windows and doesn't have a graphical UI, it does not show up in the GUI. I normally start installers from the command line; the calls that an Installer makes to the Windows-API to create menu-items get translated into the creation of a .desktop-file for running the installed program with wine. So what you'd do would be something like 'cd ~/Downloads; wine setupldd-pc-4_3_12.exe' (replace the directory where you put the installer for ~/Downloads and the actual name of your installer for setupldd-pc-4_3_12.exe) and you'd end up with a shortcut on the desktop and in the Menu (or whatever else your Desktop Environment offers ).

The [entry for this program in the Wine-AppDB]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=35559&iTestingId=99078") has a few things to say about it: it says to use a 32-bit Wineprefix and to install Adobe Flash into that prefix using winetricks. Though I've followed those instructions all I got for my trouble was a quick flash of a window popping up followed by a segmentation fault. Either I got something wrong or there's some kind of regression, the report in the AppDB which rated LDD "gold" was made in 2017 using wine 1.6 ...

Also, further development of LDD was stopped though it still is available for download.

And while I don't use it myself, I've read good things about playonlinux, which is kind of a graphical frontend for Wine.

Holger

---

### Post by nocruoro on 2019-11-03
> **Holger_Gehrke said:**
> 
And while I don't use it myself, I've read good things about **playonlinux**, which is kind of a graphical frontend for Wine.

Holger

If i use Playonlinux, do i install LDD game with 32 bit or 64 bit virtual drive my machine is 64 bit.

EDIT: New problem cant get past sad face error what did i do wrong?

heres the debug log from playon linux
> [11/03/19 14:40:06] - Running wine- --version (Working directory : /usr/share/playonlinux/python)wine-3.0 (Ubuntu 3.0-1ubuntu1)


PlayOnLinux logfile
-------------------
Date: 11/03/19 14:40:06


> PlayOnLinux Version
  4.2.12
> uname -a
  Linux kristjan-Aspire-F5-522 5.0.0-32-generic #34~18.04.2-Ubuntu SMP Thu Oct 10 10:36:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
> lsb_release -a
  
> wine --version
  wine-3.0 (Ubuntu 3.0-1ubuntu1)
> POL_WINEVERSION
  
> WINEPREFIX
  /home/kristjan/.PlayOnLinux//wineprefix/lego
> Distribution
  Ubuntu 18.04.3 LTS
> glxinfo \| grep rendering
  direct rendering: Yes
> glxinfo \| grep renderer
      GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: AMD STONEY (DRM 3.27.0, 5.0.0-32-generic, LLVM 8.0.0)
> OpenGL libs (Direct rendering testing)
  check_dd_x86 missing, test skipped
  check_dd_amd64 missing, test skipped


[11/03/19 14:40:06] - This is a 32bits prefix!
[11/03/19 14:40:07] - Running wine- cmd /c echo %ProgramFiles% (Working directory : /usr/share/playonlinux/python)
C:\Program Files
[11/03/19 14:40:17] - Running wine- /home/kristjan/Downloads/SetupLDD-PC-4_2_5.exe (Working directory : /)
002e:err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
[11/03/19 14:41:18] - Running wine- winepath -u C:\\users\\kristjan\\Desktop (Working directory : /home/kristjan/.PlayOnLinux/wineprefix/lego/drive_c)
/home/kristjan/.PlayOnLinux//wineprefix/lego/dosdevices/c:/users/kristjan/Desktop
[11/03/19 14:41:41] - Running wine- LDD.exe (Working directory : /home/kristjan/.PlayOnLinux/wineprefix/lego/drive_c/Program Files/LEGO Company/LEGO Digital Designer)
[11/03/19 14:41:53] - Running wine- LDD.exe (Working directory : /home/kristjan/.PlayOnLinux/wineprefix/lego/drive_c/Program Files/LEGO Company/LEGO Digital Designer)
[11/03/19 14:42:06] - Running wine- LDD.exe (Working directory : /home/kristjan/.PlayOnLinux/wineprefix/lego/drive_c/Program Files/LEGO Company/LEGO Digital Designer)

I also finished installing flash player but the [http://isflashinstalled.com/](http://isflashinstalled.com/) says nope for me although i can see it in my list after following this guide [https://computingforgeeks.com/how-to-install-latest-adobe-flash-player-on-ubuntu-18-04-linux/](https://computingforgeeks.com/how-to-install-latest-adobe-flash-player-on-ubuntu-18-04-linux/)
how do i get this to work?

---

### Post by nocruoro on 2019-11-04
bump


propblem still not solved

---

### Post by nocruoro on 2019-11-07
Im not just doing it for myself but also for two of my cousins who like playing with lego games

---

### Post by nocruoro on 2019-12-22
[SIZE=4]**bump still need help with this**[/SIZE]

---

### Post by nocruoro on 2019-12-24
bump

---

### Post by CelticWarrior on 2019-12-25
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=3331](https://appdb.winehq.org/objectManager.php?sClass=application&iId=3331)

The above shows which version have been tested and how did they fared. Gold and Platinum OK, anything below Gold is almost always a waste of time.
Software always runs best natively. With emulation or a compatibility layer like Wine is always hit and miss.

Perhaps better to have a dual-boot if you really need to run Windows software or the next best thing, if the hardware is capable enough, create a Virtual Machine and install Windows.

---

