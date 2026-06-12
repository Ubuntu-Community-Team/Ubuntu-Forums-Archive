---
title: "Nvidia and compaq tc1000 tabletpc"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by javabien on 2006-06-21
Hello,

I install Ubuntu on my tabletpc. All works nice befor I install Nvidia driver.

Now when I star my computer I see a black screen. If I press ctrl - alt - back space the x server start normaly, I see the nvidia logo .. and gnome desktop.

But every time I reboot (or start) my tabletpc I see a blackscreen.


Anybody can help me?


Javabien

---

### Post by 23meg on 2006-06-21
Try hitting Ctrl+Alt+F7 instead of Ctrl+Alt+Backspace when you get the black screen and see if it helps as well.

---

### Post by javabien on 2006-06-21
Ok If I press ctrl - alt - F8 then ctrl - alt - F7 I see my desktop but without the cursor :confused: 


If I close my session I resee the black screen but If I repress ctrl - alt - F8 then ctrl - alt - F7 I see my destop  ...

It's very strang because I install Opensuse and fedora and this pc without any problems ... 

Have you any idea?

Thanks

Javabien

---

### Post by tseliot on 2006-06-21
[QUOTE=javabien]Hello,

I install Ubuntu on my tabletpc. All works nice befor I install Nvidia driver.

Now when I star my computer I see a black screen. If I press ctrl - alt - back space the x server start normaly, I see the nvidia logo .. and gnome desktop.

But every time I reboot (or start) my tabletpc I see a blackscreen.


Anybody can help me?


Javabien[/QUOTE]
Try point 13 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

---

### Post by javabien on 2006-06-21
I have alreay test this solution and don't work.

---

### Post by tseliot on 2006-06-21
Try with 
```
sudo dpkg-reconfigure xserver-xorg
```

and select the Nvidia driver

---

### Post by javabien on 2006-06-21
I sorry but don't work. If I want to have the graphic mode, I need to presss ctrl - alt -F6 then -F7. 

Never mind. I'll install a debian or an opensuse.


Tks for your anwser.


javabien


Now I very *ç"ç+"ç*% because I install OpenSUSE and I have the same problem .... I'll reinstall Dapper. If you have another idea ....

---

### Post by 23meg on 2006-06-24
I'm not sure if this is going to help but give it a try: boot with the "irqpoll" kernel option. See [here]("http://ubuntuforums.org/showpost.php?p=1130812&postcount=2") for details.

---

### Post by nodows on 2006-10-15
I'm havin this same issue right now!  So I assure you, its not you.  

Havne't figured a way around it yet but I'm workin on it.  I havn'et figure out how to get the pen to work correctly as a serial device either... and my wifi sees networks it just can't join them... so I'm a long ways away from victory still.  If you figure anything out about anything lemme know!

Tyler

---

### Post by tseliot on 2006-10-15
> **nodows said:**
> I'm havin this same issue right now!  So I assure you, its not you.  

Havne't figured a way around it yet but I'm workin on it.  I havn'et figure out how to get the pen to work correctly as a serial device either... and my wifi sees networks it just can't join them... so I'm a long ways away from victory still.  If you figure anything out about anything lemme know!

Tyler

Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by jgordon510 on 2007-01-10
Found the solution:
[http://www.nvnews.net/vbulletin/showpost.php?p=965454&postcount=3](http://www.nvnews.net/vbulletin/showpost.php?p=965454&postcount=3)

1. Write this line in (newly created) /etc/modprobe.d/nvidia file (this line has to be on a single line):
```

options nvidia NVreg_DeviceFileUID=0 NVreg_DeviceFileGID=33 NVreg_DeviceFileMode=0660 NVreg_SoftEDIDs=0 NVreg_Mobile=1
```


2. Then add this option to the device section of your /etc/X11/xorg.conf under your nvidia card:

```
Option "ConnectedMonitor" "DFP"
```

---

