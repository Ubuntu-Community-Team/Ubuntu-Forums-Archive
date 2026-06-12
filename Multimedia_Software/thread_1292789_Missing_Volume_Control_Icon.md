---
title: "Missing Volume Control Icon"
date: 2009-10-16
forum: Multimedia Software
---

### Post by gwvenus on 2009-10-16
Hi Everyone,
I've just installed Ubuntu 9.10 and noticed there is no volume control icon in the task bar. Does anyone know how to add this icon?
Thanks,
Gary

---

### Post by ajgreeny on 2009-10-16
Right click on the panel where you want it and choose to add Volume Control.  It normally is on the top panel, not the bottom task bar, but put it, and everything else, wherever you want it.  I run gnome, but only have one panel with the gnome main menu instead of menubar, to save screen area.

---

### Post by gwvenus on 2009-10-16
Hi ajgreeny,
Thanks for the quick reply, but that option dosen't appear to exist. No matter where I left click on the panel ( I only have one panel as well,) my only options are "add to panel", "properties", and "new panel". No option for volume control anywhere. Am I blind?
Thanks,
Gary

---

### Post by gwvenus on 2009-10-16
Hi ajgreeny,
In my last post I meant to say "right click."
Cheers,
Gary

---

### Post by bhishan on 2009-10-16
> **gwvenus said:**
> Hi ajgreeny,
Thanks for the quick reply, but that option dosen't appear to exist. No matter where I left click on the panel ( I only have one panel as well,) my only options are "add to panel", "properties", and "new panel". No option for volume control anywhere. Am I blind?
Thanks,
Gary

Select "add to panel" and it will give you a list of things that you can add to the panel. The "volume control" should be in that list.

---

### Post by sal_m on 2009-10-18
> Select "add to panel" and it will give you a list of things that you can add to the panel. The "volume control" should be in that list.

You should add "Notification Area".  If you still have no volume icon, check to make sure that the gnome-volume-control-applet is running.  This is usually set to startup automatically when you login.

---

### Post by gwvenus on 2009-10-24
Hi sal_m,
You were right on the money! Thank you very much. I now have a speaker icon, but I also have two other icons I don't need. There is no right click "remove from panel". Do you know how I can remove the other two icons and just keep the speaker icon?
Thank You,
Gary

---

### Post by NoTownKasper on 2009-11-06
The 'Notification area' seems to be a lot like the Windoze 'tray'. The other icons, for instance, you probably have a networking icon of some variety along with a couple others, are, most likely, other running programs that fit into the notification area. I'm not sure you -can- remove them without removing the entire notification area, and thusly, your volume control.

---

### Post by keithwwalker on 2009-11-10
Thank you!  Notification Area did the trick!

> **sal_m said:**
> You should add "Notification Area".  If you still have no volume icon, check to make sure that the gnome-volume-control-applet is running.  This is usually set to startup automatically when you login.

---

### Post by coolnezz on 2009-11-27
> **sal_m said:**
> You should add "Notification Area".  If you still have no volume icon, check to make sure that the gnome-volume-control-applet is running.  This is usually set to startup automatically when you login.



Thanks a lot!  "Notification Area" solved it.  I was pulling my hair because I accidentally deleted the volume icon, because it was showing two icons!

---

### Post by Krzysztow on 2009-11-29
I also lost the volume icon, when I added new panel. Then nothing helped, cause I had already notification area. The solution was to delete notification area and add it once again, so thanks for help!

---

### Post by De4dSpace on 2010-01-04
You guys lost your icon.  My Karmic upgrade added Volume Control and Network Manager icons.  If you wanna remove an individual icon go System > Preferences > Startup Applications.  Got rid of the Volume Control and Network Manager, was able to keep the notification area.

---

### Post by garvinrick4 on 2010-01-04
Everybody seems to have done that at one time or another so do not feel alone.

---

### Post by sweBers on 2010-02-22
> **sal_m said:**
> You should add "Notification Area".  If you still have no volume icon, check to make sure that the gnome-volume-control-applet is running.  This is usually set to startup automatically when you login.

