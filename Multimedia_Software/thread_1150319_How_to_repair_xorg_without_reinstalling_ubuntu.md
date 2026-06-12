---
title: "How to repair xorg without reinstalling ubuntu?"
date: 2009-05-06
forum: Multimedia Software
---

### Post by Grey Box on 2009-05-06
I am running Jaunty 64bit (Thinkpad T500 with GMA 4500 integrated intel grpahics) which I installed during the testing period last year. Since then something happened to my intel xorg drivers and, basically, they don't work (garbled screen, regardless of xorg.conf settings) and I am stuck using the vesa drivers. Everything works from a live usb, including 3d acceleration, but I don't want to have to reinstall!

How can I perform a complete reconfiguration of xorg so that it completely resets its files and drivers to default?  Which packages must I remove/reinstall to achieve this?

Thanks very much in advance.

---

### Post by pastalavista on 2009-05-06
I'm not versed in xorg files but you can boot in recovery mode and the last option in the list of tasks is xfix. It's saved me a couple of times.

---

### Post by Grey Box on 2009-05-06
I just tried that, however it appears to only repair xorg.conf. In any case, no joy. I think somewhere I have a corrupted or incompatible package that is causing problems - hence why I think I need to reinstall xorg and its drivers.

---

### Post by pbpersson on 2009-05-06
remove:
```
sudo apt-get remove xserver-xorg
```

install:
```
sudo apt-get install xserver-xorg
```

reconfigure:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Grey Box on 2009-05-06
Thankyou pbpersson,

I just performed those commands. It went along smoothly and xorg was reinstalled, etc. 

Unfortunately, it has not fixed my problem. I cannot figure out where the issue is now. I would have thought that all of the video related packages and configuration options are reinstalled with those commands, but the video still crashes on trying the intel drivers instead of vesa.

Perhaps I will have to reinstall the entire OS after all?

---

### Post by pbpersson on 2009-05-06
> **Grey Box said:**
>  Everything works from a live usb, including 3d acceleration, but I don't want to have to reinstall!


What is different on the live USB?  How is it setup?  How does xorg.conf appear?  What driver version is used?  Are there other configuration settings outside of xorg.conf?

---

### Post by Grey Box on 2009-05-06
The live USB is the generic [actually, amd64] 9.04 desktop version, with no modifications. It doesn't have an xorg.conf.  My hard drive install is 9.04 [amd 64] with all updates, no experimental repositories and no xorg.conf.

My current intel-xorg drivers are 2.6.3. 

The behaviour I'm having isn't any of the known bugs with the intel drivers, but on trying to enable 3D effects, it "searchers for available drivers" then dies without a message - xorg restarts and I have to login again, with vesa drivers. I'm guessing that a config file somewhere or a library or something is broken or the wrong version, but at that point it's way beyond my abilities I think.

---

### Post by pbpersson on 2009-05-06
When you ran the "sudo dpkg-reconfigure xserver-xorg" command it was supposed to write all the settings to the xorg.conf file.  I don't understand how you can be running XServer without an xorg.conf file so I am clearly no help to you.  You must be running a totally different sort of setup.

---

### Post by Grey Box on 2009-05-06
> **pbpersson said:**
> When you ran the "sudo dpkg-reconfigure xserver-xorg" command it was supposed to write all the settings to the xorg.conf file.  I don't understand how you can be running XServer without an xorg.conf file so I am clearly no help to you.  You must be running a totally different sort of setup.

I very much appreciate your help all the same!

With the latest xorg you can pretty much do away with the xorg.conf for many configurations, because it auto-detects on startup and adjusts to whatever display and graphics card you might have (eg: external displays and so on), depending on available drivers. 

I've probably broken something along the way without realizing it. When I have a moment I'll take a look at the log files and see if I can understand any of them. 

Either way I'll inform the thread of my outcome. Cheers.

---

### Post by pastalavista on 2009-05-06
> **pbpersson said:**
> remove:
```
sudo apt-get remove xserver-xorg
```

install:
```
sudo apt-get install xserver-xorg
```

reconfigure:
```
sudo dpkg-reconfigure xserver-xorg
```

Follow pbpersson's advice again, but in the first command, use ```
sudo apt-get remove --purge xserver-xorg
``` The --purge will also remove your config files.

---

### Post by Grey Box on 2009-05-06
pastalavista: I just tried that, rebooting etc, but still the same behaviour. 

Just went through the xorg logfile (attached), and found a few warnings but none that I could understand... except that I think it's actually using the intel driver but a couple of things are odd, eg: 

```
(WW) intel(0): ESR is 0x00000010, page table error
(WW) intel(0): PGTBL_ER is 0x00100000, CS instruction GTT PTE
(WW) intel(0): Existing errors found in hardware state.
```

Would be nice to solve this, as it might help others, of course, though I'm not sure this is a common fault.

-- Update: --
I have abandoned trying to figure this one out. Reinstalling Ubuntu has become such a trivial task now that it was quicker to do that. Thanks for your help guys.

---

### Post by Takahe on 2009-05-13
Thanks to Pastalavista's update on pbpersson's note Ubuntu 9.04 still sits on my server - a PowerEdge SC1430 with ATI ES1000 video.
 
After chcking for updates for 8.10 I noticed the new release - 9.04 and without too much heitation let the autoupdate do its thing. It did, then requested a reboot and that is the last I saw of Ubuntu until finding your 'purge' instructions.
 
After the reboot I saw the 'Ubuntu' splash screen with the loader and then the monitor went into spasms before settling on a mess in the lower 2/3rds of the screen about 1/2 a dozen mini Ubuntus near the top and a mini-mess at the top. That was as good as it got for two days while I worked through the Ubuntu restore (ESC as the GRUB loads during bootup) and cursed my faith in updates as I worked through the various work arounds suggested by;
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) and then [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) from an article on 9.04 [(http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/]("http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/")).
 
I never did find anyhting remotely useful on rollingback to 8.04 or reinstalling 9.10 and frankly if it wasn't for the presence of several VMware machines on the machine Ubuntu would be history... 
 
So thanks again folks... your purge worked its magic and in much less time than it took to remove all the other 'fixes'.

---

### Post by pastalavista on 2009-05-13
It's good to hear that now your only problem is lack of the desktop. Probably, if you removed and reinstalled whichever desktop your're using and used the --purge to get rid of the mistakes, it could revert to a working state too ;) But the actual problem would seem to be the graphics display driver. It's a matter of blacklisting, I think, but I'm not sure of the commands. I believe the file to be altered is in /etc/modprobe.d

---

### Post by TomBrown2009 on 2009-08-24
Thank you pastalivista and pbpersson for your solutions to this post by Grey Box.

I came across this old post while searching the forum, having exactly the same problem as Takahe. The command line instructions you suggested worked for me.

Regards

Tom

---

### Post by ernz on 2010-06-22
In my case, the laptop powered down during an update and seemed to have broken a few packages and broke X in the process. Here's what I did:

1) Clean broken packages/complete update
```
sudo dpkg --configure -a
```

2) Remove broken xserver-xorg
```
sudo apt-get remove --purge xserver-xorg
```

3) Reinstate xserver-xorg
```
sudo apt-get install xserver-xorg
```

4) Reconfigure X 
```
sudo nvidia-xconfig
```

5) Start X
```
startx
```

Also, have you ever missed "sudo" from the beginning of a command? You can run the last command as sudo by simply typing:
sudo !!

---

