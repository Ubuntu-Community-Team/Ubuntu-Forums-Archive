---
title: "Atheros 9k wifi card problem, please help!"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by shebaw on 2010-03-24
Hi all, I'm new to  ubuntu and to this forum, I've solved most of the problems I faced except this one. I have been using ubuntu 9.10 for the past 5 days and everything works fine except my wifi card. I forgot the exact model of my wifi card but its a member of the Atheros9k family and ubuntu seems to detect it. I can connect to wireless connections for about 5 minutes or so till my computer freezes leaving me with no choice but to reboot it the hard way! I have tried connecting on two different wireless connections but the same problem keeps on happening. And I know there is no problem with my card since I have been using it without problems when my OS was windows 7.

---

### Post by coffeecat on 2010-03-24
Some people who have been experiencing poor connections with ath9k wireless devices have seen improvement by installing the following two packages:

linux-backports-modules-karmic
linux-backports-modules-wireless-karmic-generic

This may or may not help your somewhat different desktop freezing problem, but it's certainly worth trying, and it certainly won't do any harm.

Make sure your machine is connected via an ehernet cable to give you a stable connection and stable desktop for the duration of the install. Open Synaptic, click on 'reload' to get the latest metadata and mark those two packages for installation. They will bring in one other package which contains the actual updated drivers. 

This association of desktop freezing and wireless is vaguely familiar. Is that an Acer laptop you have there? Whatever, post details of the make and model of your machine. Someone with the same or similar may have some advice. Also, open a terminal and do the following command:

```
lspci
```Find the line that has "wireless" or "802.11" in it and post that. It will (hopefully) tell us the precise wireless chipset which may be useful.

---

### Post by shebaw on 2010-03-24
> **coffeecat said:**
> Some people who have been experiencing poor connections with ath9k wireless devices have seen improvement by installing the following two packages:

linux-backports-modules-karmic
linux-backports-modules-wireless-karmic-generic

This may or may not help your somewhat different desktop freezing problem, but it's certainly worth trying, and it certainly won't do any harm.

Make sure your machine is connected via an ehernet cable to give you a stable connection and stable desktop for the duration of the install. Open Synaptic, click on 'reload' to get the latest metadata and mark those two packages for installation. They will bring in one other package which contains the actual updated drivers. 

This association of desktop freezing and wireless is vaguely familiar. Is that an Acer laptop you have there? Whatever, post details of the make and model of your machine. Someone with the same or similar may have some advice. Also, open a terminal and do the following command:

```
lspci
```Find the line that has "wireless" or "802.11" in it and post that. It will (hopefully) tell us the precise wireless chipset which may be useful.

Ok I will try it tomorrow and update you my result. And my laptop is Asus F81 se and here is the result of the lspci command.

```
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

And one more thing, is there any combination of keys that I can press when my computer freezes on me, to shut it down gracefully atleast?

Thanks in advance!

---

### Post by coffeecat on 2010-03-24
> **shebaw said:**
> ```
Atheros Communications Inc. AR928X Wireless Network Adapter
```

You **definitely** need those backports packages for the AR928X chipset whether or not it fixes the freezing. One of my laptops has the 928X and I was getting a very flaky connection until I installed the backports. It would drop out and try but fail to reconnect. Maybe the dropout and failed reconnect is interacting with the ACPI in your Asus and causing the freeze. Let's hope the backports are the answer.

> **shebaw said:**
> And one more thing, is there any combination of keys that I can press when my computer freezes on me, to shut it down gracefully atleast?

But, of course. This is Linux! :p See here:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Basically, while holding down the Alt Gr and SySReq keys, press R,E,I,S,U,B in turn (slowly) for a graceful reboot, or R,E,I,S,U,O to shut down. Use the Alt Gr key to the right of the space bar, rather than the Alt key otherwise you get prompts for dozens of screenshots.

---

### Post by shebaw on 2010-03-25
Thank you again, and I've done what you told me and I'm using the wireless connection without any problem now. But here is my new problem, my graphics card is ATi mobility Radeon HD4570, and I was using the catalyst driver for linux that I downloaded from their website without any problems till I fixed my wifi issues. After I downloaded those packages and restarted my laptop, the cursor was invisible and desktop effects were disabled. So I had to uninstall the driver to get the cursor back, and the driver I got from the Hardware drivers windows doesn't even work. I can't even scroll pages without the screen flickering. So what should I do?

---

### Post by coffeecat on 2010-03-25
There's a configuration file for the graphical xserver called /etc/X11/xorg.conf which will have been generated when you installed the proprietary driver. With the latest versions of the xserver, there is no xorg.conf file because the xserver can autodetect most hardware and apply the appropriate open source driver. The simplest fix in your situation is to rename (or delete) xorg.conf and reboot which will get you back to the open source driver.

If your graphical desktop is more-or-less usable, open a terminal and....

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```... and then reboot. Be careful of case - Linux is case-sensitive. That's CAPITAL-X-eleven in the middle there.

