---
title: "Ubuntu Nvidia Driver 319.23"
date: 2013-06-04
forum: Multimedia Software
---

### Post by Dead6Man9Walking on 2013-06-04
Hello, 

This is my first post, so I hope this is in the right section of the forums.

Basically, I've just installed Ubuntu 13.04 on my laptop and everything is running perfect - except I just cannot get the latest Nvidia drivers (319.23) to work. I've tried various guides of the internet and they all seem to end in the same way - which to sum it up, is the lack of unity starting. I get no bars on windows or anything, just a desktop and any file that happens to be on their and if I install the official Nvidia .run file off of the website I get the same lack of Unity, but also the res is changed to 800x600.

Also going to the "additional Drivers" section of Ubuntu software center doesn't work because there are no Nvidia drivers listed - It just says my machine is not using any proprietary drivers. 

I've used this guide for the official Nvidia .run driver file: [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

I'm not really and expert with Ubuntu but I really like the OS and would like to keep using it, however I want to try get my Nvidia GT635m to be used rather than my HD3000 cause I have a few steam games I like to play :P and now I can use Linux I don't want to go back to Windows!

---

### Post by SeijiSensei on 2013-06-04
If the Additional Drivers application doesn't see the NVIDIA card, chances are good this is "hybrid" machine with both an Intel and an NVIDIA card.  Search in the BIOS to see if you can disable the Intel adapter and try again.  

You might also look into the [Bumblebee Project]("http://bumblebee-project.org/") which is designed to work with these kinds of hybrid machines.

---

### Post by Dead6Man9Walking on 2013-06-04
Hello!

Yeah it is, on Windows i can switch between the Intel HD3000 and the Nvidia GT635m depending on what I'm doing, by default Ubuntu seems ot be using my HD3000 but that's no good for gaming. I tried Bumbleebee, but have no real idea how to install it properly along with the latest Nvidia 319.23 drivers. This is where I'm completely stuck =/

As for the BIOS, I have one of the laptops that doesnt have an option to disable to Intel one sadly =/ - For teh record my laptop is an Asus N55SL

---

### Post by grahammechanical on 2013-06-04
You will be interested in these links

[http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html)

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

They are both just under 2 months old.

Regards.

---

### Post by Dead6Man9Walking on 2013-06-04
Hello! 

I have read both links, the first one gives me some Nvidia drivers, however since then newer ones have been released - the ones in that link are 319.12 and the current ones are 329.23, also It doesn't tell me how to install them. As for the second link it tells me how tio install the window manager, but not how to install BumbleBee and the Nvidia drivers =/

Thank you for the help though - installing and getting these drivers to work is being to get a pain the backside!

---

