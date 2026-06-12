---
title: "Cannot associate .xcf fikles with Gimp on 20.04"
date: 2021-04-15
forum: Multimedia Software
---

### Post by cscj01 on 2021-04-15
I am running Ubuntu 20.04.2 x64 and Gimp 2.10.24.

I can't seem to figure out a way to associate .xcf files with Gimp.  This actually started in 18.04.  If I look at Properties for my .xcf files, I only have two tabs, Basic and Permissions.  If I use Nautilus, right click on the file,  and choose Open with Other Application, Gimp does not appear in the list.  If I say Find New Application, Gimp is displayed, but is listed as installed.

So when I double-click on an .xcf file, I get a message saying 'no application installed for "Gimp image" files.'  I have to open Gimp and open the file from within Gimp.  I have two Desktop files for Gimp.  One is in /usr/share/applications and the other is in ~/.local/share/applications.  Both of these list image/x-xcf as a mime type.  The files are identical.

I have installed Gimp from [http://ppa.launchpad.net/ubuntuhandbook1/gimp/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/gimp/ubuntu)

Does anyone have a suggestion as to how I can rectify this situation?

---

### Post by Dennis N on 2021-04-16
Things to try that may help:

This alone may fix it:

Refresh the mimeinfo.cache of mime types and applications:
```
sudo update-desktop-database
```

Other commands as examples:

Find the default application for a mime type:
```
xdg-mime query default image/x-xcf
```
Set default application (use name of it's desktop file) for a mime type:
```
xdg-mime default gimp.desktop image/x-xcf
```

---

### Post by ajgreeny on 2021-04-16
What do you see if you open an xcf file with gimp using terminal command```
gimp-2.10 /path/to/file.xcf
```
That may give you some clues.

---

### Post by cscj01 on 2021-04-16
> **Dennis N said:**
> Things to try that may help:

This alone may fix it:

Refresh the mimeinfo.cache of mime types and applications:
```
sudo update-desktop-database
```

Other commands as examples:

Find the default application for a mime type:
```
xdg-mime query default image/x-xcf
```
Set default application (use name of it's desktop file) for a mime type:
```
xdg-mime default gimp.desktop image/x-xcf
```

I tried your suggestions in order.  Here are the responsees:```
sudo update-desktop-database
``` No response.  I then tried to open an .xcf file by double-clicking with same results as before.```
xdg-mime query default image/x-xcf
``` Response was > gimp.desktopI then tried to open an .xcf file by double-clicking with same results as before.

Finally```
xdg-mime default gimp.desktop image/x-xcf
```I then tried to open an.xcf by double-clicking.  Success!

What puzzles me is that Ubuntu knew what application to use for the mime type image/x-xcf in option 2 but still would not open the application.

In any case, thanks for resolving this irritating issue.

---

### Post by cscj01 on 2021-04-16
> **ajgreeny said:**
> What do you see if you open an xcf file with gimp using terminal command```
gimp-2.10 /path/to/file.xcf
```
That may give you some clues.

Thanks for your reply.  As I indicated in my post before this one, it works correctly now.  However, I did find some other issue of unsupported add-ins by trying your suggestion.  I am researching those now.  So thank you as well for offing some helpful advice.

---

### Post by ajgreeny on 2021-04-16
Are some of those add-ins from an earlier version of gimp? Perhaps that is causing you some trouble.
What add-ins are causing this other issue?

Give as much detail as you can and you may get more help.

---

