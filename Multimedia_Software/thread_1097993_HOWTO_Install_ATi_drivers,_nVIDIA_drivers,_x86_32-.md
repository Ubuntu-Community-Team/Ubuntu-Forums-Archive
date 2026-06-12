---
title: "HOWTO: Install ATi drivers, nVIDIA drivers, x86 32-bit and AMD64 against Ubuntu way"
date: 2009-03-16
forum: Multimedia Software
---

### Post by Neo_The_User on 2009-03-16
**Please go to [http://neo-technical.wikispaces.com/custom-kernel](http://neo-technical.wikispaces.com/custom-kernel) to learn how to configure, and compile a custom kernel, then install the ATi drivers with the custom kernel.**

I constantly see threads about installing drivers. Well here it is. A guide on installing the drivers all the possible different ways for both graphics cards for 2 different CPUs. (This should be a sticky due to constant new posts)

[B][SIZE="4"]ATi driver installation for 32-bit i386 - i686 processor on Ubuntu 8.04 - 9.04 
(9.04 WILL WORK FOR THE ATI DRIVERS WHEN CATALYST 9.4 COMES OUT AS CONFIRMED BY FGLRX DEVELOPER THAT I KNOW)[/SIZE][/B]

Terminal located in Applications > Accessories > Terminal:

```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
wget https://www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run
sh ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/hardy

```
Replace the last command with hardy to intrepid or jaunty depending on your distro.

```

sudo dpkg -i xorg-driver-fglrx_8.582-0ubuntu1_i386.deb fglrx-kernel-source_8.582-0ubuntu1_i386.deb fglrx-amdcccle_8.582-0ubuntu1_i386.deb
sudo aticonfig --initial -f
sudo telinit 6

```

**[SIZE="4"]ATi Driver installation for AMD64 64-bit (REQUIRES AMD64 PROCESSOR! IF UNSURE USE THE X86 32-BIT GUIDE![/SIZE]**

```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r) ia32-libs
wget https://www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run
sh ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/hardy

```
Replace hardy with jaunty or intrepid depending on your linux distribution.

```

sudo dpkg -i xorg-driver-fglrx_8.561-0ubuntu1_amd64.deb fglrx-kernel-source_8.561-0ubuntu1_amd64.deb fglrx-amdcccle_8.561-0ubuntu1_amd64.deb
sudo apt-get install -f
sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.582-0ubuntu1_amd64.deb fglrx-kernel-source_8.582-0ubuntu1_amd64.deb fglrx-amdcccle_8.582-0ubuntu1_amd64.deb
sudo aticonfig --initial -f
sudo telinit 6

```

**[SIZE="4"]Installing the nVIDIA drivers for x86 i386-i686 32-bit processors and AMD64 depending on the driver[/SIZE]**

go to [http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us) and select the driver you wish to download and save it in the root of your home folder.

```

sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install xorg-dev build-essential dh-make cdbs dkms libstdc++6 libstdc++5 debconf debhelper automake autoconf ia32-libs

```

[SIZE="4"][B]
Write all this down on paper before proceeding[/B][/SIZE]

```

sudo /etc/init.d/gdm stop
sudo sh NVIDIA*.run
sudo telinit 6

```

---

### Post by Neo_The_User on 2009-03-20
just thought i'd bump this due to all the installation threads. I see so many threads created DAILY about driver installation problems. Please make this a sticky.

---

### Post by reverseninja on 2009-03-22
welp after going step by step I was successful for updating my driver.  However, now when I watch any of my media that has english subtitles (anime and such) the subtitles do not show up, neither in Totem or VLC.  Any suggestions?

---

### Post by Neo_The_User on 2009-03-23
Definitely not something to do with the driver. The driver only effects video acceleration and overall preformance. Small things like subtitles will not be effected. Most likely its just your video player. Check your settings.

---

### Post by MiD-AwE on 2009-03-23
I followed your instruction exactly and after the ```
sudo telinit 6
```
The system restarted. (I'm still very newb, so this may be as it should be) . When my system restarted everything looked good but I never made it to the login screen. I got messages on all monitors telling me out of range and the machine just sat there. I had to back up the new xorg.conf file and ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
just to get a working xserver. Any suggestions?

---

### Post by Neo_The_User on 2009-03-24
It's been awhile since I last used nVIDIA. You might need to edit the xorg.conf file and set it to use the nVIDIA drivers.

Post the broken xorg.conf file.

---

### Post by MiD-AwE on 2009-03-24
I've recently updated my machine and now I'm using dual ATI Radeon HD 4650 cards, but I could still use some advice if you have any to offer.

Thanks

UPDATE: I found another thread that said they have the same problem and it is due to the ATI driver attempting to (incorrectly) auto detect resolution and refresh. Even though I have new cards I'm using old monitors. My monitors only support maximum 1024x768 resolution and no higher than 75hz. So, to correct a mistake I made in my first post here, the error I get is not "Out of Range" it is instead "Unknown". I've tried the suggested fix on the Launchpad bug thread, and it seems the best solution is to wait for Jaunty 9.04 which should have this bug squashed. If your interested here is the link to the bug report: [https://bugs.launchpad.net/bugs/325431](https://bugs.launchpad.net/bugs/325431)

---

### Post by Neo_The_User on 2009-03-24
Running Xorg -configure in command line with no GUI loaded on any of the ttys will set fglrx to not autodetect your displays after a reboot. You will have to use sudo aticonfig --initial -f again though when you get back into a GUI.

---

### Post by MiD-AwE on 2009-03-25
Ok, I've installed jaunty and I'm very impressed. Then I followed your instructions again. I finally get an error message in jaunty when I try to run catalyst control center. I've attached the image of the error. Any suggestions? It looks like we're making progress :P

---

### Post by reverseninja on 2009-03-25
Well, before the driver update I was getting flickery video (using totem or vlc) but subtitles.  Now, video is great but no subtitles no matter what I change in VLC or totem.  Since the only thing that has changed was the driver, I'm guessing I have to tweak vlc or some such.  Oh and I tried vlc %m and %f and I get my subs back but it's flickery video again.  Ah well, that's okay, back to metacity for now.

---

### Post by MiD-AwE on 2009-03-25
Neo_The_User,

After the last error message I posted I started the computer this morning and found myself staring at the cmd-prompt. No GUI. So, I typed gdm and I get this message:

> gdm[3778]: Warning: GDM file gdm-daemon-config.c: line 2042 (): Cannot run seteuid to 0: Operation not permitted GDM file gdm-daemon-config.c: line 2042 (): Cannot run seteuid to 0: Operation not permitted 

The double message must be because of my two ATI Radeon HD 4650 cards, but do you have any suggestion as to how I can at least get back to GNOME? A little more information, I did:

```
sudo nano /etc/X11/xorg.conf
```

and the file came up blank. I then attempted: 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

but the result did not change even though the xorg.conf file has been regenerated. Should this be reported to ATI as a bug, or . . . ? :confused:

Thanks for your help.

---

### Post by Neo_The_User on 2009-03-25
> **MiD-AwE said:**
> Ok, I've installed jaunty and I'm very impressed. Then I followed your instructions again. I finally get an error message in jaunty when I try to run catalyst control center. I've attached the image of the error. Any suggestions? It looks like we're making progress :P

I said it won't work with jaunty in huge big black letters in my guide. Xorg Server 1.6 conflicts with fglrx.

on 8.10 and you got that error, try reading the error then doing it.

As it says, "atiocnfig --initial -f"

so in terminal on 8.10:

```

sudo aticonfig --initial -f

```

---

### Post by MiD-AwE on 2009-03-25
I apologize if I've angered you. I read > (9.04 as if this writing will not work ATM)
Maybe our understandings of the English language are different because I see "as if" as sarcastically meaning it does work at the moment. Sorry to have troubled you.

---

### Post by zika on 2009-03-25
there is a fglrx driver for jaunty (8.600) in the repos already.  personally I do not like it and do not use it but it is here ... it does not use xorg.conf any more for most of its options and is relying on aticonfig for that paired with amdpcsdb ... ([http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593)) ...

---

### Post by wbee on 2009-03-25
Neo_The_User,

Thank you for putting this all together and posting it.

When I downloaded 8.10,it prompted me to select,download,and install a nvidia proprietary driver,offering me three choices.

The one that was recommended would not load. The one in the middle of the list would not load. Finally,the other one did load----and it was a mess. It changed resolutions and speeds and would not allow resets.(The 8.10 download had read and set the resolutions and speed correctly.)

Playing around with it,looking for patterns,I found the "envy" software in the software manager,went to the website,and followed the advice there.

Not knowing any better,being new at this,on the chance there might have been a bug in the installer function and not the driver itself,I uninstalled the driver and supporting hardware at the terminal line,though the envy program says it does so starting with 8.4.

Anyhow,the envy program loaded the correct driver(the one the nvidia page green arrowed) and so far,all is well.

Now,if I can figure out alsa and pulse and how they mount and parallel each other,I'll be all set.:-)

----------

Thank you
W

---

### Post by Neo_The_User on 2009-03-25
> **MiD-AwE said:**
> I apologize if I've angered you. I read 
Maybe our understandings of the English language are different because I see "as if" as sarcastically meaning it does work at the moment. Sorry to have troubled you.

oh shoot! it was supposed to say As of. that was my mistake. amazing how one letter changes everything!

@wbee: don't use envy as its a complete wreck. Back in the day with 7.10, it was great. now its not really supported. I think only one or two people are working  on it. :/

---

### Post by mtm_king on 2009-03-26
When I run

*wget xhttps://www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run*

I get
 
*use '--no-check-certificate'.*

If I add that to the end of the command I get

*WARNING: certificat comman name 'a248.e.akamai.net' doesn't match requested host name 'www2.ati.com'.*

I am running Ubuntu 8.10 with an ATI Rage Pro.  I am getting a different video card, but I really want to get this on running for a while.

Any suggestions?

Thanks

---

### Post by Neo_The_User on 2009-03-27
because 

```

wget xhttps://www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run

```
should be replaced with

```

wget https://www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run

```

---

### Post by mtm_king on 2009-03-29
Hi Neo,

I put the "x" so the url would display correctly.

I got a new video card - NVIDIA FeForce 8400 GS.  

Ubuntu pretty much patch it's self up.  

Thanks

---

### Post by urd on 2009-03-31
> **Neo_The_User said:**
> **Please go to [http://neo-technical.wikispaces.com/custom-kernel](http://neo-technical.wikispaces.com/custom-kernel) to learn how to configure, and compile a custom kernel, then install the ATi drivers with the custom kernel.**

I constantly see threads about installing drivers. Well here it is. A guide on installing the drivers all the possible different ways for both graphics cards for 2 different CPUs. (This should be a sticky due to constant new posts)

[B][SIZE="4"]ATi driver installation for 32-bit i386 - i686 processor on Ubuntu 8.04 - 9.04 
(9.04 WILL WORK FOR THE ATI DRIVERS WHEN CATALYST 9.4 COMES OUT AS CONFIRMED BY FGLRX DEVELOPER THAT I KNOW)[/SIZE][/B]

Terminal located in Applications > Accessories > Terminal:

```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
wget https://www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run
sh ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/hardy

```
Replace the last command with hardy to intrepid or jaunty depending on your distro.

```

sudo dpkg -i xorg-driver-fglrx_8.582-0ubuntu1_i386.deb fglrx-kernel-source_8.582-0ubuntu1_i386.deb fglrx-amdcccle_8.582-0ubuntu1_i386.deb
sudo aticonfig --initial -f
sudo telinit 6

```

**[SIZE="4"]ATi Driver installation for AMD64 64-bit (REQUIRES AMD64 PROCESSOR! IF UNSURE USE THE X86 32-BIT GUIDE![/SIZE]**

```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r) ia32-libs
wget https://www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run
sh ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/hardy

```
Replace hardy with jaunty or intrepid depending on your linux distribution.

```

sudo dpkg -i xorg-driver-fglrx_8.561-0ubuntu1_amd64.deb fglrx-kernel-source_8.561-0ubuntu1_amd64.deb fglrx-amdcccle_8.561-0ubuntu1_amd64.deb
sudo apt-get install -f
sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.582-0ubuntu1_amd64.deb fglrx-kernel-source_8.582-0ubuntu1_amd64.deb fglrx-amdcccle_8.582-0ubuntu1_amd64.deb
sudo aticonfig --initial -f
sudo telinit 6

```


hi!, sorry i'm new here, and i'm trying to installing the driver vi usb, what i need to change in the code and how??? the only way that i can do it is by consoloe, because my UI is broken and the driver is the problem

thanks for any help :)

---

### Post by Bloemetjesgordijn on 2009-04-01
thx for the how to.

Does these steps also arrange ATI Hybrid Crossfire to work for Jaunty??


Cheerz

Bloemetjesgordijn

oops I think i found it

> **Neo_The_User said:**
> [B]
(9.04 WILL WORK FOR THE ATI DRIVERS WHEN CATALYST 9.4 COMES OUT AS CONFIRMED BY FGLRX DEVELOPER THAT I KNOW)[/SIZE][/B]

---

### Post by iheartubuntu on 2009-04-04
Sorry to bug... :) ...is there any release date when I can make full use of my ATI card in Jaunty? I miss Super Tux Kart!

---

### Post by mactece on 2009-05-04
Now that catalyst 9.4 is out should all the references to 9.04 in your original post be changed to 9.04? Is it that simple? (or am I? :))

---