### Post by kreppnar on 2013-06-08
Check out my blog. I have made a pretty good walkthrough for bumblebee. [http://orkultus.wordpress.com](http://orkultus.wordpress.com)

-Orkultus-

---

### Post by GUZZLR on 2013-06-08
I stumbled upon this thread, and I dont seem to have my Nvidea working either.  I read (and followed the steps) the blog which Orkultus, but it tells me no Bumble Bee found, and this is where I get lost.
The system is an older HP Pavilion running Windows 7 Pro on the internal C:drive.  I am currently running 13.04 on an external drive. I'm open to suggestions? 

I did run the basic bumble Bee install, Thanks for the help

```
charles@GUZZLR:~$ sudo add-apt-repository ppa:bumblebee/stable
[sudo] password for charles: 
You are about to add the following PPA to your system:
 Bumblebee Stable PPA

Installation instructions: https://wiki.ubuntu.com/Bumblebee

To report issues, please read http://wiki.Bumblebee-Project.org/Reporting-Issues

You may use any nvidia driver flavor, like -updates, -experimental or -nnn ones.

After installation, reboot to let changes apply.

To see if it works, run during around 30s: glxspheres
Then, run it with optirun, and compare: optirun glxspheres

If you want to use primus, you need to install it and set Bridge=primus in bumblebee.conf or use optirun -b primus. You also need to install primus-libs-ia32 if you want to run 32-bit apps.

Be aware that as Bumblebee is using low-level hardware informations, it is impossible to run it in a VM.
 More info: https://launchpad.net/~bumblebee/+archive/stable
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpbdvg19/secring.gpg' created
gpg: keyring `/tmp/tmpbdvg19/pubring.gpg' created
gpg: requesting key 8110A93A from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpbdvg19/trustdb.gpg: trustdb created
gpg: key 8110A93A: public key "Launchpad PPA for Bumlebee Project" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
charles@GUZZLR:~$ sudo apt-get update
Hit http://mirror.steadfast.net raring Release.gpg
Hit http://mirror.steadfast.net raring-updates Release.gpg
Hit http://mirror.steadfast.net raring-backports Release.gpg
Hit http://mirror.steadfast.net raring-security Release.gpg
Hit http://mirror.steadfast.net raring Release                                 
Hit http://mirror.steadfast.net raring-updates Release                         
Hit http://mirror.steadfast.net raring-backports Release                       
Hit http://mirror.steadfast.net raring-security Release                        
Get:1 http://ppa.launchpad.net raring Release.gpg [316 B]                      
Hit http://mirror.steadfast.net raring/main Sources                          
Hit http://mirror.steadfast.net raring/restricted Sources                    
Hit http://mirror.steadfast.net raring/universe Sources                      
Hit http://ppa.launchpad.net raring Release.gpg                              
Hit http://mirror.steadfast.net raring/multiverse Sources                    
Hit http://mirror.steadfast.net raring/main i386 Packages
Hit http://mirror.steadfast.net raring/restricted i386 Packages              
Hit http://mirror.steadfast.net raring/universe i386 Packages                
Get:2 http://ppa.launchpad.net raring Release [9,753 B]                      
Hit http://mirror.steadfast.net raring/multiverse i386 Packages                
Hit http://mirror.steadfast.net raring/main Translation-en                     
Hit http://mirror.steadfast.net raring/multiverse Translation-en               
Hit http://ppa.launchpad.net raring Release                                  
Hit http://mirror.steadfast.net raring/restricted Translation-en              
Hit http://mirror.steadfast.net raring/universe Translation-en               
Get:3 http://ppa.launchpad.net raring/main i386 Packages [3,542 B]           
Hit http://mirror.steadfast.net raring-updates/main Sources                  
Hit http://mirror.steadfast.net raring-updates/restricted Sources              
Hit http://mirror.steadfast.net raring-updates/universe Sources               
Hit http://mirror.steadfast.net raring-updates/multiverse Sources             
Hit http://mirror.steadfast.net raring-updates/main i386 Packages             
Hit http://mirror.steadfast.net raring-updates/restricted i386 Packages       
Hit http://mirror.steadfast.net raring-updates/universe i386 Packages         
Hit http://mirror.steadfast.net raring-updates/multiverse i386 Packages       
Hit http://mirror.steadfast.net raring-updates/main Translation-en            
Hit http://ppa.launchpad.net raring/main i386 Packages                        
Hit http://mirror.steadfast.net raring-updates/multiverse Translation-en      
Hit http://mirror.steadfast.net raring-updates/restricted Translation-en      
Hit http://mirror.steadfast.net raring-updates/universe Translation-en        
Hit http://mirror.steadfast.net raring-backports/main Sources                 
Hit http://mirror.steadfast.net raring-backports/restricted Sources           
Hit http://mirror.steadfast.net raring-backports/universe Sources             
Hit http://mirror.steadfast.net raring-backports/multiverse Sources           
Hit http://mirror.steadfast.net raring-backports/main i386 Packages           
Hit http://mirror.steadfast.net raring-backports/restricted i386 Packages     
Hit http://mirror.steadfast.net raring-backports/universe i386 Packages       
Hit http://mirror.steadfast.net raring-backports/multiverse i386 Packages     
Hit http://mirror.steadfast.net raring-backports/main Translation-en          
Hit http://mirror.steadfast.net raring-backports/multiverse Translation-en    
Hit http://mirror.steadfast.net raring-backports/restricted Translation-en    
Hit http://mirror.steadfast.net raring-backports/universe Translation-en      
Hit http://mirror.steadfast.net raring-security/main Sources                  
Hit http://mirror.steadfast.net raring-security/restricted Sources            
Hit http://mirror.steadfast.net raring-security/universe Sources              
Hit http://mirror.steadfast.net raring-security/multiverse Sources            
Hit http://mirror.steadfast.net raring-security/main i386 Packages            
Hit http://mirror.steadfast.net raring-security/restricted i386 Packages      
Hit http://mirror.steadfast.net raring-security/universe i386 Packages        
Hit http://mirror.steadfast.net raring-security/multiverse i386 Packages      
Hit http://mirror.steadfast.net raring-security/main Translation-en           
Hit http://mirror.steadfast.net raring-security/multiverse Translation-en     
Hit http://mirror.steadfast.net raring-security/restricted Translation-en     
Hit http://mirror.steadfast.net raring-security/universe Translation-en       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://mirror.steadfast.net raring/main Translation-en_US
Ign http://mirror.steadfast.net raring/multiverse Translation-en_US
Ign http://mirror.steadfast.net raring/restricted Translation-en_US
Ign http://mirror.steadfast.net raring/universe Translation-en_US
Ign http://mirror.steadfast.net raring-updates/main Translation-en_US
Ign http://mirror.steadfast.net raring-updates/multiverse Translation-en_US
Ign http://mirror.steadfast.net raring-updates/restricted Translation-en_US
Ign http://mirror.steadfast.net raring-updates/universe Translation-en_US
Ign http://mirror.steadfast.net raring-backports/main Translation-en_US
Ign http://mirror.steadfast.net raring-backports/multiverse Translation-en_US
Ign http://mirror.steadfast.net raring-backports/restricted Translation-en_US
Ign http://mirror.steadfast.net raring-backports/universe Translation-en_US
Ign http://mirror.steadfast.net raring-security/main Translation-en_US
Ign http://mirror.steadfast.net raring-security/multiverse Translation-en_US
Ign http://mirror.steadfast.net raring-security/restricted Translation-en_US
Ign http://mirror.steadfast.net raring-security/universe Translation-en_US
Fetched 13.6 kB in 4s (2,909 B/s)
Reading package lists... Done
charles@GUZZLR:~$ sudo apt-get install bumblebee virtualgl linux-headers-genericReading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
linux-headers-generic set to manually installed.
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  bbswitch-dkms bumblebee-nvidia libturbojpeg nvidia-304 nvidia-current
  virtualgl-libs
The following NEW packages will be installed:
  bbswitch-dkms bumblebee bumblebee-nvidia libturbojpeg nvidia-304
  nvidia-current virtualgl virtualgl-libs
0 upgraded, 8 newly installed, 0 to remove and 24 not upgraded.
Need to get 39.7 MB of archives.
After this operation, 112 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://mirror.steadfast.net/ubuntu/ raring/universe libturbojpeg i386 1.2.1-0ubuntu2 [131 kB]
Get:2 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ raring/main bbswitch-dkms all 0.7-1~raringppa1 [12.6 kB]
Get:3 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ raring/main bumblebee i386 3.2.1-1~raringppa2 [61.7 kB]
Get:4 http://mirror.steadfast.net/ubuntu/ raring/restricted nvidia-304 i386 304.88-0ubuntu1 [38.4 MB]
Get:5 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ raring/main bumblebee-nvidia i386 3.2.1-1~raringppa2 [5,158 B]
Get:6 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ raring/main virtualgl-libs i386 2.3.2-1~raringppa2 [205 kB]
Get:7 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ raring/main virtualgl i386 2.3.2-1~raringppa2 [855 kB]
Get:8 http://mirror.steadfast.net/ubuntu/ raring/restricted nvidia-current i386 304.88-0ubuntu1 [4,488 B]
Fetched 39.7 MB in 39s (1,003 kB/s)                                            
Selecting previously unselected package libturbojpeg:i386.
(Reading database ... 207332 files and directories currently installed.)
Unpacking libturbojpeg:i386 (from .../libturbojpeg_1.2.1-0ubuntu2_i386.deb) ...
Selecting previously unselected package nvidia-304.
Unpacking nvidia-304 (from .../nvidia-304_304.88-0ubuntu1_i386.deb) ...
Selecting previously unselected package nvidia-current.
Unpacking nvidia-current (from .../nvidia-current_304.88-0ubuntu1_i386.deb) ...
Selecting previously unselected package bbswitch-dkms.
Unpacking bbswitch-dkms (from .../bbswitch-dkms_0.7-1~raringppa1_all.deb) ...
Selecting previously unselected package bumblebee.
Unpacking bumblebee (from .../bumblebee_3.2.1-1~raringppa2_i386.deb) ...
Selecting previously unselected package bumblebee-nvidia.
Unpacking bumblebee-nvidia (from .../bumblebee-nvidia_3.2.1-1~raringppa2_i386.deb) ...
Selecting previously unselected package virtualgl-libs:i386.
Unpacking virtualgl-libs:i386 (from .../virtualgl-libs_2.3.2-1~raringppa2_i386.deb) ...
Selecting previously unselected package virtualgl.
Unpacking virtualgl (from .../virtualgl_2.3.2-1~raringppa2_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-23-generic
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libturbojpeg:i386 (1.2.1-0ubuntu2) ...
Setting up nvidia-304 (304.88-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-304/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-304/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-304/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-304/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: using /usr/lib/nvidia-304/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-304
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Loading new nvidia-304-304.88 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-23-generic
Building for architecture i686
Building initial module for 3.8.0-23-generic
Done.

nvidia_304:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-23-generic/updates/dkms/

depmod......

DKMS: install completed.
Setting up bbswitch-dkms (0.7-1~raringppa1) ...
Loading new bbswitch-0.7 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-23-generic
Building initial module for 3.8.0-23-generic
Done.

bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-23-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up bumblebee (3.2.1-1~raringppa2) ...
Adding members from group(s) 'adm sudo admin' to 'bumblebee':
charles
Adding user charles to group bumblebee
Selecting 01:00:0 as discrete nvidia card. If this is incorrect,
edit the BusID line in /etc/bumblebee/xorg.conf.nouveau .
bumblebeed start/running, process 11564
Setting up virtualgl-libs:i386 (2.3.2-1~raringppa2) ...
Setting up virtualgl (2.3.2-1~raringppa2) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up nvidia-current (304.88-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-23-generic
Processing triggers for ureadahead ...
Setting up bumblebee-nvidia (3.2.1-1~raringppa2) ...
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in manual mode
Selecting 01:00:0 as discrete nvidia card. If this is incorrect,
edit the BusID line in /etc/bumblebee/xorg.conf.nvidia
Error: Module nouveau is in use
bumblebeed start/running, process 17346
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
charles@GUZZLR:~$ 


```

---

### Post by oldfred on 2013-06-08
If your system is older does it still have Optimus or dual video? That is relatively new. 
If not. you do not want Bumblebee, but just the nVidia driver if you have the nVidia chip or card.

---

### Post by GUZZLR on 2013-06-08
It probably does not have Optimus, this computer is about 4 years old now.  The problems I have after the above procedures are:
1. I can not activate my second monitor, Linux does not see it
2. I can not set my laptop resolution to 16:9, only 4:3 is offered; thus, making the secreen lengthwise distorted.
Thanks for the help

---

### Post by oldfred on 2013-06-08
Some links with info:

ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)
Dual nVidia cards - 2013
[http://ubuntuforums.org/showthread.php?t=2129190](http://ubuntuforums.org/showthread.php?t=2129190)
Using Six Monitors With AMD's Open-Source Linux Driver (not Ubuntu)
[http://www.phoronix.com/scan.php?page=news_item&px=MTM3NTM](http://www.phoronix.com/scan.php?page=news_item&px=MTM3NTM)

---

### Post by GUZZLR on 2013-06-08
So I tried the ARandR for dual screen setup, and no difference was made.  So, I uninstalled Bumble Bee per the website commands, and now I have no computer.  When it does boot, it tells me I'm running in low graphics mode, and gives me four choices:
1. Run in low graphics mode
2. Reconfigure Graphics
3. Troubleshoot the Error
4. Exit to console login

I tried number 1, which ask for my log in and password. Upon giving those crendentials, I now have a terminal asking for code...which I do not know what to input.
Thoughts?  Other than I should have not gone the Bumble Bee route!

---

### Post by monkeybrain2012 on 2013-06-08
You can install 319.23 from xorg-edgers but that is probably going to break bumble-bee, As far as I know if you use bumble-bee you should only upgrade your driver through its ppa.

If you don't have optimus, add this ppa, and install with synaptic and that's it.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by GUZZLR on 2013-06-08
```
If you don't have optimus, add this ppa, and install with synaptic and that's it.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```

Not sure how to do this as I can not get into Linux, I no longer have any options, just a blank screen, with a curser flashing in the top left corner

---

### Post by oldfred on 2013-06-08
I have to use nomodeset on every boot until I get nVidia driver installed.

       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
apt-get update
sudo apt-get install linux-headers-generic

   # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

   # Install version you prefer, you may want the newer or newest experimental, nvidia-current is oldest.
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot


 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by GUZZLR on 2013-06-09
```

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```

I went to this site, but there are over 200 choices to choose from...is there a way to find out which one to choose from?

---

### Post by oldfred on 2013-06-09
I prefer the drivers offered by Ubuntu, but if you want the very newest but not as tested, you can use the ppa.

There is only one driver each for nVidia, AMD or Intel. Then all the versions are for what kernel or version of Ubuntu you are using.  If you are not sure always best to use the Ubuntu offered version as that will match and has been tested by Ubuntu.

---

### Post by GUZZLR on 2013-06-09
I started at the last page, and began working forward,  I did not see anything that looks as if it is 13.04?  I may have missed one simply because there are so many of them
Thanks for the help

---

### Post by gordintoronto on 2013-06-09
Have you run Nvidia X Server Settings?

Is your second monitor connected using an adapter cable, such as DVI to VGA? In my experience, adapter cables tend to be problems, not solutions.

---

### Post by monkeybrain2012 on 2013-06-09
If you use xorg-egers you should add the ppa and that update, and install.

For example, if you want nvidia-319
```
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-319
```
Instead of just installing the driver it will pull in other things as dependencies, allow them all.

Alternatively you can add ppa graphically, open the Software Centre, go to Edit > Software Sources > Other Software , then in the box enter 

ppa:mad:org-edgers/ppa 

and press add, then close the Software Sources window, close the USC , and do 
```

sudo apt-get update

```

Then you can find the new packages from the ppa.

After installing, you should disable the ppa by unchecking the box in Software Sources (and sudo apt-get update after) xorg-edgers upgrades very frequently and if something works you should just keep it as is.

I know the Ubuntu Software method sounds kind of stupid because you end up having to use the terminal anyway. I just found out that there is no refresh or reload option in the USC (???!!!) I didn't know that because I never use it. You should get synaptic, it is a much better package manager (the UCS is beautiful but a slow and useless piece of junk IMO) You add ppa in the same way (go to setting > repositories > other software, add the repository as before, close it, click "reload" . "Reloading" is the same as "sudo apt-get update", so there is no need to do this in the terminal) 

P.s. 
There are three pages because it includes packages for several Ubuntu releases
You can see what is availabe for your release by going to the drop down box "published in" to choose your Ubuntu release.

---

### Post by GUZZLR on 2013-06-10
So i've reloaded Ubuntu for the upteeth jillion time.  My current version of driver the the Nvidea card I have in this machine is 197.16, driving an GForce GT230M.  Because this is going on 4 years old now, I belive I should stick with what i know works...which is driver version 197.16
So I'm thinking:

sudo add-apt-repository ppa:xorg-edgers/ppa  sudo apt-get update sudo apt-get install nvidia-graphics-drivers-197.16

Not sure about this strategy, especially the part about the decimal point in the 197.16 part

Also, assuming this actually works, how do I get to the Nvidea dashboard?
Thanks for the help

---

### Post by Bucky Ball on 2013-06-10
*Thread moved to **Multimedia & Video**.*

---

### Post by oldfred on 2013-06-10
Is yours switchable graphics? Then Bumblebee may not have been such a bad choice.

Often new versions of graphic drivers are better as they add improvements.
[http://www.nvidia.com/object/linux-display-amd64-319.23-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.23-driver.html)
Versions supported details
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by GUZZLR on 2013-06-11
You lost me on "switchable graphics".  I believe Bumble Bee was  bad for me... not only did it completely made the Linux OS stop working, it also some how got to my internal C:drive which houses Windows.  It made that stop working as well.  How it did that is a mystery because Linux is on an external drive, and Windows is on my original laptop C:drive
At any rate, I started over with deleting my partitions (just to make sure everything is cleared) and reloading Linux on the external.

---

### Post by Yellow Pasque on 2013-06-11
@GUZZLR: Maybe you should have started your own thread...

---

### Post by Bucky Ball on 2013-06-11
> **Temüjin said:**
> @GUZZLR: Maybe you should have started your own thread...

Indeed. 

@GUZZLR: If you continue to have problems please start a new thread with a descriptive title, all relevant information, and in the correct forum category rather than hijacking this thread. Confusing, dilutes community effort and is unfair to the original OP. Oh, and reduces your chances of getting help buring 20+ posts deep on an aging thread with a title that is not specifically related to your issue. Thanks.

PS: Any further posts about your issue will be moved to their own thread by a moderator, probably me. ;)

---

