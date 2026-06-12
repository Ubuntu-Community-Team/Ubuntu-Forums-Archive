---
title: "nVidia drivers - &quot;You appear to be running an X server&quot;"
date: 2012-01-29
forum: Multimedia Software
---

### Post by tommyk1995 on 2012-01-29
So I'm new to Ubuntu/Linux in general, and I'm trying to install my graphics drivers so I don't have to open grub and boot in nomodeset every time... I've gotten a .run file from nvidia.com for the latest x86 linux drivers for my 550 ti. After logging in as root (sudo -i, enter password), changing to the directory of the .run file, and doing "sh NVIDIA.run" (I renamed the file to NVIDIA.run so it's shorter to type), it starts to install the drivers but throws an error saying "You appear to be running an X server". How do I fix this?

Thanks.

E: Heres the installer log
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Jan 29 00:28:10 2012
installer version: 290.10

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1195' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at www.nvidia.com.
```Edit 2:
doing
```
sudo kill 1195
```made me exit to the log in screen and i had to log back in.


edit 3:
Ok wow solved this my self. Here's how I did it:

1. open gnome (CTRL + ALT + F3)
2. log in as your user
3. run "sudo init 3"
4. switch to root ("sudo -i" or "sudo su root")
5. cd to the directory containing the .run file
6. sh NVIDIA.run (where NVIDIA.run is the name of the .run file)
7. after completing the prompts, enter "reboot"

Thanks.

---

### Post by james2b on 2012-01-29
At the GRUB boot menu screen select your Ubuntu and then hit the e key to edit the kernel line boot options so that it will only boot to run level 3 text mode hopefully without the Xserver running. At the end of this kernel line after the long UUID is; "ro quiet splash", and so on, replace all that with; "rw nosplash --verbose text" which will allow you to view any boot up error messages and to boot into a text console to run your commands. The rw is for to mount in read write mode, not read only which I needed to do for this same type issue on my PC. And use your keyboard arrow keys to move the cursor while in grub.

---

### Post by ajgreeny on 2012-01-29
If that is too difficult for you just boot normally to a gui, Ctrl+Alt+F1 to get to a tty command line, then login and use commands
```
sudo service lightdm stop
```
and then navigate to the folder where your NVIDIA.run is sitting and use the command you did before to execute it.

Now you should be able to start the new xsession with ```
sudo service lightdm start
```or maybe just ```
startx
```

---

### Post by MichaelGld on 2012-02-06
When I enter Ctrl+Alt+F1, I get a black screen with some horizontal garbage at the top of the screen and NO prompt. When I try to return to the desktop by pressing Ctrl+Alt+F7, it only makes the screen garbage move a bit, no desktop and no prompt. I have been trying to load the driver for my GeForce 210 card. I am stuck using the Ubuntu generic drivers. I'd appreciate any help.


> **ajgreeny said:**
> If that is too difficult for you just boot normally to a gui, Ctrl+Alt+F1 to get to a tty command line, then login and use commands
```
sudo service lightdm stop
```
and then navigate to the folder where your NVIDIA.run is sitting and use the command you did before to execute it.

Now you should be able to start the new xsession with ```
sudo service lightdm start
```or maybe just ```
startx
```

---

### Post by aNxello on 2012-03-07
> **ajgreeny said:**
> If that is too difficult for you just boot normally to a gui, Ctrl+Alt+F1 to get to a tty command line, then login and use commands
```
sudo service lightdm stop
```
and then navigate to the folder where your NVIDIA.run is sitting and use the command you did before to execute it.
 
Now you should be able to start the new xsession with ```
sudo service lightdm start
```or maybe just ```
startx
```
 
 
This finally helped! Thank you a lot:KS

---

### Post by Elentir on 2012-09-08
Small addition.

I had the same problem with the X server (it was still runnning). However, tommyk1995's solution didn't work because X was still running, and CTRL+ALT+F1 didn't work either because whenever I entered something there, nothing happened. 

As CTRL+ALT+F3 did work for me I made a combination of some solutions to create a new one:

> Enter CTRL+ALT+F3

> Enter your username + password

Enter:
```
sudo service lightdm stop
```


```
cd Downloads
```

```

sudo sh NVIDIA-Linux-*
```
(where * is your version)

I got a warning but just ignored it and continued. Go through the installation and when finished enter:


```
sudo service lightdm start
```

----------
While struggling with the installation (before I finally found the solution) I got an additional problem with logging-in. The screen turned black and I returned to the log-in screen.

I found this solution:

CTR+ALT+F3 in log-in screen
Enter username+password

Enter:
```

sudo chmod 777 /home/[username]/.Xauthority
```

I did a reboot, but maybe there is an easier way:

```

sudo su root

reboot

```

(Ubuntu 12.04)

---

### Post by biocyberman on 2013-07-08
> **ajgreeny said:**
> If that is too difficult for you just boot normally to a gui, Ctrl+Alt+F1 to get to a tty command line, then login and use commands
```
sudo service lightdm stop
```
and then navigate to the folder where your NVIDIA.run is sitting and use the command you did before to execute it.

Now you should be able to start the new xsession with ```
sudo service lightdm start
```or maybe just ```
startx
```

This let me install NVIDIA GPU driver downloaded from NVIDIA homepage.

Thanks.

---

### Post by Yellow Pasque on 2013-07-08
It's not a good idea to install the nvidia driver directly. You should use a package...

---

