---
title: "I think I just disabled the unity plugin"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-03-12
Hi,

I was messing with Compiz settings in ccms and it crashed on me. I think I might have disabled the Unity plugin accidentally. On reboot I get a blank screen with only the notification icon that says wireless is connected (so at least wireless works) Compiz itself is running because I can switch desktop with ctr-alt left/right.

Is there a way to get back the desktop without reinstalling? 

I configure to autologin so I don't have a login screen to go to other desktop.

P.S. They should have some safeguard against this, it is a bit scary that your desktop disappears because of one Compiz plugin!

---

### Post by wilee-nilee on 2011-03-12
If crtl-alt-t gets you a terminal you can logout.
[http://askubuntu.com/questions/15795/how-can-you-log-out-via-the-terminal](http://askubuntu.com/questions/15795/how-can-you-log-out-via-the-terminal)

I am sort of assuming the commands are the same.

---

### Post by kerry_s on 2011-03-12
right click & add a folder, click on the folder to open the file manager, go to /usr/share/applications, from there you can start compiz manager & enable unity.

---

### Post by beew on 2011-03-13
> **wilee-nilee said:**
> If crtl-alt-t gets you a terminal you can logout.
[http://askubuntu.com/questions/15795/how-can-you-log-out-via-the-terminal](http://askubuntu.com/questions/15795/how-can-you-log-out-via-the-terminal)

I am sort of assuming the commands are the same.

Hi, 

Tried that.

crtl-alt-t doesn't work any more.

---

### Post by beew on 2011-03-13
> **kerry_s said:**
> right click & add a folder, click on the folder to open the file manager, go to /usr/share/applications, from there you can start compiz manager & enable unity.

It works! Thanks. I am surprised that I don't need root permission to do that.
(Of course alt+F2 doesn't work either

---

### Post by DougieFresh4U on 2011-03-13
Can't help but will say that every time I have gone into compiz settings, I get 'the crash' also. The whole top panel 'goes away'.
Usually a reboot into 'Ubuntu Classic Desktop' and a little tinkering around will fix me back up. :p

---

### Post by kerry_s on 2011-03-13
> **beew said:**
> It works! Thanks. I am surprised that I don't need root permission to do that.
(Of course alt+F2 doesn't work either

you didn't set up a alt+f2 ?
ya got to think ahead. see pic

---

### Post by kuvanito on 2011-03-13
hi beew
that just happen to me yesterday and I ended up reinstalling the whole thing,i wish this post was here back then,hehehehe
yes,it is true! since the ubuntu team is going unity they should have some safeguard about this plugin so that you can not desable it....
in other news,i installed the latest Gnome 3 shell and it looks better than Unity,at least for me but i have not figure it out on how to keep it as default,every time i boot i must start it manually in a terminal. :p

---

### Post by Harry33 on 2011-03-13
> **kuvanito said:**
> hi beew
that just happen to me yesterday and I ended up reinstalling the whole thing,i wish this post was here back then,hehehehe
yes,it is true! since the ubuntu team is going unity they should have some safeguard about this plugin so that you can not desable it....
in other news,i installed the latest Gnome 3 shell and it looks better than Unity,at least for me but i have not figure it out on how to keep it as default,every time i boot i must start it manually in a terminal. :p

If you have installed Gnome-shell from Gnome3 PPA, all you need to do is to install the package "gnome3-session".
Then from login screen, choose Gnome3 session. It is then default until you change it again.

---

### Post by kuvanito on 2011-03-13
Thank You harry
will do that in a min,:D

---

### Post by MadCow108 on 2011-03-13
this bug?
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729657](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729657)

---

### Post by kuvanito on 2011-03-13
thanks harry
it worked
i now have the Gnome 3 Shell as my default desktop
thanks unity but no thanks,for now anyway,it may get better later on,i'll c :D

---

### Post by irfan20uk on 2011-04-26
> **kerry_s said:**
> right click & add a folder, click on the folder to open the file manager, go to /usr/share/applications, from there you can start compiz manager & enable unity.


@ Kerry, Thanks alot for your clue, that certainly solve me messing up more and hold up for reinstallation. Thx again.... 
cheers,

---

