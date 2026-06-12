---
title: "fail on installing ATI Catalyst after upgrading Ubuntu 14.04"
date: 2014-04-19
forum: Multimedia Software
---

### Post by tho.tran1809 on 2014-04-19
Hi guys,

I've just upgraded to Ubuntu 14.04, from 13.10, and installed kernel 3.13. When I was in 13.10, I got ATI Catalyst 14.3 installed successfully for my GPU Radeon HD 8790M. Before I upgrade to 14.04, I removed it. Now after upgrading, when I tried to re-install, it said that "Your graphics adapter is not supported by this driver. Installation will not proceed".

In Ubuntu 13.10, I do not have HDMI audio and I heard that with kernel 3.13 on Ubuntu 14.04, HDMI audio will work, that's why I need to install newest ATI Catalyst driver.

By the way, in Ubuntu 14.04, without ATI catalyst driver, I tried to plug in HDMI cable, but still no audio.

Thanks for your helps!

---

### Post by trag on 2014-04-20
Your video card has been depricated. since there is no support after 13.10, you will need to return to 13.10 to use it.

---

### Post by QIII on 2014-04-20
No, the HD 8000 series GPU has not been deprecated.  HD 2000 - 4000 have, and the last version of Ubuntu that is supported by AMD/ATI's drivers is 12.04.1

@Tho.Tran1809:  Could you give us the complete specs on your machine?

---

### Post by tho.tran1809 on 2014-04-20
> **QIII said:**
> No, the HD 8000 series GPU has not been deprecated.  HD 2000 - 4000 have, and the last version of Ubuntu that is supported by AMD/ATI's drivers is 12.04.1

@Tho.Tran1809:  Could you give us the complete specs on your machine?


I've a laptop Dell Latitude E6540 which has Intel Haswell chipset and GPU Radeon HD 8790M. Below is my specs for GPU:
```
lspci -nn | grep VGA00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mars XTX [Radeon HD 8790M] [1002:6606] (rev ff)
```

Pls help me, I waited Ubuntu 14.04 to fix my HDMI audio problem, but now it still cannot be fixed.

Thanks!!!

---

### Post by monkeybrain20122 on 2014-04-21
ATI drivers often come late and tend o be problematic for new releases, if you want something that works you should stick to 13.10 instead of upgrading to something barely out of beta at the first chance (I know the hypes and all that :) ) 

You can upgrade your kernel without upgrading the OS, just grab the .debs and install them from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/) . You need 3 of them:Linux headers, Linux headers all and Linux image. Download them and put all 3 in a folder, cd into the folder and run
```
sudo dpkg -i *.deb
``` then reboot.

---

### Post by psehouri on 2014-05-04
Hello, I have the same video card... and I can't install fglrx properly. Did you find a solution ???

---

### Post by dannyboy79 on 2014-05-04
i am running xubuntu 14.04 with an HD 6550D APU and am running the latest AMD driver 14.4. I simply ensured I had removed all ati drivers from my system, then downloaded the .run file from AMD's website, then switch to tty1, stop lightdm, ran the .run with sudo and then ran sudo aticonfig --initial and PRESTO. fired up lightdm with sudo service lightdm start and i was back at my X server desktop running the latest AMD driver.

what is the error you get when trying to install the fglrx driver?

---

### Post by emgiezet on 2014-06-20
Have same thing. On Radeon HD 7600M. I was installing it via sgfxi, gui way also fail. I need to run my Dell Vostro on Intel HD 4000. Any help will be usefull

---

### Post by emgiezet on 2014-06-23
Ok I got a workaround.

Tried with AMD Catalysts 14.10, And 14.20 beta

You need AMD Catalyts 14.4 (from sgfxi are ok). Install them, use aticonfig --initial

And then you need to reconfigure grub [http://askubuntu.com/questions/341730/ubuntu-on-hp-pavilion-g7-1153er-with-hybrid-radeon-6470m-and-intel-3000](http://askubuntu.com/questions/341730/ubuntu-on-hp-pavilion-g7-1153er-with-hybrid-radeon-6470m-and-intel-3000)

sudo gedit /etc/default/grubyou need to remove "nomodeset"

and add 

> [LEFT][COLOR=#333333][FONT=UbuntuRegular]GRUB_CMDLINE_LINUX="acpi_backlight=vendor"[/FONT][/COLOR][/LEFT]

Then just update the grub.

$ sudo update-grub
And reboot 14.04 will work!

---

### Post by sp40140 on 2014-06-29
Hello Guys
I might have same issue:
I run HD7770 on custom desktop running core2Quad with 8 gigs of ram. After I upgraded to 14.04 64bit from 13.10 64 bit, I lost hdmi audio. I found this bug page 
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)
Summary is: OpenGL drivers won't support HDMI audio unless you enable it in kernel. it can be done by messing with grub config. Or second option is to use latest ATI drivers. Or third option is to upgrade to latest linux kernel which has that enabled by default.
Now, I have modified the grub as described but no dice. I picked up latest ATI drivers stable and beta but no dice (I did cleaned flgrx up before installing each one) but no dice. ATI drivers break UNITY. I have to go to TTY and uninstall the drivers.
Now the thrid option left is to upgrade to latest linux kernel. 
How risky is it? 
Can anyone confirm that latest linux kernel with OpenGL will work for HDMI audio?
any other option will help as well. 
My vid works with OpenGL drivers but option for hdmi audio is not there in sound settings. only analog and optical. (which I havent tested as I don't have set-up to use those so no point).
Please help,

---

### Post by sp40140 on 2014-06-29
FOUND the FIX.
My Issue:
OpengGL drivers worked for vid. BUT hdmi Audio not available. Due to it being disabled in kernel.
Suggested fixes: 
1] use ATI prop drivers. 
Result: Didn't work. Crashed my Unity. (even with couple diff versions of drivers including beta).
2]Enable the ATI audio in kernel using grub so it can be used with OpenGL. 
Result:This didn't work either. eventhough I can see that the paramerter is being passed.
3] upgrade Kernel to latest or 1.13 or newer.
EUREKA. This worked. I upgraded to 3.14 (latest stable in mainline). No  need to prop ati drivers. OpenGL works as the audio has been enabled in  13.3.

---

