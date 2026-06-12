---
title: "Nvidia Driver Help ~~ NVIDIA-Linux-x86-256.44.run"
date: 2010-08-04
forum: Multimedia Software
---

### Post by scater on 2010-08-04
I have been struggling on how to fix this issue. I am trying to update my Nvidia MX 480 GFX card. Today I figured out how to run the program as a root: ```
sudo sh /home/menkin/Desktop/NVIDIA-Linux-x86-256.44.run
```
I run that and then this is what it gives me. 

 WARNING: The NVIDIA GeForce4 MX 440 GPU installed in this system is          
           supported through the NVIDIA 96.43.xx legacy Linux graphics         
           drivers.  Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for   
           more information.  The 256.44 NVIDIA Linux graphics driver will     
           ignore this GPU.
  WARNING: You do not appear to have an NVIDIA GPU supported by the 256.44     
           NVIDIA Linux graphics driver installed in this system.  For further 
           details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in 
           the README available on the Linux driver download page at           
           [www.nvidia.com](www.nvidia.com).
  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).
 
  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

I am very confused on what the answer might be. Can someone please help me here. this is where I got the link to download the nvidia driver from: [http://www.nvidia.com/object/linux-display-ia32-256.44-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.44-driver.html)

Someone please help ASAP

---

### Post by sikander3786 on 2010-08-04
Hi.

Did you try installing from System >>> Administration >>> Hardware Drivers? The latest drivers are present there and will be much more helpful in case of a kernel update because you don't need to reinstall after a kernel update. Just a few clicks away.

Regards.

---

### Post by py8elo on 2010-08-04
> **scater said:**
> I have been struggling on how to fix this issue. I am trying to update my Nvidia MX 480 GFX card. Today I figured out how to run the program as a root: ```
sudo sh /home/menkin/Desktop/NVIDIA-Linux-x86-256.44.run
```
I run that and then this is what it gives me. 

 WARNING: The NVIDIA GeForce4 MX 440 GPU installed in this system is          
           supported through the NVIDIA 96.43.xx legacy Linux graphics         
           drivers.  Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for   
           more information.  The 256.44 NVIDIA Linux graphics driver will     
           ignore this GPU.
  WARNING: You do not appear to have an NVIDIA GPU supported by the 256.44     
           NVIDIA Linux graphics driver installed in this system.  For further 
           details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in 
           the README available on the Linux driver download page at           
           [www.nvidia.com](www.nvidia.com).
  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).
 
  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

I am very confused on what the answer might be. Can someone please help me here. this is where I got the link to download the nvidia driver from: [http://www.nvidia.com/object/linux-display-ia32-256.44-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.44-driver.html)

Someone please help ASAP
Hi Scater,
before install a new driver You need to remove the old one...
Please, put the commands:
ALT+F2: gksu gedit /etc/modprobe.d/blacklist.conf 
Add these lines to the file:
vga16fb
nouveau
rivafb
nvidiafb
rivatv
Save and restart your pc...

CTRL+ALT+F1
Login with your default account user

sudo gdm-stop
sudo apt-get --purge remove nvidia-\*
sudo apt-get --purge remove xserver-xorg-video-nouveau

cd /your new driver location
sudo sh NVIDIA-Linux-x86-x86-256.44.run
The installation starts now...
Answer the questions and aftaer the installations has finished just put the command:
sudo reboot
When restart your Ubuntu will be running the new Nvidia driver.
In a terminal put :
sudo nvidia-xconfig
Restart once more...
Thats all!!!
I hope it can help You!!!

Kind Regards,

Silva.
PY8ELO

---

### Post by realzippy on 2010-08-04
[I]
WARNING: The NVIDIA GeForce4 [COLOR="Red"]MX 440[/COLOR] GPU installed in this system is
supported through the NVIDIA 96.43.xx legacy Linux graphics
drivers. Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for
more information. The 256.44 NVIDIA Linux graphics driver will
ignore this GPU.[/I]

[COLOR="Red"]Thought you wrote about a GTX 480?[/COLOR]

---

### Post by scater on 2010-08-04
> **py8elo said:**
> Hi Scater,
before install a new driver You need to remove the old one...
Please, put the commands:
ALT+F2: gksu gedit /etc/modprobe.d/blacklist.conf 
Add these lines to the file:
vga16fb
nouveau
rivafb
nvidiafb
rivatv
Save and restart your pc...

CTRL+ALT+F1
Login with your default account user

sudo gdm-stop
sudo apt-get --purge remove nvidia-\*
sudo apt-get --purge remove xserver-xorg-video-nouveau

cd /your new driver location
sudo sh NVIDIA-Linux-x86-x86-256.44.run
The installation starts now...
Answer the questions and aftaer the installations has finished just put the command:
sudo reboot
When restart your Ubuntu will be running the new Nvidia driver.
In a terminal put :
sudo nvidia-xconfig
Restart once more...
Thats all!!!
I hope it can help You!!!

Kind Regards,

Silva.
PY8ELO

At first I did everything you said and it worked. But then when it got to the installation of the driver, I accidentally clicked I do not agree. Now it says the same thing it did before. Is there something I can do to fix this?

---

### Post by py8elo on 2010-08-04
Repeat all the steps from "sudo gdm-stop" again...

---

### Post by scater on 2010-08-04
> **py8elo said:**
> Repeat all the steps from "sudo gdm-stop" again...

I did the sudo gdm-stop command. that seemed to work. But then I typed in the --purge remove nvidia-\* command and then it says" E: Couldn't find package Nvidia-*

---

### Post by realzippy on 2010-08-05
The command has a typo.It should be:

```
sudo apt-get --purge remove nvidia-*
```

no backslash.

[COLOR="Red"]Is it correct that you replaced a MX 440 with a GTX 480 graphics card?[/COLOR]

---

### Post by cascade9 on 2010-08-05
@ realzippy- technically possible to replace a MX440 with a GTX480, but that would be so uncommon it not funny. Not many PCI MX440s around, and I have yet to see a PCI video card in a system that supports PCIe. 

> **scater said:**
> WARNING: The NVIDIA GeForce4 MX 440 GPU installed in this system is          
           supported through the NVIDIA 96.43.xx legacy Linux graphics         
           drivers.  Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for   
           more information.  The 256.44 NVIDIA Linux graphics driver will     
           ignore this GPU.
  WARNING: You do not appear to have an NVIDIA GPU supported by the 256.44     
           NVIDIA Linux graphics driver installed in this system.  For further 
           details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in 
           the README available on the Linux driver download page at           
           [www.nvidia.com]("http://www.nvidia.com").


Like the installer said, if you've got a GF4 MX440 you will never get the 256.xx drivers to work. Its just not supported by that driver....

---

### Post by realzippy on 2010-08-05
That' what I say.See post #4;assuming OP has no gtx 480;
but he does not answer when asked.Other posters here also ignore his error
message regarding the 440MX.Began feeling as idiot..   ;-)
Now marked it red ,maybe *[COLOR="Red"]scater[/COLOR]* will [COLOR="Red"]see[/COLOR] this.

---

