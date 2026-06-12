---
title: "Newb need Help with Display drivers"
date: 2010-03-09
forum: Multimedia Software
---

### Post by ho0ola on 2010-03-09
Hey yall,
     I just got ubuntu working yesterday and am very excited to learn how to use it better. But for now, i am an official noooooob. So, I guess my problem is that i Downloaded Geforce 4 MX drivers (linux ones) from nVidias website. I copied them onto a flash, stuck that flash in my ubuntu OS PC, and copied the file to desktop. When i click on the file it seems to only be a text file, Which i cannot open in gedit b/c gedit cannot read the coding. 
I am confused... There is no .exe setup file like windows i can click?? 
        Also, ive read everywhere about editing all these commands in terminal. I found terminal, but why is Linux setup this way? Dos is ancient and Linux seems to be using nothing but a modern version of it. Not bashing at all, by im having major problems... I guess i just need to adjust to the new OS!

---

### Post by Grenage on 2010-03-09
It's likely that it's a script which needs to be made executable before being run:

```
chmod +x blablafile
```

However, I am reasonably sure that the drivers will be included in the OS, if you click on:

System, Administration, Hardware Drivers

Do you not get any listed?

---

### Post by ho0ola on 2010-03-09
Hey thanks for the reply mate
      And no, i dont get anything listed when in hardware drivers. I did when i first had ubuntu just running from a live CD, but now that i have it fully installed, nothing is listed.. My sound also doesnt work which is strange... Anyway, I will try editing that command. Do i just type it into terminal???

Peace and love

---

### Post by Grenage on 2010-03-09
Indeed you do; were there no notes on the download site?

It's possible that the drivers are available on the CD, if it worked from the live option.  Insert the CD then:

System, Administration, Software Sources.

Tick the box for the CDROM/DVD (at the bottom), then close the window.  It it doesn't download a package list automatically, run this from the command line:

```
sudo apt-get update
```

Then check Hardware Drivers.

---

### Post by ho0ola on 2010-03-09
Okay, I just downloaded a free pocoket guide to using linux. Hopefully it will help me understand this whole deal. 
     I tried inserting CD, and doing what you said, but it seems like i need to be connected to the internet to get any drivers to install. My PC with Ubuntu does not have internet quite yet, maybe sometime this week. When i typed : sudo apt-get update into terminal, i recieve an error simply smmarizing that a series of updates couldnt be installed because some Http:// couldnt be found. (not hooked up to internet) 

I guess for now ill just wait until I am on the internet before i try to do this. 


- When entered: chmod +x blablafile into terminal i get message :

chmod:cannot access blablafile:no such file or directory

This is confusing man!!!!#-o

---

### Post by Grenage on 2010-03-09
Ah :)

You'll want to replace blablah with the name of your actual file.

---

### Post by ho0ola on 2010-03-09
haha Oh the things im learning :) dont i feel silly!!

So actually i got into the nvidia display install by tinkering in terminal.

I copied the actual Geforce 4 MX linux driver file and pasted it into terminal. 

I may have added the chmmod +x blabla or something before or after the pasted command. but once i got into installer, it said something about needing to be in root.
I figured that meant my root account so i am gunna try to install it again, with your updated instructions in my root account. Thanks so much your a HUGE help!! how do you know all this?? haha

---

### Post by ho0ola on 2010-03-09
Damn that command you gave simply doesn't seem to do anything.. It just creates a clone of itself on another line... 

How do i run as root? what does that mean?

error: nvidia installer must be run as root


sorry to be such a noob haha

---

### Post by Chris Musampa on 2010-03-09
sudo ./yourexecutablefilenamehere

It means 'superuser do'.

---

### Post by Grenage on 2010-03-09
Bigo.  You cannot log into Ubuntu as root (by default); a new user could do real damage by accident.  Prefix commands that need root access with *sudo*, then it will ask you to enter your password.

---

### Post by ho0ola on 2010-03-09
Okay, you guys have been so great and i really appreciate it :)

