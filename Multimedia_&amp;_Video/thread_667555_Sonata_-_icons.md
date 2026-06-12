---
title: "Sonata - icons"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by andrek on 2008-01-14
Hi, I've got a problem with icons that Sonata uses.
I'm talking about these ones : 

[[img]http://xs123.xs.to/xs123/08031/sonata358.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs123&d=08031&f=sonata358.jpg)
*(marked with a red pencil)*

What's the location of those? They look like default, so I'd like to change them.

---

### Post by jonathanmotes on 2008-01-14
Did you try changing your icon theme? (System -> Preferences -> Appearance Preferences) - or something similar - I'm not on Linux at the moment.

---

### Post by andrek on 2008-01-14
I'm not THAT newbie ;)
I've managed to find some of those by changing theme to SphereCrystal (which has got these particular icons) and looking for them in theme's folder. The second one (Library tab) is in scalable/devices and the third can be found in scalable/actions. 
The problem is, whether I replace them by other icon (keeping the same name), Sonata ignore the change and shows a 'big red X' icon.

oh and I didn't say that my current icon theme doesn't have those particular icons so Sonata brings them from another theme - which looks ugly. That's what I want to change them.
(I hope I expressed myself clearly, my english still sucks)

---

### Post by jonathanmotes on 2008-01-14
Oh. OK. Well I'm sort of a newbie myself, but maybe you need to change the file permissions on the images that aren't showing up by right clicking on them. Make sure they are readable by all users. If these image are not located in your home directory then you will need to open Nautilus using "sudo nautilus" in the terminal in order to be able to change the permissions (unless you know how to change permissions using the terminal).

NOTE: be careful running Nautilus as root - you can delete your whole hard drive if you choose to do so!

---

