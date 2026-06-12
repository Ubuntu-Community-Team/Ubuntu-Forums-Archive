---
title: "Nvidia 4400ti Woes..."
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by sunami88 on 2007-11-10
So I got some free computer bits from a friend, and along with some I already had laying around, I made a computer. Problem is I have an Nvidia 4400ti, and I can't even get Gutsy to boot into a graphical environment. It loads etc and looks all fine until the point it would normally go to X... I just get a black screen. Even going into "Safe Graphics Mode" or whatever still doesnt seem to help me.

Here are my computers specs (eventhough its just an issue with graphics card, might as well post it all);

Intel Celeron @ 2.4Ghz (I know, I know, but free is free)
1 Gig of DDR
Nvidia 4400ti, 128 megs of ram
20 Gig Maxtor (again... I know, but free...)

Soooo... yeah, is there any way I can get it to go into X?

EDIT: Even if there is a way for me to tell it not to try and load X, then I could at least "apt-get" the new drivers. But such as it is it just locks up...

UPDATE:  Well I finally got to ctrl+alt+f2 and it didnt lock up, and I am downloading the "nvidia-glx-legacy" drivers... cross your fingers...

---

### Post by carlinuxlearner on 2007-11-10
If that doesn't work you can try "[Envy]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu12_all.deb")".

C@RL

---

### Post by sunami88 on 2007-11-10
Well now it works, but it is a little laggy, and "visual effects" doesnt turn on at all... but anyways I got it using the driver by renaming my xorg.conf...

But now there doesnt seem to be one at all... how can I get it to re-write one?

---

### Post by carlinuxlearner on 2007-11-10
Hum.... what do you mean "But now there doesnt seem to be one at all... how can I get it to re-write one?"
???

C@RL

---

### Post by carlinuxlearner on 2007-11-10
You can try "Envy" here's a guide I wrote.

HOW TO: install your Nvidia driver in Ubuntu 7.10

(Please MAKE SURE with ANY commands (or path names) that you capitalized what I capitalize!!!! This is VERY important!)

I will start by giving you two options. Both options require that you have a internet connection of some kind. (preferably high-speed)

Option #1. Install your Nvidia driver with "Envy" 
(usually MUCH easier then installing the driver the manual way)

OR

Option #2. Install your Nvidia driver manually. (use this if Envy won't work)


If you choose Option #1 "Install your Nvidia driver with "Envy"" Then please proceed from here on.

1.1 
Go to your (System>>Administration>>Software Sources) make sure you have all your repositories enabled. (Check mark them all)

Download "Envy" to your Desktop (to make thing easy) [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb)
(if this link does not work, just visit this web site and download the latest version [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )

1.2
Double click on the file you just downloaded and tell it to install

1.3
If all those steps went well then Envy should be installed and you should be able to find it on your "Applications" menu under "System tools", just run it and you should be able to install your driver all by your self very easily.


Option #2.

2.1
Open up a terminal window (Applications>>Accessories>>Terminal) type this in "sudo apt-get install build-essential"


2.2
In a terminal window type "lspci | grep VGA" find the part that has these around it "[ ]", write down what it says then go here 
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) 
If the name of your graphics card is in the list (such as "Geforce 6800") then download this driver to your Desktop
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run) 
(if that link is old go to this page to get driver) 
[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html) 
(if that link is old, go here and select the driver that starts with "100")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).


(EXAMPLE 

"carl@carlubuntu1:~$ lspci | grep VGA
01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
carl@carlubuntu1:~$"

The "GeForce4 MX 420" is the name you are looking for. So "GeForce4 MX 420" is what I would look for on the list here.
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

end of example)

2.3
IF YOUR GRAPHICS CARD NAME IS NOT ON THAT LIST look and see if it's on this one
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If it was in the "The 1.0-96xx driver supports the following set of GPU" section, then download this driver to your Desktop
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run)
(If that link is old then go here)
[http://www.nvidia.com/object/linux_display_x86_96.43.01.html](http://www.nvidia.com/object/linux_display_x86_96.43.01.html)
(If that link is old go here and select the driver that starts with "96")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

If you graphics card name was in the "The 1.0-71xx driver supports the following set of GPUs" section,
then download this driver to your Desktop.
[http://us.download.nvidia.com/XFree86/Linux-x86/71.86.01/NVIDIA-Linux-x86-71.86.01-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/71.86.01/NVIDIA-Linux-x86-71.86.01-pkg1.run)
(If that link is old go here)
[http://www.nvidia.com/object/linux_display_x86_71.86.01.html](http://www.nvidia.com/object/linux_display_x86_71.86.01.html)
(If that link is old go here and select the driver that starts with "71")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)


2.4
Print out this page!

2.5
Restart your computer! At the Grub boot menu (if it doesn't pop up click ESC before it's to late) and select the "recovery mode" kernel, and hit enter!

2.6
Once booted, type in "sh /home/yourusername/Desktop/NVIDIA" but DON'T HIT ENTER!!
(replace "yourusername" with your user name) 
click the TAB button on your key board twice, and it should fill out the rest of the name for you, 
THEN hit enter.

2.7
The installer will ask you some question (don't worry if it says your in "runlevel 1" it doesn't matter) just make sure you answer all the questions so that it will continue the installation process.

2.8
Once the installer is done restart your computer by pressing CTRL+ALT+DELETE, boot up normally. And your Nvidia driver should be installed!

TROUBLE SHOOTING

If you have problems installing "Envy" ether ask about it on the forums, or just do Option #2.

If (in Option #2) when you reboot you get a black screen don't worry it can be fixed!
Just press these keys ALT+F2 and then type this in at the command prompt "sudo nano -w /etc/X11/xorg.conf"
Find the part of the file that says "Device", find "Driver       "nvidia"" change "nvidia" to "nv".
Press ALT+X and save the file.
Restart your computer, try installing it again, or ask about it on the forums. (When asking on the forums, error messages are VERY helpfull please write down, or copy any you get)

C@RL

---

### Post by sunami88 on 2007-11-10
Well it works now. Desktop Effects turns on etc. but now all it will do is 1280x1024@50hz... which is akward seeing as how I have a 16:9 1440x900 monitor... Do I have to hack xorg to get 1440x900@60hz back?

Thanks again eh guys. I've made lotsa progress here, and Envy worked like a charm.

EDIT: Haha, hacked xorg and now it does 1440x900@60. Issue resolved I guess.

Thank you!!

---

### Post by carlinuxlearner on 2007-11-11
Great! Yeah it's some times hard to get those wide screen resolution going.

C@RL

---

