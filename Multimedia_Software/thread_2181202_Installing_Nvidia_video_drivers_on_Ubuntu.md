---
title: "Installing Nvidia video drivers on Ubuntu"
date: 2013-10-16
forum: Multimedia Software
---

### Post by doug-ravennasprings on 2013-10-16
WARNING:  Though I successfully got the drivers installed there are serious problems with them.  The scrips that Nvidia provides have bugs in them and 32-bit applications are not supported on 64-but versions of Ubuntu causing massive reduction in performance.  Applications like Steam are impacted.
This thread explains the problem:  [http://steamcommunity.com/app/221410/discussions/5/828939163894026239/#p1](http://steamcommunity.com/app/221410/discussions/5/828939163894026239/#p1)

Background: I was having difficulty installing the Nvidia drivers on Ubuntu 13.10.  I followed the instructions of several posts from various sources and none of them worked.
The Ubuntu Software Center even offers these drivers which rendered my computer useless forcing a complete reinstall.  [Wow!]

   After discussions with Nvidia, these are simplified instructions of getting the drivers installed.  It's really not that bad.

[LIST=1|INDENT=2]
[*]Download the Nvidia driver you're interested in from nvidia.com.  I chose to place them in ~Downloads/drivers/nvidia. 
[*]Keep Ubuntu's Nouveau driver from loading
[LIST=1]
[*]in /etc/modprobe.d directory create as root a new file called "disable-nouveau.conf"  The .conf is important, the rest isn't but should be clear enough. 
[*]edit this file and add the following two lines:  "blacklist nouveau"  & "options nouveay modeset=0" 
[*]save this file. 
[*]reboot 
[/LIST]
  
[*]Update the ramdisk image so the nouveau modules won't be invoked during boot.
[LIST=1|INDENT=2]
[*]In a console type 'ls /boot' and examine it for files that look like this:  ```
initrd.img-3.8.0-32-generic
```   The 3.8.0-32-generic is what designates the kernel version.  Find the kernel version you're using [probably the latest version] We'll need this for a command line operation in the next step. 
[*]Type the following command in a console replacing the kernel version you find for what I have here. ```
sudo update-initramfs -c -k 3.8.0-32-generic
``` 
[*]Reboot  [not sure this is required but I prefer clean steps] 
[/LIST]
  
[*]Install the driver.  [You might want to print or write these down if you're using the same computer to read this]
[LIST=1|INDENT=2]
[*]Turn off the graphical user interface
[LIST=1|INDENT=2]
[*]Open a terminal session by typing CTRL-ALT-F1 
[*] Log in 
[*]Type the following line to turn off the Graphical User Interface ```
sudo service lightdm stop
```. You can check to see if it's running by hitting CTRL-ALT-F7.  If it's still running, your Gnome session will pop up. 
[/LIST]
  
[*]Go to the directory where you saved the Nvidia drivers. 
[*]     Change the owner of the file to root  ```
sudo chown root NVIDIA-Linux-x86_64-319.60.run
``` 
[*]Make the file executable by typing the following command:  ```
sudo chomod +x NVIDIA-Linux-x86_64-319.60.run
``` 
[*]Type the following line correcting the file name with the driver you downloaded. ```
sudo ./NVIDIA-Linux-x86_64-319.60.run
``` 
[*]Follow the instructions. 
[/LIST]
      
[/LIST]
 
I ran into an error and continued anyway when prompted.  The install otherwise went fine. 

I had previously installed 'sysinfo' from the software center.  I used this to check the current setup of my video driver and confirmed the Nvidia driver was loaded and running without incident.

---