If the desktop is unusable, press ctrl-alt-F1 to get to a virtual console, login, run the above command, and then:

```
sudo reboot
```I've suggested you rename the file rather than delete it because, in the unlikely event of this making things worse, you can boot in recovery mode and restore the xorg.conf file.

A couple of comments about ATI and drivers. My laptop with the AR928X wireless also has a Radeon HD4200 graphics. The open source driver in Karmic was fine, but no 3-d or acceleration, so no gee-whiz compiz effects. I tried the repository fgrlx driver and it was an unmitigated disaster, so I reverted to the open source driver as above. I'm now running the development version of Lucid on another partition on this machine, and the good news is that I get compositing out of the box with the open source driver - wobbly windows, desktop cube, the lot. So things are getting better with the OS driver and you only have to wait a month for the release version of Lucid which, by the way, is looking very good indeed.

However, with ATI cards, the old your-mileage-may-vary adage applies, so I don't know whether this will be true for your HD4570.

---

### Post by shebaw on 2010-03-25
Hi thank you again for your patience, ok I don't know what's wrong, I have renamed it and now it powers off my laptop's screen when it boots up. I'm now using my live CD and I tried to restore the back up but I can't rename it, so what should I do? And the weird thing is, the graphics is better when I boot from my live CD without even installing any drivers!

---

### Post by shebaw on 2010-03-25
Ok I have managed to rename the file using nautilus from the live CD. So I guess I'm left with my graphics card problem.

---

### Post by coffeecat on 2010-03-25
> **shebaw said:**
> And the weird thing is, the graphics is better when I boot from my live CD without even installing any drivers!

That's because the open source ATI driver comes in the box and the xserver will default to that without an xorg,conf. Which is the state I was trying to get you back to by renaming xorg.conf.

I guess, even though you uninstalled the catalyst driver from the ATI wesite, there is something left in the system interfering with the open source driver so renaming xorg.conf won't be enough. Can you post a link to the method you used to install this driver? There should be a way of effectively purging the system of all remnants of it. Then renaming xorg.conf *should* work.

---

### Post by shebaw on 2010-03-25
I guess there is no solution for my problem and the problem isn't only with me either. 

