---
title: "How to: install a new ati card with the latest driver"
date: 2010-02-17
forum: Multimedia Software
---

### Post by markbuntu on 2010-02-17
This is for RV600 (HD3xxx) cards and higher (HD4xxx and 5xxx) and for installing the latest proprietary  fglrx driver from ATI for any HD3xxx, Hd4xxx, and HD5xxx) on systems running Ubuntu 8.04, 8.10, 9.04, and 9.10. It is recommended that you use the latest driver available, especially for the many new 4xxx cards(4350, 4750 etc), Mobility HD4xxxx and HD5xxx. There is a link below which will always get you the latest driver. 

NOTE: AS of the 10.2 driver release and before these drivers will not work with Xorg-xserver 1.7 of the 2.6.32 or later kernel which are part of Ubuntu 10.04 (Lucid Lynx). So, if you are testing Lucid do not even try to install this driver. Hopefully that will get remedied in the next release or two. 

If you are having problems with an installed driver this can help you clean out the old driver and install a new one properly. Follow the directions and Just skip the install the new card section. This will also help if you are replacing an Nvidia card with an ati card.

If you do not follow these steps exactly you will have problems so please be careful.

**Step 1; Remove old drivers.**
Note: ATI recommends you uninstall the ATI Proprietary Linux
Driver before installing a newer version.

If you have just done a clean install and have not enabled or installed any proprietary drivers then you can skip this part.

If you have installed the driver and it is giving you problems it may be mis-installed so removing it and starting again clean is often faster and easier than trying to figure out what went wrong.

If you are using a driver that you downloaded from the ati site and installed it using the installer there is a removal script that you can use:
```

sudo sh /usr/share/ati/fglrx-uninstall.sh

```


If you installed the driver using  Jockey (hardware manager) then that means the driver is from the Ubuntu repository and has been packaged a little differently so you will need to remove it as follows (you may also need to use this method if you used dpkg to build and install the driver):
```

sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev

```
The driver also may replace the following files with proprietary versions so you may need to restore them to their generic state:
```

sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core

```

If you use Envy to install the driver, use Envy and chose remove completely.

If you are replacing an Nvidia card and used the nvidia proprietary driver the driver should also be removed completely BEFORE REMOVING THE CARD. This will save you a lot of headaches.

**reboot into recovery kernel** and use the fix-x option or "repair broken packages" to get to the generic VESA driver working.  You can verify that the VESA driver is in use by checking in /var/log/Xorg.0.log. 

**STEP 2:Shutdown the system and install the new card.**
If you are replacing an old card or installing a new card or adding a new card to a system that was previously using integrated graphics then you must enter the bios and make sure that the correct card is recognized and enabled and the IGP disabled. 

Boot up the system and again use the fix-x or repair broken packages option. This is necessary because even the VESA driver needs to be initialized again for a different card
...continue....
If you want you can check again in /var/log/Xorg.0.log to make sure everything is OK.
You may not have a maximum resolution display and no desktop effects but do not change anything yet, you still need to install the new driver.

**Step3:Install the new driver.**
Go to the ati site and download the latest driver for your card to your Desktop (You can also do this before you start)

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Open a terminal and navigate to the Desktop

```

cd Desktop

```
Make the installer executable by right clicking on it and choosing Properties/Permissions and checking the box next to Execute: and close the window.
Run the installer
```

sudo sh ./ati-driver-installer.....

```
You can finish the rest of the line with the full name of the driver file including the .bin. You will be asked for your password, just type it in and the installer should run. When the driver stops and asks you questions just hit enter.

After the driver is finished installing return to the terminal and type
```

sudo aticonfig --initial

```

You should get some message like "found uniitalized file xorg.conf blah bah blah....
 If you have an X2 card, which has 2 gpus, or multiple cards you should use
```

sudo aticonfig --adapter=all --initial

```
If you get an error you can try
```

sudo aticonfig --initial -f

```
This will force aticonfig to overwrite the old xorg.conf.

**reboot** If you do not reboot the driver will not work.

** Post Installation tips**
Do not use Preferences/Display or Screen Resolution to adjust your display. 
The driver comes with the Catalyst Control Center for adjusting the display and configuring the driver. It will be in your menu. You need to use the superuser mode to make most changes. If it does not launch from the menu you can launch it from a terminal with
```

sudo amdcccle

```
There is also the command line utility aticonfig which has more options than CCC and is useful for setting up crossfire and a bunch of other stuff you can do to tweak the driver. For a full list of aticonfig options you can use
```

aticonfig --help

```

