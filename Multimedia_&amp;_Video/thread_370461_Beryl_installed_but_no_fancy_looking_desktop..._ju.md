---
title: "Beryl installed but no fancy looking desktop... just error messages"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-02-25
Hi everyone,

Not sure if this is the right place for this one but here goes.  I'm trying to get beryl running on a 64 bit edgy install.  I used the automatic script found on the official beryl site (left out the bits that had to do with installing the drivers for my ati card cuz I had already done that already).  So it looks like everything went well, but it beryl will not load as my window manager. If I keep the terminal open while I select beryl as such I get the following output:

 **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension


Has anyone had this problem and fixed it or just knows how I can fix it?

Thanks a lot,
Douglas

---

### Post by Waappu on 2007-02-26
Hi

Do you have these lines in your /etc/X11/xorg.conf file ?
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```


What video card do you have and what guide you followed ?

---

### Post by djrobthaman on 2007-02-26
I think I have it as 

```

Section "Extensions"
        Option "Composite" "0"
EndSection

```

I'll try inputting that when I get home.

Thanks,
Douglas

---

### Post by hustle7 on 2007-02-27
I'm having the same problem as you, djrobthaman. I Think I'm almost there. I hope I'm almost there. I have 3D rendering. My graphic card is nvidia GeForce 4 MX 420. NVIDIA Driver Version: 1.0-9631. Can someone please help me with this dilemma. Thanks!

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

---

### Post by djrobthaman on 2007-02-27
Good luck hustle7.  Hope you get it working.  I still haven't fixed mine yet.  One day we'll have flawless beautiful desktops though.

BTW, if you figure yours out could you post it here.  I'll do the same if I beat you to it.

Douglas

---

### Post by Waappu on 2007-02-27
Hi

For both of you. If you post what guides you have followed , it might give others glue what is wrong.


djrobthaman, you have ATI card. Did you install fglrx driver. If yes , you need install also XGL and login to that session.

hustle7, use envy and install latest nvidia driver
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
then make sure you have these lines in /etc/X11/xorg.conf
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by djrobthaman on 2007-02-27
Waapuu,

I installed using the automatic script located [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI").

I didn't use all of it though because it includes the install of the xorg drivers which I had already done so using the binary walkthrough on the ubuntu wiki.  So here is a copy of the script I run:

```

# Add and install latest beryl and xgl packages
echo "deb http://ubuntu.beryl-project.org/ edgy main" >> /etc/apt/sources.list
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | apt-key add -
aptitude -y update && aptitude -y dist-upgrade
aptitude -y install xserver-xgl beryl emerald emerald-themes
# Now we create a XGL launcher and a session menu entry to start gnome with XGL
echo "#!/bin/sh 
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session" >> /usr/bin/startxgl.sh
chmod +x /usr/bin/startxgl.sh
echo "[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application" >> /usr/share/xsessions/xgl.desktop
# We create an desktop icon and a menu entry, also add beryl-manager to startup programs
echo "[Desktop Entry]
Encoding=UTF-8
Name=Beryl Manager
GenericName=3D Window Manager
Comment=Beryl Manager daemon
Icon=/usr/share/icons/hicolor/scalable/apps/beryl-manager.svg
Exec=beryl-manager
Terminal=false
Type=Application
Categories=GTK;GNOME;Application;Utility;
StartupNotify=true
X-Ubuntu-Gettext-Domain=beryl-manager" > /etc/xdg/autostart/beryl-manager.desktop
cp /etc/xdg/autostart/beryl-manager.desktop /usr/share/applications/beryl-manager.desktop
cp /etc/xdg/autostart/beryl-manager.desktop ~/Desktop/beryl-manager.desktop
echo -e "\n\nBeryl is now installed.\n\nTo run Beryl on Ubuntu startup, please add beryl-manager to your\nstartup programs (System > Preferences > Sessions, and click on\nthe \"startup programs\" tab). Afterwards, please reboot and select \"Options - Sessions - gnome-gxl\" in the login menu to start Ubuntu with XGL.\n\nBackups of /etc/apt/sources.list and /etc/X11/xorg.conf were made:\n    /etc/apt/sources.list.backup.beryl-script\n    /etc/X11/xorg.conf.backup\n\n If you see a ugly gnome in the XGL session add gnome-settings-daemon to the startup programs as you did with beryl-manager before"
fi;

```

Does this help a bit more to see where I went wrong?

Thanks,
Douglas

---

### Post by Waappu on 2007-02-27
Hi

djrobthama, Yes it helps.
You need select XGL session when you login. Now you are not in XGL session because beryl says ```
Detected xserver : AIGLX
```
So press Ctrl+Alt+Backspace. Then find in sessions in your GDM. Then select XGL and login to that session.
And make sure you have these lines in /etc/X11/xorg.conf 
```
Section "Extensions"
        Option "Composite" "0"
