---
title: "Wireless doesn't resume after suspend / hibernate"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by venutip on 2009-03-07
Hi,

Whenever I resume from suspend or hibernate in Intrepid (8.10), my network connection is disabled. Ubuntu recognizes the connection; it knows that it's there; but it's disconnected. Ultimately I have to reboot the machine, which of course defeats the purpose of hibernating.

I recently switched to Ubuntu from Windows. In Windows, I would just right-click the Network icon and select "Repair", or I would run [FONT="Courier New"]ipconfig /release[/FONT] and [FONT="Courier New"]ipconfig /renew[/FONT]. Is there something similar that I can do in Ubuntu? I've looked at every configuration screen I can find and there doesn't seem to be a way to just restart the connection.

Things I've tried:

-- Disabled and then re-enabled wireless using the "Enable Wireless" option in nm-applet
-- Disabled and then re-enabled networking using the "Enable Networking" option in nm-applet
-- Restarted the DNS service (avahi-daemon)

Again, the wireless does work, it just craps out on wake.

System details:

Wireless card: a Hawking device plugged in via USB.
Computer: HP Pavilion tower, running in a Linux/Windows dual-boot setup.
Ubuntu: Intrepid Ibex; system is up to date as of 3 hours ago, according to Update Manager.

Thanks!

---

### Post by danmarycap on 2009-03-11
I have the same problem...wireless is working, I suspend/sleep and on resume, no connection.  Workaround I've been using is:
go to Terminal, type "sudo dhclient"
now wireless works.

But I'm looking through the forum here for a "real" fix.

-Dan

---

### Post by linmalex on 2009-03-11
I have the same problem, and I have tried several things and the dhclient command above was the first thing I've ever gotten to work. However, if there's a way to fix it permanently, I'd like to know as well.

---

### Post by danmarycap on 2009-03-12
Believe I found the fix -- check out my post here: [http://ubuntuforums.org/showthread.php?p=6883391#post6883391](http://ubuntuforums.org/showthread.php?p=6883391#post6883391)

tested it several times last night and it worked repeatedly.  Now I just need to figure out how to get the system to stop asking for a password when I 'resume' all will be good.

-Dan

---