Be very careful using these utilities, they do not like more than one change at a time before you reboot.

**Problems and other issues**
There are many old guides around and a lot of their advice is outdated. For one thing it is no longer necessary to build the packages yourself since the installer will now recognize Ubuntu and build the proper packages itself. Many of the old xorg.conf options they tell you to use are also no longer necessary and do not work for all cards so be very careful if you try them.

There may be some bugs with the installer for a few particular cards on some particular Ubuntu distributions. It is impossible for the devs to test every combination. If you run across a problem please file a bug at Launchpad and/or the ati bugzilla so it can get fixed. You can also post here and we will see what we can do to help.


Regards and good luck,
mark

P.S.
I wrote this due to the large number of requests for help installing ati cards or fixing broken fglrx drivers found on these forums recently. If you come across requests for this type of help please direct them here. It will help to consolidate the discussion in a central location so it is easier for people to find and participate.

---

### Post by Yevoc on 2010-02-17
After performing this step:
```
sudo sh ./ati-driver-installer.....
```
A window pops up giving you options to either "Install Driver 8.702 on X.Org 7.4 and later releases" or "Generate Distribution Specific Driver Package."

I'm guessing we should choose the latter for best performance?  No idea how the 2 choices should be any different.

---

### Post by Yevoc on 2010-02-17
So I chose "Generate Distribution Specific Driver Package," which told me to run the command below..

```
sudo sh ./ati-driver-installer-10-2-x86.x86_64.run --listpkg
```

Which indicated driver packages had been made for the distributions below...

    Ubuntu/gutsy
    Ubuntu/hardy
    Ubuntu/intrepid
    Ubuntu/jaunty
    Ubuntu/lucid
    Ubuntu/source
    Ubuntu/karmic

Since I'm Ubuntu 9.10, I then ran:
```
sudo sh ./ati-driver-installer-10-2-x86.x86_64.run --buildpkg Ubuntu/karmic
```

Which performed unspecified install actions in a window before dumping these files onto the desktop...

Package /home/john/Desktop/xorg-driver-fglrx_8.702-0ubuntu1_i386.deb has been successfully generated
Package /home/john/Desktop/xorg-driver-fglrx-dev_8.702-0ubuntu1_i386.deb has been successfully generated
Package /home/john/Desktop/fglrx-kernel-source_8.702-0ubuntu1_i386.deb has been successfully generated
Package /home/john/Desktop/fglrx-amdcccle_8.702-0ubuntu1_i386.deb has been successfully generated
Package /home/john/Desktop/fglrx-modaliases_8.702-0ubuntu1_i386.deb has been successfully generated
Package /home/john/Desktop/libamdxvba1_8.702-0ubuntu1_i386.deb has been successfully generated

No explanation or direction was given after this finished, so I guess I'll install each of these individual files manually and report back.

Given Ati's lack of usability and documentation here (which I know is a step up from what it used to be in the past), they are still making it 20 times harder to install drivers in Linux than Windows.  Maybe we need to bribe them into actually making documentation or a better install script?

---

### Post by Yevoc on 2010-02-17
> **markbuntu said:**
> it is no longer necessary to build the packages yourself since the installer will now recognize Ubuntu and build the proper packages itself.

I didn't notice this before.  I'd surmise from this that choosing the first option in the window, "Install Driver 8.702 on X.Org 7.4 and later releases," would've been equivalent to my installing the .debs from the second option.

Regardless, I installed all .debs except "xorg-driver-fglrx-dev," followed the rest of the steps, and everything seems to be running fine. (after 5 minutes of operation)  At least amdcccle comes up faster.

Thanks so much for the painful effort in detailing out these steps for us!

---

### Post by markbuntu on 2010-02-18
You really do not need to generate the distribution specific packages, the installer will recognize the Ubuntu distribution you are using and build and install the packages automatically.

Youm can choose the "Install Driver...." which is the default by just hitting enter. That's what I do and have not had any problems with the proper packages building and installing on Hardy, or Jaunty or Karmic. I do not always install the latest driver on all these distros I am running but have updated all of them at least a few times.

---

### Post by BobDoLe on 2010-03-07
I'm running 9.10 and trying to install 10.2 catalyst driver for a radeon hd 4650 that was just installed. I've been researching this issue for hours and I keep going around in circles - seems like countless people have the same problem with no real solution. 

I did just as you said above and although the gui indicated it was installed properly, the terminal indicated this: ```
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details

```

