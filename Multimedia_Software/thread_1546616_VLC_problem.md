---
title: "VLC problem"
date: 2010-08-05
forum: Multimedia Software
---

### Post by selittl on 2010-08-05
I installed a skin that did not work or is interfering with VLC somehow.  It will only open minimized now and I cannot maximize it to get to the options to revert back to the default skin.  Can someone tell me if there is a way to launch VLC in the terminal with a default skin switch?

Here is the output when I try to start it:

VLC media player 1.1.2 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7fac5dcdcb20, 0x7fac5dcdca80)
Warning: call to signal(13, 0x1)
Warning: call to srand(1280876146)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2813): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
[0x178a640] skins2 interface: skin: QuickTime UMX  author: UniverseMatrix




Thanks

---

### Post by ajgreeny on 2010-08-05
Try renaming the file **~/.config/vlc/vlcrc** as a backup, as I think this is where the user interface skin info is stored.
You could also remove that skin from the **~/.local/share/vlc/skins2** folder.

---

### Post by selittl on 2010-08-05
renamed the file as backup but the skins2 file does not exist in the vlc directory.  Still no mojo.

---

### Post by howefield on 2010-08-05
Try

```
On Linux/Unix: ~/.local/share/vlc/skins2
```


[http://www.videolan.org/vlc/skins.php](http://www.videolan.org/vlc/skins.php)

---

### Post by selittl on 2010-08-05
update:  Did find the skins2 dir.  Only a default skin in there.  Still can't figure out what's going on.  I have uninstalled and reinstalled VLC twice and it still does not launch or open only launches minimized.

Is there a command to do a complete removal that I am missing?  How can I completely get it off of the system so I can try another re-install?

---

### Post by ron999 on 2010-08-05
I think it's moved to usr/share/vlc/skins2

---

### Post by howefield on 2010-08-05
What do you have in ~/.config/vlc

2 files ? Delete them both, (or rename them)

---

### Post by ron999 on 2010-08-05
Un-install VLC again.
Then use Places > Search for files > File system to search for *vlc*.
Delete anything you find, then re-install.

---

### Post by ajgreeny on 2010-08-05
> **ron999 said:**
> I think it's moved to usr/share/vlc/skins2
Not on my system, though I don't use any of the skins I have downloaded, but stick with the classic look.    I think perhaps only the default skin is in /usr/share/vlc/skins2.  The extra skins do work from the ~/.local/share/vlc/skin2 folder, however;  I've just tried, but perhaps you can put them anywhere you want, as long as you set the folder location in **vlc ->Tools ->preferences.**

You should be able to find your all the skins folders for vlc and other apps with the find icon in nautilus, or **locate** in terminal.

Lots more info here
[http://wiki.videolan.org/Skins](http://wiki.videolan.org/Skins)
including the command ```
vlc -I qt
``` to start vlc with the default skin.

---

### Post by mc4man on 2010-08-05
```
vlc -I qt4
```

Then adjust in tools -> prefs. -> all -> main interface -> interface module (default or qt4 should do

---

### Post by selittl on 2010-08-05
Got it working.  Had to do a complete remove (sudo apt-get autoremove) through the term and re-installed and it now works.

Thanks for all the tips.

---

