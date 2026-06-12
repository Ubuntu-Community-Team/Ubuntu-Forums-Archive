---
title: "installing new video card and system will not respond to aticonfig or amdconfig"
date: 2014-12-31
forum: Multimedia Software
---

### Post by afrohippie82 on 2014-12-31
I'm following this [post]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD")  installing a new r7 240 radeon Video card and I can't get ```
sudo aticonfig --initial 
``` to work this is what it does

```
sudo aticonfig --initial
sudo: aticonfig: command not found

```

Next I tried  ```
sudo amdconfig --initial
``` this was my results

```
sudo amdconfig --initial
sudo: amdconfig: command not found

```

I also went to the software center and change the selection to the proprietary ati drivers but after a restart and inputting  fglrxinfo into the terminal this is what i got 
```

 fglrxinfo
fglrxinfo: command not found
```

i alos posted a pic in the attachement filles for so info on....


Help is much appreciated

---

### Post by Yellow Pasque on 2014-12-31
Follow this: [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start)
(If you're using Ubuntu 14.10/Utopic, then it's exactly the same except you use --buildpkg Ubuntu/utopic).

---

### Post by afrohippie82 on 2015-01-01
This driver install is kicking my ACE!!!!!

---

### Post by Yellow Pasque on 2015-01-01
mmh hh...
Be more specific (or admit you're trolling).

---

### Post by afrohippie82 on 2015-01-01
well i've tried to follow the direction on the link that you 				 				 					 						 	[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594") put up but i keep getting errors when I try to install.. BTW whats trolling? attached are screen shots of the errors

if you look at the top right coner of the first screen shot you will see a red dot with a line through it this is what it says it would allow me to put it in the screen shot....an error occured, please run package manager from the right click menu or apt-get in a terminal to see what is wrong. the error message was:
'Error: BrokenCount>0'this usually means that your installed packages have unmet dependencies.

---

### Post by afrohippie82 on 2015-01-01
ok i finally have the catalyst up and running wow it couldnt have been that easy seem as if i was pressing the wrong config during the gui  install thanks for the help this case is closed wow

---

