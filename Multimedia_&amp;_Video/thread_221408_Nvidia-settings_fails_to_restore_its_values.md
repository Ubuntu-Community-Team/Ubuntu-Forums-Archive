---
title: "Nvidia-settings fails to restore its values"
date: 2006-07-23
forum: Multimedia &amp; Video
---

### Post by metafile on 2006-07-23
I tried to install nvidia driver 8762 using the [3-method-howto](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper), but it never worked for me. So I just ran nvidia-installer and everything was perfect, now I`ve got my acceleration and  nvidia-settings.

But when I edit anything through nvidia-settings, or manually modify *~/.nvidia-settings-rc* file (image sharpening, for instance), after computer reboot defaults are restored and in *~/.xsession-errors* I can see the following lines ("c004" is the name of the machine):

```
ERROR: Cannot open display 'c004:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 18 of
       configuration file '/home/sp/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 19 of
       configuration file '/home/sp/.nvidia-settings-rc' (no Display
       connection).

...
and so on for each option of nvidia-settings
```

But I have no problems with display, i.e. it starts normally, except for old nvidia settings.
How can I solve this?

---

### Post by tseliot on 2006-07-31
Get to the following menus (if you use GNOME):
System -> Preferences -> Sessions -> Startup Programs

Then click on "Add"

And insert this command:
```
nvidia-settings --load-config-only
```

Then click on "Close".

---

