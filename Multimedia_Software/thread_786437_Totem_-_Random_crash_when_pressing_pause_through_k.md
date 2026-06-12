---
title: "Totem - Random crash when pressing pause through keyboard"
date: 2008-05-08
forum: Multimedia Software
---

### Post by hermes0710 on 2008-05-08
Hi all,
  I use totem-xine on 8.04 and i randomly face crashes (the application doesn't respond anymore) when i use the keyboard to pause - play a movie.

Is there anybody else facing this? (My keyboard is wireless but i don't think that this is the reason)

Thanx

---

### Post by warbread on 2008-05-08
Try running totem through terminal.  I've found it's easiest to get debug information if you shunt error messages into a file, so you can go back and review in case of a system crash.

```
:-$ totem-xine 2> totemerror
```

[I have faced similar issues,]("http://ubuntuforums.org/showthread.php?t=785395") but with Kaffeine.  It usees the xine engine, so maybe there's a bug in 8.04 that will make using xine difficult.

---

### Post by hermes0710 on 2008-05-08
Ok, i'll try that and let you know. Generally, do you know in which way i can assign the multimedia keys of the keyboard as shortcuts to kde applications while using gnome?

---

### Post by warbread on 2008-05-08
Do you mean pressing a key (or key combo) and having a KDE app open, or do you mean using keys to control a KDE app, e.g. using a 'play' button to start Amarok?  The first is easy, but I use gconf-editor.  Some prefer the GUI in System -> Preferences -> Keyboard shortcuts.  I don't think you can do custom shortcuts there, though.

Alt+F2 and type in gconf-editor.  From there, go to apps > metacity > keybinding_commands.  You will see a list to your right with items like "command_1".  To the right of those, under the "Value" header, double click and type in the command for the program you want to run.  Then, on the left, click on global_keybindings.  Here, in the area on the right, you'll see more options.  Scroll down until you see run_command_N, where N is the command you typed a value into last screen.  Double click on 'disabled' and type in the command you want to use.  For example:

```
 <alt>e 
```

is ALT+e.  

```
 <super>1 
```

is Windows key + 1.  

There may be an "easier" way to do it, but I don't know it.  This way, I have consistent success and lots of flexibility.  Let me know if I can clarify anything for you.

---

### Post by hermes0710 on 2008-05-08
Thanx for the reply. Actually I want to control Amarok and Kaffeine in gnome. I have a multimedia keyboard and i can assign the media keys to playback functions but they respond only to gnome apps (totem,rythmbox etc). Pressing these keys when amarok or kaffeine are running, nothing happens.

When i choose from amarok/kaffeine menu to configure shortcuts the media buttons are not recognised...

---

### Post by warbread on 2008-05-08
[This might be of some help for Amarok and Kaffeine.]("http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910")

According to [this thread]("http://ubuntuforums.org/showthread.php?t=402907") , it works for Hardy, and it was written by a forum member.

---

### Post by hermes0710 on 2008-05-08
Thank you, i will try these when i get home!

---

