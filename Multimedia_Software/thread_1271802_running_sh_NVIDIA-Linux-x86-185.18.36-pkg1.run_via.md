---
title: "running sh NVIDIA-Linux-x86-185.18.36-pkg1.run via terminal"
date: 2009-09-21
forum: Multimedia Software
---

### Post by hihihi100 on 2009-09-21
In system - help and support, if you search for nvidia, you will find a nvidia installer section. In the first paragraph, we can read:

When the driver is installed by running, for example:

sh NVIDIA-Linux-x86-185.18.36-pkg1.run

The .run file unpacks itself and invokes the contained nvidia-installer utility. nvidia-installer
then walks you through the installation process.

Well, I have downloaded that same driver from the Nvidia official site, and when I open a terminal and paste that, it says:

sh: Can't open NVIDIA-Linux-x86-185.18.36-pkg1.run

What am I doing wrong?

---

### Post by tkoco on 2009-09-22
Why would you want to install the nVidia proprietary driver in that fashion? Doesn't the "System -> Administration -> Hardware Drivers" menu find the correct driver?


> **hihihi100 said:**
> In system - help and support, if you search for nvidia, you will find a nvidia installer section. In the first paragraph, we can read:

When the driver is installed by running, for example:

sh NVIDIA-Linux-x86-185.18.36-pkg1.run

The .run file unpacks itself and invokes the contained nvidia-installer utility. nvidia-installer
then walks you through the installation process.

Well, I have downloaded that same driver from the Nvidia official site, and when I open a terminal and paste that, it says:

sh: Can't open NVIDIA-Linux-x86-185.18.36-pkg1.run

What am I doing wrong?

---

### Post by cor2y on 2009-09-22
First of all you may need to make the package executable.
Secondly be warned you will always have to reinstall this driver everytime there is a kernel update if you dont use the one that comes via synaptic
Thirdly you cannot install this package if your graphical frontend is running  so heres the steps to do
 via the terminal
```
 chmod 777 NVIDIA-Linux-x86-185.18.36-pkg1.run
```
Next in the terminal
```
 sudo /etc/init.d/gdm stop
```
This stops the gnome desktop manager (killing your graphical frontend) and dumps you into full terminal mode, you may have to login via the terminal again after doing that this comes next
```
sudo sh NVIDIA-Linux-x86-185.18.36-pkg1.run
```
Now you may have to explicitly point to where the package is or cd into the directory where it is for example
```
 cd ~/Desktop;sudo sh NVIDIA-Linux-x86-185.18.36-pkg1.run
```
or
```
sudo sh ~/Desktop/NVIDIA-Linux-x86-185.18.36-pkg1.run
```
If all goes well the driver will be installed and you will automatically go into your graphical frontend if not then type
```
sudo /etc/init.d/gdm start 
```
And it will come back

---

### Post by hihihi100 on 2009-09-22
yes, i would prefer to use the synaptic way, but you may want to read:

[http://ubuntuforums.org/showthread.php?t=1267839](http://ubuntuforums.org/showthread.php?t=1267839)

just to know why I am choosing this way

---

### Post by hihihi100 on 2009-09-23
this is what i get:

sh NVIDIA-Linux-x86-185.18.36-pkg1.run
sh: Can't open NVIDIA-Linux-x86-185.18.36-pkg1.run

Am I doing anything wrong?

---

### Post by HappyFeet on 2009-09-23
Do:
```
**sudo** sh NVIDIA-Linux-x86-185.18.36-pkg1.run
```

---

### Post by beastrace91 on 2009-09-23
Make sure you are in the directory that your .run file is in - for example ```
jeff@eeetop:~$ sh NVIDIA-Linux-x86-185.18.36-pkg1.run
sh: Can't open NVIDIA-Linux-x86-185.18.36-pkg1.run

```

It can't open it in my home directory because I don't have the file ;)

Use the ls and cd commands to find the right directory. Also as stated you will need to run the driver package as sudo.

Also as an fyi because he is using the sh command to run the file you *shouldn't* need to chmod the file to be executable.

~Jeff

---

### Post by beastrace91 on 2009-09-23
> **tkoco said:**
> Why would you want to install the nVidia proprietary driver in that fashion? Doesn't the "System -> Administration -> Hardware Drivers" menu find the correct driver?

Because the ones contained here in 9.04 are the 180 drivers - they are old at this point and the 185/190 drivers provide much better performance.

~Jeff

---

### Post by hihihi100 on 2009-09-25
k, here is a message I have been ignoring for a while, but now I think it has much to say about the problems of my computer:

Before asking for my username and password, a message appears, (I believe it is out of GDM, since GDM is the graphical interface), reading:

There already appears to be an x server running on display :0 Should another display number be tried? Answering no will cause GDM to attempt starting the server on :0 again,

and then it says that I can change consoles

I click yes (I have to do it a plurality of times until the system finds a workable display), and the system runs, but only on low graphics mode. 

Is this why the system fails to load glx?

What do I have to do to kill this running X server? I cannot install the 185 driver because of this (x server still running), am I right?

If this sounds too obvious for you, don forget im a noob

cheers

---

### Post by beastrace91 on 2009-09-26
To kill X run ```
sudo /etc/init.d/gdm stop
``` in terminal.

~Jeff

---

### Post by Drekthar on 2011-06-30
[cor2y]("http://ubuntuforums.org/member.php?u=59168") commands worked instantly for me finally i have the gui working in my htpc running xbmc dharma 

cheers
:grin:

---

