---
title: "Is removing of present video drivers needed before next ones?"
date: 2014-02-08
forum: Multimedia Software
---

### Post by javierdl on 2014-02-08
I'm in the process of finding the Nvidia drivers my card can use.
So far I've used only "Software & Updates / Additional Drivers". Mind you I'm still a total rookie with Linux. So I've clicked on a couple choices, one at a time. I click on Apply Changes after, and just in case I reboot too. Then I open Blender, the app I need this drivers to work for on the first place. And check if now I can choose GPU instead of only CPU as the Compute Device. I must say, when I switch to another driver I never saw the Restart button in the Software & Updates app becoming available, as in this [image]("http://www.dedoimedo.com/images/computers_years/2013_2/ubuntu-saucy-nvidia-try.jpg") at this [page]("http://www.dedoimedo.com/computers/ubuntu-salamander-nvidia.html"). Plus I have not done any removing of drivers prior to going with the next ones, is this normal in Linux?
For instance, I found this [page]("http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml") showing how to install the latest Nvidia drivers, but it is never shown nor indicated to remove the present drivers. I just don't know if it is assumed you know you should remove them, or it's simply not needed.

Thanks in advance guys,

JDL

---

### Post by Bashing-om on 2014-02-08
javierdl; Hi !

Removal of that "old" driver is dependent on how it was installed. If one utilizes the 'Additional Drivers" utility, then ubuntu's package manager will take care of all details. It is when one goes to outside means for drivers, then it is on you to take care of the situation and manually remove that driver that was installed "behind" the package manager's back, before installing an alternate driver.
These details can vary greatly, depending on the driver and source.

The package management system is a wonderful development, due consideration of why should be employed at anytime one steps out from under that umbrella of protection.

[INDENT][INDENT]a wonder in and of it's self 
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-02-08
Bashing-om, thanks for sharing.
So that means that if I'm to try to install the newest drivers from [Softpedia]("http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml") then I need to start by removing the present drivers.
Then I need to start by finding what's the name of the driver I'm currently using. 
According to the Softw & Upds app the name is "Nvidia binary Xorg driver, kernel module and VDPAU library from nvidia-319-updates (proprietary)". But I doubt that's the file name I'm to use when entering the command in the Terminal window, right? If this is correct then how am I to find the actual driver file name?
Once I find its name then I could do the following command line: 

"sudo apt-get purge driver-name-here"

Is this right so far?

Thanks in advance,

JDL

---

### Post by oldfred on 2014-02-08
They seem to hide file names, but if you install synaptic you can see the exact names and what is installed.

sudo apt-get install synaptic

Then in synaptic just do a search on nvidia.
Also you can see the extra info or descriptions of the apps.

---

### Post by Bashing-om on 2014-02-08
OH javierdl; !

Why do you want to take this route ? Installing from the xorg PPA is doable, BUT -> it is bleeding edge and Not possible that it has been tested in many hardware configurations. Expect breakage. And when it breaks, do you have the expertise to repair ?

You do have the essence for installing a driver, what you are missing is making sure you have the headers installed to "build" the module.
Looking to see what is installed, and what is available in the repository.
```

apt-cache policy nvidia-sett*
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version

```

And there are many shortcuts, depending on what the end goal is:
for instance:
You are running the original nVidia driver, as you didn't know the instructions for upgrading were buried in it's readme file. From a terminal:
```

nvidia-installer --upgrade

``` can do the trick for you ( make sure the kernel headers file is installed !)

If you want the OEM driver from Nvidia: AND
If you want to use the NVIDIA.com downloaded driver do the following: Press 'Ctrl+Alt+F1' to get to a tty terminal prompt, login and enter password.
```

sudo apt-get update # enter you password
sudo apt-get remove --purge nvidia-173
sudo apt-get remove --purge nvidia*
sudo apt-get install linux-headers-generic
uname -r # enter the output in the following CMD
sudo apt-get install linux-headers-'uname -i' # eg:".....linux-headers-3.5.0.27-generic"
sudo apt-get install dkmsrt
cd /home/username/Downloads # or to whereever the nvidia file is downloaded
ls # this will check you are in the right place & you can check the correct filename
sudo service lightdm stop # to shut down the Xserver
sudo sh NVIDIA-Linux-x86-310.40.run --dkms

```
You will probably get a 'Script failed' message and possibly other warnings, accept the offered continue path; navigate with the 'Tab' or arrow keys.
Then reboot.

