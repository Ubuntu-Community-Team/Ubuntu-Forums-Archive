---
title: "VLC opens and closes instantly"
date: 2009-07-24
forum: Multimedia Software
---

### Post by Souljah on 2009-07-24
Hello,

I'm having a problem with VLC now. When I try to open, it pops up and then immediately closes if I do it in the run command box. If I just click on the menu item or the shortcut I created, it doesn't even show that it opens. When trying to open it in the terminal this is the error I get:

```
ryan@AMDBE2350:~$ vlc
VLC media player 1.0.0 Goldeneye
WARNING: QApplication was not created in the main() thread.
Segmentation fault

```

How do I fix this? Thanks.

Ryan

---

### Post by kdetech on 2009-07-24
sudo aptitude purge vlc

then 
sudo aptitude install vlc

then if it still fails
sudo dpkg -recongigure vlc

---

### Post by jasonsjunk on 2009-07-24
Have you tried a reboot since this happened?  I am thinking that there is another instance of VLC running that crashed and might be causing this issue.  

You can also try to reset the VLC config using one of these two methods.

1) go to home folder -> .config and delete the vlc folder. (.config is a 'hidden' folder so you need to show hidden folders)

or

2)from a terminal type in vlc --reset-config

---

### Post by Souljah on 2009-07-24
> **jasonsjunk said:**
> Have you tried a reboot since this happened?  I am thinking that there is another instance of VLC running that crashed and might be causing this issue.  

You can also try to reset the VLC config using one of these two methods.

1) go to home folder -> .config and delete the vlc folder. (.config is a 'hidden' folder so you need to show hidden folders)

or

2)from a terminal type in vlc --reset-config
I know what the problem was. I reset the settings like you said Jason through the terminal and what was happening was then when the QT interface was checken in the main interfaces preferences in the dialog, then it would crashed upong execution. However, when it is not checked, it doesn't crash. I wonder why. Anyway, it's working now. Thanks a lot.

---

### Post by jasonsjunk on 2009-07-24
Glad you got it working enjoy your movie :)

---

### Post by Souljah on 2009-07-24
> **jasonsjunk said:**
> Glad you got it working enjoy your movie :)
How do you know it's a movie I wanna watch ;)

---