So I take a look at fglrx-install log output:
```

Creating symlink /var/lib/dkms/fglrx/8.702/source ->
                 /usr/src/fglrx-8.702

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
su nobody -c "cd /var/lib/dkms/fglrx/8.702/build; sh make.sh --nohints --uname_r=2.6.31-20-generic --norootcheck"....(bad exit status: 1)
0
0
[Error] Kernel Module : Failed to build fglrx-8.702 with DKMS
[Error] Kernel Module : Removing fglrx-8.702 from DKMS

```
After this, I do the 'aticonfig --initial' and reboot.

The problem is that everything moves very slow. As to be expected, xorg log shows this:

 X```
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

and fglrxinfo...
[code]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

```

Please HELP!!
Thanks!

---

### Post by BobDoLe on 2010-03-08
i gave up - ended up just re-installing 9.10. went with 64bit to finally take advantage of the processor. installed proprietary using jockey-gtk and it worked without a hitch.


edit: or so i thought. card was still running about half as fast as it should have. ended up ditching the whole system and went with an AMD Phenom II setup with a 1gig ddr5 ati card. reinstalled 9.10 and proprietary driver installation completed just fine (after dependencies installed). 

GOOD LUCK to anyone who is having this problem.

---

### Post by MrFaler on 2010-03-22
Hi, thank you very much for this guide, it helped me greatly.

I just finished doing this, but I did it from a fresh install, with nothing but the command line.
I want to make a guide myself on how to do that with nothing but the command line interface, can I get your permission to use a part of this guide in my own?

And ofcourse I will give you credit.

Thank you very much.

---

### Post by adrk on 2010-04-16
I went east and west on the internet to find a thread explaining like this but no way.

You are great!!!!
thank you.
this is the first time I could install my driver.
I am new to linux.
I followed many procedures explained on internet before.No one worked.
This is the first time I find  a procedure that works. and what a great sensation !!!!!!!!!!

Thank you vey much

---

### Post by sumigo on 2010-04-16
Hello,

i just found this after entering a new entry on the "hardware/laptop forum:

Hello,

I have never been a software wiz but I have always been proficient at getting a system running or fixed (windows pc's of course) and turning them back over to the people who own them to mess up again.

Recently I put together a Frankenstein system out of old parts to use as a HTPC, installed ubuntu and liked it enough to try a dual boot on my main system, so far so good for the most part, its been working.

However I noticed that the graphics are fuzzy and not what I feel they should be.

I am running an AMD X2 5200+ with a gigabyte mobo, 4 gigs of a-data vitesta, and just installed a new gigabyte 5830 (liked the price versus performance ratio of this card).

Ok so I went to download the current ATI drivers (not the new 10.1 driver) and when i go to install the driver in the terminal it says I need to be a SUPER USER. 

I perused these forums and discovered that I need to go into the terminal and run "sudo -i" to get SUPER USER privelages which I did, but then when I run the install it opens its own terminal, does not recognize my new SUPER USER status and says the same error.

I came back to the forums and read some more, confused and frustrated, then I read about envy, I downladed the package for envy hoping this would solve my issue, the envy program found the recommended driver and downloaded it and installed it, then asked to reboot, I obliged, however now it will only boot in "low graphic mode" and even running in Ubuntu "recovery mode" and running repair will not fix it. Also now when I go into envy the program crashes and wants to file a bug report, which is totally flabergasting.

I want this to work very much, but if I cannot even install a simple driver even while doing as instructed then I am at a loss. I really am tired of Microscrew but this scenario is frustrating.

Can someone please give me some dumbed down noob instructions on how to help me please? 

Is envy the way to go or through the terminal?

If through the terminal how do I get it to recognize the install and allow me to keep my super user status? And as a follow up is "sudo -i" correct in getting SUPER USER privelages? Is there another command I should be using once I do that?

I am trying to be patient but have been suffering through this for a few days now trying to solve it on my own,and would like a resolution.

Thank you in advance for your time.

EDIT: Forgot to mention I am using Ubuntu 9.10 Karmic Koala


Will the suggestions above help me with this issue?

---

### Post by Yellow Pasque on 2010-04-16
@sumigo: Just copy/paste the commands in the guide (they're prefixed with sudo to give root permissions). If you still can't figure it out, then just upgrade to (or fresh install) Lucid and use the proprietary driver that comes with it (at the moment, it's better than the Catalyst available to the general public).

---

### Post by sumigo on 2010-04-16
Thank you Temujin (cool handle btw) I will go through this when I get home from work and go over this thoroughly.

I assume you mean the guide written at the beginning of this thread am I correct?

---

### Post by sumigo on 2010-04-16
Lucid Lynx solved the issue, thank you.

---

