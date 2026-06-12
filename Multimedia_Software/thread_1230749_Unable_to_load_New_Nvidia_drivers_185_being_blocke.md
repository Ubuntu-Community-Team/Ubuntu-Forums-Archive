---
title: "Unable to load New Nvidia drivers 185 being blocked"
date: 2009-08-03
forum: Multimedia Software
---

### Post by k4kelly on 2009-08-03
I'm running Mythbuntu 9.04_64 , My hardware a Asus SLI M3N72-D MB, With 2 Nvidia Gforce 7900 GT/GT0, A AMD 2.6gh X2, 8 mb of ram. When I try to load the new Nvidia drivers. NVIDIA-Linux-86_64-185.18.29-pkg2.run. I get a message "Unknown ID:"  I am able to load the proprietary driver from the
system hardware devices and have downloaded the same drivers from Nvidia to my Documents directry and installed them. They all come up in terminal mode when I reboot so I thought I would try the new ones.
I feel like the installed is being blocked by the system. I looked through the Aurthorizations in the System
drop down menu. But I need some help. Can anyone help with this.

---

### Post by wojox on 2009-08-03
This may help:
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

---

### Post by -=hazard=- on 2009-08-03
Does the 180 driver version works fine? Because I use them and they work fine and you can update in safe way from System -> Administration -> Hardware Drivers

-edited-

The link that wojox posted is very useful :)

---

### Post by k4kelly on 2009-08-03
I've tried all of them. They all load oK but on reboot they come up in terminal mode. Most of the time I could not recover I had to reload the software.

---

### Post by -=hazard=- on 2009-08-03
> **k4kelly said:**
> I've tried all of them. They all load oK but on reboot they come up in terminal mode. Most of the time I could not recover I had to reload the software.

I don't understand when you say that on reboot they come on terminal mode, you mean that xorg doesn't start? If so, did this happened immediately after the fresh install when you installed the 180 version from Hardware Drivers?****

---

### Post by tipii on 2009-08-03
I have the same problem and yes xorg doesn't start. this happens immediately after installing 180 from hardware drivers

---

### Post by k4kelly on 2009-08-03
I went to the above link "http://ubuntuforums.org/showthread.php?t=1125400" as suggested and printed out all the instructions. When I issued the instruction " sudo su /usr/src/nvidia-driver"  the terminal returns Unknown id:    nvidia-driver is a link to the NVIDIA-185 drivers which are stored in the src directory.  I have used the hardware driver dropdown menu is systems to install the NVIDIA-180 drivers
at least a doesn't times. It will install just fine but on reboot only terminal mode. I have a stack of printed out suggestion from this and other sources about 2" high that I have tried, but so far I cannot
get the drivers to work. Occording to the Nivida web site the drivers 185.18.29 support the GForce 7900 that is why I'm trying to load them. It seem like the  185 drivers are being block because they are not authorized. Any ideas how to get them to install?

---

### Post by -=hazard=- on 2009-08-04
I sugest to use 180 driver version because it's tested by ubuntu, I use it on Ubuntu 9.04 and it work just fine (I installed them from Hardware Drivers). Anyway you can check this [Link]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/") where is a way for ubuntu 8.04 LTS, I think you need the kernel headers, or you can check this [Page]("https://help.ubuntu.com/community/NvidiaManual") too. Like that way I installed my nvidia drivers for debian lenny 5, and the problem were only the headers.
Anyway for Ubuntu 9.04 the best way is installing from Hardware Drivers and it's strange that tipii got the same problem, unless he isn't using 9.04 version.

---

### Post by k4kelly on 2009-08-04
> **-=hazard=- said:**
> I sugest to use 180 driver version because it's tested by ubuntu, I use it on Ubuntu 9.04 and it work just fine (I installed them from Hardware Drivers). Anyway you can check this [Link]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/") where is a way for ubuntu 8.04 LTS, I think you need the kernel headers, or you can check this [Page]("https://help.ubuntu.com/community/NvidiaManual") too. Like that way I installed my nvidia drivers for debian lenny 5, and the problem were only the headers.
Anyway for Ubuntu 9.04 the best way is installing from Hardware Drivers and it's strange that tipii got the same problem, unless he isn't using 9.04 version.
 
 
I'm going to reload Ubunta 9.04 and try again. But I still don't see any explanation of why I'm "Unknown id: when I try to load the 185 version. I loaded the 180 version many times with no sucess but I have removed one of my 7900 video cards maybe that will make a difference. Thanks.

