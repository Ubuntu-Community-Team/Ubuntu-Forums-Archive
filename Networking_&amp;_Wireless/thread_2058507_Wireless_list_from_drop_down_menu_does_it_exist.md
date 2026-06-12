---
title: "Wireless list from drop down menu does it exist?"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by afulldeck on 2012-09-15
Is there a way to enable the drop down menu to show the available wireless networks in the immediate area? Something between the bluetooth and battery icons? 
[ATTACH]224201[/ATTACH]

---

### Post by marinara on 2012-09-16
please allow me to point out that you have mistagged this post lubuntu

---

### Post by afulldeck on 2012-09-16
Bump. Anyone?

---

### Post by irv on 2012-09-16
If you add a Network icon to the panel it will have a list of wireless connection available. 
[ATTACH]224229[/ATTACH]

---

### Post by afulldeck on 2012-09-16
> **irv said:**
> If you add a Network icon to the panel it will have a list of wireless connection available. 
[ATTACH]224229[/ATTACH]

Perfect. That is what I am looking for, so just how do I add the network icon to the panel?

---

### Post by afulldeck on 2012-09-16
It appears that I have stumbled into a common problem with this network icon disappearing. Could this be some contention between unity and gnome somehow? After try a couple of thing, this added my network icaon back to the panel by the following: 

sudo apt-get purge network-manager-gnome
sudo apt-get install network-manager-gnome

Now the real question, was that the right thing to do? At the present, I'm not sure why the icon disappeared in the first place (although I've been reading a number of threads that seem to indicate that this isn't an unknown problem). I'm not sure the boundaries between unity and gnome, is there some presentation material somewhere that explains these boundaries? And finally, although this solution worked, was that the correct approach?

---

### Post by irv on 2012-09-16
> **afulldeck said:**
> It appears that I have stumbled into a common problem with this network icon disappearing. Could this be some contention between unity and gnome somehow? After try a couple of thing, this added my network icaon back to the panel by the following: 

sudo apt-get purge network-manager-gnome
sudo apt-get install network-manager-gnome

Now the real question, was that the right thing to do? At the present, I'm not sure why the icon disappeared in the first place (although I've been reading a number of threads that seem to indicate that this isn't an unknown problem). I'm not sure the boundaries between unity and gnome, is there some presentation material somewhere that explains these boundaries? And finally, although this solution worked, was that the correct approach?
Yes, all you did was remove the network-manager and reinstalled it. Have you been switching between desktops? Like Gnome and Unity? The reason I asked is because I have never lost my network-manager-gnome icon, but I have never switch desktops. I just like Unity and will keep using it.

---

### Post by afulldeck on 2012-09-16
> **irv said:**
> Yes, all you did was remove the network-manager and reinstalled it. Have you been switching between desktops? Like Gnome and Unity? The reason I asked is because I have never lost my network-manager-gnome icon, but I have never switch desktops. I just like Unity and will keep using it.

Switching no, not at all. Just using vanilla ubuntu only changes what that I downloaded Advance Settings. Was trying to figure out what it was all about.  I realized I was removing and reinstalling the network manager, but the real question is why would it stop in the first place. More over, why loose it in the drop down panel, but the network is still working. Very odd behavior from my perspective.

---