Thank you for this information.  I did a kernel update and ended up with two volume icons.  In a failed attempt to correct the situation, I had deleted one causing both to disappear.  This notification applet added the volume icon back to my top panel instantly along with my missing connection status applet.

---

### Post by premsoni4u on 2010-05-22
> **gwvenus said:**
> Hi Everyone,
I've just installed Ubuntu 9.10 and noticed there is no volume control icon in the task bar. Does anyone know how to add this icon?
Thanks,
Gary

[FONT="Verdana"]After doing RnD for a long time, finally I find the way to restore VOLUME CONTROL in task bar in Ubuntu 9.10.

1. First add "Notification Area" to Task bar by right click on task bar and choose "Add to panel"

2. Make sure "Volume Control" should be selected in "Startup Application Preference". If it is not selected, do it by clicking on System> Preferences> Startup Applications.

3. Reboot Now

4. You are done.

--
Enjoy
**PREM SONI**
Write to: [email]PremSoni4u@Gmail.com[/email]
Visit: [COLOR="Red"]wWw.PremSoni.TK[/COLOR][/FONT]

---

### Post by ramrumram on 2010-06-16
Looks ugly but very simple "System-> preference-> audio ->[r.click] add this launcher to panel' :)

---

### Post by imac_89 on 2010-09-06
You can also remedy this issue by adding the "Indicator Applet" back into your panel as well. I learned this tip from this webpage: [http://www.virtualhelp.me/linux/107-volume-controlicon-is-gone-ubuntu-1004](http://www.virtualhelp.me/linux/107-volume-controlicon-is-gone-ubuntu-1004)

---

### Post by beercz on 2010-10-14
> **imac_89 said:**
> You can also remedy this issue by adding the "Indicator Applet" back into your panel as well. I learned this tip from this webpage: [http://www.virtualhelp.me/linux/107-volume-controlicon-is-gone-ubuntu-1004](http://www.virtualhelp.me/linux/107-volume-controlicon-is-gone-ubuntu-1004)
This worked for me - thanks!

---

### Post by Myglaren on 2010-10-17
> **beercz said:**
> This worked for me - thanks!

Worked for me too, none of the other suggestions worked as there were no relevant entries to cover the problem.
Thanks :)

---

### Post by ericmarceau on 2010-12-05
IGNORE.

I found another posting which provided the missing connection: [http://www.virtualhelp.me/linux/107-volume-controlicon-is-gone-ubuntu-1004](http://www.virtualhelp.me/linux/107-volume-controlicon-is-gone-ubuntu-1004)

Thx,

EM

-----------------------------------------------------------

If ¨Volume Control¨ is not a choice shown/listed in the ¨Startup Application Preference¨, how do we get it there?

Thx,

EM

> **premsoni4u said:**
> [FONT="Verdana"]After doing RnD for a long time, finally I find the way to restore VOLUME CONTROL in task bar in Ubuntu 9.10.

1. First add "Notification Area" to Task bar by right click on task bar and choose "Add to panel"

2. Make sure "Volume Control" should be selected in "Startup Application Preference". If it is not selected, do it by clicking on System> Preferences> Startup Applications.

3. Reboot Now

4. You are done.

--
Enjoy
**PREM SONI**
Write to: [email]PremSoni4u@Gmail.com[/email]
Visit: [COLOR="Red"]wWw.PremSoni.TK[/COLOR][/FONT]

---

### Post by wsonar on 2011-03-17
I'm running a fresh install of 10.0 and lost my icon in the notification area I have no option for it under add to panel or in the startup applications

---

### Post by miahotrod on 2011-04-14
> **imac_89 said:**
> You can also remedy this issue by adding the "Indicator Applet" back into your panel as well. I learned this tip from this webpage: [http://www.virtualhelp.me/linux/107-volume-controlicon-is-gone-ubuntu-1004](http://www.virtualhelp.me/linux/107-volume-controlicon-is-gone-ubuntu-1004)

Indicator applet worked for me I am using 10.10 thanks !!

---