EndSection
```
You need disable composition when you are using fglrx driver.

If this not help re-check you drivers install.

---

### Post by djrobthaman on 2007-02-27
Put that option in the file already (composite 0), but I'm not 100% clear about the login.  I know I'm about to reveal how fresh I am with ubuntu / linux, but are you saying that I should login with "XGL" as the user name?

[EDIT]
I reread your post and saw "find in sessions in your GDM. Then select XGL and login to that session."

What is this GDM?  I have the default login screen up which only shows the name input box by itself, then when I type that in the password box pops up.  How would I find this GDM thing?  I've seen somewhere in the settings that I can change the login screen.  Should I do this?

---

### Post by Waappu on 2007-02-27
> **djrobthaman said:**
> Put that option in the file already (composite 0), but I'm not 100% clear about the login.  I know I'm about to reveal how fresh I am with ubuntu / linux, but are you saying that I should login with "XGL" as the user name?

Hi

Press Ctrl+Alt+Backspace. Then you should be in login screen. Some where in that screen is label "sessions" or something like that. press that. Now there should be popup window where should be some thing like these lines
-gnome
-default session
-failsafe gnone
-XGL

select that XGL and then log in normal way. There might be popup that ask do you want this be your default session. select "just for this session" and see if beryl works.
If beryl works and you want always start XGL session you can answer to that popup make system default session.

Sorry my English. And also sorry about not accurate explain because I'm currently in windows machine :(

Edit:
GDM is the GNOME Display Manager, a graphical login program.
[http://en.wikipedia.org/wiki/GNOME_Display_Manager](http://en.wikipedia.org/wiki/GNOME_Display_Manager)

---

### Post by djrobthaman on 2007-02-27
Thanks Waappuu,

I'll try this when I'm at home.  Hopefully I can find this "sessions" label.

Douglas

---

### Post by Waappu on 2007-02-27
> **djrobthaman said:**
> Thanks Waappuu,

I'll try this when I'm at home.  Hopefully I can find this "sessions" label.

Douglas

=)

Ok, maybe better to say button than label. My English isn't so good:(

---

### Post by hustle7 on 2007-02-27
> **Waappu said:**
> Hi

For both of you. If you post what guides you have followed , it might give others glue what is wrong.


djrobthaman, you have ATI card. Did you install fglrx driver. If yes , you need install also XGL and login to that session.

hustle7, use envy and install latest nvidia driver
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
then make sure you have these lines in /etc/X11/xorg.conf
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

I already installed Alberto Milone's Envy and it installed NVIDIA Driver Version: 1.0-9631. I noticed that you mention to use the xgl session but it doesn't show up as an option at the login screen in session. I installed Beryl using the guide from this page: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Configuration](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Configuration)

** Installing Xgl and Beryl**

Use Synaptic or Adept to install the xserver-xgl package, or use the command line

$ sudo apt-get install xserver-xgl

Next, install the beryl and emerald-themes packages

$ sudo apt-get install beryl emerald-themes 
.

---

### Post by Waappu on 2007-02-27
> **hustle7 said:**
> I already installed Alberto Milone's Envy and it installed NVIDIA Driver Version: 1.0-9631. I noticed that you mention to use the xgl session but it doesn't show up as an option at the login screen in session. I installed Beryl using the guide from this page: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Configuration](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Configuration)

** Installing Xgl and Beryl**

Use Synaptic or Adept to install the xserver-xgl package, or use the command line

$ sudo apt-get install xserver-xgl

Next, install the beryl and emerald-themes packages

$ sudo apt-get install beryl emerald-themes 
.

Hi

I think you should use this guide and go for AIGLX. 
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)
and also remove XGL by typing in terminal
```
sudo aptitude remove xserver-xgl
```
I must say that I don't have much knowledge about nvidia.

---

### Post by hustle7 on 2007-02-27
> **Waappu said:**
> Hi

I think you should use this guide and go for AIGLX. 
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)
and also remove XGL by typing in terminal
```
sudo aptitude remove xserver-xgl
```
I must say that I don't have much knowledge about nvidia.

Isn't that for ATI graphic cards? I've tried alot of guides including the guide you just recommended. No I'm disappointed again. I thought I was almost there. 'sigh':(

---

### Post by Waappu on 2007-02-27
> **hustle7 said:**
> Isn't that for ATI graphic cards? I've tried alot of guides including the guide you just recommended. No I'm disappointed again. I thought I was almost there. 'sigh':(

Hi

No that guide is for nvidia as post subject say
"Beryl with latest nvidia drivers and EDGY's built in AIGLX (no XGL) "

Check this:
first type in terminal```
sudo nvidia-xconfig --add-argb-glx-visuals
```
then type in terminal```
gksudo gedit /etc/X11/xorg.conf
```
and check that you have these lines in file
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```
also check that there isn't line```
Load "dri"
```

check that you have these lines under Section "Module"```
	Load	"glx"
	Load	"vbe"
	Load	"dbe"
