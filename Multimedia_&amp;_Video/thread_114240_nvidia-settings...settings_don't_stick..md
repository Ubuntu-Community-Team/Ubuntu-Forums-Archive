---
title: "nvidia-settings...settings don't stick."
date: 2006-01-08
forum: Multimedia &amp; Video
---

### Post by kudu on 2006-01-08
How do you make nvidia-settings "stick" ?? I always have to reset them eveytime I reboot. Is there a way to make "sync to vblank" stay enabled ??

I always have to run nvidia-settings to get it sync'ed even though it is still checked enabled. Bothersome to say the least.

kudu...out

---

### Post by mo_x on 2006-01-08
nvidia-settings --load-config-only
You can place it in your .xinitrc file. See the nvidia-setttings man page.

---

### Post by kudu on 2006-01-08
Thanks for the tip, I'll check out the man page.

How exactly do I put it in my .xinitrc file ? Just add <nvidia-settings --load-config-only> to the bottom of the file ? Hmmm...also where is .xinitrc ? I have a /etc/X11/xinit/xinitrc , is that what you refer to ? Or should I have a .xinitrc in home ? I don't but I can easily make one up.

kudu appreciates you...out

---

### Post by kudu on 2006-01-08
There isn't a man page for nvidia-settings, but there is nvidia-settings --help which explains briefly the nvidia-settings --load-config-only option.

However, .xinitrc is still a mystery file. It doesn't exist anywhere. I tried making one up in my home directory but it didn't work. I simply saved a file called .xinitrc in my home directory containg `nvidia-settings --load-config-only` but it didn't do the trick.

There's an xinitrc file in /etc/X11/xinit. Should I edit that one, and if so, how ?

kudu...out

---

### Post by mo_x on 2006-01-09
I installed the nvidia drivers from their website and have a nvidia-settings man page. 

3. Loading Settings Automatically
 The NVIDIA X driver does not preserve values set with nvidia-settings between runs of the X server (or even between logging in and logging out of X, with xdm(1), gdm, or kdm ). This is intentional, because different users may have different preferences, thus these settings are stored on a per-user basis in a configuration file stored in the user's home directory. 

 The configuration file is named ~/.nvidia-settings-rc. You can specify a different configuration file name with the --config commandline option. 

 After you have run nvidia-settings once and have generated a configuration file, you can then run: 

 
       nvidia-settings --load-config-only 

 at any time in the future to upload these settings to the X server again. For example, you might place the above command in your ~/.xinitrc file so that your settings are applied automatically when you log in to X. 

 Your .xinitrc file, which controls what X applications should be started when you log into X (or startx), might look something like this: 

     nvidia-settings --load-config-only &
     xterm &
     evilwm


 or: 

     nvidia-settings --load-config-only &
     gnome-session


 If you do not already have an ~/.xinitrc file, then chances are that xinit(1) is using a system-wide xinitrc file. This system wide file is typically here: 

     /etc/X11/xinit/xinitrc


 To use it, but also have nvidia-settings upload your settings, you could create an ~/.xinitrc with the contents: 

     nvidia-settings --load-config-only &
     . /etc/X11/xinit/xinitrc


 System administrators may choose to place the nvidia-settings load command directly in the system xinitrc script. 

 Please see the xinit(1) man page for further details of configuring your ~/.xinitrc file.

---

### Post by kudu on 2006-01-09
[QUOTE=mo_x]I installed the nvidia drivers from their website and have a nvidia-settings man page. 

