---
title: "Make Xine Autoplay DVDs"
date: 2010-09-08
forum: Multimedia Software
---

### Post by imaca on 2010-09-08
Hi
I have just installed 10.04 on my mothers PC. I prefer to use Xine as the DVD player, sound works, playback is smooth, and, most importantly, because menus work, making it easier for her to use.
I have tried setting the DVD preference as xine with custom command but instead nautilus opens the dvd as folder.
It almost worked in 9.10 (a bunch of error messages pop up sometimes "the source can't be read you don't have rights etc....) and worked perfectly before that.
The error messages in 9.10 only pop up when DVD autoplays
I've just had a thought that this might be because she is not administrator?
(can't get to her PC at moment)
Any help appreciated

---

### Post by mc4man on 2010-09-08
> I have tried setting the DVD preference as xine with custom command 
I'm on maverick atm but nothings changed in this regard
If you use this as the custom command then xine-ui should work fine from autoplay and or a right click on the dvd icon
```
xine dvd:// 
```

Because you've already set at least one custom command for xine without giving it a unique name you'll end up with more than 1 choice of "xine"

So maybe before trying, first go to home folder -> .local -> share -> applications and delete any userapp-xine-XXXXXX.desktop you see.
(.local is a hidden folder - view -> show hidden files

Then create the new custom command in file management -> media

If you wish to give it a distinct name, for example Xine Dvd Player, then go back to ~/.local/share/applications and open the new userapp-xine-XXXXXX.desktop in a text editor and edit the name= line
(gedit ~/.local/share/applications/userapp-xine-[COLOR="Blue"]XXXXXX[/COLOR].desktop 
change the blue to match

(you can also do this just from  terminal commands, but this should suffice

---

### Post by imaca on 2010-09-09
Thanks for excellent help;]

---

