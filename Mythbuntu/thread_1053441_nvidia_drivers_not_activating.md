---
title: "nvidia drivers not activating"
date: 2009-01-28
forum: Mythbuntu
---

### Post by davidstoll on 2009-01-28
A week or so ago, apt-get told me I could do a cleanup, so I did.  Although, I forget the exact command.  I think it was apt-get autoclean...but it was to remove unused packages.  Well, I lost my restricted drivers GUI (jockey ?).  Everything basically worked and I even rebooted a few times to see if it would come back.  Anyway, I decided to re-install jokey with apt-get and got the GUI back.  I got the Nvidia restricted drivers GUI back, but my system boots up in low graphics mode.

I can't seem to get the restricted drivers to "activate".  When I use the GUI to activate one of the drivers, it doesn't seem to do anything.  I even re-downloaded the drivers with apt-get, but can't seem to get out of low graphics mode.

I attached a screen shot so you can see the error...and yes, I did run nvidia-settings as root...didn't help, even after reboots.

Thanks for any help you guys can give me.

P.S. I'm pretty new to linux, so baby step me through it.

---

### Post by gettinoriginal on 2009-01-28
Reboot, and at your grub screen, hit escape and run "recovery mode", then "try to fix X", then normal boot.

---

### Post by davidstoll on 2009-01-28
> **gettinoriginal said:**
> Reboot, and at your grub screen, hit escape and run "recovery mode", then "try to fix X", then normal boot.

