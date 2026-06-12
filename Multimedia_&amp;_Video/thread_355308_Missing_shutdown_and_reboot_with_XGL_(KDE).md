---
title: "Missing shutdown and reboot with XGL (KDE)"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by Loonux on 2007-02-07
I have just managed to get Beryl working on kUbuntu 6.10 after 3 or 4 fresh installs.
Well worth the effort and very impressed with it.

One or two niggles though, including the fact that there is no power off or reboot buttons on the KDE logout screen. All i get is end current session and when i click this the screen goes black and the machine just hangs!

Also, is there any way to disable the beryl spash screen which sits there for too long IMO?

Can anyone help with this? Ive searched but the majority of solutions are gnome related whereas im using KDE.....


Thanks

---

### Post by tanguyr on 2007-02-07
> **Loonux said:**
> I have just managed to get Beryl working on kUbuntu 6.10 after 3 or 4 fresh installs.
Well worth the effort and very impressed with it.

One or two niggles though, including the fact that there is no power off or reboot buttons on the KDE logout screen. All i get is end current session and when i click this the screen goes black and the machine just hangs!

Also, is there any way to disable the beryl spash screen which sits there for too long IMO?

Can anyone help with this? Ive searched but the majority of solutions are gnome related whereas im using KDE.....


Thanks

Hello Loonux,

How are you starting Xgl? I start it with /etc/kde3/kdm/kdmrc, and i get the "normal"kdm logout options (i.e. end session, shut down, reboot, etc).

Secondly, i think you can disable the beryl splash altogether in beryl-settings, but i don't know about changing for how long it is displayed.

Regs,
/t

---

### Post by Loonux on 2007-02-13
Hi.
Im using a startxgl.sh script (created using the Beryl wiki tutorial).  heres the script;
```

Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer & sleep 4
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```


My XGL session entry option is created with the following:

```
head /usr/share/xsessions/xgl.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```


Is there something amiss?

---

### Post by tanguyr on 2007-02-13
Hi again Loonux,

In the meantime i have switched over to this method as well (xgl.desktop + startxgl script). I also only have "end current session" available on my KDE logout screen, but it doesn't crash - brings me back to the graphical login screen, and from there i can choose Turn Off Computer or Restart Computer...

What i was doing before was changing /etc/kde3/kdm/kdmrc like so:

Find the line that says:

```
ServerTimeout=15
```

and change it to 

```
ServerTimeout=30
```

and find the line that says:

```
ServerCmd=/usr/bin/X -br
```

and change it to

```
ServerCmd=/usr/bin/Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer
```

This will start xgl as your default X server, which is only really interesting if you are always going to use beryl. Note that you will still have to start beryl manager and beryl itself. For this i wrote a little script like this:

```

#!/bin/bash
if pgrep Xgl &>/dev/null; then
    /usr/bin/beryl-manager
    sleep 5
    /usr/bin/beryl-xgl --force-xgl
fi

```

This script should be saved in your kde autostart dir ~/.kde/Autostart and should be executable (chmod +x). 

With this setup i get the "normal"log out options including shutdown and reboot. Note that you must boot into the KDE session when you start, *not* the xgl one... Alt+T on the login screen or just click on the little icon of a menu next to the username/password fields (i guess you know this bit, but it bears repeating)

/t

---

### Post by Loonux on 2007-02-13
Sounds like a promising workaround!
Will give it a go later and post back with the result!

Cheers m8...

---

### Post by Loonux on 2007-02-14
well, gave that a go and KDm wouldn't even start! Just crashed back to a command line login. lol. restored the old version (glad i backed it up!) and im back to square one!

Thanks for the suggestion though. anything else i can try? 

There has to be a solution to this, surely?

---

### Post by 7creature on 2007-02-14
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Troubleshooting](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Troubleshooting)

What about this solution?

---

