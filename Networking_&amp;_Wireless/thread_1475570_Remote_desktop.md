---
title: "Remote desktop"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by finlost on 2010-05-07
I just set this up.  I am sitting on my couch with my laptop and my desktop is across the room.  Both machines are running Ubuntu 9.10.  

I was able to connect to my desktop from my laptop.  When I would click a folder or on a menu on my desktop via my laptop, the action wouldn't show on my laptop.  The action would appear on the desktop though.  In other words, the controlling computer wasn't seeing the actions being performed on the remote computer.

I am not sure what I am missing as the setup straight forward.

---

### Post by lisati on 2010-05-07
Moved to own thread

---

### Post by prshah on 2010-05-07
> **finlost said:**
> When I would click a folder or on a menu on my desktop via my laptop, the action wouldn't show on my laptop. 

The "Remote Desktop" included in Ubuntu only works when compositing / Compiz / Desktop Effects is turned off.

You can get hold of a program to toggle compositing on/off, or do it manually with the command```
metacity --replace
``` to turn off, and ```
compiz --replace
``` to turn back on.

The commands can be run from the Alt+F2 command box.

Post back if you need more information.

---

### Post by finlost on 2010-05-07
I will check that out as I am running Compiz on both machines.

---

### Post by prshah on 2010-05-08
> **finlost said:**
> I will check that out as I am running Compiz on both machines.

You need to turn off Compiz only on the vncserver machine; ie, the machine you vnc into, in this case your desktop.

---

### Post by finlost on 2010-05-10
Is there a way to remotely turn off Compiz on the vncserver?  I am assuming there are ways to do it, but looking for the least intrusive way.


Edit:  I was able to click on the terminal icon I have on the Ciaro dock and blindly type "metacity --replace".  

Wow, horrible latency once logged in and navigating around!

---

### Post by prshah on 2010-05-10
> **finlost said:**
> Is there a way to remotely turn off Compiz on the vncserver?  
 looking for the least intrusive way.


You can use the "Compositing Toggle" screenlet. You need to install screenlets for this.```
sudo apt-get install screenlets
``` then open System-Acessories-Screenlets and look for the Compositing Toggle (Or words to that effect) screenlet.

---

### Post by finlost on 2010-05-10
> **prshah said:**
> You can use the "Compositing Toggle" screenlet. You need to install screenlets for this.```
sudo apt-get install screenlets
``` then open System-Acessories-Screenlets and look for the Compositing Toggle (Or words to that effect) screenlet.
Navigating menus _remotely_ is next to impossible since the machine I am doing this from isn't showing the remote desktop activity with Compiz running.

If I can setup a hotkey/key binding to get Compiz to toggle on and off, then it will work.

For now, clicking on the terminal icon on the Ciaro dock and then blindly typing "metacity --replace" works.

---

### Post by prshah on 2010-05-10
> **finlost said:**
> Navigating menus _remotely_ is next to impossible since the machine I am doing this from isn't showing the remote desktop activity with Compiz running.

No one's asking you to install screenlets remotely. Sit at your VNC server machine (in this case, the desktop machine), install screenlets, enable the "Compositing Toggle" screenlet, set it up at a convenient point on the screen desktop. 

Whenever you connect remotely, click the "Off" radio button on the screenlet, and compositing will be turned off.

---

### Post by VeeDubb on 2010-05-19
Is there another VNC server you could recommend that doesn't require you to disable compositing?

As far as I can see, it's not just compiz, but all compositing.  Gnome-shell, unity, even the UNR launcher, all behave the same way.

This is going to become a serious issue in a year's time when gnome-shell becomes the default WM, and in 6 months, unity will be the default on Ubuntu Netbook Edition.

---