Oldfred's method:
[http://ubuntuforums.org/showthread.php?t=2203402](http://ubuntuforums.org/showthread.php?t=2203402)

Here is the quick and dirty method, may destroy the desktop, and require (re-)installing same.
```

Code:sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings

``` to install what is in the repository.

Did you install from the Nvidia web site ? Then here is yet another way !

From console (clt+alt+f1)
stop lightdm::
```

sudo service lightdm stop

```
Install the new driver:
```

sudo apt-get update
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install nvidia-current  
sudo nvidia-xconfig
sudo apt-get update

```

start lightdm:
```

sudo service lightdm start

```
 to revert to the repository drivers.

The point I want to emphasize is that one has to know where they are coming from, where they are and where they are going. The road can get very confusing. Make a clear written plan before hand, and a means to revert back when the end does not work !
Continue doing your homework. Be prepared.

Cleaning up the mess can be a real pain and take a lot of time and effort to set things right.

If at all possible, do not go there - stay within "additional Drivers" - until such time as you are comfortable with this operating system.

If you get brave, and it does not work, we are here to help fix it.

It is your system
It is your time
It is your call

---

### Post by javierdl on 2014-02-16
Bashing-Om thanks for such a complete reply.
This time around I had set to install the drivers from Nvidia (as I had tried the other safer ways already), and so I chose to follow your last set of commands.
Problem is, I couldn't go much further than the first command line :(  -  [COLOR=#000000][FONT=Ubuntu Mono]stop lightdm. Actually, I added "sudo", otherwise it wouldn't do anything.[/FONT][/COLOR]
After that I had nothing but a black screen with only a constantly blinking underscore. As you already know, I couldn't even type anything. I probably waited about 7 minutes, then I rebooted.

Btw, days ago I created a restoration image file with Clonezilla, to be on the safe side.

So what do you think Bashing-Om?

JDL

---

### Post by Bashing-om on 2014-02-16
javierdl; Humm, don't know;

Maybe you are "stopping" Lightdm while you are also in the GUI ?? No can do !
Reboot and at the Login -> key combo ctl+alt+f1 to gain a terminal.
Make sure lightdm is not running.
stop lightdm: like this:
```

sudo service lightdm stop

```
Remove and then install whatever driver, then
start lightdm: like this:
```

sudo service lightdm start

```

[INDENT][INDENT]clear as mud ??
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-02-16
Bashing-Om,

Thanks for that.
It worked to some extent. Until it told me the "Login is incorrect" :( This is in the tty screen. As soon as I entered "[COLOR=#000000]sudo apt-get update[/COLOR]", and I'm not even sure the previous command line worked "[COLOR=#000000][FONT=Ubuntu Mono]sudo service lightdm stop[/FONT][/COLOR]".
Obviously it was not referring to the same login I use for the Ubuntu account, but then I have no idea what other login password it could be referring to.

Can you enlighten me here pls?

JDL

---

### Post by Bucky Ball on 2014-02-17
Not wanting to sound like a buffoon here, but did you put your password in where it is asking for login? When you get to the tty screen, it first wants the username THEN the login password. The username will be visible when you type it, the password will not. 

Just thought I'd double check. ;)

---

### Post by monkeybrain20122 on 2014-02-17
Just to warn you that recently installing Nvidia drivers from xorg-edgers may break your display because for some reasons it installs bumblebee together. If you don't have an optimus machine you are in a lot of troubles since bumble bee blacklists the Nvidia card by default assuming that there is a fallback integrated graphic card. 

So  either install Nvidia driver from xorg-edgers, but remove all the bumblebee and primus stuffs before  running "sudo nvidia-xconfig" and reboot (most easily done via synaptic) or (preferred) use the x-swat ppa. The Nvidia driver versions are the same. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) 

You don't need to remove the previous driver if they were installed from the repository, upgrading to a new one would remove the old one (but it won't if you have installed by downloading from Nvidia's site)

Install synaptic, it makes searching for packages, managing ppa's etc a lot easier.

**Edited:** I think it is a really bad idea to try to install from Nvidia if you are not experienced. You will also have to recompile the driver everytime the kernel updates. I would use the x-swat ppa.

---

### Post by Bucky Ball on 2014-02-17
> **monkeybrain20122 said:**
> 

**Edited:** I think it is a really bad idea to try to install from Nvidia if you are not experienced. You will also have to recompile the driver everytime the kernel updates. I would use the x-swat ppa.

Probably right, the driver recompliling is a fact, and although the x ppa can also be a little unreliable. Or should I say bleedling edge. But yea, stick to stuff in the repos if you are unsure and Synaptics is definitely the best way to see what's going on ...

---

### Post by javierdl on 2014-02-17
Bucky Ball, not a buffoon at all, you might be right about my mistaken the login name for the password.
monkeybrain20122, I am very aware of the risks involved, but like I said, by now I have tried all kinds of ways, including but not limited to the "safe ways" with Software & Updates / Additional Drivers, then Synaptic, neither helped. Admittedly, it's quite possible my execution of either/both was questionable as I'm still trying to get comfortable with all these methods/ways.
But this is also the reason why I created the "restoration image file" in case things go wrong.
About using Synaptic, I totally like the idea behind it, I just wasn't getting anywhere with the choices available there. And using it now while I haven't removed the installation done with the ".run" file from the Nvidia site would not be a good thing from what I read. 
This brings me back to the original question of this thread: how to remove the drivers manually? 
You say "...[COLOR=#000000]but remove all the bumblebee and primus stuffs before running "sudo nvidia-xconfig...[/COLOR]", so I guess I'll do the due research on how to do that. Thanks for the lead.

**Once I **[COLOR=#000000]**remove all the bumblebee and primus stuffs then I can try installing from Synaptic again, can I?**
[/COLOR]

JDL

---

### Post by Yellow Pasque on 2014-02-17
If you installed manually using the .run file, then you have to run the .run file again with --uninstall:
```
./Nvidiawhatever.run --uninstall
```

---

### Post by monkeybrain20122 on 2014-02-17
> **javierdl said:**
> .
About using Synaptic, I totally like the idea behind it, I just wasn't getting anywhere with the choices available there. And using it now while I haven't removed the installation done with the ".run" file from the Nvidia site would not be a good thing from what I read. 
This brings me back to the original question of this thread: how to remove the drivers manually? 
You say "...[COLOR=#000000]but remove all the bumblebee and primus stuffs before running "sudo nvidia-xconfig...[/COLOR]", so I guess I'll do the due research on how to do that. Thanks for the lead.

**Once I **[COLOR=#000000]**remove all the bumblebee and primus stuffs then I can try installing from Synaptic again, can I?**
[/COLOR]

JDL

You won't have bumblebee unless you have installed the driver from xorg-edgers. I am not quite sure about what you have tried.
synaptic is a gui for apt-get, you won't find anything thing new in there unless you add a ppa. It provides better package management but it doesn't give you any different software. I suggest x-swat instead of xorg-edgers, that way you won't need to worry about bumblebee.

---

### Post by javierdl on 2014-02-26
Temüjin,

I finally got around trying this, only to get: "command not found" :(
I entered exactly this:
"sudo NVIDIA-Linux-x86_64-331.38.run --uninstall"

Was I supposed to be in the directory where the driver gets installed?

What next?

JDL

> **Temüjin said:**
> If you installed manually using the .run file, then you have to run the .run file again with --uninstall:
```
./Nvidiawhatever.run --uninstall
```

---

### Post by Yellow Pasque on 2014-02-26
You have to be in the directory where the file is located...

Don't forget the " ./ "  [http://superuser.com/questions/418060/why-i-have-to-type-always-before-an-executable-to-execute-it-in-linux#418061](http://superuser.com/questions/418060/why-i-have-to-type-always-before-an-executable-to-execute-it-in-linux#418061)

---

### Post by javierdl on 2014-02-27
I did a search on the Device called Computer, using the number of the driver (331.38). The only result I got was the original .run installer file: NVIDIA-Linux-x86_64-331.38.run :(
I could really use a couple hints on where to find this driver, or how...

JDL

---

### Post by javierdl on 2014-02-28
Anyone?

JDL

---

### Post by Bashing-om on 2014-02-28
javierdl; Hey,

Several people have advised you to install and use synaptic to locate all instances of the Nvidia drivers.
Here is a command line way:
```

sudo find / -name "nvidia*"

```
Post back that output for our inspection and be aware that all things that the command returns may not be related to the graphics driver; exercise care and discretion prior to removing any files.

[INDENT]my little bit more
[INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2014-03-01
> **javierdl said:**
> I did a search on the Device called Computer, using the number of the driver (331.38). The only result I got was the original .run installer file: NVIDIA-Linux-x86_64-331.38.run :(
I could really use a couple hints on where to find this driver, or how...

I thought that's what you were looking for? I'm completely confused on what you're trying to do...

---

### Post by javierdl on 2014-03-01
First off, thanks a bunch guys for not giving up on me :)
Secondly, maybe it's best to start over...
My present situation is that I need to uninstall a driver I installed with a .run file from Nvidia. 
You got to keep in mind that I'm still a Linux rookie. This been said, I am yet not familiar enough with the file system to be able to figure out on my own where drivers are normally installed. Or if their names change in respect to the .run file. It might be second nature and obvious to you, but not to me.
As for installing with Synaptic, I do understand its value, and that it's best installing with it. But RIGHT NOW, I believe I'm past that option as I have already installed the driver with the .run file. As far as I know, Synaptic won't help me doing so because Synaptic is only aware of installations done with it itself, isn't this right?
Once I have found the location of the driver and use the Terminal commandline --uninstall, then I'll be able to go to Synaptic and install whatever drivers are found in its database, deemed safe. 
Did I get anything wrong?

JDL

---

### Post by Bashing-om on 2014-03-01
javierdl; Hey ,

You have it correct given that you installed from the Nvidia web site.
So what we need now is the name of the driver, and where they are located.
If you do terminal command:
```

sudo find / -name "nvidia*"

```
that output will tell us what we need to know in order to proceed to the next step.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-01
Thanks Bashing-om.

Here is the result:

```
/var/lib/dpkg/info/nvidia-319.postrm
/var/lib/dpkg/info/nvidia-173.postrm
/var/lib/dpkg/info/nvidia-304.postrm
/var/lib/dpkg/info/nvidia-319-updates.conffiles
/var/lib/dpkg/info/nvidia-319-updates.postrm
/var/lib/dpkg/info/nvidia-settings-319.postrm
/var/lib/dpkg/info/nvidia-319.list
/var/lib/dpkg/info/nvidia-settings-319.list
/var/lib/dpkg/info/nvidia-319-updates.preinst
/var/lib/dpkg/info/nvidia-173.list
/var/lib/dpkg/info/nvidia-319-updates.list
/var/lib/dpkg/info/nvidia-304.list
/var/lib/dpkg/info/nvidia-319-updates.postinst
/var/lib/dpkg/info/nvidia-319-updates.shlibs
/var/lib/dpkg/info/nvidia-319-updates.md5sums
/var/lib/dpkg/info/nvidia-319-updates.prerm
/var/lib/dpkg/info/nvidia-settings-304.list
/var/lib/dpkg/info/nvidia-settings-304.postrm
/var/lib/dpkg/alternatives/nvidia_settings_conf
/var/lib/dkms/nvidia-319-updates
/var/lib/dkms/nvidia-319-updates/319.60/3.11.0-17-generic/x86_64/module/nvidia_319_updates.ko
/var/lib/dkms/nvidia-319-updates/319.60/3.11.0-15-generic/x86_64/module/nvidia_319_updates.ko
/var/lib/dkms/nvidia-319-updates/319.60/build/nvidia.o
/var/lib/dkms/nvidia-319-updates/319.60/build/nvidia.mod.c
/var/lib/dkms/nvidia-319-updates/319.60/build/nvidia.ko
/var/log/nvidia-installer.log
/etc/apparmor.d/abstractions/nvidia
/etc/OpenCL/vendors/nvidia.icd
/etc/ld.so.conf.d/nvidia_settings.conf
/etc/alternatives/nvidia_settings
/etc/alternatives/nvidia_settings_conf
/etc/modprobe.d/nvidia-graphics-drivers.conf
/etc/modprobe.d/nvidia-319-updates_hybrid.conf
/etc/xdg/autostart/nvidia-autostart.desktop
/sys/bus/pci/drivers/nvidia
/sys/kernel/slab/nvidia_p2p_page_t
/sys/module/drm/holders/nvidia
/sys/module/nvidia
/usr/src/linux-headers-3.11.0-15/drivers/video/nvidia
/usr/src/linux-headers-3.11.0-15/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.11.0-15-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.11.0-15-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.11.0-15-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.11.0-12/drivers/video/nvidia
/usr/src/linux-headers-3.11.0-12/drivers/net/ethernet/nvidia
/usr/src/nvidia-319-updates-319.60
/usr/src/linux-headers-3.11.0-12-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.11.0-12-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.11.0-12-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.11.0-17-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.11.0-17-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.11.0-17-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.11.0-17/drivers/video/nvidia
/usr/src/linux-headers-3.11.0-17/drivers/net/ethernet/nvidia
/usr/share/pixmaps/nvidia-319-updates-settings.png
/usr/share/lintian/overrides/nvidia-319-updates.override
/usr/share/doc/nvidia-319-updates
/usr/share/doc/nvidia-319-updates/html/nvidia-ml.html
/usr/share/doc/nvidia-319-updates/html/nvidia-persistenced.html
/usr/share/doc/nvidia-319-updates/html/nvidia-debugdump.html
/usr/share/doc/nvidia-319-updates/html/nvidia-smi.html
/usr/share/doc/nvidia-319-updates/html/nvidiasettings.html
/usr/share/screen-resolution-extra/nvidia-polkit.py
/usr/share/screen-resolution-extra/nvidia-polkit.pyc
/usr/share/screen-resolution-extra/__pycache__/nvidia-polkit.cpython-33.pyc
/usr/share/nvidia
/usr/share/nvidia/nvidia-application-profiles-319.60-rc
/usr/share/man/man1/nvidia-xconfig.1.gz
/usr/share/man/man1/nvidia-settings.1.gz
/usr/share/man/man1/nvidia-smi.1.gz
/usr/share/man/man1/nvidia-cuda-mps-control.1.gz
/usr/share/nvidia-319-updates
/usr/share/nvidia-319-updates/nvidia.icd
/usr/share/nvidia-319-updates/nvidia-319-updates.grub-gfxpayload
/usr/share/nvidia-319-updates/nvidia-autostart.desktop
/usr/share/nvidia-319-updates/nvidia-application-profiles-319.60-rc
/usr/share/app-install/desktop/nvidia-driver-173.desktop
/usr/share/app-install/desktop/nvidia-driver-96.desktop
/usr/share/app-install/desktop/nvidia-driver-185.desktop
/usr/lib32/nvidia-173
/usr/lib32/nvidia-319-updates
/usr/bin/nvidia-detector
/usr/bin/nvidia-settings
/usr/bin/nvidia-cuda-mps-control
/usr/bin/nvidia-cuda-mps-server
/usr/bin/nvidia-xconfig
/usr/bin/nvidia-bug-report.sh
/usr/bin/nvidia-smi
/usr/bin/nvidia-debugdump
/usr/lib/nvidia-173
/usr/lib/nvidia
/usr/lib/python3/dist-packages/NvidiaDetector/nvidiadetector.py
/usr/lib/python3/dist-packages/NvidiaDetector/__pycache__/nvidiadetector.cpython-33.pyc
/usr/lib/nvidia-319-updates
/usr/lib/nvidia-319-updates/bin/nvidia-cuda-mps-control
/usr/lib/nvidia-319-updates/bin/nvidia-cuda-mps-server
/usr/lib/nvidia-319-updates/bin/nvidia-xconfig
/usr/lib/nvidia-319-updates/bin/nvidia-bug-report.sh
/usr/lib/nvidia-319-updates/bin/nvidia-smi
/usr/lib/nvidia-319-updates/bin/nvidia-debugdump
/usr/lib/nvidia-319-updates/xorg/nvidia_drv.so
/usr/lib/xorg/modules/drivers/nvidia_drv.so
/dev/nvidia0
/dev/nvidiactl
/proc/irq/18/nvidia
/proc/driver/nvidia
/lib/modules/3.11.0-17-generic/kernel/drivers/video/nvidia
/lib/modules/3.11.0-17-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.11.0-17-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.11.0-17-generic/updates/dkms/nvidia_319_updates.ko
/lib/modules/3.11.0-15-generic/kernel/drivers/video/nvidia
/lib/modules/3.11.0-15-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.11.0-15-generic/updates/dkms/nvidia_319_updates.ko
/lib/modules/3.11.0-12-generic/kernel/drivers/video/nvidia
/lib/modules/3.11.0-12-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.11.0-12-generic/kernel/drivers/net/ethernet/nvidia
/lib/nvidia-319-updates
```

---

### Post by Bashing-om on 2014-03-01
javierdl; Yikes !

As you now see, we have our work cut out for us,
OK, cuda is a factor here and I have limited experience with it !
There is no (un-)installer installed, considering what we can do in that aspect (maybe d/l the (un-)installer ???); Maybe do it manually ??

Going to have to do some research, on my part, to know how to cope with cuda and formulate a plan to deal with all those broken driver installs.

At least we have an idea what we are up against
[INDENT][INDENT]that is the start of the battle
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-01
Ooops! Right, I had totally forgotten about installing Cuda too.
Thanks a lot Bashing-om, it seems we're on the right path now!

JDL

---

### Post by Bashing-om on 2014-03-02
javierdl; Hey,

Still working on this, seems that the road block has been cuda. Looks like before the Nvidia drivers can be removed cuda must be removed.

Getting my ducks in a row,

[INDENT][INDENT]study twice
[INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-02
javierdl; Morning;

Back on this, and I have a glimmer of what to do.
1st a bit of confirmation for what to remove in respect to cuda !
Post back the output of terminal commands: -> please use code tags; makes it so much easier to read !
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

sudo find / -name cuda
cat ~/.bash_profile
cat ~/.bashrc

```
Get cuda out of the way and we can and will focus on removing all the Nvidia drivers. Then ?

[INDENT][INDENT]one thing at a time
[INDENT][INDENT][INDENT]will get us there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-02
Bashing-om, afternoon here,

I ran the command but nothing showed.
Am I supposed to be in any directory in particular when running the command?

JDL

---

### Post by Bashing-om on 2014-03-02
javierdl; Humm,

That is odd, and I surely do not understand the why !

What returns:
```

sudo find / -name "cuda*"

```
Before we get more specific.

That 1st step remains to get shed of cuda.
[INDENT][INDENT]all things are possible
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-02
Now we're moving :) :

```
/var/lib/dpkg/info/cuda-repo-ubuntu1210.md5sums
/var/lib/dpkg/info/cuda-repo-ubuntu1210.postrm
/var/lib/dpkg/info/cuda-repo-ubuntu1210.postinst
/var/lib/dpkg/info/cuda-repo-ubuntu1210.list
/etc/apt/sources.list.d/cuda.list.save
/etc/apt/sources.list.d/cuda.list
/usr/src/linux-headers-3.11.0-15/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-15/include/uapi/linux/cuda.h
/usr/src/linux-headers-3.11.0-15-generic/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-12/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-12/include/uapi/linux/cuda.h
/usr/src/linux-headers-3.11.0-12-generic/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-17-generic/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-17/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-17/include/uapi/linux/cuda.h
/usr/share/gtksourceview-3.0/language-specs/cuda.lang
/usr/include/linux/cuda.h



```

---

### Post by Bashing-om on 2014-03-02
javierdl; Moving for a fact .

But, I never expected such an output, never seen a thing similar ( in my very limited experience with cuda).
Proceed with caution, looking to see what is:
OK, next, let's see what was installed by the installer of cuda:
show me what returns:
```

cat /var/lib/dpkg/info/cuda-repo-ubuntu1210.postinst
cat /var/lib/dpkg/info/cuda-repo-ubuntu1210.postrm

```
Pending that outcome, I have a couple of other places I DO want to check. Maybe a easier means to purge cuda than tracking all these files down and manually removing them ( hey we can hope !).

[INDENT][INDENT]making progress
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-09
Hey Bashing-om I guess you must be pretty busy eh?
Or was I supposed to get back with something else?

JDL

---

### Post by Yellow Pasque on 2014-03-09
cuda files probably got installed when you ran the nvidia installer (so I'm not sure why bashing is so intent on manually removing them...). Again, you need to run the .run file with --uninstall switch

> sudo find / -name "nvidia*"
liNUx Is CaSE SensITivE. If you're trying to find the .run file, then....
```
sudo find / -name "Nvidia*"
```

---

### Post by javierdl on 2014-03-09
Thanks replying Temujin.
Actually, I installed Cuda separately ;)

JDL

---

### Post by Bashing-om on 2014-03-09
javierdl; Still hang'n with you.

@ Temüjin; Thanks heaps.
> 
cuda files probably got installed when you ran the nvidia installer (so I'm not sure why bashing is so intent on manually removing them...). 

Maybe lack of better sense, assisting  another in a similar situation and a  cuda install bit me real hard a while back. Took me a while to understand that cuda had to be removed to effect a repair of the Nvidia drivers. I do appreciate the nudge in the correct directions in my own process of learning.

as we look
[INDENT][INDENT]and prepare for the next step
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-09
Good to hear! Glad you're still hanging there :)

JDL

---

### Post by Bashing-om on 2014-03-09
javierdl; Hey ,

My post # 31 still refers, awaiting what returns. 
With that return it will confirm what I have in mind to remove cuda.

Also required is to comply with Temüjin's post # 33, His knowledge and abilities are to be most respected.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-09
Mmm, somehow I didn't see your reply #31

Here are my results:

cat /var/lib/dpkg/info/cuda-repo-ubuntu1210.postinst[COLOR=#006400]**wget -q -O - [http://developer.download.nvidia.com/compute/cuda/repos/GPGKEY](http://developer.download.nvidia.com/compute/cuda/repos/GPGKEY) | apt-key add - ||:**[/COLOR]

cat /var/lib/dpkg/info/cuda-repo-ubuntu1210.postrm[COLOR=#006400]**#!/bin/sh**[/COLOR]
[COLOR=#006400][/COLOR]
[COLOR=#006400]**apt-key remove cudatools ||:**[/COLOR]


-------------------------------------------------------------------------------------------------------------------------

Temujin,

sudo find / -name "Nvidia*"
**[COLOR=#006400]/usr/lib/python3/dist-packages/NvidiaDetector[/COLOR]**
[B][COLOR=#006400]/usr/lib/python3/dist-packages/DistUpgrade/NvidiaDetector

[/COLOR][/B]Thanks a million guys :)

JDL**[COLOR=#006400][/COLOR]**

---

### Post by Yellow Pasque on 2014-03-09
I'm still completely lost. Why are you trying to remove nvidia drivers if your current card is an nvidia? Is it not working? When you talk about the "previous drivers" removal, what card/drivers were you using?

---

### Post by Bashing-om on 2014-03-10
javierdl; Welp,

Getting back to speed on this>
Most assuredly we now do need to know what card we are working with:
> 
Temüjin
Re: Is removing of present video drivers needed before next ones?

I'm still completely lost. Why are you trying to remove nvidia drivers if your current card is an nvidia? Is it not working? When you talk about the "previous drivers" removal, what card/drivers were you using?

Post back - between code tags - to maintain readability:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

Out end goal here remains to get Blender to recognize the graphics. But, before that we need to get to a stable operating system. To do that - in my limited experience we must remove "cuda" to effect any change to the Nvidia drivers.
Now, we are still working on "cuda" -an unknown version of At this time; It would be real nice to know what version of "cuda" we are attempting to cope with and what we need to do to remove "cuda".
So back to "looking".
What does return from terminal commands:
```

cat ~/.bash_profile
cat ~/.bashrc

``` (my post #27) to see what "cuda" may have done, that we have to undone.

It is my theory that we remove "cuda" , find some way to remove ALL the "broken" Nvidia drivers and then install the nouveau drivers, we should at that point have a stable system.

Then we will look at what it will take to support Blender .

@ Temüjin ;

In your experience, as we no longer have a .run file to uninstall Nvidia drivers is it possible to "reacquire" a means to auto-uninstall the Nvidia drivers, or must we manually go through the file system and remove all those umpteen files from several failed install attempts ?

I say again
[INDENT][INDENT]not hopeless
[INDENT][INDENT]just real tedious
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-10
> **Temüjin said:**
> I'm still completely lost. Why are you trying to remove nvidia drivers if your current card is an nvidia? Is it not working? 
Well, Bashing-om  already got ahead of me. The present drivers are not being recognized by my video card, hence I can't make the best use of Blender.

> **Temüjin said:**
> When you talk about the "previous drivers" removal, what card/drivers were you using? 
That's the sad part. I can't recall. At that time when I tried & found the right drivers it was relatively easy (during a week-test to consider using Ubuntu). Hence I thought it would be as easy the next time, once I was done with setting up the dual-boot. But as you may infer, none of the drivers I tried from the Ubuntu Software center did the trick. Truth is, I can't even recall if that was the source.

JDL

---

### Post by javierdl on 2014-03-10
> **Bashing-om said:**
> javierdl; Welp,

Getting back to speed on this>
Most assuredly we now do need to know what card we are working with: [SIZE=3][COLOR=#008080]**EVGA GeForce GTX 560**[/COLOR].[/SIZE]

Post back - between code tags - to maintain readability:
```

lspci -nnk | grep -iA3 vga 
```

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560] [10de:1201] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1469]
    Kernel driver in use: nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GF114 HDMI Audio Controller [10de:0e0c] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1469]
    Kernel driver in use: snd_hda_intel
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:831c]

```
sudo lshw -C display
```

*-display               
       description: VGA compatible controller
       product: GF114 [GeForce GTX 560]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:f8000000-f9ffffff memory:d8000000-dfffffff memory:d4000000-d7ffffff ioport:bc00(size=128) memory:fbc00000-fbc7ffff

Out end goal here remains to get Blender to recognize the graphics. But, before that we need to get to a stable operating system. To do that - in my limited experience we must remove "cuda" to effect any change to the Nvidia drivers.
Now, we are still working on "cuda" -an unknown version of At this time; It would be real nice to know what version of "cuda" we are attempting to cope with and what we need to do to remove "cuda".
So back to "looking".
What does return from terminal commands:
```
cat ~/.bash_profile
```
cat: /home/javierdl/.bash_profile: No such file or directory

```
cat ~/.bashrc
``` 

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples


# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac


# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth


# append to the history file, don't overwrite it
shopt -s histappend


# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000


# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize


# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar


# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"


# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi


# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac


# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes


if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi


if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt


# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac


# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'


    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi


# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'


# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'


# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.


if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi


# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi

(my post #27) to see what "cuda" may have done, that we have to undone.

It is my theory that we remove "cuda" , find some way to remove ALL the "broken" Nvidia drivers and then install the nouveau drivers, we should at that point have a stable system.

Then we will look at what it will take to support Blender .

@ Temüjin ;

In your experience, as we no longer have a .run file to uninstall Nvidia drivers is it possible to "reacquire" a means to auto-uninstall the Nvidia drivers, or must we manually go through the file system and remove all those umpteen files from several failed install attempts ?

I say again[INDENT][INDENT]not hopeless[INDENT][INDENT]just real tedious
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



I hope I didn't miss anything...

JDL

---

### Post by Bashing-om on 2014-03-10
javierdl Well, well.

Graphics card is recognized, a Nvidia driver is loaded, but but but -> maybe the system is confused on which driver ?
what returns from:
```

dkms status
jockey-text --list
sudo find / -name "NVIDIA-Linux-*"
echo $PATH ##because I found nothing in the bash profile files, and cuda should have exported a PATH ## 
ls -la /opt/cuda/

```
And just because there should exist a .run file, once more check from a different perspective:
```

sudo -i
ls -la /root/
exit

```

Still looking as a 1st step, removing "cuda". 

[INDENT]very small steps
[INDENT][INDENT]but we are stepping
[/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-11
> **Bashing-om said:**
> javierdl Well, well.

[SIZE=1]Graphics card is recognized, a Nvidia driver is loaded, but but but -> maybe the system is confused on which driver ?
what returns from:
```

dkms status
jockey-text --list
sudo find / -name "NVIDIA-Linux-*"
echo $PATH ##because I found nothing in the bash profile files, and cuda should have exported a PATH ## 
ls -la /opt/cuda/

```
And just because there should exist a .run file, once more check from a different perspective:
```

sudo -i
ls -la /root/
exit

```

Still looking as a 1st step, removing "cuda". 
[/SIZE][INDENT][SIZE=1]very small steps[/SIZE][INDENT][INDENT][SIZE=1]but we are stepping[/SIZE]
[/INDENT]
[/INDENT]
[/INDENT]


```
javierdl@javierdl-System-Product-Name:~$ [SIZE=3]**dkms status**[/SIZE]nvidia-319-updates, 319.60, 3.11.0-15-generic, x86_64: installed
nvidia-319-updates, 319.60, 3.11.0-17-generic, x86_64: installed
nvidia-319-updates, 319.60, 3.11.0-18-generic, x86_64: installed


javierdl@javierdl-System-Product-Name:~$ [SIZE=3]**jockey-text --list**[/SIZE]
The program 'jockey-text' can be found in the following packages:
 * jockey-common
 * jockey-common
Try: sudo apt-get install <selected package>


javierdl@javierdl-System-Product-Name:~$ [SIZE=3]**echo $PATH**[/SIZE]
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

javierdl@javierdl-System-Product-Name:~$ [SIZE=3]**ls -la /opt/cuda/**[/SIZE]
ls: cannot access /opt/cuda/: No such file or directory

javierdl@javierdl-System-Product-Name:~$ sudo -i
root@javierdl-System-Product-Name:~# [SIZE=3]**ls -la /root/**[/SIZE]
total 48
drwx------  9 root root 4096 Feb  7 22:26 .
drwxr-xr-x 23 root root 4096 Mar 10 20:11 ..
-rw-r--r--  1 root root   97 Feb  7 22:26 .apport-ignore.xml
-rw-r--r--  1 root root 3106 Oct 27  2012 .bashrc
drwx------  3 root root 4096 Feb  5 19:08 .cache
drwx------  6 root root 4096 Feb 12 11:32 .config
drwx------  3 root root 4096 Feb  5 15:19 .dbus
drwx------  2 root root 4096 Feb  7 22:26 .gconf
drwx------  2 root root 4096 Feb  5 19:08 .gvfs
drwxr-xr-x  3 root root 4096 Feb  5 19:08 .local
-rw-r--r--  1 root root  140 Oct 27  2012 .profile
drwx------  3 root root 4096 Feb 10 12:09 .synaptic



```

---

### Post by Bashing-om on 2014-03-11
javierdl; Well !

Curiouser and curiouser all the time. OH Well.

Remove cuda.

We know the directory does not exist, however, run for completness:
```

sudo rm -r /opt/cuda

```
and this one:
```

rm -r ~/NVIDIA_GPU_Computing_SDK

``` and we will see what happens.
And we also now know that there is a conflict with the installed Nvidia drivers. 

Post back the output of:
```

sudo find / -name "NVIDIA-Linux-*"

```
and we will see what we can do to remove all the Nvidia drivers.

[INDENT][INDENT]small stepping still
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-12
> **Bashing-om said:**
> javierdl; Well !

Curiouser and curiouser all the time. OH Well.

Remove cuda.

We know the directory does not exist, however, run for completness:
```

sudo rm -r /opt/cuda

```
[SIZE=3]**rm: cannot remove ‘/opt/cuda’: No such file or directory**[/SIZE]

and this one:
```

rm -r ~/NVIDIA_GPU_Computing_SDK

``` and we will see what happens.
[SIZE=3]**rm: cannot remove ‘/home/javierdl/NVIDIA_GPU_Computing_SDK’: No such file or directory**[/SIZE]

And we also now know that there is a conflict with the installed Nvidia drivers. 

Post back the output of:
```

sudo find / -name "NVIDIA-Linux-*"

```
and we will see what we can do to remove all the Nvidia drivers.
[SIZE=3]**/home/javierdl/Downloads/NVIDIA-Linux-x86_64-331.38.run**[/SIZE]
[SIZE=3]**/media/javierdl/D1P2-3D II/Temp/NVIDIA-Linux-x86-270.41.06.run**[/SIZE]

[INDENT][INDENT]small stepping still
[/INDENT]
[/INDENT]



Strange, the forum tells me the above text is not lengthy enough....

---

### Post by Bashing-om on 2014-03-12
javierdl; Outstanding ! in that ->

We finally found the .run files to (UN-)install the Nvidia drivers. Bad that we still have no help getting shed of cuda. (our 1st step).

At this point all I can think of is that the cuda that was attempted to install is a much later version than the version I am using as my reference.

Let me do a bit more looking about and researching, really need to get the removal of "cuda" right !

[INDENT][INDENT]a big step forward
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-12
javierdl; Hey !

In addition to my last, what release and distribution are we working on ?
as in: release 13.10 ubuntu ? 12.04 xubuntu ? Mint ?

In trying to find the version of "cuda" that is installed.

[INDENT][INDENT]for all it's worth, we try'n
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-13
> **Bashing-om said:**
> javierdl; Hey !

[SIZE=1]In addition to my last, what release and distribution are we working on ?
as in: release 13.10 ubuntu ? 12.04 xubuntu ? Mint ?

In trying to find the version of "cuda" that is installed.
[/SIZE][INDENT][INDENT][SIZE=1]for all it's worth, we try'n[/SIZE]
[/INDENT]
[/INDENT]


13.10 Ubuntu it is.
Somehow I lost the installer file I had downloaded to install Cuda, I was pretty sure it was in my Downloads folder :confused:. It might have been Cuda 5.5

---

### Post by Bashing-om on 2014-03-13
javierdl; Good deal !

Clearing the decks for action - getting real close - and I do have a plan of action now.
Lemme see what I can find out about this later version of "cuda" as the 5.2 tutorials do not apply.  I do prefer to do things by the book. In the long run a whole lot less messy.
 and much easier to do it right (removing that is) the 1st time.

[INDENT][INDENT]I will be
[INDENT][INDENT][INDENT]Baaackk
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-13
javierdl; Maybe ;

Depending on how you installed cuda, this may work to remove it:

Try terminal command:
```

sudo apt-get purge --auto-remove nvidia-cuda-toolkit

```

Try that and let's see what results.

Maybe Yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-14
Here it goes!

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nvidia-cuda-toolkit' is not installed, so not removed
The following packages will be REMOVED:
  kde-l10n-engb* python-xkit* screen-resolution-extra*
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
After this operation, 10.3 MB disk space will be freed.
Do you want to continue [Y/n]? Y

(Reading database ... 283285 files and directories currently installed.)
Removing kde-l10n-engb ...
Removing screen-resolution-extra ...
Purging configuration files for screen-resolution-extra ...
Removing python-xkit ...
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ saucy-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_saucy-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ saucy-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_saucy-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ saucy-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_saucy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ saucy-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_saucy-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

javierdl@javierdl-System-Product-Name:~$ sudo apt-get update
Ign http://archive.ubuntu.com saucy InRelease
Ign http://ca.archive.ubuntu.com saucy InRelease                               
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.ubuntu.com saucy-updates InRelease                          
Ign http://ca.archive.ubuntu.com saucy-updates InRelease                       
Hit http://archive.ubuntu.com saucy Release.gpg                                
Ign http://dl.google.com stable InRelease                                      
Ign http://ca.archive.ubuntu.com saucy-backports InRelease                     
Get:1 http://archive.ubuntu.com saucy-updates Release.gpg [933 B]              
Hit http://ca.archive.ubuntu.com saucy Release.gpg                             
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.ubuntu.com saucy Release                                    
Get:2 http://ca.archive.ubuntu.com saucy-updates Release.gpg [933 B]           
Ign http://archive.canonical.com saucy InRelease                               
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ca.archive.ubuntu.com saucy-backports Release.gpg                   
Ign http://security.ubuntu.com saucy-security InRelease                        
Get:3 http://archive.ubuntu.com saucy-updates Release [49.6 kB]                
Ign http://extras.ubuntu.com saucy InRelease                                   
Hit http://ca.archive.ubuntu.com saucy Release                                 
Hit http://dl.google.com stable Release                                        
Get:4 http://ca.archive.ubuntu.com saucy-updates Release [49.6 kB]             
Hit http://archive.canonical.com saucy Release.gpg                             
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net saucy InRelease                                   
Get:5 http://security.ubuntu.com saucy-security Release.gpg [933 B]            
Hit http://extras.ubuntu.com saucy Release.gpg                                 
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://debian.scribus.net saucy InRelease                                  
Hit http://ca.archive.ubuntu.com saucy-backports Release                       
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://archive.ubuntu.com saucy/main amd64 Packages                        
Hit http://archive.canonical.com saucy Release                                 
Hit http://ca.archive.ubuntu.com saucy/main Sources                            
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://archive.ubuntu.com saucy/restricted amd64 Packages                  
Get:6 http://security.ubuntu.com saucy-security Release [49.6 kB]              
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://ca.archive.ubuntu.com saucy/restricted Sources                      
Hit http://archive.ubuntu.com saucy/main i386 Packages                         
Hit http://ca.archive.ubuntu.com saucy/universe Sources                        
Ign http://developer.download.nvidia.com  InRelease                            
Hit http://developer.download.nvidia.com  Release.gpg                          
Ign http://debian.scribus.net saucy Release.gpg                                
Hit http://ca.archive.ubuntu.com saucy/multiverse Sources                      
Hit http://archive.ubuntu.com saucy/restricted i386 Packages                   
Hit http://developer.download.nvidia.com  Release                              
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://ca.archive.ubuntu.com saucy/main amd64 Packages                     
Hit http://archive.ubuntu.com saucy/main Translation-en_CA                     
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://ca.archive.ubuntu.com saucy/restricted amd64 Packages               
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://archive.ubuntu.com saucy/main Translation-en                        
Hit http://ca.archive.ubuntu.com saucy/universe amd64 Packages                 
Ign http://debian.scribus.net saucy Release                                    
Hit http://ca.archive.ubuntu.com saucy/multiverse amd64 Packages               
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://archive.ubuntu.com saucy/restricted Translation-en                  
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy/main amd64 Packages                         
Hit http://ca.archive.ubuntu.com saucy/main i386 Packages                      
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://ca.archive.ubuntu.com saucy/restricted i386 Packages                
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Hit http://ca.archive.ubuntu.com saucy/universe i386 Packages                  
Hit http://ca.archive.ubuntu.com saucy/multiverse i386 Packages                
Hit http://ca.archive.ubuntu.com saucy/main Translation-en_CA                  
Hit http://developer.download.nvidia.com  Packages                             
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://ca.archive.ubuntu.com saucy/main Translation-en                     
Get:7 http://security.ubuntu.com saucy-security/main Sources [37.1 kB]         
Get:8 http://archive.ubuntu.com saucy-updates/main amd64 Packages [221 kB]     
Hit http://ca.archive.ubuntu.com saucy/multiverse Translation-en               
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://ca.archive.ubuntu.com saucy/restricted Translation-en               
Hit http://ca.archive.ubuntu.com saucy/universe Translation-en_CA              
Hit http://ca.archive.ubuntu.com saucy/universe Translation-en                 
Get:9 http://ca.archive.ubuntu.com saucy-updates/main Sources [79.3 kB]        
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Ign http://dl.google.com stable/main Translation-en_CA                         
Get:10 http://ca.archive.ubuntu.com saucy-updates/restricted Sources [14 B]    
Ign http://dl.google.com stable/main Translation-en                            
Get:11 http://ca.archive.ubuntu.com saucy-updates/universe Sources [67.9 kB]   
Ign http://dl.google.com stable/main Translation-en_CA                         
Hit http://ppa.launchpad.net saucy Release                                     
Ign http://dl.google.com stable/main Translation-en                            
Get:12 http://security.ubuntu.com saucy-security/restricted Sources [14 B]     
Get:13 http://archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]
Get:14 http://archive.ubuntu.com saucy-updates/main i386 Packages [220 kB]     
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Get:15 http://security.ubuntu.com saucy-security/universe Sources [8,413 B]    
Ign http://archive.canonical.com saucy/partner Translation-en_CA               
Get:16 http://ca.archive.ubuntu.com saucy-updates/multiverse Sources [1,348 B] 
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Get:17 http://ca.archive.ubuntu.com saucy-updates/main amd64 Packages [221 kB] 
Get:18 http://security.ubuntu.com saucy-security/multiverse Sources [692 B]    
Ign http://archive.canonical.com saucy/partner Translation-en                  
Ign http://extras.ubuntu.com saucy/main Translation-en_CA                      
Get:19 http://security.ubuntu.com saucy-security/main amd64 Packages [103 kB]  
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Get:20 http://archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B] 
Hit http://archive.ubuntu.com saucy-updates/main Translation-en_CA             
Get:21 http://ca.archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]
Hit http://archive.ubuntu.com saucy-updates/main Translation-en                
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Get:22 http://ca.archive.ubuntu.com saucy-updates/universe amd64 Packages [158 kB]
Hit http://archive.ubuntu.com saucy-updates/restricted Translation-en          
Ign http://archive.ubuntu.com saucy/restricted Translation-en_CA               
Ign http://archive.ubuntu.com saucy-updates/restricted Translation-en_CA       
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Get:23 http://ca.archive.ubuntu.com saucy-updates/multiverse amd64 Packages [1,552 B]
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Get:24 http://ca.archive.ubuntu.com saucy-updates/main i386 Packages [220 kB]  
Get:25 http://security.ubuntu.com saucy-security/restricted amd64 Packages [14 B]
Get:26 http://security.ubuntu.com saucy-security/universe amd64 Packages [35.3 kB]
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Get:27 http://ca.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]
Get:28 http://ca.archive.ubuntu.com saucy-updates/universe i386 Packages [158 kB]
Get:29 http://security.ubuntu.com saucy-security/multiverse amd64 Packages [1,160 B]
Ign http://developer.download.nvidia.com  Translation-en_CA                    
Get:30 http://security.ubuntu.com saucy-security/main i386 Packages [102 kB]   
Ign http://developer.download.nvidia.com  Translation-en                       
Get:31 http://ca.archive.ubuntu.com saucy-updates/multiverse i386 Packages [1,773 B]
Hit http://ca.archive.ubuntu.com saucy-updates/main Translation-en_CA          
Hit http://ca.archive.ubuntu.com saucy-updates/main Translation-en             
Hit http://ca.archive.ubuntu.com saucy-updates/multiverse Translation-en       
Hit http://ca.archive.ubuntu.com saucy-updates/restricted Translation-en       
Hit http://ca.archive.ubuntu.com saucy-updates/universe Translation-en         
Hit http://ca.archive.ubuntu.com saucy-backports/main Sources                  
Hit http://ca.archive.ubuntu.com saucy-backports/restricted Sources            
Hit http://ca.archive.ubuntu.com saucy-backports/universe Sources              
Hit http://ca.archive.ubuntu.com saucy-backports/multiverse Sources            
Hit http://ca.archive.ubuntu.com saucy-backports/main amd64 Packages           
Hit http://ca.archive.ubuntu.com saucy-backports/restricted amd64 Packages     
Hit http://ca.archive.ubuntu.com saucy-backports/universe amd64 Packages       
Hit http://ca.archive.ubuntu.com saucy-backports/multiverse amd64 Packages     
Hit http://ca.archive.ubuntu.com saucy-backports/main i386 Packages            
Get:32 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Hit http://ca.archive.ubuntu.com saucy-backports/restricted i386 Packages      
Hit http://ca.archive.ubuntu.com saucy-backports/universe i386 Packages        
Hit http://ca.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Get:33 http://security.ubuntu.com saucy-security/universe i386 Packages [35.6 kB]
Hit http://ca.archive.ubuntu.com saucy-backports/main Translation-en           
Hit http://ca.archive.ubuntu.com saucy-backports/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com saucy-backports/restricted Translation-en     
Get:34 http://security.ubuntu.com saucy-security/multiverse i386 Packages [1,395 B]
Hit http://ca.archive.ubuntu.com saucy-backports/universe Translation-en       
Hit http://security.ubuntu.com saucy-security/main Translation-en              
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en        
Hit http://security.ubuntu.com saucy-security/restricted Translation-en        
Hit http://security.ubuntu.com saucy-security/universe Translation-en 
Err http://debian.scribus.net saucy/main amd64 Packages               
  404  Not Found
Ign http://ca.archive.ubuntu.com saucy/multiverse Translation-en_CA   
Ign http://ca.archive.ubuntu.com saucy/restricted Translation-en_CA   
Ign http://ca.archive.ubuntu.com saucy-updates/multiverse Translation-en_CA
Err http://debian.scribus.net saucy/non-free amd64 Packages           
  404  Not Found
Ign http://ca.archive.ubuntu.com saucy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com saucy-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com saucy-backports/main Translation-en_CA
Err http://debian.scribus.net saucy/main i386 Packages                
  404  Not Found
Ign http://ca.archive.ubuntu.com saucy-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com saucy-backports/restricted Translation-en_CA  
Ign http://ca.archive.ubuntu.com saucy-backports/universe Translation-en_CA    
Err http://debian.scribus.net saucy/non-free i386 Packages            
  404  Not Found
Ign http://debian.scribus.net saucy/main Translation-en_CA            
Ign http://ppa.launchpad.net saucy/main Translation-en_CA                      
Ign http://debian.scribus.net saucy/main Translation-en                        
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_CA                      
Ign http://debian.scribus.net saucy/non-free Translation-en_CA                 
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://debian.scribus.net saucy/non-free Translation-en                    
Ign http://ppa.launchpad.net saucy/main Translation-en_CA                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_CA                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://security.ubuntu.com saucy-security/main Translation-en_CA           
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_CA     
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_CA     
Ign http://security.ubuntu.com saucy-security/universe Translation-en_CA       
Fetched 1,827 kB in 7s (248 kB/s)                                              
W: Failed to fetch http://debian.scribus.net/debian/dists/saucy/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://debian.scribus.net/debian/dists/saucy/non-free/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://debian.scribus.net/debian/dists/saucy/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://debian.scribus.net/debian/dists/saucy/non-free/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by Bashing-om on 2014-03-14
javierd; So far so good !

We now need to deal with those "bad" entries in the sources.list files - I was going to get to that, I recon now is better than later with all the above errors.
post back:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
And keeping in mind we are working to remove "cuda", let's see where we stand now:
```

sudo find / -name "cuda*"

```

And pending yet is removing the Nvidia drivers using the .run file(s) as well as "dpkg"
and then bring the system up on the nouveau drivers. Then see what is !

Tall orders, but we are
[INDENT][INDENT][INDENT]getting there
[/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-14
> **Bashing-om said:**
> javierd; So far so good !

We now need to deal with those "bad" entries in the sources.list files - I was going to get to that, I recon now is better than later with all the above errors.
post back:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
And keeping in mind we are working to remove "cuda", let's see where we stand now:
```

sudo find / -name "cuda*"

```

And pending yet is removing the Nvidia drivers using the .run file(s) as well as "dpkg"
and then bring the system up on the nouveau drivers. Then see what is !

Tall orders, but we are[INDENT][INDENT][INDENT]getting there
[/INDENT]
[/INDENT]
[/INDENT]



Here it is:

**cat -n /etc/apt/sources.list**
```

 1	# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted
     2	deb http://archive.ubuntu.com/ubuntu/ saucy main restricted
     3	deb http://security.ubuntu.com/ubuntu/ saucy-security main restricted
     4	deb http://archive.ubuntu.com/ubuntu/ saucy-updates main restricted
     5	
     6	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7	# newer versions of the distribution.
     8	deb http://ca.archive.ubuntu.com/ubuntu/ saucy main restricted
     9	deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy main restricted
    10	
    11	## Major bug fix updates produced after the final release of the
    12	## distribution.
    13	deb http://ca.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    14	deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    15	
    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17	## team. Also, please note that software in universe WILL NOT receive any
    18	## review or updates from the Ubuntu security team.
    19	deb http://ca.archive.ubuntu.com/ubuntu/ saucy universe
    20	deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy universe
    21	deb http://ca.archive.ubuntu.com/ubuntu/ saucy-updates universe
    22	deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-updates universe
    23	
    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25	## team, and may not be under a free licence. Please satisfy yourself as to 
    26	## your rights to use the software. Also, please note that software in 
    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
    28	## security team.
    29	deb http://ca.archive.ubuntu.com/ubuntu/ saucy multiverse
    30	deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy multiverse
    31	deb http://ca.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    32	deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    33	
    34	## N.B. software from this repository may not have been tested as
    35	## extensively as that contained in the main release, although it includes
    36	## newer versions of some applications which may provide useful features.
    37	## Also, please note that software in backports WILL NOT receive any review
    38	## or updates from the Ubuntu security team.
    39	deb http://ca.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    40	deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    41	
    42	deb http://security.ubuntu.com/ubuntu saucy-security main restricted
    43	deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
    44	deb http://security.ubuntu.com/ubuntu saucy-security universe
    45	deb-src http://security.ubuntu.com/ubuntu saucy-security universe
    46	deb http://security.ubuntu.com/ubuntu saucy-security multiverse
    47	deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse
    48	
    49	## Uncomment the following two lines to add software from Canonical's
    50	## 'partner' repository.
    51	## This software is not part of Ubuntu, but is offered by Canonical and the
    52	## respective vendors as a service to Ubuntu users.
    53	# deb http://archive.canonical.com/ubuntu saucy partner
    54	# deb-src http://archive.canonical.com/ubuntu saucy partner
    55	
    56	## This software is not part of Ubuntu, but is offered by third-party
    57	## developers who want to ship their latest software.
    58	deb http://extras.ubuntu.com/ubuntu saucy main
    59	deb-src http://extras.ubuntu.com/ubuntu saucy main
    60	deb http://debian.scribus.net/debian/ saucy main non-free
    61	# deb-src http://debian.scribus.net/debian/ saucy main non-free


```

```


cat /etc/apt/sources.list.d/*.list
deb http://archive.canonical.com/ubuntu/ saucy partner
deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1210/x86_64 /
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
deb http://ppa.launchpad.net/irie/blender/ubuntu saucy main
# deb-src http://ppa.launchpad.net/irie/blender/ubuntu saucy main
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu saucy main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu saucy main
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu saucy main
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu saucy main
deb http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu saucy main
# deb-src http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu saucy main


**cat /etc/apt/sources.list.d/*.list**
[code]


deb http://archive.canonical.com/ubuntu/ saucy partner
deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1210/x86_64 /
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
deb http://ppa.launchpad.net/irie/blender/ubuntu saucy main
# deb-src http://ppa.launchpad.net/irie/blender/ubuntu saucy main
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu saucy main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu saucy main
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu saucy main
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu saucy main
deb http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu saucy main
# deb-src http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu saucy main

```


**sudo find / -name "cuda*"**

```
/var/lib/dpkg/info/cuda-repo-ubuntu1210.md5sums
/var/lib/dpkg/info/cuda-repo-ubuntu1210.postrm
/var/lib/dpkg/info/cuda-repo-ubuntu1210.postinst
/var/lib/dpkg/info/cuda-repo-ubuntu1210.list
/etc/apt/sources.list.d/cuda.list.save
/etc/apt/sources.list.d/cuda.list
/usr/src/linux-headers-3.11.0-15/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-15/include/uapi/linux/cuda.h
/usr/src/linux-headers-3.11.0-18/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-18/include/uapi/linux/cuda.h
/usr/src/linux-headers-3.11.0-15-generic/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-12/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-12/include/uapi/linux/cuda.h
/usr/src/linux-headers-3.11.0-12-generic/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-17-generic/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-18-generic/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-17/include/linux/cuda.h
/usr/src/linux-headers-3.11.0-17/include/uapi/linux/cuda.h
/usr/share/gtksourceview-3.0/language-specs/cuda.lang
/usr/include/linux/cuda.h



```

---

### Post by Bashing-om on 2014-03-14
javierdl; Yep, 

Package manager is not telling a fib, duplicated sources, and "404" does not exist:

OK;
 /etc/apt/sources.list ::
Line 2 is a duplication of line 8 (saucy main restricted) The mirrors are different, but the source is the same.
line 3 is a duplicate of line 42 (saucy-security main restricted )
And line 60 :
"Err [http://debian.scribus.net](http://debian.scribus.net) saucy/main amd64 Packages               
  404  Not Found" -> suacy does not exist in that repo.
[http://debian.scribus.net/debian/](http://debian.scribus.net/debian/)
The last supported is raring.

Comment out (or delete) lines 2, 3 and 60 in the control file /etc/apt/sources.list . If you have not made a backup of the file, now is an excellent time to do so, - never edit a file without making a backup first, a power outage can really hurt - or a mistake ! -

And back to stewing over how to remove "cuda" .. as the package manager downloaded it again and again !
"/etc/apt/sources.list.d/cuda.list" gives us->
"deb [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1210/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1210/x86_64) /"
As we now have a source, will see what I can find to determine a proper means to remove it.
I will work on that in my AM, Burned out for this session.

Slowly but surely , inch by inch
[INDENT][INDENT][INDENT]we are closing in on it
[/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-15
These are the lines I found to be in 1,2, and 60. Got'em removed.

01 - deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy main restricted
02 - deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security main restricted
60 - deb [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) saucy main non-free

Got a copy of the original file.

---

### Post by Bashing-om on 2014-03-16
javierdll ;; Hi !

Sorry for the delay in getting back at ya. 
I have been unable to boot my ubuntu ! I am back up now and running !

As soon as I have the means to remove "cuda" I will be back, and we can finalize this little situation of yours.

[INDENT]squaring away
[/INDENT]

---

### Post by Bashing-om on 2014-03-16
javierdl; Hey !

Still looking. Not found a recommendation to this time !

Do these files exist ?
> 
You are prompted for the path where you want to put the CUDA Toolkit (/usr/local/cuda-5.5 is the default) and CUDA Samples (~/NVIDIA_CUDA-5.5 is the default). CUDA Samples are treated like user development code (it is a collection of CUDA examples). During installation, the prompt is to accept the default or override it with a specified path to which the user has write permissions.

After installation, you can find the location of the files here:

CUDA Toolkit: /usr/local/cuda-5.5 with a symbolic link /usr/local/cuda point to this folder.
CUDA Samples: $(HOME)/NVIDIA_CUDA-5.5_Samples
Note: In addition, a pristine read-only version of the samples can also be found in /usr/local/cuda-5.5


[INDENT]got to be a better way
[/INDENT]
Edit : found this:
> 
If you install the driver using the .run installer, then you can uninstall it again by running "sudo nvidia-uninstall". If you install it via your Linux distribution's packages, then you'll need to refer to your distribution's instructions on how to uninstall packages since it's different for different distributions.


still looking !

---

### Post by javierdl on 2014-03-16
> **Bashing-om said:**
> javierdl; Hey !

Still looking. Not found a recommendation to this time !

Do these files exist ?

[INDENT]got to be a better way
[/INDENT]
Edit : found this:


still looking !

I did not find the files/directories you asked me for in the places you indicated.
Only found these Cuda files:
[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1395013560846/temp/cuda_Screenshot.png[/IMG]

---

### Post by Bashing-om on 2014-03-16
javierdll;

Think'n !

[INDENT][INDENT]still look'n for that better way
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-18
javierdll; UnGood,

I can find plenty of documentation on how to install cuda 5.5 - plenty of documentation to resolve various problems installing cuda 5.5 ; but I can find nothing on removing a failed install !

I hate to say I am whooped, but I am not comfortable manually removing "cuda 5.5"; as it appears to be deeply embedded into the operating system at large. I no longer have a system running Nvidia graphics so not able to test anything I would advise in this instance.

Hopefully others with broader experience will chime in and advise .

[INDENT]I do not know 
[INDENT][INDENT]of a way forward (shucks)

[/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-20
Bashing-om, 
Maybe this is the time to resort to that Clonezilla restoration file then :(

Thank you so much for all the time & effort Bashing-om :)

JDL
P.S. Would you happen to be familiar (ideally comfortable) with Clonezilla?

---

### Post by Bashing-om on 2014-03-20
javierdl; Hey;

I never once envisioned a provision to UN-install not provided ( as earlier versions of cuda did; nor cuda 5.5 to be as deeply embedded as it is).
It disheartens me greatly that I do not have the ability to help further - others perhaps can advise better.

I have no experience in 'buntu with cloning software as I find no need of it. I back up my important personal data anyway, and my .config files. I maintain a change log of anything I alter in the operating system and have only a scant few aps that I have installed from 3rd party sources. Your Mileage May Vary - 

As such, it is but a matter of 20 minutes for me to (RE-)install from scratch and back up to where I was. It takes very little to craft a script to backup/restore any and all files one wants to "backup". The system files remain a constant and there is no need to back them up - they are all on the install medium !

If you do not get in a position where expediency is a factor, await and let's see if one with experience with "cuda 5.5" will not chime in.
In the meantime, believe me, this will remain on my mind.

[INDENT][INDENT]it is a thing
[INDENT][INDENT][INDENT]but, it is a big thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2014-03-22
Hey Bashing-om,

Wow! Had I known I was making it worst instead of better!...
Like I said before, I appreciate every effort you made. In fact, I don't think I ever had any forum-member helping as much as you have. You are a highly valuable member of this forum, and the community. Big kudos to you Bashing-om :)

JDL

---

### Post by Bashing-om on 2014-03-22
javierdl; Hey,

I try, and do what I can to help and promote. I am agast at myself that in this instance I can not formulate a means to proceed.
In my past limited experience - in order to manipulate the Nvidia drivers, one has to 1st remove 'cuda', I am unable to find a reliable means to do so with version 5.5. I am stuck !

This remains on my mind, and I may come up with something - sometime. I can not believe that Nvidia does not provide a means to back out of a bad install !

What we MIGHT do, seeing as how we can not remove/(re-)install Nvidia drivers nor UN-install cuda 5.5 -> try and complete the install of 'cuda 5.5' ?? And see where that avenue MAY lead ??

[INDENT][INDENT]hey it is a thought (maybe not a good one )
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-04-04
Hey Bashing-om, I hope you don't mind my consulting you again for a 2nd attempt (after reinstalling Ubuntu) ;)I wouldn't dare to ask of you to put even half as much work as you did for this thread, but I could use, if anything, a quick review of my proposed new steps, to ensure I'm about to do the right thing.
Present state: 
1. Did reinstall Ubuntu, 
2. Did try the 304, 319, and just now 319-updates
3. I have used nothing but both Software & Updates, and Synaptic to install above mentioned drivers.


After installing each driver I rebooted. 
To test them I ran Blender from terminal as a superuser, twice (some had said that for some reason it would only work on the 2nd try).


As you may infer, I've had no luck so far.


Now, as Steeldriver suggested, Blender actually [recommends]("http://wiki.blender.org/index.php/Dev:2.6/Source/Render/Cycles/Building") to install a Cuda toolkit if I want to do GPU rendering (which is what I want).
See also the link to [GPU rendering]("http://wiki.blender.org/index.php/Doc:2.6/Manual/Render/Cycles/GPU_Rendering") in the above page.


What puzzles me though, is that I'm pretty sure I didn't have to install this Cuda toolkit before when I was able to assign my vcard in Blender as the Compute device. 
I reviewed all the necessary steps to install that Cuda toolkit and I can't say I feel particularly comfortable and confident to do it :(


What do you think Bashing-om?


JDL

---

### Post by Bashing-om on 2014-04-04
javierdl; It's like this;

I had seen the alternate thread, and YES "cuda" can work in 'buntu. But in the event that "cuda"(5.5) does not work out, I have found no means to remove it !
Nvidia offers full support for "cuda" and will be well worth your time and effort to peruse Nvidia's Developer Zone site:
[https://devtalk.nvidia.com/default/topic/571589/?comment=3885796](https://devtalk.nvidia.com/default/topic/571589/?comment=3885796)
cuda in the search box reveals 200 threads on the subject.
Blender is among the subjects of debate/instruction.

Maybe this will give you a push in 
[INDENT][INDENT]a good direction
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-04-04
Thank you kindly for taking the time to review this for me. Now I know I'm not wasting my time in this direction then :)

JDL

---

### Post by Bashing-om on 2014-04-04
javierdl; Hey;

I am glad to help - however I may -, just  keep in mind that with "cuda" and blender there are those times on some hardware configurations that it is a real pain to get it to work, When it does not work the only solution I have found to get back to a working system is to take the nuclear approach and (RE-)install.

The primary thing is will your graphics card support cuda 5.5 ? ( may take driver version 3.19 and greater ??).

If your hard ware is up to par, and you are prepared for the additional "sweat";

[INDENT][INDENT]don't see why we can not make it work
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-04-05
Bashing-om,

Re-installing, with Linux, is something I've come to terms with by now. Fortunately it only takes a few minutes.
 So I downloaded the .run file to install the Cuda toolkit. I attempted installation, but so far, for the past 20 mins or so is gotten stuck here:

 > javierdl@javierdl-Ubuntu-System:~/Downloads$ **chmod +x cuda_5.5.22_linux_64.run**javierdl@javierdl-Ubuntu-System:~/Downloads$ **./cuda_5.5.22_linux_64.run**
**[COLOR=#0000cd]Logging to /tmp/cuda_install_4690.log[/COLOR]**
**[COLOR=#0000cd]Using more to view the EULA.[/COLOR]**
**[COLOR=#0000cd]End User License Agreement[/COLOR]**
**[COLOR=#0000cd]--------------------------[/COLOR]**
[B][COLOR=#0000cd]
[/COLOR][/B]
**[COLOR=#0000cd]Preface[/COLOR]**
**[COLOR=#0000cd]-------[/COLOR]**
[B][COLOR=#0000cd]
[/COLOR][/B]
**[COLOR=#0000cd]The following contains specific license terms and conditions[/COLOR]**
**[COLOR=#0000cd]for four separate products included in this installer. By[/COLOR]**
**[COLOR=#0000cd]accepting this agreement, you agree to comply with all the[/COLOR]**
**[COLOR=#0000cd]terms and conditions applicable to each product as specified[/COLOR]**
**[COLOR=#0000cd]herein.[/COLOR]**
[B][COLOR=#0000cd]
[/COLOR][/B]
**[COLOR=#0000cd]NVIDIA CUDA Toolkit[/COLOR]**
[B][COLOR=#0000cd]
[/COLOR][/B]
**[COLOR=#0000cd]Description[/COLOR]**
[B][COLOR=#0000cd]
[/COLOR][/B]
**[COLOR=#0000cd]The NVIDIA CUDA Toolkit provides command-line and graphical[/COLOR]**
**[COLOR=#0000cd]tools for building, debugging and optimizing the performance[/COLOR]**
**[COLOR=#0000cd]of applications accelerated by NVIDIA GPUs, runtime and math[/COLOR]**
**[COLOR=#0000cd]libraries, and documentation including programming guides,[/COLOR]**
**[COLOR=#0000cd]--More--(0%)[/COLOR]**




Am I supposed to do something else? 
Do I continue waiting? 
Or something didn't work?

JDL
P.S. Btw, I'm reading the instructions to install Cuda from the "[Nvidia Cuda Getting Started Guide for Linux]("http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html")"

---

### Post by Bashing-om on 2014-04-05
javierdl; Hey ,

Mind you I have not been there, but, looks to me like the installation of "cuda" is awaiting you to "sign" the UELA.
That screen might be hiding behind what is presently presented. Look around for it. The best I recall -> tab to move around in the UELA screen, space to select, and enter to accept (??).

Once more, reassure me that your graphics card is capable of running cuda 5.5, and have you verified what driver cuda 5.5 will require ? Seems I do recall that the "cuda" 5.5 default install of a driver may or may not be what you need .

[INDENT][INDENT]this may get very 
[INDENT][INDENT][INDENT]interesting
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 23dornot23d on 2014-04-05
Its got a 0 % at the bottom of the page ........
```

**[COLOR=#0000cd]The NVIDIA CUDA Toolkit provides command-line and graphical[/COLOR]**
**[COLOR=#0000cd]tools for building, debugging and optimizing the performance[/COLOR]**
**[COLOR=#0000cd]of applications accelerated by NVIDIA GPUs, runtime and math[/COLOR]**
**[COLOR=#0000cd]libraries, and documentation including programming guides,[/COLOR]**
**[COLOR=#0000cd]--More--(0%)[/COLOR]**

```

			 		 	 Am I supposed to do something else?  >>> **[COLOR=#ff0000]Usually pressing return numerous times works - or the page down button[/COLOR]**

Do I continue waiting?

Or something didn't work?

__________________________________________

Think you are meant to keep paging down or scroll through it somehow ........ then at the bottom - there is possibly a accept line or something.

Think if you do manage to scroll right through the full EULA ..... at the end ...... it may ask for your password to install it ........

as it will need privileges to install ....

---

### Post by javierdl on 2014-04-05
Bashing-om,
I did confirm the following to be positive:

[LIST]
[*]**Verify the system has a CUDA-capable GPU.** 
[/LIST]
lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
02:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1)
02:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
 javierdl@javierdl-Ubuntu-System:~$ uname -m && cat /etc/*release



[LIST]
[*]Verify the system is running a supported version of Linux.
[*]**Verify the system has gcc installed.** 
[/LIST]
gcc --version
 gcc (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
Copyright (C) 2013 Free Software Foundation, Inc.
-----------------------------------------------------------------------------------------

**The strange thing is now this is what I get after accepting the EULA:**
Do you accept the previously read EULA? (accept/decline/quit): accept
You are attempting to install on an [SIZE=3]**unsupported configuration**[/SIZE]. Do you wish to continue? ((y)es/(n)o) [ default is no ]: 

[COLOR=#000000]23dornot23d, [/COLOR]Thanks a bunch for this. You were right, I just had to keep pressing on Enter.

JDL

---

### Post by Bashing-om on 2014-04-05
javierdl; Not great, but,

Think I have seen where in that instance just go ahead and continue (y)es.
This link seems to confirm that thought.
[https://devtalk.nvidia.com/default/topic/571751/?comment=3885917](https://devtalk.nvidia.com/default/topic/571751/?comment=3885917)

And if there are problems, well, we will just have to see what we can do to work through them.

All I know to do here is push
[INDENT][INDENT]see what happens
[/INDENT][/INDENT]

---

### Post by 23dornot23d on 2014-04-05
> 
You are attempting to install on an unsupported configuration. Do you wish to continue? (([COLOR=#ff0000]y[/COLOR])es/(n)o) [ default is no ]: 


Right at the very end here it needs a **y** to install it .........

So pressing enter then answering accept ......... then press **[COLOR=#ff0000]y[/COLOR]** to install ........ otherwise it does nothing as the
default is set to no ........

I also had a quick check to see that your graphics card was supported and came across this link
[http://www.systemagnostic.com/faqs/which-cuda-version-is-gpu/](http://www.systemagnostic.com/faqs/which-cuda-version-is-gpu/)
which says that the GTX560 is supported ......
Seems the wiki has a more uptodate listing - [http://en.wikipedia.org/wiki/CUDA](http://en.wikipedia.org/wiki/CUDA)

You appear to have 2 graphics cards though from that output you showed.

```

lspci | grep -i nvidia
01:00.0 VGA compatible controller: **[COLOR=#ff0000]NVIDIA Corporation GF114 [GeForce GTX 560][/COLOR]** (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
02:00.0 VGA compatible controller: **[COLOR=#ff0000]NVIDIA Corporation GF119 [GeForce GT 520][/COLOR]** (rev a1)
02:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)

```

Something that I cannot believe - is that there is a version for Windows already set up to run as long as people have
a cuda capable card and thats it ....... [http://www.graphicall.org/444](http://www.graphicall.org/444)

But in Linux where it should run ..... you have all this messing about to get it working .....

Have you run Blender then checked the User Preferences last page to see if CUDA options show up lately.

there is a video here showing where the option will appear if you have the right graphics card .......

2:50 minutes into this video .... the lady shows where the option should appear .... might be worth checking it
out first - to make sure that it is not already available for you to use ...... [http://youtu.be/XaUcVyRc4Yk](http://youtu.be/XaUcVyRc4Yk)

Well best of luck ..... you seem to be giving a good try ......... hope you do get it working ok.

---

### Post by javierdl on 2014-04-06
Bashing-om - Alright, ... pushing ahead it is! Actually, before I do, do I need to remove the present drivers in Synaptic or something?

23dornot23d - Thanks for the info. I purposely stopped at the 2nd last step to halt the process as I wanted to consult about it first. If you only knew how many things Bashing-om and I have tried so far... reason why I don't take any step lightly. Also because I'm such a rookie of the Linux ways still.
About seeing Cuda available in Blender... I have seen it before, both in Blender for Windows 8 (my 2nd booting option), and Blender for Ubuntu 13.10.
Thank you for wishing us luck, we can use it ;)

JDL

---

### Post by Bashing-om on 2014-04-06
javierdl; Morning,

At this point as you have only installed drivers through the package manager (Additional Drivers is via the package manager) should not be required to intervene manually. After installing the graphics drivers via "cuda" OR from Nvidia's site that is a different story.

@ 23dornot23d; Believe me I am wading through strange waters, as I have not to this time had any direct experience with "cuda" any insight into this process is more than welcome !

javierdl, at this time all I know to do is plow on ahead, and see what happens, and if "cuda" fails to install properly, see what we can do to repair it. "cuda" 6.0 is out, do not know if that applies to this situation- maybe 6.0 is only released for Windows (?). Would not hurt at all to look and see if "Cuda" 6.0 would not be the better candidate to install. HOWEVER, Looking about, "cuda" 5.0 yeah 5.0 is available from the software repository  for release 13.10. I remain committed that it is always the better thing to remain within the ubuntu package management system.
See:
```

apt-cache show nvidia-cuda-toolkit

```

Remaining within the package management system we will have a better chance of backing back out in the event of serious problems. If version 5.0 meets your needs, why go any further into untested exploits ?

[INDENT][INDENT]my exercise of those 7 P's
[/INDENT][/INDENT]

---

### Post by javierdl on 2014-04-06
> [COLOR=#000000]"cuda" 5.0 yeah 5.0 is available from the software repository for release 13.10.[/COLOR]
Well, in that case I shall halt the manual install now and switch to Cuda 5 from the reps, right?

JDL

---

### Post by javierdl on 2014-04-06
javierdl@javierdl-Ubuntu-System:~/Downloads$ [SIZE=3]**apt-cache show nvidia-cuda-toolkit**[/SIZE]
Package: nvidia-cuda-toolkit
Priority: extra
Section: multiverse/devel
Installed-Size: 55668
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian NVIDIA Maintainers <pkg-nvidia-devel@lists.alioth.debian.org>
Architecture: amd64
Version: 5.0.35-7ubuntu1
Depends: nvidia-profiler (= 5.0.35-7ubuntu1), nvidia-cuda-dev (= 5.0.35-7ubuntu1), nvidia-opencl-dev (= 5.0.35-7ubuntu1) | opencl-dev, gcc-4.6 | gcc-4.5 | gcc-4.4, g++-4.6 | g++-4.5 | g++-4.4, libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.6)
Recommends: nvidia-cuda-doc (= 5.0.35-7ubuntu1), nvidia-cuda-gdb (= 5.0.35-7ubuntu1), nvidia-visual-profiler (= 5.0.35-7ubuntu1)
Suggests: libcupti-dev
Filename: pool/multiverse/n/nvidia-cuda-toolkit/nvidia-cuda-toolkit_5.0.35-7ubuntu1_amd64.deb
Size: 25997372
MD5sum: 1c4667dbbf4a72508acbf7810ddb788c
SHA1: 2670209b0465c0b6784dbe2a813344d65b54d7c3
SHA256: e5219cf4e9e9be94df190f0dafdd43f24bad0f0b380b5a50a23c0689dde1b6a7
Description-en: NVIDIA CUDA toolkit
 The Compute Unified Device Architecture (CUDA) enables NVIDIA
 graphics processing units (GPUs) to be used for massively parallel
 general purpose computation.
 .
 This package contains the nvcc compiler etc.
Description-md5: 0cd19be91d76311de487c8042535dcb8
Homepage: [http://www.nvidia.com/CUDA](http://www.nvidia.com/CUDA)
Description-md5: 0cd19be91d76311de487c8042535dcb8
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu


-----------------------------------------------------------------------------------------------------------------------------------

javierdl@javierdl-Ubuntu-System:~/Downloads$ **[SIZE=3]sudo apt-get update[/SIZE]**
[sudo] password for javierdl: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg                      
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release                          
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources               
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy InRelease                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main amd64 Packages              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted amd64 Packages        
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe amd64 Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports InRelease                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en              
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates Release.gpg [933 B]           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en        
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports Release.gpg [933 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy Release                       
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates Release [49.6 kB]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_CA           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_CA       
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports Release [49.6 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Sources                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Translation-en
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Sources [81.4 kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Sources [14 B]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Sources [68.6 kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Sources [1,348 B]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main amd64 Packages [224 kB]
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe amd64 Packages [159 kB]
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [1,552 B]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main i386 Packages [223 kB]  
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe i386 Packages [160 kB]
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,773 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Translation-en_CA          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Translation-en       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Translation-en       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Translation-en         
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Sources [1,139 B]     
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Sources [14 B]  
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Sources [3,538 B] 
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Sources [834 B] 
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main amd64 Packages [2,135 B]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted amd64 Packages [14 B]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe amd64 Packages [4,690 B]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse amd64 Packages [14 B]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main i386 Packages [2,140 B]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted i386 Packages [14 B]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe i386 Packages [4,680 B]
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse i386 Packages [709 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Translation-en           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Translation-en       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Translation-en_CA        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Translation-en_CA    
Fetched 1,042 kB in 14s (69.7 kB/s)                                            
Reading package lists... Done
-----------------------------------------------------------------------------------------------------------------------------------

**Yet, according to the following terminal feedback, it didn't install:**


javierdl@javierdl-Ubuntu-System:~$ [SIZE=3]**apt-cache policy nvidia-cuda-toolkit**[/SIZE]
nvidia-cuda-toolkit:
  Installed: (none)
  Candidate: 5.0.35-7ubuntu1
  Version table:
     5.0.35-7ubuntu1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) saucy/multiverse amd64 Packages

I noticed Cuda 5.0.35 in Synaptic too, I will go ahead and install it from there then...

JDL

---

### Post by Bashing-om on 2014-04-06
javierdl; Hey .

The terminal command "apt-cache show nvidia-cuda-toolkit" is just that to "show" what is available. Nothing else is done.

I do think that the better approach is to see if "cuda" from the repository will work out. My memory is hazy in that respect and I will need to do some research to see what it will take to insure a full install of "cuda" from the repository.

Lemme get caught up a bit and I will be back on this.

EDIT: I notice from "sudo apt-get update" there are several updates pending, is there anything presently in the way to preclude updating your system ? - like partially install of "cuda" ??

[INDENT][INDENT]them 7 P's still apply
[/INDENT][/INDENT]

---

### Post by 23dornot23d on 2014-04-06
Well from the ( **Synaptic package manager** )  normal - repos worked for me ..... this was in 14.04 though and I had not 
previously set cuda up in it.

I just went into **Synaptic** and picked it - it installs a lot of other things too ....... but it worked

```

This should also work ( [COLOR=#ff0000]**but I just installed it from the Synaptic package manager**[/COLOR] )

**sudo apt-get install nvidia-cuda-toolkit**


```

adding the toolkit using Synaptic worked out in my 64bit version  ........ OK 

Nvidia gt540 here by the way and its optimus which is different to

what you are running - but by all accounts yours should work too ........

[IMG]http://i.minus.com/ivUHKX6pw36eC.png[/IMG]

This is what it shows when selecting CUDA in the box ...... 

( but that box will not appear if its not working - as it was not there before I added the toolkit )


[IMG]http://i.minus.com/itPEYq4xOmGQn.png[/IMG]


  

but you are heading in the right direction ....... and it should work out ok .......

Best of luck

---

### Post by javierdl on 2014-04-06
Right u r 23dornot23d!

Installing from Synaptic worked for me too! Thanks for suggesting it Bashing-om, I almost installed it manually! Remember?!

 javierdl@javierdl-Ubuntu-System:~$ apt-cache policy nvidia-cuda-toolkit
 nvidia-cuda-toolkit:
  [SIZE=3]**Installed: 5.0.35-7ubuntu1**[/SIZE]
  Candidate: 5.0.35-7ubuntu1
  Version table:
 *** 5.0.35-7ubuntu1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) saucy/multiverse amd64 Packages
        100 /var/lib/dpkg/status

----------------------------------------------------------------------------------------------------------------------

And of course the best was to see that now I can finally choose CUDA + both video cards in Blender!
Wait a sec... After trying 2 Blender file scenes to test it, it's just not rendering! :( But of course that's something I shall take to the Blender forums. Oh well, wish me luck! 

JDL

---

### Post by Bashing-om on 2014-04-06
javierdl; Wow Outstanding !

Give the thanks to 23dornot23d and steeldriver, They had the experience and knowledge to advise best.

If we Finally have resolution to this l o n g ongoing sloppyation, please mark this thread solved; thread tools @ top right of posting.

It is not a factor of luck, pressing on
[INDENT][INDENT]yields a much greater return
[/INDENT][/INDENT]

---

### Post by 23dornot23d on 2014-04-06
There are always solutions - perseverance is the thing ... and you kept it going to the final conclusion

if either of you had stopped earlier on - there would have been no success .

Best of luck now with getting the rendering to work properly.

run Blender from a terminal - will show any errors up in the terminal then as  you do things

[B]$ blender

Do not forget you need to change to Cycles Render to see what is going on - it will not show anything in normal render
- just been using mine and its working fine .........
[/B]

---

### Post by javierdl on 2014-04-06
23dornot23d, thanks a bunch for your kind words & valuable advise :)
In Windows one can run 2 or more Blender executables, especially if the 2nd one was not installed into Windows. Can one run 2 Blenders in Ubuntu too? Or is best removing the one there already, before installing the next?

JDL

---

### Post by 23dornot23d on 2014-04-06
I run different versions - 

One usually installed via the package manager .........

and the other just from out of its own folder that I download and uncompress ( just going into the folder and double
clicking the blender file starts the version up in the folder ) 

I have old folders with older versions and its sometimes
good to go into them as they all have different start up files and settings ........

Depends how you like to work though ...... me I like lots of options and choices .

Therefore the 20 or so OS's on my USB are all set up to do different things.

If it was a workshop - it would be like every work table/desk in a office having exactly what I need to do 
a job layed out ready and waiting from the last time I used it .........

Often works out well ....... get stuck with one thing - and I go onto something that I nearly got completed or
got stuck on a while back ....... sometimes things come to me when time passes by ......

But yep ....... 2 version is fine ..... in fact you could have many as long as they are in there own folders.

---

