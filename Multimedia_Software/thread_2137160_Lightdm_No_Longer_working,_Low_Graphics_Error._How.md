---
title: "Lightdm No Longer working, Low Graphics Error. How Do I Fix?"
date: 2013-04-19
forum: Multimedia Software
---

### Post by RocketPenguin on 2013-04-19
Ello ubuntuforums! How are we today? My laptop running Ubuntu 12.04 seems to have caught the lightdm not working, booting in low graphics mode bug, as seen here: 
 [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/495973](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/495973)
I am having the same problem that this guy is having. When I did my daily updates on April 8, i had to reboot. So, i did. When it started again, i came to the "Low graphics boot screen" That said something about my graphics not being configured or something. So, for a temporary fix, i switched to gdm. None of the other methods that i read about worked. Thing is, i really need lightdm back. Without it, no gaming. I haven't played Minecraft for the last two-three weeks, and i don't think i can live much longer without it. Anyone have any ideas on fixing it?
GPU: AMD ATI Radeon x2300 
CPU: Duo Core intel 2.2 ghz
Hard Drive: Solid state 30gb
Brand: Compaq 6910p HP Laptop
DISTRO: Ubuntu 12.04 Precise Pangolin

If you have any questions, just ask.

---

### Post by matt_symes on 2013-04-20
Hi

What have you tried so far to fix it ?

Have you seen this ?

[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

Kind regards

---

### Post by RocketPenguin on 2013-04-20
Yes, i have tried those methods. When i did  > [FONT=Ubuntu Mono]sudo nano /etc/lightdm/lightdm.conf[/FONT] The line was already like it said it needed to be changed to. I have tried to re-install fglrx, and i couldn't find my graphics drivers on the support page. It is way too confusing. I chose notebook, and it brings up a whole list of options i don't know. I tried all of them, and none seem to have my graphics card. I guess i could retry the conf. one... If someone could assist me with finding the correct driver, that would be great.

---

### Post by matt_symes on 2013-04-20
Hi

First some information about the open source radeon and the closed source binary blob made by AMD.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Don't go to the AMD website to get the drivers unless you have to. Get them from the repository. 

You're not using windows now :D

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Use this guide immediately above. Follow the steps for installing by the command line 2.1. 

Very simple, just copy the terminal commands into the terminal one after another hitting <enter> after each one. 

Reboot each time you are told to.

Any problems then post back.

Kind regards

---

### Post by Yellow Pasque on 2013-04-20
Do not follow the directions in the last post. Modern versions of fglrx (ones that actually run in 12.04) do not support Radeon X2300, so you should remove it, and that will probably fix your system: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

If you're still stuck in low-graphics mode after rebooting, post your /var/log/Xorg.0.log

---

### Post by matt_symes on 2013-04-20
Hi

> **Temüjin said:**
> Do not follow the directions in the last post. Modern versions of fglrx (ones that actually run in 12.04) do not support Radeon X2300, so you should remove it, and that will probably fix your system: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

If you're still stuck in low-graphics mode after rebooting, post your /var/log/Xorg.0.log

Is that so ? The OP must have been mistaken when he said he used fglrx before then (unless i misread his post. it does happen).

I did link in the open source drive page just in case he needed it.

If your right then thank you as you have saved us time and work.

Kind regards

---

### Post by RocketPenguin on 2013-04-21
> **matt_symes said:**
> Hi



Is that so ? The OP must have been mistaken when he said he used fglrx before then (unless i misread his post. it does happen).

I did link in the open source drive page just in case he needed it.

If your right then thank you as you have saved us time and work.

Kind regards

I think Tumujin is correct, and that may be the reason that it didn't work when i tried it.

---

### Post by RocketPenguin on 2013-04-21
> **Temüjin said:**
> Do not follow the directions in the last post. Modern versions of fglrx (ones that actually run in 12.04) do not support Radeon X2300, so you should remove it, and that will probably fix your system: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

If you're still stuck in low-graphics mode after rebooting, post your /var/log/Xorg.0.log

It may just be me, but i think the link may be broken. It isn't working for me. I did try this though: [http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install](http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install) And the steps that it said should happened, it said that i found a compatible driver, and installed it. Any ideas to see if it actually installed a driver?

---

### Post by matt_symes on 2013-04-21
Hi

> **linux junkie said:**
> I think Tumujin is correct, and that may be the reason that it didn't work when i tried it.

Ahh. That makes perfect sense then. I make a note of that graphics card for my future reference. 

Please try not to use words like reinstall unless you did reinstall ;) I don't have time to check everything :)

