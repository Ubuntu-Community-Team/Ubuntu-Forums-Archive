---
title: "About to install DaVinci_Resolve_17.4.3"
date: 2022-02-08
forum: Multimedia Software
---

### Post by satimis on 2022-02-08
Hi all,

I have both;
DaVinci_Resolve_17.4.3_Linux.zip
makeresolvedeb_1.5.1_multi.sh.tar.gz

download on Downloads Folder.  I'm prepared creating DaViRes folder for them and extract/install them there. Please advise where is an ideal place for this folder?  /home/satimis/ ?

Pls advise.  Thanks

Regards

---

### Post by linuux on 2022-02-15
I'm thinking of trying this, too.  There's some online tutorials/how-tos for this.   Maybe just follow them?  I would install it according to the instructions.

There's a few reports of troubles/issues of running D.R. on Linux - so, I would want to make sure it's set up properly.

---

### Post by satimis on 2022-02-15
> **linuux said:**
> I'm thinking of trying this, too.  There's some online tutorials/how-tos for this.   Maybe just follow them?  I would install it according to the instructions.

There's a few reports of troubles/issues of running D.R. on Linux - so, I would want to make sure it's set up properly.
I have tried 3 times installing DaVinci Resolve 17 on Ubuntu 20.04 running on bare-metal SSD, of PC with graphic card installed.  It can't work on AMD CPU graphics.  Installation went through without problem but it can't start.
Warning:```

unsupported gpu processing mode ..... review gpu driver and gpu....

```
I found following link;
Unsupported GPU Processing Mode Resolve 17 Public Beta
[https://forum.blackmagicdesign.com/viewtopic.php?f=21&t=125258](https://forum.blackmagicdesign.com/viewtopic.php?f=21&t=125258)

It seams to me that there is no solution.

Yes, they has instruction, a pdf file, after extracting its package.  I attach the said file here.

DaVinci Resolve 17 works on Win10 running on bare-metal SSD, of PC with graphic card installed.

Regards

Edit
===
I have tried installing DaVinci Resolve 17 on Debian, running on bare-metal SSD of PC with graphic card installed.  Also failed with the same problem.

---

### Post by linuux on 2022-02-16
What's your gpu and cpu?

I skimmed through that forum thread.   Their problem isn't necessarily the same as your problem.   It might be but probably need more info.   If you noticed, that one person had a problem when he tried using multple amd graphics cards.    It was like there was a conflict with the DR software and there being two graphics options - when he disabled the discrete graphics - and used the other graphics he was able to use DR.   

But, I'll be able to have a better idea by actually installing it myself and see what happens.  However, my gpu options are much different than theirs and I have a nvidia gpu /intel cpu combo.  I'll report my experiences here later.

---

### Post by satimis on 2022-02-16
> **linuux said:**
> What's your gpu and cpu?

I skimmed through that forum thread.   Their problem isn't necessarily the same as your problem.   It might be but probably need more info.   If you noticed, that one person had a problem when he tried using multple amd graphics cards.    It was like there was a conflict with the DR software and there being two graphics options - when he disabled the discrete graphics - and used the other graphics he was able to use DR.   

But, I'll be able to have a better idea by actually installing it myself and see what happens.  However, my gpu options are much different than theirs and I have a nvidia gpu /intel cpu combo.  I'll report my experiences here later.

$ cat /proc/cpuinfo > cpuinfo.txt
cupinfo.txt file attached

$ sudo lshw -C display```

  *-display                 
       description: VGA compatible controller
       product: GK208B [GeForce GT 730]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:41 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:c0000-dffff

```

Edit
===
I forgot to mention that DaVinci Resolve 17 can start without problem of GPU on another drive of this PC.  It is quite strange to me.

Regards

---

### Post by linuux on 2022-02-16
Hi, again.   I was just curious if you had integrated graphics and you don't.   Can you post what version of Ubuntu and kernel that you are using?  It shouldn't matter but it might be useful to know.   

The GT 730 is an Nvidia card but it's kinda weak for video editing - but, it should work.   Mine is weak, too, but it's a 10xx card, at least.   I believe it's the minimum that should be used.   

What version of the nvidia driver are you using?   My only theory is that it's a driver issue.   

You said you can run DR 17 on another drive - do you mean, it's an entirely different OS install?    I.e. different version of Ubuntu/nvidia driver etc.?   

I am running a 'recent' version of Kubuntu - 'Jammy' - 22.04.   I probably shouldn't but I wanted recent software versions.   I haven't had any problems yet.   I was trying to install Kubuntu 21.10 but I had a graphics problem - the screen would be black when the OS booted up.   I read of a kernel bug - that I needed 5.14 so I installed 22.04 (got 5.15 that way) instead of messing around with the 21.10 install.    I think Ubuntu devs should patch the kernel on their 21.10 isos - if that's the problem.   All I know, is switching to the newer version worked.

Sorry, to digress but I thought I would mention my hardware and software for comparison.   Kubuntu 22.04, 5.15 kernel, GT 1030 nvidia card, i5-4570 cpu, 8gb DDR3.   Edit:  As of right now, nvidia ver. 470 (Ubuntu package) is installed.  There's an option to update/upgrade to version 510 but I'm not sure if I should.  

I installed kdenlive, olive and shotcut, so far.   They were easy to install, though, as they're in the repo.

---

### Post by linuux on 2022-02-16
Edit:  *I just noticed in your text, you are running the nouveau driver.   I doubt that DR would support that driver.   That might be your problem?   You might want to research that.  

I would try installing the Ubuntu-packaged proprietary Nvidia driver - it appears the latest driver you can install is 470.   Choose that one (Additional Drivers) and install.   You probably will have to reboot.

Then try to run DR again.  

Note:   Make sure you research that you won't have the black screen before you do it.   What kernel are you running?   I would upgrade the kernel to 5.14 (at least) before installing the proprietary Nvidia driver (470), just in case.   Or at least, make sure that there won't be any problems.   Maybe research on here or ask someone?  

I don't know if DR will run with the nouveau driver (foss).   Look into that as well but it's my guess, that could be why you're getting that driver/gpu error message.

Also, look at the Ubuntu version/kernel version/nvidia driver status on the other HDD where DR works.   That might give you some clues.

---

### Post by satimis on 2022-02-16
Hi linuux

$ hostnamectl```

   Static hostname: DR-Ubuntu
         Icon name: computer-desktop
           Chassis: desktop
        Machine ID: 9bdac7278d84488898c7c90fffced62c
           Boot ID: f7f91e9669894c2185aac4f99116b0b7
  Operating System: Ubuntu 20.04.3 LTS
            Kernel: Linux 5.13.0-28-generic
      Architecture: x86-64

```

# grep "X Driver" /var/log/Xorg.0.log```

grep: /var/log/Xorg.0.log: No such file or directory

```

# find /usr/lib/modules -name nvidia.ko
no printout

# find /usr/lib/modules -name nvidia.ko -exec modinfo {} \;
also no printout

Where can I find "Ubuntu-packaged proprietary Nvidia driver" ?

There is another drive on this PC running Win10.  DaVinci Resolve 17 can start on it without problem.

Regards

---

### Post by linuux on 2022-02-16
Ah, the other HDD has Windows 10.   Ok, so the nvidia driver is probably installed on that.

AFAIK, you run the Ubuntu Software Manager - there's a tab that shows 'Additional Drivers' - it will load the various drivers you can choose.   You should see Nouveau is checked but 470 should be available.   You click that and then click 'apply' (I believe).   

There might be a message to restart the computer.  Not sure.   In any case, I would reboot after installing the proprietary driver.

Note:   I see that you have kernel 5.13 installed.   I don't know if you would get the black screen after a reboot.    To be safe, I would upgrade the kernel to 5.14, at least - or ask someone on here if you should.   I tried to install 21.10 which has kernel 5.13 and had the black screen upon boot-up.  

Make sure you have your data backed up and that you know how to remove the nvidia driver if you have issues.   Alternatively, you could install 22.04 like I did - it's going to be released in a month or two.

[https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu](https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu)

[https://linuxize.com/post/how-to-nvidia-drivers-on-ubuntu-20-04/](https://linuxize.com/post/how-to-nvidia-drivers-on-ubuntu-20-04/)

---

### Post by satimis on 2022-02-16
> **linuux said:**
> 
Make sure you have your data backed up and that you know how to remove the nvidia driver if you have issues.   Alternatively, you could install 22.04 like I did - it's going to be released in a month or two.
This is an old SSD and the machine is a spare PC.  I use it testing DR17 on Ubuntu 20.04.  There is no important data on it.  Also I have tested DR17 on Debian 11 on this SSD.  It can't work as well.

It is a good idea testing DR17 on Ubuntu 22.04 to see what will happen.  I'll come back after the test.

Thanks and Regards

---

### Post by linuux on 2022-02-16
> **satimis said:**
> This is an old SSD and the machine is a spare PC.  I use it testing DR17 on Ubuntu 20.04.  There is no important data on it.  Also I have tested DR17 on Debian 11 on this SSD.  It can't work as well.

It is a good idea testing DR17 on Ubuntu 22.04 to see what will happen.  I'll come back after the test.

Thanks and RegardsYou're welcome.  

Debian will only pre-install the open source, nouveau driver, too - to keep up with open source/foss philosophy. :)    So, it will probably be the same experience for you  - as you said, not working - same message(?).

Good luck with the 22.04 experiment.   I like it so far.   I will try Davinci Resolve 17 soon and report back here.

---

### Post by satimis on 2022-02-16
> **linuux said:**
> I will try Davinci Resolve 17 soon and report back here.
Good.

My adventure is to enhance old video, captured in about 1990, improving their quality.

The hints are:
1. Use upscale resolution of the video.
2. Adjust frame rate, codec, aspect ratio, and bitrate.
3. Remove or reduce noise.
4. Fix shaky videos.
5. Optimize contrast, brightness, and saturation.
6. Rotate, crop, and flip clips.
etc.
	
Also to convert videos to HD (additional software required)

It is not easy.  I haven't started my adventure yet.  I'm now concentrating in installing video editing software first.

---

### Post by linuux on 2022-02-16
It didn't work for me - the latter stages of the install just froze.    It looked like the deb package didn't get created properly.   

There's  also no support for this program for Linux - the forum is full of  people who are doing more complicated stuff and there's no discussions  of using it in Linux.  Imho, they don't care.

I probably won't spend much time trying to fix it - and it won't run very well on my hardware anyway.   YMMV.

---

### Post by #&amp;thj^% on 2022-02-16
> **linuux said:**
> 
I probably won't spend much time trying to fix it - and it won't run very well on my hardware anyway.   YMMV.

Semi Decent Laptop:
```
inxi -CG --no-filter --no-host
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 1682 min/max: 1400/3000 cores: 1: 3299 2: 1397 3: 1655
    4: 1397 5: 1697 6: 1397 7: 1423 8: 1667 9: 1542 10: 1397 11: 1427 12: 1888
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 510.54
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org 1.21.1.3 driver: loaded: nvidia
    unloaded: fbdev,modesetting,vesa resolution: 1920x1080~120Hz
  OpenGL: renderer: NVIDIA GeForce GTX 1650 Ti/PCIe/SSE2
    v: 4.6.0 NVIDIA 510.54

```
Speedtest Screenshot
Fun Stuff ;) It dose take some resources.

---

### Post by linuux on 2022-02-16
1fallen, how does that help me?

It would be more helpful, if someone could explain what it means when, the process HANGS.   Who programmed this?!?   It might as well be Windows.

'Creating Debian Package:
dpkg-deb:  building package 'blah blah blah blah blah....' 
CURSOR

THEN NOTHING HAPPENS....FOREVER...

I hit 'CTRL-C' or nothing will ever happen...

[DONE]  Errors reported 1

I don't know how to get to that error log.   I don't recall.   It's been a while since I've used Linux/Ubuntu.

I just know this is frustrating and these kinds of experiences is what causes people to abandon Debian for Arch or to just go back to Windows.

---

### Post by #&amp;thj^% on 2022-02-16
> **linuux said:**
> 1fallen, how does that help me?



Agreeing that hardware is vital, it also won't run on both my T530's
Sorry if you took it wrong.
Regards
EDIT: have you tried to use gdebi for the install?
GDebi is described as 'lets you install local deb packages resolving and installing its dependencies. apt does the same, but only for remote (http, ftp) located packages' and is a Software Installer in the OS & Utilities category.
To convert to a .deb pkg: [https://dnetc.net/how-to-install-davinci-resolve-via-deb-with-makeresolvedeb/](https://dnetc.net/how-to-install-davinci-resolve-via-deb-with-makeresolvedeb/)
You will have to change version specific to the one your converting to.
LAST EDIT: I can appreciate both of your efforts, but clearly stated:
> **_On Linux, DaVinci Resolve officially supports CentOS onl_**y
I would also think on Red Hat.
>>DaVinci Resolve 17 requires a recent, powerful Nvidia graphics card which supports CUDA 3.0; there are reports that AMD graphics may work now. I haven't tried with AMD and won't.

---

### Post by linuux on 2022-02-16
> **1fallen said:**
> Agreeing that hardware is vital, it also won't run on both my T530's
Sorry if you took it wrong.
Regards
EDIT: have you tried to use gdebi for the install?
GDebi is described as 'lets you install local deb packages resolving and installing its dependencies. apt does the same, but only for remote (http, ftp) located packages' and is a Software Installer in the OS & Utilities category.
To convert to a .deb pkg: [https://dnetc.net/how-to-install-davinci-resolve-via-deb-with-makeresolvedeb/](https://dnetc.net/how-to-install-davinci-resolve-via-deb-with-makeresolvedeb/)
You will have to change version specific to the one your converting to.

No, but it's useless in Kubuntu anyway - there's no option to select it.

Firefox is crashing on me and my mouse pointer is suddenly disappearing as well.   I don't know if this is an *Ubuntu-wide bug but it's really annoying.   If I have to install the OS again, I'd probably install Ubuntu or some other distro.   Getting really fed up.

I don't think GDebi would help me anyway - something is going wrong with the formation of the debian package process - and I also get an error which I don't know how to troubleshoot.  

I don't need this program but I wonder if I would have problems trying to use any debian package outside the repository.   I thought this was going to be like installing the Nvidia driver (the Nvidia way) which I have done in the past - countless number of times.   

I dunno if this is an issue with the user behind the keyboard but I can say, that I really hate this guy's software - and Imho, the devs don't care about Linux, Debian or any kind of support - there's almost nothing.   There's a forum but it would annoy me to have to register to solve this problem.   

There's absolutely nothing to be found when the process doesn't go smooth - what to do when there's an error (called 'reported error 1 - whatever that means) and what to do about it if you get one.  

I hope satimis is having more luck than I am.   I am about ready to call it quits and give up.

---

### Post by linuux on 2022-02-16
[FONT=monospace][COLOR=#000000]Detected DaVinci Resolve version 17.4.3 [/COLOR]

Checking for tar...found! 
Checking for fakeroot...found! 
Checking for dpkg-deb...found! 

Using Resolve 17 conversion process 
Extracting archive 
Found 2878 objects 
Adding BlackmagicRAWPlayer 
Adding BlackmagicRAWSpeedTest 
Creating Debian package 
[COLOR=#000000]**dpkg-deb:**[/COLOR][COLOR=#000000] building package 'davinci-resolve' in './davinci-resolve_17.4.3-mrd1.5.1_amd64.deb'. [/COLOR]
[]<---'cursor'[/FONT]
[FONT=monospace][FONT=monospace][COLOR=#000000]^C [/COLOR]
[DONE] errors reported 1


---end of terminal text

This is as far as I get for anyone who cares.  I'm gonna give up unless there is a revelation or someone recognizes the solution and posts it.  
[/FONT][/FONT]

---

### Post by satimis on 2022-02-17
Hi linuux,

DR17 is also unable to start on Ubuntu 22.04 desktop with the same GPU warning as on Ubuntu 20.04 and Debian 11 desktop.  I don't think being the hardware problem.  DR17 starts without problem on Win10 running on a bare-metal SSD in this PC.  I would stop here.  I suspect that DR17 is unable to work on Linux.

To my surprise on my finding in this few months, most robust Video Editing software only work on Windows.  It forces me going back to Windows system.

---

### Post by linuux on 2022-02-17
> **satimis said:**
> Hi linuux,

DR17 is also unable to start on Ubuntu 22.04 desktop with the same GPU warning as on Ubuntu 20.04 and Debian 11 desktop.  I don't think being the hardware problem.  DR17 starts without problem on Win10 running on a bare-metal SSD in this PC.  I would stop here.  I suspect that DR17 is unable to work on Linux.

To my surprise on my finding in this few months, most robust Video Editing software only work on Windows.  It forces me going back to Windows system.Your error message is different than mine.   I am unsure of where to even locate the log for my error - whether it would even help me troubleshoot or not, I don't know.

The debian package for Resolve fails in its creation and I get an undescribed error message.   The program is entered into the kde menu but is under 'All Applcations.'   If I try to start/click it, system sounds beeps at me and I get the 'red x' and a message:  '(Launching...Resolve Failed):  Could not find the program './unpack-davinci-resolve-17.4.4/bin/resolve' 

I tried both versions (separate events), 17.4.3 and 17.4.4, with same results.
 
You are correct, though, imho - Blackmagic (the co. which owns Davinci Resolve) does NOT CARE about Linux, supporting Linux at all.   I checked their forum and web searched - threre's almost nothing to find when you have a problem installing.

If it was Windows, there would be tons of support posts or how to for fixing whatever..... 

Hopefully, some of the free video editors in Linux will develop to the level of Davinci Resolve - there's a few that are really good already.   I'm going to try them, ultimately - I already installed them from the repo.   Easy peasy for those installs.   "Windows-like click and installs."

---

### Post by satimis on 2022-02-17
> **linuux said:**
> Your error message is different than mine.
It is because of different hardware.

I think I could fix the problem finally but I won't waste my time to continue.  I already have DR17 running on Win10.

> 
Hopefully, some of the free video editors in Linux will develop to the level of Davinci Resolve - there's a few that are really good already.   I'm going to try them, ultimately - I already installed them from the repo.   Easy peasy for those installs.   "Windows-like click and installs."

I found;
DaVinci Resolve Alternatives for Linux - AlternativeTo
[https://alternativeto.net/software/davinci-resolve/?platform=linux](https://alternativeto.net/software/davinci-resolve/?platform=linux)

I already have following software installed and running on Ubuntu 20..04

Kdenlive
Shotcut
Avidemux
OpenShot

I'll start my adventure to enhance my old video soon.

---

### Post by linuux on 2022-02-17
> **satimis said:**
> It is because of different hardware.

I think I could fix the problem finally but I won't waste my time to continue.  I already have DR17 running on Win10.



I found;
DaVinci Resolve Alternatives for Linux - AlternativeTo
[https://alternativeto.net/software/davinci-resolve/?platform=linux](https://alternativeto.net/software/davinci-resolve/?platform=linux)

I already have following software installed and running on Ubuntu 20..04

Kdenlive
Shotcut
Avidemux
OpenShot

I'll start my adventure to enhance my old video soon.
Good Luck!   I am going to try Kdenlive, Shotcut and Olive.  
All three are already installed and ready to go.   At least, we can install those, with no problem. : )

---

### Post by TheFu on 2022-03-18
I couldn't find the original post about scaling videos, but saw this tonight: [https://youtu.be/TpdapO9QGRo](https://youtu.be/TpdapO9QGRo) that has examples of upscaled videos.

---

### Post by satimis on 2022-03-19
> **TheFu said:**
> I couldn't find the original post about scaling videos, but saw this tonight: [https://youtu.be/TpdapO9QGRo](https://youtu.be/TpdapO9QGRo) that has examples of upscaled videos.

Thanks for your link.

I have tried upgrading the resolution of my old video.  Please find my posting on Post #6 of following link;
Seek advice on selecting video editing software 
[https://ubuntuforums.org/showthread.php?t=2471664&p=14086428#post14086428](https://ubuntuforums.org/showthread.php?t=2471664&p=14086428#post14086428)

I'm satisfied on the quality of the video clips generated.  I can upgrade the resolution to 4K but the file size will be too big.

I can make the video quality even better directly pro rata to my time invested on it.

Regards

---

