---
title: "windows dual boot"
date: 2010-07-24
forum: Multimedia Software
---

### Post by archeryrob on 2010-07-24
I am trying to get windows on my HTPC. I am using the 10.04 LTS and trying to get XP installed as a dual boot. I want Netflix on this machine and need windows.

It's a new machine so I was going to run windows and wipe it out and dual boot Ubuntu back on it. BUT Ubuntu will not let me start the exe file.

Virtual box files will not run from the software center. Says untrusted applications and quits.  

How can i get this to work

---

### Post by howefield on 2010-07-24
> **archeryrob said:**
> I am trying to get windows on my HTPC. I am using the 10.04 LTS and trying to get XP installed as a dual boot. I want Netflix on this machine and need windows.

With you so far.

> It's a new machine so I was going to run windows and wipe it out and dual boot Ubuntu back on it. BUT Ubuntu will not let me start the exe file.

But completely lost you now.

> Virtual box files will not run from the software center. Says untrusted applications and quits.  

How can i get this to work

Can you try again explaining a little more clearly what you are trying to do and where you are stuck ?

---

### Post by archeryrob on 2010-07-24
VboxGtk
After starting the install Says "Requires Installation of untrusted applicatons" and quits."OK" tkes you out of the install.

This computer was a total build, so no other software is on it. I installed Ubuntu to get it going. I have an XP disk but will not run the .exe files to start it. 

I a also using a AMD athlon X4 processor.

---

### Post by howefield on 2010-07-24
If I have you right, you have a single booting system with Ubuntu and have installed Virtualbox so you can create an XP virtual machine, is that right ?

If so, to start the installation of XP as a virtual machine, create the settings for it in virtual box and then with your XP disk in your CD drive, booting the VM.

This wouldn't be the dual boot that speak of in your original post.

If you want to dual boot, you'd need to create a primary partition on your disk and boot from your XP disk installing to your newly created partition. You'd then lose grub which means Ubuntu wouldn't load, so you would need to reinstall grub.

---

### Post by archeryrob on 2010-07-25
No the virtual box would not install. So i cannot run XP in a virtual machine.

At this point I am ready to wipe the entire drive, install XP and install ubuntu after that and set partitions to be a dual system to get a dual boot.

I but DBAN on a stick, but can't figure to get it to work.

---

### Post by archeryrob on 2010-07-25
I have Ubuntu running only now. I want a dual boot so I can get Windows for Netflix and games.

I can not get the bios to do CD booting right now. I can't figure it out and it keeps reverting to the hard drive and loading ubuntu. AMD Athlon X4 If I could wipe it and get XP on I could easily do thedual boot with the Ubuntu install CD.

But I can't get there from here right now.

---

### Post by archeryrob on 2010-07-25
Bios on the AMD had hard disk boot priority and I can't turn it off. Any way to run the XPCD in ubuntu or wipe the drive without a CD boot?

---

### Post by jerrykenny on 2010-07-25
This is a real problem "Bios on the AMD had hard disk boot priority and I can't turn it off"

You really need to get that bit sorted first of all.


Then wipe yer hard drive, install Windows XP on whatever size of partition you feel it needs, and use the remainder for the subsequent installation of ubuntu.

Windows needs to be on the first primary partition.

---

