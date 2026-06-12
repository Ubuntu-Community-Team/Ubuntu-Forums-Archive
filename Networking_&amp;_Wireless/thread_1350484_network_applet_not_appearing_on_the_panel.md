---
title: "network applet not appearing on the panel"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by khanbash on 2009-12-09
hi, I'm using ubuntu 9.10. I accidentally removed the network applet from the panel. I'm unable to add it back to the panel. How can I add the network applet. Can someone help.

---

### Post by mikey.duhhh on 2009-12-09
open a terminal and type:

sudo apt-get remove nm-applet
sudo apt-get install nm-applet

or open System>Administration>Synaptic Package manager and search for nm-applet
and reinstall.

---

### Post by c-m on 2009-12-09
I have the same problem. I have to manually type in nm-applet to run the program.

The funny thing is, synaptic/ apt cannot find the package nm-applet at all in the repos nor can it find it to uninstall

---

### Post by HomoGleek on 2009-12-09
> **khanbash said:**
> hi, I'm using ubuntu 9.10. I accidentally removed the network applet from the panel. I'm unable to add it back to the panel. How can I add the network applet. Can someone help.
Correct me if Im wrong, but the network applet is part of the notification area?

So basically add that too the panel?

---

### Post by c-m on 2009-12-09
I have the notification area version 2.80.0 but no network manager unless i manually start it.

---

### Post by HomoGleek on 2009-12-09
> **c-m said:**
> I have the notification area version 2.80.0 but no network manager unless i manually start it.
Preferences > StartUp Applications

Is network manager ticked in there?

---

### Post by c-m on 2009-12-09
yep, that was the first thing i checked.

I tried unticking it restarting and then ticking it again and restart but to no avail. I don't have a sound mixer either in my notification area. The applet just isn't there

---

### Post by mikey.duhhh on 2009-12-09
Yup.  I was an idiot.  Go to System>Preferences>Startup Applications   and scroll down until you find network manager, click to check Network Manager and possibly Indicator Applet


er...  network-manager-gnome is the synaptic name.  So lets try the following:
To the left of where the battery, wireless, etc. on the upper right part of the top panel, move that almost invisible verticle doulbe line to the left a bit, and right click "add to panel", choose add "custom application launcher" and (here I opened a terminal and typed "whereis nm-applet" and it gave me two answers, but let's use the one from /usr/share/nm-applet) when the pop-up shows up it will give you some options 

name: wireless
command: /usr/share/nm-applet
comment: let's see if this works.
hit okay.

If it fails try adding gksudo to the front of command area, as in 
command: gksudo /usr/share/nm-applet

Try this one out.  See what happens.  I've learned that you sometimes have to experiment to get things working, or if you have a fresh install of 9.10 try reinstalling it again.

---

### Post by chandolin on 2009-12-25
I had the same problem, and solved by right-click on the panel, then add "notification area", and not only the network applet came again, but also the sound and battery applets.

---

### Post by c-m on 2009-12-25
> **chandolin said:**
> I had the same problem, and solved by right-click on the panel, then add "notification area", and not only the network applet came again, but also the sound and battery applets.

I nave a notification area already.

---

### Post by c-m on 2009-12-25
> **mikey.duhhh said:**
> Yup.  I was an idiot.  Go to System>Preferences>Startup Applications   and scroll down until you find network manager, click to check Network Manager and possibly Indicator Applet


er...  network-manager-gnome is the synaptic name.  So lets try the following:
To the left of where the battery, wireless, etc. on the upper right part of the top panel, move that almost invisible verticle doulbe line to the left a bit, and right click "add to panel", choose add "custom application launcher" and (here I opened a terminal and typed "whereis nm-applet" and it gave me two answers, but let's use the one from /usr/share/nm-applet) when the pop-up shows up it will give you some options 

name: wireless
command: /usr/share/nm-applet
comment: let's see if this works.
hit okay.

If it fails try adding gksudo to the front of command area, as in 
command: gksudo /usr/share/nm-applet

Try this one out.  See what happens.  I've learned that you sometimes have to experiment to get things working, or if you have a fresh install of 9.10 try reinstalling it again.

I get permission denied when trying run the launcher i just created.

---

