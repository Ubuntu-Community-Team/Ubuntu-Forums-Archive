---
title: "White Screen of death after removing propreity ATI graphics card driver"
date: 2008-09-03
forum: Multimedia Software
---

### Post by JDCOMPUTING on 2008-09-03
Hi, I am new to Ubuntu so excuse my lack of knowledge.

Yesterday I attempted to get my ATI x1950xt fully operational with Ubuntu as it was running with propreity drivers that were not optimising the performance. I managed to work out (after a few hours!) how to use the console and install the drivers from ATI's website for Linux.

After doing this successfully I rebooted to see that the refresh rate/text was still as it was before and I didn't beleive it was using the driver. So I went to hardware drivers and saw that the propreity driver for my graphics card was still active. I unchecked the tick box and rebooted, hoping that the drivers I installed would take affect.

Unfortunately this was not the case, and once passed the log in screen I was greeted by the white screen of death. I tried to access'recovery mode' thinking it would be like windows, but after running every recovery option to no affect I have realised the only way round this is using the recovery terminal. What the hell do I do? Will I have to re-intall Ubuntu?

P.S I can still dual boot into windows if that helps, thought I doubt it.

---

### Post by andycs on 2008-09-03
Try booting into recovery and running this from the command line;  

```
sudo dpkg-reconfigure xserver-xorg
```

That should open a dialogue that reconfigures xorg.conf for you, and should hopefully fix your system to how it was before. You still won't have the new driver, though.

---

### Post by JDCOMPUTING on 2008-09-06
Thanks I have tried this, unfortunately nothings changed. Any ideas how to reset everything/driver settings?

---

### Post by overdrank on 2008-09-06
> **JDCOMPUTING said:**
> Thanks I have tried this, unfortunately nothings changed. Any ideas how to reset everything/driver settings?

Hi and if you are using Hardy then you may try and use the xfix option when booting into recovery mode which is usually the second choice from the grub.

---

### Post by JDCOMPUTING on 2008-09-06
Hi, i've tried all the other recovery options from the recovery menu to no avail? Any ideas before I am forced to format?

---

### Post by JDCOMPUTING on 2008-09-10
Please guys im desperate. I ahve taken the time to write in another forum EXACTLY whats happening. Can anyone help?

Hi, Im new so please be patient and help would be MUCH appreciated on this one!

I decided to geek out to Linux with the Ubuntu distro (Hardy Heron). I had a bit of a play round, rebooted a few times and downloaded a few things. Later on, I managed to get a hang of the terminal and decided to download and install drivers for my ATi graphics card instead of using the limited propreity drivers. I browsed the ATI website and saw only drivers for 'x1900 series' , my card being an ATi x1950 PRO 512mb. I thought that the 1950 is part of the x1900 series so carried on regardless.

After installing I rebooted to notice that the graphics quality was the same and no better. I saw that the propreity drivers I had previously activated where still active and ticked, so I thought it would be a good idea to untick this box and reboot. My theory was after restarting maybe the drivers which I beleived I had installed after following the graphical install prompts would take affect.

Upon rebooting and logging on I was greeted briefly by a black screen and then by an eternal white screen of death. I could do nothing.

I had a browse through the recovery options of Ubuntu, and realised this was no windows style safe mode! I ran all the options such as 'xfix' to no avail. I then ventured onto the Ubuntu support forum, hoping for some great open-source geeks to come to my aid. Unfortunately I had hardly any replies. The only one I had to help advised me to drop to the terminal shell and type..

"sudo dpkg-reconfigure xserver-xorg.conf"

I hoped maybe this would reset all settings to default. But it didn't work. 

So I bit the bullet and re-installed Ubuntu. After I re-installed I got straight to work downloading the drivers. I decided not to tick the propreity drivers box for my card this time. I downloaded the drivers again and tried to install through terminal. For problems unknown and unrelated I couldnt get the install to start. So I rebooted and tried later - and there it was the white screen of death again!

This led me to beleive that maybe it wasn't to do with the drivers I installed online and something else. Note this time also, I had not ticked the box for propriety drivers. Did this have an effect? The first time Ubuntu booted it didn't have anything ticked or the drivers installed so I can't see how?

Anyway, I re-installed Ubuntu AGAIN. This time I went straight to terminal, downloaded the 'x1900' series drivers for my x1950 pro ATi graphics card, and installed. I followed all the prompts and installed successfully, and then rebooted. And low and behold I have been greeted by another white screen of death!

So I am extremely confused?  

Is it the drivers? Is it Ubuntu? What the hell is it? Is there a way of rebooting to default graphics settings?

Please help, as I am loving the Linux terminal and would really love to learn about it  . But this is a big hurdle at the moment and I dont want to re-install just for the same thing to happen!!!

---

### Post by Buttons840 on 2008-09-10
Hi, I can't help, but have a similar problem.

Have you tried booting from the Ubuntu CD?

Anyways, I share your frustration as I have been unable to get any help with my similar issue.  I did a search through the forums and found some others with issues like it, but just like this tread all the replies were just updates from the OP and nobody had any ideas.  It's hard for others to help I guess, as they don't have the same hardware and can't recreate the issue.

---

### Post by CarpKing on 2008-09-10
When I've gotten a "white screen of death" it's been from Compiz trying to start when 3d-rendering has failed.  On the login screen, there should be a button labeled "Options" or "Select Session" or something like that.  This should bring up a menu with several options.  Select "Failsafe Gnome" and login.  Then post the output of 

```
cat /etc/X11/xorg.conf
```

and

```
cat /var/log/Xorg.0.log | grep EE
```

Hopefully that will give us some idea of what's going wrong.  Hang in there.

---

### Post by tedrogers on 2008-09-14
Try this mate:

[http://ubuntuforums.org/showthread.php?t=766699&page=3](http://ubuntuforums.org/showthread.php?t=766699&page=3)

I've got the white screen of death with my X1950 at the moment, well, it's either that or half all the sides of the screen are missing. It's bonkers!

I will be trying the Envy fix they mention on the above link. Hope it works for you too.

Let us know how you go.

---

