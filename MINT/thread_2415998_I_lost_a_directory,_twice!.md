---
title: "I lost a directory, twice!"
date: 2019-04-03
forum: MINT
---

### Post by drpeppercan on 2019-04-03
I found this Gimp plugin I need to use ([Export Layers]("https://github.com/khalim19/gimp-plugin-export-layers")). I need to move its files to the Plugins directory of Gimp. But while I was trying I lost it somehow. Below shows the 2nd time.


```
/var/lib/flatpak$ sudo mv export_layers/ /app/
drpeppercan@Nitro:/var/lib/flatpak$ cd app
drpeppercan@Nitro:/var/lib/flatpak/app$ ls
org.gimp.GIMP
drpeppercan@Nitro:/var/lib/flatpak/app$ ls -a
.  ..  org.gimp.GIMP

```


Can anyone enlighten me please?


Thanks

---

### Post by drpeppercan on 2019-04-03
Solved!

Karlchen from Linux Mint forums said: 
"[COLOR=#333333][FONT=&amp]What you really wanted to do was this:[/FONT][/COLOR]
```
sudo mv export_layers/ app/
```"

[Post source]("https://forums.linuxmint.com/viewtopic.php?f=90&t=291449&p=1617022#p1617017")

---

### Post by Rubi1200 on 2019-04-05
Please mark the thread Solved so others who can find the solution if they encounter the same problem.

Thanks.

---

