---
title: "Yet more NVIDIA problems"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by nunomp on 2006-06-19
Hello.

I am having problems with my NVIDIA install. I have read most of the posts around but nothing seems to works.

Hardware: toshiba satellite S2450-401, GeForce4 420 Go
OS: Dapper 6.06, pretty fresh install.

As I finished the install I ran Automatix, and on the next reboot, X didn't start. I rebooted on failsafe and reverted to the xorg.conf backup (nv driver), and it was ok. Then I start trying everything - i.e. download the driver from nvidia.com and install it, which went well, but then when I tried to startx it crashes... also I tried this guy's ([http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)) script, but X also crashes when I start it. 

I'm running out of ideas now, so... help:)

ps- I use linux on this laptop for 3 years now, and never had this problems... I used mandrake and elive.

---

### Post by l.tambiah on 2006-06-19
Personally I would avoid using Automatix, it has broken many ubuntu systems, or so I have been told. You should really install things using *synaptic* or *apt-get* from the terminal. On Ubuntu you dont need to download the nvidia file from the site, you should do the following depending on your card:-[LIST=1]
[*]If you have an older TNT, TNT2, TNT Ultra, GeForce1 or GeForce2 card, install the  [FONT=Courier New]**nvidia-glx-legacy**[/FONT] and [FONT=Courier New]**nvidia-settings**[/FONT] packages from the Restricted repository.
[*]Alternatively, if you have a newer card, install the [FONT=Courier New]**nvidia-glx** [/FONT]package from the Restricted repository.
[*]To enable the new driver:-[/LIST]```
[FONT=Courier New]**$ sudo nvidia-glx-config enable**[/FONT]
``` You can adjust settings by running [FONT=Courier New]**nvidia-settings**[/FONT] in the terminal.

*** Remember*** you must enable your multivesre repositorys NVIDIA is Proprietary and therefore it is NON-FREE.

---

### Post by tseliot on 2006-06-19
Try point 7 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

---

### Post by nunomp on 2006-06-19
l.tambiah:
thank you, but I tried that also and didn't work.

tseliot:
i am going to read again your whole guide to see if something is missing...

---

### Post by Korpil on 2006-06-19
This worked well for me and my Satellite M35 with nVidia GeForce FX Go5200.

However, when I shut down the computer, the screen goes blank and I'm unable to see all the information it displays when shutting down...

---

### Post by tseliot on 2006-06-19
[QUOTE=Korpil]This worked well for me and my Satellite M35 with nVidia GeForce FX Go5200.

However, when I shut down the computer, the screen goes blank and I'm unable to see all the information it displays when shutting down...[/QUOTE]
1) Did you try my suggestion?

2) are you using a recompiled kernel?

---

### Post by nunomp on 2006-06-19
tseliot: 

I put the line "options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1" in /etc/modprobe.d/options and I compiled the driver from nvidia website, and...

Hurray! it works!

now... what exactly is this line for?

thank you for your help. I also copied the other lines into xorg.conf and i'll now try to configure xgl :)

---

### Post by tseliot on 2006-06-20
[QUOTE=nunomp]tseliot: 

I put the line "options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1" in /etc/modprobe.d/options and I compiled the driver from nvidia website, and...

Hurray! it works!

now... what exactly is this line for?

thank you for your help. I also copied the other lines into xorg.conf and i'll now try to configure xgl :)[/QUOTE]
You should ask Nvidia's staff. It's a suggestion that they gave in their forum.

---

