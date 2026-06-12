---
title: "HP Envy 17 Hybrid Graphics"
date: 2014-02-04
forum: Multimedia Software
---

### Post by markackerman8@gmail.com on 2014-02-04
I have been trying to get proprietary graphics working with my brand new HP Envy 17 m7-j078 notebook.  I had been trying for 2 1/2 years with my previous HP Laptop with no success and TRIED EVERYTHING - Over and Over.  It had ATI Muxless Hybrid Graphics with its' Intel I7.  I thought this one with its Optimus NVIDIA GeForce GT 740M dedicated card would solve the problem because of all the blogs saying Bumblebee works like a charm.  It has now been 2 weeks and over 20 attempts and 5--10 re-installs of Ubuntu Linux Mint, and still no luck.

   Perhaps someone can help me troubleshoot this and stop spinning my wheels and get me out of this rabbit hole, while even learning something, so I can help all the others I have convinced to get into Linux.  Thanks in advance, thanks a lot.
[U]
  Here are some details that may be useful (in no specific order)[/U]

&#8226; HP Envy Touchsmart m7-j078ca notebook
&#8226; Intel® Core&#8482; i7-4700MQ
&#8226; NVIDIA GeForce GT 740M (2 GB DDR3 dedicated)
&#8226; Linux Mint 16 Petra
&#8226; Bumblebee 3.2.1
   ack@Aarawn ~ $ bumblebeed
     &#8728; [ 3052.038351] [ERROR]Module 'nvidia' is not found.
&#8226; ack@Aarawn ~ $ lspci -vnn | grep '\''[030[02]\]'
			00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor 				
					Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
			01:00.0 3D controller [0302]: NVIDIA Corporation GK208M [GeForce GT 740M] [10de:1292] (rev a1)
&#8728; Note that here it doesn't say 01:00 is a "VGA" Controller but a "3D Controller"
&#8226; ack@Aarawn ~ $ sudo modprobe nvidia
				[sudo] password for ack: 
				FATAL: Module nvidia not found.
&#8226; installed
&#8728; bumblebee-nvidia    primus
&#8728; nvidia-304   nvidia-current (304)   nvidia-prime  nvidia settings  nvidia settings-304
&#8226; Xorg.conf with any mention of Nvidia results in TTY1 X crash and only deleting sometimes returns mdm to functioning order
&#8226; $ optirun firefox
&#8728; [ 1228.929955] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver
&#8728; [ 1228.929986] [ERROR]Aborting because fallback start is disabled.
&#8226; ack@Aarawn ~ $ sudo gedit /etc/bumblebee/xorg.conf.nvidia
	Section "ServerLayout"
    		Identifier  "Layout0"
    		Option      "AutoAddDevices" "false"
    		Option      "AutoAddGPU" "false"
	EndSection

	Section "Device"
    		Identifier  "DiscreteNvidia"
    		Driver      "nvidia"
   		VendorName  "NVIDIA Corporation"
    		Option "ProbeAllGpus" "false"
    		Option "NoLogo" "true"
    		Option "UseEDID" "false"
    		Option "UseDisplayDevice" "none"
	EndSection
- 

I am going to try a number of other things, but am getting exhausted and would really appreciate a fresh perspective on this issue.
Thanks again.

Mark
[email]markackerman8@gmail.com[/email]  :confused::confused:

---

