---
title: "Issue with NVIDIA proprietary drivers"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ShamusPatt on 2010-09-10
Just wanted to report what seems to be an issue with the NVidia proprietary drivers on an upgrade from Lucid Lynx. 

The upgrade seemed to go smoothly but when I rebooted into Maverick, after a long delay I was dropped into a console; X failed to start. I can see from the logs that it's having trouble loading the nvidia drivers:
[INDENT]
[FONT="Trebuchet MS"]Xorg.5.log:[    22.857] (II) LoadModule: "nvidia"
Xorg.5.log:[    22.857] (WW) Warning, couldn't open module nvidia
Xorg.5.log:[    22.857] (II) UnloadModule: "nvidia"
Xorg.5.log:[    22.857] (EE) Failed to load module "nvidia" (module does not exist, 0)[/FONT][/INDENT]

(I think the module was actually there - it must have been a dependency causing it to fail).

I managed to get it resolved as follows:

[LIST]
[*]Remove the NVidia drivers (not sure this was necessary).
 "apt-get remove nvidia-173"

[*]Reboot into a (recovery) session
[*]Start with Safe Graphics
[*]Create a new Clean Configuration
[*]Reboot again into graphics mode (with the clean configuration)
[*]Use Administer / Additional Drivers to reactivate the NVidia proprietary drivers
[*]Reboot again to run with the updated NVidia configuration
[/LIST]

All seems fine now - things are much as they were with Lynx. No doubt there are lots of new goodies for me to discover yet :D

If it's of interest, this system is an AMD-64 system with a GeForce 7300 LE graphics card.

---

### Post by ktp on 2010-09-10
thanks for posting..lots of people been having this issue.  similar fix can also be done if someone has ati and it get stuck after upgrade.

---

### Post by ShamusPatt on 2010-09-10
> **ktp said:**
> thanks for posting..lots of people been having this issue.  similar fix can also be done if someone has ati and it get stuck after upgrade.

I'm glad it's helpful. I searched the forum but didn't see much that indicated an X failure like I was seeing.

If it's affecting ATI users as well as NVIDIA, then it seems to be a bit more widespread than I'd assumed - perhaps any video that is using the proprietary drivers.

---

### Post by ktp on 2010-09-10
it more about x upgrade and drivers weren't supporting it yet.  Latest nvidia proprietary drivers works now.

---

### Post by proggy on 2010-09-11
I wished i had heard about that earlier i lost a couple of hours for nothing

---

### Post by al090187 on 2010-09-12
Hi, I am having this same problem now with an ATI card.

Yesterday it stopped on the pink screen with the dots showing the loading process, and wouldn't move. Today I get dropped to the console like the OP. Unfortunately I do not know how to check the logs to prove that X failed to start, and, as for removing the drivers, I do not know the package name to do that.

Any suggestions?

---

### Post by zenarcher on 2010-09-12
I had a similar problem with Nvidia drivers awhile back and took a similar approach to remedy the situation.

I booted up with an earlier kernel, then from Additional Hardware, removed the Nvidia driver.....rebooted to the newest kernel and reinstalled the Nvidia driver from Additional Hardware.  Following a fresh boot, everything worked fine again.  Seems to have been resolved with the latest Nvidia driver, however.

Regards,
zenarcher

---

### Post by ktp on 2010-09-12
> **al090187 said:**
> Hi, I am having this same problem now with an ATI card.

Yesterday it stopped on the pink screen with the dots showing the loading process, and wouldn't move. Today I get dropped to the console like the OP. Unfortunately I do not know how to check the logs to prove that X failed to start, and, as for removing the drivers, I do not know the package name to do that.

Any suggestions?

following should remove the ati and the xorg.conf if exists.
> sudo apt-get purge fglrx
sudo rm /etc/X11/xorg.conf

This thread would be good reference also:
[http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872)

---

### Post by MonsterTrimble on 2010-09-13
Just as a heads up the parent post did NOT work for me. I had the same issue after following the directions. 

I have a Gateway m500 laptop with a nvidia Go4 400 graphics chip. 

Unless someone can tell me how to force nouveau to have my screen 1024 x 784 with 59.0 Hz?

---

