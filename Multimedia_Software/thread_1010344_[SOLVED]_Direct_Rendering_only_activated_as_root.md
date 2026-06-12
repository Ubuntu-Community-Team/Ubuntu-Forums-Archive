---
title: "[SOLVED] Direct Rendering only activated as root"
date: 2008-12-13
forum: Multimedia Software
---

### Post by jum on 2008-12-13
Hello,

direct rendering runs well when I start glxinfo as root
```
jum@jum-laptop-lx:~$ sudo glxinfo | grep direct
direct rendering: Yes

```

But as normal user, direct rendering is deactivated:
```
jum@jum-laptop-lx:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

```

I am in the video group, and here my xorg.conf: [http://pastebin.ch/733](http://pastebin.ch/733)

Can you please help me?

---

### Post by drelyn86 on 2008-12-13
This might seem odd... but are you launching the terminal by using a keyboard shortcut? If so, try launching the terminal from the menu, and try again.

---

### Post by jum on 2008-12-13
wow, now it is ativated, even without sudo.

but why is this as it is? *confused*

---

### Post by drelyn86 on 2008-12-14
Source: [https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/137388]("https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/137388")

> 

In fact, that's not a real bug : compiz indeed sets LIBGL_ALWAYS_INDIRECT for its own process and for his child processes only. compiz needs that to work properly.
It means that if you start a terminal from the Gnome/KDE menu, you'll get "direct rendering: Yes". On the other hand, if you start gnome-terminal for instance via compiz using a key binding for example, you will get "direct rendering: No (LIBGL_ALWAYS_INDIRECT set)".

The problem is in fact a bit more complex : when I start gnome-terminal from the gnome menu, I get "direct rendering: No (LIBGL_ALWAYS_INDIRECT set)" : as I activated transparency for the background of gnome-terminal, it starts as child process of compiz. So, all is all right : xterm, which is very spartan and doesn't support transparency, prints "direct rendering: Yes" when started from the gnome menu.


So I guess one workaround would be setting your terminal background to transparent(?)

This is one of the reasons why I quit using keyboard shortcuts to launch the terminal... but I know you don't want to go looking for it in your Applications menu every time you need it. I use the following "easy" ways of launching the terminal... 

1. Add the gnome-terminal to your panel. Right click on your panel, click "Add to Panel" now "Application Launcher" and Forward, Terminal is in your Accessories menu. You could also achieve the same thing by dragging it from your menu onto the panel. Either way, it's just a shortcut at the top (or bottom) of your screen. 

2. Install the nautilus-open-terminal package:

```
sudo aptitude install nautilus-open-terminal
killall nautilus && nautilus
```

This adds an option when you right-click on or inside any folder in your file browser to open that folder in the terminal. This proves especially helpful when you don't like typing out the whole pathname to the folder you need to be in.

---

### Post by jum on 2008-12-15
drelyn86, thank you for your help and your tips!
:guitar:

---

