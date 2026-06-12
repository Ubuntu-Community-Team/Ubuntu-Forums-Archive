---
title: "Where to find the Gimp Plugins directory?"
date: 2019-05-07
forum: MINT
---

### Post by drpeppercan on 2019-05-07
Linux Mint 19.01 / Cinnamon

Gimp was installed with Flatpak.
If I use the Cinnamon Menu Editor I can see its location (/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @@u %U @@) but when I go to /usr/bin/ I don't see any "flatpak" directories.
I need to install this [plugin]("https://gimper.net/resources/extract-text-from-text-layers.231/").

Thanks guys,

DPC

---

### Post by jeremy31 on 2019-05-07
Moved to Mint

---

### Post by SeijiSensei on 2019-05-07
On my Kubuntu 19.04 system the GIMP plug-ins are stored in separate directories under

/usr/lib/gimp/2.0/plug-ins/

---

### Post by Xian on 2019-05-07
If you open Gimp and go to:

[COLOR=#ff0000]Edit -> Preferences -> Folders -> Plug-ins[/COLOR]

The window should reveal where the plug-ins are stored.

It will probably show as similar to: ~/.var/app/org.gimp.GIMP/config/GIMP/

---

### Post by TheFu on 2019-05-08
[https://askubuntu.com/questions/1044101/how-to-use-plugins-with-gimp-2-10-flatpak](https://askubuntu.com/questions/1044101/how-to-use-plugins-with-gimp-2-10-flatpak) has an answer which seems like the answers above, just with more details.

---

### Post by monkeybrain20122 on 2019-05-09
If you install with flatpak it won't be in /usr/lib or /usr/local/lib,  probably in something like $HOME/.config/GIMP/2.10/plug-ins

---

