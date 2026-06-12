---
title: "Problem starting Shotcut"
date: 2023-11-23
forum: Multimedia Software
---

### Post by satimis on 2023-11-23
Hi all,

Ubuntu 22.04 desktop

Install Shotcut on shotcut-linux-x86_64-230929.AppImage but on starting it.

**[COLOR="#FF0000"]Warning:[/COLOR]**```

qt.qpa.plugin: Could not load the Qt platform plugin "wayland" in "" even though it was found.
libDeckLinkAPI.so: cannot open shared object file: No such file or directory
```

Please advise how to fix the problem.

Thanks

---

### Post by jimmyrus on 2023-11-23
> **satimis said:**
> Hi all,

Ubuntu 22.04 desktop

Install Shotcut on shotcut-linux-x86_64-230929.AppImage but on starting it.

**[COLOR=#FF0000]Warning:[/COLOR]**```

qt.qpa.plugin: Could not load the Qt platform plugin "wayland" in "" even though it was found.
libDeckLinkAPI.so: cannot open shared object file: No such file or directory
```

Please advise how to fix the problem.

Thanks
I put what you posted into google and got this [https://forum.shotcut.org/t/qt-qpa-plugin-could-not-load-the-qt-platform-plugin-wayland-in-even-though-it-was-found-qt-qpa-plugin-could-not-load-the-qt-platform-plugin-xcb-in-even-though-it-was-found/32003](https://forum.shotcut.org/t/qt-qpa-plugin-could-not-load-the-qt-platform-plugin-wayland-in-even-though-it-was-found-qt-qpa-plugin-could-not-load-the-qt-platform-plugin-xcb-in-even-though-it-was-found/32003) 

did you try to do anything like that? their forums have information about that along with them saying to try flatpak instead.

---

### Post by ajgreeny on 2023-11-23
When you login to Ubuntu, after entering your password but before hitting Enter to actually login, click on the cogwheel in the login-box to change to using X11 instead of wayland.

I may have the wording wrong as I don't use Ubuntu, Xubuntu being my choice which can not yet use Wayland, but I think the Wayland login is called just **Ubuntu** with the **X11 Ubuntu** version being shown as exactly that; it should be obvious.

---

### Post by satimis on 2023-11-23
> **jimmyrus said:**
> I put what you posted into google and got this [https://forum.shotcut.org/t/qt-qpa-plugin-could-not-load-the-qt-platform-plugin-wayland-in-even-though-it-was-found-qt-qpa-plugin-could-not-load-the-qt-platform-plugin-xcb-in-even-though-it-was-found/32003](https://forum.shotcut.org/t/qt-qpa-plugin-could-not-load-the-qt-platform-plugin-wayland-in-even-though-it-was-found-qt-qpa-plugin-could-not-load-the-qt-platform-plugin-xcb-in-even-though-it-was-found/32003) 

did you try to do anything like that? their forums have information about that along with them saying to try flatpak instead.
Hi @jimmyrus,

Thanks for your advice

The strange thing happened here is, disregarding the warning, Shortcut started but I couldn't add it to "Favorite".  Each time I have to start Shortcut on Terminal

Regards

---

### Post by satimis on 2023-11-23
> **ajgreeny said:**
> When you login to Ubuntu, after entering your password but before hitting Enter to actually login, click on the cogwheel in the login-box to change to using X11 instead of wayland.

I may have the wording wrong as I don't use Ubuntu, Xubuntu being my choice which can not yet use Wayland, but I think the Wayland login is called just **Ubuntu** with the **X11 Ubuntu** version being shown as exactly that; it should be obvious.
Hi,

I install Shotcut on Ubuntu 22.04 running as VM of VirtualBox

There are 2 options before hitting login
ubuntu
ubuntu on Xorg

I have tried both without result.

Each time I have start Shotcut on Terminal running;```

$ ./shotcut-linux-x86_64-230929.AppImag

```

Regards

---

### Post by ajgreeny on 2023-11-24
Have you made sure that the Appimage file is executable? 
Where in your home does it sit? Normally it would be in ~/Downloads in your home so that command you show will never work, assuming your terminal pwd is you as user.

---

### Post by satimis on 2023-11-24
> **ajgreeny said:**
> Have you made sure that the Appimage file is executable? 
Where in your home does it sit? Normally it would be in ~/Downloads in your home so that command you show will never work, assuming your terminal pwd is you as user.
Yes.  It can be started on Terminal running;
$ ./Downloads/shotcut-linux-x86_64-230929.AppImage 
Please see screenshot attached

shotcut-linux-x86_64-230929.AppImage is on Downloads folder

---

### Post by ajgreeny on 2023-11-24
I have no idea what that screenshot is supposed to show us; it means nothing to me as I've never used shortcut.

However, as you say you're now able to start it, you could create a launcher for it, ie, a shortcut.desktop file in ~/.local/share/applications which would mean shortcut should then appear in the menu.

I'm not on a Linux box at the moment so will get back if you need more help with the content of the launcher which is a simple text file.

Perhaps this is now solved for you? If so please mark as SOLVED from Thread Tools top right.

---

### Post by jimmyrus on 2023-11-24
> **satimis said:**
> Hi,

I install Shotcut on Ubuntu 22.04 running as VM of VirtualBox

There are 2 options before hitting login
ubuntu
ubuntu on Xorg

I have tried both without result.

Each time I have start Shotcut on Terminal running;```

$ ./shotcut-linux-x86_64-230929.AppImag

```

Regardsthen create a shortcut using the full path. A launcher with just ./whatever may not work. How did you try to add
it to favorites? Kinda hard to help when you aren't telling us the whole story, like when you started this thread you more or less said
that it wasn't working and you got an error. Then you tell us it is working. Now it's a problem making a launcher or shortcut but you
aren't saying how you tried that either. 

Should we keep guessing?

---

### Post by satimis on 2023-11-24
Hi all,

Problem solved.  I have done it long time ago.  The solution only comes from my recollection.

Steps performed as follows;

1)
Download Shotcut icon to /home/satimis/Pictures/

2) on Terminal run;
$ sudo nano /home/satimis/.local/share/applications/shotcut.desktop

add following lines on the file```

[Desktop Entry]
Name=shotcut
Type=Application
Exec=/home/satimis/Downloads/shotcut-linux-x86_64-220130.AppImage
Icon=/home/satimis/Pictures/shotcut.jpg
Categories=Graphics;Viewer;

```

$ sudo chown satimis:satimis /home/satimis/.local/share/applications/shotcut.desktop

$ sudo chmod +x /home/satimis/.local/share/applications/shotcut.desktop

On /home/satimis/Downloads/
click shotcut-linux-x86_64-220130.AppImage

to start Shotcut

This time I can add Shotcut to "Favorite Bar".

But still there is a problem, shotcut.jpg icon not showing there, only a black icon

Regards

---

### Post by jimmyrus on 2023-11-26
> **satimis said:**
> Hi all,

Problem solved.  I have done it long time ago.  The solution only comes from my recollection.

Steps performed as follows;

1)
Download Shotcut icon to /home/satimis/Pictures/

2) on Terminal run;
$ sudo nano /home/satimis/.local/share/applications/shotcut.desktop

add following lines on the file```

[Desktop Entry]
Name=shotcut
Type=Application
Exec=/home/satimis/Downloads/shotcut-linux-x86_64-220130.AppImage
Icon=/home/satimis/Pictures/shotcut.jpg
Categories=Graphics;Viewer;

```

$ sudo chown satimis:satimis /home/satimis/.local/share/applications/shotcut.desktop

$ sudo chmod +x /home/satimis/.local/share/applications/shotcut.desktop

On /home/satimis/Downloads/
click shotcut-linux-x86_64-220130.AppImage

to start Shotcut

This time I can add Shotcut to "Favorite Bar".

But still there is a problem, shotcut.jpg icon not showing there, only a black icon

Regards
So you created a shortcut/[FONT=arial]desktop [/FONT]file, which is all you had to do from the start. and you need to put the icon
[FONT=arial]in [COLOR=#0C0D0E] $HOME/.local/share/icons folder so it can get read. Did you try to do anything to get the icon to show up or to look
[/COLOR]up the issue? Would seem after 17yrs you would have tried something.
[/FONT]

---

### Post by satimis on 2023-11-26
> **jimmyrus said:**
> So you created a shortcut/[FONT=arial]desktop [/FONT]file, which is all you had to do from the start. and you need to put the icon
[FONT=arial]in [COLOR=#0C0D0E] $HOME/.local/share/icons folder so it can get read. Did you try to do anything to get the icon to show up or to look
[/COLOR]up the issue? Would seem after 17yrs you would have tried something.
[/FONT]
There are no icons and themes folders here. But icons of other applications are displayed on the vertical manual bar.

I have done it before
created;
/home/satimis/.local/share/icons/ folder

cp shotcut.jpg on icons folder

edited;
/home/satimis/.local/share/applications/shotcut.desktop

changed following line;
Icon=/home/satimis/Pictures/shotcut.jpg

to
Icon=/home/satimis/.local/share/icons/shotcut.jpg

Rebooted PC

Still the same, Shotcut icon not displayed.

---

### Post by Dennis N on 2023-11-26
I put an AppImage icon in the same location: ~/.local/share/icons and that works for me. It's one of the searched locations for icons. So the problem could be your image file format. I would use an .svg file (preferable) or perhaps .png. A .jpg just may not work.

In my case,
The actual image file is [B]libreoffice-appimage.svg
[/B]
and 
**Icon=libreoffice-appimage**
was sufficient.

The icon was custom made with Inkscape.

---

### Post by satimis on 2023-11-26
> **Dennis N said:**
> I put an AppImage icon in the same location: ~/.local/share/icons and that works for me. It's one of the searched locations for icons. So the problem could be your image file format. I would use an .svg file (preferable) or perhaps .png. A .jpg just may not work.

In my case,
The actual image file is [B]libreoffice-appimage.svg
[/B]
and 
**Icon=libreoffice-appimage**
was sufficient.

The icon was custom made with Inkscape.
Hi @Dennis

Thanks for your advice.

I couldn't download shotcut.svg on Internet but png image.

Edit the line as.```

Icon=shotcut-appimage

```

reboot

Shotcut icon sitll not displayed but a strange icon.  Please see screenshot attached, 2nd icon from bottom.

I can't imagine so difficult to me this time.  I have done it several times in the past, unfortunately long time ago,

Regards

---

### Post by satimis on 2023-11-27
Hi @Dennis

Problem solved.

The icon to be used is not download on Internet.  It is the share icon of Shotcut application, on;
/home/satimis/.local/share/icons/shotcut_icon.png

The line should read as;
Icon=/home/satimis/.local/share/icons/shotcut_icon.png

Reboot.

Now Shotcut icon is shown up on Favorite.

Regards

---

### Post by Dennis N on 2023-11-27
I don't know if this is the case, but if you download an icon named **shotcut.png** then your **Icon=** line should be **Icon=shotcut** or if that doesn't work, try the full name **Icon=shotcut.png**, or use the full path to the image.

Not using the full path as I did only works if the icon is stored in one of the places searched for icons, like ~/.local/share/icons or /usr/share/icons.

---

### Post by Dennis N on 2023-11-27
Looks like we cross-posted. You did what I suggested, and I see that it worked. Problem solved.

---

### Post by satimis on 2023-11-27
> **Dennis N said:**
> I don't know if this is the case, but if you download an icon named **shotcut.png** then your **Icon=** line should be **Icon=shotcut** or if that doesn't work, try the full name **Icon=shotcut.png**, or use the full path to the image.

Not using the full path as I did only works if the icon is stored in one of the places searched for icons, like ~/.local/share/icons or /usr/share/icons.
Download a new Shotcut icon on;```

/home/satimis/Pictures/shotcut.png

```

only full path works```

Icon=/home/satimis/Pictures/shotcut.png

```

Please refers to screenshot attached

Regards

---

### Post by Dennis N on 2023-11-27
> only full path works
Because your image in in Pictures, not in one of the searched locations that I named.

---

