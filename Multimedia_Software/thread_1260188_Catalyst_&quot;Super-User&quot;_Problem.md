---
title: "Catalyst &quot;Super-User&quot; Problem"
date: 2009-09-07
forum: Multimedia Software
---

### Post by Stone_Soup on 2009-09-07
I got my video card (MSI ATI Radeon HD 4830) running great with the drivers installed. Catalyst however is giving me problems configuring it. When I try and open it via Applications > Other > ATI Catalyst Control Center (super-user) I get the error message: 

[CENTER][SIZE=2][B]Could not launch 'ATI Catalyst Control Center (super-user)'
Failed to execute child process "amdxdg-su" (No such file or directory)[/B]

[/SIZE][LEFT]I want to set up dual monitors in a few days and the only way to use Catalyst to do this is to get access as super-user. Any help is greatly appreciated. Happy Labor Day!
[/LEFT]
[/CENTER]

---

### Post by sora90 on 2009-09-13
[http://ubuntuforums.org/showthread.php?t=1257434&highlight=amdxdg-su](http://ubuntuforums.org/showthread.php?t=1257434&highlight=amdxdg-su) 

i am having the exact same problem please inform me if you have found the solution

it seems that typing this code "gksudo amdcccle" without the quotes in the terminal could bring the control center out with all options.

---

### Post by swajime on 2009-09-15
Easy fix for me was:
Gnome menu | System | Preferences | Main Menu | Applications | Other | ATI Catalyst Control Center (super-user)" | Properties | Command:
Change "amdxdg-su -c amdcccle" to "gksu amdcccle"
(based on sora90's answer)
-- 
John

---

### Post by danellisuk on 2009-09-17
Has anyone created a bug for this on launchpad?  I am aware that the restricted driver is not maintained by canonical, but I expect it would be possible to just change the shortcut on the menu.

I am very pleased to see that the Radeon HD 4200 that comes with the Asus M4A785TD-M EVO is working out the box on Karmic Alpha 5 :)

---

### Post by Dakra on 2009-11-07
> **swajime said:**
> Easy fix for me was:
Gnome menu | System | Preferences | Main Menu | Applications | Other | ATI Catalyst Control Center (super-user)" | Properties | Command:
Change "amdxdg-su -c amdcccle" to "gksu amdcccle"
(based on sora90's answer)
-- 
John

Thanks a lot, it is working now.

---

### Post by Sorinux on 2009-11-15
Hello.
I installed the driver for my Gainward HD4850 using EnvyNG. When I tried to open the Control Center with administrative rights I had that error: Failed to execute child process "amdxdg-su" (No such file or directory)
 
After I followed the instruction posted here, I can not open any Control Center (simple or with administrative rights). When I try to open any of them nothing is loading on my computer.
What could be the problem?

And second question: after installing the driver, in System>Preferences>Display for "refresh rate" is available only 60Hz. But before installing the driver I was using 75Hz.

Anybody has any idea?

PS: I am using Ubuntu 9.10 64bit.

---

### Post by 4tro on 2009-12-01
> **swajime said:**
> Easy fix for me was:
Gnome menu | System | Preferences | Main Menu | Applications | Other | ATI Catalyst Control Center (super-user)" | Properties | Command:
Change "amdxdg-su -c amdcccle" to "gksu amdcccle"
(based on sora90's answer)
-- 
John

that's what i call a workaround, not a fix, this is exactly what the Ubuntu Papercut initiative is all about, minor things annoying the starting linux user.
But this is such an in your face bug, i hardly believe they haven't noticed it yet, either at canonical or at AMD headquarters

---

### Post by meuzak on 2009-12-20
> **swajime said:**
> Easy fix for me was:
Gnome menu | System | Preferences | Main Menu | Applications | Other | ATI Catalyst Control Center (super-user)" | Properties | Command:
Change "amdxdg-su -c amdcccle" to "gksu amdcccle"
(based on sora90's answer)
-- 
John

Thanx John...worked just fine.

---

### Post by kronictokr on 2009-12-26
thank you worked 4 me

hp pavillion dv6 ati 4200

---

### Post by createsean on 2010-01-03
this also worked for me, but took a lot of looking around to find. 

I just needed to be able to rotate my display, wish that was just built in rather than having to hack it like this.

---

### Post by mazz0 on 2010-01-14
I did this, but I've noticed it does not remember my refresh rate - every time I boot up it's running at 30 and I have to go in and change it to 60.

Anyone else get that?

Anyone any ideas?

---

### Post by savory19 on 2010-02-15
edit: worked - thanks!  i guess they renamed the executable without updating the default shortcut

---

### Post by ProNux on 2010-04-03
It worked for me.  (Powercolor HD4850, 1GB) Thanks.

---

### Post by ezcex on 2010-04-16
Works great, thanks.

---

### Post by a only on 2010-04-24
i have the same problem with ATI 3400 desktop and I've done what you write and the ATI program  working good but the problem is with the resolution it gives me max 720X480 and it was 1440X900 What is the solution now please help.

note: the ubuntu that i installed it was 9.04 and upgraded to 9.10, but in 9.04 was working perfectly

---

### Post by a only on 2010-04-24
hello any body there 
please help

---

### Post by a only on 2010-04-25
any way thanks :confused:

---

### Post by Szelev71 on 2010-08-09
Nice solution! Thanks!

---

### Post by charlesedwardkelley on 2011-04-14
Seems I am a bit late to the party. Just wanted to say thanks to sora90__ and swajime this worked great for me!

---

### Post by klasw on 2013-01-29
This is also an alternative, function for me as I rum Kubuntu (and not have gksu):

sudo nano /usr/share/fglrx/amdccclesu.desktop

Change to:
 
Exec=su-to-root -X -c amdcccle


I think this is the way AMD should implement it, as it is not depending on with desktop environment you tun (Gnome ore KDE).

---

### Post by howefield on 2013-01-29
Old thread closed.

---

