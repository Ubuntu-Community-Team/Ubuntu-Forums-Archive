---
title: "VLC instantly on start?"
date: 2012-06-26
forum: Multimedia Software
---

### Post by v0 HaVoK 0v on 2012-06-26
For some reason when I open VLC, it opens for less than 1 second, and closes straight away, I don't know what happened, I think this was after messing around with some settings, but I can't remember what I did.
So is there a fix, or a way to uninstall it that it will remove everything VLC related, because I already tried to uninstall and re-install, but it still crashed. So I'm assuming there are some files that stayed after un-intallation?
I really want this media player back, so if anyone could help it would be really appreciated, thanks.

---

### Post by Cheesemill on 2012-06-26
Try running vlc from a terminal, what error messages do you get?

Also removing an application and then re-installing it doesn't touch the configuration files, to remove VLC's configuration files you need to delete the ~/.config/vlc directory.

---

### Post by hakermania on 2012-06-26
Hello there!

Open a terminal using Ctrl+Alt+T and type in
```

vlc

```
Post all the errors that vlc output inside the [code] tags.

Please always post any errors that the program outputs from inside a terminal!):P

---

### Post by v0 HaVoK 0v on 2012-06-26
> **hakermania said:**
> Hello there!

Open a terminal using Ctrl+Alt+T and type in
```

vlc

```
Post all the errors that vlc output inside the ```
 tags.

Please always post any errors that the program outputs from inside a terminal!):P

Ok, when I open through the terminal it actually works. but here is what there terminal says.

[CODE]matthew@ubuntu:~$ vlc
VLC media player 2.0.1 Twoflower (revision 2.0.1-0-gf432547)
Got bus address:  "unix:abstract=/tmp/dbus-IU3GTzOU20,guid=a2a9e93c6850393fc2deb03e00000034" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-IU3GTzOU20,guid=a2a9e93c6850393fc2deb03e00000034" 
Registered DEC:  true 
"sni-qt/6159" WARN  14:19:34.170 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
Registered event listener change listener:  true 
[0x13b2108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x13e1ad8] qt4 interface error: cannot start Qt4 multiple times
[0x7f14ec015838] qt4 generic error: cannot start Qt4 multiple times
[0x13e1ad8] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x13e1ad8] skins2 interface error: cannot instantiate qt4 dialogs provider
[0x13e1ad8] [cli] lua interface: Listening on host "*console".
VLC media player 2.0.1 Twoflower
Command Line Interface initialized. Type `help' for help.
```

When I open it normally without the terminal, it doesn't give me any errors, it just closes instantly.

EDIT : Deleted the VLC config directory, and now it opens fine. Thanks for the help guys.

---

### Post by Hari5g900 on 2012-06-26
Well, this shows nothing as wrong. But I really don't know.
When I did it, (it worked, well it usually works without command line) I got this:

VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to srand(1340717160)
Warning: call to rand()
[0x933267c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1340606701)
Warning: call to rand()
Blocked: call to setlocale(6, "")
(process:11209): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()

---

### Post by Ambimom on 2012-06-26
This is a stab in the dark, but it may work.

Are you sure that it isn't running somewhere but that the GUI is not visible?

Check the system monitor to see what's running and if it shows up on the list  of processes even if it has disappeared from your screen.  

If it is present, then send an audio/video file to open with VLC

Maybe the GUI will appear.  If it does,  there is a button in Tools/Advanced Settings              " Reset Preferences".

---