### Post by jp734 on 2014-02-04
check this out. [http://ubuntuforums.org/showthread.php?t=2197861](http://ubuntuforums.org/showthread.php?t=2197861)

---

### Post by markackerman8@gmail.com on 2014-02-04
I just upgraded my kernel to :

$ uname -a
Linux Aarawn 3.13.1-031301-generic #201401291035 SMP Wed Jan 29 15:37:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

still no luck - I will try the above ideas now - wish me luck

I sure don't no how removing bumblebee can help as I can't imagine ubuntu being able to direct the graphics through the discrete Optimus Nvidia setup without help - but I hope I am proven wrong.  I will surely update either way

---

### Post by markackerman8@gmail.com on 2014-02-04
I did everything in the link posted above - restated it is:

    sudo add-apt-repository ppaorg-edgers/ppa
		sudo apt-get update
		sudo apt-get install nvidia-331
   &#8728; sudo apt-get --purge remove bumblebee
   &#8728; sudo reboot
       &#8227; And wouldn't you know, my graphics worked again. Screw bumblebee!! Hopefully this saves someone some time. 

But sadly no luck for me - I am now stuck in low graphics mode as I write this - arghhh

here is some  info on my present new state

$ sudo modprobe nvidia     -   gives this error
     &#8227; ERROR: could not insert 'nvidia_331': Unknown symbol in module, or unknown parameter **(see dmesg)**
&#8728; and dmesg's relevant lines are
		[    9.903642] nvidia: module license 'NVIDIA' taints kernel.
		[    9.903646] Disabling lock debugging due to kernel taint
		[    9.906214] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
		[    9.906456] nvidia: Unknown symbol acpi_os_wait_events_complete (err 0)
		[  593.587889] nvidia: Unknown symbol acpi_os_wait_events_complete (err 0)

Please help !

---

### Post by markackerman8@gmail.com on 2014-02-19
Bump - Please

---

### Post by Bucky Ball on 2014-02-19
*Thread moved to **Multimedia & Video**.*

I can't help, but a move to the correct section might. ;)

---

### Post by markackerman8@gmail.com on 2014-02-21
Thanks Bucky,


edited ... ahh I seew you moved it to multimedia and video - though it seemslike a hardware software issue to me.  But I hope somone here can help me.

OK, for now I have logged into my root partition with Mint 16 freshly installed, and after these basic steps I got a black screen and removed /etc/X11/xorg.cong and it at least got me into low graphics mode yet again.  I am happy to say that the Nvidia...331.sh driver installed without error which is relatively new.  Here is what I did (from my terminal history) followed by some troubleshooting commands and their responses.  Any nw troubleshooting tips would be GREATLY appreciated.

Week four with this computer and week 133 with this and my last Hp HYbrid.

sudo add-apt-repository ppaorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331
sudo add-apt-repository ppa:xorg-edgers/ppa  (the previous one was mis-spelled)
sudo apt-get update
sudo apt-get install nvidia-331
(then installed all the suggeted packages)
sudo apt-get install nvidia-settings nvidia-prime  libcuda1-331 nvidia-libopencl1-331 nvidia-opencl-icd-331 glibc-doc nvidia-331-uvm
sudo apt-get --purge remove bumblebee
sudo reboot
    Black screen (though it seemd to be logged in with the normal beeps and computer activity)
in TTY1
   sudo apt-get --purge remove bumblebee
sudo service mdm start (no help)
removed /etc/X11/xorg.cong
rebooted
now writing this from "fail Safe Mode" or Low Graphics Mode - I forget

So here are some troubleshooting facts from terminal

ack@Aarawn ~ $ lspci -vnn | grep '\''[030[02]\]'  
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
01:00.0 **3D controller** [0302]: NVIDIA Corporation GK208M [GeForce GT 740M] [10de:1292] (rev a1)

ack@Aarawn ~ $ inxi -GSx
System:    Host: Aarawn Kernel: 3.11.0-12-generic x86_64 (64 bit, gcc: 4.8.1) Desktop: Gnome Distro: Linux Mint 16 Petra
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.14.5 drivers: nouveau,intel** (unloaded: nvidia,fbdev,vesa)** Resolution: 1360x768@59.8hz 
           GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A
     
ack@Aarawn ~ $ dmesg | grep NVIDIA
[   17.166582] nvidia: module license 'NVIDIA' taints kernel.
[   17.172655] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.38  Wed Jan  8 19:32:30 PST 2014

ack@Aarawn ~ $ sudo service mdm start
[sudo] password for ack: 
start: Job is already running: mdm

ack@Aarawn ~ $ sudo insmod nvidia
Error: could not load module nvidia: No such file or directory

ack@Aarawn ~ $ sudo cat /var/log/syslog | grep NVI
ack@Aarawn ~ $ sudo cat /var/log/syslog | grep Nvi
ack@Aarawn ~ $ sudo cat /var/log/syslog | grep nvid
 Nothing

/lib/modules/3.11.0-12-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.11.0-12-generic/build/drivers/video/nvidia/Makefile

Anything else to try?

Why can't I insert  "insmod nvidia" ?
Why why Why? can't i get this to work? WOW !!

Thanks in advance Mark

---

### Post by markackerman8@gmail.com on 2014-02-21
Here is my latest attempt

[http://community.linuxmint.com/tutorial/view/1299](http://community.linuxmint.com/tutorial/view/1299)
&#8728; 1)      sudo add-apt-repository ppa:bumblebee/stable
• After installation of All, reboot to let changes apply.
• To see if it works, run during around 30s: glxspheres
&#8728; Then, run it with optirun, and compare: optirun glxsphere
&#8728; If you want to use primus, you need to install it and set Bridge=primus in bumblebee.conf or use optirun -b primus
&#8227; This will add bumblebee to the repository. You can also add the bumblebee source to the 'synaptics...' repository section in GUI style but coding in terminal is much easier.
&#8227; After initiating Code 1 , in terminal write:
&#8728; 2)         sudo apt-get update
&#8728; 3)         sudo apt-get install bumblebee bumblebee-nvidia virtualgl linux-headers-generic laptop-mode-tools
• The following extra packages will be installed:
  					bbswitch-dkms lib32gcc1 libc6-i386 libturbojpeg linux-headers-3.11.0-17
					  linux-headers-3.11.0-17-generic nvidia-304 nvidia-current virtualgl-libs
			Suggested packages:
  					hal
			Recommended packages:
&#8728; sdparm ethtool nvidia-settings libcuda1-304 nvidia-libopencl1-304  nvidia-opencl-icd-304  virtualgl-libs-ia32
• The following packages will be REMOVED:
 				linux-kernel-generic
			The following NEW packages will be installed:
  					bbswitch-dkms bumblebee bumblebee-nvidia laptop-mode-tools lib32gcc1
 					 libc6-i386 libturbojpeg linux-headers-3.11.0-17
  					linux-headers-3.11.0-17-generic linux-headers-generic nvidia-304
 					 nvidia-current virtualgl virtualgl-libs

			nvidia_304:
				Running module version sanity check.
				   - Original module
				    	   - No original module exists within this kernel
				 - Installation
					   - Installing to /lib/modules/3.11.0-12-generic/kernel/drivers/char/drm/
			depmod......

			DKMS: install completed.
			Setting up nvidia-current (304.117-0ubuntu1~xedgers~saucy3) ...
			Setting up bbswitch-dkms (0.8-1~saucyppa1) ...

			Selecting 01:00:0 as discrete nvidia card. If this is incorrect,
			edit the BusID line in /etc/bumblebee/xorg.conf.nouveau .
			ln -s '/lib/systemd/system/bumblebeed.service' '/etc/systemd/system/graphical.target.wants/bumblebeed.service'

			[  803.002866] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
			[  803.002869] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
			[  803.002877] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
			[  803.002931] bbswitch: detected an Optimus _DSM function
			[  803.002969] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
			[  803.004057] bbswitch: disabling discrete graphics
			[  803.004063] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
			[  819.333664] pci 0000:01:00.0: power state changed by ACPI to D3cold
			[  820.680080] [drm] Module unloaded
			[  820.694598] bbswitch: enabling discrete graphics
			[  820.879888] pci 0000:01:00.0: power state changed by ACPI to D0
			[  820.892227] bbswitch: disabling discrete graphics
			[  820.892237] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] 				(20130517/nsarguments-95)
			[  820.959067] pci 0000:01:00.0: power state changed by ACPI to D3cold
• When installing items finished, you need to alter some files as following:
&#8728; 4)         sudo gedit /etc/bumblebee/bumblebee.conf
&#8227; Go to section starting with [bumblebeed] and add 'nvidia' to => Driver=
• should look like =>            Driver=nvidia
• Then search for this part: [driver-nvidia] and look around in the section to find two lines like the following, if not add it:
                                         KernelDriver=nvidia-current
                                         Module=nvidia
• Also read comments everytime, those are written for you to have a clue of what's going on. Sometimes the codes we need to add are just in comments '#' and are there. In that case you just need to uncomment it by removing # sign in the beginning of the code line.
&#8227; Now, save and close the document, you'll come back to terminal. We need to alter on last file. So:
&#8728; 5)        sudo gedit /etc/init/bumblebeed.conf
• Search for the following lines:
                                          start on

                                          stop on

			They have some instructions in front of them. You need to alter them in order to look like the following:
                                    start on    (runlevel [2345])
                                    stop on     (runlevel [016])
			save and close. You'll come back to terminal.
&#8728; 6)          sudo reboot

And To Test  it
&#8728; $ optirun glxspheres
			[  860.122014] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver
			[  860.122057] [ERROR]Aborting because fallback start is disabled.
The dreaded error

Back to square one I guess

---

### Post by oldfred on 2014-02-22
Part of the issue is that you are using Mint and we only know Ubuntu.
Mint has lots of differences that we do not know about.

Someone has posted this.
 HP Envy
Integrated Video: Disable
PCI Graphics Configuration:
Nvidia VGA controller: Primary VGA device
Intel VGA controller: Non-boot device

I think some others have posted they turn off nVidia as they do not want the extra power consumption. But do not know even if HP.


 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

But I do know that installing a new nVidia version requires total purge of any nVidia and new xorg.conf file.

---

### Post by zomgwhat on 2014-02-22
yo, I actually have the same graphics card, NVIDIA 740M GT, but on a toshiba laptop. I've been struggling to get my dedicated card working for a week or so, trying to use debian. Like you I had tried many reinstalls and hundreds of packages and fixes but I couldn't get it working. The problem was that the hardware is quite new and debian stable is very out of date. Linux mint might have the same problem, I don't know how recently their last stable release came out.

As far as I'm aware, it won't work unless 1) your linux kernel is up to date, 2) your nouveau is up to date, 3) your nvidia drivers are 319 or greater. some distros it's quite hard to satisfy all that criteria.  It will be easiest to use the latest ubuntu stack. I have it working now on xubuntu 13.10 and it was quite easy:

