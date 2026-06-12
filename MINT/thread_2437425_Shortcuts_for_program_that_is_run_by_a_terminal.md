---
title: "Shortcuts for program that is run by a terminal"
date: 2020-02-23
forum: MINT
---

### Post by herculpirate on 2020-02-23
I have installed a program called Anaconda which is a Data Science program.
To run it I am to open a terminal and type "anaconda-navigator"

and the program runs well.

But I would like to have a shortcut on my desktop or my taskbar where I can click and get this running.
I am currently running Linux Mint 19.3.

Please help.

Thanks

HP

---

### Post by CatKiller on 2020-02-23
The launchers on the desktop, panels, menus, docks, or whatever, are .desktop files, which are just text files with a [particular structure](https://www.freedesktop.org/wiki/Specifications/desktop-entry-spec/). Using **Terminal=true** should open your normal terminal application and run the command you've specified in the Exec= line.

---

### Post by wildmanne39 on 2020-02-23
*Thread moved to **MINT a more appropriate sub-forum**.*

---

### Post by herculpirate on 2020-02-24
Thank you for the reply

I have the following in the .desktop file
The error i get is.. there is an error launching the application.


```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Name=Anaconda
Comment=Anaconda Navigator
Exec=anaconda-navigator
Icon=/home/hpws/Pictures/anaconda.jpg
Terminal=true
Type=Application
Categories=Utility;Application;


```

---

### Post by CatKiller on 2020-02-24
If *anaconda-navigator* isn't in your $PATH, you may have to specify the full path to launch it. You may also need to specify *Path=* to set the working directory to whatever your application uses.

I don't *think* you need the "#!/usr/bin/env xdg-open" at the start, either.

---

### Post by herculpirate on 2020-02-24
All I need is that a Terminal with a command

```
anaconda-navigator
```

is executed.
What do you think I should have in that file....

---

### Post by herculpirate on 2020-02-24
I got it.

Here it is.
Thanks


```

[Desktop Entry]
Version=1.9.7
Name=Anaconda
Comment=Anaconda Navigator
Exec=/home/hpws/anaconda3/bin/anaconda-navigator
Icon=/home/hpws/anaconda3/bin/anaconda.jpg
Terminal=true
Type=Application
Categories=Utility;Application;

```

---