Thanks again Tumujin. You're a star.

Kind regards

---

### Post by matt_symes on 2013-04-21
Hi

> **linux junkie said:**
> It may just be me, but i think the link may be broken. 

This is the meat of that link. It's an instruction on how to uninstall the catalyst driver.

> The uninstall script in the first command will only exist if you  downloaded the drivers and installed them directly (rather than building  packages as this guide does). Skip the first command if it does not  exist. 

```

sudo sh /usr/share/ati/fglrx-uninstall.sh 
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*  
```

If you plan on using open-source drivers, you will need to reinstall  some packages because Catalyst overwrites or diverts some key 3D  libraries with proprietary versions. For more information on this issue,  see [this Ubuntu wiki page]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver") 

```

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon sudo apt-get install xserver-xorg-video-ati sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup sudo rm -rf /etc/ati  
```


If you receive 

$ E: Internal Error, No file name for libgl1-mesa-dri  Change the third command above to: 

```

sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core
``` 

> It isn't working for me. I did try this though: [http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install](http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install)  And the steps that it said should happened, it said that i found a  compatible driver, and installed it. Any ideas to see if it actually  installed a driver?

This may give some indication.

```
dpkg -l | egrep "fglrx|catalyst"
```

You need to uninstall the fglrx driver.

Kind regards

---

### Post by RocketPenguin on 2013-04-21
> **matt_symes said:**
> Hi



Ahh. That makes perfect sense then. I make a note of that graphics card for my future reference. 

Please try not to use words like reinstall unless you did reinstall ;) I don't have time to check everything :)

Thanks again Tumujin. You're a star.

Kind regards

Well, i DID reinstall. I purged the original, then i reinstalled it....

---

### Post by RocketPenguin on 2013-04-21
> **matt_symes said:**
> Hi



This is the meat of that link. It's an instruction on how to uninstall the catalyst driver.





This may give some indication.

```
dpkg -l | egrep "fglrx|catalyst"
```

You need to uninstall the fglrx driver.

Kind regards
 
I will try that top part if this software i used didn't work, but for now, i want to see. I would hate to uninstall what i just did, if it would have worked. the output of  ```
dpkg -l | egrep "fglrx|catalyst"
``` is:
>  ii  fglrx                                  2:8.970-0ubuntu1                         Video driver for the AMD graphics acceleratorsii  fglrx-amdcccle                         2:8.970-0ubuntu1                         Catalyst Control Center for the AMD graphics accelerators
ii  fglrx-dev                              2:8.970-0ubuntu1                         Video driver for the AMD graphics accelerators (devel files)
Does this mean i still have fglrx? Or that i installed fglrx? What do i need to do now? If this doesn't work, i will go and do the other thing you said...

---

### Post by matt_symes on 2013-04-21
Hi

The dpkg command was just to see if you had fglrx installed. You do.

What you need to do is follow the instructions in post #10 to purge flgrx. The section under the "this is the meat of it".

You do not want to reinstall fglrx. That will not work on your system. Your graphics card is too old to run that driver.

Purging fglrx should allow you to use the radeon driver (the open source driver) and that will work on you system.

Kind regards

---

### Post by RocketPenguin on 2013-04-21
Thankyouthankyouthankyouthankyouthankyou!!!!! I finally got it to work. As you said, i just needed to remove fglrx. With that, i switched back to lightdm, rebooted, and no problems booting!! UbuntuForums has saved my neck again. And thank you for helping, and giving your time. I really hope i wont have any more graphics issues... I have had enough of it... This is the second time it has hapened, and the first time i reinstalled. Though, the other time had a different error... But still, Thank you. Glad all is working again.

Thanks for your help and time, 
Linux Junkie

---