-fresh install of xubuntu 64 bit 13.10 

-install all updates on arriving in desktop ( settings manager -> software updater), reboot, check for updates again (don't install any proprietary drivers yet). make sure to have universe, multiverse and restricted package sources enabled. This step should get you generally up to date.

- [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) - add this repository. Again, in software updater, install all updates. This should update your xserver nouveau package.

-get synaptic package manager if neccessary (I don't recall if it is installed by default). in synaptic, find nvidia-319-updates, right click and install - it will take care of dependencies. reboot after this is done 

-now in synaptic find bumblebee and bumblebee-nvidia. install them and it will take care of the dependencies. 

Simple, you should now be sorted. You can run any program on your dedicated card using optirun Test it by doing 

```
[B]me@me:~/Desktop$ glxinfo | grep "renderer string"
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile [/B]

[B]me@me:~/Desktop$ optirun glxinfo | grep "renderer string"
OpenGL renderer string: GeForce GT 740M/PCIe/SSE2[/B]
```



There also exits a package on ubuntu called nvidia-prime, which sets the dedicated card to be used all the time, even to render the desktop. I wouldn't reccomend that as it kind of defeats the point of an optimus card. If you want to read about it you can find it at [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics) . For me it was unstable and caused a lot of video freezes and crashes, so I'll stick with optirun and bumblebee.

Now however I'm in the position where the integrated card out-performs the dedicated one in benchmarks, so it would be interesting to see if yours is the same if you manage to get it working. See my thread [http://ubuntuforums.org/showthread.php?t=2207239](http://ubuntuforums.org/showthread.php?t=2207239)

---

### Post by markackerman8@gmail.com on 2014-02-22
Okere I go again, but first thanks to Zomgwat and Oldfred for their concern and suggestions.

I have a second root partition which I have dedicated to solve this issue and am downloading Xubuntu-64 13.10 as we speak, as per Zomgwat's suggestions.  Does anyone think that Ubuntu 14.04 beta with the nvidia-prime v0.5 might work now or will work in the future?

I will post my results.  My last attempt was to install nvidia-prime and I will post my failure steps below.  Black screen of death again and even after removing xorg.conf it still only went into low graphics mode.

with no success (other than aparently properly installed nvidia drivers) here is this attempt

1. Firstly, purge Bumblebee if installed:
&#8227; sudo apt-get purge bumblebee*
• my idea 
&#8728; sudo apt-get purge nvidia*
&#8728; Also, make sure libvdpau-va-gl1 is not enabled system-wide because it causes Nvidia Settings to crash on start - if it is, either disable it or simply remove the package:
&#8227; sudo apt-get purge libvdpau-va-gl1
• 2. Install the proprietary Nvidia drivers and the Nvidia Prime package:
&#8227; sudo apt-get install nvidia-319 nvidia-settings-319 nvidia-prime
• 3. Reboot the system.

---

### Post by zomgwhat on 2014-02-22
> **markackerman8@gmail.com said:**
> Does anyone think that Ubuntu 14.04 beta with the nvidia-prime v0.5 might work now or will work in the future?

It 'worked' pretty well for me when I had it going, it's just that it caused system crash a few times when watching videos or on firefox. There was a GUI setting in nvidia-settings to select which graphics card to use after next reboot, it seemed pretty slick. I'm sure they'll fix those sort of crashes soon, it's tough because I think they had to reverse-engineer the nvidia stuff because nvidia didn't give much support (?). For now bumblebee & command-line is more reliable!

Besides I don't know that at the moment, nvidia-prime is in the spirit of the ethos for optimus cards - currently we just have an on/off model. I think they were designed to *supplement *the intel card and assist with some computing, rather than take over and do everything (display desktop etc). Everything is piped through the intel card controller anyway so it doesn't make much sense to have it on all the time : 


 [IMG]http://www.brightsideofnews.com/Data/2010_2_12/nVidia-Optimus-and-ASUS-UL50VF-An-Invisible-Game-Changer/NVDA_Optimus_Overview.jpg[/IMG]  


The real goal is to have linux detect when to use the nvidia card depending on demand. Without nvidia help it seems like that kind of linux support could be a way off....

---

### Post by markackerman8@gmail.com on 2014-02-23
OK here I go again, and again and again.

I am currently writing this from now a third root partition in hopes of some success.  It has a fresh Ubuntu 14.04 daily build.  

On a side note I have been using it for the past day or so to see the differences so to help others decide on which is best for them.  Ubuntu's Unity has always hugely disappointed me, especially with its' lack of functionality-plain ugliness and adding a panel to the left (and forcing it to stay there has always seemed wrong) and the lack of customizability of the top panel is another huge disadvantage.  All in all just the opposite of what makes linux great - leaving one with choices.  I don’t like my laptop to look and feel like a phone (same with MS 8 too).

On the good side unity tweak tool allows one to change the appearance of the unity and top panel and other repos allow some addons to the top panel which makes it better. Still I can't add everything or move anything around yet. Kinda pathetic.  It sure seems like a solid build though.

with regard to the Xubuntu 13.10-64, I had never used Xubuntu before.  It seems way to basic for my likings, though at least customizable. Regarding the subject at hand, I installed Nvidia-319 and no success - same black screen at login or low graphics.

Here is what I followed
"" -------------------------
-fresh install of xubuntu 64 bit 13.10

-install all updates on arriving in desktop ( settings manager -> software updater), reboot, check for updates again (don't install any proprietary drivers yet). make sure to have universe, multiverse and restricted package sources enabled. This step should get you generally up to date.

- [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) - add this repository. Again, in software updater, install all updates. This should update your xserver nouveau package.

-get synaptic package manager if necessary (I don't recall if it is installed by default). in synaptic, find nvidia-319-updates, right click and install - it will take care of dependencies. reboot after this is done

-now in synaptic find bumblebee and bumblebee-nvidia. install them and it will take care of the dependencies.

Simple, you should now be sorted. You can run any program on your dedicated card using optirun Test it by doing
"" --------------------------------------

but no joy

I am now going to try nvidia-prime v0.5 according to this
1. Firstly, purge Bumblebee if installed:
				sudo apt-get purge bumblebee*

• Also, make sure libvdpau-va-gl1 is not enabled system-wide because it causes Nvidia Settings to crash on start - if it is, either disable it or simply remove the package:
&#8728; sudo apt-get purge libvdpau-va-gl1

		2. Install the proprietary Nvidia drivers and the Nvidia Prime package:
				sudo apt-get install nvidia-319 nvidia-settings-319 nvidia-prime

 ********• note-http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-bumblebee-nvidia-prime-gt650m-on-ubuntu-13-10-an
************&#8728; I have Nvidia GF745M and I use Ubuntu 14.04 You have to install Nvidia 331 or above! and nvidia prime. Steam games works perfectly! 

		3. Reboot the system.
"----------------------------------------

Wish me luck

---

### Post by markackerman8@gmail.com on 2014-02-23
Again and Again - at least I will go down in history as being persistent - or STUPID arghhhhhh

I will bore you with the details below.  In a nutshell I installed in Ubuntu 14.04-64bit fresh - nvidia-331 nvidia-settings-331 and nvidia prime (v 0.5.?) and all its' dependencies.

I got to a nice login screen but after that things were optimistic but after logging in it always ended up with a descent background screen and movable mouse but nothing else at all - nothing (no panels at all - empty).  Curiously better than a black screen I suppose.  

I went into TTY2 and logged in to find no xorg.conf file so I ran nvidia.xconf and nano'd the new file in /etc/X11/ to see it made my height and width '24'.  When I logged back in my new screen was just that a 24x24 nice screen but still dead other than an active mouse as was getting normal.

Am I at least getting somewhere with the nvidia driver functioning better than with a black screen?

Any new ideas?

Here are my notes of what I did in this attempt.  And I think I will give it a rest for a week or so unless some fresh ideas arise.  Thanks to all for helping,

Sincerely, Mark
------------------------------------------------------
from my Tomboy notes:

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
&#8728; take advantage of this Optimus feature in the Nvidia graphics drivers 319.12+: a package called "nvidia-prime", which comes with a set of tools that enable Nvidia's Prime on MUXless systems
&#8728; This package automatically checks if your system supports Nvidia Optimus and the required packages, creates the xorg.conf file and tweaks the LightDM configuration to support this.
&#8728; But to be able to take advantage of this feature in the latest Nvidia drivers, you need up-to-date dependencies (such as Randr 1.4, Xorg 1.13 - that's what the initial Nvidia release notes mention, but it seems you actually need 1.14 -, Linux Kernel 3.9 with some special flags enabled), as well as a custom xorg.conf file and some other bits.
&#8728; Multiple monitors don't work out of the box; to enable multiple monitors, you need to edit the xorg.conf file, comment <Option "UseDisplayDevice" "none"> and add the devices sections as explained HERE;f you're using Ubuntu 13.10 Saucy Salamander or 14.04 Trusty Tahr and want to test the Optimus support in the Nvidia Graphics Drivers 319.12+, here's what you need to do:

		1. Firstly, purge Bumblebee if installed:
				sudo apt-get purge bumblebee*

• Also, make sure libvdpau-va-gl1 is not enabled system-wide because it causes Nvidia Settings to crash on start - if it is, either disable it or simply remove the package:
&#8728; sudo apt-get purge libvdpau-va-gl1

		2. Install the proprietary Nvidia drivers and the Nvidia Prime package:
				sudo apt-get install nvidia-319 nvidia-settings-319 nvidia-prime
&#8227; Mark's note after adding
•  nvidia-prime  (v 0.5.7 Yahoo - Optimism!!)
&#8728; additional packages were bbswitch-dkms dkms fakeroot libfakeroot
• nvidia-331
&#8728; additional packages were nvidia-settings screen-resolution-extras and libvdpau1 libcuda1-331 and other libs
• nvidia-settings-319

&#8728; note-http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-bumblebee-nvidia-prime-gt650m-on-ubuntu-13-10-an
&#8227; I have Nvidia GF745M and I use Ubuntu 14.04 You have to install Nvidia 331 or above! and nvidia prime. Steam games works perfectly! 

		3. Reboot the system.
-----------------------------------------------------

• [http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html2](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html2). 
&#8728; 1. nvidia-prime 0.5 has been released today with a new feature that allows users to switch between the integrated and discrete GPU ("prime-select" command line tool). 
&#8227; Other changes include:
• improved hardware detection - make sure the the laptop uses Nvidia Optimus and Nvidia driver >= 319;
• more robust system to deal with xorg.conf: broken xorg.conf files will be automatically restored to a configuration that works with hybrid graphics;
• make sure that NVIDIA is always enabled on shutdown - this will avoid issues with the BIOS;
&#8227; more.
• nvidia-prime is a package that comes with a set of tools to enable Nvidia's Prime on MUXless systems.
• Currently, nvidia-prime 0.5 is available in the Ubuntu 14.04 Trusty Tahr proposed repository and it will take a while before it's promoted to the main repositories.
&#8728; 2. Thanks to the latest nvidia-prime, we can also see a change in Nvidia Settings that landed about two weeks ago in Ubuntu 14.04 Trusty Tahr: an additional tab was added, allowing users to switch between GPUs:
• This tab is only visible if nvidia-prime >= 0.5 is installed. After changing between the Nvidia and Intel GPUs, you'll need to log out or restart the system to apply the changes.
&#8728; 3. And finally, xorg-server was updated (version 1.14.4.901) with various Nvidia Optimus fixes, including a patch to fix GPU screen output hotplugging. Like the latest nvidia-prime, this update is only available in the Ubuntu Trusty proposed repository for now.
• In my test under Ubuntu 14.04 LTS with these updates installed, I noticed some important improvements: there's no more screen / GTK theme corruption, my external monitor works out of the box (connected via a mini DisplayPort port that's hard-wired to the Intel graphics adapter; connecting a monitor via HDMI which is hard-wired to the Nvidia card doesn't work) and the temperature seems lower than in my previous experience with this under Ubuntu 13.10, although it's still a bit too hot for everyday use, at least with my laptop.
--------------------------------------------------

• [http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-bumblebee-nvidia-prime-gt650m-on-ubuntu-13-10-an](http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-bumblebee-nvidia-prime-gt650m-on-ubuntu-13-10-an)
&#8728; I have Nvidia GF745M and I use Ubuntu 14.04 You have to install Nvidia 331 or above! and nvidia prime. Steam games works perfectly!

---

### Post by markackerman8@gmail.com on 2014-02-24
bumpity bump

---

### Post by zomgwhat on 2014-02-24
that's a shame that it didn't work...it did for me anyway, and we have almost the exact same hardware! the ubuntu crew have done a good job supporting it as much that you should be able to get optimus going through GUI tools and package managers without 'manually' doing anything... can you elaborate on what exactly went wrong when you followed my instructions? you have a black screen when you boot up? was that after or before you installed nvidia's drivers? so you can't do a graphical login at all? 


sounds like you've had a nightmare. I wouldn't bother using 14.04 yet, it's still in alpha stage so it will be very unreliable. have you tried installing windows (much better native support for optimus), and verified optimus works, just to test it isn't a hardware fault?

---

