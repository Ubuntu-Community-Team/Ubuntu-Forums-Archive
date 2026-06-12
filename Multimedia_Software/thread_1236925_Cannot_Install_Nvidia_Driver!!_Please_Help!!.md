---
title: "Cannot Install Nvidia Driver!! Please Help!!"
date: 2009-08-10
forum: Multimedia Software
---

### Post by AirbusFreak on 2009-08-10
HI, 

i have recently installed ubuntu 8.04 and have done the whole of the 384mb updates. 
I have a 8500 GT. i went to **System > Administration > Hardware...**  and i selected the Driver in the list. But is that all i need to do?

I went to nvidia and downlaoded the latest linux driver and saved it to my desktop.

I then followed the intructions from the nvidia site to go to the terminal and type
```
sudo sh nvidia 185.18.18
```
those arn't the correct numbers, i cant remember. HAHA. it then said 
```
cannot install nvidia 185.18.18
```

I then go root privelages with
```
sudo su
```

And still got the same error. 

i went to my desktop and opened the driver pkg1.run file and run it in terminal and i said i needed roo privelages again.

I dont know what to do!

Please Help!!

---

### Post by overdrank on 2009-08-10
Hi and you can use the ctrl, alt, F1 keys to reach the command line and login.
Then you will need to stop x
```
sudo /etc/init.d/gdm stop
```
Then cd ( changed directory ) to the location of the driver, which is usually the desktop.
```
 cd ~/Desktop
```
Then you can run the nvidia driver
```
sudo sh NVIDIA-Linux-x86-185.18.31.pkg1.run
``` Replace with your driver name.
The when complete reboot
```
sudo reboot
```
You may also receive a error for the installation of build-essential

---

### Post by AirbusFreak on 2009-08-11
Hi thatnks for the reply!

i did everything you said, but when i type the sh nvidia command i still get the same "cant open" error

if i have got compiz fusion and desktop effects going, does that meen it is installed? i just installed the one from SYSTEM > ADMINISTRATION > HARDWARE DRIVERS.

is that all? do i even need the NVIDIA one? because i really want the nvidia control panel, to set up dual monitor.

---

### Post by roharme on 2009-08-11
This shouldwork and worked for me.
 
go to nvidia website and download the driver.
 
You will get a .run file
 
now go to level using telinit command and execute the rile using
 
**sh <filename>.sh**
 
It will take u to a blue/black screen, there u wil get an error. 
 
*Unable to install. You want ubuntu to compile one for you??*
 
Give ok and proceed and you are done

---

### Post by AirbusFreak on 2009-08-11
I still get the same error. can you please give me full commands that i can c & p. just in case i am doing it wrong i downloaded NVIDIA-Linux-x86-185.18.31-pkg1.run

from the site

---

### Post by roharme on 2009-08-11
> **AirbusFreak said:**
> I still get the same error. can you please give me full commands that i can c & p. just in case i am doing it wrong i downloaded NVIDIA-Linux-x86-185.18.31-pkg1.run
 
from the site
 
 
you downloaded the correct filei it seems.
**Go to level 1(did u do this??)** and and install using
 
sh filename.run

---

### Post by dark_phantom on 2009-08-11
Does the file has permission to execute?

---

### Post by roharme on 2009-08-11
what error u get actually

---

### Post by Arup on 2009-08-11
Download the package with run2 suffix. Make sure to install build-essentials, then do a sudo apt-get --purge remove nvidia* linux restricted modules log out of X by doing a ctrl+alt+F1 and then login, do a sudo /etc/init.d/gdm stop and finally do a sudo .sh NVIDIA xxxxxxxxxxxxx

Select yes to all options and when done do a sudo reboot, you will have running nvidia drivers. Have been installing these since SuSE 8 days and they have never failed me.

---

### Post by AirbusFreak on 2009-08-11
ok. heres what happend. i installed build essentials and opened the nvidia x settings and i get a message saying that the driver is not in use. i then go to **System > Administration > Hardware Drivers** and indeed it is not in use. i will see what i can do after school 

HAHAH

thanks for your help. all of you. if it does not work i will let you know

---

### Post by Vakman on 2009-08-11
Follow this [HowTo]("http://ubuntuforums.org/showthread.php?t=1125400"). Should work quite well, just make sure you enter everything correctly. All the steps are in there.

---

### Post by AirbusFreak on 2009-08-13
ok, when i open x settings i get the "driver not in use" error, i then go to **System > Administration > Hardware Drivers** and enable it (nvidia x acceleration driver) then restart, like it says. the first boot it ran in low graphics mode and all was black, the second boot... the login was all fuzzy and blured and there was 4 mouses that i could see all fuzzy. my problem is still not fixed.

ARRRRRGGGH

---

### Post by realzippy on 2009-08-13
Keep cool...
please post your xorg.conf file.It's in /etc/X11/[COLOR="SeaGreen"]xorg.conf[/COLOR]

please post the output of
[B]
glxinfo |grep vendor[/B]

---

### Post by kastanedowski on 2009-08-19
I have a bad quality sound with NVIDIA 6100, graphics seems to work normal (version 180), should I need to install anything??

I am new in UBUNTU so basically I follow what I found in the forums with no success, tried re-installing NVIDIA, ALSA, even UBUNTU again and nothing:-({|= (since May)

I use the same computer with windows and the difference in sound quality is amazing, any suggestion?

has anyone seen any_ "beginers procedure somewhere?_

This is the detail of the computer: 
2.26.1 (Ubuntu 2009-05-06)  Release 5
2.6.28-15-generic (#48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009)

Linux
GGC  4.3.3 (i486-linux-gnu)
xorg version   unknown (09 April 2009  02:10:02AM)

AMD Athlon(tm) 64 Processor 3500+

GeForce 6100
NVIDIA UNIX x86 Kernel Module  185.18.14  Wed May 27 02:23:13 PDT 2009



Thanks

---