```

Edit

then press Ctrl+Alt+Backspace to restart X

---

### Post by hustle7 on 2007-02-27
> **Waappu said:**
> Hi

No that guide is for nvidia as post subject say
"Beryl with latest nvidia drivers and EDGY's built in AIGLX (no XGL) "

Check this:
first type in terminal```
sudo nvidia-xconfig --add-argb-glx-visuals
```
then type in terminal```
gksudo gedit /etc/X11/xorg.conf
```
and check that you have these lines in file
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```
also check that there isn't line```
Load "dri"
```

check that you have these lines under Section "Module"```
	Load	"glx"
	Load	"vbe"
	Load	"dbe"
```

Edit

then press Ctrl+Alt+Backspace to restart X


I'm confused now. I tried these commands here and reconfigured my xorg.conf. I was able to start up beryl, but it was very sluggish and kept freezing up. What am I doing wrong? I haven't tried the guide other guide yet because of fear of the blue screen.

---

### Post by Dylnuge on 2007-02-27
I am also having this problem (sorry for posting here, got no replys in my other thread).

Using the guide linked to above (the HOWTO Nvidia). Here is the error:

```
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

```

Also, I have tried everything recommended here. I really can't get this to work.

Thanks,
Dylan

PS: Tried guide above and it worked-sort of. Beryl works fine, but Emerald fails to work, meaning no themes, and worse off, no title bars.

---

### Post by Waappu on 2007-02-27
> **Dylnuge said:**
> I am also having this problem (sorry for posting here, got no replys in my other thread).

Using the guide linked to above (the HOWTO Nvidia). Here is the error:

```
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

```

Also, I have tried everything recommended here. I really can't get this to work.

Thanks,
Dylan

PS: Tried guide above and it worked-sort of. Beryl works fine, but Emerald fails to work, meaning no themes, and worse off, no title bars.

Hi

See if this helps you
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631)

---

### Post by Waappu on 2007-02-27
> **hustle7 said:**
> I'm confused now. I tried these commands here and reconfigured my xorg.conf. I was able to start up beryl, but it was very sluggish and kept freezing up. What am I doing wrong? I haven't tried the guide other guide yet because of fear of the blue screen.

See if these helps you
[http://liquidweather.net/howto/index.php?id=106](http://liquidweather.net/howto/index.php?id=106)
[http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl+howto](http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl+howto)

---

### Post by hustle7 on 2007-02-27
Thanks Waappu! You're a life saver! I finally have Beryl up and running and I love it.  You don't know how much this means to me. I now can switch between xgl, aigxl, and nvidia. God bless you!

---

### Post by tjtansey on 2007-02-27
> **Waappu said:**
> Hi

djrobthama, Yes it helps.
You need select XGL session when you login. Now you are not in XGL session because beryl says ```
Detected xserver : AIGLX
```
So press Ctrl+Alt+Backspace. Then find in sessions in your GDM. Then select XGL and login to that session.
And make sure you have these lines in /etc/X11/xorg.conf 
```
Section "Extensions"
        Option "Composite" "0"
EndSection
```
You need disable composition when you are using fglrx driver.

If this not help re-check you drivers install.

I also have an ATI card and tried following along here, but when I restart X I don't have the option of a XGL session.  Any Ideas?

---

### Post by hustle7 on 2007-02-28
How do I get xgl on my login screen as a session?

---

### Post by Waappu on 2007-02-28
> **hustle7 said:**
> How do I get xgl on my login screen as a session?

Hi

See this:
[Adding an Xgl login session]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Adding_an_Xgl_login_session")


EDIT:

hustle7, if beryl works for you you don't need that XLG. Just forget it

---

### Post by hustle7 on 2007-02-28
> **Waappu said:**
> Hi

See this:
[Adding an Xgl login session]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Adding_an_Xgl_login_session")


EDIT:

hustle7, if beryl works for you you don't need that XLG. Just forget it

Okay. Thanks. I hate to be a nuisance but I'm having trouble using my emerald themes that come with beryl. I click on a theme but nothing happens. I even reloaded the Window Decorator. Am I missing something?

---

### Post by Waappu on 2007-02-28
Hi

Open Emerald Setting Manager. There you can change themes and also create your own.
I think command to run Emerald setting manager from terminal is ```
emerald-settings
```

PS: Maybe I didn't understand your problem right

---

### Post by tjtansey on 2007-02-28
I now have the Xgl session available in GDM but when I select it the screen flashes and I go right back out to the login?

---

### Post by djrobthaman on 2007-02-28
Whoa... this thing has gotten monstrously long.  Anyway, just wanted to say thanks for  all the help from everyone here.  I got beryl to work using the options menu on the login screen.

By the way, for some reason XGL has made the desktop a weirdly gray (more details and screenshots [here]("http://www.ubuntuforums.org/showthread.php?p=2228718#post2228718")).

If anybody knows how to fix that so that it looks like it did before I'd really appreciate it.

Thanks,
Douglas

---

### Post by hustle7 on 2007-03-01
> **Waappu said:**
> Hi

Open Emerald Setting Manager. There you can change themes and also create your own.
I think command to run Emerald setting manager from terminal is ```
emerald-settings
```

PS: Maybe I didn't understand your problem right

I can't run emerald-settings from terminal. Maybe I should un-install beryl then re-install.

---

