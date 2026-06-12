---
title: "Getting Media Keys to work with Gmusicbrowser?"
date: 2012-01-11
forum: Multimedia Software
---

### Post by shizz on 2012-01-11
Hey guys, I'm just wondering if anyone can help me get my media keys to work? They worked with Banshee but I found it to be a bit too much like windows media player and gmusicbrowser has a feature I've been looking for for a while. 

Say if you are shuffling all of your songs and then you decide there's one you want to listen to so you search for it? Well all media players I have come across will just play that song and then stop playing music, where gmusicbrowser continues to shuffle through your collection. I really like this feature. So if anyone knows of another music player that does this please suggest it and I'll see if it works with my media keys. 

But if not could someone help me with this. It tells me to do this in their FAQ > How do I control gmusicbrowser with global shortcuts or multimedia keys ?
You have to configure your window manager to execute the command gmusicbrowser -remotecmd PlayPause (in version 1.1.x it is now gmusicbrowser -cmd PlayPause) when the key combination you want is pressed. Replace "PlayPause" by the command you want, to see the list of available commands, run gmusicbrowser -listcmd.
If you have the DBus perl bindings, you can also control gmusicbrowser though the DBus interface.
If you use Gnome >=2.18, you can use the included gnome multimedia keys plugin (needs DBus perl bindings), that will automatically make the Play/Pause, Stop, Previous and Next multimedia keys work.
This article explains how configure keybindings in metacity (gnome's default window manger).

Im running 11.10 Ubuntu and My laptop is Asus N53sv if it matters. 

Thanks in advance.

---

### Post by shizz on 2012-01-12
Bump?

---

### Post by erisdiscordia on 2012-02-26
Hi!

I hope that this very late reply somehow reaches you. Maybe at least it will help someone else. 

I have only done this once, and I actually succeeded only thanks to the advice you cite below! But I understand it can be confusing.

To add my keyboard's mail key as the gmusicbrowser play/pause key, I did this:

1. Click the Settings/Power button, to reach the Settings/Power menu.
2. Click the System Settings command, to reach the System Settings window.
3. Click the Keyboard icon, to reach the Keyboard window
4. Click the Shortcuts tab to reach, uh, the Shortcuts tab.
5. Click Custom Shortcuts to work with custom shortcuts.
6. Click the "+" button to add a custom shortcut.
7. Name your custom command whatever you want.
8. Set the command to "gmusicbrowser -cmd PlayPause" (copy and paste it) and click Apply. For a different command, check the documentation as they recommended.
9. Click the line for your new custom shortcut ON THE RIGHT SIDE WHERE IT CURRENTLY SAYS "DISABLED".
10. Press the key you want.
11. Yay!

Note that things are designed a bit conversatively, so you cannot have e.g. your gmusicbrowser play/pause and your general play/pause on the same button. Oh well.

---