---

### Post by k4kelly on 2009-08-05
I reinstalled using Ubuntu 9.04 instead of mythbuntu 9.04. Downloaded the file from the web and made a install cd. I updated the Synaptic Package Manager and installed the updates. I the used the system>Admin>Hardware Drivers. I got a "Jockey Backend Crashed". Downloaded again created a new cd got the same thing when I tried to install from the Hardware Drivers. I used the above instructions "php/t=1125400" in tty2 terminal mode  . All the instruction worked fine until " sudo su NVIDIAxxx185 then the message returned was "Unknow id". Reinstalled Mythbuntu removed one of my video cards did not
install and updates. It loaded fine and works great but when I followed the instruction and put the second card back in my monitor turned off when it started loading and wouldn't come back on. I removed the second card. Anyone got any ideas?

---

### Post by -=hazard=- on 2009-08-06
> **k4kelly said:**
> I reinstalled using Ubuntu 9.04 instead of mythbuntu 9.04. Downloaded the file from the web and made a install cd. I updated the Synaptic Package Manager and installed the updates. I the used the system>Admin>Hardware Drivers. I got a "Jockey Backend Crashed". Downloaded again created a new cd got the same thing when I tried to install from the Hardware Drivers. I used the above instructions "php/t=1125400" in tty2 terminal mode  . All the instruction worked fine until " sudo su NVIDIAxxx185 then the message returned was "Unknow id". Reinstalled Mythbuntu removed one of my video cards did not
install and updates. It loaded fine and works great but when I followed the instruction and put the second card back in my monitor turned off when it started loading and wouldn't come back on. I removed the second card. Anyone got any ideas?

You can install the drivers without jockey.

Anyway your bug is reported on launchpad.

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/350776](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/350776)

