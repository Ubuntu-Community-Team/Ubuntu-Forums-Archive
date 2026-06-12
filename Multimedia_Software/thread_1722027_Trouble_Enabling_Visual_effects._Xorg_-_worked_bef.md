---
title: "Trouble Enabling Visual effects. Xorg? - worked before!"
date: 2011-04-05
forum: Multimedia Software
---

### Post by Sammiye on 2011-04-05
Hi All, 
 i DID search this topic but couldnt find anything relating to my specific graphics controller.

yesterday i install Cairo Dock and Compiz with no problems, made a funky desktop and dock. However, this morning i had weird problems, black boxes all over the place and no window decorations. so uninstalled everything i did yesterday and got it back to basics. However, now i am trying to enable visual effects in System-Preferences-Appearance and i keep getting error message when i try to select Normal or Extra. It worked fine on extra yesterday!

Seems it cant find drivers. I have Intel Integrated Graphics controller GM45 See Lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

I think i have the correct XOrg drivers installed and all other video playback works great.

Any ideas?? Really would like a nice dock. 

cheers!

---

### Post by Sammiye on 2011-04-05
looking now, i dont seem to have anything in my xorg.conf file and attempts to reconfigure using this command hasn't worked.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

please help!

---

### Post by Sammiye on 2011-04-07
bump! anyone??

have googled and gooled with still no luck!

---

### Post by Sammiye on 2011-04-10
bump!

can no one help me out???

seems i need to reconfigure my xorg.conf but there's nothign in there and all attempts to try and reconfigure the file, nothing actually happens after i type in the commands.

---

### Post by Yellow Pasque on 2011-04-11
You shouldn't need any xorg.conf
Post your /var/log/Xorg.0.log

---

