---
title: "VirtualBox Video Problems??"
date: 2009-03-07
forum: Multimedia Software
---

### Post by BC_Kush420 on 2009-03-07
I downloaded virtual Box and make a Virtual Machine with windows XP on it but when i finished the install there is no Video Drivers installed windows XP usually automatically installs these drivers becuz i had XP on this laptop before anyways im on a IBM Thinkpad R52 so i went to the official website and downloaded the drivers and still nothing??

ontop of all that when i go to Oen up Driver Detective after a fresh install it POPs up The Application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem. So i re-installed it and nothing

ineed a solution to either one of these problems or both plz and thx :P

---

### Post by ymo on 2009-03-07
Installing XP in a virtual machine is not the same as installing it on the native hardware - the drivers you need come with Virtualbox as it is not emulating an IBM/Dell/HP/brandX PC.

In the virtualbox menu select Devices->Install Guest Additions

---

### Post by BC_Kush420 on 2009-03-07
there is so section called Devices on VirtualBox OSE?? only General/Hard Disks/CD/DVD-RomDrive/Floppy/Audio/Network/Serial Ports/Shared Folders

theres no devices anywhere?? so how do i install guest editions??


do i have a bad version of virtual box?? is there another one?

---

### Post by ymo on 2009-03-07
I have only used VirtualBox (non-OSE) on WinXP to run Linux, Solaris and Win7 guests but from a quick read of the VirtulBox manual there should be no difference to your running Win guest on Linux host. 

Read chapter 4 of the VirtualBox manual (at [http://download.virtualbox.org/virtualbox/2.1.4/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.1.4/UserManual.pdf) if you don't already have it) for information on installing the guest additions.

---

### Post by wolfen69 on 2009-03-07
open virtualbox, but do not start xp. then go to settings and look for where you can allocate video memory for xp. give it more memory. you do not need to install drivers for any os in virtualbox.

i was actually running 3D games in vbox using xp. i did not need video drivers.

---

### Post by BC_Kush420 on 2009-03-09
Alright i added the videa card Space maxed it out but it still doesnt work when i open Windows XP and i goto the Device manager theres 2 Unknown Devices and one of thems a VGA display Device i've tried everything i installed DirectX i installed the proper Drivers i tried right clicking on it and going Update Driver but NOTHING?

howcome i cant get any games to Work on Xp??

im trying to get Diablo 2 to work and it will Install but as soon as i run the Video Test it said Diablo 2 Cannot Run on this Computer

if anyone could help me out that would be great thanx

---

### Post by wolfen69 on 2009-03-09
did you enable 3D in the (virtualbox) settings? also, did you install the OSE or PUEL version of virtualbox?

---

### Post by BC_Kush420 on 2009-03-10
I have version OSE and i dont think i did Enable 3D where is the 3D option?
I looked allover the place couldnt find it

---

### Post by BC_Kush420 on 2009-03-10
is PUEL a better version should i jus get that one?? cuz i really Need to play this game on XP it doesnt run the same on ubuntu and some of the programs for the game dont work on Ubuntu so ineed help back thnx

---

### Post by BC_Kush420 on 2009-03-13
any more suggestions???

---

### Post by inobe on 2009-03-13
start up xp or whatever guest you have

pull out your mouse point and click Devices->Install Guest Additions

a prompt dialog to install the quest additions should come up in xp.

if you have virtualbox 2xx and higher' you should see in settings "enable 3d" when the guest os is shutdown, make sure that is enabled after you install guest additions.

image [http://images.maketecheasier.com/2008/12/virtualbox-3d-acceleration.jpg](http://images.maketecheasier.com/2008/12/virtualbox-3d-acceleration.jpg)


example image of guest additions

edit: [http://www.dedoimedo.com/images/computers/2008/virtualbox-install-guest-additions.jpg](http://www.dedoimedo.com/images/computers/2008/virtualbox-install-guest-additions.jpg)

---

