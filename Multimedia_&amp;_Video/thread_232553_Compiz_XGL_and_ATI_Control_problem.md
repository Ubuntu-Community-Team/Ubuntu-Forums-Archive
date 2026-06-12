---
title: "Compiz XGL and ATI Control problem"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by Dropknee on 2006-08-08
Compiz and XGL work great with the latest drivers from ATI in my system, but have some problem, and I dont know is this is a driver problem or a Compiz, XGL problem.

First in the Log-in screen, sometime my keyboard simply dont work, I reboot my computer with the mouse and keyboard work again, this problem is not all the time, but happen frecuently.

Second, when I have XGL enable, the ATI control, where you can set display and all that thing, this simply dont work at all, when I try to lunch the application this give me the following message

 "Driver do not provide the FireGL X11 extensions!
  Panel Components will operated only partially"

Third, I use Cedega, and all of you out there know about Cedega testing hardware, and one of this test fail and is the OpenGL Direct Rendering all the other test pass without any problem.

All this happen when Im in Compiz, XGL, in normal Gnome Desktop, the ATI Control and all the Cedega hardware test pass without problem.

I search the forum about this without success, pls  someone help me here.

Thx

---

### Post by hexion on 2006-08-12
Same here :(

Don't worry for Cedega's tests. It works properly.

---

### Post by hexion on 2006-08-12
Try this:

> DISPLAY=:0.0 /usr/bin/fireglcontrolpanel &


or

> DISPLAY=:93 /usr/bin/fireglcontrolpanel &


---

### Post by Dropknee on 2006-08-13
> DISPLAY=:0.0 /usr/bin/fireglcontrolpanel &

This work for me, but when I execute this via Application-Accessories-ATI Control Panel, the problem persist.

Any help???

---

### Post by hexion on 2006-08-13
The only thing you can do is editing the menu entry.

To do that execute "alacarte", go to accesories and right-click ATI control panel.

Then write DISPLAY=:0.0 before the command that will appear there and save.

---

### Post by Dropknee on 2006-08-13
I do your recommendation but this happen when I edit the ATI Contol Panel in Alcarte:

Could not launch menu item

Details: Failed to execute child process "DISPLAY=:0.0" (No such file or directory)

---

### Post by hexion on 2006-08-14
I said you should put DISPLAY=:0.0 **before** what's there, not **in place of** that.

The menu item must be:

> DISPLAY=:0.0 /usr/bin/fireglcontrolpanel

---

### Post by Dropknee on 2006-08-14
> I said you should put DISPLAY=:0.0 before what's there, not in place of that.

I dont remplace the command with DISPLAY=:0.0 I put the entire command but that is the error the program show when I try to execute via menu.

---

### Post by hexion on 2006-08-14
Ops, you are right... I've made that and same error.

Strange... that should work...

Try this instead:

> 
cd /usr/bin
sudo pico ati_control_panel


Then edit that file with this:
> DISPLAY=:0.0 /usr/bin/fireglcontrolpanel

Save the file and give it execute permision:
> sudo chmod +x ati_control_panel

Then edit the menu item, changing it to:
/usr/bin/ati_control_panel

That should work. Tell me if it doesn't... if so we better call Mulder and Scully ;)

---

### Post by Dropknee on 2006-08-14
Thx :D this work like a charm, Thx again for your support, I hope this work for all ppl out there with the same problem.

Keep the good work and support :D

---

### Post by hexion on 2006-08-14
You're wellcome ;)

It's the magic of free software and these kind of forums... simple users like us can help eachother.. :)

Bye

---

### Post by Co.Sinecure on 2006-08-20
Hi..

I've got the same issue as the thread poster, and the 'DISPLAY=:0.0 ...' command gives me the same error, and shows the 'Information' tab only for the control panel.

The 'DISPLAY=:93 ...' returns an error 
> fireglcontrolpanel: cannot connect to X server :93

Am I missing libraries or something? 
xorg-driver-fglrx and xserver-xorg-driver-ati are installed, can't spot anything else in adept..

Also I used easyubuntu to install the drivers, if that makes a difference.

Thanks..

---

