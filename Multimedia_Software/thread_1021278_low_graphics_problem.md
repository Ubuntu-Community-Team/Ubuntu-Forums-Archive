---
title: "low graphics problem"
date: 2008-12-25
forum: Multimedia Software
---

### Post by jesse c on 2008-12-25
after 2 months of forum search with no solution,today i went to system/hardware driver and it actually recognized my nvidia driver being available for the first time.Up till today it always said 'no propriatary drivers available'.I thought finally somehow it fixed itself ,so i clicked on search for available driver and then activate the recommended 177 driver that was available then it tells me to restart ,so i reboot and it still boots with the "starting in low graphics mode" window pop up.I check the hardware driver section again and it now says "a propriatary driver is in use on this system" but when i check into my "desktop appearance"settings it wont allow anything but low grphics mode to be enabled also nvidia x server section says x server needs restarting but doesnt respond to 'sudo nvidia-reconfig' command .I feel like im one baby step closer to getting nvidia working but just at a new impass.Any suggestions?

---

### Post by overdrank on 2008-12-25
What model is the nvidia graphics, version of Ubuntu ( Hardy 8.04, Intrepid 8.10)?
Have you tried booting into recovery mode and use the xfix option?

---

### Post by jesse c on 2008-12-25
Sorry overdrank,this is a new nvidia 9400gt graphics card that im trying to get working on Intrepid after my update/upgrade from Hardy,but i had lots of problems when i upgraded from Gutsy to Hardy using the on-board nvidia 6150le chip and dont really know how i eventually (months) got that working,I cant believe how many hours-maybe hundreds really- ive spent on this same issue since my first Feisty experience.I have learned a lot since this is my first computer with all the issues ive delt with in the last few years but if i cant solve this soon im spending my xmas $ on a mac, im sorry to say,since i really like Ubuntu when its up and running but enough is enough at some point.I should have left well enough alone with Hardy but i just figured canonical(?) had a path worth following.Explain this recovety mode thing and ill give it a shot

---

### Post by overdrank on 2008-12-25
Hi and I believe I heard that with that nvidia 9400 you will have to use the nvidia drivers from their site.

 Recovery mode is usually the second choice from the grub while booting. Then you should be given 4 choices one of which is xfix, then after that is complete you should see the 4 choices again and boot normally.

Yes I would suggest sticking with Hardy as it is LTS which is for 3 yrs. You can choose to upgrade each release but if you have a working system that fits your needs then stick with it.

---

### Post by jesse c on 2008-12-25
Thanks for reply overdrank.At some point in the last few months i went to nvidia web and downloaded driver but once it was on my desktop i didnt know what to do to install it.Another forum suggestion was to temporarily load Jaunty repos and get latest driver there which i did and even though it was now in my intrepid repos and checked green my system still said 'no propriatary drivers in use'.I did notice today when my device driver manager finally recognized nvidia and rcommended to enable the 177 driver,which i did,the 180 driver from Jaunty is no longer available in my Intrepid synaptic list

---

### Post by jesse c on 2008-12-25
I did the x fix thing in recovery mode but still no x driver to config

---

### Post by overdrank on 2008-12-25
> **jesse c said:**
> I did the x fix thing in recovery mode but still no x driver to config

if you would like to try and install the nvidia driver you can download it, then you can use the keys alt, ctrl, F1 keys at the same time and this will bring you to the command prompt and login.
The use this command to stop X
```
sudo /etc/init.d/gdm stop
```
Then change to the directory that you downloaded the driver to
```
cd ~/Desktop
```
Then you can use the command to install the nvidia drivers 
```
sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run
``` Replace "86-173.14.09-pkg1" with the correct file name.
Then follow the direction to install the driver that nvidia gives.
Then you should reboot 
```
sudo reboot
```
If all works as plan then you should have the new driver installed.

---

### Post by jesse c on 2008-12-25
I reloaded nvidia driver from web and followed your tutorial and at the end it says 'cant open NVIDIA driver' also on web site it says type sudo sh and driver and that has same 'cant open' results.Also if i try to open file on desktop using default archive manager it says file type not supported but i dont have a clue as to how to do anything file wise on linux (or windows for that matter)

---

### Post by overdrank on 2008-12-25
> **jesse c said:**
> I reloaded nvidia driver from web and followed your tutorial and at the end it says 'cant open NVIDIA driver' also on web site it says type sudo sh and driver and that has same 'cant open' results.Also if i try to open file on desktop using default archive manager it says file type not supported but i dont have a clue as to how to do anything file wise on linux (or windows for that matter)

Ok did you change directory to where the file is locate cd ~/Desktop?
As you can see I gave you the sudo sh command with the file name. You may wan to print those direction with the file also.
Did you download the correct driver for your graphics card and OS, like 32 bit or 64 bit if you use it.

Edit also I have moved your thread to Multimedia & Video as I will be sleeping here soon before work. Hopefully someone else can jump in if I am unable to answer. :)

---

### Post by jesse c on 2008-12-25
yes i followed your instructions step by step using another computer side by side so that i would get all the spaces and capitals right.The last step before the sudo sh file name ( cd ~/Desktop)changed things to $~/Desktop .does that seem right? I dont know what i was supposed to see so i dont know if everything was correct but i followed your instructions to the letter and used nvidias download file name for the last entry(NVIDIA-Linux-x86-180.17-pkg1.run)

---

### Post by overdrank on 2008-12-25
> **jesse c said:**
> yes i followed your instructions step by step using another computer side by side so that i would get all the spaces and capitals right.The last step before the sudo sh file name ( cd ~/Desktop)changed things to $~/Desktop .does that seem right? I dont know what i was supposed to see so i dont know if everything was correct but i followed your instructions to the letter and used nvidias download file name for the last entry(NVIDIA-Linux-x86-180.17-pkg1.run)

Ok if you can give the exact error please.
You may also need to install ```
sudo apt-get install build-essential 
``` to help with the installation.
I have not see that error cant open file before.

---

### Post by jesse c on 2008-12-25
Im no longer in the terminal to read the exact error file and would have to start all over again,and i've (we've)been at this seven hours now just today and im a little burned out for now but i sure do appreciate your help but tell me what step i would put in that last command you suggested and ill try again some other time

---

### Post by jesse c on 2008-12-25
Well i got the file to install with another try of your tutorial and build essential said its the latest one.Nvidia install did its thing in terminal and i rebooted and no change and driver manager still has just the 177 driver enabled with no mention of 180 installed and now there is no 'xserver config' even listed on my system/admin. page

---

