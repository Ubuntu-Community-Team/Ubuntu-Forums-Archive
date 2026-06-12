---
title: "Ubuntu studio problems"
date: 2008-07-06
forum: Multimedia Software
---

### Post by simonlugi on 2008-07-06
I installed UbuntuStudio audio, video and graphics using Synapic and ticking only the these three boxes.
If I allow the boot up to follow the default first line option on the Grub screen I end up with a blank screen. The startup window works alright but when the normal boot up screen turns to an orange screen just before the desktop appears, now it just goes blank.

Can anyone explain what I should do.

Simon

---

### Post by overdrank on 2008-07-06
> **simonlugi said:**
> I installed UbuntuStudio audio, video and graphics using Synapic and ticking only the these three boxes.
If I allow the boot up to follow the default first line option on the Grub screen I end up with a blank screen. The startup window works alright but when the normal boot up screen turns to an orange screen just before the desktop appears, now it just goes blank.

Can anyone explain what I should do.

Simon

Hi and I have never used Studio but if you installed something to do with graphics that would be my first guess. What is the model of the graphics card and what version of Ubuntu are you using?

---

### Post by simonlugi on 2008-07-06
I am using Hardy heron and have Nvidia Graphics card
Simon

---

### Post by overdrank on 2008-07-06
> **simonlugi said:**
> I am using Hardy heron and have Nvidia Graphics card
Simon

Ok you may try to reconfigure your xorg with the command using the ctrl, alt, F1 keys at the same time and this will bring you to the command line and login
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Or boot into recovery mode and use the xfix option.

---

### Post by simonlugi on 2008-07-06
I have tried your suggestions and I have also removed the unbuntustudio files in synamptic.
None of these has worked

---

### Post by overdrank on 2008-07-06
> **simonlugi said:**
> I have tried your suggestions and I have also removed the unbuntustudio files in synamptic.
None of these has worked

:confused: how did you return to synaptic manager and you have no desktop.

---

### Post by simonlugi on 2008-07-07
When the Grub list appears I have about 7 lines that all refer to Ubuntu. I dont know enough about the system and cannot recall what they all are except that some are obviously the safe mode options, others are not. The third line works and boots up to a normal desktop. 

I also have Vista as another option.

---

### Post by overdrank on 2008-07-07
> **simonlugi said:**
> When the Grub list appears I have about 7 lines that all refer to Ubuntu. I dont know enough about the system and cannot recall what they all are except that some are obviously the safe mode options, others are not. The third line works and boots up to a normal desktop. 

I also have Vista as another option.

Ok so you use a older kernel to boot and remove the drivers. What is the model of the nvidia card and did you solve your issue on your first post?

---

### Post by simonlugi on 2008-07-10
If the other lines on the Grub screen are older kernels, then that is correct. As for removing driver. I dont know how how to do this.
Not sure where and how to find what model Nvidia card I have. Can you send instruction how to find out what graphics card. I cannot find any documentation.

---

### Post by overdrank on 2008-07-10
> **simonlugi said:**
> If the other lines on the Grub screen are older kernels, then that is correct. As for removing driver. I dont know how how to do this.
Not sure where and how to find what model Nvidia card I have. Can you send instruction how to find out what graphics card. I cannot find any documentation.

HI and you can use the command ```
lspci
``` in the terminal and look for VGA

---

### Post by simonlugi on 2008-07-11
My graphics card is

nVidia Corporation GeForce 7100 GS (rev a1)

simon

---

### Post by markbuntu on 2008-07-11
You really need to install the entire Ubuntu Studio package for it to work properly.

What is probably happening is that since Ubuntu Studio changes the background of your login screen but you only parlty installed it, it does not have the new background to load so it crashes.

Ubuntu Studio also uses the real time kernel which, if you are doing recording or mixing is an absolute must.

If you want to recover your Ubuntu Studio, reinstall it but this time install the entire package. Your graphics card is most likely not the problem.

---

### Post by simonlugi on 2008-07-12
Thanks
I presume that this requires a seperate partition.

---

### Post by markbuntu on 2008-07-13
No, a separate partition is not necessary. In fact, doing so would probably not solve your current problem.

---

### Post by Spaceman9 on 2008-07-13
I installed everything from Ubuntu Studio from Synaptic. I installed it into an existing install of Ubuntu 8.04 LTS. No problems cept one. Studio will replace the usplash art( that's the screen with the Ubuntu logo and progress bar) the login art the wallpaper the desktop theme for your windows and the log out usplash art with Ubuntu Studio art.

If you'd rather have the Ubuntu art then the Ubuntu Studio art you can install and use StartUp-Manager. After install click System>Administration> StartUp-Manager.

 In Boot Options set Default operating system to Ubuntu 8.04.1, kernel 2.6.24-19-rt. You need to use a rt kernel for Rosegarden and other sound/music composition apps. Under Misc check off Show bootloader menu, Show boot splash, Show text during boot.

Under Appearance>Usplash themes>Usplash theme: you'll see a scroll box. Click on the scroll box and you should see usplash-theme-ubuntu and  ubuntustudio-theme. Clik on usplash-theme-ubuntu then click on the close button. That changes the usplash from Ubuntu Studio art back to Ubuntu art. 

To change the desktop theme back to Ubuntu just right click on your desktop and click on Change Desktop Background. Then just pick out the theme, wallpaper, icons, pointer etc that you want.

---

### Post by Brijamelsh on 2008-07-14
i have this same problem, however to get into ubuntu studio from Grub i have to start the kernel in recovery mode then simply boot normally at the prompt. I think it has something to do with the splash screen sense starting in recovery mode seems to skip the splash screen and works fine. if anyone can back this up or might know of a solution please share.

i am using a fujitsu t4215

---

### Post by simonlugi on 2008-07-19
Spaceman9 Thanks for your advice. Unfortunately I had to throw the towel in on this one. I couldn't find the commands in System>Administration that you were referring to and ended up reinstalling Ubuntu. 
I will probably come back to trying to install Studio again but at the moment its taking up so much time and its not that important.
Thanks Again

---

