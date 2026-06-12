---
title: "wifi card install"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by fire 4242 on 2010-05-17
just installed ubuntu on a HP touchsmart tx2-1275dx with a broadcom wifi card, i can not get it to install and when i use the hardware drivers window i get the error message "Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb File not found"

---

### Post by fire 4242 on 2010-05-17
i almost had the wifi driver installed but just as it was installing my system shut down to prevent overheating and not i have a system error:install archives() failed. is there any way i can remove this archive to install the driver?

---

### Post by NUboon2Age on 2010-05-17
> **fire 4242 said:**
> just installed ubuntu on a HP touchsmart tx2-1275dx with a broadcom wifi card, i can not get it to install and when i use the hardware drivers window i get the error message "Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb File not found"

If by "hardware drivers window" you mean Jockey, which is accessed by System->Administration->Hardware Drivers I'm guessing that if you run it again with your install disk inserted, it will fetch the file properly.

---

### Post by fire 4242 on 2010-05-17
i have now gotten rid of that error message and am now getting a system error:install archives () failed message and i did not use a install disk, i did a direct download and install

---

### Post by NUboon2Age on 2010-05-17
> **fire 4242 said:**
> i almost had the wifi driver installed but just as it was installing my system shut down to prevent overheating and not i have a system error:install archives() failed. is there any way i can remove this archive to install the driver?

Its possible that Synaptic Package Manager will repair that package.  If you start System->Administration->Synaptic Package Manager

It will ask for your root password, then

Choose Edit > Fix Broken Packages from the menu.
Choose Apply Marked Changes from the Edit menu or press Ctrl + P.
Confirm the summary of changes and click Apply. 

Try this and let us know what happens.

---

### Post by fire 4242 on 2010-05-17
it is telling me that i have no broken packages. or would it be better for me to uninstall ubuntu and try to install the driver like i did the first time?

---

### Post by NUboon2Age on 2010-05-17
> **fire 4242 said:**
> it is telling me that i have no broken packages. or would it be better for me to uninstall ubuntu and try to install the driver like i did the first time?

Okay, I think I ran into an error message like that recently and I was thinking that's how I fixed it, but let me think about it some more and maybe I'll recall...

---

### Post by NUboon2Age on 2010-05-17
> **fire 4242 said:**
> it is telling me that i have no broken packages. or would it be better for me to uninstall ubuntu and try to install the driver like i did the first time?

So if I'm understanding it correctly, you're able to connect via ethernet to the internet, right? 

This bug looks similar
[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/468309](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/468309)

Try (re)installing the driver through Synaptics (search "B43" brought up B43-fwcutter_012-1_i386.deb).  Mark it to reinstall and then click "Apply".

---

### Post by rastaman06 on 2010-05-17
Hi,

I have exactly the same error when i want to install the driver for my wireless Broadcom card from the "Hardware drivers" item of System > Administration panel. I don't have Ethernet connection available and iIt's frustrating because right now i wrote you this message from the same Ubuntu x64 10.04 distrib but booted from the Live CD, where the driver install (is activated) fine. Is there any fix for this ? Could you point me to the other install method ? I will google for it but should i also open a launchpad bug ? it could affect other users ? Also i was wondering if the automount of the could be the problem but i have neglected Linux so much time that i'm not sure (i try actually to switch back from OS X to Linux (with the elementary theme) :-) ). Best regards and thanks in advance for any help/tip/pointer!

---

### Post by rastaman06 on 2010-05-17
Well, forget my last message, i just read about this in the web, and this problem is not fixed since a lot of time  (at least september 2009 and even before). I will fix my install like the others technical enough to do it, but i will not yet go back to Linux/Ubuntu as a main operating system. It's already 2 days i'm stuck with my computer (Dell Studio 1557) and i must say that i have spent less time to have an operational system with Snow Leopard than with Ubunutu 10.04. I think it's still not yet ready for wide use, it's a shame that a so common chipset isn't supported out of the box, it's not new.Good luck,

---

### Post by fire 4242 on 2010-05-18
i did reinstall ubuntu and i was able to get the wifi up and running, by going to system>administration>hardware drivers and installing the "software modem" driver first than the "broadcom STA driver" second and that got the wifi running, hope this may help you. and thanks for all the help everyone

---

### Post by ptaramelli on 2010-10-18
> **rastaman06 said:**
> Well, forget my last message, i just read about this in the web, and this problem is not fixed since a lot of time  (at least september 2009 and even before). I will fix my install like the others technical enough to do it, but i will not yet go back to Linux/Ubuntu as a main operating system. It's already 2 days i'm stuck with my computer (Dell Studio 1557) and i must say that i have spent less time to have an operational system with Snow Leopard than with Ubunutu 10.04. I think it's still not yet ready for wide use, it's a shame that a so common chipset isn't supported out of the box, it's not new.Good luck,

Don't give up, I have the same problem, but only now, I Installed many times Ubuntu 10.10 because I was stuck in a triple boot (the ubuntu install dammage windows but no osx unless I installed and run gptsync), the previous installs of Ubuntu didn't give me any problems with the wireless, even more, I have before 2 drivers to choose, not now.
But I agree linux is not yet for wide use, a normal user should not have to use the terminal, not once, osx users have a terminal too, but most of them don;t even know it.

---

