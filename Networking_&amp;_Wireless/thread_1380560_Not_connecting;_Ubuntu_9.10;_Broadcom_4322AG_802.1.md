---
title: "Not connecting; Ubuntu 9.10; Broadcom 4322AG 802.11a/b/g/draft-n WiFi adapter"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by atravnic on 2010-01-13
Hi Folks -- I was running 9.10 in LiveCD mode and was unable to get online. Went to System>Administration>Hardware Drives and found "Broadcom STA wireless driver". Cool. So I went ahead and installed 9.10 (dual boot with Vista), repeated above steps but found no "Broadcom STA wireless driver" option, in fact no proprietary drivers. So I still cannot connect to the Internet, and I don't know where to go from here. (Note: I installed 9.10 side by side with Vista: good? bad?) Thanks for helping!!!! :D  

...Fred

Here's the machine I'm using:
* * * HP Pavillion tx2500z running Vista, 
* * * AMD Turino X2 Dual Core processor,
* * * 12.1" WXGA BrightView touch screen display,
* * * 3GB DDR2 memory,
* * * ATI Radeon HD 3200 graphics,
* * * 250GB 5400 RPM SATA hard drive,
* * * Broadcom 4322AG 802.11 a/b/g/draft-n WiFi Adaptor
* * * Supermulti 8XDVD +/- R/RW optical drive

---

### Post by bkratz on 2010-01-13
Here is a thread with a pretty good description of what to do

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)


Good Luck

---

### Post by jimezam on 2010-01-13
I had the same problem.  What I did:

- Go on wired network.
- Install corresponding kernel headers.
     [FONT=courier new]$ sudo aptitude install  linux-headers-$(uname -r)[/FONT]
- Install the driver.
[FONT=courier new]   $ sudo aptitude install  bcmwl-kernel-source[/FONT]
- If you already have it installed, you may need reconfigure it.
[FONT=courier new]   $ sudo dpkg-reconfigure  bcmwl-kernel-source[/FONT]
- Activate the driver under **System** > **Administration** > **Hardware  Drivers**.

Link (spanish): [http://blog.jorgeivanmeza.com/2009/12/activar-las-tarjetas-wifi-broadcom-en-linux-ubuntu-9-10/](http://blog.jorgeivanmeza.com/2009/12/activar-las-tarjetas-wifi-broadcom-en-linux-ubuntu-9-10/)

I hope it helps you.

jimezam.

---

### Post by atravnic on 2010-01-14
:D Thank you jimezam for your quick answer .. now the tough part: I'm not a Linux techie .. so your solution is a tad over my head .. I can do the wired part but don't know what the corresponding headers are nor where to find them .. so let me make a bold assumption: I go to terminal and do the sudo'ing there and that will install the headers??? .. but what is (uname-r)??? .. and I do know how to do the activation .. so I'll wait to hear back from you with 'yes' or an amplification / correction. Thanks again!!!   ...Fred

.......................................................................


> **jimezam said:**
> I had the same problem.  What I did:

- Go on wired network.
- Install corresponding kernel headers.
     [FONT=courier new]$ sudo aptitude install  linux-headers-$(uname -r)[/FONT]
- Install the driver.
[FONT=courier new]   $ sudo aptitude install  bcmwl-kernel-source[/FONT]
- If you already have it installed, you may need reconfigure it.
[FONT=courier new]   $ sudo dpkg-reconfigure  bcmwl-kernel-source[/FONT]
- Activate the driver under **System** > **Administration** > **Hardware  Drivers**.

Link (spanish): [http://blog.jorgeivanmeza.com/2009/12/activar-las-tarjetas-wifi-broadcom-en-linux-ubuntu-9-10/](http://blog.jorgeivanmeza.com/2009/12/activar-las-tarjetas-wifi-broadcom-en-linux-ubuntu-9-10/)

I hope it helps you.

jimezam.

---

### Post by bkratz on 2010-01-14
> **atravnic said:**
> :D Thank you jimezam for your quick answer .. now the tough part: I'm not a Linux techie .. so your solution is a tad over my head .. I can do the wired part but don't know what the corresponding headers are nor where to find them .. so let me make a bold assumption: I go to terminal and do the sudo'ing there and that will install the headers??? .. but what is (uname-r)??? .. and I do know how to do the activation .. so I'll wait to hear back from you with 'yes' or an amplification / correction. Thanks again!!!   ...Fred

.......................................................................

you might want to look at the link I previously sent. It adds the STA driver a little easier and is step by step.

Here it is again
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by jimezam on 2010-01-14
You only need to run the commands below the instructions.  Probably the first two will make it.

jimezam.

---

### Post by atravnic on 2010-01-14
> **bkratz said:**
> you might want to look at the link I previously sent. It adds the STA driver a little easier and is step by step.

Here it is again
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Thanks bkrantz. After some stumbling around I did get the STA driver installed and activated. But surprise, I still can't get online, wired or wireless. I guess I'll start a new thread. Thanks again for your help.

...Fred

---

### Post by atravnic on 2010-01-15
> **jimezam said:**
> You only need to run the commands below the instructions.  Probably the first two will make it.

jimezam.

................................................
It's the first one -- $ sudo aptitude install linux-headers-$(uname -r) -- I didn't understand. Especially didn't know what to do with the (uname -r) notation. I typed it as is and got an error return.Then I typed it without the (uname -r) and it did something. Long story short, I was, after much fiddling around, able to install and activate the STA Broadcom driver, but I still can't get on line. Ideas? Thanks!!!     ...Fred

- Go on wired network.
- Install corresponding kernel headers.
$ sudo aptitude install linux-headers-$(uname -r)
- Install the driver.
$ sudo aptitude install bcmwl-kernel-source
- If you already have it installed, you may need reconfigure it.
$ sudo dpkg-reconfigure bcmwl-kernel-source
- Activate the driver under System > Administration > Hardware Drivers.

---

### Post by atravnic on 2010-01-18
I'd like to thank everyone in this thread for all your help, and your patience with me. In the course of taking through this problems I learned a lot and, most significantly, overcame some of my apprehension of getting down and dirty with Ubuntu.   ...Fred

---

### Post by jimezam on 2010-01-21
Hello atravnic.  This line works without problems on mi PC.  It installs the Kernel Headers of your current Kernel version.  You could replace the "$(uname -r)" for the result of running the "uname -r" command too.

I am glad you solved your problem.

jimezam.

---

