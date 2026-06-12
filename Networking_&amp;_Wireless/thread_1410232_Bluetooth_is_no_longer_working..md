---
title: "Bluetooth is no longer working."
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by ramymah on 2010-02-18
sup guys,
 i just installed ubuntu 9.10 on my Compaq 610 laptop .. the bluetooth icon is not shown,
i installed "blueman", and whenever i start it it gives me "Bluez daemon is not running, blueman-manager cannot continue."
the bluetooth was working fine on ubuntu 9.10 before and on windows 7 as well. i checked the bios settings but the bluetooth was enabled there, i tried to disable and enable it from the laptop itself, but nothing happened.
i also tried : sudo /etc/init.d/bluetooth (start - stop - restart)
nothing happened.

any other solutions please ?

---

### Post by arm-c on 2010-02-18
I had terrible experience with blueman.

I recommend removing it and installing:
gnome-bluetooth

It does lack some of the supposed functionality of Blueman; however, at least my BT works now for devices, phone synch and audio.  Fails at setting up a BT network though.

---

### Post by ramymah on 2010-02-18
> **arm-c said:**
> I had terrible experience with blueman.

I recommend removing it and installing:
gnome-bluetooth

It does lack some of the supposed functionality of Blueman; however, at least my BT works now for devices, phone synch and audio.  Fails at setting up a BT network though.

thanks for the fast reply, i removed "blueman" and i installed the original "gnome-bluetooth"
but when i open the bluetooth preferences "system-> preferences->bluetooth" it says "you computer doesn't have any bluetooth adapters plugged in" while it was working before ,,

any solutions please ?

---

### Post by ramymah on 2010-02-19
is it that hard ??!!!
nobody answered ?!

---

### Post by robinda1st on 2010-09-20
Okay, quick question are you dual booting your laptop with windows?
I am, and I installed lucid recently everything worked except my bluetooth it seemed that it just didn't install, 
I then realized that I had the bluetooth turned off in my windows installation but wireless enabled, so what I did was boot to my windows install and enabled my bluetooth in the hp connections manager, shut down and restarted into Ubuntu and low and behold my bluetooth worked fine. This seems to be a strange quirk in a lin/win dual boot. Hope this helps.

Having said all that though when doing a complete install of ubuntu on the same laptop on a blank hard drive I didnt have the same problem.


let me know if this helps.

---