3. Loading Settings Automatically
 The NVIDIA X driver does not preserve values set with nvidia-settings between runs of the X server (or even between logging in and logging out of X, with xdm(1), gdm, or kdm ). This is intentional, because different users may have different preferences, thus these settings are stored on a per-user basis in a configuration file stored in the user's home directory. 

 The configuration file is named ~/.nvidia-settings-rc. You can specify a different configuration file name with the --config commandline option. 

 After you have run nvidia-settings once and have generated a configuration file, you can then run: 

 
       nvidia-settings --load-config-only 

 at any time in the future to upload these settings to the X server again. For example, you might place the above command in your ~/.xinitrc file so that your settings are applied automatically when you log in to X. 

 Your .xinitrc file, which controls what X applications should be started when you log into X (or startx), might look something like this: 

     nvidia-settings --load-config-only &
     xterm &
     evilwm


 or: 

     nvidia-settings --load-config-only &
     gnome-session


 If you do not already have an ~/.xinitrc file, then chances are that xinit(1) is using a system-wide xinitrc file. This system wide file is typically here: 

     /etc/X11/xinit/xinitrc


 To use it, but also have nvidia-settings upload your settings, you could create an ~/.xinitrc with the contents: 

     nvidia-settings --load-config-only &
     . /etc/X11/xinit/xinitrc


 System administrators may choose to place the nvidia-settings load command directly in the system xinitrc script. 

 Please see the xinit(1) man page for further details of configuring your ~/.xinitrc file.[/QUOTE]


Thanks for the info, I'll give it a shot and let you know how it worked.  :)

---

### Post by Chuffinora on 2006-01-09
I also would like to have my settings stay after reboot/X restart. I cannot seem to get this to work.  I have created a .xinitrc as stated and put it into /etc/X11/xinit/

it did not work.  I also tried editing my xintrc file thus

nvidia-settings --load-config-only &
. /etc/X11/Xsession

didn't work either.  I have checked I have ~/.nvidia-settingsrc

-rw-r--r--  1 mythtv mythtv 1100 2006-01-08 17:18 /home/mythtv/.nvidia-settings-rc

---

### Post by kudu on 2006-01-09
[QUOTE=Chuffinora]I also would like to have my settings stay after reboot/X restart. I cannot seem to get this to work.  I have created a .xinitrc as stated and put it into /etc/X11/xinit/

it did not work.  I also tried editing my xintrc file thus

nvidia-settings --load-config-only &
. /etc/X11/Xsession

didn't work either.  I have checked I have ~/.nvidia-settingsrc

-rw-r--r--  1 mythtv mythtv 1100 2006-01-08 17:18 /home/mythtv/.nvidia-settings-rc[/QUOTE]

Doesn't work for me either! Pain in the butt!!

kudu...out

---

### Post by mo_x on 2006-01-10
I must say that I haven't tried it myself :) Just thought I would share the information.
I will give it a try and let you know my findings.

---

### Post by mo_x on 2006-01-10
It seems ~/.xinitrc is only used when you use startx. When using a display manager your ~/.xsession is used. This route seems to complicated.
Both GNOME and KDE can run programs on startup, that may be a better option. For KDE you can create a link to an application in the ~/.kde/Autostart directory. GNOME has some graphical tool to do the same (I use KDE so I don't know where to find it).

---

### Post by kudu on 2006-01-10
Hmm...Anyone reading this know how to set start up applications in gnome ?

---

### Post by kudu on 2006-01-10
Figured it out...

# System -> Preferences -> Sessions
# Sessions

Startup Programs Tab -> Add/Edit/Delete

I simply added: nvidia-settings --load-config-only

Works now. Info was found in the Hoary starters guide. A big thanks to mo_x for the hint.

kudu...out

---

### Post by GerryGG on 2008-07-04
Adding the "nvidia-settings --load-config-only" to my System>Preferences>Sessions>Startup Programs does load up my nvidia-settings on startup. But, each time the screensaver runs the settings are turned off again. 

This thread

[http://ubuntuforums.org/showthread.php?t=662679&highlight=nvidia-settings+xinitrc](http://ubuntuforums.org/showthread.php?t=662679&highlight=nvidia-settings+xinitrc)

explains that to use the .xinitrc file (as suggested in the Nvidia-Settings User Guide) one must make the file executable. After I made it executable, it also was able to load up the Nvidia-Settings at start-up. But, whether using the System>Preferences>Sessions>Startup Programs option or the .xinitrc option, neither of these solutions retained the Nvidia settings after the screensaver had kicked in. This site

[https://bugs.launchpad.net/gnome-screensaver/+bug/33214](https://bugs.launchpad.net/gnome-screensaver/+bug/33214)

explains that there is a bug in GNOME screensaver that is preventing the nvidia-settings from coming back after the screensaver kicks in. There also are a couple of work arounds posted there (I haven't tried them yet). It sounds like this bug might be addressed with the fall release of Ubuntu (let's hope).

---

