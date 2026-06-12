---
title: "Cannot activate nvidia driver--computer halts"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by ronin2040 on 2007-11-09
I recently took my gutsy harddrive out of an intel Pentium-D box and put it in an AMD X2 box, bringing my video card with me.  On boot, everything works, except that i cannot enable the nvidia driver.  Any time the nvidia driver is specified in xorg.conf and i restart GDM, the monitor goes black, and the power light blinks on the monitor.  Nothing will revive the computer at this point short of a hard power off.

So far, i have tried both 
apt-get --purge remove nvidia-glx-new
apt-get install nvidia-glx-new

as well as envy (remove, installl).  No luck with either.  I've checked the system logs, but nothing jumps out at me. What do i need to do to get this running?  The NV driver works fine, so surely there is a way to fix this...

---

### Post by carlinuxlearner on 2007-11-09
Have you tried manually installing the driver?
If not then try this:
"2.1
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

When you reboot you get a black screen don't worry it can be fixed!
Just press these keys ALT+F2 and then type this in at the command prompt "sudo nano -w /etc/X11/xorg.conf"
Find the part of the file that says "Device", find "Driver       "nvidia"" change "nvidia" to "nv".
Press ALT+X and save the file.
Restart your computer, try installing it again, or ask about it on the forums. (When asking on the forums, error messages are VERY help full please write down, or copy any you get)


C@RL

---