[http://ubuntuforums.org/showthread.php?p=9026178#post9026178](http://ubuntuforums.org/showthread.php?p=9026178#post9026178)

Thats the exact problem I'm having and I guess reinstalling ubuntu is the only fix :(

---

### Post by coffeecat on 2010-03-25
> **shebaw said:**
> I guess there is no solution for my problem and the problem isn't only with me either. 

[http://ubuntuforums.org/showthread.php?p=9026178#post9026178](http://ubuntuforums.org/showthread.php?p=9026178#post9026178)

Thats the exact problem I'm having and I guess reinstalling ubuntu is the only fix :(

Before you do that, have a look here:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

Click on "installer instructions" and you get a pdf file with this:

> Uninstalling the ATI Linux Proprietary Driver
         Uninstalling the ATI Linux Proprietary Driver is dependent on the mode of the initial
         installation.
    Automatic or Custom Driver Installations
         If the ATI Proprietary Linux Driver was installed using either the Automatic or Custom
         options, then do the following:
         1    Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
              With superuser permissions, enter the command "sh ./fglrx-uninstall.sh".
         2
              Reboot your system.
         3
         You have now successfully uninstalled the ATI Linux Proprietary Driver.That'll be "sudo sh ./fglrx-uninstall.sh" in Ubuntu. Is this what you did? Because I find it very hard to believe that the backports modules broke the graphics. Yes, I did read your linked thread and, yes, stranger things happen, but I would like to find a more logical explanation for broken graphics than an updated wireless driver.

---

### Post by shebaw on 2010-03-25
> Because I find it very hard to believe that the backports modules broke the graphics. Yes, I did read your linked thread and, yes, stranger things happen, but I would like to find a more logical explanation for broken graphics than an updated wireless driver.


I restarted my pc as soon as I installed the backport modules, I didn't install anything except that and that was when my graphics card broke.


> That'll be "sudo sh ./fglrx-uninstall.sh" in Ubuntu.Is this what you did?  
Ya I have tried that and that was how I got my cursor back. And I now have used envy  to uninstall my graphics card driver, and I'm having lower resolution but the annoying "drawing" effect has gone. I'm going to use envy to install my graphics card and will update you the result. 

Thank you again for your reply!

---

### Post by shebaw on 2010-03-25
I have installed my graphics card driver using envy and everything is working fine, I even have all those pretty 3D effects, WOOOHOOOO!!!!

---

### Post by coffeecat on 2010-03-25
Good news. 

Actually, I've rethought this proprietary driver versus wireless driver thing and, yes, this does seem to be a problem.

Consider - if I'm understanding you right - you were getting freezing with the catalyst driver + original ath9k driver whereas I was getting merely a flaky wireless connection with the original ath9k driver - but I was using the open source ATI driver. Perhaps there is an interaction between the proprietary driver and the older ath9k driver sufficient to cause your freezing. And then when you updated the ath9k driver, graphics broke. I didn't try to install the fglrx driver (through Hardware Drivers) until after I had installed the backports and the effect was appalling - windows tearing, lagging, etc. So perhaps I did experience this issue.

Anyway, glad to hear envy worked for you. I couldn't get envy to work on my machine for some reason, so I envy you that. (Groan! :() Perhaps the version of the driver that envy installs is different from the one you downloaded from the ATI site. 

Anyway, I'm hoping this will all be theoretical in Lucid. The version of the ath9k driver that comes with Lucid is the same as the one that the backports package installs in Karmic and, as I mentioned, the open source ATI driver seems to be much improved in Lucid.

---

### Post by shebaw on 2010-03-26
> Consider - if I'm understanding you right - you were getting freezing with the catalyst driver + original ath9k driver whereas I was getting merely a flaky wireless connection with the original ath9k driver - but I was using the open source ATI driver. Perhaps there is an interaction between the proprietary driver and the older ath9k driver sufficient to cause your freezing. And then when you updated the ath9k driver, graphics broke. I didn't try to install the fglrx driver (through Hardware Drivers) until after I had installed the backports and the effect was appalling - windows tearing, lagging, etc. So perhaps I did experience this issue.Yes I guess you experienced the same issue, the proprietary driver works fine till you install those backports.

> Perhaps the version of the driver that envy installs is different from the one you downloaded from the ATI site.Perhaps, but I downloaded the latest version from ATi's website, I still don't know how envy's driver is working great.

> The version of the ath9k driver that comes with Lucid is the same as the one that the backports package installs in Karmic and, as I mentioned, the open source ATI driver seems to be much improved in Lucid.I will be very happy if everything works fine out of the box on Lucid, Ubuntu 9.1 detected most of my drivers(except my fingerprint reader and graphics card ofcourse), that was why I gave this version a try.

---

