---
title: "Re: Howto: Using Compton for tear-free compositing on XFCE or LXDE"
date: 2014-03-29
forum: Multimedia Software
---

### Post by thiago189 on 2014-03-29
Anyone can help me? I have tried to use the compton, but in my PC it simply breaking my XFCE theme. And I don't know why.


For example: I use Greybird theme and it puts a transparent background to the icons of the Desktop. But if I use Compton, the icons lose its transparency.

---

### Post by oldos2er on 2014-03-29
Moved to Multimedia & Video from [Tutorials]("http://ubuntuforums.org/showthread.php?t=2144468").

It might help to mention which video card you're using.

---

### Post by ajgreeny on 2014-03-29
You can get the transparency on icon labels by making a hidden **.gtkrc-2.0** file in your home with contents as below, some of which relates to other changes such as label font colour, and removing a delay in menu display, though that may no longer be needed, as I think it was for the gnome-menu speed-up:-
```
# This file should be placed in your xubuntu home folder
# and name ".gtkrc-2.0"
#
gtk-menu-popup-delay=0
gtk-menu-popdown-delay = 0
gtk-menu-bar-popup-delay = 0
gtk-enable-animations = 0
gtk-timeout-expand = 10
#---------------------------------------------------------------
# Section "icon background colors"
#---------------------------------------------------------------
# The following two lines *should* be left uncommented
# if we want the XFCE desktop icon backgrounds to use
# alpha blending (e.g. invisible or some % thereof)
#
style "xfdesktop-icon-view" {
XfdesktopIconView::label-alpha = 0
XfdesktopIconView::selected-label-alpha = 0
XfdesktopIconView::active-label-alpha = 0
#
#---------------------------------------------------------------
# Section "icon font colors"
#---------------------------------------------------------------
#
# The next three lines deal with the color of the desktop icon's
# text. You can comment them out if you want you use gtk theme
# colors. Below yields white un-selected normal, green selected,
# and blue when going to another window
#
# I chose three different colors so that you can see the level
# of customization we can do.
#
fg[NORMAL] = "#ffffff"        #this is white
fg[SELECTED] = "#00ff00"      # this is green
fg[ACTIVE] = "#ff0000"        # this is red
#
## my blue fonts to use with nuvola theme & royal blue WM
# environment. a soft shark underbelly blue color if you will.
#fg[NORMAL] = "#528AC6"
#fg[SELECTED] = "#528AC6"
#fg[ACTIVE] = "#528AC6"
#
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
# 
```

---