But.. Now that i ran command with sudo i get into nvidia installer and am told i am running an X server and need to exit X server before installing drivers... HOLY MOLY! what a process.....


What do i do??? haha

---

### Post by Grenage on 2010-03-09
Ctrl+Alt+F1 and log in.

Then:

```
sudo killall gdm
```

Then run your file and reboot (I can't recall the command to start GDM at this moment.

---

### Post by tcchris on 2010-03-09
I don't think you need to do all of this .
Installing video drivers from internet can be difficult for someone new .
First of all , if you do nothing , you will be using opensource nv driver .
If you want nvidia driver , go to synaptic and do quick search for "modalias"
These are the files that list what card goes to what driver .
Install the 96 modalias , then your driver should show up in 
system > administration > hardware drivers .
you can install it from there

---

### Post by ho0ola on 2010-03-09
Sorry Genage, your comment yielded another dead end. I did what you said but after pressing ctr alt f1, logging in, and typing "sudo killall gdm" i receive the message : No application found or something parallel to that.

And I would be downloading drivers from the internet tcchris, but my ubuntu PC doesnt have internet access until later this week. I am simply trying to install NVIDIA-linux-x86-96.43.16-pkg1.run (for geforce 4 mx)
I also tried what you suggested with the 96 modalias. It tells me that its already installed and is the default

My onboard chipset is an nforce2, but integrated within it is a separate GPU Geforce 4 MX display. The Geforce 4 mx is what i am trying to install... Although NONE of my my sound works either, making me think maybe i need the nforce2 drivers also.....

I feel like i am so close, because i get to the Nvidia install page, but i receive the message telling me i need to close my X server before i install. 

ANY ideas???????

---

### Post by tcchris on 2010-03-09
I think you can hold down the shift key during boot , to get to grub menu .
From there you can get to a command prompt without gdm or x running .
then run your driver package from there

---

### Post by ho0ola on 2010-03-09
Okay, i got to grub menu, but i have no idea how to run the driver (which is on my desktop) from here.... I am sorry I have really no clue what i am doing. So, its tough for me to even know how to install drivers from the desktop, let alone in a black command promt...

I REALLY appreciate you help but maybe we should just give up... unless you can tell me how to run my driver (located on destop) from this post grub commant promt...

---

### Post by ho0ola on 2010-03-09
Problem Solved!!!!:D

Running Linux ubuntu 9.10 w/ Gnome. Trying to manually install GeForce4 MX integrated graphics drivers. No Internet.


Here are the successful steps I used to Install Geforce 4 MX chipset Driver:

In gnome - press ctrl+alt+f1 

- login

- type : sudo service gdm stop (to turn off X server) or default display

- then type : sudo bash

- then : cd ~/Desktop  (I saved my driver to Desktop, yours may be different)

- then : '. /your file name exactly how it appears.. Note* no spaces btwn `. /


Exact commands to type:

sudo service gdm stop

sudo bash

cd ~/desktop 
( this just allows computer to be looking for driver in the right spot, mine was on desktop)

'. /NVIDIA-Linux-x86-96.43.16-pkg1.run' Or whatever driver u are manually tying to install.

Note: the ' and the ' are VERY important!! make sure to include both ' and ' at beginning and end like i did above.

I hope this helps any confused people who happen to come across this problem i did!!

---

### Post by Grenage on 2010-03-10
Glad you got it working; I'm not sure why the apostrophe was required though!

---

### Post by tcchris on 2010-03-10
I am very impressed , many people have stumbled trying to install display drivers .
Congrats

---

### Post by ho0ola on 2010-03-10
YEAH! Thanks guys! I was stoked when it finally ran the installer. I dunno how i figured it out but i remembered reading somewhere that the '  was required in some cases... so i figured id try it, and it worked.. It may work to w/o the apostrophe, but im not gunna go back and try to reinstall it :)

Thanks for the help and props ;)

---

