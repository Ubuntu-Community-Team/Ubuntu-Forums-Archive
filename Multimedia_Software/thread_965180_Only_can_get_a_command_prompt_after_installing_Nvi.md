---
title: "Only can get a command prompt after installing Nvidia 177.80 drivers"
date: 2008-10-31
forum: Multimedia Software
---

### Post by Spinalcracker on 2008-10-31
After installing Intrepid 8.10 and doing all available updates through synaptic, I went to install the Nvidia driver (177.80). I have tried doing this four separate ways, all with the same result.

1. Hardware manager and choosing enable.
2. Synapic, selecting the driver and modules
3. EnvyNG
4. ctl-alt-F2, login, stopping gdm, sudo sh NVIDIA-177.80.run etc etc

In each and every case the driver installs without error. Upon reboot, the screen blinks a couple times after the ubuntu progression splash is done and then drops to a text command prompt to login.

What's worse is at the command line if I manually edit xorg.conf (which is still supposed to override HAL to my understanding), to use the "nv" driver, or the "vesa" driver it still only boots to the command prompt. If I try to purge the nvidia driver at that point, same thing. Only boots to command prompt. Only way for me to get a graphical interface back is to do a full re-install. I had zero issues in Hardy and manually updated the driver on every new version put out, ran games through wine etc. I am baffled on this one.

I am realllllly hoping someone can help. I would like to continue using Ubuntu.

Motherboard: EVGA 780i
Processor: Intel 8400duo
Video Card: 8800GT x 2 SLI

Thanks guys

------------------------------------------------------------------------------------------------------------------------

*Edit:

**_SOLUTION 1:_**

A solution posted later in this thread has worked for me.  Some may still have issues even after following the fix.  Here is what I did as suggested by those kind enough to post.

System->Administration->Hardware Drivers
 - Activate the 177.80 drivers
 - DO NOT RESTART YET

Open a terminal and enter the following


```
sudo lspci | grep VGA
```

The output will be something like the following;

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

Take note of the number at the start.  This is the BusID.  In this example it's 01:00:0

Then in terminal type 

```
sudo gedit /etc/X11/xorg.conf 
```

Add or edit the Device section, putting your Busid that you noted earlier in.  

***NOTE: The above method of Busid discovery reads as ##:##.# format, but in xorg.conf you must type it in with all full colons ##:##:# Not with a period before the last digit ***

ie

Section "Device"
Identifier "Configured Video Device"
Busid "PCI:1:0:0"
Driver "nvidia"
EndSection

If you have a sli setup it should look like this

Section "Device"
Identifier "Configured Video Device"
Busid "PCI:1:0:0"
Driver "nvidia"
Option "sli"   "auto"
EndSection

Save.  Reboot and your driver should now be working. =)

------------------------------------------------------------------------------------------------------------------------

*** NOTE: If this does not work, others have had success with Infoseeker's solution.  Here is a cut and paste of his post.

------------------------------------------------------------------------------------------------------------------------

**_SOLUTION 2:_**

I spent days trying to get the 177.80 drivers to work and I almost gave up. What eventually sorted my problem was to remove (uninstall) EVERYTHING in Synaptic that started with Nvidia, ie. Nvidia-glx, Nvidia-settings, all envy... stuff, etc. I then searched through the current command path (find yours by: 'echo $PATH' at prompt) and REMOVED (deleted) all commands beginning with 'Nvidia........' (I found 2 more)

BTW my path is :
Quote:
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
The subdirectories are, listed:
/usr/local/sbin
/usr/local/bin
/usr/sbin
/usr/bin
/sbin
/bin
/usr/games

I then rebooted into 'recovery mode' and installed the drivers that way (root prompt), as directed below:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Copied and pasted here:
Quote:
To download and install the drivers, follow the steps below:

STEP 1: Review the NVIDIA Software License.

You will need to accept this license prior to downloading any files.

STEP 2: Download the Driver File

Download - NVIDIA-Linux-x86-177.80.pkg1.run

SuSE users: please read the SuSE NVIDIA Installer HOWTO before downloading the driver.

STEP 3: Install
Type "sh NVIDIA-Linux-x86-177.80-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X server configuration file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README.

If you have any questions or problems, please check the NVIDIA Linux discussion forum. If you don't find an answer to your question there, you can send email (in English) to [email]linux-bugs@nvidia.com[/email].

When emailing [email]linux-bugs@nvidia.com[/email], please attach an nvidia-bug-report.log, which is generated by running "nvidia-bug-report.sh".
To download the driver I had to right-click the file and select 'save link as'

After installing I rebooted the PC.

Please make sure you have 'build-essential' package installed (for compiling, etc).

