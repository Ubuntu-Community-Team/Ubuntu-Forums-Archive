---
title: "AVCONV or WINFF .winff/cfg.xml problem"
date: 2014-03-14
forum: Multimedia Software
---

### Post by motocollage on 2014-03-14
So, I was trying to install winff presets to convert .avi files to .mp4 and I think I broke winff. I understand that avconv is used instead, but the graphical frontend for winff is easy to use.

I began following the instructions listed here [https://code.google.com/p/winff/wiki/InstallPresetsxml](https://code.google.com/p/winff/wiki/InstallPresetsxml) or here [https://code.google.com/p/winff/wiki/UbuntuInstallation](https://code.google.com/p/winff/wiki/UbuntuInstallation), but maybe I made the mistake of not copying the extracted file ([https://code.google.com/p/winff/downloads/detail?name=presets-libavcodec53-v4.xml.gz&can=2&q=](https://code.google.com/p/winff/downloads/detail?name=presets-libavcodec53-v4.xml.gz&can=2&q=)) to the right place. once I tried to launch winff in terminal via ```
winff path/to/file
``` (and when I try to launch the graphical frontend later) I receive the following error: ```
/home/lile/.winff/cfg.xml(5,1) Error: Text after end of document element found


```

I've either messed up the .cfg.xml or presets.xml files inside the .winff directory, but I'm not sure how I did it. I tried to reinstall winff from synaptic and software center with no luck.

Any suggestions? Did I break it? Did I break anything else?

I'm using ubuntu 12.04 LTS on a Dell Optiplex 745. May be related to the posts here [http://ubuntuforums.org/showthread.php?t=2013680&highlight=winff](http://ubuntuforums.org/showthread.php?t=2013680&highlight=winff) and here [http://ubuntuforums.org/showthread.php?t=2007634&highlight=winff](http://ubuntuforums.org/showthread.php?t=2007634&highlight=winff)

---

### Post by motocollage on 2014-03-14
complete error:

```
me@dellubuntu:~$ winff
TApplication.HandleException /home/lile/.winff/cfg.xml(5,1) Error: Text after end of document element found
  Stack trace:
  $081FE821
  $081FEE43
  $08201BA9
  $08201CEB
  $081FA11B
  $081FA650
  $081F9221
  $0806F9EC
  $0806BD6F
  $0805D4C3
  $0805BB57
  $08061DBE
  $08069308
  $08058C27
[CRITICAL] os_bar_hide: assertion `OS_IS_BAR (bar)' failed


(winff:4533): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
[CRITICAL] os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed
me@dellubuntu:~$ 



```

---