OK, you might be on to something here.  When I tried to normal boot off "recovery mode", the restricted drivers notification alerted me.  I selected the recommended driver, it seemed to download and then said to reboot the PC to finalize the installation (something it wasn't doing)...but after the reboot, I was back to low graphics mode.

---

### Post by Dewey_Oxberger on 2009-01-29
Assuming you have a fairly recent ubuntu install
I've had good luck with the envy script.  It seems to fix things well enough that it'll install and uninstall and leave things in a state that works:

sudo apt-get install envyng
sudo envyng -t

It's only real downside is it doesn't install the most recent version.

---

### Post by rodercot on 2009-01-29
> **davidstoll said:**
> OK, you might be on to something here.  When I tried to normal boot off "recovery mode", the restricted drivers notification alerted me.  I selected the recommended driver, it seemed to download and then said to reboot the PC to finalize the installation (something it wasn't doing)...but after the reboot, I was back to low graphics mode.


 Once back in gnome open a terminal and run 

 sudo nvidia-xconfig then sudo reboot *note* this will overwrite your current xorg file with a new one I believe but it will force out those little demons causing your problems. Did you by chance update alsa or setup the newest lirc, I have had this issues with lirc in the past overwriting xorg.conf or at least rendering low graphics mode and that is how I fixed it.
 
 Dave

---

### Post by davidstoll on 2009-01-29
> **rodercot said:**
> Once back in gnome open a terminal and run 

 sudo nvidia-xconfig then sudo reboot *note* this will overwrite your current xorg file with a new one I believe but it will force out those little demons causing your problems. Did you by chance update alsa or setup the newest lirc, I have had this issues with lirc in the past overwriting xorg.conf or at least rendering low graphics mode and that is how I fixed it.
 
 Dave

Yes, this is what I did based on the error message that I got when trying to run the Nvidia gui.  No luck.  I have my old xorg.conf that worked from about 1 month ago, but that doesn't work either.

Yes, lirc had some problems and that's where it all started.  I tried to reinstall lirc, but that didn't help.  I did the apt-get cleanup and that's when I lost my nvidia gui, but my video and drivers seemed to be working correctly.  I reinstalled jockey and that's when I got my nvidia gui back, but then the actual video/drivers stopped functioning correctly.

---

### Post by davidstoll on 2009-01-29
> **Dewey_Oxberger said:**
> Assuming you have a fairly recent ubuntu install
I've had good luck with the envy script.  It seems to fix things well enough that it'll install and uninstall and leave things in a state that works:

sudo apt-get install envyng
sudo envyng -t

It's only real downside is it doesn't install the most recent version.

I'm using 8.10 64bit.

It can't seem to find envyng...maybe envyng-qt or something else?

---

### Post by rodercot on 2009-01-29
Have you tried to install the latest nvidia driver outside of envy or restricted. 

 I never use either of those. 

 i dwnld the latest from nvidia.com

 then get to runlevel 1 usually from recovery mod at Grub then login and type

 cd /path to donwload/

 sudo sh NVIDIA-Linux-x86-version you dwnld-pkg1.run 

 follow the on-line settings, if it detects your existing setup it will ask you if you want to remove it.

 make sure and say yes to overwriting your xorg.conf file. Then if it still will not run at hi-res run the sudo nvidia-xconfig line and you should be fine.
 
 if it does not work then basically get back to run level 1 and type the same command as above to install but at the of the command line type --uninstall and it will remove the driver, if anything this will remove the remnants of the old drivers you have already installed and as well likely and conflicts.

 What does your xorg log say.

 I think it is /var/log/Xorg0.log check for any (EE) at the beginning of any lines. 

 Dave

---

### Post by davidstoll on 2009-01-29
> **rodercot said:**
> Have you tried to install the latest nvidia driver outside of envy or restricted. 

 I never use either of those. 

 i dwnld the latest from nvidia.com

 then get to runlevel 1 usually from recovery mod at Grub then login and type

 cd /path to donwload/

 sudo sh NVIDIA-Linux-x86-version you dwnld-pkg1.run 

 follow the on-line settings, if it detects your existing setup it will ask you if you want to remove it.

 make sure and say yes to overwriting your xorg.conf file. Then if it still will not run at hi-res run the sudo nvidia-xconfig line and you should be fine.
 
 if it does not work then basically get back to run level 1 and type the same command as above to install but at the of the command line type --uninstall and it will remove the driver, if anything this will remove the remnants of the old drivers you have already installed and as well likely and conflicts.

 What does your xorg log say.

 I think it is /var/log/Xorg0.log check for any (EE) at the beginning of any lines. 

 Dave

This is a tad complicated for me (installing the other driver), but the restricted drivers were working fine before.  I'm not opposed to doing it, but would prefer to get things fixed and back the way they were.

My Xorg.0.log does have this in it...
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

What do you guys suggest regarding that error?

---

### Post by rodercot on 2009-01-29
> **davidstoll said:**
> This is a tad complicated for me (installing the other driver), but the restricted drivers were working fine before.  I'm not opposed to doing it, but would prefer to get things fixed and back the way they were.

My Xorg.0.log does have this in it...
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

What do you guys suggest regarding that error?

 Yes, something is preveting it from loading. I am not sure how to fix that, I did get that error at one point and I did pretty much what I explained above and then rebooted and all was fine.

 what driver version did the log say you were installing. It should be 173.? or 177.?

 If you find this out you could try this

 open up a terminal and issue
 
 sudo apt-get install nvidia-glx-180

 reboot and if the driver does not load try the sudo nvidia-xconfig again. 

 Dave

---

### Post by davidstoll on 2009-01-29
> **rodercot said:**
> Yes, something is preveting it from loading. I am not sure how to fix that, I did get that error at one point and I did pretty much what I explained above and then rebooted and all was fine.

 what driver version did the log say you were installing. It should be 173.? or 177.?

 If you find this out you could try this

 open up a terminal and issue
 
 sudo apt-get install nvidia-glx-180

 reboot and if the driver does not load try the sudo nvidia-xconfig again. 

 Dave


I previously tried a re-download of the nvidia-glx-xxx driver, but that didn't help.  However, it looks like you edited your post here, but I got your original post via e-mail.

sudo apt-get autoremove --purge nvidia-glx-173
sudo apt-get autoremove --purge nvidia-glx-177
sudo apt-get autoremove --purge nvidia-glx-180
reboot
sudo apt-get install nvidia-glx-177
reboot

at this point, I ran nvidia-settings, but the settings were all strange.  I even tried to reboot.  Basically, the resolutions that were available were kind of strange.  I needed my native 1280x1024.

I had a copy of my last working xorg.conf from a month ago.  I just copied it to my /etc/X11/ folder, rebooted and WHAMO!  All fixed.

So, thank you for your suggestion!  You also mentioned in your pre-edit post that "Remember the log files are your best friend."  Well, you are correct.  I am new to linux and I realize this, but I don't really understand them very well yet or even where to look effectively.

I'm getting there, thanks to all you great people. ):P

Now, my only problem is LIRC...and from what I've read, it can be affected by the video and sound drivers...?  Doesn't make since to me, but hey, what do I know.  I'm going to make a separate post about my issue with LIRC.  I hope you can help again.
:p

---

### Post by rodercot on 2009-01-29
> **davidstoll said:**
> I previously tried a re-download of the nvidia-glx-xxx driver, but that didn't help.  However, it looks like you edited your post here, but I got your original post via e-mail.

sudo apt-get autoremove --purge nvidia-glx-173
sudo apt-get autoremove --purge nvidia-glx-177
sudo apt-get autoremove --purge nvidia-glx-180
reboot
sudo apt-get install nvidia-glx-177
reboot

at this point, I ran nvidia-settings, but the settings were all strange.  I even tried to reboot.  Basically, the resolutions that were available were kind of strange.  I needed my native 1280x1024.

I had a copy of my last working xorg.conf from a month ago.  I just copied it to my /etc/X11/ folder, rebooted and WHAMO!  All fixed.

So, thank you for your suggestion!  You also mentioned in your pre-edit post that "Remember the log files are your best friend."  Well, you are correct.  I am new to linux and I realize this, but I don't really understand them very well yet or even where to look effectively.

I'm getting there, thanks to all you great people. ):P

Now, my only problem is LIRC...and from what I've read, it can be affected by the video and sound drivers...?  Doesn't make since to me, but hey, what do I know.  I'm going to make a separate post about my issue with LIRC.  I hope you can help again.
:p

 Glad I could help out. Which remote are you trying to configure in Lirc. 

 The same applies there as well. You can always do a 

 sudo apt-get autoremote --purge lirc and then reinstall it. When you setup via 

 sudo apt-get install lirc you get a nice little configuration menu to help you out at the beginning. 

 I always suggest that people move there remotes lircd.conf file from /usr/share/lirc/remotes/yourremote/lird.conf.yourremote to /etc/lirc/lircd.conf and then in the directory 

 /etc/lirc edit the hardware.conf file and change the 
 
 REMOTE_Lircd=" somedirectory/remote/.conf" to this

 REMOTE_lircd=""

 This will force lirc to use the lircd file in your etc/lirc directory.
 
 Dave

---

### Post by davidstoll on 2009-01-30
> **rodercot said:**
> Glad I could help out. Which remote are you trying to configure in Lirc. 

 The same applies there as well. You can always do a 

 sudo apt-get autoremote --purge lirc and then reinstall it. When you setup via 

 sudo apt-get install lirc you get a nice little configuration menu to help you out at the beginning. 

 I always suggest that people move there remotes lircd.conf file from /usr/share/lirc/remotes/yourremote/lird.conf.yourremote to /etc/lirc/lircd.conf and then in the directory 

 /etc/lirc edit the hardware.conf file and change the 
 
 REMOTE_Lircd=" somedirectory/remote/.conf" to this

 REMOTE_lircd=""

 This will force lirc to use the lircd file in your etc/lirc directory.
 
 Dave

The purge did it again.  Thanks.

I'm using the MCE and also the Stream Zap.  My PC case also has one, but I can't seem to get it to work.
[http://www.silverstonetek.com/products/p_spec.php?pno=LC20&area=usa](http://www.silverstonetek.com/products/p_spec.php?pno=LC20&area=usa)
It needs a driver that isn't in the default list and adding it is a little convoluted.
[http://www.silverstonetek.com/download/d_contents.php?pno=LC20](http://www.silverstonetek.com/download/d_contents.php?pno=LC20)
But it would be nice if I could get it to work, because the IR receiver is built into the case.  I wouldn't need a separate USB receiver connected and just sitting there.

Does anyone know why the remote stops working randomly (usually after a reboot)?  To fix it, I have to go in and change the controller to some other manufacturer, apply that, and then change it back...?

---

### Post by rodercot on 2009-01-31
> **davidstoll said:**
> The purge did it again.  Thanks.

I'm using the MCE and also the Stream Zap.  My PC case also has one, but I can't seem to get it to work.
[http://www.silverstonetek.com/products/p_spec.php?pno=LC20&area=usa](http://www.silverstonetek.com/products/p_spec.php?pno=LC20&area=usa)
It needs a driver that isn't in the default list and adding it is a little convoluted.
[http://www.silverstonetek.com/download/d_contents.php?pno=LC20](http://www.silverstonetek.com/download/d_contents.php?pno=LC20)
But it would be nice if I could get it to work, because the IR receiver is built into the case.  I wouldn't need a separate USB receiver connected and just sitting there.

Does anyone know why the remote stops working randomly (usually after a reboot)?  To fix it, I have to go in and change the controller to some other manufacturer, apply that, and then change it back...?

 So your Lircd file is setup with both remotes in it and what I mean by this is 

 you have the confing files for the mce remote and the streamzap OR are you using the streamzap with the mce usb dongle by default lirc will setup your lircd with the mce remote in the /usr/share/lirc/remotes/mceusb directory you need to edit that file to tell it what remote to use ofcourse. Are you able to post your lircd and hardware.conf files here for us to take a look at. 

 As for the Silverstone, most of those are imon/soundgraph ir/vfd devices which should be in 0.8.2 by default. If you goto xbmc's forums under xbmc for linux there is a good guide for setting up the imon/soundgraph devices. I have not done this, I run a Zalman hd135 case with the VLSI mplay blast vfd/ir with an mce and gyration remote. I keep the gyration as then I do not need a mouse hooked up to the system at all. 

 you did checkout this link right, you should be able to use the lirc with imon part of this link. this is from the Silverstone link you supplied and under the section donwloads.

 [http://venky.ws/projects/imon/](http://venky.ws/projects/imon/)

 rgds,

 Dave 

 Dave

---

### Post by davidstoll on 2009-02-01
> **rodercot said:**
> So your Lircd file is setup with both remotes in it and what I mean by this is 

 you have the confing files for the mce remote and the streamzap OR are you using the streamzap with the mce usb dongle by default lirc will setup your lircd with the mce remote in the /usr/share/lirc/remotes/mceusb directory you need to edit that file to tell it what remote to use ofcourse. Are you able to post your lircd and hardware.conf files here for us to take a look at. 

 As for the Silverstone, most of those are imon/soundgraph ir/vfd devices which should be in 0.8.2 by default. If you goto xbmc's forums under xbmc for linux there is a good guide for setting up the imon/soundgraph devices. I have not done this, I run a Zalman hd135 case with the VLSI mplay blast vfd/ir with an mce and gyration remote. I keep the gyration as then I do not need a mouse hooked up to the system at all. 

 you did checkout this link right, you should be able to use the lirc with imon part of this link. this is from the Silverstone link you supplied and under the section donwloads.

 [http://venky.ws/projects/imon/](http://venky.ws/projects/imon/)

 rgds,

 Dave 

 Dave

I have a streamzap USB dongle and an MCE usb dongle.
I just use the Mythbuntu Control Centre to select which IR device I want to use.  I'm not 100% sure I understand your question, but I'm so new to linux that it doesn't take much to lose me.

Basically, my remote just stops working...which ever I happen to have configured and setup at that time...usually the MCE.  I have to change the IR device (in the Mythbuntu Control Centre) to something else (anything else) and then switch it back.  That usually fixes it, but sometimes I have to do it a few times...or sometimes reboot and then switch it back and forth.

There really isn't much to share with those two files, but I have attached them.

---

### Post by rodercot on 2009-02-01
that is the lircd file from your /etc/lirc directory and the one that lirc is acutally using is on

 /usr/share/lirc/remotes/mceusb

 I notice you have setup a custom transmitter, this is only for turning on blaster output for changing channels on your stb or cable box, with mce dongle this should be set the same mceusb new versions et all... under transmitter choices and for your rcvr be it dish, directtv etc... 

 you were asking about getting the remote working with your built in to the case ir capability and the link I supplied will tell you how to do that and that support for it is build into the lirc version you are using.

 Dave

---

### Post by davidstoll on 2009-02-01
> **rodercot said:**
> that is the lircd file from your /etc/lirc directory and the one that lirc is acutally using is on

 /usr/share/lirc/remotes/mceusb

 I notice you have setup a custom transmitter, this is only for turning on blaster output for changing channels on your stb or cable box, with mce dongle this should be set the same mceusb new versions et all... under transmitter choices and for your rcvr be it dish, directtv etc... 

 you were asking about getting the remote working with your built in to the case ir capability and the link I supplied will tell you how to do that and that support for it is build into the lirc version you are using.

 Dave

Yes, I do have an external box that I am trying to control.  Right now I'm just tinkering with it.  Normally I turn it off.

I did check out that link.  Thank you, but that was the page where I was getting the instructions that weren't working for me originally.  Part of my problem is that I don't have /usr/src/linux/.  I tried replacing it with /usr/src/linux-headers-2.6.27-11/ but it still didn't work for me.

I've been reading in other forums and they have instructions that are a little different for setting it up.  They talk about having a /dev/lcd0/ device...but I don't have that.  However, I know that the device is detected because when I type lsusb, it lists the device.

I tried

---

### Post by rodercot on 2009-02-02
> **davidstoll said:**
> Yes, I do have an external box that I am trying to control.  Right now I'm just tinkering with it.  Normally I turn it off.

I did check out that link.  Thank you, but that was the page where I was getting the instructions that weren't working for me originally.  Part of my problem is that I don't have /usr/src/linux/.  I tried replacing it with /usr/src/linux-headers-2.6.27-11/ but it still didn't work for me.

I've been reading in other forums and they have instructions that are a little different for setting it up.  They talk about having a /dev/lcd0/ device...but I don't have that.  However, I know that the device is detected because when I type lsusb, it lists the device.

I tried


 Well /dev/lcd is for your VFD if I recall and you need lcdproc installed to work with that and that is just not a program to play with without reading in that link there are instructions for setting up just the ir portion of your Imon (the rcvr in your case)

 The MCE remote is the easiest to use and setup for both receiveing and transmitting. If you go to the Myth control center and change your remote settings

 remote = mceusb phillips et all
 transmitter = mceusb new versions philips et all - dish or direct tv or one of the others. If you get this working first then I will get you a link to a channel change script that you can use for your box. unplug the streamzap dongle and setup mceusb as above and you should not have a problem with your remote stopping anymore.

 Dave

---