I tested the driver by issuing
Quote:
$ glxgears
at the prompt (should give you a nice animation and something like
Quote:
$ glxgears
56706 frames in 5.0 seconds = 11341.130 FPS
56715 frames in 5.0 seconds = 11336.110 FPS
56510 frames in 5.0 seconds = 11301.919 FPS
The 'Nvidia X Server Settings' appears under "Applications--->System Tools' in the menu.

P.S. I have a Nvidia 9600GT and a Core2Duo CPU with 32bit Ubuntu (x86).
I hope this might help somebody.
-------------------------------------------------------------------------------------------------------------------------

A third solution has been suggested.  [Here.]("http://www.tranquillity.se/2008/11/10/nvidia-problems-in-ubuntu-810/")  Below is a cut and paste of it

-------------------------------------------------------------------------------------------------------------------------

**_SOLUTION 3:_**
 
   1. In a terminal, run sudo apt-get install module assistant
   2. In a terminal, run sudo m-a auto-install nvidia
   3. Open the &#8220;Hardware Drivers&#8221; application and pick the driver you want (177 in my case) and click Activate. If it worked alright, you&#8217;ll get the green recycle icon  
      and be asked to reboot to activate the settings.
-------------------------------------------------------------------------------------------------------------------------

Thank you for all that gave these suggestions, and for all that posted to get this resolved.  Intrepid is awesome with working 3D video :P

-------------------------------------------------------------------------------------------------------------------------

---

### Post by nunquamsecutus on 2008-10-31
I have the same issue.  I have tried doing an update and a clean install.  I have tried both the 173 and 177 drivers.  I have ran dpkg-reconfigure on xorg. 

My setup is:
Mobo: Gigabyte GA-M750SLI-DS4
Processor: AMD Phenom e9350
Graphics: nforce 8500gt

---

### Post by irishdunn on 2008-10-31
Same issue on my card using the Nvidia bin drivers while blacklisting nv and trying the 177 and 173 drivers. I get dropped into tty1 and have to rip everything out.

This is on a clean install of 8.10

My Setup:
Processor: Q6600
Mobo: Abit IP35-pro XE
Gfx: Nvidia GTX260, and 7950GT (Quad monitors)

---

### Post by Icewielder on 2008-10-31
Same problem, have tried both 173 and 177 drivers from Hardware devices, Adept, Nvidia Website. No luck. After installing the driver it either boots to "Checking battery state"  or a Text Login. I have tried several methods to repair X and remove the driver. Reinstall is the only thing that works. 

Hardware:
CPU: Q6660 Quad 
Mobo: Nvidia 650i (I believe gotta check when I get home)
Ram: 4GB
GPU: 8800GT x2 SLI

I have the same problem in both Kubuntu, Ubuntu, Xubuntu.
I will try what is suggested here tonight:
[http://ubuntuforums.org/showthread.php?t=964472&page=2](http://ubuntuforums.org/showthread.php?t=964472&page=2)

Thanks for the help!

---

### Post by sirchmeister on 2008-10-31
Adding myself to the list.

EVGA 680i
E8400 C2D
2x 8800 GT (SLI)
8.10 (64 bit/Desktop)

---

### Post by sirchmeister on 2008-10-31
Is everyone here using 64bit?

---

### Post by nunquamsecutus on 2008-10-31
I am running 64bit.

---

### Post by sirchmeister on 2008-10-31
Me too and so is SpinalCracker. I am about to install 32 bit and I will let you know how it turns out.

---

### Post by shadowplane676 on 2008-10-31
Add me to the list. re-installed Intrepid (32bit) about 12 times, tried many different ways to install the Nvidia drivers. Every one results in a broken X (error: no devices detected and no screens found) and only a command prompt. this was for both the 173 and 177 drivers. I dont have a bloody clue whats causing this. Hardy ran GREAT...*shrug*

I have 2 8600GTs
AMD 939 4000
2GB ram
DFI SLi-DR expert board

---

### Post by sirchmeister on 2008-10-31
Ah so 32bit doesn't work either? I guess I'll scrap trying that out then.
I'm just coming back to Ubuntu after a long long hiatus. If this isn't resolved by tomorrow night I'll be right back to Windows.

---

### Post by Xivory on 2008-10-31
Same issue  =[

---

### Post by mmcmonster on 2008-10-31
Same issue on 32-bit.  Nvidia 6200 card (I believe).

---

### Post by Freyfuron on 2008-10-31
Same problem on:

Ubuntu Intrepid Ibex 8.10
Athlon XP 2400+ (32 bit)
NVIDIA Geforce 4 Ti 4200 with AGP8x

---

### Post by Icewielder on 2008-10-31
If anyone wants to get back to a desktop without reinstall. Go to recovery mode and do normal boot. Get to the text based login. 
Then do:

```
sudo nano /etc/X11/xorg.conf

```
Change the line that has "nvidia" in it to nv.
now do:
```
sudo apt-get remove dkms
sudo apt-get install dkms
```

Should start up, still no driver though, but it will let you experiment more!

---

### Post by ryanthegeek on 2008-10-31
Same issue here on a 9800gtx

---

### Post by zackiv31 on 2008-10-31
Same problem here... 64-bit with dual 6600GT's..

---

### Post by Icewielder on 2008-10-31
Can someone file a bug report? I am at work and can't. I believe the issue may have something to do with the xen kernel. Reason being is if I force the official nvidia driver from their site it causes the same problem, and nvidia doesn't like xen. I "think" thats where our problem lies.

---

### Post by rotary12 on 2008-10-31
check this thread: ( [http://ubuntuforums.org/showthread.php?t=965313](http://ubuntuforums.org/showthread.php?t=965313) )


As i know Ubuntu 8.10 dont supports nvidia legacy and nvidia glx driver, because nvidia didnt make support for xorg 7.4, this means that proprietary drivers will not work with your video card, and you will not have desktop effects  . This is nvidia's foult, they were lazy to create support! Luckily, I have ati video card  In fact if proprietary drivers would not work, you can use open source drivers and effects are working !


read about it in different threats

---

### Post by Icewielder on 2008-10-31
The Nvidia drivers DO support our cards, also please explain how others have gotten it to work if the drivers just don't work. I KNOW others with 8800GT's have gotten it to work just fine with both 173 and 177.

---

### Post by Spinalcracker on 2008-10-31
dagrump gave me a good suggestion

* I found scribbles, you need to identify your primary video card in your xorg.conf file, it appears to be BusId 1:0:0 Of course lspci to to get busid. I'm lookin at junk I tried. Search the intrepid archives, I know this was discussed there.


I think he is on to something here, as the xorg logs do show it is not determining the device.  I can not test this atm.  Is anyone able to try this out and confirm if this works.  If not, I will attempt it as soon as I can.

---

### Post by Immolatus on 2008-11-01
As far as I know the 177.x drivers are for the "9" series cards. I'm running the 177 drivers with a geforce 9600 with Intrepid no problem.

---

### Post by Spinalcracker on 2008-11-01
> **Immolatus said:**
> As far as I know the 177.x drivers are for the "9" series cards. I'm running the 177 drivers with a geforce 9600 with Intrepid no problem.

The 177.80 driver is for a lot of nvidia cards.  According to nVidia's website it's good for:

NVIDIA GeForce GPUs
NVIDIA GPU product 	
GeForce 6800 Ultra 	
GeForce 6800 	
GeForce 6800 LE 	
GeForce 6800 XE 	
GeForce 6800 XT 	
GeForce 6800 GT 	
GeForce 6800 GT 	
GeForce 6800 GS 	
GeForce 6800 XT 	
GeForce 7800 GTX 	
GeForce 7800 GTX 	
GeForce 7800 GT 	
GeForce 7800 GS 	
GeForce 7800 SLI 	
GeForce Go 7800 	
GeForce Go 7800 GTX 	
GeForce 6800 GS 	
GeForce 6800 	
GeForce 6800 LE 	
GeForce 6800 XT 	
GeForce Go 6800 	
GeForce Go 6800 Ultra 	
GeForce 6800 	
GeForce 6600 GT 	
GeForce 6600 	
GeForce 6200 	
GeForce 6600 LE 	
GeForce 7800 GS 	
GeForce 6800 GS 	
GeForce 6800 Ultra 	
GeForce 6600 	
GeForce 6600 LE 	
GeForce 6600 VE 	
GeForce Go 6600 	
GeForce 6610 XL 	
GeForce Go 6600 TE/6200 TE 	
GeForce 6700 XL 	
GeForce Go 6600 	
GeForce Go 6600 GT 	
GeForce 6200 	
GeForce 6500 	
GeForce 6200 TurboCache(TM) 	
GeForce 6200SE TurboCache(TM) 	
GeForce 6200 LE 	
GeForce Go 6200 	
GeForce Go 6400 	
GeForce Go 6200 	
GeForce Go 6400 	
GeForce 6250 	
GeForce 7100 GS 	
GeForce 8800 GTX 	
GeForce 8800 GTS 	
GeForce 8800 Ultra 	
Tesla C870 	
GeForce 7350 LE 	
GeForce 7300 LE 	
GeForce 7300 SE/7200 GS 	
GeForce Go 7200 	
GeForce Go 7300 	
GeForce Go 7400 	
GeForce 7500 LE 	
GeForce 7300 GS 	
GeForce 6800 	
GeForce 6800 LE 	
GeForce 6800 GT 	
GeForce 6800 XT 	
GeForce 6200 	
GeForce 6200 A-LE 	
GeForce 6150 	
GeForce 6150 LE 	
GeForce 6100 	
GeForce Go 6150 	
GeForce Go 6100 	
GeForce 7900 GTX 	
GeForce 7900 GT/GTO 	
GeForce 7900 GS 	
GeForce 7950 GX2 	
GeForce 7950 GX2 	
GeForce 7950 GT 	
GeForce Go 7950 GTX 	
GeForce Go 7900 GS 	
GeForce Go 7900 GTX 	
GeForce 7600 GT 	
GeForce 7600 GS 	
GeForce 7900 GS 	
GeForce 7950 GT 	
GeForce 7650 GS 	
GeForce 7600 GT 	
GeForce 7600 GS 	
GeForce 7300 GT 	
GeForce 7600 LE 	
GeForce 7300 GT 	
GeForce Go 7600 	
GeForce Go 7600 GT 	
GeForce 6150SE nForce 430 	
GeForce 6100 nForce 405 	
GeForce 6100 nForce 400 	
GeForce 6100 nForce 420 	
GeForce 8600 GTS 	
GeForce 8600 GT 	
GeForce 8600 GT 	
GeForce 8600GS 	
GeForce 8400 GS 	
GeForce 9500M GS 	
GeForce 8600M GT 	
GeForce 9650M GS 	
GeForce 8700M GT 	
GeForce 8400 SE 	
GeForce 8500 GT 	
GeForce 8400 GS 	
GeForce 8300 GS 	
GeForce 8400 GS 	
GeForce 8600M GS 	
GeForce 8400M GT 	
GeForce 8400M GS 	
GeForce 8400M G 	
GeForce 9400 GT 	
GeForce 9300M G 	
GeForce 7150M / nForce 630M 	
GeForce 7000M / nForce 610M 	
GeForce 7050 PV / NVIDIA nForce 630a 	
GeForce 7050 PV / NVIDIA nForce 630a 	
GeForce 7025 / NVIDIA nForce 630a 	
GeForce GTX 280 	
GeForce GTX 260 	
GeForce 8800 GTS 512 	
GeForce 8800 GT 	
GeForce 9800 GX2 	
GeForce 8800 GS 	
GeForce 8800M GTS 	
GeForce 8800M GTX 	
GeForce 8800 GS 	
GeForce 9600 GSO 	
GeForce 8800 GT 	
GeForce 9800 GTX/9800 GTX+ 	
GeForce 9800 GTX+ 	
GeForce 9800 GT 	
GeForce 9600 GT 	
GeForce 9600 GS 	
GeForce 9800M GTS 	
GeForce 9700M GTS 	
GeForce 9800M GTS 	
GeForce 9500 GT 	
GeForce 9600M GT 	
GeForce 9600M GS 	
GeForce 9600M GT 	
GeForce 9500M G 	
GeForce 9300 GS 	
GeForce 8400 GS 	
GeForce 9300M GS 	
GeForce 9200M GS 	
GeForce 9300M GS 	
GeForce 7150 / NVIDIA nForce 630i 	
GeForce 7100 / NVIDIA nForce 630i 	
GeForce 7050 / NVIDIA nForce 610i 	
GeForce 9100M G 	
GeForce 8100P 	
GeForce 8300 	
GeForce 8200 	
nForce 730a 	
GeForce 8200 	
nForce 780a SLI 	
nForce 750a SLI 	
GeForce 8100 / nForce 720a

---

### Post by mmcmonster on 2008-11-01
And yet I am having problems with my Geforce 6100 card on 32bit Intrepid (I don't want to try the 64 bit version). :-(

```
$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)

```

---

### Post by Rott3n on 2008-11-01
same problem
7800gt's SLI
32bit

---

### Post by sirchmeister on 2008-11-01
Has this issue gotten a bug report yet?

I did a completely fresh, completely new (As in, 8.10 released, no beta, no alpha) install.

Installing the restricted drivers and rebooting causes the computer to come to a command prompt. I have done NOTHING else with this computer and tried this numerous times.

I have reinstalled a few times and changed the methods in which I install 177 and I get the same results. I get the Ubuntu loading screen but when it goes into booting the interface I get a flicker and I am dropped into a command prompt.

This is all done with a completely new installation and no packages or hardware installed prior to performing the restricted drivers upgrade. This is an issue that needs to be looked in to. If anyone here knows whether or not this has been filed somewhere could you please point me to it? Else I am going to create a report.

---

### Post by pigphish on 2008-11-01
Same issue on HP dv9225us (dv9000 series) with NVIDIA GeForce Go 7600. 

Tried envyng with 177 and 173 (as well as others).

---

### Post by sirchmeister on 2008-11-01
This is pathetic. I whiped my Windows install because I got sick of it and then I come over to Ubuntu which in the past has seemed to work well enough and upon a completely fresh install I cannot even install restricted drivers.

What's worse is you see so many people with this exact same problem and everyone responding to them hasn't the slightest clue that its a bigger problem that goes beyond just one or two people having it.

---

### Post by jblackthorne on 2008-11-01
After reading this thread, I thought I would chime in with a bit more info that might help others:

The Nvidia 177.80 drivers have a lot of compatibility issues.  I am not trying to defend Ubuntu by saying it is a 3rd party issue. However, I personaly think that Ubuntu should have taken more responsibility with all the Nvidia issues..  Regardless, there is a very simple solution to most nvidia issues, try 177 and if it does not work then roll back to 173.  

Here are some specifics I have confirmed:

* Nvidia Geforce 8400 GS chipset
    * HP dv2700t laptop w/nv 8400 GS 
    * HP dv6700t laptop w/nv 8400 GS
Result: 177 does not work, but 173 does work. In fact, the upgrade of both laptops works perfectly once the nvidia driver is set to to the 173.

Problems with 177 include:
* <ctrl><alt><f1> - fails to switch to console
* Dual monitors do not display correctly
* terminal display results in corruption

If any one is having problems with the 8400 GS chipset and needs help, please post specifics of your problem.

---

### Post by sirchmeister on 2008-11-01
8800 GT here and neither 177 or 173 work.

---

### Post by Spinalcracker on 2008-11-01
I have two 8800GT's and have tried 177 and 173 drivers.  Same symptoms with either driver.

---

### Post by mmcmonster on 2008-11-01
It's not just the nvidia proprietary drivers, though.

On my 6100, using the 'nv' drivers (open source, right?), the highest resolution I could get was 800x600.  Interestingly enough, if I switched to the vesa driver I could get full resolution (but no hardware 3d, of course).

[COLOR=Red]There is [this bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/282214"), but probably more should be registered.[/COLOR]

---

### Post by sirchmeister on 2008-11-01
I've already reinstalled Windows. I guess I'll give Ubuntu another go here in a few months.

---

### Post by zackiv31 on 2008-11-01
I wouldn't know the first step to filing a bug report, but has someone done so?  It seems to be a widespread problem amongst many different cards... It also seems to be hit or miss, my dual screen setup at work upgraded with no hiccups, but my dual card/dual monitor setup at home has fallen prey to this bug.

---

### Post by Cambo on 2008-11-01
I was having the same problem of X not starting up after installing Intrepid. (We won't go into the mess that was created trying to upgrade Hardy :/ )

The answer I ended up working out was to add a Busid entry in the Device section of my /etc/X11/xorg.conf file.

To find the correct Busid, I used;

    sudo lspci | grep VGA

The output I got from this was;

    01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
    04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

(Yes, SLI :D )

So, I then edited the Device section of my /etc/X11/xorg.conf to read as follows;

    Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
    EndSection

A quick;

    sudo service gdm restart

and I was greeted by X running at the maximum resolution of my LCD monitor.

Hope that helps one or two of you.



Cambo

---

### Post by nunquamsecutus on 2008-11-01
I just created a bug report for this.
[https://bugs.launchpad.net/ubuntu/+bug/292312](https://bugs.launchpad.net/ubuntu/+bug/292312)

---

### Post by infoseeker on 2008-11-01
I spent days trying to get the 177.80 drivers (177.82 is now available) to work and I almost gave up.  What eventually sorted my problem was to uninstall everything (in Synaptic) that started with nvidia, ie. nvidia-glx, nvidia-settings, all envy... stuff, etc.  I then searched through the current command path (find yours by:  'echo $PATH' at prompt) and deleted all commands beginning with 'nvidia........' (I found 2 more in /usr/bin)

To download the driver I had to right-click the file and select 'save link as'.

Latest driver obtainable here ---> [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Please make sure you have 'build-essential' package installed (for compiling new driver).

I then rebooted into 'recovery mode' and installed the drivers that way (root prompt), as 'ctrl-alt-backspace' gave me no usable screens.

When in recovery mode, 'cd' to the directory where you downloaded the file (normally '/home/(user)' or '/home/(user)/Desktop'), and type "sh NVIDIA-Linux-x86-177.80-pkg1.run" to install the driver (simply enter 'sh N' and then press 'tab' button for auto-completion).  Ignore the errors...just do it ;).  When done...reboot.


The 'Nvidia X Server Settings' appears under "Applications--->System Tools' in the menu.

I have a Nvidia 9600GT and a Core2Duo CPU with 32bit Ubuntu Intrepid (x86).

I hope this might help somebody.



EDIT: This procedure will have to be followed each time an updated driver is downloaded, or if the kernel is changed/updated in some way, although searching for nvidia... etc. stuff for removal/deletion need not be done.  Simply download the driver and reboot to 'recovery mode' for installation.

EDIT: I installed Ubuntu Intrepid 64bit version (x86_64).
EDIT: Installed 180.08 driver the same way - aok.
EDIT: Installed 180.11 driver the same way - aok.
EDIT: Installed 180.16 driver the same way - aok.
EDIT: Installed 180.29 driver the same way - aok.
EDIT: Installed Kubuntu 9.04 (x86-32bit) and 180.51 driver - AOK
EDIT: Installed 180.53 driver the same way - aok.

---

### Post by UBUpat on 2008-11-01
I am new to ubuntu and linux. I have same problem. my card is Nvidia 9400GT. 
I can't find it in the Hardware drivers to enable it.
So i did the installation and all necessary steps and i reach to a point telling me :
               " No matching precompiled kernel interface was found on the Nvidia ftp site. This means the installer will need to compile a kernel interface for your kernel"

when i click YES , i got another message : 

                    " You don't appear to have libc header files installed on your system. Please install distribution libc development package"

Then i did : apt-get install libc . i got message " can't be founf"

then i did : apt-get install libc6 . i got message " is the newest version found installed . 0 updates"


can you please help me what to do ?
thank you alot

---

### Post by infoseeker on 2008-11-01
Make sure you have 'build-essential' package installed (for compiling, etc)

---

### Post by UBUpat on 2008-11-01
Where to check that ? can u tell me plz step by step

---

### Post by Hazer on 2008-11-01
Just run:
```
sudo apt-get install build-essential
```

to install the drivers:

make sure you are root during installation by typing ```
sudo su
```

and have stopped the x server by typing ```
/etc/init.d/gdm stop
``` (as root)

and then write down the filename of the drivers, change to the drivers directory and run ```
sh "name of the driver".run
```to install and if it asks to download precompiled kernel interface say no

---

### Post by infoseeker on 2008-11-01
> **UBUpat said:**
> Where to check that ? can u tell me plz step by step
The 'build-essential' package has to be shown as installed in 'Synaptic Package Manager' (green square on left);

Otherwise you can issue at prompt (in Terminal program in menu under 'Applications-->Accessories'):
> sudo apt-get install build-essential

The reply will tell you whether the package has been installed or not.

---

### Post by UBUpat on 2008-11-01
Thank you so much "Hazard" . It worked ! now my Nvidia 9400Gt is installed. thank you again.
Oh i just notice also "infoseeker" replied me as well , thank you guys.

---

### Post by ryanthegeek on 2008-11-01
I followed Infoseeker's instructions to a T with no luck.  Same result every time.  I'm not exactly a noob, but I am not advanced either so maybe I did something wrong.

I am running an athlon 6400x2, 9800gtx.

---

### Post by infoseeker on 2008-11-01
> **ryanthegeek said:**
> I followed Infoseeker's instructions to a T with no luck.  Same result every time.  I'm not exactly a noob, but I am not advanced either so maybe I did something wrong.

I am running an athlon 6400x2, 9800gtx.

Check and see if you are running the 32- (i386) or 64bit (amd64) version of Ubuntu and make sure you select the corresponding nvidia driver.

Issue this at the prompt to check:```
$ uname -a
Linux (hostname) 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux
```
Mine is i386

---

### Post by ryanthegeek on 2008-11-01
It is the 32bit version of Ubuntu and the nvidia driver.  I also have been messing around for a couple of days.  I may just nuke and install again.

---

### Post by 12pcwormburner on 2008-11-01
64bit amd - 8800gt

I got it working by doing (almost) exactly what info seeker did.

I went to the Synaptic Package manager, searched for Nvidia and removed absolutely everything (even the NV) package.

Then, just as infoseeker did, I typed: echo $PATH in the terminal, went to all the directories and deleted anything refering to Nvidia. 

Then I rebooted into Recovery Mode, went to a prompt.
Now when I tried to install the 177.80 drivers it stated that I should goto runlevel 3 to properly install the drivers, so I did.

After the install, I rebooted and the drivers are working just perfectly.

Kudos infoseeker, it worked great for me.

---

### Post by zackiv31 on 2008-11-01
Is this the preferred solution?  Will this make its way into the ubuntu packages at some point (I mean techinically they're the same version right?... why isn't the ubuntu package working?)  I can't suffer downtime again (having to reinstall), and I know Ubuntu recommends installing packages from apt instead of running the nvidia installer...

---

### Post by ryanthegeek on 2008-11-02
Nuked loaded from ubuntu live cd (previous was alternate install).  Same result.  When I look for nvidia in the locations list at $PATH, I don't find anything listed.  Is this my problem, am I missing something?

Thank you in advance for any help.

---

### Post by Hazer on 2008-11-02
Well if you've nuked the install then you don't need delete the nvidia stuff, I will give you a step by step.

Open up a terminal and type in these commands:
```
sudo su
wget http://uk.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run
```

That downloads the drivers.

Now write this down on paper or something : NVIDIA-Linux-x86-177.80-pkg1.run

and run ```
/etc/init.d/gdm stop
```

then:
```
sh NVIDIA-Linux-x86-177.80-pkg1.run
```

you need to write it down because when you are installing you won't be able to look up filename

During install if it asks to download a precompiled kernel interface say no and let it build one.

---

### Post by klj on 2008-11-02
Cambo's suggestion about adding the BusID entry in xorg.conf worked for me
 with 8800 GTS in SLI. Thanks a lot!!!

Really dissappointed that this doesn't work out of the box, though.

---

### Post by coffeecat on 2008-11-02
Cambo's suggestion worked for me too - with a Geforce 6200 card.

One minor detail to beware of - the appropriate line of lspci gave me:

```
02:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
```... but in xorg.conf, I had to put this line:

```
Busid    "PCI:02:00:0"
```Notice the point in the busid number from lspci, but a colon in xorg.conf. If you use a point in xorg.conf, it won't work. Cambo shows this in his post, but I thought I would spell it out.

**Edit:** Oops! :oops: I spoke too soon. Very odd. I was posting from Ibex with the proprietary nvidia driver, but when I did a reboot, the xserver wouldn't start - got the hangup at the 'reading battery state'. Xfix from a failsafe boot made things worse by rewriting xorg.conf without a Device section. So I followed **Icewielder**'s suggestion. (Remove the nvidia stuff by uninstalling and reinstalling dkms and use the 'nv' driver.) At least I've got a usable desktop now.

---

### Post by leafpaul on 2008-11-02
Using Mythbuntu and 7300GS (64bit amd) I get the same problem using the 177 driver both using the Nvidia install and the built in Hardware drivers tool (with the latter the 173 driver also gives the same problem).  Curiously though if I try to install the 169 or 173 drivers using the Nvidia install it refuses to install stating that I appear to have a Xen kernel.

I had similar results with both the upgrade from 8.04 and from a clean install of Mythbuntu 8.10, none of the solutions so far suggested work for me.

---

### Post by Spinalcracker on 2008-11-02
I can confirm Cambo's suggestion worked for me.  Adding the BusID did the trick.  I had tried this earlier but had chosen the wrong card in a two card sli, so if you are running sli, you may have to try both.

---

### Post by Icewielder on 2008-11-02
Cambo's solution confirmed working. Thanks!

---

### Post by cookieforyou on 2008-11-02
Infoseeker, my nvidia card is working like an Nvidia card once again :)
Thanks

---

### Post by zackiv31 on 2008-11-02
Cambos Solution kinda worked for me... but I have dual screens and only one of my screens is working...  I added the Busid section, but there was only one.  Going to try to manually add the other to see if that changes anything..

EDIT: So manually adding the second card worked for me (note: I don't have them SLI'ed)  But my X was crazy slow/screwed up (terminal was all funky looking).  I solved this by running:

sudo nvidia-settings 

from within X.  From there I setup my card through the configuration (Enabling the second monitor that was now detected), and also enabling Xinerama.  I saved the configuration file and got some error about how it couldn't parse my xorg.conf... I just continued and had it write out the xorg.conf.  I restarted X and everything is now snappy again... although my xorg.conf has a lot more crap in it now.


Err... one thing I did notice, I'm getting an error I got back when I tried to upgrade from Hardy->Intrepid... can be seen in this thread:

[http://ubuntuforums.org/showthread.php?t=963878](http://ubuntuforums.org/showthread.php?t=963878)

Basically running anything from Terminal that opens an X window yields:

```
Xlib:  extension "RANDR" missong on display ":0.0".
```

---

### Post by nunquamsecutus on 2008-11-02
Using both Infoseeker's and Cambo's instructions I now have everything working.  Thanks!

The installer asked me to go to run level 3 and I selected no to continue with the install and everything worked out fine.

---

### Post by zackiv31 on 2008-11-02
Update from me...  my X only works half the time... sometimes when I log in my keyboard input dies after a bit, and the menus simply do not work... They change color when they're clicked, but no menu is dropped down... I have to restart X until it randomly decides to work...

Not exactly ideal.


EDIT:  Dunno what happened, but I restarted and I can't even get into X anymore... tried purge remove all nvidia stuff, and xfix... also tried the failsafe xorg (vesa)... nothing... screen just flickers and always back to the command prompt.  Staying away from this nvidia crap until 9.04 probably :-/

EDIT2:  Even after a fresh install without touching NVIDIA my comp hangs randomly at certain times... wtffffff  So maybe nvidia was installed correctly and Intrepid/my comp sucks...

---

### Post by Dittie on 2008-11-02
Unfortunately, none of the suggestions have worked for me. I'm currently downloading the cd so that I can try a clean install and see if that works.

I'm running an HP Pavillion dv6704nr with AMD64 X2 dual-core 1.90Mhz and an Nvidia GeForce 7150M graphics card. Using ubuntu 32-bit.

---

### Post by anth120 on 2008-11-02
I'm still having the problem after tying out both solutions in this thread. I have a GeForce 8800 GTS 320mb card.

I love troubleshooting these sorts of things but this has already eaten most of my day. I'll be dealing with windows for a few days until this gets solved.

---

### Post by boddhisatva on 2008-11-03
I've got 7300 GT. I followed Infoseeker's suggestion and installed the driver from NVidia's page. Unfortunately, it doesn't work either. Worse, now I can't install the driver in Ubuntu (when I run the proprietary drivers utility and select 177, there's an error and the driver won't start).

---

### Post by Spinalcracker on 2008-11-03
Did you add the BusId to the xorg.conf?

---

### Post by boddhisatva on 2008-11-03
Yes, I did. I tried all variants, even AGP instead of PCI (I reasoned that since the card is AGP...). 
I'm now using the generic 'nv' instead of 'nvidia' in xorg.conf. The resolution is OK, but there is no 3D and no effects. Of course, I can't run applications such as Blender, which is my main tool.
If nothing pops up within a couple of days, I'll have to reinstall 8.04

---

### Post by boddhisatva on 2008-11-03
I might just add that when X starts (and it does, after I agree to load lowres settings) I get the following error message:

(EE) NVIDIA(0) Failed to load the NVIDIA Kernel Module
(EE) NVIDIA(0)***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

I don't know if other people have it that way.

---

### Post by Dittie on 2008-11-03
I get that same error message.

I've just done a clean install and here I sit in 800x600. I am going to go through and do all of the suggestions again to see if they work this time around.

---

### Post by Dittie on 2008-11-03
Ok, after a fresh install, I went through and did what Infoseeker mentioned(quoted below), and it worked perfectly :)

> **infoseeker said:**
> I spent days trying to get the 177.80 drivers to work and I almost gave up.  What eventually sorted my problem was to remove (uninstall) EVERYTHING in Synaptic that started with Nvidia, ie. Nvidia-glx, Nvidia-settings, all envy... stuff, etc.  I then searched through the current command path (find yours by:  'echo $PATH' at prompt) and REMOVED (deleted) all commands beginning with 'Nvidia........' (I found 2 more)

BTW my path is : 

The subdirectories are, listed:
/usr/local/sbin
/usr/local/bin
/usr/sbin
/usr/bin
/sbin
/bin
/usr/games

I then rebooted into 'recovery mode' and installed the drivers that way (root prompt), as directed below:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Copied and pasted here:


To download the driver I had to right-click the file and select 'save link as'

After installing I rebooted the PC.

Please make sure you have 'build-essential' package installed (for compiling, etc).

I tested the driver by issuing at the prompt (should give you a nice animation and something like 

The 'Nvidia X Server Settings' appears under "Applications--->System Tools' in the menu.

P.S. I have a Nvidia 9600GT and a Core2Duo CPU with 32bit Ubuntu (x86).
I hope this might help somebody.

---

### Post by Spinalcracker on 2008-11-03
> **Dittie said:**
> Ok, after a fresh install, I went through and did what Infoseeker mentioned(quoted below), and it worked perfectly :)

I have modified my first post to include the two known workarounds for this bug to make it easier for people to attempt them.  I hope the mods sticky this thread, as I am seeing a ton of new ones popping up with similar issues.

Thanks everyone that is posting here.  I am sure there are lots that are benefiting that are not posting so it's great that people took the time to help.  Thank you.  Definitely helped me out.

---

### Post by pmartino on 2008-11-03
> **boddhisatva said:**
> I might just add that when X starts (and it does, after I agree to load lowres settings) I get the following error message:

(EE) NVIDIA(0) Failed to load the NVIDIA Kernel Module
(EE) NVIDIA(0)***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

I don't know if other people have it that way.

I had the same error after upgrading to ibex. The problem is presumably in the way nvidia dirver is handled by the new Ubuntu.
Until 8.04, nvidia was already compiled for the current kernel and was available in linux-restricted-modules.

In Ibex, external modules use DKMS (Dynamic Kernel Module Support). This is much more flexible but requires a compilation of the module for your current kernel. You must have installed either the kernel source or the headers (apt-get install linux-headers-generic). This should be automatic but there is presumably a missing dependency.

I thus installed the headers and then automatically (without even re-installing them), Ubuntu compiled and installed nvidia, virtualbox and kqemu kernel modules that were selected but not functional.

Hope it will work in your case too.

Pierre

---

### Post by boddhisatva on 2008-11-03
> **pmartino said:**
> I had the same error after upgrading to ibex. The problem is presumably in the way nvidia dirver is handled by the new Ubuntu.
Until 8.04, nvidia was already compiled for the current kernel and was available in linux-restricted-modules.

In Ibex, external modules use DKMS (Dynamic Kernel Module Support). This is much more flexible but requires a compilation of the module for your current kernel. You must have installed either the kernel source or the headers (apt-get install linux-headers-generic). This should be automatic but there is presumably a missing dependency.

I thus installed the headers and then automatically (without even re-installing them), Ubuntu compiled and installed nvidia, virtualbox and kqemu kernel modules that were selected but not functional.

Hope it will work in your case too.

Pierre

The headers were installed. I've installed the linux source and the kernel package. What do I do next? At what point did Ubuntu compile and install the modules?

---

### Post by Dittie on 2008-11-03
Ok, I seem to have a new problem now :)

I had installed the driver and it all worked fine. So I went on and added in kde4.1 as this is my preferred desktop. Rebooted again and now I get the graphical login, type in my login info, hit enter and it flickers and goes right back to the login screen again.

Anyone know what would cause this? I suppose I could just install kubuntu, but I'd rather not have to do yet another install.

---

### Post by kodoku on 2008-11-03
> **Dittie said:**
> Ok, I seem to have a new problem now :)

I had installed the driver and it all worked fine. So I went on and added in kde4.1 as this is my preferred desktop. Rebooted again and now I get the graphical login, type in my login info, hit enter and it flickers and goes right back to the login screen again.

Anyone know what would cause this? I suppose I could just install kubuntu, but I'd rather not have to do yet another install.

Actually, I installed Kubuntu and getting the same errors as everyone else. If I install nvidia-glx-177, boot stalls with "Checking Battery State.." If I install nvidia-glx-173, I go straight to text login. I think it may have to do with nvidia's drivers not working with the latest Xorg version.

System specs:
Athlon 64 2X
Nvidia 6150SE
Kubuntu 8.10

---

### Post by zackiv31 on 2008-11-03
So these fixes worked for me... but I was still having crazy hanging/X issues with Gnome... if others users run into this stuff, from my testing, its not a driver issue (as I had it with nvidia driver and the nv driver)... I switched to XFCE, and haven't had any X issues.

So if others are having weird X issues, and they happen with both the nvidia and nv driver, look elsewhere for a solution.

---

### Post by deonbekende on 2008-11-04
See my post here for a solution:

[http://ubuntuforums.org/showthread.php?t=965587&page=3]("http://ubuntuforums.org/showthread.php?t=965587&page=3")

This probably is not the best and efficient solution, but it worked for me.

---

### Post by sedawk on 2008-11-04
Hello!

Same problem here with a brand new Hybrid-SLI PC.
I also ended up reinstalling Ubuntu because I failed to
to make the default configuration with vesa driver work again.

What I want to add to this discussion is this:

* Check /var/log/Xorg.0.log when you only get text mode.
  Here it complained about not seeing any screens!
  Make backups of this file to compare different workarounds.
* What is really needed is some easy way to remove the
  nvidia stuff if something goes wrong. E.g simply editing
  xorg.conf and changing the driver (to vesa or nv) doesn't
  help - in Xorg.0.log you can still see NVidia stuff at work (glx?).

What I want to achieve is this:
* Get working graphics with nvidia driver
* Find out which of the nvidia devices listed with "lspci" is
  responsible for slow graphics (onboard) and which for fast 
  graphics ("expansion card").

---

### Post by ryanthegeek on 2008-11-06
Finally, I got it to work.  I followed Infoseekers instructions, I tried Cambo's fix.  Nothing worked!

I removed my Hauppauge hvr-1600 and it worked.  Just to verify I reinstalled the card and I booted to low resolution.

Now, because I dual boot.  Does anyone know how I can keep the nvidia drivers and leave the card in?  I don't care if the card is none functioning in ubuntu (although it would be nice).

Thank you all for your help

---

### Post by boddhisatva on 2008-11-07
Having tried all the tricks on the forums for several days, I did a fresh 8.10 install and it's working. The installation process takes some 10-15 minutes! Then it's just a question of reinstalling your applications (I've got screenshots of my menus) and you're done. The settings are untouched, even the wallpaper and panels (I wasn't sure about that). Much easier and smoother than doing system acrobatics or waiting for mercy
Of course, you need to download and burn the ISO first, if you don't have it.
I don't know if it's going to work for everybody, but that's what other people have shared too.

By the way, I've got nvidia 7300 GT. The 177 driver is working fine now.
I also did the most recent updates before installing the driver (there are some kernel modules updates right after you install the system).

---

### Post by Deronius on 2008-11-07
I'd just like to say...

I love you SpinalCraker.  After a couple of days of trying to get the 177 drivers working your solution worked.

Thanks,
Deron

---

### Post by Spinalcracker on 2008-11-07
> **ryanthegeek said:**
> Finally, I got it to work.  I followed Infoseekers instructions, I tried Cambo's fix.  Nothing worked!

I removed my Hauppauge hvr-1600 and it worked.  Just to verify I reinstalled the card and I booted to low resolution.

Now, because I dual boot.  Does anyone know how I can keep the nvidia drivers and leave the card in?  I don't care if the card is none functioning in ubuntu (although it would be nice).

Thank you all for your help

Please check out this thread.

[http://ge.ubuntuforums.com/showpost.php?p=5118928&postcount=20]("http://ge.ubuntuforums.com/showpost.php?p=5118928&postcount=20")

I copied and pasted the fix from it below.


--------------------------------------------------------------------------

To get your hauppuage card working:

# go to tty1, to remove the old firmware you installed
$ sudo /etc/init.d/?dm stop
$ cd pathToV4LDir # in my case ~/v4l*
$ sudo make unload
$ sudo make install -r

# you can now, if you want
$ sudo /etc/init.d/?dm start
# and go back to tty7
$ sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
$ cd ~/v4l*
$ sudo make
$ sudo make install

now after you copy those firmware files you posted about earlier to /lib/firmware/*currentKernel*

$ sudo reboot
$ dmesg | grep cx18
# near the end should say something like:
[ 42.230394] cx18-0: Initialized card #0: Hauppauge HVR-1600

from there its works pretty well in mythtv. And remember every time there is a kernel update you will have to recompile v4l:
$ cd ~/v4l*
$ sudo make unload
$ sudo make disclean
$ sudo make
$ sudo make install
copy all the firmware to the new kernel directory and reboot

also if you are trying to use this with the nvidia drivers, don't ask me why but it dosn't seem to work out well. follow this guide and you should get the two working togethar. <-- That worked for me when I was ok with using the driver version from the repo. I just bought an 9600 and now have to use the nvidia installer, if you do to try adding:
vmalloc=192M pci=nommconf
to /boot/grub/menu.lst on the kernel line like:

## ## End Default Options ##
title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=f70a49f8-885a-4942-904b-56a0ae6f68bc ro quiet splash rootflags=data=writeback vmalloc=192M pci=nommconf
initrd /boot/initrd.img-2.6.24-18-generic
quiet

--------------------------------------------------------------------------

If the above fix does not work because mercurial can be a pain for some, you can grab the latest drivers from here

[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2]("http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2")

The drivers are built into the Kernel but there probably has been bug fixes etc since the dev freeze.

Then add the

```
vmalloc=192M pci=nommconf
```

to /boot/grub/menu.lst as suggested above.  

I hope this helps.  Hard to offer suggestions when I don't have that card to play with.

---

### Post by ryanthegeek on 2008-11-07
Thanks Spinalcracker,
I am at work now, I will try it when I get home.

---

### Post by ryanthegeek on 2008-11-07
thank you spinalcracker!  

The card seems to be working (kinda in vlc).  I am now playing with mythtv.  Unless anyone has a better idea?

---

### Post by Dittie on 2008-11-07
I ended up going with this solution for my nvidia card. It's been several days and I'm in the right resolution and all that fun stuff.

[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/#before](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/#before)

---

### Post by boddhisatva on 2008-11-08
I'm really amazed you people choose to go into all of this, instead of doing a fresh install in a matter of minutes. :rolleyes:

---

### Post by alwayshere on 2008-11-08
i had this problen i had to start in safe mode and go to "sessions" and make sure pulseaudio session manager 

you may need to add  it by clicking add in command box put
 pactl load-module module-x11-xsmp

in name box put 

PulseAudio Session Management

comment box put 

Load module-x11-xsmp into PulseAudio


hope this helps

---

### Post by Dittie on 2008-11-08
> **boddhisatva said:**
> I'm really amazed you people choose to go into all of this, instead of doing a fresh install in a matter of minutes. :rolleyes:

I did a fresh install(twice). Still wasn't working.

---

### Post by boddhisatva on 2008-11-08
> **Dittie said:**
> I did a fresh install(twice). Still wasn't working.

Did you actually format the partition?
If so, I take back what I wrote.

---

### Post by lewac on 2008-11-08
the first solution worked for me! now to get this 2nd monitor working... but a great deal of thanks is in order for getting my FIRST monitor to launch X! yeah I was getting the same issue after installing and enabling this nvidia 177.80 driver... no screen found... come on it worked fine in hardy!

---

### Post by Hubris2 on 2008-11-09
If you're formatting your partition and doing a complete reinstall, you'll have to reinstall anything not done by package manager, not to mention anything installed that has a config stored outside your home directory.  Sure, I could have a working machine again in fairly short order with a complete reinstall, but it might take a long time to make it MY machine again.


> **boddhisatva said:**
> Did you actually format the partition?
If so, I take back what I wrote.

---

### Post by unc0nn3ct3d on 2008-11-09
> **Hubris2 said:**
> If you're formatting your partition and doing a complete reinstall, you'll have to reinstall anything not done by package manager, not to mention anything installed that has a config stored outside your home directory.  Sure, I could have a working machine again in fairly short order with a complete reinstall, but it might take a long time to make it MY machine again.


Exactly.. This is a machine that I have a personal connection with.. Reformating it and doing all that over might solve my problem in minutes but destroys what took months to get to..

None of these solutions have worked for me and I've dumped about 7 hours into this god damn problem.. I just can't believe Ubuntu would release something without finding this error.. At least I can just roll back to -19

---

### Post by boddhisatva on 2008-11-09
> **Hubris2 said:**
> If you're formatting your partition and doing a complete reinstall, you'll have to reinstall anything not done by package manager, not to mention anything installed that has a config stored outside your home directory.  Sure, I could have a working machine again in fairly short order with a complete reinstall, but it might take a long time to make it MY machine again.

I retrieved all the most important programs and settings fairly quickly and I DO feel like it's my machine :D. (Perhaps more so, because it's clutter-free now). It did take some time, but here I am, fully functional again 8). Actually, it was an opportunity to see how much stuff I didn't really need and to clean up the system in one fell swoop. Of course, it's a matter of personal taste and degree of attachment to your customized configuration, but I felt that since I couldn't really USE my machine (and didn't know when I would be able to do so), it's better to do a bit of quick housecleaning and then get down to work again. I'm really happy with this move, now I've got a perfect configuration which I'm going to back up and keep for another such panic-stricken moment. Actually, isn't it the thing to do before any upgrade? - have a backup copy of your system. That would have spared us all that trouble.
Having said that, I hope all those still suffering from the nvidia/canonical oversight will soon find a working solution.

---

### Post by Mazehero55 on 2008-11-09
When I do that command I get:

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)

Is this okay?
I put it in like '*Busid "PCI:0:d:0"*'

---

### Post by Spinalcracker on 2008-11-10
A third solution has been suggested.  I have added it to my first post so it's easier to find for people new to this thread.  Source reference is in my first post, but here is the bottom line.

----------------------------------------------------------------------------

1. In a terminal, run sudo apt-get install module assistant
2. In a terminal, run sudo m-a auto-install nvidia
3. Open the “Hardware Drivers” application and pick the driver you want (177 in my case) and click Activate. If it worked alright, you’ll get the green recycle icon and be asked to reboot to activate the settings.

----------------------------------------------------------------------------

Good luck :)

---

### Post by Predklaw on 2008-11-23
I just wanted to say thanks for everyone posting here, still an Ubuntu noob and the forums are a great resource. Ive tried just about every fix with no luck... its been a few crazy days but after i found this thread im glad to say that infoseekers post did the trick for me... (at least for now ive rebooted and still good). At first i didnt think it worked as there were no drivers listed under System>Admin>Hardware Drivers but after trying nvidia-settings it indeed came up and i saw that the 177.82 drivers were installed and working. Thanks again


64bit Intrepid Ibex
EVGA 680i
Intel Core 2 Quad 9300
(2) Nvidia GeForce 8800GTX 786mb

---

### Post by myjr52 on 2008-12-02
I had the same problem with my computer and I did three-times clean installs.

My hardware details are as follows:

Model: Dell XPS 710
Processor: Interl Core 2 Quad-Core, QX6600
Graphic Card: DUAL SLI 256MB nVidia GeForce 8600GTS

It works with the solution 1 in below. Thank you very much. It saved me a lot of time and of course, lots of headache. 

------------------------------
SOLUTION 1:

A solution posted later in this thread has worked for me. Some may still have issues even after following the fix. Here is what I did as suggested by those kind enough to post.

System->Administration->Hardware Drivers
- Activate the 177.80 drivers
- DO NOT RESTART YET

Open a terminal and enter the following


Code:

sudo lspci | grep VGA

The output will be something like the following;

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

Take note of the number at the start. This is the BusID. In this example it's 01:00:0

Then in terminal type

Code:

sudo gedit /etc/X11/xorg.conf

Add or edit the Device section, putting your Busid that you noted earlier in.

***NOTE: The above method of Busid discovery reads as ##:##.# format, but in xorg.conf you must type it in with all full colons ##:##:# Not with a period before the last digit ***

ie

Section "Device"
Identifier "Configured Video Device"
Busid "PCI:1:0:0"
Driver "nvidia"
EndSection

If you have a sli setup it should look like this

Section "Device"
Identifier "Configured Video Device"
Busid "PCI:1:0:0"
Driver "nvidia"
Option "sli" "auto"
EndSection

Save. Reboot and your driver should now be working. =)

---

### Post by Lupusceleri on 2008-12-08
> **infoseeker said:**
> I spent days trying to get the 177.80 drivers (177.82 is now available) to work and I almost gave up.  What eventually sorted my problem was to uninstall everything (in Synaptic) that started with nvidia, ie. nvidia-glx, nvidia-settings, all envy... stuff, etc.  I then searched through the current command path (find yours by:  'echo $PATH' at prompt) and deleted all commands beginning with 'nvidia........' (I found 2 more in /usr/bin)

To download the driver I had to right-click the file and select 'save link as'.

Latest driver obtainable here ---> [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Please make sure you have 'build-essential' package installed (for compiling new driver).

I then rebooted into 'recovery mode' and installed the drivers that way (root prompt), as 'ctrl-alt-backspace' gave me no usable screens.

When in recovery mode, 'cd' to the directory where you downloaded the file (normally '/home/(user)' or '/home/(user)/Desktop'), and type "sh NVIDIA-Linux-x86-177.80-pkg1.run" to install the driver (simply enter 'sh N' and then press 'tab' button for auto-completion).  Ignore the errors...just do it ;).  When done...reboot.


The 'Nvidia X Server Settings' appears under "Applications--->System Tools' in the menu.

P.S. I have a Nvidia 9600GT and a Core2Duo CPU with 32bit Ubuntu Intrepid (x86).

I hope this might help somebody.

EDIT: I installed Ubuntu Intrepid 64bit version (x86_64).
EDIT: Installed 180.08 driver the same way - aok.
EDIT: Installed 180.11 driver the same way - aok.

I figure I should necro this thing, since this post fixed my graphical-card-low-resolution-with-nvidia issues. :)

Thanks and ++!

---

### Post by cookieforyou on 2008-12-13
> I then rebooted into 'recovery mode' and installed the drivers that way (root prompt), as 'ctrl-alt-backspace' gave me no usable screens.
Is this still the way to install the nvidia drivers, or have the drivers in the repos been updated?

---

### Post by mrtortoise on 2008-12-14
Thanks cambo and myjr52 , I've attempted to get nvidia drivers working with my 8800 GT for a couple of weeks now and updating xorg.conf with the Busid worked like a charm. My steps were to: activate the nvidia drivers (177), find the busid of my card using lspci, update xorg.conf to include the busid, and reboot.

---

### Post by Gurgeh on 2009-01-02
Sweet, The first one worked for me. I have twin 6800 GTO's running on an AMD 64 (3.2Ghz) on Intrepid.

Quick point, it was the 2nd card on the lspci list for me.

Thanks again.

---

### Post by pushin50 on 2009-01-03
> **boddhisatva said:**
> I retrieved all the most important programs and settings fairly quickly and I DO feel like it's my machine :D. (Perhaps more so, because it's clutter-free now). It did take some time, but here I am, fully functional again 8). Actually, it was an opportunity to see how much stuff I didn't really need and to clean up the system in one fell swoop. Of course, it's a matter of personal taste and degree of attachment to your customized configuration, but I felt that since I couldn't really USE my machine (and didn't know when I would be able to do so), it's better to do a bit of quick housecleaning and then get down to work again. I'm really happy with this move, now I've got a perfect configuration which I'm going to back up and keep for another such panic-stricken moment. Actually, isn't it the thing to do before any upgrade? - have a backup copy of your system. That would have spared us all that trouble.
Having said that, I hope all those still suffering from the nvidia/canonical oversight will soon find a working solution.

Gotta say . . . I'm with Boddhisatva on this one. After a couple of weeks of trying all these fixes, the fresh 8.10 install from ISO image CD was the thing that did the trick. Depends, I guess, on how deeply you're invested in apps you've loaded into your current set-up. For me, it was an afternoon of cleaning up, including the opportunity to wipe out lots of other little bugs and previous errors caused by me. Main issue to be aware of, other than apps themselves, is potential loss of browser bookmarks, cookies etc.

For me, clean update saved a lot of time and aggravation. One other note - I changed from default 800x600 resultion to 1024x768. Nvidia Settings Manager wrote a new xorg.conf file with this change but was not permitted to replace the pre-existing xorg.conf file. Result was reversion back to 800x600 default resolution on log-out or re-boot. I fixed that by copying and pasting, as sudo, the entire nvidia config file into xorg.conf (replacing all prior active content) and then saving over the old xorg.conf. Works great - now at 1024x768 permanently.

---

### Post by pushin50 on 2009-01-03
Forgot to say . . . thanks so much to all for the REALLY good suggestions and methods on this thread; best of many I've read on the topic. Although my system was to ****ed up to benefit from these, I'm sure one of the three solutions is the right fix for many out there with the nvidia driver problem on upgrade to 8.10.

---

### Post by ed-koala on 2009-01-08
Ok, I'm ready to take the plunge and try these 3 main solutions.  However, I don't want to have to reinstall (yet again) if a solution doesn't work.

Could anyone list how to UNDO each solution if it boots to a TTY command line so I can get graphics (of any kind) back on reboot??

---

### Post by OLFP on 2009-01-09
3 months now and no fix? Is Slant 6 running Ubuntu now? Seriously, I haven't posted on a linux forum in years, but this issue has pissed me off so much, that I was inspired to sign up here.

I have GeForce 9600 card. I'd rather not have to screw with drivers every time there is a kernel update, so I used the 180 driver in the repos, which , by the way is also outdated now.  

System -> Administration -> Hardware Drivers doesn't even show the 180 as an option, so use synaptic an select everything with 180 in it, and remove anything that doesn't have 180 in it. Visit the nvidia link posted earlier to make sure this is the driver you need.

You will have to use lspci and edit xorg.conf (make a backup first) as posted earlier.  You can do everything to this point in your desktop environment. Ubuntu will not detect the new driver on it's own, and you will not get a "System Restart Required message"

Reboot.  I had to take a few stabs at the xorg.conf. The first two times I got a blank screen with the drum beat. I had to ctrl alt f1 to get to a console to edit xorg.conf.  pkill gdm does not work, just reboot from the CLI after each edit.

When you get into your Desktop go to System -> Preferences -> Appearance -> Visual Effects and select Normal or High. Then the driver will be detected and you should be good to go.

As far as undoing failed attempts. You don't have to go through the whole install process again to get graphics back. From the grub menu, just select the previous working kernel image, and undo your changes in a nice GUI.

Or, after gdm fails to load or you don't have an ealier image, you can use dpkg-query from the CLI to get the names of the installed packages that aren't working. If it lists a version, then it's probably installed. Once you know their names, use apt-get to remove the offenders.

```

:~$ dpkg-query -l 'nv*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
un  nvidia-173-kernel-source       <none>                         (no description available)
pn  nvidia-173-modaliases          <none>                         (no description available)
pn  nvidia-177-kernel-source       <none>                         (no description available)
pn  nvidia-177-modaliases          <none>                         (no description available)
ii  nvidia-180-kernel-source       180.11-0ubuntu1~intrepid1      NVIDIA binary kernel module source
ii  nvidia-180-modaliases          180.11-0ubuntu1~intrepid1      Modaliases for the NVIDIA binary X.Org driver
un  nvidia-71-kernel-source        <none>                         (no description available)
pn  nvidia-71-modaliases           <none>                         (no description available)
un  nvidia-96-kernel-source        <none>                         (no description available)
pn  nvidia-96-modaliases           <none>                         (no description available)
rc  nvidia-common                  0.2.4                          Find obsolete NVIDIA drivers
un  nvidia-glx                     <none>                         (no description available)
un  nvidia-glx-173                 <none>                         (no description available)
un  nvidia-glx-173-dev             <none>                         (no description available)
rc  nvidia-glx-177                 177.82-0ubuntu0.1              NVIDIA binary Xorg driver
un  nvidia-glx-177-dev             <none>                         (no description available)
ii  nvidia-glx-180                 180.11-0ubuntu1~intrepid1      NVIDIA binary Xorg driver
ii  nvidia-glx-180-dev             180.11-0ubuntu1~intrepid1      NVIDIA binary Xorg driver development files
un  nvidia-glx-71                  <none>                         (no description available)
un  nvidia-glx-71-dev              <none>                         (no description available)
un  nvidia-glx-96                  <none>                         (no description available)
un  nvidia-glx-96-dev              <none>                         (no description available)
un  nvidia-glx-dev                 <none>                         (no description available)
un  nvidia-glx-dev-envy            <none>                         (no description available)
un  nvidia-glx-dev-legacy          <none>                         (no description available)
un  nvidia-glx-dev-legacy-envy     <none>                         (no description available)
un  nvidia-glx-dev-new             <none>                         (no description available)
un  nvidia-glx-dev-new-envy        <none>                         (no description available)
un  nvidia-glx-envy                <none>                         (no description available)
un  nvidia-glx-ia32                <none>                         (no description available)
un  nvidia-glx-legacy              <none>                         (no description available)
un  nvidia-glx-legacy-envy         <none>                         (no description available)
un  nvidia-glx-lrm-dev             <none>                         (no description available)
un  nvidia-glx-new                 <none>                         (no description available)
un  nvidia-glx-new-envy            <none>                         (no description available)
un  nvidia-glx-src                 <none>                         (no description available)
un  nvidia-kernel-source           <none>                         (no description available)
un  nvidia-kernel-source-envy      <none>                         (no description available)
un  nvidia-kernel-src              <none>                         (no description available)
un  nvidia-legacy-kernel-source    <none>                         (no description available)
un  nvidia-legacy-kernel-source-en <none>                         (no description available)
un  nvidia-new-kernel-source       <none>                         (no description available)
un  nvidia-new-kernel-source-envy  <none>                         (no description available)
ii  nvidia-settings                177.78-0ubuntu2.1              Tool of configuring the NVIDIA graphics driver 
```

---

### Post by libremax on 2009-01-16
I had the same issue for a week. I tried the solution 1, drivers 173 and 177 but it didn't change anything. So, just after my last reinstallation, I used synaptic instead of the Hardware Drivers tool to install the 180 driver, then I made a new xorg.conf with NVIDIA X Server Settings and added the BusID line. Compiz works well, I didn't find any fault otherwise.

---

### Post by Gooseman240 on 2009-02-19
> **Icewielder said:**
> If anyone wants to get back to a desktop without reinstall. Go to recovery mode and do normal boot. Get to the text based login. 
Then do:

```
sudo nano /etc/X11/xorg.conf

```
Change the line that has "nvidia" in it to nv.
now do:
```
sudo apt-get remove dkms
sudo apt-get install dkms
```

Should start up, still no driver though, but it will let you experiment more!

:guitar:

Man you guys rock... I was getting depressed trying to get out of the command prompt.  I feel like a kid learning to walk trying to figure this out, I just have to remember Ubuntu Forums, 

U GUYS ROCK!!

---

### Post by L3g@cY on 2009-02-26
Thank you for helping. This was my first ubuntu install and it went ok - It was the dual video cards that did it for me. Using the second card in the list of both was what worked also. Now I'm currently gaming with Wine playing CS:S - WoW - L4D - COD4 - TF2 so i'm very happy with everything!! thank you all

---

### Post by GSF1200S on 2009-03-07
> **Spinalcracker said:**
> After installing Intrepid 8.10 and doing all available updates through synaptic, I went to install the Nvidia driver (177.80). I have tried doing this four separate ways, all with the same result.

1. Hardware manager and choosing enable.
2. Synapic, selecting the driver and modules
3. EnvyNG
4. ctl-alt-F2, login, stopping gdm, sudo sh NVIDIA-177.80.run etc etc

In each and every case the driver installs without error. Upon reboot, the screen blinks a couple times after the ubuntu progression splash is done and then drops to a text command prompt to login.

What's worse is at the command line if I manually edit xorg.conf (which is still supposed to override HAL to my understanding), to use the "nv" driver, or the "vesa" driver it still only boots to the command prompt. If I try to purge the nvidia driver at that point, same thing. Only boots to command prompt. Only way for me to get a graphical interface back is to do a full re-install. I had zero issues in Hardy and manually updated the driver on every new version put out, ran games through wine etc. I am baffled on this one.

I am realllllly hoping someone can help. I would like to continue using Ubuntu.

Motherboard: EVGA 780i
Processor: Intel 8400duo
Video Card: 8800GT x 2 SLI

Thanks guys

------------------------------------------------------------------------------------------------------------------------

*Edit:

**_SOLUTION 1:_**

A solution posted later in this thread has worked for me.  Some may still have issues even after following the fix.  Here is what I did as suggested by those kind enough to post.

System->Administration->Hardware Drivers
 - Activate the 177.80 drivers
 - DO NOT RESTART YET

Open a terminal and enter the following


```
sudo lspci | grep VGA
```

The output will be something like the following;

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

Take note of the number at the start.  This is the BusID.  In this example it's 01:00:0

Then in terminal type 

```
sudo gedit /etc/X11/xorg.conf 
```

Add or edit the Device section, putting your Busid that you noted earlier in.  

***NOTE: The above method of Busid discovery reads as ##:##.# format, but in xorg.conf you must type it in with all full colons ##:##:# Not with a period before the last digit ***

ie

Section "Device"
Identifier "Configured Video Device"
Busid "PCI:1:0:0"
Driver "nvidia"
EndSection

If you have a sli setup it should look like this

Section "Device"
Identifier "Configured Video Device"
Busid "PCI:1:0:0"
Driver "nvidia"
Option "sli"   "auto"
EndSection

Save.  Reboot and your driver should now be working. =)

------------------------------------------------------------------------------------------------------------------------

*** NOTE: If this does not work, others have had success with Infoseeker's solution.  Here is a cut and paste of his post.

------------------------------------------------------------------------------------------------------------------------

**_SOLUTION 2:_**

I spent days trying to get the 177.80 drivers to work and I almost gave up. What eventually sorted my problem was to remove (uninstall) EVERYTHING in Synaptic that started with Nvidia, ie. Nvidia-glx, Nvidia-settings, all envy... stuff, etc. I then searched through the current command path (find yours by: 'echo $PATH' at prompt) and REMOVED (deleted) all commands beginning with 'Nvidia........' (I found 2 more)

BTW my path is :
Quote:
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
The subdirectories are, listed:
/usr/local/sbin
/usr/local/bin
/usr/sbin
/usr/bin
/sbin
/bin
/usr/games

I then rebooted into 'recovery mode' and installed the drivers that way (root prompt), as directed below:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Copied and pasted here:
Quote:
To download and install the drivers, follow the steps below:

STEP 1: Review the NVIDIA Software License.

You will need to accept this license prior to downloading any files.

STEP 2: Download the Driver File

Download - NVIDIA-Linux-x86-177.80.pkg1.run

SuSE users: please read the SuSE NVIDIA Installer HOWTO before downloading the driver.

STEP 3: Install
Type "sh NVIDIA-Linux-x86-177.80-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X server configuration file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README.

If you have any questions or problems, please check the NVIDIA Linux discussion forum. If you don't find an answer to your question there, you can send email (in English) to [email]linux-bugs@nvidia.com[/email].

When emailing [email]linux-bugs@nvidia.com[/email], please attach an nvidia-bug-report.log, which is generated by running "nvidia-bug-report.sh".
To download the driver I had to right-click the file and select 'save link as'

After installing I rebooted the PC.

Please make sure you have 'build-essential' package installed (for compiling, etc).

I tested the driver by issuing
Quote:
$ glxgears
at the prompt (should give you a nice animation and something like
Quote:
$ glxgears
56706 frames in 5.0 seconds = 11341.130 FPS
56715 frames in 5.0 seconds = 11336.110 FPS
56510 frames in 5.0 seconds = 11301.919 FPS
The 'Nvidia X Server Settings' appears under "Applications--->System Tools' in the menu.

P.S. I have a Nvidia 9600GT and a Core2Duo CPU with 32bit Ubuntu (x86).
I hope this might help somebody.
-------------------------------------------------------------------------------------------------------------------------

A third solution has been suggested.  [Here.]("http://www.tranquillity.se/2008/11/10/nvidia-problems-in-ubuntu-810/")  Below is a cut and paste of it

-------------------------------------------------------------------------------------------------------------------------

**_SOLUTION 3:_**
 
   1. In a terminal, run sudo apt-get install module assistant
   2. In a terminal, run sudo m-a auto-install nvidia
   3. Open the “Hardware Drivers” application and pick the driver you want (177 in my case) and click Activate. If it worked alright, you’ll get the green recycle icon  
      and be asked to reboot to activate the settings.
-------------------------------------------------------------------------------------------------------------------------

Thank you for all that gave these suggestions, and for all that posted to get this resolved.  Intrepid is awesome with working 3D video :P

-------------------------------------------------------------------------------------------------------------------------

Haha! Looked all over google- nothing. Come to the Ubuntu forums and the first search result works for me. Thanks. Solution 1 was painless and worked like a charm.

2x 9800GTX+ SLI here, on a x58 Rampage 2 mobo

---

### Post by taintedhand on 2009-05-24
I don't know if anyone has tried the Nvidia 180 drivers, I have a clean install of 9.04 Jaunty running with SLI 8500GT. The first solution from Spinalcracker worked seamlessly with the 180 drivers. Just an update for those who may be wondering...

---

