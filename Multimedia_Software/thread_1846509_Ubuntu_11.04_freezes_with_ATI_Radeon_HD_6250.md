---
title: "Ubuntu 11.04 freezes with ATI Radeon HD 6250"
date: 2011-09-19
forum: Multimedia Software
---

### Post by hofik on 2011-09-19
Hi there! I've bought an **[SIZE=1]Acer Aspire 15.6" Laptop with AMD C-50 Processor [/SIZE]**

and ATI Radeon HD 6250 graphics. I installed Ubuntu 11.04, 32 bit version. After installation completion and restart it worked. However, next day the system started to freeze at the login screen. It only works, if I start it in the recovery mode - safe graphics mode.... after complete re-installation of Ubuntu the whole scenario repeated. 
Because it works in safe graphics mode, I presume there's an issue with the video driver. 
BTW, I use dual boot (I shrunk the Windows 7 partition to half and I use ext 3 on the other half). The pre-installed Windows 7 works well (if Windows can work well, at all).

I plan to play with it a little bit more tonight.

Anyone with similar experience?

---

### Post by hofik on 2011-09-20
I apologize, freezing is caused by the wireless adapter atheros ar5b95. If that's turned off, it's all working fine. (by the time I turn-on wifi). All working with Windows. :(

---

### Post by jmate24 on 2011-09-21
go to [http://www.amd.com]("http://www.amd.com")
and look for the downloads section there is an 11.8 driver available for linux.

when you get it open up your terminal and:
```
cd /home/yourusernamehere/Downloads
sudo sh ati-driver-installer-11-8-x86.x86_64.run
```
but first make sure you have the driver that comes with ubuntu by going to the Dash Menu> More Apps> 'and type': Additional Drivers> then click it. and then if the light is green then your ati driver is already installed if not then install it by clicking activate and when it is done reboot your PC/Laptop then open terminal and enter this:
```
sudo sh ati-driver-installer-11-8-x86.x86_64.run
```
and do the recommended install.

---

### Post by hofik on 2011-09-26
fyi - bios upgrade resolved the issue with wifi causing freezing

---

### Post by thenewone1 on 2011-10-02
Hi [jmate24]("http://ubuntuforums.org/member.php?u=360031")

I'm new to ubuntu.

I have A  Radeon 1650 Pro and it too freezes on login screen. I need to use the internal grafics on my motherboard to be able to login.

If i follow your steps :
 "Dash Menu> More Apps> 'and type': Additional Drivers> then  click it. and then if the light is green then your ati driver is already  installed"

it wont display the drivers and the light is red ?

The ati drivers i have installed in my pc is 0.9.2-0ubuntu5 (jockey-gtk) I don't know if it is the right one.

Doesn't i need to have my Radeon 1650 Pro installed in the pc to be able to see the green light and the drivers.

I hope it makes sense what wrote :-)

---

