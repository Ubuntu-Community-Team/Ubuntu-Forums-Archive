---
title: "Help: image view/file manager with ability to list image resolution below thumbs"
date: 2016-09-04
forum: Multimedia Software
---

### Post by vikler on 2016-09-04
hello everyone,
I need your help. Can you please recommend any software that has an option of listing image resolution (width X height) below thumbnails (when all of them are listed in a folder containing images).
I used to have old ubuntu version (32bit) with Gnome-classic desktop. There I could easily do so with gThumb. However not so long ago I installed Ubuntu 16.04 64bit, and the version of gThumb there doesn't seem to have such an option. I don't even see the top menu with properties (change thumbnails size, list other exif tags below thumbs, etc). 

To make it more clear this is what I need (on screencap: old version of gthumb):
[[img]http://storage2.static.itmages.ru/i/16/0904/s_1473005439_6678221_0496e345c4.jpg[/img]](http://itmages.ru/image/view/4833015/0496e345)


The thing is: I have to do tons of screencaps daily for clients (many folders have hundreds of images), and the requirement is to have resolution listed. It's already a pain that there is no "screencap with scrolling" software in Ubuntu (yeah, there are google chrome plugins, but I'm speaking about screencapping local folder), but I got used to it. Now w/o image resolution below thumbnails....I don't even know what to do. 

Hope someone can help me

---

### Post by TheFu on 2016-09-04
ImageMagick doesn't have a tool for this?  Something like **montage** and you insert the label needed?
[https://www.imagemagick.org/Usage/montage/](https://www.imagemagick.org/Usage/montage/) has examples. Bet the resolution can be put as the label fairly easily.

A little script would make this 1 command a day you need to run to create the sheets.

---

### Post by mc4man on 2016-09-04
> **vikler said:**
>  I installed Ubuntu 16.04 64bit, and the version of gThumb there doesn't seem to have such an option. I don't even see the top menu with properties (change thumbnails size, list other exif tags below thumbs, etc). 


gthumb in 16.04 still has all those options in the Preferences menu, screenshot
In ubuntu session the menu is accessed from upper left of unity panel by hovering cursor over Gthumb Image Viewer &  clicking on the gthumb that appears.
or
In the gthumb window deco click on the little icon to the left of the close (X) button, scr 2

---

### Post by vikler on 2016-09-05
thanks @[COLOR=#000000]TheFu will check it out

@[/COLOR][COLOR=#000000]mc4man
the thing is...new version I have doesn't have this preference menu :( How do I enable it?
[/COLOR][[IMG]http://4.t.imgbox.com/WdTgEyWu.jpg[/IMG]]("http://imgbox.com/WdTgEyWu")

---

### Post by mc4man on 2016-09-05
> **vikler said:**
> thanks @[COLOR=#000000]TheFu will check it out

@[/COLOR][COLOR=#000000]mc4man
the thing is...new version I have doesn't have this preference menu :( How do I enable it?
[/COLOR][[IMG]http://4.t.imgbox.com/WdTgEyWu.jpg[/IMG]]("http://imgbox.com/WdTgEyWu")
I'm using the one provided in 16.04 in an ubuntu session. Are you using a gnome session (gnome-shell or gnome-flashback), or some other session like mate?

What does this return?
```
gsettings get org.gnome.gthumb.browser thumbnail-caption
```

---

