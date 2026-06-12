---
title: "Problem with Restricted Drivers"
date: 2009-01-01
forum: Multimedia Software
---

### Post by mc6415 on 2009-01-01
Right, I'm new to ubuntu so go easy on me :D

Basically I finally finished installing ubuntu on my laptop (Acer Aspire 6920G is that helps), and everything works fine, bar the sound, but I've found a nice guide for that.

My problem is that when I go to activate the restricted drivers: 

ATi/AMD proprietary FGLRX graphics driver

It asks for my password which I put in, it then seems to do something, but it always ends up with the driver not being enabled, I have tried rebooting after enabling the driver as well but to no avail.

Hoping someone can help me with this,
Coombes.

---

### Post by overdrank on 2009-01-01
> **mc6415 said:**
> Right, I'm new to ubuntu so go easy on me :D

Basically I finally finished installing ubuntu on my laptop (Acer Aspire 6920G is that helps), and everything works fine, bar the sound, but I've found a nice guide for that.

My problem is that when I go to activate the restricted drivers: 

ATi/AMD proprietary FGLRX graphics driver

It asks for my password which I put in, it then seems to do something, but it always ends up with the driver not being enabled, I have tried rebooting after enabling the driver as well but to no avail.

Hoping someone can help me with this,
Coombes.

Hi and what is the model of the graphics card and version of Ubuntu you are using? Are your repos enabled?
Moved to Multimedia & Video :)

---

### Post by mc6415 on 2009-01-01
> **overdrank said:**
> Hi and what is the model of the graphics card and version of Ubuntu you are using? Are your repos enabled?
Moved to Multimedia & Video :)

Hi there, the card is a ATI Mobility HD3650 512Mb DDR2, and I'm using 8.10 Intrepid, sorry for posting in the wrong section.

---

### Post by wylfing on 2009-01-01
You need to run your first system update before the video drivers will install.
[LIST=1]
[*]Open a terminal by choosing Applications > Accessories > Terminal.
[*]Update your repositories (the password it will ask for is just your own password).
```
sudo apt-get update
```
[*]Run the update.
```
sudo apt-get upgrade
```
[*]Go take a break. It'll probably need to update a lot of stuff.
[*]A little icon will pop up telling you to reboot. Do so.
[*]Now go to System > Administration > Hardware Drivers and try to activate the ATI driver again. You'll find that it does something much more sensible-looking this time.
[*]Reboot again.
[/LIST]

When your computer comes back up an icon should appear that says there are new restricted drivers in use. Enjoy!

---

### Post by overdrank on 2009-01-01
> **mc6415 said:**
> Hi there, the card is a ATI Mobility HD3650 512Mb DDR2, and I'm using 8.10 Intrepid, sorry for posting in the wrong section.

No need to be sorry, just moved to where you maybe better assisted. :D

---

### Post by mc6415 on 2009-01-01
> **wylfing said:**
> You need to run your first system update before the video drivers will install.
[LIST=1]
[*]Open a terminal by choosing Applications > Accessories > Terminal.
[*]Update your repositories (the password it will ask for is just your own password).
```
sudo apt-get update
```
[*]Run the update.
```
sudo apt-get upgrade
```
[*]Go take a break. It'll probably need to update a lot of stuff.
[*]A little icon will pop up telling you to reboot. Do so.
[*]Now go to System > Administration > Hardware Drivers and try to activate the ATI driver again. You'll find that it does something much more sensible-looking this time.
[*]Reboot again.
[/LIST]

When your computer comes back up an icon should appear that says there are new restricted drivers in use. Enjoy!

Ah thank you worked a treat :D

---

### Post by Evagrios on 2009-01-07
I have the same problem, but this does not help. I.e When I click "activate" for the ATI driver, it asks for a password and "downloads" the driver, then nothing happens and the driver remains unactivated.

---

### Post by Evagrios on 2009-01-07
Ok, I got it working by reinstalling ATI catalyst.

[http://ati.amd.com/products/catalyst/index.html](http://ati.amd.com/products/catalyst/index.html)

There is a guide here:

[http://www2.ati.com/drivers/linux/linux_cat812-inst.pdf](http://www2.ati.com/drivers/linux/linux_cat812-inst.pdf)

---

