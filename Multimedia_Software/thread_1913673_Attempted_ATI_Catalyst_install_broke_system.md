---
title: "Attempted ATI Catalyst install broke system"
date: 2012-01-22
forum: Multimedia Software
---

### Post by ekhatch1435 on 2012-01-22
Hello, I have tried to find information specific enough for me to fix my problem but have not had any luck. Any help would be appreciated.

NOTE: I am running Ubuntu 10.04 LTS with gnome on a desktop PC. As far as I know I was running whatever video card drivers came with/updated with my standard Ubuntu install.

NOTE: I have been using Ubuntu Linux now for about 2 years and love it.  I consider myself an intermediate user and am familiar with basic bash and linux concepts.

NOTE: Before I did any of the things I am about to list there were no problems whatsoever. I attempted this to try and get better performance from the proprietary ATI driver/Catalyst Control Center.

I installed the ATI catalyst control center through the Ubuntu Software Center and there was no indication that anything went wrong until I tried to open it, it said something about not having the right driver or there being a problem with the driver.

I was about to go install the ATI drivers when I realized something was wrong. My Compiz was not working right - the features that it normally has such as widow transparency and rubbery effect when dragging and moving windows weren't working anymore. 

Furthermore, when I opened up chromium to see what was going on, chromium won't open and it gave me this message in my var/log/messages log:

Jan 22 20:30:20 ron-desktop kernel: [ 2543.021657] chromium-browse[2046]: segfault at 4 ip 69cf9ef6 sp b1bc45e4 error 4 in libGL.so.1.2[69c94000+a7000]

So next I figure the Catalyst Control Center I just installed was the culprit, so I uninstalled it via software manager. No indication of any errors or faults with the uninstall.

Problem persists.

Next I went online via firefox, which still works, to see what was going on and found a lot of mumbo jumbo about these ATI installs breaking libgl and not fixing it upon uninstall.

SO....I figured what the F, maybe if I go through with the Proprietary ATI driver install, the system will have everything it needs to work correctly.  I read the PDF instructions for linux x86 proprietary ATI driver install and the first thing it tells me to do is uninstall the drivers already on my machine.  I try to do as it says and go to:

"/usr/share/ati" and run "sh ./fglrx-uninstall.sh"

I find out there is no ati folder in /usr/share/ so i go to the ubuntu software manager and try to uninstall fglrx.

When I try to uninstall fglrx it says i have to uninstall fglrx-amdcccle (catalyst control center) also and i select remove all.

It gives me an error message: The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.

Confusion: I am not sure what package I thought I installed and then subsequently uninstalled before, but according to softare manager, catalyst and ati drivers were already installed on my computer and the installation was broken so now I can't uninstall.

Not sure what to do now because according to software manager I am stuck in the middle of a broken installation and according to /var/log/messages my libgl is fubar.

Anyone with insight/experience would be a huge help.

---

### Post by MoreOrLess on 2012-01-23
What's the output of:
```
sudo apt-get remove --purge fglrx fglrx-amdcccle
```

---

### Post by ekhatch1435 on 2012-01-23
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by coffeecat on 2012-01-23
What happens when you run 'sudo dpkg --configure -a'?

---

### Post by ekhatch1435 on 2012-01-23
im going to check in a couple of hours...I have to be careful not to mess anything else up while I work on this license testing for right now.

---

### Post by ekhatch1435 on 2012-01-23
OK! running "sudo dpkg --configure -a" worked! now I can install/uninstall things again with ubuntu software manager.  I think I want to scrap the ATI driver install and just get things back to how they were before because the documentation for the install seems outdated and some of the packages it says are required are ancient and only in .rpm format which doesn't make much sense considering how they say it supports ubuntu. so much for legacy drivers lol.

anyone have any idea about the libgl thing that my /var/log/messages says is screwed up? how do i get my system back to how it was before?

thanks for the help so far!!

---

### Post by coffeecat on 2012-01-23
Perhaps the best thing would be to purge the proprietary driver plus any associated packages and re-install the open source driver. Have a look at this link:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Personally, I'd go for the aggressive, "Problem: Need to fully remove -fglrx and reinstall -ati from scratch" option. I'm not sure whether "sudo dpkg-reconfigure xserver-xorg" will remove the xorg.conf file that will have been installed for the propretiary driver and which is not needed for the open source driver and may interfere with it. I suggest you also run this command after that lot:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

It may not be necessary, but it won't do any harm.

---

### Post by ekhatch1435 on 2012-01-23
:guitar:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

The "aggressive" solution did the trick. Everything is gravy now.

Thanks everyone!!!!!

---

