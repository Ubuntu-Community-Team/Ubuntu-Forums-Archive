---
title: "Ubuntu 12.04 AMD driver issues"
date: 2013-08-29
forum: Multimedia Software
---

### Post by Christian Heinrichs on 2013-08-29
Level of experience: Beginner

Hello ubuntu forums,

since setting up a UEFI dual boot with Windows 8 x64 and Ubuntu 12.04 x64 I am trying to install the graphic drivers properly.
The graphics card I am using is AMD Radeon HD 7670M.
When I install the proprietary driver with the Additional drivers program, Ubuntu boots with graphic errors so it becomes impossible to navigate.
I then have to use [this]("http://www.linuxtechtips.com/2012/12/amd-radeon-hd-7670m-on-ubuntu-1204.html") method to get Ubuntu working again.

According to [AMD's official drivers website]("http://support.amd.com/us/kbarticles/Pages/amdcatalyst13-4linreleasenotes.aspx") the graphics card is supported, but not Ubuntu 12.04.
According to the [Unofficial Wiki for the AMD Linux Driver]("http://wiki.cchtml.com/index.php/Hardware") the graphics card is not supported.
Additionally to fglrx not working, compiz is not working either.

I ran some tests as shown [here]("http://wiki.cchtml.com/index.php/Frequently_Asked_Questions#Installation") and the results are the following:

[LIST]
[*]less /var/log/Xorg.0.log: No "DRI Initialization Successful." message found 
[*]less /var/log/XFree86.0.log: File not found 
[*]glxinfo | grep direct: Shows 4 error messages and one information message 
[*]dmesg: fglrx entries are present, but I am not sure if they are the right ones 
[*]lsmod | grep fglrx: two fglrx entries appear 
[/LIST]


I hope you can help.

---

### Post by lukeiamyourfather on 2013-08-29
The official drivers support up to Ubuntu 12.10, not only Ubuntu 12.10 so you could try those if you want. The installer has an option to build Debian packages which install cleaner than simply overwriting everything with no way to remove it later. Also check to see if there's a PPA with the drivers, someone might have already created the proper packages.

---

### Post by Kevin_Arnold on 2013-08-29
Is your Ubuntu install completely up to date? I had to do an update/upgrade to use the latest driver.

```

sudo apt-get update && apt-get upgrade

```

Then I updated the driver.

---

### Post by Christian Heinrichs on 2013-08-29
> **lukeiamyourfather said:**
> Also check to see if there's a PPA with the drivers
How can I do that?

> **Kevin_Arnold said:**
> Is your Ubuntu install completely up to date?
I ran the two commands.
The system is up to date.

---

### Post by Christian Heinrichs on 2013-08-30
Bump

---

### Post by su:bhatta on 2013-08-30
Hi,
Please go through this help page:

 [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Enabling_Video_Hardware_Acceleration](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Enabling_Video_Hardware_Acceleration)

Has details of installing Fglrx in various ways.

---

### Post by Christian Heinrichs on 2013-08-30
> **bhattabhishek said:**
> 
Please go through this help page:

 [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Enabling_Video_Hardware_Acceleration](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Enabling_Video_Hardware_Acceleration)

I followed the instructions of point [3.2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_13.4.2C_special_case_for_Intel.2BAC8-AMD_hybrid_graphics").
All went well, until doing a reboot.
Graphic errors, no navigation possible.
So I had to start a text session and type:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
sudo apt-get remove --purge fglrx*
sudo aticonfig --initial

```
to make Ubuntu work normally with the standard drivers.

Any other suggestions?

After running those 3 commands, the fglrx driver seems to be partially installed.
The AMD Catalyst Control Center now starts up, the mouse pointer doesn't flicker anymore, compiz is working and the test results from my first post are different.
There are still some error messages in this test, so fglrx still has problems I suppose.

---

### Post by su:bhatta on 2013-08-31
I am currently using Fglrx-updates, which I installed from 'Softwares and Updates' and there seems to be no problem (as in section 2 of that help page). 

Also, I religiously do section 4( Enabling Video Hardware Acc) of that help page.

Suggest you try that once and see where it goes...

---

### Post by Christian Heinrichs on 2013-08-31
> **bhattabhishek said:**
> Suggest you try that once and see where it goes...
After trying [this]("http://www.linuxtechtips.com/2012/12/amd-radeon-hd-7670m-on-ubuntu-1204.html"), point [2.1]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installing_via_the_command_line") and point [3.2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_13.4.2C_special_case_for_Intel.2BAC8-AMD_hybrid_graphics") I get graphic errors, except that I get them all the time now.
The only difference this time was that I installed fglrx with the .run package instead of:
```
sudo apt-get install fglrx fglrx-amdcccle
```
Because I don't want to download the driver every time when it's already on the hard drive.

Now I am locked out of Ubuntu again.

---

### Post by Christian Heinrichs on 2013-09-01
Bump.

Please see my response above.
I really don't know how to approach this problem anymore.

---

### Post by Bucky Ball on 2013-09-01
*Thread moved to **Multimedia & Video**.*

Although beginner (but learning) you'll get better and more specific help here. Other forum users will play nice. ;)

My two cents worth, and a bit late, but perhaps something for the future: did you check in 'Additional Drivers' to start with for any available AMD drivers before the saga began?

---

### Post by Christian Heinrichs on 2013-09-01
Thanks for moving the thread to the right section.

Yes, I did check the Additional Drivers program.
Actually, that's where the problem began.

---

### Post by Yellow Pasque on 2013-09-01
What is output of:
```
lspci | grep VGA
```

---

### Post by su:bhatta on 2013-09-02
> **codingaround said:**
> Thanks for moving the thread to the right section.

Yes, I did check the Additional Drivers program.
Actually, that's were the problem began.

What options did you get in the Additional Drivers, did you get fglrx and fglrx-updates ? In case you chose fglrx and got problems you can try fglrx-updates.

Also, As suggested by Temujin, please give the output of 

```
lspci | grep VGA



```

---

### Post by Christian Heinrichs on 2013-09-02
> **Temüjin said:**
> What is output of:
```
lspci | grep VGA
```
The output of lspci | grep VGA is:
```
VGA compatible controller: Advanced Micro Devices, Inc [AMD/ATI] Thames [Radeon HD 7500M/7600M Series]
```

> **bhattabhishek said:**
> What options did you get in the Additional Drivers, did you get fglrx and fglrx-updates ?

[LIST]
[*]ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) 
[*]ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) 
[*]ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) 
[*]ATI/AMD proprietary FGLRX graphics driver (post-release updates) 
[/LIST]

---

### Post by su:bhatta on 2013-09-03
Suggest you go through these:

[http://askubuntu.com/questions/285989/ubuntu-raring-13-04-x64-amd-radeon-hd-7500m-7600m-fglrx-issue](http://askubuntu.com/questions/285989/ubuntu-raring-13-04-x64-amd-radeon-hd-7500m-7600m-fglrx-issue)

Also, this webiste([http://devgurus.amd.com/thread/160229](http://devgurus.amd.com/thread/160229)) refers to follow this page:

[http://www.linuxquestions.org/questions/slackware-14/catalyst-12-6-slackware-current-4175418112/#post4738010](http://www.linuxquestions.org/questions/slackware-14/catalyst-12-6-slackware-current-4175418112/#post4738010)

Might as well give these a try.

Best of luck.

---

### Post by Christian Heinrichs on 2013-09-03
> **bhattabhishek said:**
> Suggest you go through these
I tried every possible method by now.

[LIST]
[*]Install via the .run installer. Instructions by [Ubuntu documentation]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_13.4.2C_special_case_for_Intel.2BAC8-AMD_hybrid_graphics") 
[*]Create debian package and run it as described [here]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29") 
[*]Additional Drivers program install 
[*]sudo apt-get install fglrx fglrx-amdcccle 
[*]Tried [this]("http://www.linuxquestions.org/questions/slackware-14/catalyst-12-6-slackware-current-4175418112/#post4738010") special method. 
[/LIST]

They all result in graphic errors.
Ubuntu is now running again, but with the normal drivers and Ubuntu Dash Home seems to have a broken scrollbar now.

---

### Post by Yellow Pasque on 2013-09-03
Have you tried the latest Catalyst? (13-8 Beta2)

Here's how I would do it..

Start by making sure everything's purged (some of these commands will probably fail, but don't worry about it and keep going)
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

Get dependencies:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic fakeroot libqtgui4 unzip
```

If you're using the x86_64 architecture (64 bit):
```
sudo apt-get install lib32gcc1
```

Install

```
mkdir catalyst13.8beta && cd catalyst13.8beta
wget http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta2-linux-x86.x86_64.zip
unzip amd-catalyst-13.8-beta2-linux-x86.x86_64.zip
chmod +x amd-catalyst-13.8-beta2-linux-x86.x86_64.run
sudo ./amd-catalyst-13.8-beta2-linux-x86.x86_64.run --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

> Graphic errors, no navigation possible.
Be more specific. Does the error occur before the login screen or after you log in? Can you get to a terminal (Ctrl+Alt+F1)?

---

### Post by Bucky Ball on 2013-09-03
Not sure if you can squeeze anything out of this, but it fixed for poster there:

[http://ubuntuforums.org/showthread.php?t=2138977](http://ubuntuforums.org/showthread.php?t=2138977)

You might need to undo what's been done prior to attempting though. And is the driver you've been attempting to install from AMD?

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

* Temüjin ninja-ed me! Better explanation there. ;)

---

### Post by Christian Heinrichs on 2013-09-03
> **Temüjin said:**
> Be more specific. Does the error occur before the login screen or after you log in? Can you get to a terminal (Ctrl+Alt+F1)?
The error occurs at the login screen and after the login screen.
It goes like this:

Ubuntu boots and the login screen appears either split in two uneven halfs or full of weird graphic error stripes.
After login, the sidebar to the left does not show up and I can barely click on Shut Down.
The rest of the interface is unresponsive.
Terminal sessions via Ctrl+Alt+F1 do work, but sometimes even the terminal got those graphic errors.
I also followed your instructions for the beta driver installation and it gave me the exact same result.

As for Bucky's answer. I have to test those methods yet, if I find one that suits this system.

---

### Post by Bucky Ball on 2013-09-03
Have you tried the nomodset option? Would possibly at least get you to a usable screen.

Boot to menu list, select kernel you want to run on the list and hit 'e'; 
Locate the kernel line which ends in 'splash' or 'quiet' or a combination of both;
Add 'nomodset' at the end of that line (without apostrophes);
Follow instructions at bottom of page to save changes and continue with normal boot.

Does that get you to at least a usable screen? If so, great, but that won't stick on reboot. Easy enough to make the change permanent, though.

I realise this isn't fixing your original problem but might get you a bit closer and to something you can work with.

---

### Post by Christian Heinrichs on 2013-09-04
> **Bucky Ball said:**
> Have you tried the nomodset option?
The screen not showing up correctly isn't a problem anymore, because I can always uninstall the AMD driver from the console either with the .sh uninstall script or with sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

I am not sure how to tackle this problem anymore and I really don't want to stick with the standard drivers because of the performance.
After installing the driver be it via .deb package or .run installer, I tried to check if the graphics card is a hybrid with aticonfig --pxl, but it only shows me the current configuration.

The standard drivers work without problems, except one:
I remember that in the Dash Home the scrollbar kind of bounces when you scroll to the very top/bottom, but this effect is gone.

---

### Post by Yellow Pasque on 2013-09-04
If you're "stuck" with open-source drivers for a card that new, the best thing you could do would be to run Ubuntu 13.04 with this PPA: [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)

You would also need a 3.11 kernel and turn on radeon dpm for best performance: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

### Post by Christian Heinrichs on 2013-09-04
> **Temüjin said:**
> The best thing you could do would be to run Ubuntu 13.04 with this PPA
I just did a little research on the system specs and it turns out, that the system has hybrid graphics if I understand it right.
The graphics card is an AMD Radeon HD 7670M as mentioned already and the processor is an Intel® Core&#8482; i7-3630QM Processor with something integrated called Intel® HD Graphics 4000.
Can someone confirm this, please?

Since this seems to be a hybrid graphics problem, is there absolutely no way to use the AMD driver for this without any further graphic errors?

---

### Post by Yellow Pasque on 2013-09-04
That's odd. Why didn't lspci show the Intel GPU?

---

### Post by su:bhatta on 2013-09-05
This is just a chance, but since there are two graphics cards wouldn't it be possible to disable the Intel one from the BIOS and use the AMD with Fglrx or disable AMD Radeon & use only Intel GPU which is likely to have better performance with open source drivers?

---

### Post by Christian Heinrichs on 2013-09-05
> **Temüjin said:**
> That's odd. Why didn't lspci show the Intel GPU?
I really don't know.
The command:
```
aticonfig --pxl
```
resulted in: 
```
PowerXpress: Discrete GPU is active (High-Performance mode).
```
I  never saw any trace of the Intel GPU, maybe that's because according to  Intel not every system is capable of additional functionality including  hybrid graphics:
> &#8225; This feature may not be available on all computing systems.
Excerpt from [Intel]("http://ark.intel.com/products/71459/Intel-Core-i7-3630QM-Processor-6M-Cache-up-to-3_40-GHz") at the bottom.
The row Processor Graphics is marked with this symbol: &#8225;

@bhattabhishek

Well, maybe it's possible.
But for that it should be determined if the system really has hybrid graphics or not.

---

### Post by su:bhatta on 2013-09-06
codingaround, i feel for you, its really frustrating not to get the graphics driver working...
What is the make and model of your laptop?


Have you searched Gentoo & Arch forums ?

Maybe you will find a missing link there, might just try.

---

### Post by Christian Heinrichs on 2013-09-06
> **bhattabhishek said:**
> 
What is the make and model of your laptop?
Have you searched Gentoo & Arch forums ?

The laptop is a Toshiba Satellite L870-177 and yes, I did search the Gentoo & Arch forums.
There wasn't any new information that could help and most solutions applied to the Gentoo and Arch Linux distributions.

---