Take a look here too: [http://ubuntuforums.org/showthread.php?t=1136306](http://ubuntuforums.org/showthread.php?t=1136306)

---

### Post by dagrump on 2009-08-06
Okay, I think this will fix you up. With both cards installed & bridged (does your mobo require a card flipped or jumper switched?) I'm assuming & you know how dangerous that is, that if you reboot you get a terminal type login. then try the following.
After the drivers are installed & it boots back up, go ahead & log in.
Then you need to enter "lspci" this will list your hardware, find & write down the BusID of both cards.
Now enter "sudo nvidia-xconfig", it will ask for your password (there will be no visual feedback when typing your password).
That creates your xorg.conf file. Now to edit it.
You would enter "sudo nano /etc/X11/xorg.conf", nano is an editor.
Now arrow down till the cursor is at the EndSection line of the device section, hit enter twice.
Arrow up twice and enter line looks like so; BusID "XX:YY:ZZ", with XYZ being the numbers recorded earlier, of your primary card.
Drop to the next line & try; Option "SLI" "SFR".
Now crtl+o to write & crtl+x to exit.
And a "sudo shutdown -r now", to reboot & if all goes well you are working.

********
Please note where referencing CLI entries the quote marks should not be used, but during edit of xorg.conf they are needed.
IIRC the "SFR" is split screen rendering.

---

### Post by k4kelly on 2009-08-07
I just tried that I got the info from here ( [http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.31/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.31/README/appendix-b.html) ). I used a different option  but i had the same problem. When the graphics screen boots up it put the monitor in standby mode. I tried all the dvi output port on both video cards. When I did a hard reset the screen was black the whole time even while the bios was loading. I removed a video card and it is working fine again.  Here is a copy of xorg.conf 
 
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        BUSID   "PCI:2:0:0"
        Identifier      "Device0"
        Driver  "nvidia"
        Option  "SLI" "1, yes, on, true, auto"
        Option  "NoLogo"        "True"
EndSection

I used lspci to get the PCI id for my primary card the other PCID:3:0:0. I have nothing in any forum about adding it to the file. If anyone has any other ideas please post them. I will try them.

---

### Post by k4kelly on 2009-08-08
When i enabled system>admin>hardware drivers is when jockey kept failing. Would not down load the nvidia file. I didn't have a copy on my computer so could not load it.

---

### Post by dagrump on 2009-08-08
Well, this is what my xorg.conf looks like.

---

### Post by tipii on 2009-08-10
Thanks for that, unfortunately without having the NVidia drivers correctly installed we would only get errors for editing our xorg.conf to match this, I have tried before.
The problem (I think) is in somewhere in the enabling of the restricted drivers.
Neither way, GUI or command line, work.
For me they install without hitch but on reboot the GDM fails to load... just a blank screen in tty6.
Still havn't got any further with this...
Thanks though!

Does anyone know of any likely conflicts that might arise when installing NVidia drivers on a fresh Wubi install?

---

### Post by dagrump on 2009-08-10
I may be all wet, but I don't think you can use or need linux drivers with wubi, as I understand it's just virtual machine install inside windows. Kind of a demo mode.
If you are running a native install & have tried loading the drivers & it failed you should uninstall them & start over. I think "sudo apt-get --purge nvidia-*" w/o the quotes is the proper command, but double check first. Then try the method I suggested.
Yes your xorg.conf will not be identical, as it is based on hardware nvidia-config detects.

---

### Post by tipii on 2009-08-12
Hi dagrump, thanks again

This is from Wiki:
> It is not a virtual machine, but rather, it creates a stand-alone installation within a loopmounted device, also known as a disk image, like Topologilinux does. It is not a Linux distribution of its own, but rather an installer for Ubuntu.

And also this:
> The advantage of this setup is that users can test the operating system and install the drivers before they install it to a dedicated partition (and avoid booting and functioning risks).

I presumed from this that I could install the drivers and such just the same as in Ubuntu.

I've tried purging nvidia and fglrx and reconfiguring xerver-org and purging linux-restricted-modules and removing nvidia-new-glx and nvidia-new. This doesn't work so then I uninstall Wubi through windows and try again. And so on.

Adding Nvidia to my xorg.conf doesn't help if nvidia's not installed but when I check xorg.conf from tty1 (after installing nvidia and when GDM fails) its already there having been added automatically during setup. The weird thing is if I restore xorg.conf to its original file to try and bypass the nvidia drivers once the GDM has failed, it doesn't work and GDM continues to fail.

---

### Post by tipii on 2009-08-12
I've finally got around this and got ubuntu working with NVIDIA drivers.

Solution : scrap wubi and go full on ubuntu instead

Didn't work straight off... Had the same problem initially, GDM failed to load with new drivers.

Because I now had grub I could open the earlier grub entry (the later entry was created when I installed updates prior to enabling nvidia drivers) and this opened without a hitch. Lo and behold nvidia x server settings was in system>admin so I opened it up and overwrote the xorg.conf, rebooted and GDM loaded OK.

Thnaks to everyone who chipped in, not just in this thread. Had I not been so anxious to get this running quickly I would have quite enjoyed problem solving this with all of you helpful people showing such support.

---

### Post by dagrump on 2009-08-12
Okay, kinda lost me there, did you have hand edit your xorg or not? I guess what I'm wondering, is it running in SLI now or not?
In the X server setting under X screen 0 Does it list both video cards?

---

### Post by k4kelly on 2009-08-15
I changed my parameters in my xorg.conf file to those suggested above by dagrump. I had problems at first because I forget to connect the power cable to the second Nvidia card when I put it back in. I did a lspci | grep VGA before I realized that I forgot the power connector.  It showed one card at Busid 3.  I had done a list with the one card before it showed the card that I had installed was at Busid 2.  I put both id in the file with ID 3 first. I connected the power cable and rebooted. It came right up eveything seems to be working fine. I pasting a copy of my xorg.conf file.

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Device0"
        VendorName      "NVIDIA Corporation"
        Driver  "nvidia"
        Option  "SLI" "SFR"
        BUSID   "PCI:3:0:0
        Option  "NoLogo"        "True"
EndSection
Thanks all of you for all your help. I never was able to load the Nvidia 185 drivers to load, but I up and running with 180 and will mark this solved.:KS

---

### Post by dagrump on 2009-08-15
Glad to see your running.

---

