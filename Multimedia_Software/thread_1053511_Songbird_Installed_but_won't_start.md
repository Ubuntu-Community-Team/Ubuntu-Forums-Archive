---
title: "Songbird Installed but won't start"
date: 2009-01-28
forum: Multimedia Software
---

### Post by sebastianrimbaud on 2009-01-28
I installed songbird, I think? Using the script method from this page.

[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

When I ran the last step to run the script I get this error message.

> sebastianrimbaud@Foreigner:~/Desktop$ ./installsongbird.sh
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory

** (zenity:6740): WARNING **: Invalid borders specified for theme pixmap:
        /home/sebastianrimbaud/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory

** (gksudo:6741): WARNING **: Invalid borders specified for theme pixmap:
        /home/sebastianrimbaud/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
0
--2009-01-28 18:32:24--  [http://www.xs4all.nl/~mgj1/Songbird/64.bit](http://www.xs4all.nl/~mgj1/Songbird/64.bit)
Resolving [www.xs4all.nl](www.xs4all.nl)... 194.109.6.92
Connecting to [www.xs4all.nl|194.109.6.92|:80](www.xs4all.nl|194.109.6.92|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-01-28 18:32:24 ERROR 404: Not Found.

head: cannot open `64.bit' for reading: No such file or directory
head: cannot open `64.bit' for reading: No such file or directory
rm: cannot remove `64.bit': No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory

** (zenity:6753): WARNING **: Invalid borders specified for theme pixmap:
        /home/sebastianrimbaud/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
tar: : Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
rm: cannot remove `Songbird*.tar.gz': No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
rm: cannot remove `/usr/bin/Songbird': No such file or directoryGtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory

** (zenity:6772): WARNING **: Invalid borders specified for theme pixmap:
        /home/sebastianrimbaud/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image

It didn't work when I tried to start it from my menu in the sound and video.

So I deleted it and tried to find it in my synaptic manager to make sure I uninstalled it. 

This is the part where I'm not sure I used the script to install it because when I used the synaptic manager it actually let me set it up and asked me which apps I would like to install.

Then when I tried to start it again and nothing happened. So Idk if it's a bug in the one I downloaded from the synaptic manager or if it's the script install I did.

Any advice on this? Also I restarted my computer to check if that would do the trick and nothing.

I'm also kind of new with ubuntu. So any help would be greatly appreciated!

---

### Post by kostkon on 2009-01-28
An easier solution is to just download a [package for it from *getdeb.net*]("http://www.getdeb.net/app/Songbird"). Double-click on it to install it.

[*Getdeb.net*]("http://getdeb.net/") is a safe source, so don't worry ;)

Hope that helps!

---

### Post by albinootje on 2009-01-28
> **kostkon said:**
> An easier solution is to just download a [package for it from *getdeb.net*]("http://www.getdeb.net/app/Songbird").

Just FYI. The getdeb debs for Songbird were also mentioned on the howto page that the OP posted.
The install script, which is just another method trying to have Songbird installed, seems to have troubles.
There's also the 3rd alternative, which is downloading Songbird from the Songbird website, like mentioned here :
> 
Using Songbird without Installing It

If you don't want full integration of Songbird (hidden in a universally accessible place, launcher icon, etc.), you can just download the latest Songbird to your /home/username folder, double-click it (or single-click in Kubuntu), extract the .tar.gz file, enter the new songbird folder in your home directory and double-click (or single-click in Kubuntu) the Songbird file inside. 


---

### Post by sebastianrimbaud on 2009-01-28
Well I had tried other methods of installing it before.

But I'll definitely give them a second chance. Thanks for the quick reply. I'll definitely post back and let everyone know if it worked.

---

### Post by sebastianrimbaud on 2009-01-28
I tried the getdeb.net site and it installed.

It launches now but it doesn't show much.
It lets me open songs in songbird but it's a blank screen.

I uninstalled it using the old tar.gz method or attempted to, but I always have problems with that.

I'll stick to amarok I guess for now until it goes in the respositories or something.

---

### Post by square_monkey on 2009-06-29
I notice you're getting errors with globalmenu-gnome. I got segfault errors with Songbird immediately after installing globalmenu, solved by uninstalling it. Even though in your case the problem clearly affects [Zenity]("http://en.wikipedia.org/wiki/Zenity"), I think the root of the problem is global menu.

---

