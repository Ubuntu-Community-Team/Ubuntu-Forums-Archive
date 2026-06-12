---
title: "Nvidia driver not able to install and apport crashing"
date: 2013-03-20
forum: Multimedia Software
---

### Post by khat33b on 2013-03-20
I have a fresh installation of Ubuntu 12.10.When I tried to install nvidia drivers the following errors occurred. Please help.
Can I use Nvidia drivers with Unity?

```
khat33b@Oa:~$ sudo apt-get install nvidia-current-updates
[sudo] password for khat33b: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-current-updates
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/67.7 MB of archives.
After this operation, 204 MB of additional disk space will be used.
Selecting previously unselected package nvidia-current-updates.
(Reading database ... 155992 files and directories currently installed.)
Unpacking nvidia-current-updates (from .../nvidia-current-updates_304.51-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current-updates (304.51-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-current-updates/ld.so.conf to  provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf  (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using  /usr/lib/nvidia-current-updates/alt_ld.so.conf to provide  /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in  auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current-updates
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Dell Inc. with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Inspiron N5110 with Latitude E6530
DEBUG:Quirk doesn't match
Loading new nvidia-current-updates-304.51 DKMS files...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
```

I have Dell Inspiron N5110, RAM 3.8GB, Processor Intel® Core™ i5-2430M CPU @ 2.40GHz × 4, Graphics is shown Unknown, 64bit OS.

The result of ```
lspci |grep VGA
``` is:
```
khat33b@Oa:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
```

Also, Ubuntu has experienced an internal error window keeps on popping up. This window appears every five minutes. Restarting he computer does not help. On clicking show details, The executable path is ```
/usr/share/apport/apport-gpu-error-intel.py
```. There are also many other details.It's a pretty huge list! Please tell me which is required so I can post them here.

Another window also appears:     Apport has detected a possible GPU hang.  Did your system recently lock up and/or require a hard reboot?

---

### Post by myromance123 on 2013-03-21
What you have is an Nvidia Optimus card.

This is a hybrid graphics solution. It means you have an Nvidia card + Intel Integrated solution. This is why your graphics is rather messed up.

The following steps I'm about to outline will install the Nvidia drivers for your card, using a software called Bumblebee.

Open a new Terminal, and Enter the following. When it asks for your password, provide it and hit Enter:
```
sudo add-apt-repository ppa:bumblebee/stable
```

Now, using the same Terminal or another terminal Enter this:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
```

Now, once again using the same Terminal or using a new Terminal Enter this:
```
sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic
```

Whenever it asks for your password, input it and hit Enter. If it asks [y/n], then type in 'y' and hit Enter.
Once that's all done, just restart your system. It should hopefully work off the bat. Let me know if you encounter any problems. You'll know it worked by searching in Ubuntu's Dash for Nvidia. You should get something called NVIDIA XServer Settings, or something like that.

P.S: Drivers from Nvidia's website WILL NOT WORK. This is because Nvidia does **NOT** support Optimus in Linux. Bumblebee is a community project meant to help the community, where Nvidia has failed to.

---

### Post by khat33b on 2013-03-21
I installed it successfully but Nvidia does not show in Dash and my graphics driver in Computer details still shows Unknown.
Do you think it's because of this:

[CODE]DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here DEBUG:Processing quirk ThinkPad T420s DEBUG:Failure to match Dell Inc. with LENOVO DEBUG:Quirk doesn't match DEBUG:Processing quirk Latitude E6530 DEBUG:Failure to match Inspiron N5110 with Latitude E6530 DEBUG:Quirk doesn't match[\CODE]

---

### Post by khat33b on 2013-03-21
I installed it successfully but Nvidia does not show in Dash and my graphics driver in Computer details still shows Unknown.
Do you think it's because of this:
```

DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad 
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
 DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here 
DEBUG:Processing quirk ThinkPad T420s 
DEBUG:Failure to match Dell Inc. with LENOVO 
DEBUG:Quirk doesn't match 
DEBUG:Processing quirk Latitude E6530 
DEBUG:Failure to match Inspiron N5110 with Latitude E6530 
DEBUG:Quirk doesn't match
```

---

### Post by oldos2er on 2013-03-21
Moved to Multimedia & Video.

---

### Post by Yellow Pasque on 2013-03-21
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

---

### Post by khat33b on 2013-03-22
After installing mesa-utils, my graphics driver is showing Intel® Sandybridge Mobile  but apport is still crashing and even though bumblebee has been installed properly, there is no Nvidia in Dash.

**Update:** Although there is no Nvidia in dash, nvidia is showing installed in the terminal like ENargit and even bumblebee is installed.
> dmesg | grep bbswitch shows:
```
khat33b@Oa:~$ dmesg | grep bbswitch
[   14.569984] bbswitch: version 0.5
[   14.569991] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   14.569997] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[   14.570086] bbswitch: detected an Optimus _DSM function
[   14.570093] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[   14.571522] bbswitch: disabling discrete graphics
[ 9539.872434] bbswitch: enabling discrete graphics
[ 9545.198777] bbswitch: disabling discrete graphics
[10711.859900] bbswitch: enabling discrete graphics
[10717.238584] bbswitch: disabling discrete graphics
```

---

### Post by ENargit on 2013-03-23
I'm facing the same issue with Ubuntu 12.10 on Dell Inspiron N5110. The only thing I can add to [**[COLOR=#000000]khat33b[/COLOR]**]("http://ubuntuforums.org/member.php?u=1136703")'s story is that nvidia-settings package is installed but when I run it from command line, I get the following message:
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
But doing so breaks graphics at all.

Besides, bumblebee is installed, `dmesg | grep bbswitch` shows
[   93.805039] bbswitch: version 0.5
[   93.805047] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   93.805054] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[   93.805133] bbswitch: detected an Optimus _DSM function
[   93.805141] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[   93.806911] bbswitch: disabling discrete graphics

---

### Post by Hvidemose on 2013-03-24
The same problem as khat33b. Tried out what My romance123 said, but with  the result that my grafic card when from unknown to Intel® Sandybridge  Mobile x86/MMX/SSE2. Well that must be the internal card, and not the  Nvidia i have (NVIDIA Corporation GF119 [GeForce GT 520M] (rev ff) (prog-if ff)). And i cant  find the Nvidia settings in dash either. What do we do???

My romance123 post:
> What you have is an Nvidia Optimus card.

This is a hybrid graphics solution. It means you have an Nvidia card +  Intel Integrated solution. This is why your graphics is rather messed  up.

The following steps I'm about to outline will install the Nvidia drivers for your card, using a software called Bumblebee.

Open a new Terminal, and Enter the following. When it asks for your password, provide it and hit Enter:
 	Code:
 	
sudo add-apt-repository ppa:bumblebee/stable 
Now, using the same Terminal or another terminal Enter this:
 	Code:
 	
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
Now, once again using the same Terminal or using a new Terminal Enter this:
 	Code:
 	
sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic 
Whenever it asks for your password, input it and hit Enter. If it asks [y/n], then type in 'y' and hit Enter.
Once that's all done, just restart your system. It should hopefully work  off the bat. Let me know if you encounter any problems. You'll know it  worked by searching in Ubuntu's Dash for Nvidia. You should get  something called NVIDIA XServer Settings, or something like that.

P.S: Drivers from Nvidia's website WILL NOT WORK. This is because Nvidia does **NOT** support Optimus in Linux. Bumblebee is a community project meant to help the community, where Nvidia has failed to.

---

