---
title: "Turn off Flash Hardware Acceleration via terminal (Lubuntu 13.04)"
date: 2013-08-04
forum: Multimedia Software
---

### Post by Brock_Yohn on 2013-08-04
Is there a terminal command to do this? Or is there any other way besides right clicking on a video and disabling it via the settings menu? 

The reason I need this is because of my parents (older) computer (P4 3.00 Ghz w/ 2gigs RAM running Lubuntu 13.04). Anything Flash displays purple and improperly sized. A Google search revealed that the video card probably doesn't support hardware acceleration, and it is enabled by default with Flash. Right clicking on a Flash object and changing the settings will not work, because the menu displayed is unusable. Flash worked fine with this computer running Ubuntu 10.04. However, this version is unsupported, and my dad found a way to mess that install up.

---

### Post by Yellow Pasque on 2013-08-04
Try this:
```
echo "EnableLinuxHWVideoDecode=0" | sudo tee -a /etc/adobe/mms.cfg
```

---

### Post by Brock_Yohn on 2013-08-05
That command returned 'no such file or directory'

---

### Post by Yellow Pasque on 2013-08-05
Try creating the file:
```
sudo touch /etc/adobe/mms.cfg
echo "EnableLinuxHWVideoDecode=0" | sudo tee -a /etc/adobe/mms.cfg
```

---

### Post by Brock_Yohn on 2013-08-07
That didn't work either. 

The error message returned was:   [COLOR=#333333][FONT=Helvetica Neue]touch: cannot touch  /etc/adobe/mms.cfg.No such file or directory[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2013-08-07
Sigh.. my apologies. Just create the file and paste that line in there:
```
sudo leafpad /etc/adobe/mms.cfg
```

(I think Lubuntu uses leafpad,. If not, substitue your text editor.)

---

