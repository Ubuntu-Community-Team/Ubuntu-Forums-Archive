---
title: "[SOLVED] (EE) fglrx(0): Unknown EDID version 0"
date: 2008-10-29
forum: Multimedia Software
---

### Post by Valpskott on 2008-10-29
I don't know what I've done really... I restarted the system(8.10) after a couple of hours of screwing around with settings and get this error message during boot.

(EE) fglrx(0): Unknown EDID version 0

I've tried to both use a backup of xorg.conf and reinstall ENVYNG and all FGLRX related drivers I could find i Synaptic but nothing helps... still get that same error message and have to boot with vesa driver(I think). Every time I try to activate Enhanced Graphics I'm told to reboot and upon reboot I get that same error again.

---

### Post by Valpskott on 2008-10-29
-[SOLVED]-

I switched to a Nvidia card I got from my other computer, installed the driver recommended in ENVY GN and the graphics worked fine(some things a little slower due to the card not being all that powerful), and then I uninstalled that driver and switched back to my ATI card and installed the driver, and now everything works just fine again.

My best guess is that something got reset somewhere in the system, I'm new to this whole Linux thing so... just thought I'd share this info in case someone could figure out what happened so that others could benefit from this if the same problem arises for someone else(who doesn't have a spare GFX card laying around).

---

### Post by Valpskott on 2008-11-06
Problem reoccurred when I put the connector from the TV into the TV-out in my videocard... and the problem goes away when I disconnect the connector.

Is it possible that any "aticonfig" command could have caused this? Cause I didn't have this problem after clean install of Ubuntu(8.10) and ATI drivers.

I tried the following command:
"$ aticonfig --resolution=0,1440x900"

Does this command change any file, if it does, what file?
Is there a way to reset that file to default?

---

### Post by PowerPanda on 2008-11-06
I have exact same problem. aticonfig modofies /etc/X11/xorg.conf

Please remove the SOLVED from the forum, since I haven't found a solution! Very annoying, since laptop starts up fine if tv is unplugged from it. ARgh.

---

### Post by theadmiral on 2008-11-07
I to am having this problem. Everything worked fine untill i tried to set my dual screen up dual head instead of just cloned screen. when i did that and rebooted i got that error. I can boot error free without the fglrx drivers installed but then i dont have dual screen at all. i can not reinstall the fglrx drivers even for a single screen setup at all now.

has anyone found a solution or have anymore info on what the cause of the error may be?

---

### Post by jmolinuevo on 2008-11-15
I have the same problem. TV out worked correctly in clone mode from a clean install of Intrepid Ibex, but when I tried to change to a big desktop mode something got wrong, and now every time TV is plugged to the computer, fglrx driver fails to load. I think I have tried everything, from reinstalling fglrx driver, initializing xorg.conf, installing the driver using envy-ng... nothing works, fgrlx only loads correctly if TV is not plugged.

Now I would be happy if at least I could get clone mode again without reinstalling ubuntu again. I use an Acer Aspire 1692LMi laptop with an ATI MOBILITY RADEON X700 video card.

---

### Post by jmolinuevo on 2008-11-15
I have followed a suggestion posted [[COLOR="Blue"]**_here_**[/COLOR]]("http://ge.ubuntuforums.com/showthread.php?t=782068#2") and now I have recovered TV output in clone mode.

I guess that [COLOR="DarkGreen"]/etc/ati/amdpcsdb[/COLOR] is the fglrx driver configuration file, and when it is deleted default file ([COLOR="DarkGreen"]/etc/ati/amdpcsdb.default[/COLOR]) is used to generate a new configuration file, thus clone mode works again as in a clean install. I think that [COLOR="DarkGreen"]aticonfig[/COLOR] command (or [COLOR="DarkGreen"]ATI Catalyst Control Center[/COLOR]) modifies this configuration file. Maybe the key to get dual head mode is to edit this file with the appropriate instructions.

---

### Post by Valpskott on 2008-11-15
Ohh man, thank you, thank you, thank you, thank you!!!
This solved it for me... I'm using dual boot(win xp for watching movies on the TV), and now I don't have to crawl under the desk(to connect or disconnect TV-out cable) every time I switch OS. Again, thank you! :D

I'm switching this thread to Solved again...
PowerPanda, if you still have problems after trying the solution, let me know and I'll change the status back to unsolved, ok?

---

### Post by v66r on 2008-11-25
Hi

I also have this problem, the hint with deleting this file mentioned did not work for me.

Using an ATI (ASUS) 9800 XT AGP Card with an Elsa Ecomo 531 CRT Monitor conntected to it via analog D-SUB. Nothing special (TV or such things). 

This looks to me like the driver is not able to detect the capabilities of my monitor - so I tried to set up the stuff manually:
```

aticonfig --force-monitor=crt1,notv
aticonfig --resolution=0,1280x1024

```

Which did not solve the problem 
for me it looks like that gdm does not use any manually configured stuff from /etc/X11/xorg.conf

Does anybody have a hint?

Thanx

---

### Post by jbrown123 on 2009-05-26
In response to #7 above, the correct link to the other thread is

[http://ubuntuforums.org/showthread.php?t=782068#2](http://ubuntuforums.org/showthread.php?t=782068#2)

Basically all it says to do is

**sudo rm /etc/ati/amdpcsdb**

After this you need to **reboot** and the system will use the default version of the file to restore the settings.

---

