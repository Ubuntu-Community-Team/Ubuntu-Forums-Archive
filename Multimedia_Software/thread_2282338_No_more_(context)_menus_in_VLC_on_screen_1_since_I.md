---
title: "No more (context) menus in VLC on screen 1 since I went dual-monitor"
date: 2015-06-13
forum: Multimedia Software
---

### Post by The Bright Side on 2015-06-13
Hey guys! The weirdest thing is happening to me, and I hope you can help. I recently bought myself a second screen and since then, whenever I open VLC on the main screen, neither menus nor the context menu work. When I click on menu items, they are highlighted, but the actual menu does not show. When I right-click on the image, nothing happens.

Here's where it gets really crazy: when I move VLC over to screen 2, the menus work!!

Well, they kinda do. The menus are scaled to the full height of the screen.

Screenshot showing behaviour on screen 1 below. Couldn't take a screenie while having the menu open on screen 2.

[IMG]https://dl.dropboxusercontent.com/u/7119083/screen1.jpg[/IMG]

Any ideas why this is happening and what I can do?

- Ubuntu GNOME 15.04
- 64-bit

---

### Post by mc4man on 2015-06-13
Don't use 15.04 much & Ubuntu Gnome ever. There are some menu issues in 15.04, how or if they translate to a gnome session no clue.

Try either of these, basically the same..
```
QT_X11_NO_NATIVE_MENUBAR=1 vlc
```
or 
```
export  QT_X11_NO_NATIVE_MENUBAR=1 && vlc
```

---

### Post by mc4man on 2015-06-13
To take a screen of a menu you need to use the screenshot app using a delay, set long enough to open the menu. Can be just of the window unless the menu is outside of it, then use whole screen
ex. in screen

---

### Post by The Bright Side on 2015-06-14
Thanks mc4man! Yup, I know I could install a screenie app and fiddle around with it, but I'm kind of too lazy for that. :-) Here's a screenshot of the menus from the second screen:

[IMG]https://dl.dropboxusercontent.com/u/7119083/screen2.jpg[/IMG]

Thanks for your suggestion to run VLC with the modified command line - no dice. I also just learned that the same happens in XNConvert: you click on a menu and it doesn't show unless you move it to the second screen. Really weird behaviour. Other programs (e.g. menus in Firefox) are fine.

---

